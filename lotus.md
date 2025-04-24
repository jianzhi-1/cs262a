# LOTUS (2024)

### What is the problem being solved?

The problem is to build systems that allows the performing of semantic queries (in natural language, which is declarative) over a large corpuses of data (e.g. database table) at scale. 

### How was this problem solved previously?

Previously, there are Retrieval Augmented Generation (RAG) methods, which are good for point lookups but not bulk processing. There was a previous effort called SUQL which provides a SQL extension to serve specialised tasks or applications, but that is limited to row-wise LLM execution. There were also LM programming models such as LangChain, but passing a table to it is infeasible.

### What is the main idea?

The main idea is to construct a query engine over the data for the purpose of reasoning about the data. This involves a new (declarative) programming model and automatic optimisations to handle structured and unstructured data together. LOTUS uses semantic (AI-based) operators for semantic queries over datasets (e.g. sorting or aggregating records using a natural language prompt). It also has three model classes to support it: a language model, a retrieval class model and a reranker class model (presumably to support the various data operations).

### What are the key results?

LOTUS's efficiency is evaluated through three diverse applications: fact-checking, extreeme multi-label classification, and search and ranking. In each of the applications, LOTUS achieves near state-of-the-art results with a few lines of code (due to its programmability) and few semantic operators (expressiveness of its programming model). For example, it improves accuracy over FacTool (factuality detection in generative AI) by 9.5%, offering 7-34x lower execution time. 

### What are the main limitations of this paper?

A possible limitation from the systems perspective is that people usually store data in a database precisely for its structure. Natural language data tends to be compressed or tensorised. In particular, the scenarios where natural language data exists in a structured table is (in my opinion) rare and thus LOTUS's use might be limited.

### Why did this paper have an impact?
LOTUS is open-sourced. It supports interesting applications with its semantic operators, such as filtering vulgarities, searching through text messages etc. It has pandas-like syntax, which is easy for the community to adopt. Furthermore, it provides telemetry capabilities, such as tracking total language model usage.
