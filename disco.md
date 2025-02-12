# Disco (1997)

### What is the problem being solved?

The problem is to develop modern operating systems to run efficiently on scalable shared-memory multiprocessors without a massive implementation effort. In general, it is to ease the development effort of software to keep up the pace with innovations in hardware.

### How was this problem solved previously?

Previously, to deal with system software challenges of scalable shared-memory multiprocessors, one either (1) throw a large OS development effort at the problem (Hive, Hurricane, Cellular-IRIX) or (2) statically partition the machiene and run multiple, independent OS that use distributed-system protocols to export a partial single-system image to the users (Sun Enterprise10000).

There were many previous efforts along other axes:
- A software layer (IBM's VM370), Hypervisor system)
- OS-structuring technique: Exokernel, Fluke, 
- CC-NUMA memory management: IBM Ace, BBN Butterfly.

### What is the main idea?

Insert another layer of software between the hardware and operating system - acts like a virtual machine monitor that allows many commodity operating systems to efficiently cooperate and share resources with each other (1).

### What are the key results?

A prototype system (Disco) targeting the Stanford FLASH shared-memory multiprocessor, combines commodity operating systems. A high-performance system software base. Minimises overhead of virtual machine, enhances resource sharing. Allows OS running on different virtual machines to be coupled using standard distribute system protocols such as TCP/IP and NFS.

Simulated with realistic workloads. Overhead of virtualisation around 3% to 16% of uniprocessor workloasd. Methods to hide the NUMA-ness of the memory system, reduce execution time by 37%.

### What are the main limitations of this paper?

The paper is too long. Changes still need to be made to the hosted operating system to enable virtualised execution on the MIPS architecture. On ccNUMA machines, efficient communication and I/O are still highly important, and adding another level of indirection just adds to the overhead.

### Why did this paper have an impact?

I think it just works well. 

