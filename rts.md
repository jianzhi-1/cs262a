# Scheduler for Real-time Time-shared Systems (1996)

### What is the problem being solved?

Provide real-time support in a general purpose operating system, but in a way such that real-time and non-real-time events are less distinctly treated. Integrating real-time and non-real-time computing.

### How was this problem solved previously?

Embed a periodic thread or process model into an existing operating system kernel and to use a real-time scheduling algoirthm such as rate-monotonic scheduling to schedule the processes. Aperiodic and non-real-time activities are typically scheduled either as background processes or thorugh the use of a second-level scheduler that is executed quasi-periodically as a server process.


### What is the main idea?

Use a proportional share scheduling algorithm. The main idea is to consider a virtual time frame that is the real time frame weighted inversely by the sum of weights of all active processes (competition). Then, use EEDF on this virtual time frame.

### What are the key results?

Theoretical bounds: in a proportional share allocaation system, every process in the system is guaranteed to make progress at a well-defined uniform rate (basically within a certain fixed threshold of their guarantee) - lag is bounded and not better to achieve better bounds.

Experimental results with FreeBSD.

Fairness results.

### What are the main limitations of this paper?
I think that the computational overhead of the virtual time frame might discourage some operating systems from using this. I also wonder if modern day operating systems use this class of schedulers - because a cursory search says they still default to the typical round-robin kinds.

### Why did this paper have an impact?
Useful for general purpose operating systems that need to support a variety of real-time and non-real-time applications together. No need to search for better algorithms in this class of schedulers.

