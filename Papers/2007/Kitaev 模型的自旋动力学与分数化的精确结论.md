---
tags:
  - 论文
created: 2023-08-16 18:00:28
aliases:
  - Exact Results for Spin Dynamics and Fractionalization in the Kitaev Model
DOI: https://doi.org/10.1103/PhysRevLett.98.247201
author:
  - "[[G. Baskaran]]"
  - "[[Saptarshi Mandal]]"
  - "[[Ramamurti Shankar|R. Shankar]]"
original title: Exact Results for Spin Dynamics and Fractionalization in the Kitaev Model
year: "2007"
---

# 摘要

我们在 Kitaev 模型中提出了某些动态自旋相关函数的精确分析结果。这是非平凡量子自旋模型中首次获得的这种结果。该结果也是新颖的：尽管存在无间隙传播的 Majorana 费米子激发，但动态双自旋相关函数在超过最近邻距离后完全为零。这表明存在一个*无间隙但有限范围*的自旋液态。

我们还展示了一种不寻常的、在所有能量尺度上的自旋翻转量子分数化现象，将其分解为两个无限质量的通量和一个动态的 Majorana 费米子。由于 Kitaev 模型是拓扑量子计算的典型示例，我们的结果为了量子比特的动态和拓扑激发的生成提供了新的见解。

# 正文

在量子计算和量子通信领域，寻找能够稳定并*避免退相干*的实用量子比特是一个首要挑战[^1]。在这个背景下，Kitaev 提出了[^2]在强关联的量子多体系统中出现的某些紧密相关的拓扑激发作为稳定的量子比特。在容错量子计算方案中[^2][^3][^4]，Kitaev 构建了一个非平凡且精确可解的二维自旋模型[^2]，并阐述了基本思想。在某些极限情况下，它也成为了著名的 “toric code 码” 哈密顿量。在最近提出的实验实现方案[^5][^6]和操控与检测方案[^7]之后，Kitaev模型已经更接近现实。在初始化、错误修正和读出操作中，直接从外部访问的是“自旋”，而不是紧密相关的拓扑自由度。因此，对动态自旋相关性的理解至关重要。

我们针对 Kitaev 模型中任意本征态的时间相关自旋相关函数提出了一些确切的分析结果。我们的结果是非平凡且新颖的，可能对新的量子计算方案产生影响。此外，我们的结果在某种意义上是独特的，因为它是首个在非平凡的二维量子自旋模型中得到的平衡动态自旋相关函数的确切结果。我们的结果适用于具有周期性边界条件的任何晶格尺寸。

我们展示了动力学双自旋相关函数在所有时间 $t$, 所有耦合常数 $J_x$, $J_y$ 和 $J_z$ 的取值范围内都是短程的，在最近邻位点之外完全消失，即使在模型的 $J$ 值范围内，该模型是无间隙的。

我们的结果严格地表明，它是一种*短程*[[量子自旋液体]]，*长程自旋序是不存在的*。我们获得了关于时间依赖性的紧凑形式，从而使物理现象更加透明。Kitaev 模型支持动态的 Majorana 费米子和静态的 $\pi$-flux 本征激发，具有其自身 sharp 的量子数。特别是，局部自旋算符的任何分量 $\sigma_i^\alpha$ 会在位点 $i$ 创建一个 $Z_2$ 荷，并在适当的平面上形成一个绑定的 $Z_2$ 通量对，这些平面共享位点 $i$（见图3）。

我们展示了这个复合体会发生量子数分数化[^8][^9]，意味着 $Z_2$ 荷和通量会在*空间*上分离.

在本研究中，我们限制了我们的计算范围，仅涉及到对于时间无关的哈密顿量，在任意本征态和热态下的动态相关函数。在实际的量子计算中，关键的操作，比如编织（braiding），涉及到哈密顿量的参数变化以及拓扑自由度的绝热传输[^7]。原则上，一些需要的“非平衡”动态相关函数可能通过将我们的结果与适当的[[Berry 相位]]因子进行卷积来获得。

在我们的工作中，我们遵循Kitaev的方法[^2]，使用自旋 $1/2$ 算符的 Majorana 费米子表示和一个扩展的希尔伯特空间。值得注意的是，由于 Kitaev 模型中存在某些局部守恒量，希尔伯特空间的扩展只会产生“规范副本”，而不会改变能谱。而对于使用扩展的费米子希尔伯特空间研究标准的二维海森堡模型时，这种豪华并不存在[^9][^10]. 

Kitaev 哈密顿量是

