# Xen (2003)

### What is the problem being solved?

Developing modern operating systems to run efficiently on scalable shared-memory multiprocessors without a massive implementation effort.

### How was this problem solved previously?

Previously, to deal with system software challenges of scalable shared-memory multiprocessors, one either (1) throw a large OS development effort at the problem (Hive, Hurricane, Cellular-IRIX) or (2) statically partition the machiene and run multiple, independent OS that use distributed-system protocols to export a partial single-system image to the users (Sun Enterprise10000).

There were many previous efforts along other axes:
- A software layer (IBM's VM370), Hypervisor system)
- OS-structuring technique: Exokernel, Fluke, 
- CC-NUMA memory management: IBM Ace, BBN Butterfly.


### What is the main idea?

Xen: a x86 virtual machine monitor, allows multiple commodity operating systems to share conventional hardware in a safe and resource managed fashion, without sacrificing either performance or functionality. Idealised virtual machine abstraction, to which opering systems can be ported with minimal effort.

### What are the key results?

Allows hosting up to 100 virtual machine instances simultaneously on modern server. Considerably outperform competing commercial and freely available solutions in a range of microbenchmarks and system-wide tests.

### What are the main limitations of this paper?


### Why did this paper have an impact?


