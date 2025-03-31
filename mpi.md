# MPI (1996)

### What is the problem being solved?

The problem is to create an implementation of MPI (message passing interface) that emphasises portability as the primary goal and high performance (bandwidth and latency for message-passing operations) as the secondary goal. In particular, targets must include all systems capable of supporting the message-passing model (i.e. no constraints on the target architecture).

### How was this problem solved previously?

The precursor systems were P4, Chameleon and Zipcode. MPICH leverages all these three existing efforts, but I believe MPICH improves upon these in terms of portability and standardisation. Other related efforts were focused on the workstation environment (LAM, CHIMP-MPI, Unify etc).

### What is the main idea?

MPICH was developed (CH stands for Chameleon). The main design goals are to (1) maximise the amount of code (system independent code, MPI opaque objects) that can be shared without compromising performance and (2) have a structure that guarantees portability and also incremental performance tuning (by replacing part of the shared code by platform specific code). To achieve (1), the abstract device interface (ADI) was formalised, where all MPI functions have to be implemented in terms of macros and functions that make up the ADI to ensure portability. To achieve (2), MPICH contains many implementations of the ADI.

### What are the key results?

A set of interfaces and abstractions (such as ADI = abstract device interface (4.1), channel interface (4.2)) were defined. The protocols, collective operations were laid out.

Benchmarks for performance of MPICH on various platforms (mpptest, goptest). Same order of magnitude as compared to native vendor systems (Figure 1, 2, 3, 4, 5, 6).

### What are the main limitations of this paper?

I think one limitation is that it was not clearly explained why portability is such an important criteria. It is unclear to me what would be an acceptable tradeoff of performance for portability. The figures (Figure 1, 2, 3, 4, 5, 6) show that native vendor systems outperform MPICH (not surprisingly), but I cannot judge the significance of the performance achieved.

### Why did this paper have an impact?

The MPICH effort closely tracked the development of MPI standard - it was available immediately after the release of the MPI Standard. It also came with a set of developer tools (e.g. profiling interface (5.6)). It is also a free distribution that is freely available. The paper itself documents lessons learnt along the way.

### Own Notes
- MPI: message-passing interface, includes point-to-point message passing and collective operations. Processes with separate address spaces (e.g. Unix processes) communicate with one another by sending and receiving messages).
- ADI: abstract device interface

