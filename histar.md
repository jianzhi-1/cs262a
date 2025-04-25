# HiStar (2011)

### What is the problem being solved?

The problem is to build an operating system that requires minimal amount of code to run, so that only this minimal piece of code can be verified to guarantee the security of the system. It is motivated by the many high-profile cases of security breaches due to vulnerabilities in application software. 

### How was this problem solved previously?

Previously, operating systems were monolithic and it is difficult to predict the full implications of every action by a piece of code. This makes it difficult to guarantee the security of the system. 

A previous effort is Asbestos, which is a message-passing system that provides labelling and isolation mechanisms to contain the effects of exploitable software flaws. HiStar uses labels to enforce information flow as well, but it provides system-wide security.

### What is the main idea?

The main idea is to construct a new operating system to minimise the amount of code that must be trusted. This is achieved by providing strict information flow control without superuser privilege. Furthermore, all OS abstractions are built on top of six kernel object types: threads, address spaces, segments, gates, containers, devices. Each object has a label that controls information flow to and from the object. This enforces the information flow and hence allows the kernel to be of a small size (the root of the SCC).

### What are the key results?

The size of the trusted kernel code is less than 16,000 lines, which is much easier to verify. HiStar performs competitively with Linux and OpenBSD with respect to several microbenchmarks: LFS small-file, LFS big-file, IPC, and fork/exec. The latency of HiStar was similar to its counterparts except for fork() and exec() (Figure 12). HiStar also has comparable application/network performance (wget, ClamAV) (Figure 13).

### What are the main limitations of this paper?

HiStar lacks several useful features because they cannot coexist with the strict information flow control (e.g. lack of file access times). Some semantics, such as the familiar chmod, chown, chgrp, are changed. On the securities side, the HiStar system seems to be still susceptible to timing side-channel attacks (9).

Another side note is that bugs can still occur (3.2).

### Why did this paper have an impact?

HiStar is a UNIX-like system, appealing to familiarity. It also supports downstream applications such as an entirely untrusted login process, separation of data between virtual private networksm and privacy-preserving, untrusted virus scanners. 
