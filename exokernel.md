# Exokernel (1995)

### What is the problem being solved?

The problem is to improve the performance, flexibility and functionality of applications running on an operating system. This is done by breaking certain abstractions of the OS, which reduces paying extraneous overhead cost, provides more information, and improves flexibility.

### How was this problem solved previously?

Previously, OSes are general purposed (e.g. Ultrix4.2 which was used as the benchmark) i.e. they define a set of abstractions for all applications. While useful for a wide range of applications, they are inflexible and suffer in performance for performance-critical applications. This results in high latency for syscalls in particular.

### What is the main idea?

The main idea is to have a minimal kernel (the exokernel) and exports all the hardware resources (even privileged instructions etc) through a low-level interface to (a collection of) untrusted library operating systems. This allows the implementation of traditional OS abstractions at the application level (2.2) (e.g. applications do their own resource management instead of the exokernel). In particular, the virtual memory (bootstrapping) and IPC (via protected control transfer) are done at application-level. The exokernel has some ways of enforcing security via protocols. Performance gains are realised because applications have more information about their hardware resources and control their own allocation; and bypasses the kernel (e.g.they can return from their own exception without kernel intervention (5.3)).

### What are the key results?

The exokernel (Aegis) and a library operating system (ExOS) is implemented. They were benchmarked against Ultrix 4.2 (a mature monolithic system). Results showed that Aegis has very fast syscalls (protected control transfer) and exception dispatch (Table 5), at least one order of magnitude lower than Ultrix 4.2.

### What are the main limitations of this paper?

A limitation to the exokernel idea is developer time: do most application developers want the extra performance for an increased development time (due to choosing libraries, the need to properly understand low-level implementations)?

There are also limitations to the isolation function of the exokernel. For example, the abort protocol is again contending with how strict the exokernel should manage the resource. (In my view, it is no different from how a traditional OS could implement its policy.)

### Why did this paper have an impact?

The exokernel OS had a very big performance gain (one to two orders of magnitude). It also prompted the rethinking of the traditional role of operating system, especially its role as the illusionist (removes the general abstractions of the OS). It demonstrates application-specific optimisation and trades off a bit of security for large performance gains.
