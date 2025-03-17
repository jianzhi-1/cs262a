# Delta Lake (2020)

### What is the problem being solved?

The problem is to improve the performance and consistency of existing cloud object stores. Specifically, to improve upon the eventual consistency offered by the object stores and the latency of scanning and modifying the key-value items.

### How was this problem solved previously?

There were several projects (Aurora, BigQuery, Redshift Spectrum, Snowflake) but those require a constantly running frontend node which is not scalable. There were also Hudi and Iceberg, which have less features than Delta Lake. (8)

### What is the main idea?

The main idea is to have an ACID table storage layer over the cloud object stores in which a write-ahead log (encoded in Parquet) is maintained to provide ACID properties. Log also contains statistics about columns for optimisation purposes. This allows clients to enjoy the traditional ACID properties (serialisability, consistency, atomicity) with high performance and also additional features such as time travel (1).

### What are the key results?

A series of experiments were conducted (6), which showed that Delta Lake with caching has superior SCAN latency and that optimisations (such as Z-ordering) were effective in skipping data. End-to-end performance was also measured on TPC-DS and Delta Lake was shown to outperform other configurations. The statistics collection was also shown not to contribute significant overhead.

### What are the main limitations of this paper?

Currently, Delta Lake only provides serialisable transactions within a single table (due to an individualised transaction log). It is desirable to share the transaction log, but that would increase contention. Delta Lake is also dependent on the latency of the underlying cloud object store for streaming workloads. It also does not support secondary indices yet. (7)

### Why did this paper have an impact?

It is deployed at Databricks and is already used by thousands of organisations to process exabytes of data daily. It has already replaced the traditional data warehouse architecture. Also, it is open-sourced.

