# FFS

### What is the problem being solved?

Improving the UNIX file system, in particular increasing throughput rates and interoperability. This supports applications such as VLSI design and image processing, which requires high throughput from the file system (memory-bound rather than compute bound). Also, some enhancements (advisory locks on files, extensions of the name space across filee systems, ability to use long file names, quotas) to the programmers' interface are implemented.

### How was this problem solved previously?

UNIX's original file system has no explicit structure for how data should be placed on the disk, except that inode should be placed separately from data. This necessitates a long seek from a file's inode to its data. Also, there's no explicit structure for the arrangement of inodes either, necessitating several non-consecutive blocks of inodes to be read when performing operations on files in a single directory. ALso, there's no explicit structure imposed on the allocation of data blocks. Each disk transaction transfers no more than 512B (too small) and often needs to perform a seek again due to non-contiguous blocks.

Some previous efforts include increasing block size from 512B to 1024B, which improved performance. However, it was still plagued by the fragmentation problem.

### What is the main idea?

Parametrise processor capabilities and mass sorage characteristics so that blocks can be allocated in an optimuum configuration dependent way (speed of processor, hardware support for mass storage transfers, characteristics of mass storage devices). 

Layout policies i.e. blocks of files are better ordered on disk. 

The main idea is to cluster data that is sequentially accessed and provide two block sizes to allow fast access to large files while not wasting large amounts of space for small files.

Minimum size of file system block is 4096B. Cater to both large and small files; small files are those with size < 4096B. By dividing a block into smaller units called fragments.

### What are the key results?

Both the read and write bandwidth were up to 10 times faster than the old UNIX file system.

### What are the main limitations of this paper?

Limited by memory to memory copies. Batching up allocation was not implemented.

### Why did this paper have an impact?

Its optimisations gave a very massive performance improvement (10x). Support many applications.
