# Journalling File System

### What is the problem being solved?

Improving the UNIX file system, in particular increasing throughput rates and interoperability (with hardware and storage devices). This supports applications such as VLSI design and image processing, which requires high throughput from the file system (memory-bound rather than compute bound).

### How was this problem solved previously?

UNIX's original file system has no explicit structure for how data should be placed on the disk, except that inode should be placed separately from data, which necessitates a long seek from a file's inode to its data. There's no explicit structure for the arrangement of inodes either, necessitating several non-consecutive blocks of inodes to be read when performing operations on files in a single directory. Also, there's no explicit structure imposed on the allocation of data blocks. Each disk transaction transfers no more than 512B (too small) and often needs to perform a seek again due to non-contiguous blocks. Everything limits throughput.

A previous effort increased the block size from 512B to 1024B, which improved throughput. However, it was still plagued by the fragmentation problem.

### What is the main idea?

There were 3 ways. Firstly, the minimum size of file system block is 4096B. Furthermore, a block can be divided into smaller units called fragments, so as to cater to both large and small files; small files are those with size < 4096B. This improves storage utilisation and increases throughput.

Secondly, the file system now can be parametrised by processor capabilities and mass sorage characteristics, so that blocks can be allocated in an optimal configuration dependent way (speed of processor, hardware support for mass storage transfers, characteristics of mass storage devices). This allows the file system to adapt with changing disk technology.

Lastly, To increase throughput, policies (3.3) were devised to allocate inodes and data blocks. For example, inodes of files in a single directory were generally placed in the same cylinder group (up to some limit) and data blocks for a file were also generally placed in the same cylinder group (up to some limit). In essence, the blocks were better arranged on the disk, which increase locality of reference and minimises seek latency. 

### What are the key results?

Both the read and write bandwidth were up to 10 times more than the old UNIX file system.

### What are the main limitations of this paper?

Some additional techniques were mentioned and not implemented due to design and principle considerations, such as eliminating memory to memory copies by aligning buffers, chaining kernel buffers, and batch preallocation.

### Why did this paper have an impact?

The proposed changes were implemented and they worked very well - the optimisations gave a very massive performance improvement (10x). This enabled the file system to support many downstream applications.
