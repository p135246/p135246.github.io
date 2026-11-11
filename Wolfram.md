---
permalink:  Wolfram.html
layout:     category
nav-name:   wolfram
category:   Wolfram
---
# Wolfram

From October 2025 to October 2026, I was a research fellow at the [Wolfram Institute](https://www.wolframinstitute.org/).
My fellowship was funded by the John Templeton Foundation through the grant [Causality, Observers and Computation: A New Approach to Fundamental Physics and Metamathematics][templeton-grant].

Under the direction of [Stephen Wolfram](https://www.stephenwolfram.com/), my main responsibility was to develop a dictionary of discrete geometric concepts for the [Wolfram Physics Project](https://www.wolframphysics.org/) and contribute to a blog post on [Stephen Wolfram's writings][WolframBlog] as part of the Institute's *Infrageometry* project.

The term Infrageometry was originally used by [Carlos Zapata-Carratalá](https://zapatacarratala.me/) and Jonathan Gorard for a program exploring how elementary hypergraph rewriting could simulate geometric operations such as homotopies of paths.
Carlos further explored this idea in his [work at Arity Science](https://arity.science/findings/infrageometry/).

After initial consultations with Stephen Wolfram and Nik Murzin, during which I learned about the basic concepts and philosophy, I set out to develop a physically and mathematically sound minimal-model pipeline for reconstructing spacetime geometry, as experienced by a given observer, from a single history in the multiway system of hypergraph rewriting.

As part of this work, I wanted to understand how geometry might emerge when a computationally bounded observer measures a large graph at a coarse scale, leading to the idea of scale-dependent geometry.
In mathematical terms, one could think of defining Riemannian geometry and other geometric notions not in terms of a manifold equipped with a metric tensor and additional tensors, but through a scaled Gromov-Hausdorff limit of a sequence of graphs viewed as metric-measure spaces, together with a sequence of discrete minimal models of the relevant structures.
In this limit, appropriately scaled observables of the discrete minimal models converge to observables of geometric objects and satisfy the relations expected for the resulting type of space.

I was also interested in characterizing the limits of hypergraph rewriting under different rules in terms of their emergent geometry, a question within the Institute's area of study known as Ruliology.
I also wanted to explore whether higher-arity relations could lead to higher-order notions of geometry in the limit.

Before leaving the Institute, I consolidated parts of this computational research in the [InfraGeometry repository](https://github.com/WolframInstitute/InfraGeometry), whose deployed Wolfram paclet documentation outlines the theoretical background, and which forms part of the public deliverables under the Templeton grant.
This format seemed better suited to communicating computational research than LaTeX papers.

Note that Carlos has also introduced his alternative to LaTeX papers: [Hyperiad](https://arity.science/hyperiad/notebook/), an interactive notebook format that runs Python directly in the browser and requires no installation. It should be used for one-off presentations of areas for educational purposes and does not attempt to provide all the general functionalities and numerical abilities of Wolfram.

During my time at the Institute, I started several [other repositories](https://github.com/WolframInstitute) and scientific projects, which I plan to pursue further through our [Multihistory collaboration](https://multihistory.org/).

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
