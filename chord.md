# Chord (2001)

### What is the problem being solved?

The problem is efficiently and scalably locate the node that stores a particular data item in a P2P application, even in the face of node arrivals and departures.

### How was this problem solved previously?

Most previous works have poorer scaling laws as they require nodes to be aware of most other nodes in the system (i.e. O(N) states per node). Chord only requires O(log N) states per node. There exists multiple applications and work such as DNS, Freenet, Ohaha, Globe, Plaxton, Pastry, CAN which differs from Chord by guarantees, application, system model. Chord's main selling point over them is that it handles scaling very gracefully (in terms of O(log N) states and lookups, ability to handle node arrival and departure), provable correctness and no extra constraints on the network (vs CAN, which assumes each node has a fixed O(d) state invariant of network size N).

### What is the main idea?

The main idea is to follow consistent hashing literature and use a hash ring data structure to store routing information. The information at each node resembles the that stored in 2k decomposition from lowest common ancestor (LCA) problem. This ensures the operation of finding the successor of a node take O(log N). Furthermore, any node joins or leaves with complexity O((log N)^2). A stabilisation protocol is also in place to handle concurrent changes to the network. Periodic sampling is suggested to fix the network topology in case of network partitions.

### What are the key results?

Theoretical bounds were proven for each of the operations (lookup, stabilisation). The Chord protocol was simulated under various scenarios (e.g. simultaneous load failures); each operation were tested and their scaling laws were verified. The Chord protocol was also deployed on the Internet and the results again confirmed its scalablity. 

### What are the main limitations of this paper?

The main limitation is possibly the high similarity between Chord and OceanStore. OceanStore has stronger guarantees and Chord's main selling point over OceanStore is its ability to handle concurrent node joins and failures. It depends a lot on the use cases of an distributed application, whether concurrent node joins/failures are important considerations.

### Why did this paper have an impact?

Chord solves a fundamental problem. Thus, it provides a very useful primitive that is feasible for a wide range of applications: coorperative mirroring, time-shared storage, distributed indices, large-scale combinatorial search (3). 

