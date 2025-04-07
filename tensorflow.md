# Tensorflow (2016)

### What is the problem being solved?
The problem is to enable large-scale training and inference of machine learning models in a way that is easy to experiment and productionise In particular, it must be flexible both in the variety of models, system optimisations, and deployment environment (i.e. efficiently scales to x GPUs, runs models on y devices). 

### How was this problem solved previously?

DistBelief was the distributed system for training neural networks at Google prior to TensorFlow. However, it was not flexible enough in terms of defining new layers (e.g. attention modules), swapping optimisation methods (due to the parameter server interface), and testing training algorithms that fall outside the traditional forward-pass-then-backward-pass scheme (e.g. RNN, GAN, Deep-RL). It is also designed with a single platform in mind, instead of environment-independent (required for deployment and open-source).

### What is the main idea?

The main idea is to use (static) dataflow graphs, where each vertex represents a unit of local computation (operations). Data (tensors) flow from vertex to vertex. An operation resides on a device and can have mutable states (stored on vertex) that can be shared across executions of the graph. A device is responsible for executing a kernel for each operation assigned to it. The static dataflow graphs allow the mapping of operations/nodes across many devices, making deployment flexible. Furthermore, a common abstraction is enforced heterogeneous accelerators.

The dataflow graphs are constructed by a high-level scripting language for easy experimentation. Also, TensorFlow supports more complex architectures (RNN) via dynamic control flow.

### What are the key results?

The performance of TensorFlow was evaluated on several benchmarks and workloads. It achieves reasonable throughput for training image classification models and language models (and included optimisations such as adding backup workers to mitigate tail latency). In the open-source world, TensorFlow supports a variety of applications, training and inference on deep neural networks.

### What are the main limitations of this paper?

The main limitation is that the static dataflow graph, even with dynamic control flow, is still not the best structure for deep neural network experimentation, such as those required by deep RL. Dynamic computational graphs are more useful, and in this sense, I think TensorFlow lost to PyTorch.

Another mini-limitation is that TensorFlow's evaluation section is not very convincing. It did not beat Neon, even though it should have optimised the individual operations to do so (orthogonal).

### Why did this paper have an impact?

TensorFlow is an open-source project and is widely used in the machine learning research. It also has a lasting legacy - many existing libraries and Google's ML work were done in TensorFlow.

### Own Notes:
Parameter server architecture: https://www.cs.cmu.edu/~muli/file/parameter_server_osdi14.pdf

