---
tags:
  - StatisticalMechanics
  - Lee-YangTheorem
  - IsingModel
created: 2023-04-21 20:54:43
---

# General form with grand canonical ensemble


The [[Grand Canonical Ensemble#1. Grand Partition Function|grand canonical partition function]] ^70c786


$$
\Xi_M(z,V,T)
= \sum_{n=0}^M Z_n(V,T)\ z^{n}
$$


where the $Z_n \equiv \sum_r \exp (-\beta \Energy_r)$ and the $z \equiv \exp(\beta \mu)$ are the *canonical partition function* and the [[逸度]], respectively.


[[李政道|Lee]] and [[杨振宁|Yang]] have proven two theorems in 1952, stated below[^1][^2]

>[! Theorem 1]
>Assume that the shape of $V$ is such that its surface area does not increase faster than $V^{2/3}$. Then for all *positive real* values of $z$, $V^{-1} \ln \Xi$ approaches, as $V \to \infty$, a limit which is *independent of the shape* of $V$. Furthermore, this limit is a continuous, *monotonically increasing* function of $z$.

>[!Theorem 2]
>If in the complex $z$ plane a region $R$ containing a segment of the positive real axis does not contain any roots of [[Lee-Yang 定理与应用#^70c786|grand canonical partition function]], then, in this region, as $V \to \infty$, all the quantities
>$$
>\qty(\pdv{\ln z})^k \frac1V \ln \Xi \qquad (k = 0, 1, \cdots)
>$$
>approach limits which are *analytic* with respect to $z$. Furthermore the operators $(\pdv{\ln z})$ and $\lim_{V \to \infty}$ *commute* in $R$.



Grand canonical partition function 为多项式，且系数均为正数。在*有限系统*下，对于巨配分函数 $\Xi_M$，逸度 $z$ *无实根*。[^3]

复数根的例，见图1.[^4]


![[LeeYangLimitPoint.jpeg#CENTRE|figure 1. The two regions separated by the limit point. Zhu, E.Y. (2014)|350]]

此时对于实数轴上的任意点，都可以找到不包含 $z$ 的邻域
$$\forall\ t \in \mathbb{R}, \exists\ U(t) \not\supset z$$

但如果取热力学极限，点线变连续。则必可以找到实数值，它的任何邻域存在 $z$.

且根据定理2，

$$
\qty(\pdv{\ln z})^k \frac1V \ln \Xi
$$
将失去*解析性*。

因此，比方说
$$\beta p = \lim_{V\to \infty} \qty(\frac1V \ln \Xi)$$

$$
\rho = \lim_{V \to \infty} \qty(
	\pdv{\ln z} \frac1V
 \ln \Xi)
$$
在该领域内失去解析性。从而导致 phase transition。


---

# Ising model


由文献[^3]可知，Ising model 的 [[Lee-Yang 定理与应用#Canonical partition function|canonical partition function]] 有如下形式（[[Lee-Yang 定理与应用#Canonical partition function|论证过程]]）

$$
\begin{align}
Z_N(H,T) =& \me^{\beta N(\frac12 qJ - \mu H)} \sum_{N_+=0}^N \exp \qty[
	-2 \beta (qJ - \mu H) N_+
]\\
&\sum_{N_{++}} \Omega_N(N_+, N_{++})
\exp \qty(4 \beta J N_{++})
\end{align}
$$

令 $y = \exp(2 \beta H)$，$y^N = \exp(2N \beta H)$，通过对正则配分函数整理可以得到

$$
\begin{align}
	Z_N &= \exp(-\beta NH) \sum_{j=0}^N \qty(a_j\ y^j)\\
	&= a' \exp(-\beta NH) \prod_{j=1}^N \qty[
	y - y(j)]
\end{align}
$$

自由能密度
$$
\begin{align}
-\beta f &= \frac{1}{N} \ln a' - \beta H + \frac1N \sum_{i = 1}^N \ln \qty[ y - y(i) ]\\
&= \frac{1}{N} \ln a' - \beta H + \iint \dd{z_1}\dd{z_2} \rho(z_1,z_2) \ln(y-z)
\end{align}
$$
其中，$$\rho(z_1,z_2)\equiv \frac1N \sum_{i=1}^N \delta[z-y(i)] = \frac1N \sum_{i=1}^N \delta\qty[z_1-\Re{(y)}]\ \delta\qty[z_2-\Im{(y)}]$$

$$
\begin{align}
	m &= -\pdv{f}{H} = -1 + \int\dd{z_1}\dd{z_2} \rho(z_1,z_2)\frac{2y}{y-z}\\
	\chi &= -4\beta \int \dd{z_1}\dd{z_2} \rho(z_1,z_2)\frac{yz}{(y-z)^2}
\end{align}
$$

$y$ 等于复数 $z$ のところで、特異性が生じます。この点でゼロ点密度が有限にならないと寄与は生じないので、ゼロ点は実軸にあることがわかります。

特異性の強さは実軸付近でのゼロ点密度によって決まる.自由エネルギーの傾きにとぴが生じる1 次相転移の方が特異性が強く,ゼロ点密度が大きいと考えられる.

> [!tip] 零点密度
> $$
> \rho(y_1,y_2)
> = \frac{1}{2\pi N}
> \qty(\pdv[2]{y_1}+\pdv[2]{y_2}) \ln \abs{Z \me^{N\beta h}}
> $$


Ising モデルについては、円定理があって、図2のように[^6]、ゼロ点は*磁場複素平面*上、$\abs{y} = 1$ の単位円上分布します。

![[LeeYangIsing.png#center|figure 2. Lee-Yang zeros. Takahashi, K. and Nishimori, H. (29)|400]]


同じように、温度複素平面の場合、ゼロ点は、Fisher ゼロと呼びます。

---

## 一维 Ising model

此处证明，一维 Ising model 不会发生相变。

由 [[伊辛模型#3.1.2. Partition Function|一维Ising配分]] 可知，一维 Ising model 的配分函数写作
$$
Z = \lambda_1^N + \lambda_2^N
$$
$$
\begin{align}
	\lambda_{1,2} = \me^{\beta J} \qty[
	\cosh(\beta H) \pm \sqrt{\sinh^2(\beta H) + \me^{-4 \beta J}}]
\end{align}
$$
由零点条件 $Z = 0$
$$
\lambda_1 = \exp \qty[
	\frac{\mi(2n-1)\pi}{N} 
] \lambda_2
$$
联立方程，整理可得[^4]
$$
\begin{align}
	\cos \frac{(2n-1)\pi}{2N} \sqrt{\me^{-4K} + \sinh^2h}
	&= \mi \sin \frac{(2n-1)\pi}{2N} \cosh h\\
	\cosh^2 h &= \cos^2 \qty[\frac{(2n-1)\pi}{2N}] \qty(1-\me^{-4K})
\end{align}
$$
where $K \equiv \beta J, h \equiv \beta H$

这个方程的解有如下形式 [^4]
$$
h_n = \mi\theta_n, \qq{where} \cos \theta_n
= \sqrt{1- \me^{-4 K}} \cos \frac{(2n-1)\pi}{2N}
$$
$h$ 的根，全都落在虚轴上

有限温度时
$$
\abs{\cos \theta_n} \leq \sqrt{1- \me^{-4K}} <1
$$
取热力学极限后 
$$N \to \infty \implies \cos \theta_n \not\to 1
\implies h_n \not\to 0$$

也就是说为了让 $h$ 有实数解
$$K \to \infty \implies \beta \to \infty,\ T \to 0$$

相变温度为 $0\ \text{K}$。In other word, there's no [[相变]] in 1D Ising model.




[^1]: Yang, C. N., and T. D. Lee. “Statistical Theory of Equations of State and Phase Transitions. I. Theory of Condensation.” _Physical Review_ 87, no. 3 (August 1, 1952): 404–9. [https://doi.org/10.1103/PhysRev.87.404](https://doi.org/10.1103/PhysRev.87.404).

[^2]: Lee, T. D., and C. N. Yang. “Statistical Theory of Equations of State and Phase Transitions. II. Lattice Gas and Ising Model.” _Physical Review_ 87, no. 3 (August 1, 1952): 410–19. [https://doi.org/10.1103/PhysRev.87.410](https://doi.org/10.1103/PhysRev.87.410).

[^3]: Quera, Arnau, and Tomeu Fiol. “The Lee-Yang Theorem and Applications”, 2015.

[^4]: Zhu, Elton Yechao. “Lee Yang Singularity,” May 15, 2014. [https://web.mit.edu/8.334/www/grades/projects/projects14/EltonZhu_Lee%20Yang%20singularity.pdf](https://web.mit.edu/8.334/www/grades/projects/projects14/EltonZhu_Lee%20Yang%20singularity.pdf)
[^5]: Pathria, Raj K., and Paul D. Beale. _Statistical Mechanics_. Fourth edition. London San Diego Cambridge, MA Oxford: Academic Press, an imprint of Elsevier, 2022.

[^6]: Takahashi, Kazutaka, and Hidetoshi Nishimori. 相転移・臨界現象とくりこみ群. Tōkyō-to Chiyoda-ku: Maruzen Shuppan, 29.

