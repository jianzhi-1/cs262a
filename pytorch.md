# PyTorch

### What is the problem being solved?

The creation of a machine learning library that is both efficient (high throughput), easy-to-use for the research community (easy to debug, trace, fast iteration i.e. low-to-no compilation time), inter-operable (can be used with other visualisation libraries) and flexible (can deal with architectures that take in variable length inputs such as RNN and support branching).

### How was this problem solved previously?

There is a class of define-then-run frameworks (TensorFlow, Caffe etc) which first creates a static dataflow graph, then runs data through it. This approach is fast but not flexible (difficult to support variable length input and conditionals); also hard to debug. There already exist define-by-run frameworks (Chainer, Torch, DyNet) but the paper says they are either slow (low throughput) or less expressive (not as flexible; can't support as many architectures).

### What is the main idea?

Present a machine learning library with several design principles to balance speed and ease of use, favouring ease of use.

Pythonic programming style (imperative, so under full control of user) for all deep learning workflow (not just the layers, but also optimisers, dataloader). Eager (easier debugging; no waiting for compilation). To still boost performance, PyTorch uses C++ core (fast; also avoids GIL; also allows interoperability by creating and using bindings), having separate control and dataflow, overlapping of execution of Python code on CPU and operations on GPU (saturate GPU), abstracts away CPU-GPU synchronisation. Custom allocator which bypasses calling CUDA APIs, maintains one pool of memory for every CUDA stream and is incrementally built up.

### What are the key results?

Demonstration that PyTorch does asynchronously execute dataflow on CPU and GPU. Demonstration that the custom allocator works as intended (incrementally build up memory pool and reuses it).
Overall speed of PyTorch on some benchmarks vs existing define-then-run and define-by-run frameworks; PyTorch competitive "within 17% of fastest framework" (6.3).
Received well by the research community (296 ICLR 2019 submissions with PyTorch).

### What are the main limitations of this paper?

PyTorch supports research-style development of machine learning models. To productionise, still need one more step of optimisation (they mentioned PyTorch JIT compiler).

### Why did this paper have an impact?

Supports the research community. Alignment of goals (speed, easy to debug, faster iteration, Pythonic). Easy to extend upon (Pythonic).

