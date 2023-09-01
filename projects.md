---
layout: page
title: Projects
description: EECS 700 Projects
nav_order: 5
---

# Project Ideas

Here are some project ideas, roughly in the order of increasing difficulty / scope. For all projects that involve applying program synthesis to a new application area, the default recommendation is to use an existing synthesis framework such as:

* [Sketch](https://people.csail.mit.edu/asolar/)
* [Rosette](https://emina.github.io/rosette/)
* [PROSE](https://www.microsoft.com/en-us/research/project/prose-framework/)
* [Absynthe](https://github.com/ngsankha/absynthe)

You can also implement a synthesizer from scratch if you feel up to task. Please talk to me before finalizing your project topic. A list of papers that have applied program synthesis to other areas is given in [Synthesis + X](../synx/).

* Reproduce any experimental results from the papers we read in class or from the [reading list](../readings).
* **CEGIS:** Re-impement a symbolic program synthesizer based on a CEGIS loop. Your synthesizer must accept input in the [SyGuS](https://sygus.org/) format.
* **SemGuS:** Build a [SemGuS](https://www.semgus.org/) solver. You can try to adapt any papers for SyGuS to SemGuS or build on top of the existing solvers. You can also contribute domain specific benchmarks in the SemGuS format and build a solver only for that domain. Some algorithms to target [FrAngel](https://arxiv.org/abs/1811.05175), Markov Chain Monte Carlo, symbolic solvers, neural solvers, and advanced enumeration techniques. Some concrete ideas:
  * Use inductive relations and random testing library like QuickChick to synthesize SemGuS programs.
  * Use unrealizability proofs to accelerate search to candidate solutions.
* **Extend [RbSyn](https://github.com/ngsankha/rbsyn/):** RbSyn is a synthesizer we developed to synthesize Ruby programs with side effects. There are exciting opportunities to extending this work:
  * **Synthesize loops:** There has been past work on synthesizing programs given some loop invariant (or inferring the loop invariant). However, this is about synthesizing programs that can use the higher order combinators like map, reduce, filter, etc. (potentially without built-in knowledge of what [constraints to use](https://dl.acm.org/doi/abs/10.1145/2813885.2737977)).
  * **Synthesize resource safe programs:** A capability system can be potentially included in RbSyn to synthesize programs that are always resource-safe, i.e., always closes files after using, closes sockets after network I/O is done, etc.
  * **Integrate with LLM:** Ruby has a large amount of publicly available code on Github, thus allowing large language models to generate almost correct code. The goal would to find novel ways to integrate LLM in the program generation part while still maintaining correctness.
* **Extend [Absynthe](https://github.com/ngsankha/absynthe/):** Absynthe is a synthesizer we developed to synthesize programs in any target language by writing only abstract interpreter for a domain and combining it with testing. Potential ways to build on this work:
  * Think of ways you can reason about programs in a particular domain (eg: fairness, differential privacy, effects, etc.) and try to encode that domain as an abstract interpretation. Evaluate how Absynthe works on synthesizing example programs from that domain.
  * Absynthe only considers programs that it can automatically prove are sound with respect to the abstract domain. However, due to approximations there maybe programs that are correct but never considered in the search. Can feedback be taken from testing to see where Absynthe lost precision in the abstract interpretation?
* **Synthesis of recursive functions with [egg](https://egraphs-good.github.io/):** There is interesting [recent work](https://dl.acm.org/doi/10.1145/3434335) on combining top-down and bottom-up enumeration to synthesize recursive functions. The goal of this project would be to re-implement their techniques using e-graphs and the efficient egg library. There is also potential to do some interesting work involving synthesizing [optimized Datalog queries](https://arxiv.org/abs/2202.10390) or [optimizing quantum circuits](https://arxiv.org/abs/2211.09691).
* **Synthesis with ASP:** There is some [recent work](https://mgree.github.io/papers/2023popl_asp.pdf) on using Answer-Set Programming (ASP) to synthesize Datalog programs. The goal of this project would be to apply ASP to a different relational domain, e.g. synthesizing context-free grammars (or tree grammars). You can think of other domains where relational reasoning can be used.
* [Scallop](https://scallop-lang.github.io/) is a language that allows programmers to write a rules in a declarative language and combine it with a neural network to jointly enable probabilistic reasoning. Can it be scaled up to synthesize programs with respect to some specification? 
* **ARC:** Implement a synthesizer that solves (a simple subset of) tasks from the [Abstraction and Reasoning Challenge](https://www.kaggle.com/c/abstraction-and-reasoning-challenge).
