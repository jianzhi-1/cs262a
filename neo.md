# Neo (2019)

### What is the problem being solved?

The problem to conduct end-to-end query optimisation with deep reinforcement learning techniques, with the intent of learning a policy that beats traditional heuristics while maintaining correctness and robustness.

### How was this problem solved previously?

The traditional query optimiser is Selinger, which uses a dynamic programming approach. Then, we have a series of deep learning efforts. Firstly, we have LEO from IBM, which learns from its mistakes by adjusting its cardinality estimations over time. However, this still requires a human-engineered cost model, a hand-picked search strategy, and a lot of developer-tuned heuristics. Furthermore, it only improves its cardinality estimation model and cannot optimise its search strategy based on data. Then, we have DQ and ReJOIN which use RL combined with traditional human-engineered cost models to automatically learn search strategies and explore the space of possible join orderings. However, they focus on join orderings and are not end-to-end.

### What is the main idea?

The main idea is to construct a deep learning pipeline that does query optimisation in an end-to-end fashion. To learn from data, the query trees and plans are featurised and inductive biases are captured via tree convolution. The authors also constructed row vectors as features to represent the query predicate semantics. In the pipeline, the authors used an expert (an existing commercial database query optimiser) to conduct learning from demonstration in order to overcome sample inefficiency. Correctness is checked using a set of query rewrite rules.

During inference, Neo takes in a partial query plan, predicts the best expected runtime that could result from completing this partial plan with guidance from the deep RL network. Value-iteration is performed until policy converged.

### What are the key results?

The end result is the establishing of an end-to-end reinforcement learning system that is capable of building query execution plans that achieves equal or better performance compared to the state-of-the-art commercial optimisers (Oracle and Microsoft) on their own query execution engines (Figure 9). Furthermore, it also generalises to unseen queries (6.4).

### What are the main limitations of this paper?

Neo requires a priori knowledge about query rewrite rules to guarantee correctness (1). Also, as of writing, Neo is restricted to select-project-equijoin-aggregate queries. Then, there is a plethora of deep learning related limitations: (1) Neo does not yet generalise from one database to another. (2) Features are specific to a schema. (3) Neo still requires a traditional query optimiser to bootstrap its learning process.

### Why did this paper have an impact?

Despite all the limitations, Neo produced query plans that beat state-of-the-art database query optimisers when executed on their own engine. It maximises performance and trades off generalisability. Neo also inspired a series of efforts in creating deep versions of database components (Bao, LLMSteer).

### Own Notes

- Traditional query optimiser: cardinalityh estimation, cost model, plan search algorithm
- QEP: query execution plan
