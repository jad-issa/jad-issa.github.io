---
layout: post
title: "'Shape': a generalization of topological countability axioms"
date: '2020-11-04 18:15:00 +0200'
---

NOTE: This post needs JavaScript to show LaTeX expressions using MathsJax.

# Motivation
The concept of countable bases for a topological space and its ramifications in
terms of the power of sequences (allowing us to prove continuity of functions
and that for every point of the closure $$\bar A$$ of a set $$A$$, there is a
sequence of points of $$A$$ converging to it) can be generalized into classes of
nets of different levels of generality and produces fruitful results. The
problem with the usual generalization to completely general nets is that it
leaves no use for intermediate structures between first-countable spaces and
completely general spaces. Introducing the concept of 'shape' solves that. 

If you know the definitions and results presented before "$$I$$-shaped local
basis", then just skip to that part.

# Definitions
## Local basis
A (local) basis for a topological space $$X$$ at the point $$x \in X$$ is a
subset of the neighbourhoods (open sets) of $$x$$ such that any neighbourhood of
$$x$$ contains at least one element in the basis.

# The countability axioms
A local basis for a topological space $$X$$ at $$x$$ is simply a local basis which is
countable as a set (can be injected into $$\mathbb N$$). When a topological
space $$X$$ has locally countable bases at each point $$x \in X$$, I will call
it _locally countable_ (usually, _first-countable_ or satisfying the
_first countability axiom_, though I don't prefer that terminology for what I am
going to display). There is a global version called _second countability_, but I
will not use that.

The first-countability axiom is especially important because it is a every
natural generalization of some properties of metric space (which we know to be
very easy to work with compared to general topological spaces). In particular,
in a locally countable space $$X$$ two important theorems hold from metric spaces:

1. In a locally countable space, the closure $$\bar A$$ of $$A$$ is **exactly**
   the limit points of the sequences of points in $$A$$.
2. In a locally countable space, a function out of $$X$$ ($$f : X \to Y$$) is
   continuous **exactly** when for every sequence $$x_n$$ that converges to
   $$x$$, $$f(x_n)$$ converges to $$f(x)$$.

One direction of each of these two theorems holds in general spaces, the other,
only when the space is locally-countable. We would like to have such
equivalences for broader classes of topological spaces. The motivation here is
that we also know that for general spaces, replacing sequences with general nets
does that, so there must be some interesting intermediate levels of
generalization, and indeed this is what I will show.

# Nets and $$I$$-shaped bases
## Directed sets
A _directed set_ $$I$$ is a set with preorder (a reflexive and transitive
relation) and some upper bound for any two elements. An example is any lattice
(which also has lower bounds and other properties). An important example is the
natural numbers where an upper bound is anything above the maximum of the two
numbers. A directed set can be seen as a (very harsh) generalization of
$$\mathbb N$$ for our purposes.

## Nets
A _net_ $$x$$ over a directed set $$I$$ of points in $$X$$ is any function $$x :
I \to X$$. A sequence is a net over $$\mathbb N$$, so any sequence is a net. The
notation used for nets is the same as that of sequences, so $$x_i := x(i)$$ for
$$i\in I$$. Furthermore, a net $$x_i$$ is said to converge to converge to $$x
\in X$$ when for any neighbourhood $$U$$ of $$x$$, there is an $$i \in I$$ such
that for all $$j \geq i$$, $$x_j \in U$$. (Notice the use of the order).
Therefore, nets are generalizations of sequences.

It is possible to rephrase (1) and (2) into theorems for general topological
spaces with general nets.
1. In any topological space, the closure $$\bar A$$ of $$A$$ is **exactly**
   the limit points of the nets of points in $$A$$.
2. In any topological space, a function out of $$X$$ ($$f : X \to Y$$) is
   continuous **exactly** when for every net $$x_n$$ that converges to
   $$x$$, $$f(x_n)$$ converges to $$f(x)$$.
   
These are much nicer definitions, but the problem is that we go from locally
countable immediately to completely general, so unless we have a locally
countable space, **we're not really using any of the extra structure of the
space**. I try to present here a generalization of the first-countability axiom
that will allow us to do that.

