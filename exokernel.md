# Exokernel (1995)

### What is the problem being solved?

Applications being hurt in performance (paying extraneous overhead cost, lack of information) and limited in flexibility (functionality) due to the generalistic nature of traditional operating system, which aims to provide all the features needded by all applications (2.1).

### How was this problem solved previously?



### What is the main idea?

Applications can return from their own exception without kernel intervention (5.3).

### What are the key results?

Exokernel (Aegis) and a library operating system (ExOS) is implemented.

Benchmarked against Ultrix 4.2 (a mature monolithic system). Very fast syscalls (protected control transfer) and exception dispatch (Table 5), at least one order of magnitude lower than Ultrix 4.2.


### What are the main limitations of this paper?

A limitation to the exokernel idea is developer time: do most application developers want the extra performance for an increased development time (due to choosing libraries, the need to properly understand low-level implementations)?

There are also limitations to the isolation function of the exokernel. For example, the abort protocol is again contending with how strict the exokernel should manage the resource. (In my view, it is no different from how a traditional OS could implement its policy.)

### Why did this paper have an impact?

Probably the fastest operating system model so far. Very fast procte.

Prompts rethinking the role of operating system, especially breaking the roles of illusionist.
