---
title: Fibration - Categorical Logic
date: 2024-09-15
tags: math
---

<p></p>

Putting a logic on a type theory corresponds to putting a pre-order fibration on
top of the structure describing the type theory. For logic, one uses pre-order
structures, since in logic one is interested in provability and not in explicit
proofs (or proof terms as in type theory), which are described as non-trivial
morphisms.

<!--more-->

# Introduction

Fibred category theory is ordinary category theory with respect to a base
category[^1]. For example, several concepts in category theory are defined in
terms of sets. One says that a category $\cat C$ has arbitrary products if for
each set $I$ and each $I$-indexed collection $(X_i)_{i \in I}$ of objects
$X_i \in \cat C$ there is a product object $\prod_{i \in I} X_i \in \cat C$
together with projection morphisms
$$\pi_j : \left( \prod_{i \in I} X_i \right) \to X_j$$

which are suitably universal.

In category theory, one is not very happy with this privileged position of sets
and so the question arises: is there a way to make sense of such products with
respect of an object $I$ of a "universe" or "base category" $\cat B$, more
generally than the category $\bold{Set}$ of sets and functions ? This kind of
generality is needed to interpret logical products $\forall x : \sigma . \phi$
or type theoretic products $\prod_{x:\sigma}. \tau$ when the domain of
quantification $\sigma$ is not interpreted as a set (but as some ordered set, or
algebra for example).

Fibred category theory provides answers to such questions: it tells what it
means or a category $\cat E$ to be "fibered over" a category $\cat B$. In that
case we write[^2]:

$$
\begin{CD}
\cat E \\
@VVV \\
\cat B
\end{CD}
$$

In such a situation, one can define quantification with respect to objects
$I \in \cat B$ and say when one has appropriate hom-objects
$\bold{Hom}(X, Y) \in \cat B$ for $X, Y \in \cat E$.

For a category $\cat C$ there is always a "family fibration"

$$
\begin{CD}
\mathrm{Fam}(\cat C) \\
@VVV \\
\bold{Sets}
\end{CD}
$$

of set-indexed families in $\cat C$.

# The logic and type theory of sets

Of course we should make the fibred perspective more concrete by describing the
familiar logic and type theory of ordinary sets in fibred form. For this reason,
we may consider the vibrations of predicates over sets and of families of sets
over sets, without assuming knowledge of what precisely constitutes a fibration.

Predicate on sets can be organised in a category, that will be called
$\bold{Pred}$ as follows

- _objects_ : pairs $(I, X)$ where $X \subset I$ is a subset of a set $I$ ; in
  this situation we consider $X$ as a predicate on a type $I$, and write $X(i)$
  for $i \in X$ to emphasize that an element $i \in I$ may be understood as a
  free variable in $X$. When $I$ is clear from the context, we sometimes write
  $X$ for the object $(X \subset I)$.

- _morphisms_ : $(I, X) \to (J, Y)$ are functions $u : I \to J$ between the
  underlying sets satisfying
  $$ X(i) \quad \text{implies} \quad Y(u(i)), \quad \quad \text{for each}\quad i \in I. $$

Diagrammatically the existence of such a function $u : I \to J$ amounts to the
existence of a necessarily unique (dashed) map

<img width="170px" style="display: block; margin-left: auto; margin-right: auto;" src="../images/fibration_logic/ql_c0ae76e3e67975f5794e7c75440f367f_l3.svg">

indicating that $u$ restricts appropriately.

There is an obvious forgetful functor $\bold{Pred} \to \bold{Sets}$ sending a
predicate to its underlying set (or type): $(I, X) \mapsto I$.

For a specific set $I$, the "fibre" category $\bold{Pred}_I$ is defined as the
the subcategory of $\bold{Pred}$ of predicates $(X \subset I)$ on $I$ and of
morphisms that are mapped to the identity function on $I$.

# Fibrations

Basically a fibration is a categorical structure which captures indexing and
substituting. Since the formal definition of a fibration is a bit technical,
let's start with the following observations.

Suppose we wish to consider a family of sets, ranging over some index set $I$.
There are two ways of doing so.

a) _Pointwise_ (or _split_) _indexing_: as a collection $(X_i)_{i \in I}$, where
each $X_i$ is a set. Probably this way is most elementary and comes first to
one's mind. One can think of tis collection as being given by a function (or
functor) $I \to \bold{Sets}$, namely $i \mapsto X_i$.

<img width="100%" style="display: block; margin-left: auto; margin-right: auto;" src="../images/fibration_logic/main.svg">

b) _Display indexing_: as a function $\phi : X \to I$. The sets in the family
then appear as _fibres_ "over $i$"

$$
\phi^{-1} (i) = \left\{ x \in X\ |\ \phi(x) = i \right\}
$$

for each $i \in I$.

Given a collection $(X_i)_{i \in I}$ as in (a), take $X$ equipped with a
projection function $\pi : \bigsqcup_{i \in I} X_i \to I$ sending
$(i, x) \mapsto i$.[^3] Consersely, given a function $\phi : X \to I$ as in (b),
put $X_i = \phi^{-1}(i)$. This yields a collection $(X_i)_{i \in I}$ as in (a),
together with an isomorphism $\bigsqcup_{i \in I} X_i \cong X$.

> Although pointwise indexing (a) seems more natural at first, display indexing
> (b) has the great advantage that it generalises to arbitrary categories since
> it only involves the notion of a morphism.

For this reason, we often describe a family of sets as a function
$\phi : X \to I$ as in (b).

[^1]: such a category is like a universe

[^2]: where the arrow $\cat E \to \cat B$ is a functor which has a certain
    property that makes it into a fibration.

[^3]: Up to isomorphism, the fibre $\pi^{-1}(i)$ over $i$ is the original $X_i$
