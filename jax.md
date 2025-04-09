# JAX (2018)

### What is the problem being solved?

Maximising hardware utility (in FLOPs) while also facilitating research-friendly programmability. The prior requires more static information, while dynamic languages (e.g. Python) are too unconstrained to enable optimised code generation

### How was this problem solved previously?

Previously, systems provide function calls to a fixed set of hand-written, target-specific numerical kernels. This is problematic because the kernels are target-dependent.

### What is the main idea?

The authors make the empirical observation that ML workloads are typically dominated by PSC subroutines, and thus use those as the unit of optimisation. PSCs consist of Numpy's numerical functions, Autograd's functions; hence they are very expressive and favourable for acceleration. JAX basically uses a XLA compiler infrastructure to generate optimised code for the PSCs. To compile a function, Jax traces it i.e. monitoring its execution once. It stores the signature to trace mapping in the trace cache in case it reencounters the same signature in the future.

### What are the key results?

A lot of nodes were optimised away after fusion (Figure 1). The compiled and fused code had 100+x speed up over its normal Python runtime. It scales well with increasing replica count: linear speedup and execution time is minimally impacted by replica count. It has comparable performance to TensorFlow with minimal changes to an existing Python script.

### What are the main limitations of this paper?

One concern is that the expressivity of the primitives might be limited. I am also concerned about how this scales with larger code sizes (rather than replica count), since the paper mentioned a trace cache. Could large models cause trace cache thrashing and thereby fail to be optimised efficiently?

### Why did this paper have an impact?

JAX is a simple and flexible way of getting improvement out of an existing Python script for machine learning. It also integrates well with the major Python libraries: numpy, tensorflow and torch.

### Own Notes:
Pure: a function is pure when it does not have side effects.
Statically-composed: a function is statically composed relative to a set of primitive functions when it can be represented as a static data dependency graph on those primitives.
PSC: pure and statically-composed functions - prime candidates for acceleration.
PSC entry point: a Python function for which the PSC assumption holds.
Monomorphic signature: a signature for a function such that any newly encountered array element types, aray dimensions, or tuple members will fail to match the signature and thus trigger a re-compilation.
Trace cache: a cache mapping the signatures to its trace

### More Notes:

A domain-specific tracing JIT compiler for generating high performance accelerator code from pure Python and Numpy.

JAX supports structured control flow -> can generate code for sophisticated machine learning algorithms while maintaining high performance.

JAX system: a just-in-time compiler which generates code for PSC subroutines via high-level tracing with XLA compiler infrastructure. Tracing is implemented in user-level code. 
Primitives consist Numpy's numerical functions, Autograd's functions. 
XLA: array-level program optimisation and code generation.
JAX provides a mean of staging out new kernels from existing ones.
