# HybridFlow (2024)

### What is the problem being solved?

The problem is to create a RLHF framework that can execute the RLHF dataflow (where nodes = distributed LLM training or generation program, edges = many-to-many multicast between nodes) in a way that is flexible (easy to swap out policies / computation nodes) and efficient (low control dispatch overhead). 

### How was this problem solved previously?

Traditional (i.e. non-neural network) frameworks (such as RLLib and RLLibFlow) execute the dataflow using a hierarchical single controller (a node) that coordinates both intra-node computation and inter-node communication. This is inefficient due to substantial overhead of dispatching operators to distributed accelerators. Prior RLHF systems adopt a multi-controller paradigm. This has negligible dispatch overhead, but is inflexible to perform various RLHF dataflow (modifying a single node requires changing all dependent nodes' implementation).

### What is the main idea?

The main idea is to combine single-controller and multi-controller paradigms in a hybrid manner. The single-controller paradigm is used on the inter-node level to allow for flexible expression of various data dependencies and easy coordination of inter-node communication (i.e. low overhead). The multi-controller paradigm is used within intra-node computation to enhance computation efficiency. 

The authors also provide a set of hierarchical APIs that encapsulate distributed compuation of different LLMs. This allows efficient operation orchestration to implement RLHF algorithms and flexible mapping of computation onto various devices.

A 3D-HybridEngine is also designed for efficient execution of training and generation of the actor model (0 memory redundancy, reduced communication overhead).

### What are the key results?

HybridFlow achieved 1.53x - 20.57x throughput (tokens/second) improvement when running various RLHF algorithms as compared to state-of-the-art baselines (DeepSpeed-Chat, OpenRLHF, NeMo-Aligner). The authors attribtuted this to the fact that HybridFlow executes generation, inference, and training by sharding the models with different parallelism strategies to fit various computation workloads.

### What are the main limitations of this paper?

I personally find this paper very hard to follow, maybe because of my lack of experience in RL. Initially, it was also unclear what the authors meant by "flexible" and "efficient". Also, I wonder why the authors chose to focus on RLHF when the method of executing a computation graph can be generalised to arbitrary network.

### Why did this paper have an impact?
The project is open-sourced and backed by ByteDance, which is known for its recommendation systems. The flexibility would be extremely appreciated by RL researchers as they swap out policies/computation nodes.

### Own Notes:
- RL as dataflow, node represents computation of NN, edge denotes data dependency between the neural network.
- RLHF: expands each node into a distributed LLM training/generation program (basically, distributed computation that involves data/pipeline parallelism), edge becomes many-to-many multicast (data resharding). 
- Programming model for distributed machine learning:
- Single-controller paradigm: centralised controller that managements the overall execution flow of the distributed program. Controller can generate distributed workers to carry out the computation. Flexible and optimised resource mapping and execution order coordination among dataflow tasks because it has global view of the hardware and dataflow graph.
- Multi-controller paradigm: each device has its own controller; need collective communication, computation, point-to-point data transfer.

