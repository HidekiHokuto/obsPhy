---
tags: 
- 论文
- Floquet态
- Shaking 光晶格
- 拓扑序
- 反常霍尔效应
- 拉曼耦合
- Su-Schrieffer-Heeger模型
- Haldane模型
created: 2023-06-05 13:49:58
aliases: []
---

| 原标题 | 作者|年份|
|:-:|:-:|:-:|
|Floquet Topological States in Shaking Optical Lattices|Wei Zheng, Hui Zhai|2014|

# Abstract

在这份快速通信中，我们提出了通过振动光学晶格来实现拓扑非平凡Floquet态的现实方案，以一维晶格和二维蜂窝晶格作为示例。在二维模型中的拓扑相展现了量子反常霍尔效应。通过振动频率和振动幅度，可以轻松控制拓扑平凡和非平凡态之间的转变。我们的方案具有两个主要优势。首先，静态哈密顿量和振动方案都相对简单易实现。其次，它需要相对较小的振动幅度，因此可以将加热效应最小化。这两个优势使得我们的方案更加实用。

# Introduction

在平衡系统中，拓扑态物质已经得到广泛研究。最近，在周期驱动的非平衡系统中提出了一种称为“Floquet拓扑绝缘体”的拓扑非平凡量子态[1-3]。Floquet拓扑能带已经在光子晶体中首次实现，并观察到了光的*边缘态*[4]，***但迄今为止尚未在任何固态或冷原子系统中实现***。

冷原子物理学中，实现和研究拓扑态物质也是当前的主要趋势之一，其中包括了*Raman laser coupling* [5-12]和 *shaking optical lattice* [13-15]的发展。已经证明，快速振动的光学格子可以产生合成的阿贝尔规范场和磁通量[13,14]，并存在各种理论提议[16-25]。在这篇快速通讯中，我们提出振动光学格子也是实现冷原子系统中Floquet拓扑态的强大工具。我们证明了等效于Su-Schrieffer-Heeger模型在一维中的系统[26]和等效于Haldane模型在二维蜂窝格子中的系统[27]可以实现，后者展示了量子反常霍尔效应。

迄今为止，量子反常霍尔效应只在掺铬的 $(\text{Bi},\text{Sb})_2\text{Te}_3$ 材料中发现，而生长这种材料非常具有挑战性[29]。因此，通过*冷原子系统进行量子模拟这种效应是非常可取的*。然而，尽管已经有几种使用原子-光相互作用的提议[20-25]，但这种效应在冷原子实验中尚未实现。关键的技术挑战是设计一个足够简单、可以在当前可用的实验装置中实施，并且可以***避免不必要的加热的方案***。我们的方案满足了这两个要求，因此可以帮助克服这个挑战。

1. 首先是其*简单性*。要在静态系统中实现拓扑态，通常需要特殊形式的跃迁项。例如，为了实现Haldane模型[28]，需要生成一种特殊的 next-nearest range hopping term，通常需要在冷原子系统中实现laser-assisted tunneling [9-12]。相比之下，在我们的方案中，静态哈密顿量非常简单（只包含普通的最近邻跃迁项，没有额外的相位因子），并且已经在不同实验室中实现过。我们将展示这个方案的优雅之处在于，当适当且足够简单的 shaking 方式启动时，这样简单的静态哈密顿量可以导致拓扑非平凡态的出现。

2. 其次是减小 heating 问题。与其他 shaking 方案[13,14]不同，我们方案的一个关键因素是摇晃提供了不同能带之间的 resonant coupling；因此，正如我们稍后将展示的，为了达到拓扑相，它只需要比晶格间距小得多的摇晃幅度，从而避免了在利用原子-光相互作用方案中经常遇到的 heating 问题。最近由芝加哥小组进行的实验发现，来自如此小的摇晃幅度的加热是微不足道的[15]。

我们还要指出，在蜂窝格子中，我们的摇晃方案在数学上可以被看作是为中性原子产生了合成的圆偏振光[1,30]。然而，要在石墨烯中用真实光实现这一点，所需的频率必须在 [[soft x-ray]] regime 内[30]，这使得实验极具挑战性。而在我们的方案中，所需的摇晃频率在数百赫兹左右，非常实用。
# General method

> [! tip] Floquet 理论
>我们对振动光学晶格的理论处理是基于 [[Floquet theory|Floquet 理论]]。周期为 $T$ 的 periodically driven Hamiltonian $\hat{H}(t)$ 的 Floquet 算符的定义为 $(\hslash= 1)$
>$$\hat{F} = \hat{U}(T_i+T,T_i)=\hat{\mathcal{T}}\exp \qty[
>	-\mi \int_{T_i}^{T_i+T} \dd{t} \hat{H}(t)
>]\tag{1}$$
>其中 $\hat{\mathcal{T}}$ 表示 time order.
>
>$\hat{F}$ 的本征值和本征态为
>$$
>\hat{F} \ket{\varphi_n} = \me^{-\mi \energy_n T}\ket{\varphi_n}\tag{2}
>$$
$−π/T < ε_n < π/T$ 表示 quasienergy 区间。

下面介绍了两种不同的方法来评估 Floquet 算符，每种方法都有其自身的优势。


## 方法 1

