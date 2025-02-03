# Invariant Confluence (2014)

### What is the problem being solved?

Coordination to maintain application-level consistency - when is it strictly necessary

### How was this problem solved previously?

Serialised transaction e.g. always coordinate conflicting read and write, hence always preserve application correctness at the cost of limited scalability.

Perform ad-hoc analyses (see ref)

### What is the main idea?

Defining a property called invariant confluence which captures the potential scalability and availability of an application (independent of database implication). This provides a basis for coordination avoidance: use coordination only when necessary

### What are the key results?

Formalised a necessary and sufficient condition for invariant-preserving and coordination-free execution of an application's operations. 

25 fold improvement over prior results.

### What are the main limitations of this paper?

Requires the programmer to specify the correctness criteria for the application. 

### Why did this paper have an impact?

A large performance gain. The definition comprises many basic blocks of databases (priumary key, uniqueness, foreign key, row-level check constraints) (1) so the optimisations have huge performance gains. 



