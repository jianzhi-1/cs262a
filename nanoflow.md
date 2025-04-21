# NanoFlow (2024)

### What is the problem being solved?

The problem is to minimise the underutilisation of resources (in particular compute = GPU) of LLM serving systems and thereby increasing its throughput. This is done by exploiting intra-device parallelism.

### How was this problem solved previously?

Orca and vLLM were used originally for language model serving. However, when viewed on a timeline (Figure 3), the authors showed that they do not fully utilise the most constrained resource (compute = GPU).

### What is the main idea?

The main idea is to exploit intra-device parallelism by overlapping the usage of resources (compute, memory, network) within a single device through operation co-scheduling. NanoFlow splits requests into nano-batches at the granularity of operations. The nano-batches can be co-scheduled on the same device and thus enabling overlapping of compute-, memory-, and network-intensive operations. The most constrained resource will no longer underutilised.

The device's functional units are partitioned across NanoFlow's operation-level pipeline. This allows simultaneous execution of different operations within each unit. 

### What are the key results?

NanoFlow was evaluated on LLaMA-2-70B model and used practical workloads from ShareGPT, LMSys and Splitwise. It achieved 1.91x greater throughput compared to state-of-the-art serving systems (vLLM, DeepSpeed-FastGen, TensorRT-LLM). This is between 59% to 72% of optimal throughput.

### What are the main limitations of this paper?

The improvement is not as great as I expected, though it might be significant for industrial use case. Industrial stakeholders might wonder whether they want to pivot to NanoFlow. It also raises many other problems to solve such as having a good operation scheduler.

### Why did this paper have an impact?

The parameter search is done automatically, so the partitioning of the device's functional units is automated. NanoFlow can generalise easily to arbitrary models, since it looks at the granularity of operations. NanoFlow is also open-sourced.
