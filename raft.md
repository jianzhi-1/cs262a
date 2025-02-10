# Raft (2014)

### What is the problem being solved?

A consensus algorithm that is easier to be understood compared to Paxos and also more practical to be implemented in real systems. Essentially, enforcing more structure to a theoretically correct solution so that it is easier to be implemented in real systems.

### How was this problem solved previously?

Previous solutions are Paxos or extensions of Paxos. Those solutions that implemented Paxos were proprietary (Chubby, Spanner). Paxos is fundamentally symmetrically P2P, which made theoretical sense because one would usually not distinguish a node (e.g. a leader) so as to prevent hierarchical failures. However, because of this, Paxos became harder to understand, since there are more ways that different nodes can be inconsistent with one another. 

### What is the main idea?

The main idea is to have a leadership system, followed by a set of invariants, and a principle to keep the system independent from time (synchronisation is not necessary) and understandable. The central problem is again state machine replication, where each node has a log and state machine. Firstly, a leader is elected. Then, clients only interact the leader, and log entries flow unidirectionally from the leader to the followers. Communications take place via RPC (AppendEntry and InstallSnapshot). By the specification of the process, several invariants are maintained (Leader Append Only, Leader Completeness, Log Matching, State Machine Safety). The details are presented, such as snapshotting for log compaction (and a possible violation to the principle of strong leadership), randomised backoff for possible reelections, and cluster membership change via a two-phase process (where the intermediate phase is called joint consensus). Finally, an evaluation on the understandability of the Raft algorithm was done on university students.

### What are the key results?

The main result is a summary of a correct and safe consensus algorithm, that is easier to understand and for a system designer to build. The presentation of the paper is oriented towards a programmer who is implementing the cluster. Another result is that Raft is deemed more understandable than Paxos based on statistical tests.

### What are the main limitations of this paper?

While it is good that the evaluation of understandability was done, it felt a bit arbitrary - I felt that the growing popularity of Raft was enough evidence that it is taking off. It would also be good if the authors point out similarities between Raft and Paxos. If they are both correct consensus algorithms, what is the spectrum between these two different solutions?

### Why did this paper have an impact?

It is more understandable. It is surprising to me that Paxos took years to understand - but it seems plausible that programmers are more open to understanding a less-distributed approach (strong leader) that eliminates many edge cases for the sake of understanding, even if two solutions are both correct. Also, Raft has a number of open-source implementations, versus Paxos' more proprietary and hidden ones.



