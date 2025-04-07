# Tensorflow (2016)

### What is the problem being solved?
Experimenting with machine learning models, training them on large dataset and moving them into production. Large-sclae training and inference. Efficiently scales to x GPUs, runs models on y devices. Flexible in model and system optimisations.


### How was this problem solved previously?

DistBelief was the distributed system for training neural networks prior to Tensorflow. However, it was not flexible enough in terms of defining new layers (e.g. attention modules), swapping optimisation methods (due to the parameter server interface), and testing training algorithms that fall outside the traditional forward-pass-then-backward-pass scheme (e.g. RNN, GAN, Deep-RL). It is also designed with a single platform in mind, instead of environment-independent (required for open source).



### What is the main idea?

Create a machine learning system that operates at large scale and in heterogeneous environments.

Use dataflow graphs to represent computation, shared state, operations that mutate the state. Data (tensors) flow from vertex to vertex. Each vertex represents a unit of local computation (operations). An operation can have mutable states that can be shared across executions of the graph. Dataflow graphs are constructed by a high-level scripting language for easy experimentation. Maps nodes of a dataflow graph across many devices. Enforcing a common abstraction for heterogeneous accelerators.

Eac operation resides on a device. A device is responsible for executing a kernel for each operation assigned to it. -> great flexibility in how operations in dataflow graph are mapped to devices.

Supports more complex architectures via dynamic control flow.



### What are the key results?

Supports a variety of applications, training and inference on deep neural networks.

Performance of TensorFlow was evaluated on several benchmarks and workloads.

Reasonable throughput for training image classification models and language models. Added backup workers to mitigate tail latency.



### What are the main limitations of this paper?

Did not beat Neon - could have optimised individual operations but chose not to (orthogonal).

The static dataflow graph is still not the best representation (deep RL). Calls for dynamic computational graph. Lost to PyTorch.

### Why did this paper have an impact?

Open-source project, widely used in the machine learning research. Legacy - many existing libraries and Google's ML work are done in TensorFlow.

### Own Notes:
Parameter server architecture: https://www.cs.cmu.edu/~muli/file/parameter_server_osdi14.pdf

