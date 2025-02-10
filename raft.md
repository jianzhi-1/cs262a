# Raft (2014)

### What is the problem being solved?

A consensus algorithm that is easier to be understood compared to Paxos and also more practical to be implemented in real systems. Essentially, enforcing more structure to a theoretically correct solution so that it is easier to be implemented in real systems.

### How was this problem solved previously?

Previous solutions are Paxos or extensions of Paxos. Those solutions that implemented Pxos were proprietary (Chubby, Spanner). Paxos is fundamentally symmetrically P2P, which made theoretical sense because one would usually not distinguish a node (e.g. a leader) so as to prevent hierarchical failures. However, because of this, Paxos became harder to understand, since there are more ways that different nodes can be inconsistent with one another. 

### What is the main idea?

The nodes can be classified into three classes (not necessarily disjoint): proposers, acceptors and learners. A proposer first send a prepare message with a unique ID _n_. An acceptor EITHER does not respond at all OR respond with a promise not to accept any proposals less than that and with the highest value _v_ it has accepted. The proposer then sends _(n, max v)_. Essentially, monotonicity is preserved in both first and second argument. After this procedure when a value is finally chosen (i.e. accepted by a majority of the acceptors), a distinguished learner (which all acceptors relay their accepting behaviours to) will relay this message to all other learners. 

State machine replication is achieved by treating each command in the cluster as an instance of the consensus algorithm. The proposals are what the command should be, and the outcome is that all learners learn the same command. Missing values in the sequence of commands can be treated as no-op. This ensures that all nodes execute the same sequence of transitions and hence end in the same states deterministically.

### What are the key results?

Disregarding rare events (e.g. failure of leader, system start up), Paxos consensus algorithm is optimal (phase 2 has minimum possible cost). Safety is prioritied: two nodes will "never disagree on the value chosen" (11).

### What are the main limitations of this paper?

Points that are unclear during the paper: nodes are supposed to be aware of one another's role (e.g. a proposer must be able to send to group of acceptors and know the total number of acceptors to ascertain majority). Progress is not guaranteed: might be slow (e.g. using timeout to elect the leader i.e. the distinguished proposal) and worst case is if a single leader cannot be elected. 

### Why did this paper have an impact?

Paxos can be regarded as a fundamental building block for all distributed applications. It is particularly important when durability is concerned, e.g. for databases. Many variants of Paxos were subsequently made and Raft came after Paxos. The design of Paxos was optimal in the sense the theoretical upper bound was proven (Fischer, Lynch, Patterson) and Paxos hit the upper bound.

### Own Notes

Definitions:
- Safety = consistency: two nodes will never disagree on the value chosen
- State machine replication: convert an algorithm into a fault-tolerant, distributed version
