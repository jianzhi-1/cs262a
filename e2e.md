# End to End (1984)

### What is the problem being solved?

Proposing a guideline for choosing which functions should be provided by the network (paper called it communication subsystem) and the application.

### How was this problem solved previously?

Previously, there were various guidelines spread out in different problems such as ensuring delivery, ordering of data, security of data etc, but those were not summarised into one. Also, prior to this paper, network reliability was poor, so having the network to do some additional functions such as reliability is helpful (e.g. provide some assurance that everything was well (5)). But generally, the increasing reliability of the communication subsystem eliminated this concern. Also, prior to this, the modular design principle, in which each module must be independently good and reliable, was highly favoured. 

### What is the main idea?

The proposed design is an end-to-end one, where one should push more functions from the network to the endpoints of the system, under certain conditions. The most important consideration is the application use-case (does the user retry anyways? is it mission critical? can the user tolerate delay? etc...). Following which, there are many proposed guidelines for when the E2E design should be favoured: (1) when the application has to repeat the functionality anyways; (2) when the network cannot implement the function completely anyways (since the network does not see as much information as the application); (3) when many applications are using the same communication subsystem (flexibility, availability of choice); (4) certain performance benefits such as latency = low overhead. One exception to the E2E is other performances, e.g. adding an additional layer of encryption in the network or intra-network retry for improved throughput.

### What are the key results?

The authors summarised various use cases/mistakes and how they all demonstrated the E2E design in most ways, and elucidated the application use cases and therefore the motivation for certain infringement of the E2E design.

### What are the main limitations of this paper?

The E2E is a design principle, so there is no concrete rule to follow. The paper gives a general guideline; the specifics are still left to the programmers e.g. criteria for assigning functions to layers.

### Why did this paper have an impact?

The paper summarises many arguments for the E2E design, so later authors do not need to argue for it (5) - they can just cite this paper. It saves and redirects a lot of engineering effort that might previously be targeted at redundant features in the communication system. It promotes careful thinking of the design of distributed computer system (particularly between the application and communication subsystem) and minimises mistakes. It also helps with the designing of layered comunication protocols, organising layered systems.


