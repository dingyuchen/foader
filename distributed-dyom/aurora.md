# Aurora

## Introduction

Aurora is a relational database service for OLTP workloads offered as part of AmazonWeb Services.

Checkpointing and dirty page writing can reduce the penalty of blocking reads.

dirty page writing 
: writing into a cache, that only becomes reflected on persistent storage when the buffer is flushed.


Transaction commits are intolerant of failure.
They are also high latency, as high scale systems are distributed across multiple data centers.
(140ms for nodes across the ocean)

### Core idea
Redo log (something similar to write-ahead logs)

1. protect the database from performance variance and transient or permanent failures at either the networking or storage tiers.
2. By only writing redo log records to storage, we are able to reduce network IOPS by an order of magnitude.
3. Move some of the most complex and critical functions (backup and redo recovery) from one-time expensive operations in the database engine to continuous asynchronous operations amortized across a large distributed fleet.

## Durability at scale

> Data, once written, can be read.

### Replication

Nodes need to be replicated on some level to achieve resiliency to failure.

Quorum must obey 2 rules

1. Each read must be aware of the most recent write.
2. Each write must be aware of the most recent write to avoid conflicting writes.

Availability Zone (AZ) is a subset of a Region that is connected to other AZs in the region through low latency links but is isolated for most faults, including power, networking, software deployments, flooding, etc.

Quorums need to tolerate an AZ failure as well as concurrently occurring background noise failures.

Chosen design point of tolerating
1. losing an entire AZ and one additional node (AZ + 1) without losing data, 
2. and losing an entire AZ without impacting the ability to write data.

Ensuring read quorum enables us to rebuild write quorum by adding additional replica copies.

> Can still achieve healing from a 3-node failure.

Partition the database volume into small fixed size segments, each replicated into Protection Groups (PG).


Segments are now our unit of independent of background noise failure and repair
We would eed to see two such failures in the same 10 second window plus a failure of an AZ not containing either of these two independent failures to lose quorum.

### Operational Advantages of Resilience

Treat nodes as "bad" and make use of repair mechanism.

> This allows us to use agile methodologies and rapid deployments in our storage service.

## The Log is the Database

Model of 6 ways segmentation and 4/6 quorum results in untenable performance for a traditional database like MySQL that generates many different actual I/Os for each application write.

Types of data that the engine needs to write:
1. The redo logs
2. Binary (statement) log that is archived to S# in order to support point-in-time restores 
3. The modified data pages
4. Seoncd temporary write of the data page (double-write) to prevent torn pages
5. Metadata (FRM) files


Durable redo record application happens at the storage tier, continuously, asynchronously, and distributed across the fleet. 
Any read request for a data page may require some redo records to be applied if the page is not current.
Crash recovery is spread across all normal foreground processing.
