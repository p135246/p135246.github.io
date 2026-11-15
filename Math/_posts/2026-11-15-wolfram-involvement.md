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

The term Infrageometry was originally used by [Carlos Zapata-Carratalá](https://zapatacarratala.me/) and Jonathan Gorard for a program exploring how elementary hypergraph rewriting could simulate geometric operations such as homotopies of paths. They were interested in its expressive power, much as one might ask how rewriting can generate algebraic axioms through confluence or simulate a Turing machine. See [Arity Science](https://arity.science/findings/infrageometry/) for the development of these ideas.

After initial consultations with Stephen Wolfram and Nik Murzin, during which I learned about the basic concepts and philosophy of Wolfram's computational universe, it became clear that we needed a more robust approach based on aggregated properties. I set out to develop a physically and mathematically sound minimal-model pipeline for reconstructing spacetime geometry for a given observer from a single history in the multiway system of hypergraph rewriting.

As part of this work, I wanted to understand how geometry might emerge when a computationally bounded observer measures a large graph at a coarse scale, leading to the idea of scale-dependent geometry.
The usual starting point is a manifold equipped with a metric tensor and additional tensors. Here, one could define Riemannian geometry and other geometric notions through a scaled limit of Gromov–Hausdorff type, using a sequence of graphs viewed as metric-measure spaces together with a sequence of discrete minimal models of the relevant structures.
In this limit, appropriately scaled observables of the discrete minimal models converge to observables of geometric objects and satisfy the relations expected for the resulting type of space.
These graphs can be obtained by taking the 1-skeleton of the hypergraphs produced by rewriting, by spatial reconstruction from causal graphs, or, in a toy model, by subdivision.
It seems that classical geometry can emerge from graphs representing only the binary relation of closeness. This raises the question of what higher-arity relations could mean and whether they could lead to higher-order notions of geometry in the limit.
I was also interested in mapping the landscape of hypergraph rewriting rules by characterizing their limits through the observables of the emergent geometries and studying the stability and convergence of those observables. This falls within the Institute's area of study known as Ruliology.

Before my fellowship at the Institute ended, I managed to consolidate parts of this computational research in the [InfraGeometry repository](https://github.com/WolframInstitute/InfraGeometry), which forms part of the public deliverables under the Templeton grant. The deployed Wolfram paclet documentation outlines some of the theoretical background.
This publication format seemed better suited to communicating computational research than LaTeX papers.
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
