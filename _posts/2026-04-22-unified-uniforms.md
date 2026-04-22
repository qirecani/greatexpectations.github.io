---
layout: post
title: "Unified Uniforms"
---

Let's kick off this second post with some more probability.

I first encountered the uniform distribution in high school, and I remember thinking to myself - "this can't be that hard". Oh boy, how wrong that would turn out to be...

In this post, we'll explore some interesting problems involving standard uniform distributions, that is, random variables with the following Probability Density Function (pdf)

$$
f(x)=\mathbb{1}_{\{x\in(0,1)\}}.
$$

and Cumulative Distribution Function (cdf)

$$
F(x)=x\mathbb{1}_{\{x\in(0,1)\}}.
$$

Now, I expect this post to be much lengthier than the first one, so feel free to kick back and enjoy a barrage questions that you never thought could be asked about $X\sim U(0,1)$.

$$
\text{Let }X,Y,Z\text{ each be independent }U(0,1)\text{ random variables. Prove that }(XY)^Z\sim U(0,1).
$$

Honestly, this more of an algebra exercise than a thinking exercise. Let's first find the cdf of $XY$. Using, the Law of Total Probability, we have

$$
\mathbb{P}(XY\le m)=\int_0^1\mathbb{P}(XY\le m\mid Y=y)dy=\int_0^1\mathbb{P}(X\le \frac{m}{y})dy.
$$

Now, when $y\le m$, $\mathbb{P}(X\le \frac{m}{y})=1$, so the integral is

$$
\int_0^1\mathbb{P}(X\le \frac{m}{y})dy=\int_0^mdy+\int_m^1\frac{m}{y}dy=m-m\log m,m\in(0,1).
$$

We now use this cdf and Law of Total Probability again, where

$$
\mathbb{P}((XY)^Z\le t)=\int_0^1\mathbb{P}((XY)^Z\le t\mid Z=z)dz=\int_0^1\mathbb{P}(XY\le t^{\frac1z}\mid Z=z)dz=\int_0^1t^{\frac1z}-t^{\frac1z}\log t^{\frac1z}dz.
$$

We now make the substitution $s=\frac1z\implies dz=\frac{-1}{s^2}ds$ and obtain

$$
\int_0^1t^{\frac1z}-t^{\frac1z}\log t^{\frac1z}dz=\int_1^\infty\frac{t^s}{s^2}\left(1-s\log t\right)dz=-\int_1^\infty d\left(\frac{t^u}{u}\right)=t,t\in(0,1).
$$

$$
\implies\mathbb{P}((XY)^Z\le t)=t\implies(XY)^Z\sim U(0,1).
$$

and we are done.