## $$I$$-shaped local basis
For a topological space $$X$$, and a directed set $$I$$, define a local basis
$$\mathcal B$$ at $$x\in X$$ to be of _shape $$I$$_ or _$$I$$-shaped_ when there
is a monotone injection from $$\mathcal B$$ to $$I$$ (w.r.t. reverse inclusion).
(A task is to see whether monotonicity is required; i.e. whether any injection
can be turned into a monotone injection (by some permutation probably)).

The space is locally of shape $$I$$ when there is a basis of shape $$I$$ for
each point of the space. In particular, to say that a space is first-countable
is equivalent to saying that it is locally $$\mathbb N$$-shaped. Note that since
there is an injection from $$\mathcal B$$ to $$I$$, and $$\mathcal B$$ is not
empty (so it contains $$B$$ at least), we can define a function $$f : I \to
\mathcal B$$ such that if $$i$$ is the image of $$B_x$$ by the injection, then
$$f(i) = B_i = B_x$$ and if $$i$$ is not the image of any $$B_x$$, then $$f(i) =
B$$, which means we can index $$\mathcal B$$ with elements of $$I$$ (not
necessarily invectively).

### Generalized theorems

1. In a locally $$I$$-shaped topological space, the closure $$\bar A$$ of $$A$$
   is **exactly** the limit points of the nets of points in $$A$$ over $$I$$.
2. In a locally $$I$$-shaped topological space, a function out of $$X$$ ($$f : X
   \to Y$$) is continuous **exactly** when for every net $$x_n$$ over $$I$$ that
   converges to $$x$$, $$f(x_n)$$ converges to $$f(x)$$.

#### Proofs
One direction in both is easy because the equivalence is proven for general
spaces and general nets, so:
1. All nets in $$A$$ that converge to $$x \in X$$ have their limit point $$x \in
   \bar A$$; this is in particular true for nets over $$I$$.
2. If $$f$$ is continuous, then for all nets $$x_n$$ converging to $$x$$,
   $$f(x_n)$$ converges to $$f(x)$$, this is true also for nets over $$I$$.

The other direction is the interesting direction.

1. If $$x \in \bar A$$, then consider a basis $$\mathcal B$$ at $$x$$. This
   basis is of the shape of $$I$$. We will construct now a net over $$I$$ of
   points in $$A$$ that converges to $$x$$. For $$i \in I$$, let $$B_i$$ be the
   basis element around $$x$$ that maps to $$i$$. Since $$B_i$$ is a
   neighbourhood of $$x$$, there is a non-empty intersection $$B_i \cap A$$.
   Pick a point of that intersection and call it $$x_i$$. Then $$(x_i)$$ is a
   net over $$I$$. I claim that it converges to $$x$$. Consider any
   neighbourhood $$U$$ of $$x$$. There is a basis element $$B_i \subset U$$.
   Now, for all $$j \geq i$$, $$x_j \in B_j \subset B_i \subset U$$, so $$x_i$$
   converges to $$x$$.
2. Let $$f : X \to Y$$ and $$x \in X$$ and suppose $$f$$ is not continuous at
   $$x$$, then, there must be a neighbourhood $$V$$ of $$f(x)$$ such that there
   exists no neighbourhood $$U$$ of $$x$$ whose image lies inside $$V$$. In
   particular, for each basis element $$B_i$$ around $$x$$, there is some point
   $$x_i$$ in $$B_i$$ such that $$f(x_i) \not \in V$$. Therefore, we have a
   sequence $$(x_i)_{i \in I} {}_{}$$ such that $$f(x_i) \not \in V$$.  This
   sequence converges to $$x$$ since for any $$U$$ neighbourhood of $$x$$, we
   have a basis element $$B_i \subset U$$ and such that for all $$x_j$$ where
   $$j \geq i$$, $$x_j \in B_j \subset B_i \subset U$$. However, for the
   neighbourhood $$V$$ of $$f(x)$$, no $$f(x_i) \in V$$; therefore, $$f(x_i)$$
   does not converge to $$f(x)$$.
