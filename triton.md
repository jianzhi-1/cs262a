# Triton (2019)

### What is the problem being solved?


### How was this problem solved previously?

Development of various domain-specific languages for DNNs e.g. polyhedral machinery, loop synthesis techniques. -> slower than vendor libraries, lack expressiveness.

Then micro-kernels: hand-writeen, tile-level intrinsics. Requires a lot of manual labour and lacks portability.

### What is the main idea?
Tile-level opeartions and optimisations. More flexibility and support for non-affine tensor indices, automatic inference of possible execution schedule that would otherwise have to be specified manually.

### What are the key results?

Triton is able to generate matrix multiplication implementations on par with cuBLAS, 3x faster than alternative domain-specific languages.


### What are the main limitations of this paper?
Increased programming efforts.

### Why did this paper have an impact?

