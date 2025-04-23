# Deep Unsupervised Cardinality Estimation (2019)

### What is the problem being solved?

The problem is to do better cardinality estimation using deep learning techniques, in hope of beating the existing tools which can routinely produce up to 10^4-10^8x estimation error.

### How was this problem solved previously?

Previously, single column histograms are used for selectivity estimates (1). Then, joint approximation estimators, such as multidimensional histograms are applied (7). Various statistical models such as probabilistic relational models (PRM) allow the factorisation of joint probability distribution into univariate ones. There are also efforts from query-driven estimators.

### What is the main idea?

The main idea is to learn the multivariate distribution of the data in the database using a deep autoregressive model. The use of autoregressive models is just due to its performance in adjacent NLP and signal processing fields. From the table, batches of random tuples from T are read to train Naru. In the end, Naru produces a density estimate, given a query with equality/range predicates. Progressive sampling, akin to changing receptive field in a CNN, is used to optimise density estimation for multidimensional queries (5.1) while reducing the number of samples required.

### What are the key results?

The main contribution of the paper is the construction of a statistical estimator using deep autoregressive network and the idea of progressive sampling. Besides that, Naru was created and excelled in the extreme tail of query difficulty. In particular, it achieved single-digit multiplicative error at tail and an up to 90x accuracy improvement over existing methods when evaluated on real-world datasets (Tables 3, 4). It is also space and runtime-efficient.

### What are the main limitations of this paper?

Also, the paper focused on selectivity estimates; I think there is a huge challenge in bridging this to join cardinality estimations. It is also very hopeful to say that the end-to-end result of combining this with a learnt query optimiser will be good.

I am still not too convinced about this method. If the database is static and the data is repeatedly fed in batches to the model, could the model just remember the estimates? We are comparing this model to heuristics which have not seen the data in full before, which might be an unfair comparison. If existing heuristics can see the data, they can just cache the results. Furthermore, if the database is dynamic (schema change, periodic ingestion of data), it is unclear if the deep unsupervised models will work.

### Why did this paper have an impact?

The paper demonstrates that with the tools from the deep unsupervised learning literature, one can make a sharp improvement over existing methods. Improvements in selectivity estimates may lead to downstream improvements in query optimisers (7).
