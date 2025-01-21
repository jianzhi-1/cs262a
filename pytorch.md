# What is the problem being solved?

The creation of a machine learning library that is both efficient (high throughput), easy-to-use for the research community (easy to debug, trace, fast iteration i.e. low-to-no compilation time), inter-operable (can be used with other visualisation libraries) and flexible (can deal with architectures that take in variable length inputs such as RNN and support branching).

# How was this problem solved previously?

There is a class of define-then-run frameworks (TensorFlow, Caffe etc) which first creates a static dataflow graph, then runs data through it. This approach is fast but not flexible (difficult to support variable length input and conditionals); also hard to debug. There already exist define-by-run frameworks (Chainer, Torch, DyNet) but the paper says they are either slow (low throughput) or less expressive (not as flexible; can't support as many architectures).

# What is the main idea?


# What are the key results?


# What are the main limitations of this paper?

PyTorch supports research-style development of machine learning models. To productionise, still need one more step of optimisation (they mentioned PyTorch JIT compiler).

# Why did this paper have an impact?

Supports the research community. Alignment of goals (speed, easy to debug, faster iteration, Pythonic). Easy to extend upon (Pythonic).

