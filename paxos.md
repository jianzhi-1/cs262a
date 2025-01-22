# What is the problem being solved?

An algorithm to ensure that multiple nodes/processes agree on the same value eventually in spite of partial or network failures (but not corruption). This allows the implementation of "a fault-tolerant distributed system" (1).

# How was this problem solved previously?



# What is the main idea?

Split the nodes into two classes: proposers and acceptors. Proposers first send a prepare message with a unique ID _n_. Acceptors EITHER does not respond at all OR respond with a promise not to accept any proposals less than that and with the highest value _v_ it has accepted. Proposer then sends _(n, max v)_. Essentially, monotonicity is preserved in both first and second argument. After this procedure when a value is finally chosen (i.e. accepted by a majority of the acceptors), a distinguished acceptor will relay this message to everyone. 

# What are the key results?

Disregarding rare events (e.g. failure of leader, system start up), Paxos consensus algorithm is optimal (minimum possible cost). Safety is prioritied: two nodes will "never disagree on the value chosen" (11).

# What are the main limitations of this paper?

Points that are unclear during the paper: nodes are supposed to be aware of one another's role (e.g. a proposer must be able to send to group of acceptors and know the total number of acceptors to ascertain majority). Worst case scenario is no progress: when a single leader cannot be elected. Costly to select a single proposal - need randomisation or timeout.

Could there be interference during the learning phase and the proposing phase?

# Why did this paper have an impact?

Paxos can be regarded as a fundamental building block in many distributed applications.
