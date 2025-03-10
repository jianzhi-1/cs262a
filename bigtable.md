# Bigtable (2006)

### What is the problem being solved?

The problem is to store structured data for various Google applications, while ensuring flexibility, high performance and high level of control.

### How was this problem solved previously?

Previous, there exists the Boxwood project, which is very similar to Bigtable but provided services at a lower level than what Google required. Also, it is not optimised for Google's internal applications. There were other efforts such as CAN, Chord, Tapestry, but those address more problems than what Google is concerned with (10).

### What is the main idea?

The assumption (validated empirically) is that most applications require only single-row transactions (9). Hence, the data model is such that data is maintained in lexigraphic order by row key and the row range (a.k.a. tablet) is dynamically partitioned (2). This allows for quick accesses to tablets without going through many machines. Two more dimensions (column, timestamps) are used for access controls and versioning. Bigtable follows the one-master design (master and many tablet servers). Relevant ideas are taken from distributed databases (B+ trees, distributed locking).

### What are the key results?

The authors did experiments in which a Bigtable cluster was scaled up and measured performance w.r.t. various workloads. The throughput scales very well (Figure 6). Random reads were found to have the worst performance across the workloads and methods (such as smaller block size) were proposed to alleviate it. There is also interaction with network and CPU processes, causing a non-linear scale up.

### What are the main limitations of this paper?

I think the main limitation is the limited use case of Bigtable. Only vendors with a large number of Web-scale services will find Bigtable useful, due to the assumptions of no untrusted participants, no variable bandwidth, no frequent reconfigurations. 

### Why did this paper have an impact?

It is impactful for Google because many of their applications are now supported by Bigtable clusters. The paper also listed several lessons learnt from implementing such an application, which will be rare due to the specific purpose of the application.
