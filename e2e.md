# End to End (1984)

### What is the problem being solved?

Choosing which functions should be provided by the communication subsystem vs application. Separation of functions.

### How was this problem solved previously?

Less to no guidelines.
Previously, due to poor network reliability, a more porous ... between the application and the network is helpfl (e.g. provide some assurance that everything was well). But the general increase in reliability guaranteed by technology pushes functions towards the endpoints.

As opposed the modularity design principle, where each module must be independently good/reliable. E2E displaces this to higher levels. Less specific so that applications can do their own thing, not limited by design choices at the bottom.


### What is the main idea?

Tradeoff between latency/throughput and reliability.


### What are the key results?


### What are the main limitations of this paper?


### Why did this paper have an impact?

Summarises many arguments about the design, so authors do not need to argue about it (5). Helps with designing of layered comunication protocols, criteria for assigning functions to layers. Organising layered system. 

Save a lot of engineering effort that might be targeted at something that is not focused on. Redirects engineering effort. Prevent mistakes.

A guideline that helps in application and protocol design analysis: use some care to identify the endpoints to which the argument should be applied.


