# Kubernetes (2016)

### What is the problem being solved?

Examining the best practices of designing a container management system, which takes on a more application-centric perspective than a machine-centric one.

### How was this problem solved previously?

Previously, container management systems were more machine oriented with focus on the architectures and OSes of possibly inhomogeneous machines (as in datacenters). The norm is one application per machine, which led to low utilisation.

### What is the main idea?

The authors point out the trend of having application-oriented infrastructure, due to containers encapsulating the application environment, including almost all of an application's dependencies. The authors also noted the practical uses of nested containers (10) for easiness of development and robustness, composability and fine-grained resource isolation.

### What are the key results?

The result of this shift from machine to application oriented container management system meant that application developers need not worry about the details of machines and OSes (7); infrastructure can be flexibly rolled out with minimal impact on applications; telemetry can be more oriented towards applications for analysis; (4) management system can communicate more information (such as resource limits) into containers for better application metrics.

### What are the main limitations of this paper?

Containers do not completely isolate resource management: the paper pointed out that containers cannot prevent interference in resources that the operating system kernel doesn't manage (4). Also, containers might need a security layer. This means that the management system still has to deal with issues at the container-level.

There are also much inefficiencies at the configuration level and with dependency management, which take up developer time.

### Why did this paper have an impact?

Kubernetes is open-sourced. Many application developers today use containers to deploy their applications and do not worry about the underlying architecture/servers/OSes. It is also useful for datacenter workloads to achieve high utilisation. In general, the better utilisation and resource isolation properties are appreciated by the developer community.

