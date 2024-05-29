---
tags: 
created: 2023-08-30 03:38:18
aliases: []
DOI: 
---


| 原标题 | 作者|年份|
|:-:|:-:|:-:|
|Floquet engineering in Rydberg atoms|[[国見昌哉\|Masaya Kunimi]]||


基于 [[国見昌哉|Masaya Kunimi]] 笔记

# 1. Rydberg 原子的 Floquet engineering

## 1.1. XYZ 相互作用 engineering

在这里，我们讨论了微波脉冲对 [[里德伯原子|Rydberg 原子]]间相互作用的工程[^6][^7]。哈密顿量由
$$
\begin{align}
\hat{H}(t) &= \frac12\sum_{j \neq k}
J_{jk}(\hat{S}_j^x \hat{S}_k^x + \hat{S}_j^y \hat{S}_k^y)
+ \hs \Omega(t) \sum_j [\cos \varphi(t) \hat{S}_j^x+\sin \varphi(t) \hat{S}_j^y]\\
&\equiv \hat{H}_{\text{XY}} + \hat{H}_{\text{drive}}(t)\tag{1}
\end{align}
$$

在这里，我们假设进行了一系列的 $(X, -Y, Y, -X)$ 四个 $π/2$ 微波脉冲。为简单起见，我们假设脉冲具有 $δ$ 函数形式。详细内容请参见文献[^6][^7]。在旋转坐标系中，哈密顿算符变为：

$$
\begin{align}
\hat{H}_\text{I}(t) &= \hat{U}^\dagger(t)\hat{H}(t)\hat{U}(t)
- \mi \hs \hat{U}^\dagger(t) \pdv{t} \hat{U}(t)\\
&= \hat{U}^\dagger(t) \hat{H}_{\text{XY}} \hat{U}(t)\tag{2}\\
\hat{U}(t) &\equiv \hat{T} \exp \qty[- \frac{\mi}{\hs} \int_0^t \dd{t} \hat{H}_{\text{drive}(t)}]\tag{3}
\end{align}
$$
为了得到旋转坐标系下的哈密顿量，我们计算了时间演化算符 (3)
$$
\hat{U}(t) =
\begin{cases}
\hat{U}_1 \equiv \mathbb{1}, & 0 \leq t < \tau_1,\\
\hat{U}_2 \equiv \me^{-\mi \hat{S}_{\text{tot}}^x \pi/2}\hat{U}_1 = \me^{-\mi \hat{S}_{\text{tot}}^x \pi/2}, & \tau_1 \leq t < \tau_1+\tau_2,\\
\hat{U}_3 \equiv\\
\hat{U}_4\\
\hat{U}_5
\end{cases}\tag{4}
$$


这些结果意味着，在哈密顿量随时间变化的情况下，我们不需要在旋转坐标系中考虑脉冲哈密顿量。

从这个结果可以得出，零阶 Floquet 哈密顿量为：

我们得到了 Floquet 哈密顿量：

## 1.2. DM 相互作用 engineering

在这里，我们讨论基于文献[^10]的 DM 相互作用的 engineering. 在这里，脉冲与 XYZ 情况不同。我们假设以下的哈密顿量：

## 1.3. Kitaev 相互作用 engineering

在这里，我们将讨论 Kitaev 相互作用的工程。在这种情况下，我们需要将全局和局域脉冲结合起来。首先，我们考虑 Kitaev 链模型。目标哈密顿量给定为：
$$
\hat{H}_{\text{target}} = J\sum_{j}(\hat{S}_{2j-1}^x \hat{S}_{2j}^x + \hat{S}_{2j}^y\hat{S}_{2j+1}^y)\tag{23}
$$

