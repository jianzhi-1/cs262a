# Mach (1991)

### What is the problem being solved?

The problem is to address some inefficiencies of the traditional monolithic operating system. In particular, the kernel size is large and system structure knowledge/information has to be spread throughout every functionalities of the OS. This makes changing of environments and adding new system services difficult (I think of it as the environment information has to be propagated throughout the system; adding new system services require importing these knowledge even though not every piece of information is needed).

### How was this problem solved previously?

Prior to Mach, operating system architecture was monolithic in nature. Besides the fundamental functionalities (IPC, virtual memory, scheduling), it also handles device drivers, protocol stacks, file systems.

### What is the main idea?

The main idea is to have a modular design of the operating system implementation. Basically, implement the near-minimal set of functionalities of an OS (3.1) and implement the rest as "applications" (4). This design allows the near-minimal set of functionalities (such as memory object mechanism, system call mechanism...) to be "called" by the applications without modifying the kernel. This resembles the concept of microarchitecture, which implements an ISA, in computer architecture.

### What are the key results?

Firstly, several OSes have been successfully implemented in the microkernel fashion (4). Performance was measured by system calls, compilation and file system tests. Comparing 4.3BSD server on Mach 3.0 with commercial systems (SunOS 4.1, Ultrix 4.0), it was found out that the Mach system achieved comparable performances (speedup in some tests and almost equivalent performances in others) and could potentially achieve better performances through parameter tuning.

### What are the main limitations of this paper?

I think the performance gains might not sufficient to convince developers/companies to pivot to a microkernel approach. I also think the paper's purpose might be to introduce the possible design pattern, rather than convince a broad takeup of this microkernel design, since the paper focused a lot on the implementation specifics.

### Why did this paper have an impact?

It is proven commercially that Mach can achieve competitive performances and potentially achieve more. This design can also be used in constrained environments where the OS needs to be lightweight and flexible (e.g. edge devices).
