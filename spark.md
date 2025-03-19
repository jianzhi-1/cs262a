# Spark (2010)

### What is the problem being solved?

The problem is to support the class of applications that reuse a working set of data while retraining the scalability and fault tolerance properties.

### How was this problem solved previously?

Previously, the existing frameworks are MapReduce, Dryad and Map-Reduce Merge. However, they mainly support acyclic dataflows, which do not comprise a major class of machine learning algorithms. Hadoop is used for interactive analytics, but each query invokes a new MapReduce job that reads data from disks when the data could be cached.

### What is the main idea?

The main idea is to set up a new abstraction: resilient distributed dataset (RDD). The uniqueness of this abstraction is that more controls are given to the user - the user can explicitly cache a RDD in memory. Spark also provides two types of shared variables (broadcasts and accumulators) to increase the expressivity of jobs that it encompasses.

### What are the key results?

Through 3 examples, the authors showed that Spark outperforms Hadoop on machine learning algorithms with job completion time being 10x/2.8x faster. For interactive analytics, the subsequent queries were 35x faster. They also tested Spark's resilience to failure (21% slowdown on average).

### What are the main limitations of this paper?

There are still possible improvements in the expressivity of the programs. There are also edge cases to the assumptions in the paper - what happens when the cache isn't large enough to fit all of the RDD? The integration of Spark and Mesos might require users to use Mesos as well.

### Why did this paper have an impact?

The world shifted to machine learning and data analysis workloads, so professionals need fast iteration time and queries. The caching of reused data contents saved a lot of programmer's idle time. Many data analytic tools are built on Spark.
