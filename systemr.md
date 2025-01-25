# System R

### What is the problem being solved?

Creating a database system that supports many concurrent users who are performing a mixture of one-time and scripted transactions. This includes having a user interface and locking ability. The other key goal was recovery. Lastly, to compare this system with "lower-function database systems".

### How was this problem solved previously?

It was the first of its kind. The previous technology was XRM, which was single-user without locking or recovery capabilities. It was inferred from the phrase "lower-function database systems" that users would previously specify the exact methodology for retrieving the entries that they want via scripts.

### What is the main idea?

System R achieved the goal by following the design principle of data independence. Firstly, System R decouples the user application from the system and storage (how the data are stored and how the system extracts the rows). This is done by employing the declarative SQL language (as compared to an imperative language) and separating modules RSS (access method, locking, logging) and RDS (query optimiser). The nature of SQL also allowed for an elegant compiler that is also practically efficient and can be uniformly used across ad-hoc and scripted transactions. Secondly, System R used a hierarchical locking system (still used today) and shadow pages for recovery (they noted its slowness and proposed write-ahead logging, which is mainstream today).

### What are the key results?

The project was implemented in a few phases with feedback collected at the end of each phase. The key result from Phase Zero is to use a weighted combination of CPU time (due to CPU-bound nature of query processing) and the number of I/Os as the metric. For Phase Two (the evaluation of Phase One), users were "enthusiastic" (639) and "satisfied" and offered new language features to SQL. The query optimiser was tested for validity with realised metrics and gave the same order of rankings. A "convoy phenomenon" was identified (essentially due to the interaction between OS and DB application scheduling and thus the interference of the scheduler on the hierarchical locking system).

### What are the main limitations of this paper?

The paper offers a lot, more than what one would expect for a normal paper (it is wonderful they actually managed to create the entire system stack while innovating on almost every aspect, but I am not convinced that it was realistic from the outset). The authors did not do any comparisons between the final Phase Two product and a "navigational" system, but I think that is understandable given the focus of System R.

### Why did this paper have an impact?

The application works and is efficient. It tries to achieve a lot of goals (recovery, multi-user, optimisation) and managed to achieve most of them very well. It maintained the data independence philosophy, which is correct for a system dealing with data. It focused on relational data and gave up certain data features such as links. The application was designed for users and many important features (views, authorisation, speed) were satisfactory to the users. 

### Own Notes

Definitions:
- Data independence: immunity of applications to change in storage structure or access strategy (referring to the high-level, declarative SQL, decoupling of it to the implementation of the query operators etc)
- System catalog: description of the content and structure of the database / schema
- CPU bound: a program is CPU bound if it becomes faster when CPU becomes faster
- Consistent: A consistent state is one in which the database does not reflect any updates made by transactions which did not complete successfully
- Canned transaction: a transaction that only access a few records
