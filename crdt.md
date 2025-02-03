# CRDT (2011)

### What is the problem being solved?

Establishing a middle ground between strong consistency (enforces a global total order to all updates, which limits scalability) and eventual consistency (better availability and performance at the cost of having to do arbitration and rollback). One also needs a practical formalism of eventual consistency and design guidelines, since it is difficult to analyse in practice, leading to anomalies (1). 

### How was this problem solved previously?

Ad-hoc approaches, brittle and error-prone.
Concurrency anomalies of Amazon Shopping Cart

### What is the main idea?

The authors defined Strong Eventual Consistency as a special case of eventual consistency (updates delievered at a correct replica will eventually be delivered to all correct replica) which satisfies strong convergence (correct replicas that delivered the same updates have equivalent state i.e. query operations on them produce the same result). They then formulated two equivalent sufficiency conditions (state-based and op-based CRDT) for the strong convergence property; and they guide the design of distributed systems.


### What are the key results?

Definitions, proving of sufficiency conditions for SEC and theoretical framework. Proving certain classes of objects fall under CRDT.

### What are the main limitations of this paper?

I think the paper is a very difficult read. The authors did not define the diamond and the box symbol. There are errors in indexing and the symbols were sometimes unintuitive. I also wonder if it is really necessary to define the two equivalent conditions when one is an implementation-oriented way of expressing the other.

### Why did this paper have an impact?

The new definition comprises a sizeable amount of existing objects: such as integer vectors, counter, co-operative text editing, can be extended to sets, graphs. Many distributed databases, such as Redis and Cosmos DB, use CRDT data types (Wiki).



