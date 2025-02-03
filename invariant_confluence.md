# Invariant Confluence (2014)

### What is the problem being solved?

Coordination to maintain application-level consistency - when is it strictly necessary

### How was this problem solved previously?

Serialised transaction e.g. always coordinate conflicting read and write, hence always preserve application correctness at the cost of limited scalability.

Perform ad-hoc analyses (see ref)

### What is the main idea?

Defining a property called invariant confluence which captures the potential scalability and availability of an application (independent of database implication). Combination of transactiions and invariants. 

This provides a basis for coordination avoidance: use coordination only when necessary. 

In particular, an invariant confluent application can scale out without sacrificing correctness, latency or availability (6).

### What are the key results?

Formalised a necessary and sufficient condition for invariant-preserving and coordination-free execution of an application's operations. 
Demonstrated that the invariant confluence property covers a wide range of applications: relations (equality, uniqueness, foreign keys etc...)
25 fold improvement over prior results.

### What are the main limitations of this paper?

The programmer must specify the correctness criteria for the application. Beyond the standard basic blocks of databases (e.g. primary key...), the checking that application transactions and specified invariants are invariant confluent feels nontrivial. I believe the complexity for is harder than it seems. It might only be worthwhile if the application from a database-specific company.

### Why did this paper have an impact?

When applied to TPC-C (the gold-standard benchmark), it has large performance gain over 2PL. It highlights the importance that "safe but judicious use of coordination can have meaningful positive effect on performance" (6.2), specifically scaling gracefully and large number of transactions per second. Also, the definition of invariant confluence comprises of many basic blocks of databases (primary key, uniqueness, foreign key, row-level check constraints) (1) so the optimisations of each will have huge performance gains. 



