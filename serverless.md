# Serverless (2017)

### What is the problem being solved?

Serverless computing seems to be solving the problem of abstracting away the operational concerns (e.g. monitoring, scaling, provisioning of resources, charging for cost) away from the application/services developers.

### How was this problem solved previously?

Previous models which people have used includes Platform as a Service (PaaS), where developers use a prepackaged platform and services. People also used Infrastructure-as-a-Service (IaaS), where the developer is responsible for provisioning the hardware and virtual machines, which gives them more control but also more operational labour. Mobile Backend as a Service (MBaaS), Software as a Service are also existing approaches, but those are limited to within mobile and app platforms and not general enough.

Compared to PaaS, serverless computing is less modular (it is regarded as functions as a service FaaS) and more "lightweight labour of computation" (2).

### What is the main idea?

The main idea is to have a programming model in which the units are called serverless functions, which are generally stateless, that are executed in the cloud. This paradigm models a lot of use cases, in particular the functions can be set to respond to events (hence encompassing event-driven programming). The scaling is managed by the operator of the cloud. The cost is usually charged by execution time rather than resource allocation, which is usually more cost efficient. 

The limitations are that developers must conform to this model of programming (e.g. event-driven, function based, also a preference for compute-bound rather than I/O bound functions, decomposing functions if necessary) and cannot control certain properties of their services/applications as those are managed by the cloud (e.g. monitoring, QoS monitoring, scaling, fault-tolerance (1)).

### What are the key results?

This paper is a summary paper, so the key result is just that serverless computing, though young, already have several use cases such as event processing, API composition/aggregation, flow of data between services. In particular, it is good for "bursty, compute intensive workload" (5) due to its cost model.

### What are the main limitations of this paper?

My view is that there is not a quantitative threshold of when serverless computing is beneficial. The authors brushed this point away by saying it depends on the frequency and burstiness of the workloads, but there are several other considerations such as cold start. It is not obvious to me that serverless is strictly better without some comparison. Also, developers' time and migrating/refactoring code will be a significant barrier.

### Why did this paper have an impact?

I think this paper follows the trend of abstracting away operational concerns by making things modular on a smaller scale. Existing applications at that time probably monolithic and people are starting to move towards microservices, so this seemed like additional steps further in that direction, to entirely ease operational burdens. I also think people either like to depend on the cloud or are not too concerned about performance issues in the services which are deployed on the cloud. 
