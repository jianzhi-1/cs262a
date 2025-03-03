# Kubernetes (2016)

### What is the problem being solved?

Examining the best practices of designing a container management system, which takes on a more application-centric perspective than a machine-centric one.

### How was this problem solved previously?

Previously, more machine oriented (e.g. data centers). Lower utilisation. One application on one machine.

### What is the main idea?

Application-oriented infranstructure. Containers encapsulate the application environemtn _> shift management APis from machine-oriented to application oriented. Have a hermetic container image that encapsolates almost all of an application's dependeices into a package that can be deplohyed in tot the container. Nested containers (10) for easiness of development and robustness, composability and fine-grained resource isolation.

### What are the key results?

Application developers don't need to worry about the details of machines and OSes (7); infrastructure team can flexibly roll out/upgrade OSes with minimal impact on applications; telemetry more oriented towards applications, improves introspection; (4) managemnet system can communicate information into containers such as resource limits etc.

### What are the main limitations of this paper?

Tension between containers and operating system kernel in resource isolation: containers cannot prevent interference in resources that the operating system kernel doesn't manage (4); also need a security layer (4)

Configuration and dependency management.


### Why did this paper have an impact?

