---
tags: SpecialFunction
number headings: first-level 1, max 6, 1.1.
created: 2023-05-29 21:49:35
aliases: [厄米多项式, Hermite 多项式]
---
[[Hermite polynomials|Hermite 多项式]]
# 1. Overview

$$
H_n(\xi) = \sum_{m=0}^M
(-1)^m \frac{n!}{m!(n-2m)!}
(2\xi)^{n-2m}
$$
# 2. Generating Function
$$\begin{equation}

\boxed{

S(x,r) \equiv \exp(2xr-r^2) = \sum_{n=0}^\infty H_n(x) \frac{r^n}{n!}

}

\end{equation}$$
# 3. Orthogonality

$$
\begin{equation}

\boxed{

\int_{-\infty}^\infty

H_m(x) H_n(x)\ \text{e}^{-x^2}\dd{x} = 2^n n! \sqrt{\pi} \delta_{mn}

}

\end{equation}
$$