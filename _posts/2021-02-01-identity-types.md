---
layout: post
title: "Logic in Type Theory II: Identity Types"
date: '2021-02-01 12:30:00 +0200'
---

NOTE: This post needs JavaScript to show LaTeX expressions using MathsJax.

This is the second post on a series on logic as formulated in the language of
type theory.

Identity types, some of the cornerstones of the new revolution in type theory
and logic, are surprisingly simple, and surprisingly complex!

# Definitional equality and path equality

Unlike in usual set theory, in type theory, equality is of two forms. The first
form is definitional equality, which is a judgement, and the other is a binary
relation $$a = b$$, which is simply a type dependent over two parameters. The
two kinds of equalities are different in nature as one belongs to the
metalanguage, while the other to the language itself.

Judgemental equality asserts -- _as a judgement_ --  that two terms are
definitionally the same. For instance $$1 \equiv S\ 0$$. Likewise, if one
follows the definition of addition, one can always get $$3 + 5 \equiv 8$$
definitionally, that is, purely in the metalanguage. However, although the
addition of natural numbers is commutative, it is impossible to definitionally
get $$n + m \equiv m + n$$ for variable terms $$n$$ and $$m$$.

On the other hand, path equality -- whose naming will be clear when the path
structure of types is discussed -- is a type which may or may not be inhabited.
For instance, there is a way to prove that $$\forall x, y : \mathbb N, x + y = 
y + x$$ by finding a term of type $$\prod_{x, y : \mathbb N} x + y = y + x$$ (by
recursion).

# Path induction

As the identity type $$a =_ A b$$ (given, $$a, b : A, A : \mathcal U$$) can be
seen as a binary relation over $$A$$, the best way to define is to say that it
is completely generated by reflexivity; that is, the only generator is: 
$$\text{refl}_ a : a =_ A a$$ (for every type $$A$$ and term $$a : A$$). In
particular, this means that $$a = b$$ for $$a \not \equiv b$$ is an uninhabited
type (no proofs of it).

As an initial definition of the identity type, it is in fact equivalent to
definitional equality; however, the statement of such a theorem is somewhat
delicate as it crosses levels in the hierarchy of languages connecting
definitional equality from the metalanguage with identity types from the
language itself. By this, equality has been internalized from the metalanguage
to the language itself allowing us to develop on it as a proposition (or type)
instead of a judgement which cannot admit argumentation.

The 'induction' over the identity type is analogous to induction on the
natural numbers. In particular, $$a =_ A b$$ is generated by
$$\text{refl}_ a : a =_ A a$$ giving an introduction rule $$=_ \mathcal I $$ of
the form
$$\Gamma, A : \mathcal U, a : A \vdash \text{refl}_ A : a =_ A a$$.
There is also the elimination rule, by which functions out of the identity type
are constructed. Given the single introduction rule, there is a single
elimination rule whereby any element of the type $$a = b$$ is assumed to be the
element $$\text{refl}_ a$$ of type $$a =_ A a$$. So, any function out of $$a =
b$$ is completely 'generated' by its value at $$\text{refl}_ a$$.
Examples below should hopefully make this clearer.

# Theorems / functions over identity types

## Symmetry (inverses)
Symmetry is a function from $$x = y$$ to $$y = x$$, in particular,
$$\text{sym} : \prod_{A : \mathcal U} \prod_{x, y : A} (x = y \to y = x)$$. To
build this function, we only need to consider the case of the _point_
$$\text{refl}_ x : x = x$$. For this case, $$\text{sym}(A, x, x, \text{refl}_ x) =
\text{refl}_ x$$. We also write $$\text{sym}(A, x, y, p) = p^{-1}$$
(with implicit types) because it acts as the inverse of $$p$$ in the sense we
will talk about in a bit.

## Transitivity (composition)
This is also a function, this time an operation of 2 paths, concatenation or
composition.

What we need is a function $$\cdot : \prod_{A : \mathcal U}\prod_{x, y, z : A}
(x = y \times y = z) \to x = z$$. By currying, that is $$A \times B \to C \cong
A \to (B \to C)$$, it is enough to do 2 inductions, one on $$x = y$$ and one on
$$y = z$$.

By assuming $$x \equiv y \equiv z$$ and $$ p \equiv q \equiv \text{refl}_ x : x = x$$ in
the expression $$p \cdot q$$ (type arguments implicit), we get to define
$$\text{refl}_ x \cdot \text{refl}_ x :\equiv \text{refl}_ x$$, and by induction thus
totally defining the concatenation operation $$\cdot$$ which is also a proof of
the transitivity of equality.

However, one induction could have sufficed with $$x \equiv y$$ and $$p \equiv
\text{refl}_ x$$, we can get $$\text{refl}_ x \cdot q :\equiv q$$. Induction on
$$y = z$$ alone also works giving $$p \cdot \text{refl}_ x :\equiv p$$. Since
all three definitions match on the only generator of the identity type (namely,
$$\text{refl}$$), they are all equivalent definitions.

## Proof of inverses
A proof that the inverses defined below are true inverses consists of a function
$$\text{inv} : \prod_{A:\mathcal U} \prod_{x, y : A} \prod_{p : x = y} p \cdot
p^{-1} = \text{refl}_ x$$. This again is done by induction on the path-type with
$$x \equiv y$$ and $$p = \text{refl}_ x$$. Then, 

$$\begin{align} 
    p \cdot p^{-1} &\equiv \text{refl}_ x \cdot (\text{refl}_ x)^{-1} \\
                   &\equiv \text{refl}_ x \cdot \text{refl}_ x \\
                   &\equiv \text{refl}_ x \\
\end{align}$$

Since $$p \cdot p^{-1} \equiv \text{refl}_ x$$, we have the term
$$\text{refl}_ {\text{refl}_ x} : p \cdot p^{-1} = \text{refl}_ x$$. This means
that $$\text{inv}(A, x, x, \text{refl}_ x) = \text{refl}_ {\text{refl}_ x}$$ thus
generating all of of $$\text{inv}$$ by path induction.

# Groupoid structure

The above theorems (inverses, composition, identity) allow us to conclude that
identity types have a groupoid structure. Groupoid means group-like, since
composition is not within the same type, but rather is "transitive", more like
function composition than a group operation. I will be talking about this very
important structure, and extending it to the $$\infty$$-groupoid structure which
represents the bigger picture. However, this not the full picture yet, as there
still is the important analogy of paths in homotopy spaces, which I will also be
discussing later.