# FSCQ (2016)

### What is the problem being solved?

The problem is to firstly create a formalism for the security guarantees that should be provided by a file system and secondly create a file system whose implementation can be proved to meet its specification.

### How was this problem solved previously?

Previous approaches include separating the system into separate abstraction layers, each with its own domain-specific language. However, that did not incorporate the idea of crash conditions, which must be inside the formalism to prove the idempotence of log recovery. Another approach was to consider execution traces, but that is suboptimal since execution traces include the order of operations, but the order was not the minimal statistic for security guarantees.

### What is the main idea?

The main idea is to adapt the traditional Hoare logic to file systems by injecting a crash condition, a recovery procedure, and logical address spaces for specifying disk states. By drawing from the theorems of Hoare (with some work incorporating the extensions), one can guarantee that under any sequence of crashes, the file system will act correctly without losing data. The formalism also allows for automatic proof checker, which is helpful since it is tested against a (massive) file system codebase and reduces proving efforts for developers.

### What are the key results?

The FSCQ file system is specified, developed, and proved. FSCQ was tested against a set of applications such as git clone, make etc. It has a larger running time than its other counterparts (ext4, xv6), but by less than an order of magnitude. The authors also showed how FSCQ guarantees tackle the top bugs faced by real-world file systems.

### What are the main limitations of this paper?

FSCQ is not as complete and high-performance compared to its counterparts (albeit with much less security guarantees). Even though the authors claimed that FSCQ can be improved incrementally, it is unclear whether the security guarantees and nice formalism is worth the final performance tradeoff.

### Why did this paper have an impact?

FSCQ is the first file system with a machine-checkable proof that its implementation meets its specification and whose specification includes crashes. FSCQ provably avoids bugs (which can have unpredictable downstream behaviours) that plague the previous file systems. 

