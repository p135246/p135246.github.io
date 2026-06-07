---
title:      "Infrageometry Manifesto"
categories: [Wolfram]
mathjax:    false
utterances: true
---

# Infrageometry Manifesto

Infrageometry is not just ordinary discrete geometry.
It is a foundational theory of geometry on graphs and hypergraphs, in which ordinary geometry - be it Euclidean geometry, algebraic geometry, or differential geometry - emerges as an effective description on sufficiently large graphs and at sufficiently large scales.
In the context of the [Wolfram Physics Project][WP], this emergence also depends on the class of observers along certain classes of rewriting paths.
Notions such as dimension, gauge degrees of freedom, observer independence, and relativity should arise within infrageometry as emergent phenomena, rather than being assumed from the start as in ordinary geometry.

*Note:* A graph is nothing more than a metric space with an integer-valued geodesic metric, and a hypergraph is just a graph together with a cochain on its unit Rips-Vietoris complex that is supported on cliques corresponding to hyperedges.

We do not primarily try to find a suitable graph that represents a given smooth manifold and then study to what extent it determines that manifold.
Methods of that approach would include, for example, embedding trivalent graphs into a Riemannian manifold with sufficiently short edges, all of the same length, distributed proportionally to the volume; constructing approximate unit-length embeddings of graphs in Euclidean spaces; manifold learning; and deriving bounds on coarse manifold invariants in terms of discrete invariants.
Instead, we ask what geometric theories a [computationally bounded observer][observer], with possibly limited capacity, would build about the discrete substrate it observes, which geometric notions make sense, and which properties they satisfy.
From this perspective, ordinary geometry can be seen as an idealization of macro-experience by macro-observers in the real world, and infrageometry as a renormalizable proto-geometry in Wolfram's computational universe.

Our theory is computable at every level, so we build the framework of infrageometry primarily as code.
We put significant effort into designing a language for convenient infrageometric constructions; it often leads to discovery of naturally parametrized generalizations.
Due to this computability, we can utilize computers and AI to run computational experiments and explorations.
We use robust aggregated observables, detect and classify features, enumerate all cases, and keep track of all branching and do statistics over it.
This is in contrast with ordinary geometry, where uniqueness, well-definedness, and top-down structure are a primary goal, as the people who laid the foundations hundreds of years ago could only do pen-and-paper computations and abstract arguments, so they could handle only objects carved by very specific, but brittle, assumptions.

*Note:* Already the real numbers are uncomputable and cannot be stored in finite memory.

Although we have code, we do not expect infrageometry to produce better simulations or predictions for macroscopic theories, because of [computational irreducibility][irreducibility].
We also do not aim to improve the classical discretization and reconstruction pipeline or to optimize computations with the discretized structures.
Our main goal is to build a framework and demonstrate the emergence of geometry in the Wolfram computational universe.
Assuming this is a good model of the real world, we are answering the question of why geometry appears and is so successful, and what its variants for different scales, substrates, and observers would be.

For some very early work, see:

- the [talks in Srní and Madrid][talks]
- the [Austin conference post][austin-post] (to be published soon)

I am currently developing the following repositories:

- [Infrageometry](https://github.com/WolframInstitute/Infrageometry)
- [SyntheticInfrageometry](https://github.com/WolframInstitute/SyntheticInfrageometry)
- [InfraElements](https://github.com/WolframInstitute/InfraElements)
- [InfraGaugeTheory](https://github.com/WolframInstitute/InfraGaugeTheory) (to be published soon)
- [InfraAnalysis](https://github.com/WolframInstitute/InfraAnalysis) (to be published soon)
- [InfraCausality](https://github.com/WolframInstitute/InfraCausality) (to be published soon)

This is joint work with S. Wolfram, who has laid out the main philosophical directions and wrote the [technical introduction to the WPP](https://www.wolframphysics.org/technical-introduction/limiting-behavior-and-emergent-geometry/), and with others on the [Wolfram Institute][WI] team.

[WP]: https://www.wolframphysics.org/
[talks]: /wolfram/2026/03/31/talks-infrageometry-srni-madrid.html
[austin-post]: /wolfram/2026/06/15/wolfram-models-conference-austin.html
[observer]: https://writings.stephenwolfram.com/2023/12/observer-theory/
[irreducibility]: https://www.wolframscience.com/nks/p737--computational-irreducibility/
[WI]: https://www.wolframinstitute.org/
