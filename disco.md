# Disco (1997)

### What is the problem being solved?

The problem is to develop modern operating systems to run efficiently on scalable shared-memory multiprocessors without a massive implementation effort. In general, it is to ease the development effort of software to keep up the pace with innovations in hardware.

### How was this problem solved previously?

Previously, to deal with system software challenges of scalable shared-memory multiprocessors, one either (1) throw a large OS development effort at the problem (Hive, Hurricane, Cellular-IRIX) or (2) statically partition the machine and run multiple, independent OS that use distributed-system protocols to export a partial single-system image to the users (Sun Enterprise10000).

There were many previous efforts along the subproblems:
- Adding a software layer: IBM's VM370
- OS-structuring technique: Exokernel, Fluke, 
- CC-NUMA memory management: IBM Ace, BBN Butterfly.

### What is the main idea?

The central idea is to insert another layer of software between the hardware and operating system. This layer (called the hypervisor) allows many commodity operating systems to efficiently cooperate and share resources with each other (1). Disco virtualises all resources of the underlying hardware machine, such as memory, processors, I/O devices.

Also, it comes with optimisation techniques to reduce overheads, such as (1) coupling OSes on different VMs with communication protocols, (2) global buffer cache that is transparently shared by all the virtual machines.

### What are the key results?

A prototype system (Disco), which targets the Stanford FLASH shared-memory multiprocessor, was created.

Disco was evaluated with realistic workloads (pmake, database, raytrace) and the overhead of virtualisation is modest (3% - 16%). The authors also evaluated the overheads to be primarily caused by UTLB-MISS (TLB reload misses). The workloads pmake and RADIX were also used for scalability measures. Partitioning the workloads across 8 virtual machines lowers execution time by 37%. The authors also demonstrated their memory management policy for the multiprocessor (page migration and replication) worked.

### What are the main limitations of this paper?

The paper is too long. Also, there are some constraints on the underlying processor that can be virtualised. For example, R10000 does not support the complete virtualisation of the kernel virtual address space, requiring OS changes to enable virtualised execution on the MIPS architecture (4.1). On ccNUMA machines, efficient communication and I/O are still highly important, and adding another level of indirection adds to the overhead. There is no concept of isolation between the VMs, so it assumes that the clients are all trustworthy. There were also some difficulties faced in evaluating Disco due to the specificity of the target machine (R10000) - these should be decoupled.

### Why did this paper have an impact?

Despite the fact that the target hardware is proprietary and the authors have to keep shifting targets, this paper showed the importance of virtualisation for keeping up with hardware innovations such as the multiprocessor and managing its shared memory. The amount of code modified is kept to minimal and the performance gains are demonstrated.

