# Invariant Confluence (2014)

### What is the problem being solved?

A formalism of when coordination is necessary to maintain application-level correctness (i.e. identifying safe, coordination-free execution), then using them to minimise coordination when it is not necessary to maintain application-level correctness.

### How was this problem solved previously?

Previously, programmers choose between a wide range of database concurrency control policies, such as serialisable isolation (guarantees correctness, but is often conservative and lowers scalability) and other ad-hoc analyses.

### What is the main idea?

The paper sets out to minimise the amount of coordinatino required to correctly execute an application's transaction by seeking a higher-level specification of correctness (beyond the usual read-write condition for serialisation). The authors defined a property called invariant confluence which captures the potential scalability and availability of an application (independent of database implication). I understand it as: given a collection of transactions, the set of reachable (applying the transactions in any order) DB states is closed (still satisfies the invariants laid out). The property depends on a combination of the application transactions (transitions between states) and invariants (specified by the programmer), and hence is a higher-level condition than concurrent read-writes.

### What are the key results?

The invariant confluence property is proven to be a necessary and sufficient condition for whether an application requires coordination for correct execution. Hence it provides a basis for coordination avoidance: use coordination only when necessary. It provides guidelines for application designers who can impose or take out invariants/operations.

The authors demonstrated that the invariant confluence property covers a wide range of applications: relations (equality, uniqueness, foreign keys etc...) It yielded 25 fold improvement over prior methods (2PL) in the TPC-C (the gold-standard benchmark for database concurrency control) - large performance gain.

### What are the main limitations of this paper?

The programmer must specify the correctness criteria for the application. Beyond the standard basic blocks of databases (e.g. primary key...), the checking that application transactions and specified invariants are invariant confluent feels nontrivial. I believe the complexity for is harder than it seems. It might only be worthwhile if the application from a database-specific company.

### Why did this paper have an impact?

It highlights the importance that "safe but judicious use of coordination can have meaningful positive effect on performance" (6.2), specifically scaling gracefully and large number of transactions per second. Also, the definition of invariant confluence comprises of many basic blocks of databases (primary key, uniqueness, foreign key, row-level check constraints) (1) so the optimisations of each will have huge performance gains. 



