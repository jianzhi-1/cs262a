# eBPF (2024)

### What is the problem being solved?

Improving the flexibility of existing (monolithic) operating systems without giving up their benefits (isolation, security).

### How was this problem solved previously?

Previous efforts include directly bypassing the kernel or library OS to specialise the OS stack for a specific workload, at the cost of some benefits of the traditional OS (security and isolation). Other efforts rely on changing the operating environment, such as VINO, SPIN, TockOS. Scaling these is unfeasible, so they do not work well with the existing monolithic kernels.

### What is the main idea?

The main idea is to allow dynamic programming capabilities directly into monolithic kernels without the need to create a new operating environment or adjustments. This is done by loading and attaching user-written programs dynamically at designated hooks for execution. Safety is promised by a verifier engine (a static checker). Performance is guaranteed by just-in-time compilation to native machine instructions.

### What are the key results?

The key result of the paper is to explain the design and implementation of the eBPF runtime in the Linux kernel, since eBPF has already been used in general. To summarise, the flow goes: user authors eBPF program -> compile to bpf format -> verifier -> generates a file descriptor to user space -> apply hook -> ... -> clean up (4).

### What are the main limitations of this paper?

The main limitation lies with soundness and correctness of the verifier: it is difficult to ensure that the verifier itself is secure (11.3, 11.4). Also, the scalability of the verifier has also been brought into question (11.2). Therefore, the paper notes that eBPF is largely used only in trusted user model (11.5).

### Why did this paper have an impact?

eBPF is very impactful because it acts as an add-on component to an otherwise monolithic system, so there are a lot of potential applications. The add-on capability allows applications to use it for data collection and telemetry. As such, it is used in next-generation networking (optimised performance, load-balancing), observability, and security functionality. Many companies now use it.

