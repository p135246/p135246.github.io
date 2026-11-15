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

Under the direction of [Stephen Wolfram](https://www.stephenwolfram.com/), my main responsibility was to develop a dictionary of discrete geometric concepts for the [Wolfram Physics Project](https://www.wolframphysics.org/) and contribute to a blog post on [Stephen Wolfram's writings][WolframBlog] as part of the Institute's [*Infrageometry project*](https://wolframinstitute.org/research).

The term Infrageometry was originally used by [Carlos Zapata-Carratalá](https://zapatacarratala.me/) and Jonathan Gorard for a program to explore the expressive power of elementary hypergraph rewriting in simulating geometric operations such as homotopies of paths, much as it can generate algebraic axioms via confluence or simulate a Turing machine. See [Arity Science](https://arity.science/findings/infrageometry/) for the development of these ideas.

After initial consultations with Stephen Wolfram and Nik Murzin, during which I learned about the basic concepts and philosophy of Wolfram's computational universe, it became clear that a different, more "robust" and less "exact" approach was wanted. Hence I set out to develop a physically and mathematically sound minimal-model pipeline for reconstructing spacetime geometry for a given observer from a single history in the multiway system of hypergraph rewriting, using aggregated properties rather than the exact structure.

As part of this work, I wanted to understand how geometry might emerge when a computationally bounded observer with distinguishing power of certain size measures a large graph. The simplest model of this observer-dependent geometry is scale-dependent geometry, leading to the question of renormalization. Note that one could potentially try to define geometry when the computational time or storage capacity of the observer is limited.

Another idea I wanted to explore was whether Riemannian geometry and other geometric structures could be formulated not by starting with a smooth manifold equipped with a metric tensor and additional infinitesimal structure, but through a scaled Gromov–Hausdorff-type limit of graphs viewed as metric-measure spaces, together with discrete minimal models of the relevant geometric structures and corresponding coarse-graining maps. In such a limit, observables associated with the discrete models would converge weakly to observables of the limiting geometric object and satisfy the relations expected for the resulting type of geometry. The graphs could arise directly from hypergraph rewriting by taking their 1-skeletons, from causal graphs of individual rewriting histories through spatial reconstruction with a chosen foliation, or, as a simpler toy model, from subdivision schemes applied to a given graph, possibly together with an embedding.

This led me to ask to what extent differential-geometric structure can emerge from graphs encoding essentially a binary relation of “closeness” between points. The ability of such relations to recover the homotopy type of sufficiently fine discretizations of manifolds is illustrated by Latschev’s theorem, which motivated the broader question of whether Riemannian notions, such as geodesic structure or curvature bounds, could similarly be recovered from suitable discrete models and their limits. I was interested in asking an analogous question for symplectic geometry, in particular whether a discrete analogue of the canonical one-form on a graph cotangent bundle could give rise to the corresponding continuous structure in an appropriate limit.

A further question is what higher-arity relations between points might represent geometrically, and whether they could give rise, in an appropriate limit, to genuinely higher-order notions of geometry.

I was also interested in characterizing the limiting behavior of hypergraph rewriting systems across different rules, initial conditions, and branches of multiway evolution through observables of their emergent geometry. In particular, I wanted to study the stability and convergence of observables such as dimension and curvature, and to use them to map the landscape of rules according to the geometries they generate. A further goal was to understand how these limiting geometric properties relate back to structural properties of the underlying rewriting rules. This direction falls within the Institute’s area of study known as Ruliology.

Before my fellowship at the Institute ended, I managed to consolidate parts of this computational research in the [InfraGeometry repository](https://github.com/WolframInstitute/InfraGeometry), whose deployed Wolfram paclet documentation outlines some theoretical background and which forms part of the public deliverables under the Templeton grant.
This format of publication seemed better suited to communicating computational research than LaTeX papers.
Note that Carlos has also introduced his alternative to LaTeX papers: [Hyperiad](https://arity.science/hyperiad/notebook/), an interactive notebook format that runs Python directly in the browser and requires no installation.

During my time at the Institute, I also started several [other repositories](#my-wolfram-institute-repositories) and scientific projects, which I plan to pursue further through our [Multihistory collaboration](https://multihistory.org/).

## My Wolfram Institute repositories

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

## Links
- [Wolfram Community][WolframCommunity].
- [Wolfram Institute repositories](https://github.com/WolframInstitute)
- [Wolfram Events][WolframEvents]
- [Stephen Wolfram's blog][WolframBlog]

[infrageometry]:/wolfram/2026/03/31/talks-infrageometry-srni-madrid.html
[templeton-grant]:https://www.templeton.org/grant/causality-observers-and-computation-a-new-approach-to-fundamental-physics-and-metamathematics
[WolframCommunity]:https://community.wolfram.com/web/hajekpavel
[WolframEvents]:https://events.wolfram.com/
[WolframBlog]:https://writings.stephenwolfram.com/

{% include post-index.html posts=site.categories.Wolfram heading="Related Wolfram posts" %}
