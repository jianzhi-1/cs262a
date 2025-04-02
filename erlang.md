# Erlang (2003)

### What is the problem being solved?

The central problem is the problem of constructing reliable, fault-tolerant software systems from programs which may themselves contain software errors. To construct the required reliable systems, more requirements are imposed on the programming language. The practical problem is to find better ways of programming Telecom applications (in particular, telecoms switching systems), which are large programs with several requirements (concurrency, soft real-time, distributed, ...) which will contain many software errors despite testing efforts.

### How was this problem solved previously?

Many other programming languages do not satisfy key requirements for a robust system. For example, Java does not have the ability to isolate software components from each other without degrading performance (2.10), which renders it unable to limit the consequence of software errors which can spread outside the boundary of a particular process (3.1).

### What is the main idea?

A new programming language Erlang (a pure message-passing, concurrent process-based language) and a design methodology and a set of libraries for building robust systems (OTP). Erlang is a concurrent oriented langauge (i.e. concurrency is provided by Erlang). Everything in Erlang is a fail-fast process and processes are strongly isolated (to limit the consequence of an error) and only communicate via message passing.

At the system level, software is organised into a hierarchy of tasks (2.3). To deal with errors, the general philosophy is just for a process to fail fast and let some other process do the error recovery (4.3).

### What are the key results?

The author identified principles and abstractions for building fault-tolerant software systems, such as isolation and fail-fast processees. The author and team also implemented Erlang and its library modules, which a number of large commercially successful products use (e.g. Ericsson product (AXD301), which was even branded as the "most reliable" Ericsson product).

### What are the main limitations of this paper?

The limitation at that point in time is probably the prevalence of the assumption that it is okay for programs to contain internal software errors (which I assume to be low). Hence, the principles are unlikely to apply to other sectors.

### Why did this paper have an impact?
It appeals to the (niche) applications such as telecommunication, banking and messaging due to its fault tolerance properties and support for high concurrency. It probably dominated those markets. Some of its principles could even extend to the LLM era, where programs can contain software (logical) errors and require fixing.

### Own Notes
- Assumptions: large programs which will contain errors. Want to find ways to build reliable systems despite such errors -> new programming language.
- Client-server model: a central server and an arbitrary number of clients. Generally used for resource management operations.
