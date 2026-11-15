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

As part of this work, I wanted to understand how geometry might emerge when a computationally bounded observer measures a large graph at a coarse scale. The simplest model of this observer-dependent geometry is scale-dependent geometry, leading to the question of renormalization, but later one could try to define geometry when the computational time or storage capacity of the observer is limited.
Another idea is that one could try to define Riemannian geometry and other geometric notions not in terms of a manifold equipped with a metric tensor and additional tensors, but through a scaled Gromov–Hausdorff-type limit of a sequence of graphs viewed as metric-measure spaces, together with a sequence of discrete minimal models of the relevant structures and coarse-graining maps.
In this limit, observables of the discrete minimal models converge weakly to observables of the limiting geometric objects and satisfy the relations expected for the resulting type of space.
Here the graphs may arise directly from hypergraph rewriting by taking the 1-skeleton, from the causal graph of a single rewriting history by spatial reconstruction with a chosen foliation, or, as a toy model, from a subdivision scheme for a given graph, possibly together with an embedding.
I have the impression that most of differential geometry can emerge in this way just from graphs representing the binary "closeness relation" between points. Note that the power of "closeness relations" to capture homotopical information about a smooth space by taking a dense enough embedded graph is shown by Latschev's theorem, and that one could extend this to Riemannian notions like geodesics and curvature. It is an interesting question what higher-arity relations could mean in terms of relations between geometric points and whether they could lead to higher-order notions of geometry in the limit.
I was also interested in characterizing the limits of hypergraph rewriting under different rules, initial conditions, and branches of multiway evolution in terms of observables of their emergent geometry, in particular the stability and convergence of those observables. I wanted to map the landscape of rules in terms of these observables, such as dimension and curvature, and try to connect the limiting properties with the properties of the rule. This question would fall within the Institute's area of study known as Ruliology.

Before my fellowship at the Institute ended, I managed to consolidate parts of this computational research in the [InfraGeometry repository](https://github.com/WolframInstitute/InfraGeometry), whose deployed Wolfram paclet documentation outlines some theoretical background and which forms part of the public deliverables under the Templeton grant.
This format of publication seemed better suited to communicating computational research than LaTeX papers.
Note that Carlos has also introduced his alternative to LaTeX papers: [Hyperiad](https://arity.science/hyperiad/notebook/), an interactive notebook format that runs Python directly in the browser and requires no installation.

During my time at the Institute, I also started several [other repositories](https://github.com/WolframInstitute) and scientific projects, which I plan to pursue further through our [Multihistory collaboration](https://multihistory.org/).

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
