---
title:      Wolfram Institute Involvement
layout:     post
categories: [Math, Software]
pinned:     true
last_updated: 2026-11-15
---
# Wolfram Institute Involvement

From October 2025 to October 2026, I was a research fellow at the [Wolfram Institute](https://www.wolframinstitute.org/).
My fellowship was funded by the John Templeton Foundation through the grant [Causality, Observers and Computation: A New Approach to Fundamental Physics and Metamathematics][templeton-grant].

Working directly with [Stephen Wolfram](https://www.stephenwolfram.com/) and under his direction, I was mainly responsible for developing a discrete geometric backbone for the [Wolfram Physics Project](https://www.wolframphysics.org/) as part of the Institute's [*Infrageometry project*](https://wolframinstitute.org/research) and contributing to a post on [Stephen Wolfram's blog][WolframBlog].

The term Infrageometry was originally used by [Carlos Zapata-Carratalá](https://zapatacarratala.me/), [Jonathan Gorard](https://www.wolframphysics.org/pages/people/jonathan-gorard/), and [Utkarsh Bajaj](https://dontgetbohred.wordpress.com/) for a program to explore the expressive power of elementary hypergraph rewriting in simulating geometric constructions such as operations on vector fields and homotopies of paths, much as it can generate algebraic axioms via confluence or simulate a Turing machine. See [Arity Science](https://arity.science/findings/infrageometry/) for the development of these ideas. When I joined the Institute, a repository called [Infrageometry](https://github.com/WolframInstitute/DiscreteGeometry) had just been created by [Nik Murzin](https://community.wolfram.com/web/murzinnikolay/home). It contained clique complexes, methods from topological data analysis, and "quantum calculus" work by [Oliver Knill](https://people.math.harvard.edu/~knill/index.html).

In my initial consultations with Stephen Wolfram and Nik Murzin, I learned about the basic concepts and philosophy of Wolfram's computational universe, which is based on hypergraph rewriting implemented using [Max Piskunov](https://wolframinstitute.org/people/max-piskunov)'s [SetReplace](https://github.com/maxitg/SetReplace). Those discussions shifted the emphasis toward a more "robust" and less "exact" approach to Infrageometry that treats geometry as a macroscopic phenomenon arising from aggregation. The questions I was asked to focus on included dimension, curvature, and gauge degrees of freedom in the "limiting universe," as well as how to make sense of notions such as the Ricci tensor, covariant derivatives, the Einstein equations, and holographic duality. I was also asked to complete a dictionary of graph-based counterparts to notions from continuous geometry, which we called computational minimal models. The work was also meant to follow the paradigm of computational experimentation: write the code first and see what it does before going too deep into the theory. Hence, I set out on a journey to develop a physically and mathematically sound pipeline for reconstructing spacetime geometry for a given observer from a single history in the multiway system of hypergraph rewriting and a set of minimal models that would describe the geometry of its spatial slices and whose aggregated properties would converge to continuous notions in an "infrageometric limit," all through empirical computational exploration first.

**Important:** I now propose to keep the name ***Infrageometry*** for the original project of Carlos et al., ***Discrete Geometry*** for Nik's repository, and ***Emergent Geometry*** for the direction I was developing.

One question I asked in emergent geometry was how a computationally bounded observer perceives the geometry of a large graph. I tried to develop a simple, concrete model of such observer-dependent geometry: a discrete geometry that depends on the observer’s scale, together with a notion of renormalization under aggregation. More generally, one can ask how the perceived geometry changes when an observer has limited storage or limited computational time relative to the rate at which the underlying graph is rewritten. A related perspective appears in Utkarsh’s recent paper [Discrete geometry and de-Rham cohomology of graphs](https://arxiv.org/abs/2610.25302), which develops a mathematically rigorous notion of graph atlases whose charts can be thought of as different ways of mapping the graph.

Another direction I wanted to explore was whether Riemannian geometry, usually formulated in terms of a smooth manifold equipped with an infinitesimal metric tensor, could instead be characterized as a Gromov–Hausdorff-type limit of a sequence of graphs. These graphs could arise as spatial graphs reconstructed from the causal graph of a single rewriting history under a chosen foliation, directly from hypergraph rewriting by taking the 1-skeletons of successive hypergraphs, or, as a simpler toy model, from subdivision schemes applied to an initial graph, possibly with a given embedding. Note that the elementary objects here would always be unlabeled graphs. Vertex or edge labels would instead represent aggregated properties, and we would call theories involving them "mesoscale." One can treat the graphs as metric-measure spaces, consider coarse-graining maps between them, and ask whether appropriately scaled observables of the discrete minimal models converge weakly to observables of the corresponding geometric objects defined using infinitesimal quantities in the limit. Do these limiting observables satisfy the relations expected of the resulting continuum geometry? Such relations could take the form of **emergent PDEs**, as in [Stephen Wolfram's work on cellular automaton fluids](https://content.wolfram.com/sw-publications/2020/07/cellular-automaton-fluids-theory.pdf).

**Note:** For spatial slices, coarse-graining maps that represent the persistence of spatial constituents (which could be called effective [emes](https://writings.stephenwolfram.com/2022/03/the-physicalization-of-metamathematics-and-its-implications-for-the-foundations-of-mathematics/), borrowing Wolfram’s terminology) could potentially be derived from the causal graph, and I still hope that we can achieve a mathematically rigorous formulation of a physically sound minimal model pipeline.

So far, we have considered only graphs, which encode a binary relation of “closeness” between points. [Latschev’s theorem](https://publish.illinois.edu/ymb/files/2019/06/Latschev-2001-Vietoris-Rips-complexes-of-metric-spaces-near-a-cl.pdf) shows that, at a suitable scale, the clique complex of the closeness graph of a sufficiently dense sample of a closed Riemannian manifold recovers its homotopy type. One can then ask the broader question of whether Riemannian notions, such as geodesic structure or curvature bounds, could similarly be recovered from the discretizing graph with uniform edge lengths. I was also interested in an analogous question for symplectic geometry: Is there a discrete model of a symplectic form or a discrete analogue of the canonical one-form on a graph cotangent bundle that could give rise to the corresponding continuous structure in an appropriate limit, provided the base graph converges to a manifold?

If Riemannian and symplectic geometry can be recovered using just binary relations, what might higher-arity relations between points represent geometrically, and could they give rise to higher-order notions of geometry in the limit?

I was also interested in using observables of emergent geometry, such as dimension and curvature, to map the landscape of hypergraph rewriting systems across rules and initial conditions, and to describe how these observables are distributed across branches of multiway evolution. The broader question was whether one could infer properties of the emergent geometry directly from the rules or go the other way and identify clusters of rules that produce desired geometric properties (the "inverse problem").
This direction would fall within the Institute’s research area of [Ruliology](https://writings.stephenwolfram.com/2026/01/what-is-ruliology/).

Before my fellowship at the Institute ended, I managed to consolidate parts of this computational research in the [InfraGeometry repository](https://github.com/WolframInstitute/InfraGeometry), which forms part of the public deliverables under the Templeton grant (see the disclaimer below). The deployed Wolfram paclet documentation outlines some of the theoretical background.
This format of publication seemed better suited to communicating computational research than papers.
After his fellowship ended, Carlos also introduced an interesting alternative to papers: [Hyperiad](https://arity.science/hyperiad/notebook/), an interactive notebook format that runs Python directly in the browser, simulates the Wolfram kernel, and requires no installation.

There is more material and theoretical work that I did not manage to consolidate and may return to through our [Multihistory collaboration](https://multihistory.org/).

## Wolfram Institute repositories
{: #my-wolfram-institute-repositories }

During my time at the Institute, I started several repositories devoted to exploring the computational paradigm and the practice of computational exploration.
Here is a list of them.

**Disclaimer:** I worked on these repositories during the "AI revolution" and my own "personal revolution" in the first few months after my first child was born. Even though I tried to keep the mathematics sound and tame the constructions, there is a fair amount of vibe-coded experimental material that still needs to be [de-LLMified][de-llmification] and thought through.

- [InfraGeometry](https://github.com/WolframInstitute/InfraGeometry)
- [DiscreteGeometry](https://github.com/WolframInstitute/DiscreteGeometry)
- [SyntheticInfrageometry](https://github.com/WolframInstitute/SyntheticInfrageometry)
- [InfraElements](https://github.com/WolframInstitute/InfraElements)
- [InfraGaugeTheory](https://github.com/WolframInstitute/InfraGaugeTheory)
- [InfraAnalysis](https://github.com/WolframInstitute/InfraAnalysis)
- [InfraCausality](https://github.com/WolframInstitute/InfraCausality)
- [InfraUniverseRegistry](https://github.com/WolframInstitute/InfraUniverseRegistry)
- [PersistenceRewriting](https://github.com/WolframInstitute/PersistenceRewriting)
- [UniversalityDB](https://github.com/WolframInstitute/UniversalityDB)
- [IteratedFiniteAutomaton](https://github.com/WolframInstitute/IteratedFiniteAutomaton)
- [MathNotebook](https://github.com/WolframInstitute/MathNotebook)
- [ClaudePluginComputationalResearch](https://github.com/WolframInstitute/ClaudePluginComputationalResearch)
- [ClaudePluginMarketplace](https://github.com/WolframInstitute/ClaudePluginMarketplace)

## Wolfram Links
- [Wolfram Community][WolframCommunity].
- [Wolfram Institute repositories](https://github.com/WolframInstitute)
- [Wolfram Events][WolframEvents]
- [Stephen Wolfram's blog][WolframBlog]

[infrageometry]:/wolfram/2026/03/31/talks-infrageometry-srni-madrid.html
[templeton-grant]:https://www.templeton.org/grant/causality-observers-and-computation-a-new-approach-to-fundamental-physics-and-metamathematics
[WolframCommunity]:https://community.wolfram.com/web/hajekpavel
[WolframEvents]:https://events.wolfram.com/
[WolframBlog]:https://writings.stephenwolfram.com/
[de-llmification]: {% link WorkWithMe.md %}#de-llmification

{% include post-index.html posts=site.categories.Wolfram heading="Related Wolfram posts" %}
