---
layout: post
title: "why is grothendieck's inequality true?"
date: 2026-08-15
permalink: /blog/grothendiecks-inequality/
---

The purpose of this post is to discuss Grothendieck's inequality, which we state in the following form.
>## Theorem 1 (Grothendieck's Theorem)
>
>There is a universal constant $$K_G$$ with the following property: let
>$$a_{ij}$$ be an $$n\times n$$ matrix and suppose that
>
>$$
>\sup_{|s_i|\leq 1,\ |t_j|\leq 1}
>\left|
>\sum_{i,j=1}^n a_{ij}s_i t_j
>\right|
>\leq 1.
>$$
>
>Then
>
>$$
>\sup_{\|x_i\|\leq 1,\ \|y_j\|\leq 1}
>\left|
>\sum_{i,j=1}^n a_{ij}\langle x_i,y_j\rangle_H
>\right|
>\leq K_G,
>$$
>
>where the $$x_i$$ and $$y_j$$ are vectors in a Hilbert space $$H$$.

The theorem is true over both the real and complex fields, though with different values of the universal constants $$K_G^{\mathbb R}$$ and $$K_G^{\mathbb C}$$, known as the *Grothendieck constants*.

There are many proofs of Grothendieck's inequality available. In this post I'd like to discuss one of them, due essentially to Andrew Tonge, which, although it does not produce the best values of $$K_G$$, has the advantage of being conceptually very simple. It's one of those proofs that, once you've read it, you feel like you actually understand why the theorem is true.

In particular, this post is in no way meant to be a survey of all there is to say about Grothendieck's theorem; for that you can't beat Pisier's survey. You should also look at the book *The Metric Theory of Tensor Products* by Diestel, Fourie, and Swart. If anything, this post should be read as an advertisement for that book, since I understood nothing about tensor products until I started reading it. The proof of GT presented here is an adaptation of Tonge's proof as presented there.

The basic strategy of this proof, and of many other proofs of Theorem 1, is to realize inner products of vectors $$\langle x_i,y_j\rangle$$ in Hilbert space as covariances of random variables; that is, we will find some probability space $$(\Omega,\mathcal E,\mu)$$ and random variables $$X_1,\dots,X_n,Y_1,\dots,Y_n$$ so that

$$
\tag{1}
\langle x_i,y_j\rangle_H
=
\mathbb E(X_iY_j),
\qquad i,j=1,\dots,n.
$$

Of course, merely realizing inner products as covariances in (1) is a triviality. Fix a basis $$\{e_n\}$$ for $$H$$ and expand $$x_i$$ as

$$
x_i
=
\sum_n \langle x_i,e_n\rangle e_n,
$$

and similarly for the $$y$$'s. Now choose any probability space with $$L^2(\mu)$$ infinite-dimensional, fix an orthonormal basis $$\{\psi_n\}$$ for $$L^2(\mu)$$, and put

$$
X_i(\omega)
=
\sum_n
\langle x_i,e_n\rangle
\psi_n(\omega),
$$

and likewise define $$Y_j$$. Then by orthonormality we have (1).

With this construction, the random variables $$X_i,Y_j$$ are in $$L^2$$ (or, since I should probably be consistent with the probabilistic language, they have finite variance). Indeed, by orthonormality again,

$$
\operatorname{var}(X_i)
=
\mathbb E|X_i|^2
=
\sum_n
|\langle x_i,e_n\rangle|^2
=
\|x_i\|_H^2
<\infty.
$$

Of course, by itself this can't accomplish anything, since all we've done is embed $$H$$ isomorphically into $$L^2(\mu)$$. However, there are gains to be had if we can arrange that the random variables $$X_i,Y_j$$ are better than $$L^2$$. In fact, by the following lemma, if we could arrange to realize inner products as covariances of *bounded* random variables, we would get an easy proof of Grothendieck's inequality.
>## Lemma 2 ($$L^\infty$$-flattening implies GT)
>
>Suppose there exists a constant $$C>0$$ with the following property: whenever $$x_1,\dots,x_n,y_1,\dots,y_n$$ are vectors in the unit ball of a Hilbert space $$H$$, there exist a probability space $$(\Omega,\mathcal E,\mu)$$ and random variables $$X_1,\dots,X_n,Y_1,\dots,Y_n$$ on $$\Omega$$ such that for all $$i,j=1, \dots, n$$,
>
>$$
>\tag{2}
>\langle x_i,y_j\rangle_H
>=
>\mathbb E(X_iY_j),
>$$
>
>and
>
>$$
>\tag{3}
>|X_i|\leq C,
>\qquad
>|Y_j|\leq C
>\quad\text{almost surely.}
>$$
>
>Then Grothendieck's inequality holds with constant $$K=C^2$$.

