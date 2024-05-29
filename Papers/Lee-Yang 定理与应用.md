---
tags:
  - Papers
created: 2023-04-23 19:16:40
---


# General form

The *grand canonical partition function* ^70c786
$$
\Xi_M(z,V,T)
= \sum_{n=0}^M Z_n(V,T)\ z^{n}
$$

where the $Z_n \equiv \sum_r \exp (-\beta \Energy_r)$ and the $z \equiv \exp(\beta \mu)$ are the *canonical partition function* and the *fugacity*, respectively.

[[李政道|Lee]] and [[杨振宁|Yang]] have proven two theorems in 1952, stated below[^1][^2]

>[! Theorem 1]
>Assume that the shape of $V$ is such that its surface area does not increase faster than $V^{2/3}$. Then for all *positive real* values of $z$, $V^{-1} \ln \Xi$ approaches, as $V \to \infty$, a limit which is *independent of the shape* of $V$. Furthermore, this limit is a continuous, *monotonically increasing* function of $z$.

>[!Theorem 2]
>If in the complex $z$ plane a region $R$ containing a segment of the positive real axis does not contain any roots of [[The Lee-Yang Theorem and applications#^70c786|grand canonical partition function]], then, in this region, as $V \to \infty$, all the quantities
>$$
>\qty(\pdv{\ln z})^k \frac1V \ln \Xi \qquad (k = 0, 1, \cdots)
>$$
>approach limits which are *analytic* with respect to $z$. Furthermore the operators $(\pdv{\ln z})$ and $\lim_{V \to \infty}$ *commute* in $R$.

> 由定理2可知，算符在零点位置*不可交换*，由此 Yang 也借此评判了 Mayer 一番。
> 
> > [!todo] 
> > - [x] 关于算符交换的论述有误 (@2023-05-24 10:02)
> 

巨正则配分为多项式，且系数均为正数。$\Xi_M$ 无正根。[^2]

---

# Ising model

The typical hamiltonian of [[伊辛模型]]
$$
\ham = -J \sum_{\ev{ij}} \sigma_i \sigma_j -  H \sum_i \sigma_i
\qquad (J > 0)
$$
Let $q$ be the number of nearest neighbors at each site. 
$N_-, N_+$ be the numbers of spins facing down or up.

## Canonical partition function

$$Z = \sum_r \exp (-\beta \Energy_r)$$

$$
-\beta \ham = \beta \qty(J \sum_{\ev{ij}}\sigma_i \sigma_j + H \sum_i \sigma_i)
$$

假定所有 spin 向下，则能级唯一
$$
Z = \me^{\beta J N \frac{q}{2} - \beta NH}= \me^{\beta N \qty(\frac12 qJ - H)} 
$$

先不考虑简并，此时如果反转任意一个 spin（$N_{+}+1$），则将会多增加一项配分函数的贡献

任意反转多个也同样的方式

$$Z' = \me^{\beta N \qty(\frac12 qJ - H)} \qty[1 + \me^{-2 \beta(qJ - H)} + \cdots]$$

任意反转多个也同样的方式

再考虑到 the *degeneracy* of energy levels $\Omega$ 带来的修正，最终*正则配分函数*为

$$
\boxed{
\begin{align}
Z_N(H,T) =& \me^{\beta N(\frac12 qJ - \mu H)} \sum_{N_+=0}^N \exp \qty[
	-2 \beta (qJ - \mu H) N_+
]\\
&\sum_{N_{++}} \Omega_N(N_+, N_{++})
\exp \qty(4 \beta J N_{++})
\end{align}
}
$$

## Lattice gas

以上求得了Ising model的正则配分，但是[[Lee-Yang theorem]]涉及到的是巨正则配分函数。

Lee, Yang 在论文中证明了，lattice gas model 和 Ising model 的等价性。



格子气的正则配分
$$
Z_N = \frac{1}{2^N} \exp \qty(
	\beta J \gamma + \beta \mu \sum_i h_i
) P(\beta, h_i)
$$
where
$$
P = \sum_{\qty{\sigma_i = \pm 1}} \exp \qty[
	\beta J \sum_{\ev{ij}} (\sigma_i \sigma_j -1)
	+ \beta \mu \sum_{i} h_i (\sigma_i - 1)
]
$$




[^1]: Yang, C. N., and T. D. Lee. “Statistical Theory of Equations of State and Phase Transitions. I. Theory of Condensation.” _Physical Review_ 87, no. 3 (August 1, 1952): 404–9. [https://doi.org/10.1103/PhysRev.87.404](https://doi.org/10.1103/PhysRev.87.404).

[^2]: Quera, Arnau, and Tomeu Fiol. “The Lee-Yang Theorem and Applications,” 2015.
