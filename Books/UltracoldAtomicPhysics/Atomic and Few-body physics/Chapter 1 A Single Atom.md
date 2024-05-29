---
tags: 
number headings: first-level 1, max 6, 1.1.
created: 2023-05-07 13:20:40
---
#  Electronic Structure

先来考虑有 $Z$ 个电子，且有库伦相互作用，spin-orbit coupling，hyperfine coupling 时的 Hamiltonian.

## 电子-核库伦相互作用

$$
\hat{\ham}_0
= \sum_{i=1}^Z \qty[\frac{\hslash^2}{2m^*}\laplacian_i + V_{\text{ei}}(\vb*{r}_j)]
$$

The term $m^* \equiv \dfrac{Mm}{M+m}$ is the *reduced mass*. 

$V_{\text{ei}}(\vb*{r}) = -\dfrac{Z \kappa}{r}$

由于 $\dfrac1r$ Coulomb potential, 能量本征态为

$$
\Energy = -\frac{m^* Z^2 \kappa^2}{2 \hslash^2 n^2}
$$

只依赖于 principal quantum number $n$. 此时 angular quantum number 的取值为 $0$ 到 $n-1$ 之间的整数。由于$\dfrac1r$ Coulomb potential 导致的 $SO(4)$ 大于三维转动对称性，导致能级对*角量子数*简并。

## 电子间库伦相互作用

电子间相互作用的哈密顿形式如下

$$\hat{V}_c = \sum_{i<j} V_{\text{ee}}(\vb*{r}_i - \vb*{r}_j),\quad V_{\text{ee}}(\vb*{r}) = \frac{\kappa}{r} = \frac{1}{4 \pi \epsilon_0}\frac1r$$

首先，内层电子会屏蔽内部的 $Ze$ 正电荷，于是外部 valence electron 受到 reduced Coulomb potential. 而最外侧电子感受到的场，受到其它 $Z-1$ 个电子的屏蔽。

对 $r$ 较大的电子，收到来自核的 effective attraction 约为 $-\kappa/r$. 

越靠里，则越不收到屏蔽影响。因此对于足够小的 $r$，电子收到完整的 $-Z\kappa/r$. 

因此，valence electrons 收到的势场不正比于 $1/r$，$SO(4)$ 对称性被破坏，对角量子数的简并将被解除。

$$
\Energy = -\frac{m^* Z^2 \kappa^2}{2 \hslash^2 [n - \delta(n,l)]^2}
$$

> $\delta(n,l)$ 称为 *quantum defect*.


## 自旋-轨道以及超精细耦合

### Spin-orbit coupling

考虑一个电子的静止系，带电的原子核将围绕着电子运动，所形成的环形电流正比于核-电子相对运动的 [[角动量]]. 环形电流诱导出磁场，作用与电子的 spin。
$$
\hat{\ham}_{\text{SO}} = \sum_i \alpha^i_{\text{f}} \hat{\vb*{S}}_i \vdot \hat{L}_i
$$
这被认为是 spin-orbit coupling 的起源。

### Hyperfine coupling

Hyperfine interaction 将电子的自由度 $\hat{\vb*{S}}$, $\hat{\vb*{L}}$ 与核的 spin $\hat{\vb*{I}}$ 进行了耦合。




## 超冷原子

### Alkali-Metal Atoms
| Atom| Valance electron | Label $^{2S+1}L_J$ | Nuclear spin $I$|
|:-:|:-:|:-:|:-:|
|$\text{Li}$ |$2s^1$|$^2S_{\frac12}$|$^7\text{Li}$ ($I=3/2$, B); $^6\text{Li}$ ($I=1$, F)

### Alkaline-Earth-Metal (-Like) Atoms

### Magnetic Atoms

# Magnetic structure