### Proof

Fix a matrix $$(a_{ij})$$ satisfying the hypothesis of Theorem 1. Let the vectors $$x_i,y_j$$ be given and consider the random variables $$X_i,Y_j$$ as in the hypothesis of the lemma. Then, using linearity of expectation and the trivial bound $$\lvert \mathbb{E}(Z)\rvert\leq\mathbb{E}(\vert Z\rvert )$$, we have

$$
\begin{aligned}
\left|
\sum_{i,j=1}^n a_{ij}\langle x_i,y_j\rangle_H
\right|
&=
\left|
\sum_{i,j=1}^n
a_{ij}\mathbb E(X_iY_j)
\right| \\
&=
\left|
\mathbb E\left(
\sum_{i,j=1}^n a_{ij}X_iY_j
\right)
\right| \\
&\leq
\mathbb E
\left|
\sum_{i,j=1}^n a_{ij}X_iY_j
\right|.
\end{aligned}
\tag{4}
$$

Now, since $$\lvert X_i\rvert ,\lvert Y_j\rvert \leq C$$ almost surely, we have by the hypothesis on $$a$$,

$$
\left|
\sum_{i,j=1}^n a_{ij}X_iY_j
\right|
\leq C^2
\qquad\text{almost surely}.
$$

Thus its expectation is bounded by $$C^2$$ as well, so Grothendieck's inequality holds with $$K\leq C^2$$. $$\square$$

It turns out that there does indeed exist such a constant $$C$$, and in fact the existence of uniformly bounded random variables as in the lemma is equivalent to Grothendieck's inequality. I hope to work through this in a later post; in the meantime you can find it in Pisier's survey.

However, as far as I know, there is no proof of Grothendieck's inequality using the lemma, because it seems like the only proof of the lemma uses Grothendieck's inequality. Instead, proofs of Grothendieck's inequality proceed by using the strategy suggested by the lemma, but weakening either (2) or (3), or both.

That is, one can keep (2) but give up almost sure boundedness. The strategy then is to get enough control on the tails of the now-unbounded random variables to still allow favorable estimates of the expectation in (4). This is the strategy we will follow below.

On the other hand, one can give up (2) holding exactly and instead have it hold only approximately; the adjustment to the proof is then needed in (4). It seems like this is the strategy in the proofs that give the best known constants.

As we just said, our strategy here will be to give up boundedness (3), since this seems very hard to get by any direct argument. And as we also noted above, it is trivial to get $$L^2$$-ness. As it turns out, however, if we can get anything better than $$L^2$$, we win.

That is, if we can realize inner products as covariances of random variables in $$L^p$$ (or, sorry, with "finite $$p$$th moments") for some $$p>2$$, and of course with uniform constants, we can prove GT.
>## Lemma 3 ($$L^p$$-flattening implies GT)
>
>Fix $$2<p<\infty$$. Suppose there exists a constant $$C>0$$ with the following property: whenever $$x_1,\dots,x_n,y_1,\dots,y_n$$ are vectors in the unit ball of a Hilbert space $$H$$, there exist a probability space $$(\Omega,\mathcal E,\mu)$$ and random variables $$X_1,\dots,X_n,Y_1,\dots,Y_n$$ on $$\Omega$$ such that
>
>$$
>\tag{6}
>\langle x_i,y_j\rangle_H
>=
>\mathbb E(X_iY_j),
>\qquad i,j=1,\dots,n,
>$$
>
>and
>
>$$
>\tag{7}
>\mathbb E(|X_i|^p)\leq C,
>\qquad
>\mathbb E(|Y_j|^p)\leq C
>\quad\text{for all }i,j=1,\dots,n.
>$$
>
>Then Grothendieck's inequality holds with constant $$K$$ depending only on $$C$$ and $$p$$.

