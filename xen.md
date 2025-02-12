# Xen (2003)

### What is the problem being solved?

Host 100 virtual machine instances (operating systems) simultaneously on a single modern server, while maintaining isolation and high performance (low virtualisation overhead). Specifically, tackling the inability of hosting transient servers for short periods of time with low instantiation costs (6.2).

### How was this problem solved previously?

Previous solutions, such as VMware and Connectix, implement a full virtualisation of the underlying hardware (this was deemed unfavourable due to inflexibility - guest OS does not have information about real resources, which forbids some optimisations and techniques such as superpages and page-colouring - and the performance overhead of directly hosting unmodified x86 code). Previous methods to build a system that hosts multiple applications on a shared machine include just deploying them as processes on one OS (not performance isolated due to interactions, low level of flexibility since users' binaries must be modified to the target OS).

### What is the main idea?

The main idea is to create a hypervisor that multiplexes physical resources at the granualrity of an entire operating system (1) and provide performance isolation between them.

Xen: a x86 virtual machine monitor, allows multiple commodity operating systems to share conventional hardware in a safe and resource managed fashion, without sacrificing either performance or functionality. Idealised virtual machine abstraction, to which opering systems can be ported with minimal effort.

### What are the key results?

Allows hosting up to 100 virtual machine instances simultaneously on modern server. Considerably outperform competing commercial and freely available solutions in a range of microbenchmarks and system-wide tests. Maintains a high throughput, almost consistent with native Linux (indicating it has low overhead), and drastically outperforms existing virtualisation systems such as VMware workstation and User-Mode Linux.

### What are the main limitations of this paper?

It involved a high development effort (e.g. rewriting all the syscalls to use a lower privilege ring than the hypervisor) because it requires rewriting OS-level code, which poses tendency for errors. There is still high initialisation cost and resource consumption due to spawning OSes (as compared to process level multiplexing).

### Why did this paper have an impact?

The paper demonstrated that paravirtualisation is good for scalability and demonstrated it. Also, provided an interface which other operating systems can implement (with more development/open-source effort).


