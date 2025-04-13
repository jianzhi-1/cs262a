# ZeRO (2019)

### What is the problem being solved?

The problem is to be able to train larger models with sizes that exceed the memory capacity of a single device (GPU), while maintaining performance (hardware utilisation).

### How was this problem solved previously?

Previously, two memory reducing methods are pipeline parallelism and model parallelism. However, exploiting pipeline parallelism requires tuning the batch size (which also affects convergence rate). Large bubble sizes can cause performance downgrades. The implementation of pipeline parallelism is also less standard and sometimes constrains the model. Model parallelism requires a model that can be sharded vertically and hence constrains the model. Furthermore, using MP turns out to be tedious in practice, as the researcher has to maintain correctness.

### What is the main idea?

The main idea is to partition the optimiser states, gradients, and parameters across the devices and make a tradeoff with higher communication volume. Then, other optimisations are applied on the remnant operations that impact memory, such as activation partitioning and offloading activation computation to CPU, allocating more accurate temporary buffer sizes, and managing memory based on the life-time of tensors.

### What are the key results?

ZeRO always provides a better speedup versus state of the art baselines for varying model sizes (Figure 2). It is able to train models up to 100B parameters on high-end hardware clusters (400 GPUs), which is a 8x increase in model size and 10x increase in available performance over the state of the art (Figure 3). It also has downstream results, where the trained large models managed to achieve higher accuracy due to training scaling.

### What are the main limitations of this paper?

Despite relieving the memory bottleneck, it places the bottleneck on compute power (9) and communication (10.4) instead. Also, it did not investigate interactions between the optimisation methods.

### Why did this paper have an impact?

For training, it vastly increases the allowed size of a model. Also, it involves no model refactoring and hence is easy to use as a standard, as opposed to the existing model parallelism. 
