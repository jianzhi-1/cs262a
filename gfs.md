# Google File System (2003)

### What is the problem being solved?

Summarising design decisions for a scalable, distributed file system for large distributed data-intensive applications, with certain assumptions (from empirical data) on workloads.

### How was this problem solved previously?

There are several POSIX-compliant distributed file systems before. Some removed the centralised server. GFS differs from them in that they optimised w.r.t. their workloads, hence it did not care for POSIX compliance (8). The features of GFS can be found in previous distributed file systems but with more optimisations.

### What is the main idea?

The main idea is to first observe the workload and its interaction with the current file systems: high component failures, modest number of very large files, high frequency of appends as compared to overwrites. Then, these observations are used to design and optimise the file system, such as using chunks as the (larger) unit of storage, minimising interactions with master by going directly to chunkservers, maintaining a persistent TCP connection, having a "record append" operation for concurrent appends while guaranteeing atomicity etc.

### What are the key results?

A testing environment for a small scale GFS is simulated. The scaling graphs of read and write rates w.r.t. showed that the file system scales well to increasing number of clients, since both approaches the network limit in the limit. The append rate is resistant to sharp decreases as the number of clients scales. Google also published some empirical evidence supporting their workload assumptions (6.3).

### What are the main limitations of this gaper?

I think GFS is very tailored to Google's internal workloads and made several assumptions that might not stand the test of time (e.g. the composition of read and write types). Any changes to those will result in the loss of effectiveness of some portions of the design. The lessons learnt might not be relevant to general developers. Since GFS also impacts Google's internal applications (e.g. assumptions on the APIs to call), it might unintentionally shape how applications are designed and limit performance in some areas.

### Why did this paper have an impact?

It is from Google. Many people are interested in their workloads because it reflects the Web's usage. Therefore, Google's design pattern sets the standard for how systems can handle requests at a large scale and shows what optimisations can be considered.
