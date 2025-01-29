# Semantic Block-Level Analysis and Semantic Trace Playback

### What is the problem being solved?

Establishing methods to analyse file system behaviour and evaluating file system changes
New methodology for file system benchmarking.

### How was this problem solved previously?

The previous analysis workflow was: apply synthetic or real workloads and measure the resulting performance for a sequence of file system operations. The issue is that this approach does not collect disk traffic and therefore, it was difficult to discover the reasons for the observed performance. There are no methods to evaluate improvements to the file system without simulation. 

### What is the main idea?

Use block tracing to provide insight about the internal behaviour of a file system. A stream of read and write request at the block level (block-level tracing). 

Rapid evaluation of new ideas for file systems.

Semantic block-level analysis (SBA): enables users to understand the internal behaviour and policies of the file system. allows users to understand why the file system behaves as it does. The main idea here is to insert a "pseudo-device driver" in the kernel associated with an underlying disk. When the driver passes the traffic to and from the disk, it tracks each equest and response.

semantic trace playback (STP): allows users to quantify how changing the file system will impact the performance of real workloads.

### What are the key results?

Analysis of several file systems, focusing on ext3 and ReiserFS, and proposed strengths and weaknesses. Discovered tangled synchrony problem in ext3's compound transaction implementiation (where asynchronous traffic must wait for synchronous updates to complete); discovered an extraneous wait which falsely limited parallelism (3.2.2); identified early and frequent flushing behaviour (3.2.3). Used STP to validate that fixes actually fixed the problems.

Found a variety of bugs in ReiserFS and alerted the developers.

### What are the main limitations of this paper?

SBA must be customised to the file system under test (2.1). Cannot uniformly test, must implement additionally for additional drivers. Must distinguish traffic sent to journal.

STP is suited for evaluating design alternatives under simpler benchmarks. Limited to evaluating file system changes that keep the basic operations inact (for the trace). Does not evaluate the implementation of the additional feature. (2.2)

Still requires the construction of a workload to observe specific features of the file system.

### Why did this paper have an impact?

It can be applied to all journalling file systems, does not require source code of the file system, device code can be mostly reused, and hence was applicable to finding flaws/bugs in many existing file system. After correction, I think it has less of an impact.

From a security point of view, can infer policies and parameters (2.1.1).
