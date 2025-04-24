# CHASE-SQL (2024)

### What is the problem being solved?

The problem is to improve the performance of LLM in Text-to-SQL tasks i.e. given a natural language prompt, transform it into a SQL query for execution by the database, such that the semantics of the natural language prompt and the SQL query are similar.

### How was this problem solved previously?

Previously, TAPAS (Google), an encoder-decoder model, and GraPPa, a masked language model, were developed to encode the tables and textual data. Other optimisations involved prompt engineering, schema linking, self-correction, self-debugging, self-consistency techniques. The (only, in my opinion) reason why CHASE-SQL came out is because it ranked first in one of the popular benchmarks, implicitly implying it has a better model.

### What is the main idea?

The authors essentially used LLMs to generate SQL candidates with a few LLM-specific tricks, such as divide-and-conquer approach to break down complex queries and chain-of-thought reasoning (on query plans) etc. Then, an agentic approach was used in which a selection agent ranks candidates by a binary selection approach, in which another LLM agent was fine-tuned specifically for this binary selection task. This pipeline allows the transformation of a NL prompt into a reasonably good SQL statement for execution. The authors also claimed that this pipeline promotes query diversity.

### What are the key results?

CHASE-SQL was evaluated on BIRD and Spider (two cross-domain datasets) and the execution accuracy was used as the metric. CHASE-SQL with Gemini 1.5 pro achieved 73.0% accuracy on the BIRD holdout test, outperforming the previous record by Distillery (67.21%). It did not beat the state-of-the-art in the Spider dataset, but the authors commented that that was due to lack of specific training with the dataset beforehand.

### What are the main limitations of this paper?

I think the main limitation of the paper is that it seemed like a bag of LLM tricks i.e. it picked a set of LLM optimisations from LLM research literature and applied it to the Text-to-SQL problem. It also did not convincing beat one of the benchmarks (Table 2, R), even though the authors could have easily trained CHASE-SQL to ensure it can be compared similarly to the rest of the methods.

### Why did this paper have an impact?

It beat the record in one of the popular benchmarks by around 6%, which is relatively large. It also documents an experience combining a set of LLM optimisation techniques together to solve an important problem.
