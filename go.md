# Go (2012)

### What is the problem being solved?

The problem being solved is developing a language that supports software engineering at scale (i.e. many humans working on a codebase, the need for shorter compilation time = "slowness", the need to catch more human errors = "clumsiness", familiarity) with the modern computing environment. 

The list of pain points in the article are: slow builds, uncontrolled dependencies, using a subset of language by a programmer, poorly documented program, duplication of effort, cost of updates, version skew, difficulty of writing automatic tools, cross-language builds (4).

### How was this problem solved previously?

Previous programming languages such as C, C++, Java were used and the pain points were simply just accepted/worked around individually.

### What is the main idea?
The main idea is to create a new language that is compiled, concurrent, garbage-collected, and statically typed. Each of the pain points were tackled through the same language. For example, unused dependencies are raised as compile-time errors. The grammar is regular and is kept modest at 25 key words, compared to C (37) and C++ (84).

### What are the key results?

Compilation times are faster than C and C++ by 50x. Tools are easily built around the library, with Gofmt library being used to format code to maintain uniformness. There were optimisations over previous garbage-collected languages (e.g. Java), such as the support interior pointers.

### What are the main limitations of this paper?

As the paper mentioned, there is no breakthrough. Go exists as an engineering tool, and all of its features already exist in some form in traditional programming languages. 

Go sacrifices convenience for safety and dependability (e.g. enforced garbage collection, lack of exceptions, no default arguments and brace-bounded blocks - why are people so against this semantic anyways?). This may irk some people.

### Why did this paper have an impact?

From an organisation perspective, it probably saved a lot of developer time and people be more production (and can work more). It got rid of the excuse "I'm waiting for the code to compile". Also, it is open-sourced and backed by Google.

### Notes
CSP: communicating sequential processes, a formal language for describing patterns of interaction in concurrent systems. Can be throught of as an add-on feature to a programming language.

Interior pointer: a pointer to struct's field to keep the entire struct from being garbage collected.

