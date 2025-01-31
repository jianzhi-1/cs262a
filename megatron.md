# Megatron (2021)

### What is the problem being solved?

Training large language models efficiently. Scaling to thousands of GPUs. Combining tensor, pipeline, and data parallelism to scale to thousands of GPUs. Improve throughput with same memory footprint.

### How was this problem solved previously?

ZeRO-3

### What is the main idea?

Suggested PTD-P. Novel interleaved pipelining schedule

Metric is throughput per GPU. Obtain scaling graph by training GPT of the appropriate sizes.

Investigated many dimensions.


### What are the key results?

Throughput improved by 10%. Memory footprint comparable to existing approaches. Tested that this interleaving allows the performing of training iterations on a model with 1 trillion parameters at 502 petaFLOP/s on 3072 GPUs (per-GPU throughput of 52% of theoretical peak). Graceful scaling. Train models with a trillion parameters.

Implemented using PyTorch, NCCL for communication between devices, optimisations in communication and computation.

Measured end-to-end training throughput of 163 teraFLOP/s per GPU, aggregated throughput of 502 petaFLOP/s on GPT model with 1 trillion parameter, mixed precision. Facilitate practical training time of 3 months.

Superlinear scaling to 3072 A100 GPUs. Provided empirical training time estimates and model.

Scales gracefully, meaning when more GPUs are used, the utilisation per GPU decreases less compared to ZeRO-3.

Demonstrated that the using of both parallelisms together work better than singularly.

Some guidance:
- Interactions between parallelisms: pipeline model parallelism must be used for larger models. Tensor model aprallelism useful within a multi-GPU server.
- Schedule used for pipeline parlalelism has impact on amount of communication, pipeline bubble size, memory used to store activations
- Search for optimal valye of microbatch size
- Distributed training is computationally intensive: use fast interconnects.
- Heuristics work well in practice.

### What are the main limitations of this paper?

Evaluation is not very fair since ZeRO-3 was evaluated without model parallelism.

### Why did this paper have an impact?

### Definitions
Data parallelism: have N copies of the model, split training data into smaller chunks, accumulate gradients. Issue: per-GPU batch size becomes too small, reudcing GPU utilisation, increased communication cost; batch size as limit for the number of accelerators used during training. Each worker has a copy of its full model. Input dataset is shaded, workers aggregate their gradients periodically to ensure they see consistent version of weights (2.1). Use data parallelism on model shards.

Tensor model parallelism: matrix multiplications within each transformer layer split over multiple GPUs.
- Issue: larger models need to be split across multiple multi-GPU servers, all-reduce communication required for tensor parallelism needs to go through inter-server links, slower than link available; high degree of model parallelism, small matrix multiplications, decreasing GPU utilisation.

Pipeline model parallelism: layers of a model are striped over multiple GPUs. A batch of data split into microbatches. Execution pipelined across these microbatches. A pipeline flush at the end of evrey batch to synchronise optimiser steps. Must use a high batch size to take advantage of pipelining; average cycles per batch decreases. Layers of a model sharded across multiple devices. 

Scheduling forward and backward microbatches across devices: tradeoff between pipeline bubble size, communication, memory footprint. 

Considerations: memory footprint, device utilisation, amount of communications

Memory footprint: how memory is used. Memory is used to store the activations (basically inputs to a layer of the neural network) for the backward pass.

Activation recomputations: An technique to trade off an increase in number of compute operations for lower memory footprint. Basically, set some checkpoints within a neural network. Only save activations at the input to the checkpoints. During the backward pass, run the forward pass within the checkpoint to get the intermediate values for backpropagation. As long as this technique is used, throughput is not affected by the number of checkpoints.



