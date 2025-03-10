# Google File System (2003)

### What is the problem being solved?

Summarising design decisions for a scalable, distributed file system for large distributed data-intensive applications, with certain assumptions (from empirical data) on workloads.

### How was this problem solved previously?

There are several distributed file systems before that are POSIX-compliant. Some removed the centralised server. GFS differs from them in that they optimised w.r.t. their workloads, hence it did not care for POSIX compliance. The features of GFS can be found in previous distributed file systems but with more optimisations.

### What is the main idea?

The main idea is to first observe the workload and its interaction with the current file systems: high component failure, modest number of very large files, high frequency of appends as compared to overwrites. Then, these observations are used to design and optimise the file system, such as using chunks as the unit of storage, minimising interactions with master (instead going directly to chunkservers), maintaining a persistent TCP connection, a "record append" operation for concurrent appends while guaranteeing atomicity.

### What are the key results?

A testing environment for a small scale GFS is simulated. The scaling graphs of read and write rates w.r.t. showed that the file system scales well to increasing number of clients, since both approaches the network limit. The append rate is resistant to sharp decreases as the number of clients scale. Google also published empirical evidence supporting their workload assumptions.

### What are the main limitations of this gaper?

GFS is very tailored to the workloads of Google and made several assumptions that might not stand the test of time (e.g. the composition of read and write types). Any changes to those will result in the loss of effectiveness of some portions of the design. Also, GFS also considers internal applications, which might not be what general developers are considering.

### Why did this paper have an impact?

It is from Google. Many people are interested in their workloads because it reflects the Web's usage. Therefore, Google's design pattern sets the standard for how systems can handle requests at a large scale and shows what optimisations can be considered.