### Proof

We will exploit the basic trick of using a cutoff parameter to split an $$L^p$$ function into its "big" and "small" parts. Since we have an $$L^p$$ estimate for some $$p>2$$, it will follow that the "big" part will have uniformly small $$L^2$$ norm.

Let us work in the general setting of $$L^p$$ spaces for a moment. Fix a measure space $$(\Omega,\mathcal E,\mu)$$ and $$f\in L^p$$. Choose a parameter $$M>0$$ and define the cutoff functions

$$
f^M(\omega)
=
\begin{cases}
f(\omega), & |f(\omega)|>M,\\
0, & |f(\omega)|\leq M,
\end{cases}
$$

and

$$
f_M(\omega)
=
\begin{cases}
f(\omega), & |f(\omega)|\leq M,\\
0, & |f(\omega)|>M.
\end{cases}
$$

We have

$$
f=f_M+f^M.
$$

Trivially, $$f_M\in L^\infty$$ and $$\|f_M\|_\infty\leq M$$. On the other hand, the "big" part $$f^M$$ will belong to $$L^q$$ for all $$1\leq q\leq p$$. In particular, since $$p>2$$, we have the standard estimate

$$
\begin{aligned}
\|f^M\|_2^2
&\leq
\int |f^M|^2\,d\mu \\
&=
\int
\frac{|f^M|^p}{|f^M|^{p-2}}
\,d\mu \\
&\leq
\frac{1}{M^{p-2}}
\int_{|f|>M}|f|^p\,d\mu \\
&\leq
\frac{1}{M^{p-2}}\|f\|_p^p.
\end{aligned}
\tag{8}
$$

Now we can begin the proof of the lemma proper. Fix $$n$$ and the $$n\times n$$ matrix $$a$$. We will define two norms on $$a$$, namely, the two quantities we are interested in:

$$
\|a\|
:=
\sup_{|s_i|\leq 1,\ |t_j|\leq 1}
\left|
\sum_{i,j=1}^n a_{ij}s_i t_j
\right|,
$$

and

$$
\|\!|a|\!\|
:=
\sup_{\|x_i\|\leq 1,\ \|y_j\|\leq 1}
\left|
\sum_{i,j=1}^n
a_{ij}\langle x_i,y_j\rangle_H
\right|.
$$

It is clear that both of these quantities are finite.

Now fix the vectors $$x_1,\dots,x_n,y_1,\dots,y_n$$ and the random variables $$X_i,Y_j$$ associated to them as in the hypotheses. Fix a cutoff parameter $$M$$, to be specified later, and consider the splittings

$$
X_i=(X_i)_M+(X_i)^M
$$

and likewise for the $$Y$$'s.

By definition,

$$
\|(X_i)_M\|_\infty\leq M,
$$

and from (8) we have

$$
\|(X_i)^M\|_2^2
\leq
M^{2-p}C.
$$

Also, since we are on a space of finite measure, we have $$L^p\subset L^2$$ boundedly for $$p>2$$, so

$$
\|X_i\|_2\leq C'
$$

with $$C'$$ depending only on $$C$$ and $$p$$.

Let us write

$$
\begin{aligned}
XY
&=
X(Y_M+Y^M) \\
&=
(X_M+X^M)Y_M+XY^M \\
&=
X_MY_M+X^MY_M+XY^M.
\end{aligned}
\tag{9}
$$

Proceeding as in the proof of Lemma 2, we have

$$
\left|
\sum_{i,j=1}^n
a_{ij}\langle x_i,y_j\rangle_H
\right|
=
\left|
\mathbb E\left(
\sum_{i,j=1}^n a_{ij}X_iY_j
\right)
\right|.
$$

We split each term $$X_iY_j$$ as in (9) and bound the three terms separately.

First, we have

$$
\left|
\mathbb E\left(
\sum_{i,j=1}^n
a_{ij}(X_i)_M(Y_j)_M
\right)
\right|
\leq
M^2\|a\|
$$

by the same argument as in Lemma 2, since

$$
|(X_i)_M|, |(Y_j)_M|\leq M
$$

almost surely.

Now we have to control the contributions from the remaining tail terms $$X^M,Y^M$$. To do this, first note that

