# MapReduce (2004)

### What is the problem being solved?

The problem is to standardise the non-executional aspects of special-purpose computation, so that those issues (parallelising the computation, distributing the data, handling failures) can be abstracted away from the often simple execution logic.

### How was this problem solved previously?

Previously, those tasks where implemented with special-purpose computations that had to deal with the non-executional issues mentioned above. The closest effort was Bulk Symchronous Programming and some MPI primitives, but those abstractions were too generalised. 

### What is the main idea?

The main idea is to have a constrained programming model with two simple primitives, the map and reduce operators, and abstract away the non-executional logic behind this model. The map and reduce operators are the same concepts as those seen today in Python or other programming languages.

### What are the key results?

The paper defined the interface and provided an implementation of the interface (Figure 1) that enables automatic parallelisation and distribution of large-scale computation. Optimisations, such as assigning a task to a machine where the input data is already local (locality optimisation) and redundant execution for stragglers (backup task optimisation), were also suggested to achieve high performance on large clusters of commodity PC. The authors also tested the data transfer rates, demonstrating that optimisations worked as expected and that the algorithm is resistant to killed tasks (Figure 3). 

### What are the main limitations of this paper?

One limitation is the failure of the master node, in which the state of the map-reduce task will be lost - maybe the master node is replicated for fault-tolerance. The authors also offered guidelines in choosing N and M, but those parameters can be made to adapt to the given workload.

### Why did this paper have an impact?

The simple programming model encompasses a lot of tasks. Google (and many other technology companies due to cloud computing) has access to the resources (a cluster of machines), so they can employ this model to generalise many tasks. It solves a pain point and saves many programming hours because no special-purposed scripts are required.