$$
H = -\sum_{\ev{ij}_x}J_x S_i^xS_j^x
-\sum_{\ev{ij}_y}J_y S_i^yS_j^y
-\sum_{\ev{ij}_z}J_z S_i^zS_j^z\tag{1}
$$
其中 $i, j$ 标记了一个六边形格点的位置，$\ev{ij}_a$ 表示第 $i$ 和 $j$ 个格点之间的连接。该模型没有连续的全局自旋对称性。所有键之间的相互作用都类似于 [[伊辛模型|Ising 模型]]，尽管在 $x$、$y$ 和 $z$ 三个不同的量子化方向上，存在三种不同的键类型，使得该模型 quantum mechanical. 

此外，它产生了很高程度的*阻挫*，即使在经典水平上，一个给定的自旋也不能同时满足来自3个相邻格点的矛盾要求，这些要求涉及到彼此正交方向上的取向。该模型具有丰富的局部对称性。每个基本六边形中 6 个自旋分量的特定乘积，$\sigma_1^y\sigma_2^z\sigma_3^x\sigma_4^y\sigma_5^z\sigma_6^x$（图1），与整个哈密顿量相对易。![[截图-1692756071001.png#R|图 1|400]]

```ad-info
title: 图 1
初等六边形和“键费米子”结构。一个自旋被 4 个马约拉纳费米子( $c, c^x, c^y, c^z$ )所取代。定义了键费米子 $\chi_{\ev{23}}$ 和自旋算符。$A$ 和 $B$ 表示子格指标。
```

因此，在六边形格点的每个对偶格点 (dual lattice site) 上都存在一个守恒的 $Z_2$ 荷 $\pm 1$. 该模型是精确可解的，并且成为非相互作用的 Majorana 费米子，在静态 $Z_2$ 规范场的背景中传播。

不同的可能的 $Z_2$ 电荷将希尔伯特空间分为 [[超选择区域|super selected sectors]]. 基态对应于所有 $Z_2$ 电荷为 $+1$ 的情况。在这个 sector 中，在一系列的 $J$ 值范围内，包括特殊点 $J_x=J_y=J_z$，Majorana 费米子是无间隙的.

在 Kitaev 的工作中，我们使用马约拉纳费米子来表示自旋。在每个格点上，我们定义了4个马约拉纳费米子 $c^\alpha,\ \alpha = 0, x,y,z$，且 $\acomm{c^\alpha}{c^\beta}=2\delta_{\alpha \beta}$.

四个马约拉纳(实)费米子合并形成了两个复费米子，从而构建了一个四维的[[希尔伯特空间|希尔伯特空间]]。马约拉纳费米子的希尔伯特空间维度理论上是 $\sqrt{2}$，一个无理数，这提醒我们在物理问题中马约拉纳费米子必须成对出现（导致在实际问题中存在一个 $\sqrt{2} \times \sqrt{2}=2$ 维的 Fock 空间）。

$N$ 个自旋的希尔伯特空间维度是 2的N次方。扩展的希尔伯特空间维度为4N的2次方 × 2的π次方 × 2的π次方 × 2的π次方 × 2的π次方 × ... × 2的π次方（重复N次）。

物理希尔伯特空间中的状态矢量满足以下条件...


当投影到物理希尔伯特空间时，上述定义的算子满足自旋 $1/2$ 算子代数 $\comm{\sigma_i^a}{\sigma_j^b} = \mi \epsilon_{abc}\sigma^c \delta_{ij}$. 哈密顿函数用马约拉纳费米子来表示
$$
H = -\sum_{\alpha=x,y,z} J_\alpha \sum_{\ev{ij}_\alpha} \mi c_i \hat{u}_{\ev{ij}_\alpha} c_j \tag{4}
$$

其中, $\hat{u}_{\ev{ij}_\alpha} = \mi c_i^\alpha c_j^\alpha$. Kitaev 表明 $\comm{H}{\hat{u}_{\ev{ij}_\alpha}}=0$ 和 $\hat{u}_{\ev{ij}_\alpha}$ 成为具有特征值 $\pm 1$ 的运动常数. 变量uhijia是通过化学键上的静态(Ising) Z2规范场确定的。基塔耶夫哈密顿量[公式(6)]在扩展的希尔伯特空间中具有局部Z2规范不变性。

总之，本论文为 Kitaev 模型的自旋动力学提供了一些精确的分析结果，并提出了一种自旋翻转分数化方案。由于这个非平凡的自旋模型也是一个用于拓扑量子计算的模型，我们的精确结果应该为量子比特动力学提供了洞察力，以及产生紧密拓扑量子比特的可能方式。

我们的形式体系利用了扩展希尔伯特空间中的本征函数的分解特性，可以很容易地适用于多自旋相关函数的计算，这是计算和理解量子纠缠性质的关键步骤。

$$
\ket{\tilde{\Psi}} = \ket{\mathcal{M}_{\mathcal{G}};\mathcal{G}} \equiv \ket{\mathcal{M}_{\mathcal{G}}}\ket{\mathcal{G}}\tag{6}
$$

$$
\chi_{\ev{ij}_a}^\dagger \chi_{\ev{ij}_a} \ket{\mathcal{G}}
= n_{\ev{ij}_a}\ket{\mathcal{G}}\tag{7}
$$

现在我们要计算物理子空间中的自旋-自旋关联。由于自旋算符是规范不变量，我们可以计算任何规范固定扇区中的关联，其答案将与物理规范不变量子空间中的答案相同。(我们已经通过对投影物理子空间的计算证实了这一点。)因此，我们考虑了基塔耶夫哈密顿函数任意本征状态下的双自旋动力关联函数

现在我们希望在物理子空间中计算自旋-自旋关联函数。由于自旋算符是*规范不变*的，我们可以在任何规范固定的部分计算关联，并且答案将与物理规范不变子空间中的结果相同（我们已经通过在投影的物理子空间中进行计算来确认了这一点）。因此，我们考虑在某个固定规范场配置 $\mathcal{G}$ 下 Kitaev 哈密顿量的任意本征态中的2自旋动力学关联函数

$$
S_{ij}^{\alpha \beta}(t) = \bra{\mathcal{M}_{\mathcal{G}}}\bra{\mathcal{G}}
\sigma_i^\alpha(t) \sigma_j^\beta(0) \ket{\mathcal{G}}
\ket{\mathcal{M}_\mathcal{G}}
$$

要计算 $g_{\ev{ij}_{\alpha}}(t)$，我们从方程（7）和（8）中代入σ。我们选择一个规范，其中 uhijia = -1，意味着 χ† hljib |Gi = χ† hikib |Gi = 0。我们注意到，在 t = 0 时施加的上述条件将在任何时刻继续成立，因为键合费米子数是守恒的。因此，我们有：




[^1]: M. A. Nielsen and I. L. Chang, Quantum Computation and Quantum Information (Cambridge University Press, Cambridge, England, 2000); C. H. Bennett and D. P. DiVincenzo, Nature (London) 404, 247 (2000); J. Preskill, Phys. Today 52, No. 6, 24 (1999); A.Yu. Kitaev, A. H. Shen, and M. N. Vyalyi, Classical and Quantum Computation (American Mathematical Society, Providence, 2002); S. das Sarma, M. Friedman, and C. Nayak, Phys. Today 59, No. 7, 32 (2006).
[^2]: [[通过任意子的可容错量子计算_Kitaev]], [[精确可解模型及其他中的任意子_Kitaev]]
[^3]: J. Preskill, arXiv:quant-ph/9712048.
[^4]: M. Freedman, M. Larsen, and Z. Wang, Commun. Math. Phys. 227, 605 (2002).
[^5]: L. M. Duan, E. Demler, and M. D. Lukin, Phys. Rev. Lett. 91, 090402 (2003).
[^6]: A. Micheli, G. K. Brennen, and P. Zoller, Nature Phys. 2, 341 (2006).
[^7]: C. Zhang et al., quant-ph/0609101.
[^8]: R. Jackiw and C. Rebbi, Phys. Rev. D 13, 3398 (1976); S. Kivelson, P. Rokshar, and J. Sethna, Phys. Rev. B 35, 8865 (1987); W. P. Su, J. R. Schrieffer, and A. J. Heeger, Phys. Rev. Lett. 42, 1698 (1979); L. D. Fadeev and L. A. Takhtajan, Phys. Lett. 85A, 375 (1981); R. B. Laughlin, Phys. Rev. Lett. 50, 1395 (1983); P.W. Anderson, Science235, 1196 (1987); G. Baskaran and R. Shankar, Mod. Phys. Lett. B 2, 1211 (1988); V. Kalmeyer and R. B. Laughlin, Phys. Rev. Lett. 59, 2095 (1987); T. Senthil and M.P. A. Fisher, Phys. Rev. B 62, 7850 (2000).
[^9]: G. Baskaran, Z. Zou, and P.W. Anderson, Solid State Commun. 63, 973 (1987).
[^10]: B. S. Shastry, Phys. Rev. Lett. 60, 639 (1988).