$$
\mathbb E\big((X_i)^M(Y_j)_M\big)
=
\left\langle
(X_i)^M,(Y_j)_M
\right\rangle_{L^2(\mu)}.
$$

Therefore, by the definition of the $$\|\!|\,\cdot\,|\!\|$$ norm,

$$
\begin{aligned}
\left|
\mathbb E\left(
\sum_{i,j=1}^n
a_{ij}(X_i)^M(Y_j)_M
\right)
\right|
&\leq
\|\!|a|\!\|
\max_i\|(X_i)^M\|_2
\max_j\|(Y_j)_M\|_2 \\
&\leq
M^{1-p/2}C^{1/2}C'
\|\!|a|\!\|.
\end{aligned}
$$

Likewise, for the last term,

$$
\left|
\mathbb E\left(
\sum_{i,j=1}^n
a_{ij}(X_i)(Y_j)^M
\right)
\right|
\leq
M^{1-p/2}C^{1/2}C'
\|\!|a|\!\|.
$$

Putting it all together, we have

$$
\left|
\sum_{i,j=1}^n
a_{ij}\langle x_i,y_j\rangle_H
\right|
\leq
M^2\|a\|
+
2M^{1-p/2}C^{1/2}C'
\|\!|a|\!\|.
$$

Taking the supremum over unit vectors $$x_i,y_j$$ on the left-hand side gives

