# Scheduler for Real-time Time-shared Systems (1996)

### What is the problem being solved?

The goal is to provide real-time support in a general purpose operating system in a way such that real-time and non-real-time events are less distinctly treated and are integrated more seamlessly.

### How was this problem solved previously?

Usually, a periodic thread or process model is embedded into the operating system kernel and a real-time scheduling algorithm (such as rate-monotonic scheduling) is used to schedule the real-time processes. Aperiodic and non-real-time activities are typically scheduled either as background processes or through the use of a second-level scheduler that is executed quasi-periodically as a server process (1).

### What is the main idea?

The main idea is to consider a virtual time frame that is the real time frame weighted inversely by the sum of weights of all active processes (competition) at each particular time. Then, EEDF (quantum allocated to process which has an earliest eligible deadline) is used on this virtual time frame to get the algorithm EEVDF.

### What are the key results?

Theoretical bounds were obtained and showed that in a proportional share allocation system, every process in the system is guaranteed to make progress at a well-defined uniform rate (within a certain fixed threshold of their guarantee). Specifically, Corollary 3 showed that the service time lag (difference between the time when a process should receive service vs when it actually receives service) is bounded and asymptotically tight.

Experimental results were obtained by implementing the scheduler to schedule user-level processes in FreeBSD and showed that the scheduler behaves as intended. The number of iterations performed by each process during a particular interval of time is proportional to the competition present during that period.

### What are the main limitations of this paper?
I think that the computational overhead, in particular the updating of weights for all processes after a time interval, of the virtual time frame might discourage some operating systems from using this. I also wonder if modern day operating systems use this class of schedulers over the classical round-robin kinds.

### Why did this paper have an impact?
The scheduler is useful for general purpose operating systems that need to support a variety of real-time and non-real-time applications together. The paper also showed there is no need to search for better algorithms within this class of schedulers.