我们可以根据方程（1）对 Floquet 算符进行数值计算，并从方程（2）中确定其特征值和特征波函数。如果一个周期性驱动的系统展示出非平凡的拓扑态，那么必定存在 in-gap quasienergies $ε$ 及其相应的波函数 $ϕ$ 在系统边缘上有很好的空间局域性[2]。这种方法的优势在于，一旦给定 $\hat{H}(t)$，就不需要进一步的近似。

## 方法 2

我们可以通过 $\hat{F} = \me^{-\mi \hat{H}_{\text{eff}}T}$ 引入一个不含时的有效哈密顿量 $\hat{H}_{\text{eff}}$. 将 $\hat{H}(t)$ 展开为
$$\hat{H}(t)= \sum_{n=-\infty}^\infty \hat{H}_n(t)\ \me^{\mi n \omega t}$$

![[截图-1686044147566.png#CENTRE|FIG. 1|300]]

其中 $ω=2π/T$，我们考虑如图 1(a) 所示的情况，即静态成分 $\hat{H}_0$ 在能量范围 $\Delta$ 内包含 $m$ 个能带，并且 $ω \gg Δ$。以下讨论的两个具体示例要么属于这种情况，要么可以通过旋转波变换转化为这种情况，其中 $m = 2$。在这种条件下，可以直接证明在 $\Delta/ω$ 的数量级下，可以得到 $\hat{H}_\text{eff}$ 的表达式

$$\hat{H}_\text{eff}
= \hat{H}_0 + \sum_{n=1}^\infty
\qty{
\frac{\comm{\hat{H}_n}{\hat{H}_{-n}}}{n \omega}
- \frac{\comm{\hat{H}_n}{\hat{H}_0}}{\me^{- 2\pi n \mi \alpha}n \omega}
+ \frac{\comm{\hat{H}_{-n}}{\hat{H}_0}}{\me^{2 \pi n \mi \alpha}n\omega}
}$$

其中，将 $T_i$ 取为 $αT$，其中 $0 \leq α < 1$. 由于 $\hat{F}$ 在不同初始时间 $T_i$ 的选择下只相差一个幺正变换，所以准能量εn不依赖于Ti的选择。特别地，我们可以选择一个最佳的 $α$ 来简化 $\hat{H}_{\text{eff}}$.

然后，我们可以将用于时间独立哈密顿量的方案应用于 $\hat{H}_\text{eff}$ 以对这个周期性系统的拓扑进行分类。尽管该方法涉及进一步的近似，但其优点是物理上更透明，并且*可以揭示与平衡系统中的拓扑现象的联系*。

## 一维情况
一维晶格由两束反向传播的激光形成。当一个激光周期性地调制两束激光之间的相对相位 $θ$ 时，将导致一个时间依赖的晶格势场 [31,32]，如图1(b)所示
$$H(t) = \frac{\hat{k}_x^2}{2m}
+ V \cos^2 [k_r x + \theta(t)]\tag{4}$$

其中 $θ(t) = k_rb \cos(ωt)$，$b$ 是晶格的最大位移。通过转换到 comoving 参考系，$x \to x + b \cos(ωt)$，哈密顿量获得一个时间相关的矢势项，表示为

$$H(t) = \frac{\hat{k}_x^2}{2m}
+V \cos^2(k_r x)
-b \omega \sin(\omega t)\vdot \hat{k}_x
\tag{5}
$$
前两个静态项给出了带有 Bloch 波函数 $ϕ_λ(k_x)$ 的静态带结构。在此基础上，只保留 $s$ 和 $p$ 带，我们可以写出一个 tight-binding 的哈密顿量为

$$
\hat{H}(t)
= \sum_i \hat{\Psi}_i^\dagger K(t)
\hat{\Psi}_i
+\sum_i \qty[
	\hat{\Psi}_i^\dagger
	J(t) \hat{\Psi}_{i+1}
	+ \text{H.c.}
]
$$

其中, $\hat{\Psi}_i^\dagger = \qty(\hat{a}_{p,i}^\dagger, \hat{a}_{s,i}^\dagger)$ 是 $s$ 轨道和 $p$ 轨道的生成算符.

$$K(t)=
\mqty(
	\energy_p & \mi h_0^{sp} \sin{\qty(\omega t)}\\-\mi h_0^{sp} \sin{\qty(\omega t)}& \energy_s
)
$$
$$
J(t) = \mqty(
t_p & -\mi h_1^{pp} \sin{\qty(\omega t)}\\
-\mi h_1^{sp} \sin{\qty(\omega t)}
& t_s - \mi h_1^{ss} \sin{\qty(\omega t)}
)
$$
其中 $\energy_s$ 和 $\energy_p$ 为 on-site 能量，$t_s$ 和 $t_p$ 为来自静态部分的跳跃振幅，符号 $h_0^{sp}$ 表示由 shaking 引起的 on-site 耦合过程，其计算方式为
$$h_0^{sp} = bω \int\dd{x} \phi_s(x)\  ∂_x \phi_p(x)$$
符号 $h_1^{\lambda\lambda'}$ 表示由 shaking 引起的最近邻跃迁过程，其中 $λλ'=ss,pp,sp$.

现在的 $\phi_s(x)$ 和 $\phi_p(x)$ 是两个轨道的[[Wannier wave function|万尼尔函数]], $a=\pi/k_r$ 为晶格常数. 