$$
\tag{10}
\|\!|a|\!\|
\leq
M^2\|a\|
+
\frac{2C^{1/2}C'}{M^{p/2-1}}
\|\!|a|\!\|.
$$

Thus, by taking $$M$$ sufficiently large, we can move the $$\lvert\lvert\lvert a\rvert\rvert\rvert$$ term to the left-hand side and conclude that

$$
\|\!|a|\!\|
\leq
K(C,p)\|a\|.
$$

This proves the lemma.$\square$$

I'll refer to the process of passing from the vectors $$x_i,y_j$$ to the random variables $$X_i,Y_j$$ as *flattening*. The idea is that we are placing the vectors into $$L^2(\mu)$$ in such a way that inner products are preserved, but so that the functions themselves lie in $$L^p$$ for some larger $$p$$, and are thus in a sense "flatter" than typical $$L^2$$ functions.

So, Lemma 3 says that uniform flattening implies GT, and from the point of view we've set up, the reason GT is true is that flattening is possible. It is accomplished by using not just any orthonormal set to embed $$H$$ in $$L^2$$, but an orthonormal set consisting of an appropriate system of *independent* random variables. We thus have an illustration of how much stronger independence is than mere orthogonality.

To accomplish the flattening, we recall the *Rademacher system*, which is an independent sequence of random variables, each taking the values $$\pm1$$ with probability $$1/2$$.

Concretely, we can construct such a system in $$L^2[0,1]$$ by letting

$$
r_n(x)=2\beta_n(x)-1,
$$

where $$\beta_n(x)$$ denotes the $$n$$th digit in the binary expansion of the real number $$x\in[0,1]$$. We can of course ignore the non-uniqueness of binary expansions, since this occurs only on a Lebesgue null (in fact, countable) set of $$x$$.

Alternatively, we have

$$
r_n(x)
=
\operatorname{sgn}\big(\sin(2^n\pi x)\big),
\qquad n=1,2,\dots.
$$

Or, finally, in words, $$r_n$$ is a square wave with frequency $$2^n$$.

Each $$r_n$$ has mean $$0$$ and variance $$1$$, so by independence we have

$$
\mathbb E(r_nr_m)=\delta_{nm}.
$$

Thus, as realized in $$L^2$$, the $$r_n$$ are orthonormal. In particular, for any $$\ell^2$$ sequence of scalars $$(a_n)$$,

$$
\left\|
\sum_n a_nr_n
\right\|^2
=
\sum_n|a_n|^2.
$$

However, the *independence* of the $$r_n$$ buys us more than this, since it allows us to control higher-degree products such as

$$
\mathbb E(r_ir_jr_kr_l).
$$

In particular, we have the following.
>## Lemma 4 ($$L^4$$ flattening of Hilbert space)
>
>Let $$(r_n)_{n=1}^\infty$$ be a Rademacher system. Then for every $$\ell^2$$ sequence of real scalars $$(a_n)_{n=1}^\infty$$, we have
>
>$$
>\left\|
>\sum_n a_nr_n
>\right\|_4
>\leq
>3^{1/4}
>\left\|
>\sum_n a_nr_n
>\right\|_2.
>$$

### Proof

We may assume that only finitely many of the $$a_n$$ are nonzero, and normalize so that

$$
\left\|
\sum_n a_nr_n
\right\|_2
=
\sum_n a_n^2
=
1.
$$

Now

$$
\begin{aligned}
\left\|
\sum_n a_nr_n
\right\|_4^4
&=
\int_0^1
\left(
\sum_n a_nr_n(x)
\right)^4\,dx \\
&=
\sum_{i,j,k,l}
a_ia_ja_ka_l
\int_0^1
r_i(x)r_j(x)r_k(x)r_l(x)\,dx \\
&=
\sum_{i,j,k,l}
a_ia_ja_ka_l
\mathbb E(r_ir_jr_kr_l).
\end{aligned}
$$

Pondering independence, we see that $$\mathbb E(r_ir_jr_kr_l)$$ vanishes if the $$i,j,k,l$$ are all distinct.

If two are equal, say $$i=j$$, then since $$r_n^2\equiv1$$ we get $$\mathbb E(r_kr_l)$$. Thus the expression $$\mathbb E(r_ir_jr_kr_l)$$ is equal to $$1$$ if the indices $$i,j,k,l$$ occur in two matching pairs, and is $$0$$ otherwise.

Labeling the matching pairs and compensating for double-counting, we have

$$
\begin{aligned}
\left\|
\sum_n a_nr_n
\right\|_4^4
&=
\sum_{i,j}a_i^2a_j^2
+
\sum_{i,k}a_i^2a_k^2
+
\sum_{i,l}a_i^2a_l^2
-
2\sum_i a_i^4 \\
&\leq
\sum_i a_i^2
\left(
\sum_j a_j^2
+
\sum_k a_k^2
+
\sum_l a_l^2
\right) \\
&\leq 3
\end{aligned}
$$

by our normalization. This proves the lemma.$$\square$$

Of course, since the $$r_n$$ are real-valued, we can deduce an inequality in the complex case by taking real and imaginary parts, at the cost of an extra factor of $$\sqrt{2}$$ in the constant.

Those who know, know that what I have called the "flattening lemma" is really a special case of Khinchin's inequality: 
>## Theorem 2 (Khinchin's inequality)
>
>Let $$r_n$$ be a Rademacher system and $$(a_n)$$ a sequence of scalars. Then for all $$1\leq p<\infty$$,
>
>$$
>\left\|
>\sum_n a_nr_n
>\right\|_p
>\approx
>\left(
>\sum_n|a_n|^2
>\right)^{1/2},
>$$
>
>where the implied constants depend only on $$p$$.

I won't prove this here. 

At any rate, using either Khinchin's inequality or our pedestrian version, we now get a proof of GT. Given the vectors $$x_i,y_j$$, expand them in an orthonormal basis of $$H$$ as

$$
x_i
=
\sum_n
\langle x_i,e_n\rangle e_n,
$$

and make these the coefficients of the Rademacher functions. Put

$$
X_i(\omega)
:=
\sum_n
\langle x_i,e_n\rangle
r_n(\omega),
$$

and do the same for the $$y$$'s.

Now, in the real case, the hypotheses of the $$L^p$$-flattening lemma (Lemma 3) are satisfied with

$$
p=4,
\qquad
C=3,
\qquad
C'=1.
$$

Thus, digging through the proof again (or rather, just looking at (10)), we get an estimate for the constant $$K$$ in terms of the cutoff parameter $$M$$:

$$
K_G^{\mathbb R}
\leq
\frac{M^2}{1-\frac{2\sqrt{3}}{M}}.
$$

Optimizing in $$M$$, this works out to (I think)

$$
M=3\sqrt{3},
$$

which gives

$$
K_G^{\mathbb R}\leq81.
$$

This isn't very good: the best known value is

$$
K_G^{\mathbb R}\leq1.78.
$$

By managing the cutoff a little more subtly, one can improve the constant attainable by this method to

$$
\frac{81}{16}=5.0625.
$$

This is what comes from the proof as described in Diestel, Fourie, and Swart.
