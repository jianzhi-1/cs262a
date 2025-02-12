# Xen (2003)

### What is the problem being solved?

Host 100 virtual machine instances (operating systems) simultaneously on a single modern server, while maintaining isolation and high performance (low virtualisation overhead). Specifically, tackling the inability of hosting transient servers for short periods of time with low instantiation costs (6.2).

### How was this problem solved previously?

Previous solutions, such as VMware and Connectix, implement a full virtualisation of the underlying hardware (this was deemed unfavourable due to inflexibility - guest OS does not have information about real resources, which forbids some optimisations and techniques such as superpages and page-colouring - and the performance overhead of directly hosting unmodified x86 code). Previous methods to build a system that hosts multiple applications on a shared machine include just deploying them as processes on one OS (not performance isolated due to interactions, low level of flexibility since users' binaries must be modified to the target OS).

There was also the Denali project, which focused on a large quantity of small-scale virtual machines (not OS) and hence have different design principles.

### What is the main idea?

The main idea is to use a paravirtualisation approach where a similar, but not identical, virtual machine abstraction to the underlying hardware is presented to the guest operating system (2), with modification to the guest OS's code. This enables the hypervisor to multiplex physical resources at the granularity of an entire operating system (1) and provide performance isolation between them.

The virtual machine interface virtualises the memory, CPU, and device I/O, by delegating responsibilities between the hypervisor and the guest OSes (e.g. guest OSes allocate space for the hypervisor in memory and must allocate and manage hardware page tables; support more than 2 privilege levels). In particular, all syscalls must be modified as hypercalls. Communication is established via an event delivery mechanism. Similar to how multiple processes are created, the first domain (domain0) created at boot time can create and terminate other domains.

### What are the key results?

Xen considerably outperform competing commercial and freely available solutions in a range of microbenchmarks (PostgreSQL database, dbench, SPEC WEB99, ...) and system-wide tests (lmbench, ttop). Xen maintains a high throughput, almost consistent with native Linux, and drastically outperforms existing virtualisation systems such as VMware workstation and User-Mode Linux. Xen has a very low context switching time, file system latency. The goal of allowing the hosting up to 100 virtual machine instances simultaneously on a single server is achieved.

### What are the main limitations of this paper?

It involved a high development effort (e.g. rewriting all the syscalls to use a lower privilege ring than the hypervisor) because it requires rewriting OS-level code, which poses tendency for errors. There is still high initialisation cost and resource consumption due to spawning OSes (as compared to process level multiplexing).

### Why did this paper have an impact?

The paper demonstrated that paravirtualisation is good for scalability (of running heavy OSes) and demonstrated it. There is significant performance gains. Also, it provided an interface which other operating systems can implement (with more development/open-source effort).


