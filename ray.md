# Ray (2017)

### What is the problem being solved?

The problem being solved is to support the deep reinforcement learning pipeline in a tightly-coupled way (training, serving, simulation). In more details, the system must provide fine-grained computations, support for heterogeneity in time and resource usage, and dynamic execution. It must also achieve performance of millions of tasks completed per second. 

### How was this problem solved previously?

Previous systems were mostly decoupled. For example, MapReduce, Spark Dryad do not support fine-grained simulation or policy serving. Task parallel systems (CIEL, Dask) were mainly not distributed. TensorFlow, MXNet do not naturally support simulation and serving.

RL scientists typically make one-off systems for their experiments, and thus do not benefit from system optimisations and efforts.

### What is the main idea?

The main idea is to build a general-purposed, distributed, cluster-computing framework that supports the entire RL pipeline (simulation, training and serving). To this end, Ray implements a dynamic task graph computation model. Ray also implements the actor and task abstractions. On the systems side, it has a distributed scheduler and a distributed, fault-tolerant store to manage the system's control state. They are both highly scalable and fault tolerant. This allows it to be flexible (unified interface) and can express both task-parallel and actor-based computations.

### What are the key results?

Ray was evaluated on evolution strategies, which showed that it has a speedup of 1.6x and can scale up to more cores. It was also evaluated on PPO, and outperformed the MPI implementation while using less GPUs. The cost factor also decreased by 4.5.

### What are the main limitations of this paper?

My personal opinion is that Ray seems to benefit mostly mature RL experiments (e.g. when people want to deploy their trained networks). It is still a steep system for researchers to conduct early-stage experiments, particularly in different context. I also wonder if Ray shares similar abstractions to OpenAI gym library.

### Why did this paper have an impact?

This paper aimed to support the entire standard deep reinforcement learning pipeline. Deep reinforcement learning is clearly an emerging field and a system that takes care of scheduling and fault tolerance will definitely be appreciated. It is also open-sourced. I think it is very useful for deploying mature RL experiments.

### Own Notes
- Serving system: using the trained policy to render an action based on the current state of the environment. Aims to minimise latency and maximise the number of decisions per second. To scale a serving system, load is typically balanced across multiple nodes serving the policy.
- Task: (stateless) execution of a remote function on a stateless worker
- Actor: (stateful) stateful computation


