# Mesos (2011)

### What is the problem being solved?

Sharing fine-grained resources across different cluster-computing frameworks without imposing constraints.

### How was this problem solved previously?

Statically partition the cluster, run one framework per partition. Allocate a set of virtual machines to each framework. Fail to achieve high utilisation and efficient data sharing.

### What is the main idea?

Delegate control over scheduling to the frameworks via a resource offer absraction. Two-level scheduling: Mesos decides how many resources to offer to each framework (from its computation); frameworks decide which resources to accept and which tasks to run on them. Decentralised scheduling model.

### What are the key results?

Performs well in fractice. Data locality achieved nearly perfectly. Simple to impleement, highly scalable, robust.

### What are the main limitations of this paper?

Not globally optimal scheduling.

### Why did this paper have an impact?

Very general. Did not impose constraints.

