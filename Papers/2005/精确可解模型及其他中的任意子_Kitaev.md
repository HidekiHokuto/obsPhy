---
tags:
  - 论文
  - 任意子
  - Kitaev模型
created: 2023-06-29 23:24:10
aliases:
  - Anyons in an exactly solved model and beyond_Kitaev
DOI: https://doi.org/10.1016/j.aop.2005.10.005
原标题: Anyons in an exactly solved model and beyond
author:
  - "[[Alexei Kitaev]]"
年份: " 2005"
---

# 摘要

研究了蜂窝状格点上的自旋 $1/2$ 系统。最近邻之间的相互作用可以是 $XX$ 型、$YY$ 型或 $ZZ$ 型，取决于连接的方向；不同类型的相互作用可能强度不同。

该模型通过将其化归为静态 $Z_2$ 规范场中的自由费米子而得到了精确解。在参数空间中获得了相图。其中一个相*具有能隙*并携带*阿贝尔任子*的激发。另一个相是*无能隙*的，在存在磁场时会获得能隙。在后一种情况下，激发是*非阿贝尔任子*，其编织规则与伊辛模型的 conformal blocks 相同。我们还考虑了具有有能隙谱的自由费米子的一般理论，其特征是 spectral 陈数 $\nu$。原始模型的阿贝尔相和非阿贝尔相分别对应于 $ν = 0$ 和 $ν = ±1$. 激发的任意性质取决于 $ν \mod 16$，而 $ν$ 本身控制着边界的热传输。该论文还提供了关于任子的数学背景以及对准对角矩阵的陈数的基础理论。

---

## 内容点评

当然，这篇论文的主要结果是一个特定二维量子模型的确切解法。然而，我花了很长时间来完善这个结果，推导模型的一些性质，并将其放入一个更一般的框架中。因此，许多相关的内容也随之出现。其中一些源于避免使用共形场论的愿望，因为共形场论更适用于*边缘激发*而不是 bulk 物理。这个计划在某种程度上取得了成功，但仍然使用了一些*共形场论*的基本原理 (即*拓扑自旋* $θ_a = \me^{2π \mi(h_a−\overline{h}_a)}$ 和 chiral central charge $c_- = c − \overline{c}$)。

该论文是自包含的，并提供了该主题的介绍。对于大多数读者来说，一个好的策略是跟随论文的阐述直到第8节的开始，即非阿贝尔任意子，然后浏览该节的其余部分，其中内容变得更加技术性。但对于数学倾向的读者，他们可能对这些细节感兴趣，以及一些附录。我试图使论文具有模块化的结构，使其某些部分可以在不详细阅读其他部分的情况下理解。这导致了一些冗余内容。附录E《任意子的代数理论》是关于单位模块范畴的初级介绍，它扩展了第8节中的讨论。

这篇论文是自包含的，并提供了对这个主题的介绍。对于大多数读者来说，一个很好的策略是跟随论文的阐述直到第8节的开始，即*非阿贝尔任意子*，并浏览该节的其余部分，其中内容变得更加技术性。但对于数学倾向的读者来说，他们可能对这些细节感兴趣，以及一些附录。我尽力使论文具有模块化的结构，以便其中的某些部分可以在不详细阅读其他部分的情况下理解。这导致了一些冗余内容。

附录E《任意子的代数理论》是关于单位模块范畴的初级介绍，它扩展了第8节中的讨论。

附录C《准对角矩阵》也主要是陈述性的，但其中的一些论证可能是新的。它以对 “operator flow” 和 “noncommutative Chern number” 的简化处理开始（后者已被用于证明无序系统中的霍尔电导的量子化[^1]），但主要目标是解释“未配对的Majorana模式”，这是与陈数相关的一种特定的奇偶现象。

附录D关于手性中心荷和附录F关于*弱对称性破缺*包含一些可能最终发展成有趣理论的初步想法。

---

# 0. 导言

## 主题概述

任意子是具有非传统统计特性（既不是玻色子也不是费米子）的粒子，只能存在于二维空间中。量子统计可以被理解为一种特殊的相互作用：当两个粒子沿着特定轨道交换位置时，整体的量子态会乘以 $\me^{\mi \varphi}$。
- 在三维空间中，交换两个粒子只有一种拓扑上不同的方式。两次交换等同于恒等变换，因此 $\me^{\mi \varphi} = \pm1$。
- 相反，在二维空间中，双重交换对应于一个粒子围绕另一个粒子做一整个旋转；这个过程在拓扑上是非平凡的。因此，交换相位 $\varphi$ 可以原则上取任何值，因此被称为“任意子”（不过，稳定性的考虑要求ϕ是2π的有理倍数）。当然，真正的问题是这样的粒子是否存在于自然界中或是否可以以某种方式构建，但我们将沿着历史的路径，从数学的角度接近这个问题。

在20世纪80年代初，威尔切克（Wilczek）[^2][^3]开启了对任意子的研究。他提出了一个简单但相当抽象的模型，该模型基于 $(2 + 1)$ 维电动力学。这个理论具有*整数电荷*和携带磁通量（实数，定义上差一个整数）的涡旋。单独考虑，这两种粒子都是玻色子。但当一个电荷 $q$ 绕一个涡旋 $v$ 旋转时，它会累积相位 $2πqv$，被称为 *Aharonov-Bohm 相位*。因此，电荷和涡旋具有非平凡的*相互*统计，因此当它们在一起考虑时必须称为任意子。此外，由电荷和涡旋组成的复合物 $(q,v)$ 本身就是任意子，因为它们具有非平凡的交换相位 $\varphi_{(q,v)} = 2πqv$。

一种描述量子统计的一般方法是考虑粒子在 $(2+1)$ 维时空中的世界线。这样的世界线形成了一个 braid，因此统计性质由 braid group 的表示来描述。在前面的讨论中，我们假设编织*仅由相位因子来描述*，即表示是一维的。相应的任意子被称为*阿贝尔任意子*。但也可以考虑编织群的多维表示；在这种情况下，任意子被称为*非阿贝尔任意子*。实际上，编织群的作用方式可能并不那么重要，而与几个粒子相关联的多维空间的存在本身就是一个关键特征。这个空间中的向量是几乎具有相同能量的量子态（见下面关于拓扑量子计算的讨论）。

从历史上看，非阿贝尔任意子的理论起源于*共形场论*（CFT）。然而，对于任意子而言，只有共形理论中的拓扑和代数结构是相关的。这个结构的不同部分是在许多人的巨大工作中发现的，最终在 Moore 和 Seiberg 的论文中达到了顶峰[4]。Witten 关于量子 Chern-Simons 理论的工作[5]也具有很大的影响力。Fredenhagen、Rehren 和 Schroer[6] 以及Frohlich 和 Gabbiani[7]则采用了一种更抽象的方法（基于 local field theory）进行了研究。

最令人惊奇的是，任意子实际上作为某些凝聚态系统中的激发存在着。这些系统还具有*高度非平凡的基态*，被描述为具有*拓扑序*的系统。最为研究广泛的例子（无论是理论上还是实验上）是在填充因子 $ν = 1/3$ 的分数量子霍尔系统中的 Laughlin 态[8]。它携带有交换相位 $\varphi = π/3$ 和电荷 $±1/3$ 的阿贝尔任意子。这个电荷的分数值是在原始的 Laughlin 的论文中预测并通过多种方法确认的，特别是通过 shot noise measurement[9, 10]。统计相位是一种更微妙的性质，可以通过理论推导得到[11, 12]；最近通过 quasiparticle tunneling 的实验测试也得到了非平凡的结果[13]。

在填充因子 $ν = 5/2$ 时观察到了一种不同类型的态，尽管它更为脆弱且在实验上研究较少。有很多证据表明这个系统可以用 Moore 和 Read 提出的优美理论来描述[14, 15]。Moore-Read 态具有电荷 $±1/4$ 的非阿贝尔任意子。如果存在 $2n$ 个这样的粒子，相关的希尔伯特空间的维数为 $2n−1$。（本文中研究的非阿贝尔任意子具有类似的性质，尽管没有电荷。）

任意子的概念假设基态*具有能隙*（至少对于拓扑非平凡的准粒子）。否则，激发无法定位，且编织操作可能无法定义。需要注意的是，如果所有激发都有能隙，那么所有 equal-time correlators 都会随着距离的增加呈指数衰减[16]。

一个具有自旋 $1/2$ 的系统中的任意子的例子源于*共振价键理论*（RVB）。RVB 的概念由 Anderson 提出，并在后来被用作高温超导铜氧化物中未掺杂的绝缘相的模型[18]。在没有电荷空穴的情况下，该问题似乎可以用类海森堡的哈密顿量来描述，但其解决方案非常困难。已经提出了几种 RVB 态的变体，既有有能隙的也有无能隙的。在这里，我们讨论一种特殊的有能隙 RVB 相，即在三角格子上实现的相[19]，但在方格子上似乎也存在。

这个相容许四种类型的准粒子：
1. 平凡的激发（如自旋波）
2. 自旋子（自旋 $1/2$ 的费米子，模2守恒）
3. $Z_2$ 涡旋（无自旋的玻色子，也称为 visons）
4. spinon-vison 复合态[20]。

自旋子和 vison 的相互统计由阿哈诺夫-博姆因子 $-1$ 所描述，因此复合粒子是玻色子。需要注意的是，这个理论与铜氧化物超导体的关联性还存在争议。Senthil 和 Fisher 提出了一种有趣的方法来检测这些材料中的 vison[21]，但实验证实了一个负结果[22]。然而，某种形式的RVB态可能在不同的材料中实现，例如 $\text{Cs}_2\text{CuCl}_4$. 这个结论是通过中子散射实验得出的，该实验显示出存在自旋 $1/2$ 的激发[23]。

![[截图-1688212271012.png|Figure 1|400]]
> 一个经典的涡旋（a）被涨落所扭曲（b）。

任意子粒子最好被视为一种*拓扑缺陷*，揭示了基态的非平凡性质。因此，任意子具有一些*拓扑量子数*，使它们保持稳定：单个粒子不能在局部被湮灭，只能通过与反粒子融合才能消失。一个直观的方式来描绘一个任意子是想象一个存在于具有局域序参量的介质中的涡旋（参见图1a）。现在假设量子涨落非常强烈，以至于序参量完全被洗去，只留下拓扑性质（参见图1b）。当然，这只是一个粗略的描绘。它类似于具有幂律相关衰减的 Kosterlitz-Thouless 相，而在任意子系统中，由于能隙的存在，相关性衰减是指数级的。

在一个正方形格点上，可以构建一个真实的例子，其中边缘的自旋由变量 $s_j = ±1$ 来描述，这可以被看作是一个 $\mathbb{Z}_2$ 规范场（即“矢势”），而在每个 plaquette $p$ 上的“磁场强度”可以表示为：

$$
w_p = \prod_{j \in \text{boundary}(p)} s_j
\tag{1}
$$

如果 $w_p = -1$，则我们说平面 $p$ 上存在一个涡旋。现在我们可以定义*无涡旋态*
$$
\ket{\Psi} = c \sum_{\vb*{s}:\ w_p(\vb*{s})=1,\ \forall p}\ket{\vb*{s}}, \qq{where} \vb*{s} = (s_1, \cdots, s_N) \tag{2}
$$

^9665af

