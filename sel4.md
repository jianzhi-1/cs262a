# seL4 (2009)

### What is the problem being solved?

The main problem is to tackle complete formal verification in a microkernel, by deriving a formal proof of its functional correctness. It is also to show that due to the size of microkernels, it is possible to guarantee the absence of bugs.

### How was this problem solved previously?

Previously, there were Secure Unix from UCLA and Provably Secure Operating System (PSOS). Those efforts found that verification were not feasible due to the state of tools at that time. Subsequently, KIT had an implementation proof for a kernel, although the kernel was assumed to be highly idealised. There were many other efforts and techniques (static analysis, model checking, shape analysis).

### What is the main idea?

The authors used an interactive, machine-assisted and machine-checked proof technique (2.3) with Isabell/HOL theorem prover. They designed a methodology, which they termed as "rapid kernel design and implementation", that comprises 3 stages: abstract specification, executable specification, C implementation; each being a refinement of the previous one. Then, the proof was constructed and verified using Hoare triples, by verifying the postconditions after preconditions and command. They also took into account interrupts and exceptions. To make their lives easier, they specifically designed the microkernel to have functionalities that are easier to verify (non-preemptable execution, except at a few interrupt-points (3.5), event-based design to minimise invariants).

### What are the key results?

The authors showed that a full, rigorous, formal verification is practical for OS microkernels with reasonable effort (2 person-year as opposed to 5 for previous efforts). The authors also listed their experience in the verification process and explained how that helped the design of the OS (such as using a non-preemptable event-based kernel, interrupt polling...) (7) without sacrificing performance.

### What are the main limitations of this paper?

I think the main limitation is its specificity to the seL4 microkernel, as opposed to a more general microkernel framework. Many OSes have been designed without verifiability in mind and I think people might be generally more concerned about verifying existing OSes than building more new ones. The success of this is also dependent on the potential of the microkernel framework.

### Why did this paper have an impact?

It redefined the "ultimate degree of trustworthiness" for an OS (7) and is currently the "world's most highly assured OS kernel", so it provides a good benchmark for performance and verifiability. It is also open-sourced. I also think that this paper would increase the attractiveness of the microkernel paradigm, since it showed microkernels are more feasible to be verified.
