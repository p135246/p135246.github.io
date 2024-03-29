---
title:      "Canonical IBL algebra on cyclic words in Wolfram Mathematica"
categories: [MATH, IT]
mathjax:    true
utterances: true
---

# Canonical IBL algebra on cyclic words in Wolfram Mathematica

I wrote a [Mathematica notebook](https://github.com/p135246/canonical-ibl-algebra) that implements the canonical structure of an IBL algebra on the space of cyclic words of vectors of a graded vector space with a graded symmetric pairing as described in [Cieliebak, Fukaya, Latschev: Homological algebra related to surfaces with boundary, 2015][CFL].
The signs should agree with the reference, too.

## Canonical IBL algebra

Consider a graded vector space $$V$$, with grading denoted by $$|\cdot|$$, equipped with a graded symmetric pairing $$\bullet$$ of degree $$n$$.
Let $$C$$ be the graded vector space generated by *cyclic words*

$$l_1\dots l_k = \pm l_c\dots l_{c-1},$$

where each $$l_i$$ is a homogenous element of $$V$$ and $$\pm$$ is the Koszul sign, with the shifted grading

$$[l_1\dots l_k] = |l_1|+\dotsb+|l_k|+n-2.$$

Then $$C$$ carries a *canonical Lie bracket* $$[-,-]$$ of degree $$2(2-n)$$ and a *canonical Lie cobracket* $$\delta(-)$$ of degree $$0$$ that satisfy the relations of an *involutive bi-Lie algebra (IBL)*.

The predefined example in the notebook is for $$n=1$$ and $$V$$ generated by $$x$$ and $$y$$ with

$$|x|=-1,\quad|y|=0,\quad x\bullet y = - y\bullet x = 1,\quad x\bullet x = y\bullet y = 0.$$

However, one can easily change the parameters and consider any situation.
 
 
The operations $$[-,-]$$ and $$\delta(-)$$ are naturally extended to certain operators on the *exterior algebra* $$EC$$ of $$C$$, such that the IBL relations formulated in terms of these extensions take a simple form without signs.
This is similar to the case of $$A_\infty$$ algebras, where the operations are extended to coderivatives on the bar complex.
These extensions and IBL relations are also implemented in the notebook; in particular, one can let the computer to check the IBL relations on all cyclic words up to some length.


The operations $$[-,-]$$ and $$\delta(-)$$ can also be combined into a canonical *BV operator* on the space $$F$$ of formal functions on $$EC$$ with parameter $$\hbar$$ with $$|\hbar|=2(n-3)$$ (see [my thesis][PhD]).
Maurer-Cartan elements, which govern deformations of the IBL algebra, then correspond to elements $$S\in F^0$$, called *BV actions*, that satisfy the *quantum master equation*, and gauge equivalence of Maurer-Cartan elements then corresponds to *homotopy equivalence of BV actions*.
The BV formalism shall be implemented in a future release.

Finally, note that the BV operator on $$F$$ together with the function multiplication is in fact a BD algebra, which can be canonically associated to a degree shift of the *modular operad $$M$$ of surfaces with boundary punctures (open strings)* equipped with connected sum.
This is for $$n=3$$ (no degree shift) described in [Doubek, Jurco, Peksova, Pulmann: Connected sum for modular operads and Beilinsion-Drinfeld algebras, 2022](https://arxiv.org/abs/2210.06517).
The general situation is a part of our common ongoing project, whose goal is to interpret Maurer-Cartan elements as algebras on $$V$$ over the Feynman transform of $$M$$, the so called *quantum $$A_\infty$$ algebras*, and study consequences.


## Notes on implementation

1. [Wolfram Mathematica](https://www.wolfram.com/mathematica/) was chosen because of its versatile yet easy-to-use computer algebra system, which makes it a convenient sandbox for [rapid development](https://en.wikipedia.org/wiki/Rapid_application_development). 
   Even though my implementation relies heavily on Mathematica's [pattern matching](https://en.wikipedia.org/wiki/Pattern_matching) abilities, a [procedural imlementation](https://en.wikipedia.org/wiki/Procedural_programming) with the same functionality could be done easily as follows:

   First of all, a cyclic word would be translated into its *minimal cyclic form*---that is, a cyclic permutation that is the smallest in the lexicographic order---keeping track of the Koszul sign.
   Likewise a wedge product of cyclic words would be translated into a lexicographically ordered tuple of lexicographically ordered minimal cyclic words keeping track of the (shifted) Koszul sign.
   A sum of wedge products of cyclic words would be stored as a *linked tree* (e.g., "x" to the left, "y" to the right) with bivalent *wedge-vertices* indicating the wedge product.
   A *special wedge-vertex* would be inserted if the coefficient of the wedge product that corresponds to the path to the root was nonzero.
   This wedge-vertex would store the nonzero coefficient and pointers to the next and previous special wedge-vertices.
   Having such tree, one could, on one hand, quickly distribute operations over sums by going through the list, and,      on the other hand, update coefficients of the summands by traversing the tree from the root.

## ToDo

1. Implement *actions*, the *BV operator*, and the *BV bracket*.
2. Implement a test whether an action satisfies the *Quantum master equation (QME)*.
3. Implement tests whether two actions are *BV homotopic*.


[PhD]: https://github.com/p135246/phd-thesis/raw/master/Text.pdf
[CFL]: https://arxiv.org/abs/1508.02741
[code]: https://github.com/p135246/canonical-ibl-algebra/canonical-ibl-algebra.nb


