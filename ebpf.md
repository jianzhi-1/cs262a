# eBPF (2024)

### What is the problem being solved?

Improving the flexibility of existing (monolithic) operating systems without giving up their benefits (isolation, security).

### How was this problem solved previously?

Previous effects include directly bypassing the kernel or library OS to specialise the OS stack for a specific workload, at the cost of some benefits of the traditional OS (security and isolation). Other efforts rely on changing the operating environemnt, such as VINO, SPIN, TockOS. Scaling these is unfeasible, so they do not work well with the existing monolithic kernels.

### What is the main idea?

Allow dynamic programming capabilities directly into monolithic kernels without the need to create a new operating environment or adjustments.
Users can write programs, load them into kernel, attach them at designated hooks to begin execution -> dynamic. Safety is guaranteed by a static checker (verifier). Performance is guaranteed by just-in-time compilation to native machine instructions.

### What are the key results?



### What are the main limitations of this paper?


### Why did this paper have an impact?

