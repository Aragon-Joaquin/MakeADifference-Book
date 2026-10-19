### LSM Trees

- where this could be useful
- why not a b-tree nor a in-memory hashmap
- whats a lsmtree & sstable
- benchmark

---

## Introduction

#### Storage engines

As known of, databases need to comply the ACID principles (even some NoSQL databases follow this principle like [MongoDB](https://www.mongodb.com/company/newsroom/press-releases/mongodb-announces-multi-document-acid-transactions-in-release-40)) and thus needing to implement a data structure being able to manage high writes & reads while having a relative low I/O cost and a transaction recovery.

Thinking about implementing a B-Tree is common, since most of relational databases uses them, although they are kindof limited when it comes off in a high write scenario. It would double the expensive in I/O since accessing random data is going to be much lower than sequential data[¹]. Instead, is it common to see b-trees and variants, like B+Trees, in highly demanding reads context (more on this later).

A log structured merge (LSM, for shorthand) tree is becoming the standard in NoSQL databases since it provides low-cost indexing for a file experiencing a high rate of record inserts (and deletes) over the long run, along side with a write ahead log (WAL) which makes possible to recover data in case of a unexpected shutdown of the system, although a WAL is not specific to LSMTrees only.

## The simple complexity of a modern LSMTree

![high_level_architecture](./images/high_level_arch.webp)

As you might expect, implementing a modern storage engine is not easy. We will continuing with the LSMTree example and explaining one of its components.

#### SSTable

A sorted string table (SSTable) is a persistent file of ordered key/value pairs where the key is the primary identifier for the block (which internally has in the same file, usually 64kb in size) and the value indicates the offset where this block starts. Usually this stage is reached only on writes and reads, by missing the cache of the Memtable and using a Bloom Filter. Both of these artifacts will be explained later on.

Then, an interesting question would be "Why we don't instead use in-memory hash maps for lookups in disk?".

```md
| key | offset |
| --- | ------ |
| 1   | 0      |
| 2   | 17     |
| 3   | 24     |
| 4   | ...    |

// example.db
1,"hello, world!"\n
2,"1120"\n
3,"\[null, 1, 10, null\]"\n
...
```

There's certain flaws with this:

- The hash table must fit in memory.
- A restart would require to compute every key offset since there's no disk recover for these indexes.
- Old log entries would be hard to modify since the offset would be pointing to the wrong location (changing the key 1 to "bye, world!" needs to update the offset of the following keys). Deleting entries also is a problem.

There's also compaction.

## LSMTrees vs B-Trees

Both of these data structures are use in a context of write/read-heavy applications like storage engines, cdn's and data processing.

## References

⁰¹²³⁴⁵⁶⁷⁸⁹

- 1] The Log-Structured Merge-Tree (LSM-Tree) | https://www.cs.umb.edu/~poneil/lsmtree.pdf

![LSM_vs_Btree_Benchmark](images/LSM_btree_Throughput.png)
![sequential_vs_random](images/jacobs3.jpg)

```

```