（$c$ 是一个归一化因子）。类似地，单个涡旋存在于特定平面的态可以类似地定义。显然，通过测量沿任何*封闭路径* $l$ 的可观测量 $\prod_{j \in l} σ^z_j$, 可以检测到涡旋的存在，尽管不存在局域序参量。

态 [[精确可解模型及其他中的任意子_Kitaev#^9665af|(2)]] 可以表示为以下具有四体相互作用的哈密顿量的基态[24]:
$$
H = -J_e \sum_{\text{vertices}} A_s -J_m\sum_{\text{plaquettes}}B_p
\tag{3}
$$

^44212c

其中 $A_s = \prod_{\text{star}(s)} \sigma_j^x,\quad B_p = \prod_{\text{boundary}(p)}\sigma_j^z$.

该模型的基本激发是具有能量 $2J_e$ 的 $Z_2$ 电荷和能量 $2J_m$ 的涡旋。该模型的某些基本特征对于小的局域扰动是稳定的（例如外部磁场或相邻自旋之间的*海森堡相互作用*）。需要注意的是，激发的稳定特征不是能量或 the property of being elementary，而是 *superselection sector*。超选择扇区被定义为通过*局部算符*可以相互转化的一类态。该特定模型具有
1. vacuum sector 1
2. 电荷扇区 $e$
3. 涡旋扇区 $m$
4. 电荷-涡旋复合体 $ε$

类型为 $e$ 和 $m$ 的粒子是玻色子，具有非平凡的相互统计关系，而 $ε$ 是费米子。因此，该模型代表了拓扑序的普适类别，实际上与 RVB 相同。

任意子超选择扇区可能与传统量子数（如自旋或电荷）有关，也可能没有关联。大多数研究都集中在任意子携带*分数电荷*或*半整数自旋*的情况下。这种任意子在实验上可能更容易找到，因为它们对集体效应（特别是电流）有贡献，或者在自旋相关散射中具有特定的选择规则。无电荷和无自旋的准粒子通常更难识别。但是，由于其拓扑稳定性，任意子必须具有某些可观测的特征。例如，任意子可以被杂质困住并在那里停留足够长的时间，从而改变局部模式（magnons、excitons 等）的能谱。***然而，目前还没有找到观察任意子的有效方法。***

因此，寻找任子和拓扑序是一项艰巨的努力。我们为什么要关注这些呢？首先，因为它们是概念上重要的现象，打破了一些范式。特别是，考虑以下原则（在许多情况下起到重要的指导作用）：

1. 来自对称性的守恒定律（通过诺特定理或其量子模拟）；
2. 对称性最初存在于哈密顿量（或拉格朗日量）中，但可能会自发破缺。

让我们将讨论限制在规范对称性和局域守恒定律的情况下，这些对称性由超选择扇区之间的融合规则描述。对于第一原理及其潜在假设的深入理解归功于 Doplicher 和 Roberts [25, 26]。他们证明了任何一致的*玻色子融合规则系统*都等价于某个*紧致群*的不可约表示的乘法规则。费米子也适用于这个框架。然而，任意子的融合规则一般不由一个群来描述！至于第二原理，拓扑序并不需要任何预先存在的对称性，但会导致新的守恒定律。因此，拓扑序的形成与对称性破缺完全相反！

## 拓扑量子计算

寻找任意子的一个更实际的原因是它们在量子计算中的潜在用途。在参考文献[24]中，我提出 topologically ordered states 可以作为纠错量子码的物理模拟。因此，任意子系统提供了一种*保护不退相干*的量子存储器的实现。一些量子门可以通过编织实现; 这个实现是*精确*的，不需要显式的错误校正。Freedman, Larsen 和 Wang[27]证明了对于某些类型的非阿贝尔任意子，编织使人们能够执行通用量子计算。这种方案通常被称为*拓扑量子计算*(TQC)。

让我们概述一些拓扑量子计算（TQC）的基本原理。首先，拓扑有序系统在某些情况下具有简并的基态。特别是，存在*阿贝尔任子*意味着在环面上存在基态简并 [28]。实际上，考虑一个过程，其中创建了一个粒子-反粒子对，其中一个粒子绕着环面旋转，然后将该对湮灭。这样的过程对应于作用在基态上的一个算符。如果 $A$ 和 $B$ 是对应于环面上两个基本回路的这样的算符，那么 $ABA^{-1}B^{-1}$ 描述了一个过程，其中没有粒子实际上穿过环面，但其中一个粒子绕另一个粒子旋转。如果阿哈诺夫-博姆相位是非平凡的，那么 $A$ 和 $B$ 是不对易的。因此，它们在一个多维空间上起作用。

实际上，这种简并性并非绝对的，而是非常精确的。它因为 virtual particle 在环面上的*隧穿效应*而被解除，但这个过程被指数级抑制。因此，基态能级之间的距离与 $\exp(-L/ξ)$ 成正比，其中 $L$ 是环面的线性尺寸，$ξ$ 是一些特征长度，与激发能谱中的能隙相关。在非阿贝尔系统中，即使在平面几何中，当几个任子在彼此相距较远的地方定位时，也会出现简并性（它是辫子群作用的量子态空间）。基本特性可以描述为：给定的两个非阿贝尔粒子可以通过几种方式融合（类似于非阿贝尔群的多维表示）。例如，本文中研究的非阿贝尔相具有以下融合规则：

$$\varepsilon \cross \varepsilon = 1, \quad \varepsilon \cross \sigma = \sigma, \quad \sigma \cross \sigma = 1 + \varepsilon$$

其中 $1$ 表示真空扇区，$ε$ 和 $σ$ 是其他 superselection sectors. 最后一个规则尤其有趣：它意味着两个 $σ$ 粒子可以相互湮灭或融合成一个 $ε$ 粒子。但当 $σ$ 粒子相距较远时，$1$ 和 $ε$ 对应于两个量子态，$\ket{\psi_1^{\sigma \sigma}}$ 和 $\ket{\psi_{\varepsilon}^{\sigma \sigma}}$. 这些态是persistent 的。例如，如果我们通过将一个 $ε$ 粒子分裂成两个 $σ$ 粒子来创建 $\ket{\psi_\varepsilon^{\sigma \sigma}}$，等待一段时间后再将 $σ$ 粒子融合，我们仍将得到一个 $ε$ 粒子。

这里有一个更微妙的特性：fusion states $\ket{\psi_1^{\sigma \sigma}}$ 和 $\ket{\psi_\varepsilon^{\sigma \sigma}}$ 在实际上是无法区分的，它们具有几乎相同的能量。事实上，一种区分它们的自然过程是虚拟ε粒子在固定的σ粒子之间的隧道传输（因为σ × ε = σ）。然而，ε粒子是带隙的，因此这个过程会被指数级地压制。当然，这种解释依赖于许多细节，但这是一个普遍的原则：只有通过运输一个准粒子才能区分不同的融合态。即使在存在热浴和外部噪声的情况下，只要温度和噪声频率远小于带隙，这样的过程也是不太可能发生的。

## 与之前的工作进行比较并总结结果

在本文中，我们研究了一个在二维格子上的精确可解自旋模型。它只涉及两体相互作用，因此比[24]中考虑的Hamiltonian (3)要简单，但解决方案却不那么平凡。目前尚不清楚如何在固体中实现这个模型，但已经提出了一个光学格子的实现方法[42]。

该模型有两个不同参数值下的相（记为 $A$ 相和 $B$ 相）。通过将其归约为自由实费米子，我们得到了精确解。因此，系统中的准粒子可以被描述为*费米子和 $Z_2$-涡旋*。涡旋和费米子之间的相互作用由阿哈诺夫-博姆相位因子等于 $-1$ 来描述。

在 $A$ 相中，费米子具有能隙，而涡旋是玻色子，分别落入两个不同的超选择扇区。（有趣的是，这两种涡旋类型具有相同的物理性质，它们之间通过晶格平移相互关联。）整体的粒子分类、融合规则和统计性质与模型 [[精确可解模型及其他中的任意子_Kitaev#^9665af|(2)]] 或 RVB 模型相同。

在 $B$ 相中，费米子是无能隙的，只存在一种涡旋，其统计性质未定义。*在 Hamiltonian 中加入一个磁场会在费米子能谱中引入能隙，而涡旋变成非阿贝尔任意子*。$A$ 相和带磁场的 $B$ 相之间涡旋统计性质的差异可以归因于*费米子配对*的不同拓扑性质。

Fermi 系统的拓扑性质最早在整数量子霍尔效应的理论中进行了研究[43, 44]。让我们概述一下主要结果。首先，非相互作用电子在周期势中的霍尔电导（例如，Hofstadter 模型中每个平面格点上有 $m/n$ 个磁通量子）可以用傅里叶基下的单粒子哈密顿量来表示。这样的哈密顿量是一个依赖于动量 $\vb*{q}$ 的 $n×n$ 矩阵。对于每个 $\vb*{q}$ 值，可以定义与负能态相关联的子空间 $\mathcal{L}(\vb*{q}) ⊆ \mathbb{C}^n$，即被电子占据的态。因此，在动量空间上定义了一个向量丛。量子化的霍尔电导与该丛的陈数成正比。Bellissard等人[1]利用非交换几何的强大数学理论将这个理论推广到无序系统中[45]。

当粒子数不守恒时（由于存在类似 $a^†_j a^†_k$ 的项，如超导体的平均场描述中），会发生更有趣的拓扑现象。在这种情况下，单粒子哈密顿量被更一般的对象所取代，即 Bogolyubov-Nambu matrix。它也有一个关联的陈数 $ν$，当前面的定义适用时，它是上面定义的两倍。但一般情况下，$ν$ 是一个任意的整数。这种类型的第一个物理例子，$^3\text{He-A}$ 薄膜，由 Volovik [46]研究过。Volovik和Yakovenko [47]表明，在这个系统中的陈数决定了 soliton 的统计性质。最近，Read和Green [48]考虑了角动量 $l = -1$ 的无自旋粒子的BCS配对。他们确定了一个“强配对相”陈数为零，和一个“弱配对相”陈数为 $ν=1$。后者与 Moore-Read 态密切相关，并具有非阿贝尔的涡旋和 chiral edge modes。

在本文中，我们将这些结果推广到由二维晶格上的二次型哈密顿量描述的任意费米系统。我们表明当陈数 $ν$ 为偶数时，$Z_2$ 涡旋是*阿贝尔粒子*，而当 $ν$ 为奇数时，它们是*非阿贝尔任意子*。非阿贝尔的统计性质是由于与涡旋相关的 *unpaired Majorana modes*. 我们的方法依赖于一种 *quasidiagonal matrix formalism*（见附录C），它类似于非交换几何，但更为基础。它还可以应用于无序系统。

此外，我们发现实际上有 $16$ 种（$8$ 种阿贝尔和 $8$ 种非阿贝尔）的 vortex-fermion statistics，对应于不同的 $ν$ 模 $16$ 的取值。在原始自旋模型中，只有三种情况（对于 $ν = 0, ±1$）被实现。我们给出了所有 $16$ 种情况的完整代数描述，见第30、41和42页的表格。

---

# 1. 模型

我们研究的是一个自旋 $1/2$ 系统，其中自旋位于蜂窝状晶格的顶点上，如图 $3a$ 所示。

![[截图-1688224501305.png#C|Figure 3. 蜂窝晶格中有三种链接|500]]


该晶格由两个等效的简单子晶格组成，分别称为“偶”和“奇”（它们在图中由空心圆和实心圆表示）。晶格的一个单位胞包含一种顶点。连接分为三种类型，取决于它们的方向（参见图 $3b$）；我们称它们为“$x$-连接”，“$y$-连接”和“$z$-连接”。哈密顿量如下:

$$
H = -J_x \sum_{x\text{-links}} \sigma_j^x \sigma_k^x
- J_y \sum_{y\text{-links}} \sigma_j^y \sigma_k^y
- J_z \sum_{z\text{-links}} \sigma_j^z \sigma_k^z
\tag{4}$$

^ad6fcb

让我们为哈密顿量中的单个项引入一个特殊的符号:
$$
K_{jk} = \begin{cases}
\sigma_j^x \sigma_k^x,\quad \text{if } (j,k) \text{ is an } x\text{-link};\\
\sigma_j^x \sigma_k^y,\quad \text{if } (j,k) \text{ is an } y\text{-link};\\
\sigma_j^x \sigma_k^z,\quad \text{if } (j,k) \text{ is an } z\text{-link};
\end{cases}\tag{5}
$$

^450c45

```ad-note
title: $K_{jk}$ 与 $W_p$ 交换
值得注意的是，*任意的*算符 $K_{jk}$ 都可以与如下算符 $W_p$ 进行交换
```

 Plaquette 算符如图, 定义为![[截图-1688225332829.png#R|Plaquette 算符|150]]
$$
W_{p} = \sigma_1^x \sigma_2^y \sigma_3^z \sigma_4^x \sigma_5^y \sigma_6^z = K_{12}K_{23}K_{34}K_{45}K_{56}K_{61}
\tag{6}
$$

^9136a9

$$K_{12}K_{23} = \sigma_1^z\sigma_2^z$$

其中 $p$ 是一个标记表示一个 plaquette. 请注意，不同的算符 $W_p$ 彼此对易。因此，哈密顿量 [[精确可解模型及其他中的任意子_Kitaev#^ad6fcb|(6)]] 具有一组 "integrals of motion" $W_p$, 这极大地简化了问题。为了找到哈密顿量的本征态，我们首先将总的希尔伯特空间 $\mathcal{L}$ 划分为 sectors —— $W_p$ 的本征空间，它们也是 $H$ 的不变子空间。这可以写成

$$\mathcal{L} = \bigoplus_{w_1,\cdots,w_m}\mathcal{L}_{w_1,\cdots,w_m}$$

其中 $m$ 是 plaquettes 的数量。每个算符 $W_p$ 具有本征值 $+1$ 和 $-1$，因此每个扇区对应于为每个 plaquette $p$ 选择 $w_p = ±1$。然后我们需要求解哈密顿量在特定扇区 $\mathcal{L}_{w_1,\cdots,w_m}$ 上的本征值.

蜂窝格子每个顶点有 $1/2$ 个 plaquette，因此 $m ≈ n/2$，其中 $n$ 是顶点的数量。由此可知，每个扇区的维度约为 $\sim 2^n/2^m ≈ 2^{n/2}$（事实上我们将看到所有这些维度都是相等的）。因此，将问题分成扇区并没有解决问题。幸运的是，事实证明每个 sector 内的自由度可以用 real (Majorana) 费米子来描述，而限制后的哈密顿量只是 Majorana 算符的二次型。这使得精确解成为可能。

---

# 2. 通过Majorana算符表示自旋

## 2.1. 一般的自旋费米子变换

让我们提醒读者一些关于费米子系统的一般形式。一个具有 $n$ 个费米子模式的系统通常由湮灭和产生算符 $a_k$ 和 $a^†_k$（$k = 1, \cdots, n$）描述。然而，我们可以使用它们的线性组合
$$
c_{2k-1} = a_k + a_k^\dagger, \quad c_{2k}=\frac{a_k - a_k^\dagger}{\mi}
$$
```ad-note
即一个费米子模式对应于两个马约拉纳算符.
```
它们被称为*马约拉纳算符*. 算符 $c_j$（$j = 1,\cdots , 2n$）是*厄米算符*，并满足以下关系：

$$c_j^2 = 1, \quad c_jc_l = -c_lc_j \qq{if} j\neq l \tag{8}$$

```ad-note
Note that all operators $c_j$ can be treated on equal basis.
```

我们现在通过*两个费米子模式*（即四个 Majorana 算符）来描述自旋。让我们用 $b^x$, $b^y$, $b^z$ 和 $c$（而不是 $c_1$, $c_2$, $c_3$, $c_4$）来表示这些算符。

Majorana 算符作用于 4 维的 Fock 空间 $\widetilde{\mathcal{M}}$，而自旋的希尔伯特空间则被认为是 $\widetilde{\mathcal{M}}$ 中的一个二维子空间 $\mathcal{M}$，它满足以下条件: 

$$\ket{\xi} \in \mathcal{M} \qq{if and only if} D\ket{\xi} = \ket{\xi}, \quad \qq{where} D = b^xb^yb^zc \tag{9}$$

我们将 $\mathcal{M}$ 称为*物理子空间*，$\widetilde{\mathcal{M}}$ 称为*扩展空间*；算符 $D$ 可以看作是 $Z_2$ 群的*规范变换*。

Pauli 算符 $σ^x, σ^y, σ^z$ 可以由一些作用于*扩展空间*的算符 $\widetilde{\sigma}^x, \widetilde{\sigma}^y, \widetilde{\sigma}^z$ 表示。这种 representation 必须满足两点:
1. $\widetilde{\sigma}^x, \widetilde{\sigma}^y, \widetilde{\sigma}^z$ 保持子空间 $\mathcal{M}$ 不变.
2. 当限制在 $\mathcal{M}$ 时, $\widetilde{\sigma}^x, \widetilde{\sigma}^y, \widetilde{\sigma}^z$ 与 $σ^x, σ^y, σ^z$ 遵守相同的代数关系.
$$
\widetilde{\sigma}^x = \mi b^x c,\quad
\widetilde{\sigma}^y = \mi b^y c,\quad
\widetilde{\sigma}^z = \mi b^z c
$$
```ad-note
在量子力学中，当两个算符相互对易时，子空间的保持是一个基本概念。让我们分解一下这是如何工作的：

当两个算符相互对易时，意味着它们的操作可以交换，而不改变结果。数学上，如果算符 $A$ 和 $B$ 对易（即 $AB = BA$），那么对于任何矢量 $\ket{\Psi}$，先应用 $A$ 再应用 $B$ 会得到与先应用 $B$ 再应用 $A$ 相同的结果：

$$AB\ket{\Psi} = BA\ket{\Psi}$$

现在，当我们考虑一个较大的希尔伯特空间中的子空间M时，意味着M由一组基矢张成。如果算符A和B对易，并且A和B的作用都将子空间M中的矢量保持在M内部，那么子空间M在A和B的作用下被保持不变。

在你的问题背景下，你有算符eσx、eσy和eσz与规范算符D相互对易。这意味着这些算符的作用不会将矢量从子空间M中移出，而只会在M内部对矢量进行变换。因此，子空间M在这些算符的作用下被保持不变。

在物理解释中，当子空间被保持不变时，意味着与该子空间相关的某些物理性质或量子态在这些算符的作用下保持不变。这种保持在定义对称性和研究量子系统中的守恒量时非常重要。
```

（我们将马约拉纳算符与四个点关联起来，这个原因稍后会变得清楚。）这种表示是正确的，因为 $\widetilde{\sigma}^α$ 与 $D$ 对易（从而保持 $\mathcal{M}$ 不变），$(\widetilde{\sigma}^α)^\dagger = \widetilde{\sigma}^α$，$(\widetilde{\sigma}^α)^2=1$，并且

$$
\widetilde{\sigma}^x\widetilde{\sigma}^y\widetilde{\sigma}^z = \mi b^xb^yb^zc = \mi D
$$

最后一个方程式与公式 $σ^xσ^yσ^z = \mi$ 是一致的，因为 $D$ 在子空间 $\mathcal{M}$ 上作用为单位算符 (与式子 9 对应)。多自旋系统由每个自旋的四个马约拉纳算符描述。相应的算符 $\widetilde{\sigma}^{\alpha_j}$、$D^α_j$ 和物理子空间 $\mathcal{L} \subset \widetilde{\mathcal{L}}$ 的定义如下

$$
\begin{align}
\widetilde{\sigma}^{\alpha_j} = \mi b_j^\alpha c_j, \quad D_j = b_j^x b_j^y b_j^z c_j\\
\ket{\xi} \in \mathcal{L} \iff D_j \ket{\xi} = \ket{\xi}, \forall j.
\end{align}
$$
```ad-note
此处的 $\ket{\xi}$ 应该是多体态.
```

任何自旋哈密顿量 $H\qty{\sigma_j^\alpha}$ 都可以用费米子哈密顿量 $\widetilde{H}\qty{b_j^\alpha, c_j} = H \qty{\widetilde{\sigma}^{\alpha_j}}$ 代替，其作用仅限于物理子空间。(所得的哈密顿 $\widetilde{H}$ 相当特殊; 特别是，它与算符 $D_j$ 对易)

```ad-note
title: Remark 2.1.

$\sigma_j^\alpha \mapsto \widetilde{\sigma}_j^\alpha = \mi b_j^\alpha c_j$ 与更常见的替换间规范等价（参见[^49]及其中的引用）:
$$
\sigma_j^\alpha \mapsto D_j \widetilde{\sigma}_j^\alpha\qq{i.e.}
\sigma_j^x \mapsto -\mi b_j^y b_j^z,\quad
\sigma_j^y \mapsto -\mi b_j^z b_j^x,\quad
\sigma_j^z \mapsto -\mi b_j^x b_j^y
$$
因此，可以仅用 3 个马约拉纳算符来表示自旋，而无需施加规范约束。然而，这对于我们的目的来说是不够的。

```

## II.2. 应用于具体模型

让我们将一般过程应用于自旋哈密顿量 (4). 每个项 $K_{ij} = \sigma_j^\alpha\sigma_k^\alpha$ 变为
$$\widetilde{K}_{jk} = (\mi b^α_j c_j)(\mi b^α_k c_k) = -\mi (\mi b^α_j b^α_k) c_jc_k$$

括号中的算符，$\hat{u}_{jk} \equiv \mi b^α_j b^α_k$，是厄米的；我们将其与 link $(j,k)$ 关联起来。

因此，我们得到
$$
\widetilde{H} = \frac{\mi}{4} \sum_{j,k}\hat{A}_{jk} c_j c_k,
\quad \hat{A}_{jk} = \begin{cases}
2 J_{\alpha_{jk}}\hat{u}_{jk} \quad & \text{if } j \text{ and } k\text{ are connected}\\
0 & \text{otherwise}
\end{cases}\tag{13}
$$
$$
\hat{u}_{jk} = \mi b_j^{\alpha_{jk}}b_k^{\alpha_{jk}}
$$

需要注意的是，每对连接的站点都会被统计两次，$\hat{u}_{jk} = -\hat{u}_{kj}$. 这个哈密顿量的结构如图 4 所示。
![[截图-1692473766464.png#C|图 4: 哈密顿函数的图示|500]]

值得注意的是，算符 $\hat{u}_{jk}$ 与哈密顿函数交换，并且彼此交换。因此，Hilbert 空间 $\widetilde{\mathcal{L}}$ 分裂为 $\hat{u}_{jk}$ 的公共本征空间，这些特征空间被对应的特征值 $u_{jk} =±1$ 索引。与 (7) 类似，我们可以写成 $\widetilde{\mathcal{L}} = \bigoplus_u \widetilde{\mathcal{L}}_u$，其中 $u$ 代表所有 $u_{jk}$ 的集合。

将哈密顿量（13）限制在子空间 $\widetilde{\mathcal{L}}_u$ 内可以通过“去掉帽子”的方式获得，即将算符替换为数值。这个过程得到了哈密顿量 $\widetilde{H}_u = \dfrac{\mi}{4}\sum_{j,k}A_{jk}c_jc_k$，对应于自由费米子。$\widetilde{H}_u$ 的基态可以被精确地找到，我们将其表示为 $\ket{\widetilde{\Psi}_u}$.

```ad-note
请注意，子空间 $\widetilde{\mathcal{L}}_u$ 并不是规范不变的：应用规范算符 $D_j$ 会改变连接顶点 $j$ 与三个相邻顶点 $k$ 的链接上 $u_{jk}$ 的值。因此，状态 $\ket{\widetilde{\Psi}_u}$ 不属于物理子空间。
```

为了获得物理空间，我们必须对所有规范变换进行对称化。具体而言，我们构造以下状态：

$$
\ket{\Psi_w} = \prod_j \qty(\frac{1+D_j}{2}) \ket{\widetilde{\Psi}_u}\in \mathcal{L}\tag{14}
$$

这里，$w$ 表示在规范变换下 $u$ 的等价类。对于平面晶格（但不适用于环面），$w$ 由 $w_p = ±1$ 表示，其定义为六边形周围的 $u_{jk}$ 的乘积。为了避免歧义（由于关系 $u_{kj} = −u_{jk}$），我们为每个链接选择了一个特定的方向：

$$
w_p = \prod_{(j,k)\in \partial p}u_{jk}\quad (j \in \text{even sublattice, }k\in\text{odd sublattice})\tag{15}
$$

^c6a0bd

相应的算符 $\widetilde{W}_p = \prod \hat{u}_{jk}$ 与规范变换以及哈密顿算符相互对易。将该算符限制在物理子空间上，其结果与之前定义的运动积分 $W_p$ 相一致（参见 [[#^9136a9|6]] ）.

```ad-warning
title: 符号更改
从现在开始，我们将不再区分作用于扩展空间的算符和它们限制在物理子空间中的算符，例如，$\widetilde{W}_p$ 与 $W_p$. 波浪符将用于其他目的。
```

## II.3. 路径和 loop 算符

我们可以把变量 $u_{kj}$ 看作 $Z_2$ 规范场。数值 $w_p$ 可解释为通过 plaquette $p$ 的磁通量。

若 $w_p =−1$，则称 plaquette 携带涡旋。

$\hat{u}_{kj}$ 沿着任意路径的乘积对应于一个费米子在起始点和终点之间的传递。然而，这个乘积不是规范不变的。我们可以用自旋或费米子定义一个不变的费米子路径算符:

$$
W(j_0,\cdots,j_n) = K_{j_nj_{n-1}}\cdots K_{j_1j_0}
= \qty(\prod_{s=1}^n - \mi \hat{u}_{j_sj_{s-1}})c_nc_0\tag{16}
$$

^eb169a

其中 $K_{jk}$ 由 [[#^450c45|5]] 给出。如果路径是闭合的，即 $j_n = j_0$，因子 $c_n$ 和 $c_0$ 会互相抵消。在这种情况下，路径算符称为 [[Wilson 环]]；它推广了磁通的概念。

在蜂窝晶格上，所有的环都有偶数长度，公式 [[#^eb169a|16]] 符合基于偶, 奇子晶格划分的符号约定。然而，自旋模型可以推广到任何 trivalent 图中，在这种情况下，环的长度是任意的。对于奇数长度的环 $l$，算符 $W(l)$ 具有特征值 $w_l = \pm \mi$. 

这不仅仅是定义的产物：奇数长度的 loop 的特殊之处，在于它们引起了[[时间反演对称性]]的自发破缺。

[[时间反演算符]]是一个*共轭线性幺正算符* $T$，满足条件
$$
T \sigma_j^\alpha T^{-1} = -\sigma_j^\alpha,\quad
T b_jT^{-1} = b_j,\quad
T c_j T^{-1} = c_j\tag{17}
$$
（第一个方程是一个物理要求；其他两个方程表示了 $T$ 在扩展空间中的作用。）因此，$T$ 与哈密顿算符 [[#^ad6fcb|4]] 和 Wilson 环相互对易。将方程 $W_l \ket{\Psi} = w_l \ket{\Psi}$ 两边乘以 $T$，我们得到
$$W_l T\ket{\Psi} = w_l^* T \ket{\Psi}$$
因此，时间反演算符将 $w_l$ 变为 $w^∗_l$. 对于一个 bipartite，$w^*_l = w_l$ 对所有的环成立，因此固定 wl 变量不会破坏时间反演对称性。

相反，在一个 non-bipartite 图（例如，包含三角形的晶格）上的类似模型中，算符 $T$ 并不保持场的配置，这由所有环上 $w_l$ 的值所定义。但是 $T$ 是一个对称算符，因此所有哈密顿算符的本征态至少是双重简并的.

---

# 3. 二次型哈密顿

在前面的章节中，我们将自旋模型 [[#^ad6fcb|4]] 转化为了一般形式的二次费米子哈密顿量：
$$
H(A) = \frac{\mi}{4} \sum_{jk} A_{jk} c_jc_k\tag{18}
$$

^0de6b7

在这里，$A$ 是一个尺寸为 $n = 2m$ 的实斜对称矩阵。让我们简要陈述一些这类哈密顿量的通用性质，并固定术语。

首先，我们对方程 [[#^0de6b7|18]] 中的归一化因子 $1/4$ 进行说明。它的选择是为了使得
$$
\comm{-\mi H(A)}{-\mi H(B)}
= -\mi H(\comm{A}{B})\tag{19}
$$
因此，二次算符的李代数 $-\mi H(A)$ (作用于 $2^m$ 维 Fock 空间) 被确定为 $\mathfrak{so}(2m)$. 

$\me^{-\mi H(A)}$ 形的算符构成李群自旋 $(2m)$.

这个群的中心由相位因子 $±1$（例如，$\me^{πc_1c_2} = -1$）组成。商群 $\text{Spin}(2m)/\qty{+1, -1} = \text{SO}(2m)$ 描述了 e^-iH(A) 对马约拉纳算符的共轭作用:
$$
\me^{-\mi H(A)}c_k \me^{\mi H(A)}
= \sum_j Q_{jk} c_j\qq{where} Q=\me^A\tag{20}
$$
（其中 $Q$ 是一个行列式为 $1$ 的*实正交矩阵*）。

请注意，方程 20 中的求和, 对应于将行向量 $(c_1, \cdots, c_{2m})$ 与矩阵 $Q$ 相乘。另一方面，当我们考虑马约拉纳算符的线性组合时

$$F(x) = \sum_j x_j c_j\tag{21}$$
我们更喜欢把 $x$ 看成一个*列向量*。如果系数 $x_j$ 是实数，我们称 $F(x)$ (或 $x$ 本身)为*马约拉纳模*。

为了找到哈密顿量 (18) 的基态，我们需要把它简化成正则形式

$$
H_{\text{canonical}}
= \frac{\mi}{2}\sum_{k=1}^m \epsilon_k b_k' b_k''
= \sum_{k=1}^m \epsilon_k \qty(a_k^\dagger a_k - \frac12),
\quad \epsilon_k \geq 0 \tag{22}
$$

其中 $b_k', b_k''$ 是 normal modes，而 $a_k^\dagger = \frac12(b_k' - \mi b_k''),\ a_k = \frac12 (b_k' + \mi b_k'')$ 则是相应的产生和湮灭算符。$H_{\text{canonical}}$ 的基态, 对于所有 $k$, 满足条件 $a_k \ket{\Psi} = 0$. 

将其化简为正则形式是通过以下变换实现的
$$
(b_1',b_1'',\cdots,b_m',b_m'')
= (c_1,c_2,\cdots,c_{2m-1},c_{2m})Q, \quad Q\in \text{O}(2m)\tag{23}
$$
以至于
$$
A=Q\mqty(0 & \epsilon_1\\
-\epsilon_1 & 0\\
&& \ddots\\
&&&0& \epsilon_m\\
&&&-\epsilon_m&0)Q^T\tag{24}
$$
数值 $± \epsilon_k$ 构成了厄米矩阵 $\mi A$ 的谱，而 $Q$ 的奇数（偶数）列等于特征向量的实部（虚部）。马约拉纳系统的基态能量为：
$$
E = -\frac12 \sum_{k=1}^m \epsilon_k = -\frac14 \Tr \abs{\mi A}\tag{25}
$$
这里的函数 $\abs{\ \cdot\ }$ 作用于特征值，而特征向量被固定。（实际上，任何一个实变量的函数都可以应用于厄米矩阵。）注意不同的二次哈密顿量可能会导致相同的基态。实际上，后者取决于：
$$
B = -\mi\ \text{sgn} (\mi A)=Q
\mqty(0&1\\-1&0\\
&&\ddots\\
&&&0&1\\
&&&-1&0)Q^T\tag{26}
$$
（我们假设 $A$ 是非简并的。）矩阵 $B$ 是实斜对称的，并且满足 $B^2 = -1$. 通过以下条件，它决定了基态：
$$
\sum_j P_{jk}c_j \ket{\Psi} = 0,\ \forall k \qq{where} P_{jk} = \frac12(\delta_{jk}-\mi B_{jk})\tag{27}
$$

从宽泛的角度来看，$B$ 对应于马约拉纳模式之间的配对[^1]。如果 $x'' = \pm Bx'$，那么算符 $b' = F(x')$ 和 $b'' = F(x'')$ 会被配对。

方程 27 中的矩阵 $P$ 称为*谱投影矩阵*。它将 $2m$ 维的复数空间 $\mathbb{C}^{2m}$ 投影到 $m$ 维的子空间 $L$，该子空间由 $\mi A$ 对应于*负特征值*的特征向量张成。

对于任意向量 $z ∈ L$，相应的算符 $F(z)$ 会湮灭基态，因此我们可以称 $L$ 为湮灭算符的空间。

需要注意的是，如果 $z, z' \in L$，则 $\sum_j z_jz_j' = 0$. 选择一个满足这个条件的 $m$ 维子空间 $L \subseteq \mathbb{C}^{2m}$ 的选择等价于选择矩阵 $B$。

一个二次哈密顿量的基态也可以通过*关联函数*来描述。二阶相关函数为 $\ev*{c_jc_k}{\Psi} = 2 P_{kj}$；使用 [[Wick 定理]]可以找到更高阶的相关函数。

# IV. 费米子的谱和相图

现在我们来研究蜂窝格子上的马约拉纳费米子系统。它由二次哈密顿量 $H_u = H(A)$ 描述，其中 $A_{jk} = 2J_{α_{jk}} u_{jk}$，$u_{jk} = ±1$。尽管哈密顿量是由 $u_{jk}$ 参数化的，但相应的规范不变态（或自旋系统的态）实际上取决于变量 $w_p$, 参见（[[#^c6a0bd|15]]）。

首先，我们注意到整体基态能量不依赖于交换常数 $J_x$、$J_y$、$J_z$ 的符号，因为改变符号可以通过改变相应的变量 $u_{jk}$ 来补偿。

我们进一步注意到，即使 $u$ 固定，$H_u$ 的基态能量也不依赖于这些符号。例如，假设我们将 $J_z$ 替换为 $-J_z$. 这样的变化等同于改变所有 $z$-link的 $u_{jk}$. 但规范不变量 $w_p$ 保持恒定，因此我们可以应用一个规范变换，将 $u_{jk}$ 返回到它们的原始值。

总的效果是，某些 site 上的马约拉纳算符会被转化为 $c_j \mapsto -c_j$. 具体来说，这个变换作用于位于下图中阴影区域内的 site 集 $\Omega_z$. 在自旋的术语中，这个作用是由以下幺正算符诱导的：

![[截图-1692622264007 1.png|400]]
$$R_z = \prod_{j \in \Omega_z} \sigma_j^z\tag{28}$$
因此，为了找到基态能量和激发谱，交换常数的符号无关紧要 (但其他物理量可能依赖于它们)。

$u_{jk}$ 中最有趣的选择是使基态能量最小的那个。结果表明，在无涡场构型下，能量达到最小值，即，对于所有 plaquette $p$, $w_p = 1$。这一说法来自于一个美丽的定理，由 [[Elliott H. Lieb|Lieb]]证明[^50]。(由于不知道 Lieb 的结果，我做了一些数值研究，得出了相同的答案，见[[#附录 A]])

因此，我们可以假设对于所有的 link $(j,k)$, $u_{jk} = 1$，其中 $j$ 属于偶子格，而 $k$ 属于奇子格。这种场构型 (用 $u_{jk}^{\text{std}}$ 表示) 具有*平移对称性*，因此可以用[[傅立叶变换|傅里叶变换]]解析地找到 fermionic 谱

一般的步骤如下。我们将 site 指标 $j$ 表示为 $(s, λ)$，其中 $s$ 表示一个单位胞，$λ$ 表示单元胞内的位置类型（我们选择如在附带 Eq. (32) 图中所示的单位胞）。哈密顿量变为
$$H = \frac{\mi}{4} \sum_{s,\lambda,t,\mu}A_{sλ,tµ} c_{sλ}c_{tµ}$$

其中 $A_{sλ,tµ}$ 实际上取决于 $λ$, $\mu$ 以及 $t-s$. 然后我们转换到动量表示：

$$
H = \frac12 \sum_{\vb*{q}, \lambda,\mu} \mi \widetilde{A}_{\lambda \mu}(\vb*{q}) a_{-\vb*{q},\lambda}a_{\vb*{q}, \mu},
\quad \widetilde{A}_{\lambda \mu}(\vb*{q})
= \sum_t \me^{\mi (\vb*{q}, \vb*{r}_t)}A_{0\lambda,t\mu}\tag{29}
$$
$$
a_{\vb*{q},\lambda} = \frac{1}{\sqrt{2N}}\sum_s \me^{-\mi(\vb*{q},\vb*{r}_s)}c_{s\lambda}\tag{30}
$$
其中 $N$ 是单位胞的总数。（从这里开始，动量表示中的算符将用波浪线标记。）

请注意
$$a^\dagger_{\vb*{q},λ} = a_{−\vb*{q},λ} \qq{and}a_{\vb*{p},\mu} a^\dagger_{\vb*{q},\lambda}+a^\dagger_{\vb*{q},\lambda}a_{\vb*{p},\mu} = \delta_{\vb*{pq}}\delta_{\mu \lambda}$$


能谱 $ε(\vb*{q})$ 由矩阵 $i \widetilde{A}(\vb*{q})$ 的特征值给出。由于其冗余性，我们可以称其为“双重能谱”：$ε(-\vb*{q}) = -ε(-\vb*{q})$. 

通过仅取正特征值（如果没有特征值为零），可以获得“单一能谱”。

现在，我们将这个步骤应用到具体的哈密顿量：
$$
H_{\text{vortex-free}}=\frac{\mi}{4} \sum_{j,k} A_{jk} c_jc_k
,\quad A_{jk} = 2 J_{\alpha_{jk}}u_{jk}^{\text{std}}\tag{31}
$$
我们选择一个平移群的基 $(\vb*{n}_1, \vb*{n}_2)$，并得到以下结果：

$$
\begin{align}
\mi \widetilde{A}(\vb*{q}) = \mqty[0 & \mi f(\vb*{q})\\-\mi f(\vb*{q})^* &0], \quad \epsilon(\vb*{q}) = \pm \abs{f(\vb*{q})}\\
f(\vb*{q}) = 2 (J_x \me^{\mi (\vb*{q}\vdot\vb*{n}_1)}
+ J_y \me^{\mi(\vb*{q}\vdot \vb*{n}_2)}+J_z
)
\end{align}\tag{32}
$$

在标准 $xy$ 坐标系中，$\vb*{n}_1 = \qty(\frac12, \frac{\sqrt{3}}{2})$，$\vb*{n}_2 = \qty(- \frac12, \frac{\sqrt{3}}{2})$

能谱的一个重要性质是它是否是无能隙的，即 $ε(\vb*{q})$ 是否在某些 $\vb*{q}$ 值上为零。

方程 $J_x \me^{\mi (\vb*{q}\vdot\vb*{n}_1)}+J_y \me^{\mi(\vb*{q}\vdot \vb*{n}_2)}+J_z=0$ 有解，当且仅当 $\abs{J_x}, \abs{J_y}, \abs{J_z}$ 满足三角不等式:
$$
\abs{J_x}\leq\abs{J_y}+\abs{J_z}
, \quad \abs{J_y}\leq\abs{J_z}+\abs{J_x}
, \quad \abs{J_z}\leq\abs{J_x}+\abs{J_y}\tag{33}
$$
如果不等式是严格的，则会有确切的两个解：$\vb*{q} = \pm \vb*{q}_∗$.

![[截图-1692634499094.png#C|图 5|400]]

不等式（33）定义的区域在图 5 中标记为 $B$；这个相是*无能隙*的。被标记为 $A_x$、$A_y$ 和 $A_z$ 的*有隙*相在代数上是不同的，尽管它们通过旋转对称性相互关联。

它们在晶格平移作用于任意子量子态上的方式上存在差异（参见第5.2节）。因此，即使我们在哈密顿量中引入新项，也无法从一个*有隙相*连续地过渡到另一个*有隙相*。

另一方面，每个相位的 8 个副本（对应于 $J_x$、$J_y$、$J_z$ 的不同符号组合）具有相同的平移性质。目前尚不清楚 8 个无能隙相位的副本在代数上是否是不同的。

我们现在考虑存在于无隙相中的能谱零点。动量 $\vb*{q}$ 被定义为模除倒格子，即它属于一个环面。我们通过由 $(\vb*{q}_1, \vb*{q}_2)$ 张成的平行四边形来表示动量空间，这个基是 $(\vb*{n}_1, \vb*{n}_2)$ 的对偶基。在对称情况下（$J_x = J_y = J_z$），能谱的零点给出：

![[截图-1692634888236.png#C|200]]

$$
\begin{align}
\vb*{q}_*&=\frac13 \vb*{q}_1 + \frac23 \vb*{q}_2\quad (\text{mod}\ \vb*{q}_1,\vb*{q}_2)\\
-\vb*{q}_*&=\frac23\vb*{q}_1+\frac13\vb*{q}_2\quad(\text{mod}\ \vb*{q}_1,\vb*{q}_2)
\end{align}\tag{34}
$$

^d51420

如果 $\abs{J_x}$ 和 $\abs{J_y}$ 逐渐减小，而 $\abs{J_z}$ 保持不变，$\vb*{q}_*$ 和 $-\vb*{q}_*$ 会向彼此靠近（在平行四边形内），直到它们融合并消失。当 $\abs{J_x} + \abs{J_y} = \abs{J_z}$ 时，这种情况发生。

点 $\vb*{q}_*$ 和 $-\vb*{q}_*$ 也可以在平行四边形的相对侧有效地融合。（请注意，方程 $\vb*{q}_* = -\vb*{q}_*$ 在环面上有三个非零解）。

在点 $\pm \vb*{q}_*$ 处，能谱会出现锥形奇点（假设 $\vb*{q}_* \neq -\vb*{q}_*$ ）：
![[截图-1692635552988.png#C|150]]

$$
\begin{align}
&\epsilon(\vb*{q}) \approx \pm \sqrt{g_{\alpha\beta}\delta_{q_\alpha}\delta_{q_\beta}}\\
\qq{where}& \delta \vb*{q} = \vb*{q}-\vb*{q}_* \qq{or}
\delta \vb*{q} = \vb*{q}+\vb*{q}_*
\end{align}
$$

# V. 有能隙相的性质

在一个有能隙的相中，自旋关联在距离上以指数方式衰减，因此空间分离的准粒子不能直接相互作用。也就是说，对一个粒子进行小的位移或另一种*局部*操作不会影响另一个粒子。

然而，如果它们彼此绕行，这些粒子可以在拓扑上相互作用。这种现象由编织规则描述。（我们指的是在三维时空中由粒子世界线形成的编织。）在我们的情况下，这些粒子是涡旋和费米子。当一个费米子绕一个涡旋移动时，整体的量子态会乘以 $-1$. 正如介绍中所提到的，这种具有简单相位编织特性的粒子被称为*阿贝尔任意子*。

任意子的描述始于识别超选择 sector，即通过局部操作定义的激发类型。（"激发"被认为是在空间上*局域*的，但它可能具有不确定的能量或由多个未束缚粒子组成。）

平凡的 [[超选择区域]] 是真空的 sector；它还包含可以通过局部算符的作用从真空获得的所有激发。

乍一看，我们模型中的每个有能隙相都有三个超选择 sectors：一个费米子，一个涡旋和一个真空。然而，我们将看到实际上有两种不同类型的涡旋，它们存在与不同的 plaquette 子集上。

它们具有相同的能量和其他物理特性，但它们属于不同的超选择扇区：将一种类型的涡旋转变为另一种类型的涡旋必须创造或湮灭一个费米子。

为了理解*有能隙相*的粒子类型和其他代数性质，我们将我们的模型映射到一个已知的模型中[^24]。

让我们关注相 $A_z$，这个相位，当 $\abs{J_x} + \abs{J_y} < \abs{J_z}$ 时发生。由于我们只对相的离散特性感兴趣，我们可以设置 $|J_x|$, $|J_y|$ $\ll |J_z|$ 并应用微扰理论。

## V.1. 微扰理论

这个哈密顿量可以表示为 $H = H_0 + V$，其中 $H_0$ 是主要部分，而 $V$ 是微扰：
$$
H_0 = -J_z \sum_{z\text{-links}}\sigma_j^z \sigma_k^z,
\quad V = -J_x \sum_{x\text{-links}}\sigma_j^x \sigma_k^x-J_y \sum_{y\text{-links}}\sigma_j^y \sigma_k^y
$$

假设 $J_z > 0$（相反的情况类似地研究）。

我们首先设定 $J_x = J_y = 0$ 并找到基态。它高度简并：通过 $z$-link 连接的每两个自旋都是*对齐*的（ $\uparrow \uparrow$ 或 $\downarrow \downarrow$ ），但它们的共同方向没有固定。我们将每对这样的自旋视为*有效自旋*。从物理自旋到有效自旋的转变在图 6a,b 中显示。基态能量是 $E_0 = -NJ_z$，其中 $N$ 是单元格的数量，即自旋数量的一半。

![[截图-1692637846741.png#C|图 6|500]]

我们的目标是找到在有效自旋空间 $\mathcal{L}_{\text{eff}}$ 中起作用的有效哈密顿量。解决这个问题的一种方法是在 $\mathcal{L}_{\text{eff}}$ 中选择一个 basis 并计算矩阵元

$$
\mel*{a}{H_{\text{eff}}^{(1)}}{b} = \mel*{a}{V}{b},
\quad
\mel*{a}{H_{\text{eff}}^{(2)}}{b}
= \sum_j' \frac{\mel*{a}{V}{j}\mel*{j}{V}{b}}{E_0-E_j}
,\ \text{etc.}
$$

让 $\Upsilon: \mathcal{L}_{\text{eff}}\to \mathcal{L}$ 成为将有效希尔伯特空间映射到 $H_0$ 的基态子空间的 embedding. 映射 $\Upsilon$ 简单地使每个自旋加倍：$\Upsilon\ket{m} = \ket{mm}$，其中 $m = \uparrow$ 或 $m = \downarrow$. 

如果“有效哈密顿量”存在，其特征值应该是源自 $H_0$ 基态的 $H$ 的能级。这些能级可以明确地定义为[[格林函数]] $G(E) = \Upsilon^†(E − H)^{-1}\Upsilon$ 的极，该函数是作用在 $\mathcal{L}_{\text{eff}}$ 上并依赖于参数 $E$ 的算符。

通常，[[格林函数]]被表示为 $\qty(E-E_0-\Sigma(E))^{-1}$，其中 $\Sigma(E)$ 被称为[[自能]]，因此所讨论的能级是使得算子 $E-E_0-\Sigma(E)$ 退化的 $E$ 的值。忽略 $\Sigma(E)$ 关于 $E$ 的依赖（对于 $E \approx E_0$），我们将有效哈密顿量定义为 $H_{\text{eff}} = E_0 + \Sigma(E_0)$.

自能是通过标准方法计算的。让 $G_0'(E) = \qty((E − H_0)^{-1})'$ 为 $H_0$ 激发态的无微扰 Green 函数. *撇号标记*表示算子 $\qty((E - H_0)^{-1})'$ 在激发态上按照自然的方式起作用，但在基态上为零。然后

$$
\Sigma(E)=\Upsilon^\dagger
\qty(
V+VG_0'(E)V
+VG_0'(E)VG_0'(E)V
+ \cdots
)\Upsilon\tag{36}
$$
我们设置 $E = E_0$，计算 $H_{\text{eff}} = E_0 + \Sigma$ 的零阶 ($H^{(0)}_{\text{eff}} = E_0$)，一阶，二阶，直到找到一个非常数项. 计算如下.

1. $H_{\text{eff}}^{(1)} = \Upsilon^\dagger V\Upsilon = 0$.
2. $H_{\text{eff}}^{(2)} = \Upsilon^\dagger V G_0' V \Upsilon = -\sum_{x\text{-links}} \dfrac{J_x^2}{4J_z}-\sum_{y\text{-links}} \dfrac{J_y^2}{4J_z} = -N\dfrac{J_x^2 + J_y^2}{4J_z}$. 确实，考虑在表达式 $\Upsilon^\dagger V G_0' V \Upsilon$ 中第二个 $V$ 的作用. 每个项 $\sigma_j^x \sigma_k^x$ 或 $\sigma_j^y\sigma_k^y$ 都会翻转两个自旋，将能量增加 $4J_z$. 其他的 $V$ 必须将它们翻回来.
3. $H_{\text{eff}}^{(3)} = \Upsilon^\dagger V G_0' V G_0' V \Upsilon = 0$.
4. $H_{\text{eff}}^{(4)} = \Upsilon^\dagger V G_0' V G_0' V G_0' V \Upsilon = \text{const} - \dfrac{J_x^2J_y^2}{16J_z^3}\sum_p Q_p$, 其中 $Q_p = (W_p)_{\text{eff}}$ 表示算符 [[#^9136a9|6]] 的有效自旋表示，因子 $\dfrac{1}{16}$ 是通过对 24 项求和得到的，每一项都对应于以特定顺序翻转 4 对自旋：

$$
\frac{1}{16} = 8 \vdot \frac{1}{64} + 8 \vdot \frac{-1}{64} + 8 \vdot \frac{1}{128}
$$

上述论证可以很容易地适用于 $J_z$ 小于 $0$ 的情况。现在我们有 $\Upsilon: \ket{\uparrow} \mapsto \ket{\uparrow \downarrow}, \ket{\downarrow} \mapsto \ket{\downarrow \uparrow}$. 结果证明是相同的，只是 $J_z$ 被替换为 $\abs{J_z}$. 因此，有效哈密顿量具有以下形式：

因此有效的哈密顿量具有这样的形式

$$
H_{\text{eff}}=-\frac{J_x^2J_y^2}{16 \abs{J_z}^3}
\sum_p Q_p, \quad
Q_p = \sigma_{\text{left}(p)}^y\sigma_{\text{right}(p)}^y
\sigma_{\text{up}(p)}^z\sigma_{\text{down}(p)}^z\tag{37}
$$

^1b9540

（自旋的几何排列对应于图6b）.

## V.2. 阿贝尔任意子

哈密顿函数 ([[#^1b9540|37]]) 已经适合于直接分析。然而，首先让我们将其简化为更熟悉的形式 (3). 我们构造一个新的晶格 $\Lambda'$，使得有效自旋位于其链接上（参见图 6c）. 这是原始晶格 $\Lambda$ 中的一个子晶格，指数为 $2$（这里的“晶格”意味着“平移群”）。$\Lambda'$ 的基向量为 $\vb*{m}_1 = \vb*{n}_1 - \vb*{n}_2$ 和 $\vb*{m}_2 = \vb*{n}_1 + \vb*{n}_2$. 有效自旋晶格的平面变为新晶格的平面和顶点，因此哈密顿量可以写成以下形式：

$$
H_{\text{eff}}=-J_{\text{eff}}
\qty(
\sum_{\text{vertices}}Q_s
+\sum_{\text{plaquettes}}Q_p
)
$$
其中 $J_{text{eff}}=J_x^2J_y^2/\qty(16 \abs{J_z}^3)$.

现在我们应用幺正变换

$$
U = \prod_{\text{horizontal links}}X_j
\prod_{\text{vertical links}}Y_k \tag{38}
$$
适当选择 $X$ 和 $Y$ 的自旋旋转，这样哈密顿量就变成

$$
H_{\text{eff}}'=U H_{\text{eff}}U^\dagger
= -J_{\text{eff}}
\qty(
\sum_{\text{vertices}}A_s
+ \sum_{\text{plaquettes}}B_p
)\tag{39}
$$
其中 $A_s$ 和 $B_p$ 在方程 [[#^44212c|3]] 中定义。（注意：变换（38）破坏了原始模型的平移对称性。）最后的哈密顿量已经详细研究过[^24]。其关键特性是所有的项 $A_s$、$B_p$ 都是可交换的，并且基态会分别最小化每个项。因此，基态满足以下条件：

$$
A_s \ket{\Psi} = +\ket{\Psi},\quad
B_p \ket{\Psi} = +\ket{\Psi}\tag{40}
$$
激发态可以通过将一些顶点和 plaquette 的 $+$ 号替换为 $-$ 号来获得。这些顶点和 plaquette 是任意子的位置。我们将它们分别称为“电荷”和“磁涡”，或称之为 $e$-粒子和 $m$-粒子。当一个 $e$-粒子绕着一个 $m$-粒子移动时，系统的整体状态会乘以 $-1$。这个性质对于哈密顿量的小局部扰动是稳定的。（局部算子是一系列作用于少数相邻自旋的项的总和。）每种类型的粒子数量在模 2 下保持不变，这也是一个稳健的性质。

该模型具有4个[[超选择区域|超选择扇区]]：
1. $1$（真空）
2. $e$
3. $m$
4. $ε = e × m$

后者表示由“电荷”和“磁涡”组成的复合对象。以下是*融合规则*：
$$
\begin{align}
e \times e = m \times m = \varepsilon \times \varepsilon = 1,\\
e \times m = \varepsilon,\quad
e \times \varepsilon = m,\quad
m \times \varepsilon = e
\end{align}\tag{41}
$$
(通常情况下，融合规则必须辅以*结合关系*或 $6j$ 符号，但在我们的例子中，它们是微不足道的。)

让我们来讨论一下编织规则。我们提到过一种特殊情况:让 $e$ 粒子绕 $m$ 粒子移动会产生 $−1$. 这个事实可以用图画的方式来表示:

![[截图-1692711437491.png#C|500]]

第一个图示显示了该过程的“俯视图”。第二个方程中的图示对应于“正视图”：其中的“上”方向表示时间。

很容易证明，$e$-粒子对自身而言是玻色子（尽管对于 $m$-粒子而言，它们显然不像玻色子那样表现）；$m$-粒子也是玻色子。然而，$ε$-粒子是费米子。为了理解这一点，考虑两个过程。在第一个过程中，创建了两个 $εε$-对，四个 $ε$-对象中的两个, 通过 180° 逆时针旋转交换，然后这些对被湮灭。（每个 $ε$-对象由 $e$ 和 $m$ 表示，因此涉及 8 个基本粒子。）

在第二个过程中，两个 pairs 立即被湮灭。如何准确地创建和湮灭这些对并不重要，但在两种情况下我们应该采用相同的方法。例如，我们可以使用这个定义：

![[截图-1692712075362.png|500]]

现在我们来比较这两个过程。每个过程都会使基态乘以一个数，但是这两个数的差异是 $-1$：

![[截图-1692712085006.png|500]]

确实，在左图中，虚线与实线相连。这对应于一个 $e$-粒子绕着一个 $m$-粒子旋转，从而产生负号。


# 6. 相 B 在磁场存在时获得一个间隙

## 6.1. 锥形奇点与时间反演对称性


# VII. 边缘模与热输运

# VIII. 非阿贝尔任意子

我们继续研究磁场下的 $B$ 相。现在，所有的 bulk 激发都有能隙，它们的编织规则必须是明确定义的。当然，这仅在粒子之间的距离远远大于与能谱相关的*相关长*时才成立（51）。相关长度可以定义如下：$ξ = \abs{\text{Im}\ \vb*{q}}^{−1}$，其中 $\vb*{q}$ 是方程 $ε(\vb*{q}) = 0$ 的复数解。因此
$$
\xi = \abs{\frac{\sqrt{3}J}{\Delta}}
\sim \abs{\frac{J^3}{h_xh_yh_z}}
$$

涡旋的编织规则取决于谱 Chern 数 $ν$。尽管 $ν$ 实际上等于 $+1$ 或 $-1$（取决于磁场的方向），但可以形式上考虑一个具有任意*能隙费米子谱*的模型，这种情况下 $ν$ 可以取任意整数值。我们将看到，对于任何奇数的 $ν$ 值，涡旋表现为*非阿贝尔任子*，但它们的确切统计性质取决于 $ν$ 对 $16$ 取模的结果。

任子的性质在第 30 页的表格 $1$ 中进行了总结。下面解释了符号和基本概念；还可参考附录 E。首先，我们将从共形场论（CFT）中最重要的情况 $ν = ±1$ 中快速推导出这些性质的方法。（有关 CFT 的一般参考文献，请参阅[63]。）然后，我们将给出另一种推导方法，该方法仅使用了基本的 CFT，并涉及编织和 [[任意子]] 的操作意义。

# 附录
## 附录 A: 无涡相位稳定性的数值结果

本研究的目标是比较无涡流相的能量与其他相的能量。已经最仔细地研究了 $J_x = J_y = J_z = 1$ 的情况。无涡流相的能量等于每个晶胞（即每两个站点或一个六边形）的 $E_0 \approx -1.5746$. 实际的计算是在每个方向上具有周期性或反周期性边界条件的环面上进行的。无涡流相和其他具有小周期的周期性相在计算上非常简单，因此处理大环面不是问题。然而，对于任意的涡流配置，能量计算需要找到一个 $N \times N$ 矩阵的奇异值，其中 $N$ 是晶胞的数量。使用我们的设置（在 PC 上运行的 MATLAB），我们可以处理大小为 $N \leq 2500$ 的矩阵，这对应于线性尺寸 $L = \sqrt{N} \leq 50$ 的系统。尽管这些数字相当大，但由于能谱的无能隙性质（见[[#IV. 费米子的谱和相图|第 4 节]]），有限尺寸效应仍然是可感知的。![[截图-1698749213381.png#R|图 11|400]]


```ad-info
title: 图 11

无涡旋相的有限尺度效应
```

首先让我们讨论在无涡旋的相位中的有限尺寸效应. 从现在开始，我们考虑相对能量，即我们从实际结果中减去 $NE_0$. 图 11a 中的图表显示了相对能量作为大小的函数，对称的 $L \times L$ 环面上的大小. 振荡行为的周期为 3，这是因为 $ε(\vb*{q})$ 在 $\vb*{q} = \vb*{q}_\ast$ 处为零（参见 [[#^d51420]]）。可以争论环面的每个周期 $\vb*{r}$ 对总能量的贡献约为 $\sim \abs{\vb*{r}}^{-1} \cos (2(\vb*{q}_\ast, \vb*{r}))$（因为周期形成一个晶格，有无穷多个这样的项）。有趣的是，在具有基矢 $(L \vb*{n}_1, L \vb*{n}_2 + \vb*{n}_1)$ 的环面上，这些贡献几乎互相抵消了，该基矢是晶格的基矢（见等式（32）中的图示）. 相应的图表显示在图 11b 中.

孤立涡旋的能量 $E_{\text{vortex}} \approx 0.1536$，高于基态能量. 计算是针对基矢 $(L \vb*{n}_1，L \vb*{n}_2 + \vb*{n}_1)$ 的 $L = 9, \cdots, 32$ 的环面完成的（实际上在两倍大小的环面上放了 4 个涡旋，因为涡旋的数量必须是偶数）. 然后，将数据拟合到曲线 $E(L) = E_{\text{vortex}} + a_1 L^{-1} + a_2 L^{-2}$ 中，分别对 $L = 3k$，$L = 3k + 1$ 和 $L = 3k + 2$ 进行拟合（见图 12）.![[截图-1698752128394.png#R|图 12|400]]

```ad-info
title: 图 12
外推到无限大小: 环面上 $4$ 个等距涡，以 $(2L \vb*{n}_1, 2(L \vb*{n}_2 + \vb*{n}_1))$ 为基.
```

涡旋对的能量小于 $2 E_{\text{vortex}}$，如果涡旋彼此靠近的话，最近邻的情况下大约减小了约 $0.04$，次近邻的情况下大约减小了约 $0.07$（我们没有试图补偿有限尺寸效应，因此精度较低）。这些数字表明涡旋之间的相互作用相当强大，原则上可能导致一些构型具有负能量。然而，我们的进一步计算提供了相反的证据。我们已经检查了包含 1, 2, 3 或 4 个六边形的单元格的所有周期性相位，详见表 4.（如上所述，与研究单个涡旋或涡旋对相比，这种计算需要较少的计算资源）. ![[截图-1698752944661.png#R|表 4|400]]

```ad-info
title: 表 4
$J_x = J_y = J_z = 1$ 的数值结果。漩涡用灰色表示; 对于周期相位，单元用平行四边形表示。
```

在所有这些情况下，能量都是正的，并随着涡旋数量的增加而增加。每个涡旋的最小能量由相位 1 和 5 实现，分别为 0.067 和 0.078. 所有 14 个相位对于 $J_x$, $J_y$, $J_z$ 的所有非零值都具有正能量（相对于无涡旋相位而言）.




## 附录 B: 相 $B_\nu$ 中的边缘模

## 附录 C: 准对角矩阵

## 附录 D: 关于手性中心电荷的一些评论

## 附录 E: 任意子的代数理论

## 附录 F: 弱对称破缺

Wen [^95][^96]


[^1]: J. Bellissard, A. van Elst, H. Schulz-Baldes, “The noncommutative geometry of the quantum Hall effect,” J. Math. Phys. 35, 5373–5451, (1994), cond-mat/9411052. [[量子霍尔效应的非对易几何]]
[^2]: F.Wilczek, “Magnetic flux, angular momentum, and statistics”, Phys. Rev. Lett. 48, 1144–1146 (1982). [[磁通, 角动量与统计]]
[^3]: F.Wilczek, “Remarks on dyons”, Phys. Rev. Lett. 48, 1146–1149 (1982).
[^4]: G.Moore, N. Seiberg, “Classical and quantum conformal field theory”, Commun. Math. Phys. 123 no. 2, 177–254 (1989).
[^5]: E.Witten, “Quantum field theory and the Jones polynomial”, Commun. Math. Phys. 121 no. 3, 351–399 (1989).
[^6]: K. Fredenhagen, K. H. Rehren, B. Schroer, “Superselection sectors with braid group statistics and exchange algebras, I: General theory”, Commun. Math. Phys. 125 no. 2, 201–226 (1989).
[^7]: J. Fr¨ohlich, F.Gabbiani, “Braid statistics in local quantum field theory”, Rev. Math. Phys. 2 no. 3, 251–353 (1990).
[^8]: R. B. Laughlin, “Anomalous quantum Hall effect — an incompressible quantum fluid with fractionally charged excitations,” Phys. Rev. Lett. 50, 1395–1398 (1983).
[^9]: L. Saminadayar, D. C.Glattli, Y. Jin, B. Etienne, “Observation of the e/3 fractionally charged Laughlin quasiparticles”, Phys. Rev. Lett. 79, 2526–2529 (1997), cond-mat/9706307.
[^10]: R. de-Picciotto, M. Reznikov, M. Heiblum, V. Umansky, G. Bunin, D.Mahalu, “Direct observation of a fractional charge”, Nature 389, 162–164 (1997), cond-mat/9707289.
[^11]: B. I. Halperin , “Statistics of quasiparticles and the hierarchy of fractional quantized Hall states”, Phys. Rev. Lett. 52, 1583–1586 (1984).
[^12]: D. Arovas, J. R. Schrieffer, and F.Wilczek, “Fractional statistics and the quantum Hall effect”, Phys. Rev. Lett. 53, 722–723 (1984).
[^13]: F. E. Camino, W. Zhou, V. J.Goldman, “Direct observation of fractional statistics in two dimensions”, cond-mat/0502406.
[^14]: G.Moore, N. Read, “Nonabelions in the fractional quantum Hall effect,” Nucl. Phys. B 360, 362–396 (1991).
[^15]: G.Moore, N. Read, “Fractional quantum Hall effect and nonabelian statistics”, hep-th/9202001.
[^16]: M. B. Hastings, “Lieb-Schultz-Mattis in higher dimensions”, Phys. Rev. B 69, 104431 (2004), cond-mat/0305505.
[^17]: P.W. Anderson, “Resonating valence bond: A new kind of insulator?”, Mat. Res. Bull. 8, 153–160 (1973).
[^18]: P.W. Anderson, “The resonating valence bond in La2CuO4 and superconductivity”, Science 235, 1196–1198 (1987).
[^19]: R.Moessner, S. L. Sondhi, “Resonating valence bond phase in the triangular lattice quantum dimer model”, Phys. Rev. Lett. 86, 1881–1884 (2001), cond-mat/0007378.
[^20]: N. Read, B. Chakraborty, “Statistics of the excitations of the resonating-valence-bond state”, Phys. Rev. B 40, 7133–7140 (1989).
[^21]: T. Senthil, M. P. A. Fisher, “Fractionalization in the cuprates: Detecting the topological order”, Phys. Rev. Lett. 86, 292–295 (2001), cond-mat/0006481.
[^22]: D. A. Bonn, J. C.Wynn, B.W.Gardner, Yu-Ju Lin, Ruixing Liang, W. N. Hardy, J. R. Kirtley, K. A.Moler, “A limit on spin-charge separation in high-Tc superconductors from the absence of a vortex-memory effect”, Nature 414, 887–889 (2001).
[^23]: R. Coldea, D. A. Tennant, A.M. Tsvelik, Z. Tylczynski, “Experimental realization of a 2d fractional quantum spin liquid”, Phys. Rev. Lett. 86, 1335–1338 (2001), cond-mat/0007172.
[^24]: A. Yu. Kitaev, “Fault-tolerant quantum computation by anyons”, Annals of Physics 303 no. 1, 2–30 (2003), quant-ph/9707021. [[通过任意子的可容错量子计算_Kitaev]]
[^25]: S. Doplicher, J. E. Roberts, “Why there is a field algebra with a compact gauge group describing the superselection structure in particle physics”, Commun. Math. Phys. 131 no. 1, 51–107 (1990).
[^26]: S. Doplicher, J. E. Roberts, “A new duality theory for compact groups” Invent. Math. 98 no. 1, 157–218 (1989).
[^27]: M. H. Freedman, M. Larsen, Z.Wang, “A modular functor which is universal for quantum computation”, Commun. Math. Phys. 227 no. 3, 605–622 (2002), quant-ph/0001108.
[^28]: T. Einarsson, “Fractional statistics on a torus”, Phys. Rev. Lett. 64, 1995-1998 (1990).
[^29]: A. Ocneanu, unpublished.
[^30]: P. Etingof, D. Nikshych, V. Ostrik, “On fusion categories”, math.QA/0203060.
[^31]: N. Read, E. Rezayi, “Beyond paired quantum Hall states: Parafermions and incompressible states in the first excited Landau level”, Phys. Rev. B, 59 8084–8092 (1999), cond-mat/9809384.
[^32]: R.W. Ogburn, J. Preskill, “Topological quantum computation”, Lecture Notes in Computer Science 1509, C. P.Williams (ed.) QCQC’98, pp. 341–356, Springer-Verlag (1999).
[^33]: J. Preskill, “Fault-tolerant quantum computation”, quant-ph/9712048.
[^34]: C.Mochon, “Anyon computers with smaller groups”, Phys. Rev. A 69, 032306 (2004), quant-ph/0306063.
[^35]: M. H. Freedman “Amagnetic model with a possible Chern-Simons phase”, Commun. Math. Phys. 234 no. 1, 129–183 (2003), quant-ph/0110060.
[^36]: M. Freedman, C. Nayak, K. Shtengel, K.Walker, Z.Wang, “A Class of P, T-Invariant Topological Phases of Interacting Electrons”, cond-mat/0307511.
[^37]: M. Freedman, C. Nayak, K. Shtengel, “Non-Abelian topological phases in an extended Hubbard model”, cond-mat/0309120.
[^38]: B. Dou¸cot, J. Vidal, “Pairing of Cooper Pairs in a Fully Frustrated Josephson Junction Chain”, Phys. Rev. Lett. 88, 227005 (2002)cond-mat/0202115.
[^39] L. B. Ioffe, M. V. Feigel’man, “Possible realization of an ideal quantum computer in Josephson junction array”, Phys. Rev. B 66, 224503 (2002), cond-mat/0205186.
[^40] B. Dou¸cot, L. B. Ioffe, M. V. Feigel’man, “Topological order in the insulating Josephson junction array”, Phys. Rev. Lett. 90, 107003 (2003), cond-mat/0211146.
[^41]: B. Dou¸cot, L. B. Ioffe, M. V. Feigel’man, “Discrete non-Abelian gauge theories in two-dimensional lattices and their realizations in Josephson-junction arrays”, Phys. Rev. B 69, 214501 (2004), cond-mat/0302104.
[^42]: L.-M. Duan, E. Demler, M. D. Lukin Phys. Rev. Lett. 91, 090402 (2003), cond-mat/0210564.
[^43]: D. J. Thouless, M. Kohmoto, M. P. Nightingale, M. den Nijs, “Quantized Hall conductance in a two-dimensional periodic potential,” Phys. Rev. Lett. 49, 405–408 (1982).
[^44]: J. E. Avron, R. Seiler, B. Simon, “Homotopy and quantization in condensed matter physics,” Phys. Rev. Lett. 51, 51–53, (1983).
[^45]: A. Connes, “Noncommutative Geometry”, Academic Press (1994).
[^46]: G. E. Volovik, “Analog of quantum Hall-effect in a superfluid 3He film” Zh. Eksp. Teor. Fiz. 94 no. 9, 123–137 (1988) (in Russian) [English translation: Sov. Phys. JETP 67, 1804 (1988)].
[^47]: G. E. Volovik, V.M. Yakovenko, “Fractional charge, spin and statistics of solitons in superfluid 3He film”, J. Phys.: Condens. Matter 1, 5263–5274 (1989).
[^48]: N. Read, D.Green, “Paired states of fermions in two-dimensions with breaking of parity and time reversal symmetries, and the fractional quantum Hall effect,” Phys. Rev. B 61, 10267 (2000), cond-mat/9906453.
[^49]: A.M. Tsvelik, “Quantum field theory in condensed matter physics”, Cambridge University Press, 2nd edition (2003).
[50]: E. H. Lieb, “Flux phase of the half-filled band”, Phys. Rev. Lett. 73, 2158–2161 (1994), cond-mat/9410025. [[半填充带的通量相]]
[^51]: B. I. Halperin “Quantized Hall conductance, current-carrying edge states, and the existence of extended states in a two-dimensional disordered potential,” Phys. Rev. B 25, 2185–2190 (1983).
[^52]: Y. Hatsugai, “Chern number and edge states in the integer quantum Hall effect,” Phys. Rev. Lett. 71, 3697–3700 (1993).
[^53]: H. Schulz-Baldes, J. Kellendonk, T. Richter, “Simultaneous quantization of edge and bulk Hall conductivity,” J. Phys. A: Math. Gen. 33 L27–L32 (2000), cond-mat/9912186.
[^54]: J. Kellendonk, T. Richter, H. Schulz-Baldes, “Edge current channels and Chern numbers in the integer quantum Hall effect,” Rev. Math. Phys. 14 no. 1, 87–119 (2002).
[^55]: G. E. Volovik, “Quantum Hall and chiral edge states in thin 3He-A film”, Pis’ma v ZhETF 55 no. 6, 363–367 (1992) [JETP Letters, 55 368–373 (1992)].
[^56]: C. L. Kane, M. P. A. Fisher, “Quantized thermal transport in the fractional quantum Hall effect”, Phys. Rev. B 55, 15832–15837 (1997), cond-mat/9603118.
[^57]: A. Cappelli, M. Huerta, G. R. Zemba, “Thermal transport in chiral conformal theories and hierarchical quantum Hall states”, Nucl. Phys. B 636 no. 3, 568–582 (2002), cond-mat/0111437.
[^58]: U. Sivan, Y. Imry, “Multichannel Landauer formula for thermoelectric transport with application to thermopower near the mobility edge”, Phys. Rev. B 33, 551–558 (1986).
[^59]: L. Alvarez-Gaume, E.Witten, “Gravitational anomalies”, Nucl. Phys. B 234 no. 2, 269–330 (1984).
[^60]: G. E. Volovik, “The gravitational topological Chern-Simons term in a film of superfluid 3He-A”, Pis’ma v ZhETF 51 no. 2, 111–114 (1990) (in Russian) [English translation: JETP Letters, 51 125–128 (1990)].
[^61]: K. H. Rehren, “Braid group statistics and their superselection rules” in The algebraic theory of superselection sectors, D. Kastler (ed.) Proceedings Palermo 1989, pp. 333–355, World Scientific Publishing (1990).
[^62]: E. Verlinde, “Fusion rules and modular transformations in 2D conformal field theory”, Nucl. Phys. B 300, 360–376 (1988).
[^63]: P. Di Francesco, P.Mathieu, D. S´en´echal, “Conformal field theory”, Springer (1996).
[^64]: A. Yu. Kitaev, “Unpaired Majorana fermions in quantum wires”, cond-mat/0010440.
[^65]: D. A. Ivanov, “Non-Abelian statistics of half-quantum vortices in p-wave superconductors”, Phys. Rev. Lett. 86, 268–271 (2001), cond-mat/0005069.
[^66]: N. Reshetikhin, V.G. Turaev, “Invariants of 3-manifolds via link polynomials and quantum groups”, Inventiones Mathematicae 103 no. 3, 547–597 (1991).
[^67]: K.Walker, “On Witten’s 3-manifold invariants”, http://canyon23.net/math/ (1991).
[^68]: V.G. Turaev, “Quantum invariants of knots and 3-manifolds” (de Gruyter Studies in Mathematics 18), de Gruyter (1994).
[^69]: V. Kalmeyer, R. B. Laughlin, “Equivalence of the resonating-valence-bond and fractional quantum Hall states”, Phys. Rev. Lett. 59, 2095–2098 (1987).
[^70]: M. V. Feigel’man, A. Yu. Kitaev, unpublished.
[^71]: R. B. Laughlin, “Quantized Hall conductivity in two dimensions,” Phys. Rev. B 23, 5632–5633 (1981).
[^72]: J. E. Avron, R. Seiler, B. Simon, “Quantum Hall effect and the relative index of projections,” Phys. Rev. Lett. 65, 2185–2189 (1990).
[^73]: J. E. Avron, R. Seiler, B. Simon, “Charge deficiency, charge transport and comparison of dimensions,” Commun. Math. Phys. 159 no. 2, 399–422 (1994), physics/9803014.
[^74]: J. E. Avron, R. Seiler, B. Simon, “The index of a pair of projections,” J. Func. Analysis 120, 220–237 (1994).
[^75]: E.M. Rains, “Correlation functions for symmetrized increasing subsequences”, math.CO/0006097.
[^76]: D. A. Rokhsar, S. A. Kivelson, “Superconductivity and the quantum hard-core dimer gas”, Phys. Rev. Lett. 61, 2376–2379 (1988).
[^77]: E. H. Lieb, D.W. Robinson, “ The finite group velocity of quantum spin systems”, Commun. Math. Phys. 28, 251–257 (1972).
[^78]: R. Haag, “Local quantum physics”, Springer Verlag, 2nd edition (1996).
[^79]: B. Bakalov, A. Kirillov Jr., “Lectures on tensor categories and modular functors” (University Lecture Series 21), American Mathematical Society (2001).
[^80]: C. Kassel, “Quantum groups” (Graduate Texts in Mathematics 155), Springer Verlag (1995).
[^81]: J. Preskill, “Topological quantum computation”, (Chapter 9 of Lecture notes on quantum computation), http://www.theory.caltech.edu/people/preskill/ph229/#lecture (2004).
[^82]: S.Mac Lane, “Categories for the working mathematician” (Graduate Texts in Mathematics 5), Springer Verlag, 2nd edition (1998).
[^83]: J. D. Stasheff, “Homotopy associativity of H-spaces” (parts I and II), Trans. Amer. Math. Soc. 108, 275–292 and 293–312 (1963).
[^84]: J.-L. Loday, “Realization of the Stasheff polytope” Arch. Math. (Basel) 83 no. 3, 267–278 (2004), math.AT/0212126.
[^85]: V.G. Drinfeld, “Quantum groups”, Proceedings of the International Congress of Mathematicians, Berkeley 1986, pages 798–820, Amer. Math. Soc. (1987).
[^86]: F. A. Bias, P. van Driel, M. de Wild Propitius, “Quantum symmetries with discrete gauge symmetries”, Phys. Lett. B 280, 63–70 (1992), hep-th/9203046.
[^87]: R. Dijkgraaf, V. Pasquier, P. Roche, “Quasi Hopf algebras, group cohomology and orbifold models”, Nucl. Phys. B (Proc. Suppl.) 18, 60–72 (1991).
[^88]: F. A. Bias, P. van Driel, M. de Wild Propitius, “Anyons in discrete gauge theories with Chern-Simons term”, Nucl. Phys. B 393, 547–570 (1993), hep-th/9203047.
[^89]: K. Fredenhagen, K. H. Rehren, B. Schroer, “Superselection sectors with braid group statistics and exchange algebras, II: Geometric aspects and conformal covariance”, Rev. Math. Phys. special issue 1, 113–157 (1992).
[^90]: C. Vafa, “Toward classification of conformal theories”, Phys. Lett. B 206, 421–426 (1988).
[^91]: L. Crane, D. N. Yetter, “Deformations of (bi)tensor categories”, Cahiers Topologie G´eom. Diff´erentielle Cat´eg. 39 no. 3, 163–180 (1998), q-alg/9612011.
[^92]: A. A. Davydov, “Twisting of monoidal structures”, q-alg/9703001.
[^93]: D. N. Yetter, “ Functorial knot theory”, (Series on Knots and Everything, 26), World Scientific Publishing (2001).
[^94]: A. Rosenberg, “The existence of fiber functors”, Gelfand Mathematical Seminars 1996–1999, 145–154, Birkh¨auser Boston (2000).
[^95]: X.-G.Wen, “Quantum orders and symmetric spin liquids”, Phys. Rev. B 65, 165113 (2002), cond-mat/0107071. [[量子序与对称自旋液体]]
[^96]: X.-G.Wen, “Quantum orders in an exact soluble model”, Phys. Rev. Lett. 90, 016803 (2003), quant-ph/0205004. [[精确可解模型中的量子序]]
[^97]: R. Dijkgraaf, E.Witten, “Topological gauge theories and group cohomology”, Commun. Math. Phys. 129 no. 2, 393–429 (1990).
[^98]: A. Hatcher, “Algebraic topology”, Cambridge University Press (2002).
[^99]: J. P.May, “Simplicial objects in algebraic topology” (Chicago Lectures in Mathematics Series) University of Chicago Press, Reprint edition (1993).


