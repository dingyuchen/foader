# Google File System
[[2021-01-17]]

#school #paper

> Original paper referenced [here](https://pdos.csail.mit.edu/6.824/papers/gfs.pdf)


## Motivation
Usage for Google's distributed file system defers from the traditional assumptions in the following ways:

1. Component failure are the norm rather than the exception.
2. Files are huge by traditional standards
3. Most files are mutated by appending new data rather than overwriting existing data. Random writes within a file are practically non-existent.
   - Appending is the focus of performance optimization and atomicity guarantees

## Design Overview

### Assumptions
1. System must be able to constantly monitor itself, detect and tolerate and recover from failures on a routine basis.
2. System is optimized for large, multi-GB files.
   - Small files are supported but not optimized for
3. Workload primarily consist of:
   1. Large streaming reads
   2. Small random reads
      - Small reads are batched together as large read by performance conscious applications anyway
4. Workload consist of large, sequential writes
5. System must efficiently implement well-defined semantics for multiple clients that concurrently append to the same file.
6. High sustained bandwidth is more important than low latency.

## GFS API
- Support the usual _create_, _delete_, _open_, _close_, _read_, _write_.
- Also provides _snapshot_ and _record append_.
## Architecture
- Single _master_, multiple _chunkservers_.
- Accessed by multiple _clients_.

> Neither the client nor the _chunkservers_ caches file data.

> Client **do** cache metadata

### Chunkserver
Files are divided into fixed-size chunks, each chunk is identified by an immutable and gloablly unique `64-bit` _chunk handle_.
Chunks are replicated on different chunkservers (replication level can be determined by user)

### Single Master
The _master_ 
- maintains all file system metadata
- controls chunk lease management, garbage collection and chunk migration

Polls _chunkservers_ periodically to send instructions and collect state.

#### Shadow Masters
Master state is replicated on other machines in order to achieve fault tolerance and high availability.
Shadow masters lag slightly and may provide stale metadata, however, it allows clients to perform read operations even when the master is down to enhance read availability.

It polls the master for operation log and applies the same mutations to its internal data structure.

### Chunk Size
`64mb` is much larger than typical file system block sizes.

Large chunk size pros:
1. Reduces client's need to interact with the master
2. Reduces network overhead by keeping a persistent connection to the chunkserver
3. Reduces the size of metadata

Cons:
- Small files that consist of only few chunks can become hotspots if many clients are accessing the same file.
  - unlikely since most files are big
  - increase replication factor and stagger batch-queue system.

### Metadata
- File and chunk namespaces
- Mapping from files to chunks
- Locations of each chunk's replicas

Namespaces and mappings are kept persistent by logging mutations to an _operation log_.

Locations are requested from the _chunkservers_ at startup and periodically after. This helps keep the _master_ in sync

### Operation Log
The operation log contains a historical record of critical metadata changes.
- Changes are not made visible to clients until metadata changes are made persistent.
- Log is replicated on multiple remote [machines](#shadow-masters) 
  - A mutation to the state is considered committed only after its log record has been flushed to disk locally and on all master replicas.
- Recovery needs only the latest complete checkpoint and subsequent log files.

## Consistency Model
> A file region is _consistent_ if all clients will always see the same data, regardless of which replicas they read from.

> A region is _defined_ after a file data mutation if it is consistent and clients will see what the mutation writes in its entirety.

File namespace mutations (creations) are atomic.

- Singular successful mutation guarantees file region to be defined and consistent.
- Concurrent successful mutations guarantees file region to be undefined but consistent.
- A failed mutation makes the region inconsistent.
  - If a record append fails at any replica, the client retries the operation. GFS only guarantees that the data is written at least once as an atomic unit.
  - Record prepared by the writer contains extra information like checksums so that its validity can be verified. Reader should handle padding and duplicates.

## System Interactions
Below I attempt to summarize the interactions during each GFS operation.

### Create
Client acquires read-lock along the directory nodes and write-lock for the file being created.

Subsequently client follows the same steps as in [write](#write).

### Read
1. Client requests read operation with file name, chunk index from master.
2. Master acquires the necessary read-locks, replies client with chunk handle and location.
3. Client caches chunk handle, requests chunk from "closest" machine.


### Write
1. Client asks the master which chunkserver holds the current lease for the chunk and the locations of the other replicas.
   1. Master grants the lease if no chunkserver is holding the lease
2. The master replies with the identity of the primary and the locations of the other replicas.
3. The client pushes the data to all replicas. 
4. Client sends a write request to the primary. 
5. Primary serializes the mutations and apply it to local state.
   1. If an error occurs at the primary, mutations will not be assigned a serial number and write request will not be forwarded.
6. Primary forwards the write request to all secondary replicas.
7. The primary replies to the client after replicas report success. Any errors in the replica is also forwarded (request will be considered a failure).

#### Chunk Overflow
Primary checks to see if appending the record to the current chunk would cause teh chunk to exceed the maximum size. 
If so, it pads the chunk to the maximum size, tells secondaries to do the same, and replies to client indicating that the operation should be retried on the next chunk.

> Record append is restricted to be at most $\frac{1}{4}$ of the maximum chunk size to keep worst-case fragmentation at an acceptable level.

#### Dataflow
Data is pushed linearly along a chain of chunkservers rather than distributed in some other topology.
Each machine's full outbound bandwidth is used to transfer the data as fast as possible rather than divided among multiple recipients.

Each machine forwards the data to the "closest" machine in the network topology that have not received it.

##### Pipelining
Once a chunkserver receives some data, it starts forwarding immediately. Useful in switched network with full-duplex links.

Without network congestion, the ideal elapsed time for transferring $B$ bytes to $R$ replicas is $B/T + RL$ where $T$ is the network throughput and $L$ is latency to transfer bytes between two machines.

### Delete
Deletion happens lazily and storage space is reclaimed from garbage collection.

1. Master logs deletion immediately.
2. File is renamed to a hidden name that includes the deletion timestamp.
   1. File is properly removed if it has existed for more than _some configurable interval_, during master's regular scan.
   2. Master removes in-memory metadata of hidden file.

In regular scan of the **chunk namespace**, the master identifies orphaned chunks and erases the metadata for those chunks.

In _HeartBeat_ messages exchanged with the master, each chunkserver reports a subset of the chunks it has, and the master replies with the identity of all chunks that are no longer present in the master's metadata. 
The chunkserver is free to delete its replicas of such chunks.

### Snapshot
Snapshots are implemented using standard copy-on-write techniques.

1. Master revokes any outstanding leases on the chunks that are about to be snapshot.
2. Master commits snapshot into its operation log
3. Metadata for the source file or directory tree is duplicated.

For write to some snapshot chunk $C$, master notices that the reference count for chunk $C$ is greater than one. 
It defers replying to the client request and instead picks a new chunk handle $C'$. 
It then asks each chunkserver with $C$ to create copy $C'$ locally.

## Fault Tolerance


# Discussion Questions
1. When does GFS choose _write append_ vs _record append_?
   1. write append -> non-concurrent ?
   2. record append -> concurrent ?
   3. Who decides?
2. Consider the paper "The Google File System" by Ghemawat et al. Suppose that, at the moment, nobody is writing to the GFS file named
"info". Two clients open "info" and read it from start to finish at
the same time. Both clients' cached meta-data information about file
"info" is correct and up-to-date. Are the two clients guaranteed to
see the same content? If yes, explain how GFS maintains this
guarantee; if no, describe an example scenario in which the clients
could see different content.
3. [2018 Q1](https://pdos.csail.mit.edu/6.824/quizzes/q18-1.pdf)
4. [2017 Q2.2](https://pdos.csail.mit.edu/6.824/quizzes/q17-1.pdf)


[//begin]: # "Autogenerated link references for markdown compatibility"
[2021-01-17]: ../journal/2021-01-17 "Sunday, January 17, 2021"
[//end]: # "Autogenerated link references"