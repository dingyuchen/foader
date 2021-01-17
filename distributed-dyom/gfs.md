# Google File System

#school #paper

> Original paper referenced [here](https://pdos.csail.mit.edu/6.824/papers/gfs.pdf)


## Motivation
Usage for Google's distributed file system defers from the traditional assumptions in the following ways:

1. 

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
5. System must efficiently implement well-defined semenatics for multiple clients that concurrently append to the same file.
6. High sustained bandwidth is more important than low latency.

## Architecture
