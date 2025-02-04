# Turing (1936)

### Strength and Weakness

Strength: Turing's formalism of conditions, symbol, finite state automata, machine configuration (m-configuration), skeleton tables are very ahead of his time and spans a huge portion of the modern stack. They correspond to branches, PC, transitions by modifying PC and memory, initial set of registers and memory, boolean logic in FPGA. Turing also made several comments on the tradeoffs between the symbol set and number of microinstructions "an apparent need of more E-squares can be satisfied by having a sufficiently rich variety of symbols capable of being printed on E-squares" (end of Section 3). I also think that the alternating E and F squares at that time is quite intelligent (not in today's world of course due to cache locality).

Weaknesses: Maybe Turing's time does not have proper tables; some borders would be very helpful. I also think he went overboard with the abstractions in the skeleton table (skeleton table is fine, but not compound operations). The distinction between standard description and description number is not well understood by me either - they seem the same to me. If so, maybe Turing doesn't need to define both of them.


### Comments

My understanding of skeleton tables is that it is an interface for multiple machines which implement different sets of symbols, therefore helping in interoperability. I think it also helps in clumping transition logics together (like routing table in routers, FPGA boolean optimisations etc). I struggled to understand the last example of section 4 (mainly not sure what Turing was trying to demonstrate there and also the absence of borders made it difficult) and section 5.

### Discussion Questions

- What is the difference between standard description and description number? Why is there a need to define both?
- Why is it meaningful to define compound symbols e.g. f(f(a, b, c), b, c)? Is the interface even useful at this point?

### Idea

Explore c-machine (choice motion) where next state is only partially determined by configuration. Set aside some bits for maybe 2 branches?

