# Dominant Resource Fairness (2011)

### What is the problem being solved?

The goal is to extend fair resource allocation from a system with only one type of resource to a system with different resource types, and where each process have different demands for each resource.

### How was this problem solved previously?

For multi-resource environments, previous methods such as slot-level fair sharing (used by Hadoop and Quincy) allocate resources at the level of slots (fixed-size partitions of the node). This does not take into account the different demands for resources by different jobs. Other ways of scheduling include max-min fairness and its weighted version.

### What is the main idea?

The main philosophy is that the allocation of a user should be determined by the user's dominant share (maximum share that the user has been allocated of any resource). To implement this, a linear optimisation problem is solved: maximise the resource allocation subject to resource constraints (inequalities constraint) and that dominant shares of each process are equal (equality constraint). This is one way to generalise max-min fairness for multiple resources.

### What are the key results?

Theoretical results showed that DRF has desirable theoretical properties: incentivises sharing, strategy-proof, envy-free, Pareto efficient. (5)

DRF is implemented in Mesos cluster resource manager. The empirical evidence showed that it performed as intended, with resource scheduling adaptive to chaning task sizes of the jobs (7.1). It led to better throughput and fairness than slot-based fair sharing schemes.

The trace-driven simulations showed that DRF led to better throughput (utilisation) and fairness (job completion time) than slot-based fair sharing schemes and the traditional max-min scheduling. (7.2)

### What are the main limitations of this paper?

The definition and construction of a "dominant resource" might not be good for a subset of processes. For example, a job might need a specific subset of resources that do not scale linearly with each other. This prompts consideration of second-dominant/third-dominant resources. Equating the most dominant resources might not be the best constraint to impose on the optimisation problem here.

### Why did this paper have an impact?
The scheduler is useful in datacenters where there are many processes with heterogenous demands. The theoretical properties of this way of scheduling allow these processes to coexist harmoniously. It can also be extended to other multi-resource allocation environments (e.g. multi-core machines).
