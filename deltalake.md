# Delta Lake (2020)

### What is the problem being solved?

The problem is to improve the performance and consistency of existing cloud object stores.  
Performant and mutable table storage over systems. Consistency guarantees across datasets (2.2) instead of eventual consistency.


### How was this problem solved previously?

Cloud object stores implemented as key-value stores (Amazon S3) for simplicity and scalability. 

### What is the main idea?

ACID table storage layer over cloud object stores.
Transactional log to provide ACID properties. 

The main idea is to maintain information about which objects are part of a Delta table in an ACID manner, using a write-ahead log that is itself encoded in Parquet and stored in the cloud object store. Log also contains statistics about columns for optimisation purposes.


### What are the key results?

Faster metadata operations for large tabular datasets.


### What are the main limitations of this paper?

Only provides serialisable transactions within a single table, because each table has its own transaction log. Would like to sharing transaction log across multiple tables, but increases contention. Dependent on the latency of the underlying cloud object store for streaming workloads. Does not support secondary indices yet.

### Why did this paper have an impact?

Deployed at Databricks. Used at thousands of organisations. 