目标哈密顿量的原理如图 1 所示.![[截图-1693347330246.png#R|图 1|500]]

```ad-info
title: 图 1
基塔耶夫链。红键和蓝键分别表示 $\hat{S}_j^x \hat{S}_{j+1}^x$ 和 $\hat{S}_j^y \hat{S}_{j+1}^y$.
```

为了构造这个哈密顿量，我们考虑以下含时哈密顿量:
$$
\hat{H}(t) = \hat{H}_{\text{XY}}+\hat{H}_\text{G}(t)+\hat{H}_\text{L}(t)\tag{24}
$$
其中，$\hat{H}_\text{G}(t)$ 是全局脉冲项，而 $\hat{H}_\text{L}(t)$ 是局域脉冲项。在这里，全局脉冲的选择与 XYZ 哈密顿量的情况类似。为简单起见，我们考虑 $\tau_i \equiv \tau$. 我们引入幺正算符：
$$
\begin{align}
\hat{U}_{\text{rot}1}(t) &\equiv \hat{T} \exp\qty[-\frac{\mi}{\hs}
\int_0^t \dd{t'} \hat{H}_{\text{G}}(t')]\\
&=
\begin{cases}
\mathbb{1}, \quad& 0 \leq t < \tau,\\
\me^{-\mi \hat{S}_{\text{rot}}^x\pi/2}, &\tau \leq t < 2\tau
\end{cases}\tag{25}
\end{align}
$$


# 附录 A: Floquet 理论

在这里，我们考虑 [[Floquet theory|Floquet 理论]]. 我们考虑时间周期性的哈密顿算符 $\hat{H}(t+T) = \hat{H}(t)$，其中 $T$ 是周期。[[薛定谔方程|薛定谔方程]]表示为：
$$
\mi \hs \dv{t} \ket{\Psi(t)} = \hat{H}(t) \ket{\Psi(t)}\tag{53}
$$
我们将时间演化算符定义为
$$
\ket{\Psi(t)} = \hat{U}(t,0) \ket{\Psi(0)}\tag{54}
$$

其中 $\hat{U}(t, 0)$ 是幺正算符。我们可以形式地写成：

$$
\hat{U}(t,0) = \hat{\mathcal{T}} \exp \qty[-\frac{\mi}{\hs}\int_0^t \dd{\tau} \hat{H}(\tau)]\tag{55}
$$
从方程 53 中，时间演化算符满足
$$
\mi \hs \dv{\hat{U}(t,0)}{t}=\hat{H}(t)\hat{U}(t,0)\tag{56}
$$

初始条件为 $\hat{U}(0, 0) = \mathbb{1}$. 时间演化算符具有以下性质：
$$
\hat{U}(t_1+t_2,0) = \hat{U}(t_1+t_2,t_1)\hat{U}(t_1,0)\tag{57}
$$
当哈密顿算符是时间周期性的时候，时间演化算符满足以下性质：

$$
\hat{U}(t+T,0) = \hat{U}(t,0) \hat{U}(T,0)\tag{58}
$$
证明如下
$$
\begin{align}
\hat{U}(t+T,0) &= \hat{U}(t+T,T) \hat{U}(T,0)\\
&= \hat{U}(t,0) \hat{U}(T,0)
\end{align}\tag{59}
$$
我们利用关系
$$
\begin{align}
\hat{U}(t+T,T) &= \hat{\mathcal{T}} \exp \qty[-\frac{\mi}{\hs}\int_{T}^{t+T}\dd{\tau} \hat{H}(\tau)]\\
&= \hat{\mathcal{T}} \exp \qty[-\frac{\mi}{\hs} \int_0^t \dd{\tau'} \hat{H}(\tau'+T)]\\
&= \hat{\mathcal{T}} \exp \qty[- \frac{\mi}{\hs} \int_0^t \dd{\tau}\hat{H}(\tau)]\\
&= \hat{U}(t,0)
\end{align}\tag{60}
$$


![[截图-1693347451924.png#C|图 2 蜂窝晶格和各键的定义|200]]

![[截图-1693347648794.png#C|图 3|500]]


## A.1. 时间演化算符

## A.2. Floquet-Magnus 展开

## A.3. 例子

### A.3.1. 二能级系统

### A.3.2. Paul 阱

### A.3.3. Lattice shaking

# 附录 B: 旋转自旋的公式




[^1]: N. Goldman and J. Dalibard, Phys. Rev. X 4, 031027 (2014).
[^2]: M. Bukov, L. D’Alessio, and A. Polkovnikov, Adv. Phys. 64, 139 (2015).
[^3]: M. Holthaus, J. Phys. B: At. Mol. Opt. Phys. 49, 013001 (2016).
[^4]: H. Levine, A. Keesling, G. Semeghini, A. Omran, T. T. Wang, S. Ebadi, H. Bernien, M.
Greiner, V. Vuletić, H. Pichler, and M. D. Lukin, Phys. Rev. Lett. 123, 170503 (2019).
[^5]: J. Choi, H. Zhou, H. S. Knowles, R. Landig, S. Choi, and M. D. Lukin, Phys. Rev. X 10,
031002 (2020).
[^6]: S. Geier, N. Thaicharoen, C. Hainaut, T. Franz, A. Salzinger, A. Tebben, D. Grimshandl, G. Zürn, and M. Weidemüller, Science, 374, 1149 (2021).
[^7]: P. Scholl, H. J. Williams, G. Bornet, F. Wallner, D. Barredo, L. Henriet, A. Signoles, C. Hainaut, T. Franz, S. Geier, A. Tebben, A. Salzinger, G, Z¨urn, T. Lahaye, M. Weidemüller, and A. Browaeys, PRX QUANTUM 3, 020303 (2022).
[^8]: M. Kalinowski, N. Maskara, and M. D. Lukin, arXiv:2211.00017 (2022).
[^9]: B.-Y. Sun, N. Goldman, M. Aidelsburger, and M. Bukov, PRX Quantum 4, 020329 (2023).
[^10]: N. Nishad, A. Keselman, T. Lahaye, A. Browaeys, and S. Tsesses, arXiv:2306.07041 (2023).