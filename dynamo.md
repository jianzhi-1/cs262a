# Dynamo (2007)

### What is the problem being solved?

The problem is to achieve extremely high availability and reliability for a distributed data store at massive scale.

### How was this problem solved previously?

There were a lot of work done previously in P2P systems, distributed databases/file systems with various structures, guarantees etc. However, Amazon clearly does not use them because they have their own metric, which is to have extremely high availbility and reliability (must be able to handle network partitions); and are willing to sacrifice (under certain scenarios) consistency. 

### What is the main idea?

The main idea is to modify the traditional quorum system for get() and put() operations, called "sloppy quorum" (4.6), so as to achieve high availability. Dynamo has 3 tunable parameters depending on business needs: N = number of (healthy) nodes in the preference list that handles the operations; R = minimum number of nodes that must participate in a successful read operation; W = minimum number of nodes that must participate in a successful write operation. All read and write operations are performed on the first N healthy nodes from the preference list, rather than by walking the consistent hashing ring. This allows Dynamo to still be available during server failures and network partitions (when the consistent hashing ring breaks). 

### What are the key results?

Running on standard commodity hardware components, Dynamo is able to achieve low latency in addition to providing high availability and reliability (Figure 4, 5). Its ability to load balance was also empirically verified (Figure 6). Various partitioning and placement strategies were experimented and the load distribution efficiency was compared (Figure 8). Surprisingly, there are no empirical results on availability and reliability.

### What are the main limitations of this paper?

Amazon has a set of its own objectives to optimise for, for example its insistence on maintaining a very high level of availability and the use of 99.9th percentile as its benchmark. Such personalised metric might lower the general applicability of the E2E method to other use cases, although it is still cool to see. It is also difficult to compare to related work because it operates on the end of the availability spectrum. Furthermore, the development of every application requires a discussion on the service level agreements to its unique business needs, which is not general-purposed (might lead to vendor lock-in problem).

### Why did this paper have an impact?

It is from Amazon. In the end, many applications which need storage turn to the S3 service, partially due to its high availability guarantees (99.99995% successful request rate) and reliability (no date loss event). 

### Extras

Highly available key-value distributed storage system, provides an "always-on" experience. Sacrifices consistency under certain failure scenarios to achieve high level of availbility. Extensive use of object versioning, application-assisted conflict resolution in a manner that provides a novel interface for developers to use.

Partitioning and replicating data using consistent hashing. Consistency replaced by object versioning. A "quorum-like technique" and a decentralised replica synchronisation protocol to maintain consistency among replicas during updates. Gossip-based distributed failure detection and membership protocol. Minimal need for manual administration. Storage nodes can dynamically be added or removed.

