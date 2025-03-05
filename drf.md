# Dominant Resource Fairness (2011)

### What is the problem being solved?

Fair resource allocation in a system with different resource types, where each user have different demands for each resource. DRF: dominant Resource Fairness, a geneneralisation of max-min fairness to multiple resource types.

### How was this problem solved previously?

For multi-resource environments, previous methods allocate resources at the level of slots (fixed-size partitions of the node), regardless of different jobs' demands for resources.

Max-min fairness and its weighted version.
Slot-based fair sharing schemes

### What is the main idea?

Generalise max-min fairness for multiple resources. The main idea is that the allocation of a user should be determiend by the user's dominant share (maximum share that the user has been allocated of any resource). DRF maximises the minimum dominant share across all users.

### What are the key results?

Good theoretical properties: incentivises sharing, strategy-proof, envy-free, Pareto efficient.

Implemented in Mesos cluster resource manager -> empirical evidence that it leads to better throughput and fairness than slot-based fair sharing schemes.

### What are the main limitations of this paper?

"Attempt to equalise CPU with memory" -> how can this be achieved if not subjective? Would there be a case where a job need a specific subset of resources to work (e.g. all or nothing). How about second-dominant?

### Why did this paper have an impact?

Can extend to other multi=resource allocation environments (datacenters, multi-core machines).
