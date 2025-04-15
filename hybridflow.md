# HybridFlow (2024)

### What is the problem being solved?


### How was this problem solved previously?


### What is the main idea?

Combine a single-controller and multi-controller paradigms in a hybrid manner to enable flexible representation and efficient execution of the RLHF dataflow. 

A set of hierarchical APIs that decouple and encapsulate computation and data dependencies in the complex RLHF dataflow, allowing efficient operation orchestration to implement RLHF algorithms and flexible mappin gof computation onto various devices.

3D-Hybrid Enginee for efficient actor model resharding between training and generation phases, with zero memory redundancy, singificantly reduced communication overhead. 


### What are the key results?

1.53x - 20.57x throughput improvement when running various RLHF algorithms using HybridFlow, as compared to state-of-the-art baselines. 


### What are the main limitations of this paper?

### Why did this paper have an impact?
Open-sourced

### Own Notes:
- Programming model for distributed machine learning:
- Single-controller paradigm: centralised controller that managements the overall execution flow of the distributed program. Controller can generate distributed workers to carry out the computation. Flexible and optimised resource mapping and execution order coordination among dataflow tasks because it has global view of the hardware and dataflow graph.
- Multi-controller paradigm: each device has its own controller; need collective communication, computation, point-to-point data transfer.

