# Lakehouse (2021)

### What is the problem being solved?

The authors argued for a unified data platform architecture that implements data warehousing functionality over open data lake file formats. They believed that this new architecture will better address the four common problems in data architectures: (1) reliability; (2) data staleness; (3) limited support for advanced analytics; (4) total cost of ownership.

### How was this problem solved previously?

Data lakes were still the primary data architecture. There were related "cloud-native" systems such as Hive, Snowflake, BigQuery that achieved good commercial success but were not the primary data store in organisations. (5)

### What is the main idea?

The main idea is to have the system store data in a low-cost object store using a standard file format (e.g. Parquet), but implement a transactional metadata layer on top of the object store that annotates the objects belonging to a table version. This layer allows the implementation of management features (e.g. ACID, versioning) while keeping the bulk of data in low-cost object store. Clients can access data via standard file format. Optimisations such as caching, auxiliary data structures (e.g. indices and statistics), and data layout optimisations are used to achieve similar performance as traditional data warehouses.

### What are the key results?

The authors offered a possible Lakehouse system design (Figure 2). The authors also offered optimisations and evaluated the optimisations on TPC-DS with an execution engine, which showed the power score of the optimisations were the lowest (Figure 3).

### What are the main limitations of this paper?

The main limitation is that many optimisations from data warehouses (e.g. storing hot data on fast devices, maintaining statistics, co-optimisation) cannot be directly ported to Lakehouse (3.1), despite it being a unified architecture. Another limitation of the paper is the possibility of other designs for a Lakehouse. The paper provided one possible design and suggested another (i.e. a massively parallel serving layer (4)), but should have more for comparison purposes. Another limitation is that the optimal combination of storage formats, metadata layer designs and access APIs is yet to be found.

### Why did this paper have an impact?

The paper was probably implemented within Delta Lake in Databricks, which already comprises half the compute-hours (3.2) and half the workload (3.1). It is unclear if it had a big impact outside Databricks.
