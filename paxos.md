# What is the problem being solved?

An algorithm to ensure that multiple nodes/processes agree on the same value eventually in spite of partial or network failures (but not corruption). This allows the implementation of "a fault-tolerant distributed system" (1).

# How was this problem solved previously?



# What is the main idea?



# What are the key results?

Disregarding rare events (e.g. failure of leader, system start up), Paxos consensus algorithm is optimal (minimum possible cost). Safety is prioritied: two nodes will "never disagree on the value chosen" (11).

# What are the main limitations of this paper?

Points that are unclear during the paper: nodes are supposed to be aware of one another's role (e.g. a proposer must be able to send to group of acceptors and know the total number of acceptors to ascertain majority). Worst case scenario is no progress: when a signle leader cannot be elected.

# Why did this paper have an impact?

Paxos can be regarded as a fundamental building block in many distributed applications.
