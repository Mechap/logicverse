---
title: The groupoid model of type theory [CONSTRUCTION]
date: 2024-09-18
tags: math
---

<p></p>

Identity sets are one of the most intriguing concept of intensional Martin-Löf
type theory. Their axiomatisation as an inductive family allows one to deduce
the usual properties of equality, notably Leibniz' principle which allows one to
conclude $P(b)$ from $P(a)$ from a proof that $a$ equals $b$. This is not in
conflict with decidability of type checking since if $a$ equals $b$ and
$p : P(a)$ then one does not have $p : P(b)$ but only
$\bold{subst}(s, p) : P(b)$ where $s$ is the proof that $a$ equals $b$ and
$\bold{subst}$ is defined from the eliminator for identity sets.

It is now a natural question to ask whether these translation functions
$\bold{subst}(s, \_)$ actually depend on the nature of the proof $s$, or, more
generally, the question whether any two elements of an identity set are equal.

<!--more-->

# Provability of UIP

We will call $\bold{UIP}$[^1] the following property: If $a_1$, $a_2$ are
objects of type $A$ then for any two proofs $p$ and $q$ of the proposition
"$a_1$ equals $a_2$" there is another proof establishing equality of $p$ and
$q$.

> First, notice that in traditional logical formalism a principle like
> $\bold{UIP}$ cannot be expressed as proofs cannot be referred to by terms of
> the object language and thus are not within the scope of propositional
> equality.

The question whether $\bold{UIP}$ is valid in intensional Martin-Löf type theory
was actually open for a while though it was commonly believed that $\bold{UIP}$
is underivable as any attempt for constructing a proof has failed.

On the other hand, the intuition that a type is determined by its canonical
objects might be seen as evidence for the validity of $\bold{UIP}$ as the
identity sets have at most one canonical element corresponding to a proof of
reflexivity.

Let's put some formalism using Martin-Löf's type theory.

# Syntax

This type theory derives judgements[^2] of the following forms

$$
\begin{align*}
 A\ &\bold{type} &&\text{to mean that A is a type} \\
 a &: A &&\text{to mean that $a$ is an object of type $A$} \\
 A &= B &&\text{to mean that types $A$ and $B$ are} \\
   &          &&\text{\textit{definitionally equal}} \\
 a &= a' : A \quad &&\text{to mean that $a$ and $a'$ are} \\
        &          &&\text{\textit{definitionally equal} objects of type $A$}
\end{align*}
$$

If $A\ \bold{type}$ and $B\ \bold{type}$ under $[x:A]$ then the dependent
function space $\prod_{x:A} B$ is a type. If $b : B\ [x : A]$ then
$[x : A]\ b : (x : A) B$.

[^1]: Uniqueness of Identity Proofs

[^2]: Of course all judgements are relative to a list of variable declarations
    of the form $$ x_1 : A_1, \dots, x_n : A_n $$

    Such lists of assumptions are called contexts and are ranged by capital
    Greek letters, $\Gamma$, $\Delta$, ...

    One writes $\mathcal{J}[\Gamma]$ (alternatively $\Gamma \vdash \mathcal{J}$)
    to indicate that judgement $\mathcal{J}$ holds in context $\Gamma$.
