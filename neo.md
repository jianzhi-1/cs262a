# Neo (2019)

### What is the problem being solved?

End-to-end query optimisation with deep reinforcement learning techniques.

### How was this problem solved previously?

Leo, learns from its mistakes by adjusting its cardinality estimations over time. Still requires a human-engineered cost model, a hand-picked search strategy, and a lot of developer-tuned heuristics. Only improves its cardinality estimation model. Cannot optimiser its search straegy based on data. 

DQ, ReJOIN use RL combined with traditional human-engineered cost models to automatically learn search strategies and explore the space of possible join orderings


### What is the main idea?

Given a set of query rewrite rules to ensure semantic correctness, Neo learns to make decisions about join order, operator, index selection. Neo optimisers these deicisons using reinforcement learning, tailoring itself to the user;s database instance and basing its decision on actual query altency.

Takes in a partial query plan, predicts the best expected runtime that could result from completing this partial plan. Neo uses its value network to perform a simple search over the query plan space to make decisions. Value-iteration until policy converged.

Inductive bias to capture tree-structured query plans: tree convolution. Row vectors as features to represent the query prediate semantics automatically by using data from the underlying database. Learning from demonstration to overcome sample inefficiency.


### What are the key results?

End-to-end reinforcement learning system capable of building query execution plans. Generalises to unseen queries.

Achieves similar or improved performance compared to state-of-the-art commercial optimisers (ORacle and Microsoft) on their own query execution engines. 

### What are the main limitations of this paper?

Requires a priori knowledge about query rewrite rules to guarantee correctness. Restrict Neo to select-project-equijoin-aggregate queries. Optiiser does not yet generalise from one database to another. Features are specific to a schema. Neo generalise to unseen queries, but not across databases (e.g. different schema). Still requires a tradiitonal query optimiser to bootstrap its learning process.

### Why did this paper have an impact?

Produces query plans that beat state-of-the-art database query optimisers when executed in their own engine.

I wonder if Neo is actually used? If not, why? It seems only to be a demonstration of ideas.


### Own Notes

- Traditional query optimiser: cardinalityh estimation, cost model, plan search algorithm
- QEP: query execution plan
