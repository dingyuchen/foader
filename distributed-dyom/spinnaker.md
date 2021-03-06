# Spinnaker

Spinnaker is a datastore.

It features key-based range partitioning, 3-way replication, and a transactional get-put API with the option to choose either strong or timeline consistency on reads.

## Limitations Master-Slave Replication

Loss of either master or slave can result in permanent data loss.

For 3 replicas, more complicated failure sequences can be possible.

## Consistency

Strong consistency
: guarantees that all replicas appear identical to applications

Timeline consistency
: allows potentially stale data to be return in exchange for better performance.


[[cap-theorem]]

Within a single datacenter where network partitions are rar, opting for strong consistency and availability is a better design choice.

## Data Model and API

get(key, colname, consistent)
: Read a column value and its version number from a row. The setting of the 'consistent' flag is used to choose the consistency level.

> Setting it to `true` chooses strong consistency, and the latest value is always returned.
>
> Setting it to `false` chooses timeline consistency, and a possibly stale value is return in exchange for better performance.

put(key, colname, colvalue)
: Insert a column value into a row

delete(key, colname)
: Delete a column from a row

conditionalPut(key, colname, value, v)
: Insert a new column value into a row only if the column's current version number is equal to 'v'. Otherwise, an error is returned.

conditionalDelete(key, colname, v)
: Like `conditionalPut` but for delete

Version numbers are monotonically increasing integers that are managed by Spinnaker and exposed through its get API

## Architecture

Each node is assigned a base key range which is replicated on the next $N - 1$ nodes.

> $N$ is a replication setting

Each group of nodes involved in replicating a key range is denoted as a _cohort_.

### Node Architecture

## Replication Protocol

[//begin]: # "Autogenerated link references for markdown compatibility"
[cap-theorem]: cap-theorem "CAP Theorem"
[//end]: # "Autogenerated link references"