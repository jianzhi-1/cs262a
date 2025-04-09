# Triton (2019)

### What is the problem being solved?

The problem is to provide custom implementations of efficient compute kernels (so as to achieve high hardware utilisation) for deep learning workloads at minimal performance cost and good portability. 

### How was this problem solved previously?

Previously, several domain-specific languages for DNNs (based on polyhedral machinery, loop synthesis techniques) were developed, such as Tensor Comprehensions, Halide, TVM, PlaidML. However, they are slower than vendor libraries and lack expressivity.

On the other hand, micro-kernels (hand-written, tile-level intrinsics) requires a lot of manual labour and also lacks portability.

### What is the main idea?

The authors reused the tile concept idea; a statically shaped multi-dimensional sub-array. Then, they made a compiler stack with a C-based language and a LLVM-based intermediae representation, which expresses tensor programs as operations on parametric tile variables. Then, in Triton-JIT, they proposed a set of optimisation passes for code generation to GPU code.

Tile-level opertions and optimisations. More flexibility and support for non-affine tensor indices, automatic inference of possible execution schedule that would otherwise have to be specified manually. Triton-JIT provides opportunities for both machine-independent and machine-dependent optimisations.

### What are the key results?

Triton is able to generate matrix multiplication implementations on par with cuBLAS, 3x faster than alternative domain-specific languages. It achieves consistently high TFLOPS (Figure 8). Triton is also able to produce portable implementations. 

### What are the main limitations of this paper?

A critism is that this paper essentially built almost an entire compiler stack. One may wonder if all the previous efforts (e.g. compiler optimisations from LLVM, IR design) were able to be carried over.

### Why did this paper have an impact?

Since more novel and custom primitives are emerging, one no longer needs experts to carefully perform the code generation. It allows researchers to write programs that reach near-peak hardware utilisation with less programming effort. It also abstracts away the difficult part of CUDA programming - coalescing memory transfer from DRAM to maximise bankwidth usage, minimise shared SRAM bank conflict upon retrieval, and maximising ILP and TLP. 

### Own Notes:
- Tile: a statically shaped multi-dimensional sub-array.

