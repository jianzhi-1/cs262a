# Mesos (2011)

### What is the problem being solved?

Sharing fine-grained resources across different cluster-computing frameworks without imposing individual constraints on their schedulers.

### How was this problem solved previously?

Previously, there were two solutions for sharing a cluster. The first way is to statically partition the cluster and run one framework per partition. The second way is to allocate a set of virtual machines to each framework. However, these methods fail to achieve high utilisation and efficient data sharing.

### What is the main idea?

The main idea is to delegate control over scheduling to the frameworks via a resource offer abstraction. This is achieved through a two-level scheduling mechanism: Mesos decides how many resources to offer to each framework via some computation; then frameworks decide which resources to accept and which tasks to run on them. Essentially, this is a decentralised scheduling model where the central scheduler does not impose individual constraints and give some flexibility to the sub-schedulers.

### What are the key results?

Mesos was measured with respect to ramp-up time, job completion time, and system utilisation. It was also tested with different workloads. The authors presented a theoretical framework and showed that the utilisation achieved by Mesos was optimal for elastic frameworks. Industrial usage showed that Mesos performs well in practice and data locality achieved nearly perfectly.

### What are the main limitations of this paper?

The scheduling by Mesos, though great, was not necessarily globally optimal. Also, there were no benchmarks to compare against (due to novelty), which is possibly why the authors opted for a theoretical framework.

### Why did this paper have an impact?

The idea of a two-level scheduler was pretty nice and is a change from the heuristic/algorithmic schedulers that we know of. The policy is very general and did not impose constraints that might hurt performance of individual frameworks. Mesos is also simple to implement, highly scalable and robust.

