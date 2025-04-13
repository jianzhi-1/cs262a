# PyTorch FSDP (2023)

### What is the problem being solved?

The problem is to train large models with more than a few billion parameters, because those are not able to be trained on a single GPU device due to memory limitations. Also, another goal is to make the training process as smooth and easy as possible ("industry-grade" solution), while maintaining high training efficiency (same or improved hardware utilisation, low communication traffic, low memory footprint).

### How was this problem solved previously?

Previously, the DDP (data distributed parallel) wrapper in PyTorch was used. However, it performs model replication, so models with size larger than a GPU's memory cannot be trained. ZeRO does model parameter sharding, but it is not designed closely with the PyTorch framework. Hence, this prompts the work on a native (PyTorch) implementation of model parameter sharding, which is FSDP.

### What is the main idea?

The main idea is that FSDP decomposes a model into smaller units and shards the model along those units across multiple GPUs. During training, the parameters were communicated on-demand before computations. After use, the non-local parameters are freed.

Then, because FSDP is to be closely co-designed with PyTorch, there are many techniques such as deferred initialisation, optimisation of sharding strategies, communication optimisations and memory management techniques (rate limiter) that are used to improve performance.

### What are the key results?

The results showed that the optimisation techniques worked as expected (Figure 6c). It also showed FSDP can accommodate models of different sizes and achieves performance similar to DDP in terms of TFLOPS/GPU, but managed to scale effortlessly to larger models when DDP met with OOM error. FSDP achieves 50-60% of GPU hardware utilisation on a GPU cluster.

### What are the main limitations of this paper?

The main idea is the same as ZeRO, so it is not that novel. The contribution of the paper mainly stems from doing parameter sharding better, in the sense of implementing it in PyTorch and allowing users to customise the sharding as much as possible while lessening the impact on efficiency. Also, the target audience seems to be industrial researchers with access to a large cluster of GPUs, which is a small pool of people.

### Why did this paper have an impact?
The impact of the paper is probably enhanced by the fact that PyTorch is the most common ML research library. It appears to be used by the research labs of many leading company. 


