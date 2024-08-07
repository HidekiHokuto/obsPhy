---
tags:
  - 论文
created: 2024-07-16 19:05:10
aliases:
  - Symmetric Infinite Projected Entangled-Pair State Study of Quantum Lattice Models
DOI: 
author:
  - Changkai Zhang
original title: Symmetric Infinite Projected Entangled-Pair State Study of Quantum Lattice Models
year: "2021"
---

# 摘要

强关联系统中存在诸多有趣的现象及物相。对这些现象及物相的研究获得了凝聚态物理学术界的广泛关注。然而，对多体系统的直接暴力求解是几乎不可行的，因为多体系统具有指数级增长的自由度。张量网络技术的出现给我们提供了一个极具竞争力的计算框架从而克服复杂度问题。在这篇论文中，我们利用无限投影纠缠对态 (infinite Projected Entangled-Pair State, iPEPS) 张量网络来模拟带有近邻或次近邻相互作用的、正方形晶格上的二维量子模型。与其它广泛应用的数值方法相比，例如密度矩阵重整化群 (Density Matrix Renormalization Group, DMRG) 及量子 Monte-Carlo 方法，iPEPS 具有忠实表示纠缠面积定律及不受符号问题的影响的独特优势。因此，它特别适合用于研究 fermionic 模型，比如能够产生诸多包括高温超导在内的有趣现象的 Hubbard 模型。

我们 iPEPS 算法的一个独特优势即是可以利用对称性。QSpace 张量程序库可以自动追踪张量的 U(1) 和 SU(2) 对称性。这将极大降低对计算资源的需求并且允许对带有不同对称性的量子态进行研究。

本文中研究的量子格点模型包括 *Heisenberg 模型*，*自由 fermion 模型*以及 *Hubbard 模型*。我们用成熟的模型 (例如近邻 Heisenberg 模型) 以及一个理论可解的自由 fermion 模型来验证我们的 iPEPS 算法。特别地，我们研究了次近邻 Hubbard 模型在次近邻 hopping 幅 t2=−0.25t_2 = -0.25t_2 = -0.25 及 1/8 参杂下带有 U(1) 及 SU(2) 对称性的基态性质。值得注意的是，我们发现了一个 SU(2) 对称的基态比之前 iPEPS 发现的具有 U(1) 对称性的、带有电荷与自旋序的基态具有更低的能量。

# 1. 引言和动机

由多体相互作用引起的强量子相关的相互作用可能产生各种迷人的现象和物质的相。大多数量子多体系统的高能理论是量子电动力学。然而，直接应用量子电动力学会遇到严重的复杂性问题。即使是模拟一小块材料也已经超出了我们目前的计算能力。因此，用暴力从头算法求精确解在实际中是不可能的。

这些问题引发了凝聚态物理学的出现，它试图通过有效的理论来解决量子多体物理。其基本思想是，当存在大量相互作用的粒子时，就会出现集体自由度，并且整个系统可以用演生的准粒子及其之间的相互作用来有效地描述。著名的例子包括布洛赫的近自由电子模型和朗道的费米液体理论。然而，大多数有效的理论高度依赖于摄动方法，只有当相互作用足够弱时才有效。

在过去的几十年里，人们发现了许多传统有效理论无法解释的奇特现象。例子包括莫特绝缘体[1]，高tc超导[2][3]，受挫量子磁体[4]，分数量子霍尔效应[5]等等。这些有趣现象的共同特征是，它们通常存在于特别设计的材料中，其中粒子之间的相互作用被强烈增强，并且变得与动能相当甚至更大。强相互作用导致强量子关联，从而产生这些非常规效应.

强关联的出现要求采用可考虑完整多体波函数的替代非微扰方法。这对理论和数值分析都提出了新的挑战。幸运的是，最近关于张量网络的研究，特别是无限投影纠缠对态(iPEPS)[6-8]，显示出它们在解决量子多体问题方面具有很强的竞争力。这就是本文所采用的方法。

投影纠缠对态(PEPS)[9]是一种专门用于模拟二维量子晶格模型量子态的张量网络态分析。利用平移不变性，无限PEPS (iPEPS)[10]可以通过有限张量表示无限扩展的量子态。与其他流行的数值方法相比，iPEPS具有忠实地表示纠缠特性的优点，并且避免了符号问题。因此，它在模拟费米子模型方面特别有竞争力，因为*费米子模型孕育了许多强关联现象*。在接下来的两节中，我们将讨论本文研究的重要有效模式以及iPEPS在这些背景下的主要好处。

## 1.1. 有效量子晶格模型

强相关系统内部的物理学包括电子和核子之间复杂的相互作用。因此，需要额外的近似来降低计算的复杂性。一个常见的策略是考虑在晶格上定义的有效哈密顿量。有效的哈密顿量包含了相当少的自由度，并且应该捕捉原始高能理论的基本(低能)特性。因此，通过研究有效哈密顿量，我们仍然可以学到很多关于其背后的物理原理。

自然界中存在许多不同的晶格几何形状。然而，许多显著的强相关现象，如铜酸盐中的高tc超导，存在于方形晶格上。因此，本文将重点研究定义在方形晶格上的量子晶格模型。

### 1.1.1. Heisenberg 模型

### 1.1.2. Hubbard 模型

哈伯德模型[12]被认为是捕获高温超导体背后基本物理的有效模型。哈伯德模型通常由描述电子从一个位置跳到另一个位置的动力学项和一个现场相互作用项组成。具有最近邻跳变的哈伯德模型的哈密顿量可以写成

## 1.2. 常用数值方法

# 2. 张量网络技术

张量网络技术包括一系列用于多体物理的数值方法，这些方法将量子态编码为张量网络。本文采用的主要张量网络方法是*无限投影纠缠对态*(iPEPS)方法。第2.1节介绍了张量的图形符号，极大地简化了对它们的处理。第2.2节通过引入矩阵积态(MPS)方法，激励了张量网络在一维晶格模型中的使用。第2.3节和第2.4节分别说明了费米子统计是如何实现的，以及如何跟踪张量网络中的对称性。第2.5节介绍了处理二维模型的PEPS方法，随后的2.6节详细说明了如何通过角转移矩阵(CTM)方案实现iPEPS。然后，2.7节给出了获取给定模型基态的核心算法——简单更新方案(适用于同时具有最近邻和次近邻交互作用的模型)和完整更新方案(仅适用于具有最近邻交互作用的模型)。最后，第2.8节演示了如何在iPEPS的形式体系中测量可观测值。

## 2.1. 图形记法
本节解释张量的图形表示法和它们的收缩运算. 张量网络方法通常涉及高阶张量的复杂操作。用传统的数学公式表示所有这些张量运算将导致具有许多张量索引的冗长表达式。此外，许多二维张量表达式的意义在逐行写出时会变得模糊不清。因此，类似于费曼图已被广泛用于微扰理论，张量网络的图形表达式调用，以克服公式的不便。

张量网络图通常由圆（或矩形等）组成。和线的组合。每个圆圈代表一个张量，与圆圈相连的直线代表张量的指数。图2.1给出了 rank-1 张量（向量）、rank-2 张量（矩阵）和 rank-3 张量的图解表达式的三个例子。Line 的方位通常是无关紧要的，而在费米情况下 line 的顺序是至关重要的。

张量的收缩用对应于同一指数的连线来图解表示。如图2.2所示，对应于 index $\beta$ 的内部线表示收缩。通常，开放的线被称为 legs，连接的线被称为 bonds.

张量网络可以涉及许多收缩操作。并且*进行收缩的顺序不影响所获得的结果*。然而，它确实影响了算法的计算复杂度。计算复杂度可以直接从张量图中读出。例如，计算图 2.2 中的收缩需要 $\order{\mathcal{D}\qty[\alpha] \mathcal{D}\qty[\sigma] \mathcal{D}\qty[\beta] \mathcal{D}\qty[\rho] \mathcal{D}\qty[\gamma]}$ 个运算，其中 $\mathcal{D}\qty[i]$ 是 index $i$ 的维数。一般来说，计算复杂度是图中出现的所有线的维数的乘积。然而，根据图的拓扑，实际的数值成本可能取决于计算收缩的顺序。

## 2.2. 矩阵乘积态

在讨论二维张量网络之前，让我们先从一维的情况开始。这里不打算详细和独立地讨论一维模型和算法。然而，在各种张量网络形式中经常遇到的许多基本概念在简单的一维情况下变得更加直观。因此，详细说明这些基本组成部分，然后推广到更高的维度，将是有益的。

考虑一个定义在长度为 $N$ 的一维链上的量子晶格模型，每个晶格点拥有一个维数为 $d$ 的局部状态空间。那么，任何量子态都可以利用 Fock 空间 $\ket{\sigma_1} \ket{\sigma_2} \cdots \ket{\sigma_N}$ 展开
$$
\ket{\psi} = \sum_{\sigma_1,\sigma_2, \cdots, \sigma_N} \varPsi^{\sigma_1\sigma_2 \cdots \sigma_N} \ket{\sigma_1} \ket{\sigma_2} \cdots \ket{\sigma_N}
$$


系数 $\varPsi^{\sigma_1\sigma_2 \cdots \sigma_N}$ 可以看作是一个 rank-N 张量。而张量网络技术正是用来构造和分析这个张量的方法。矩阵积态(Matrix Product State, MPS)的思想[^23][^24][^25]是将这个大张量分解为一组3阶张量的积为
$$
\varPsi^{\sigma_1 \sigma_2 \cdots \sigma_N}=\sum_{\alpha_1,\alpha_2,\cdots,\alpha_N} A_{\alpha_1}^{\sigma_1} A_{\alpha_1 \alpha_2}^{\sigma_2} \cdots A_{\alpha_{N-2} \alpha_{N-1}}^{\sigma_{N-1}} A_{\alpha_{N-1}}^{\sigma_N}
$$
这么长的数学公式，既不方便，也没有足够的信息量。因此，将调用上一节中介绍的图表表达式。从图表上看，上述公式可以重写为图2.3[^25]所示。

> **Fig. 2.3** ![[截图-1720759077004.png#R|Fig. 2.3|400]]
> 多体波函数的矩阵积态表示。张量 $\varPsi$ 的每个分量由一系列矩阵乘积获得。

MPS 代表的动机很简单。第一个张量 $A^{\sigma_1}_{\alpha_1}$ 是一个幺正变换，它改变了与第一个点相关的局部空间的基。第二个张量 $A^{\sigma_2}_{\alpha_1 \alpha_2}$ 取第一个点的局部态(用指标 $\alpha_1$ 表示)和第二个点的局部态(*物理指标* $\sigma_2$)，并将它们组合成一个用 virtual bond index $\alpha_2$ 标记的二体态。重复这个过程，直到所有的 $N$ 个位点都被包括在内。

> **Fig. 2.4** ![[截图-1720759378375.png#R|Fig. 2.4|300]]
> *张量 $A$ 的奇异值分解(SVD)*，其中 $U^\dagger U = 1$, $V^\dagger V = 1$, $S$ 是一个非负对角矩阵。截断可以通过只保留最大的奇异值来执行。

这种构造可以精确地生成 MPS 形式的波函数，而不需要任何近似。很明显，键 $\alpha_i$ 的维数是 $d^i$，它仍然呈指数增长。因此，需要采取额外的措施来减小键的尺寸。

我们要采用的技术是在数据压缩领域已经得到广泛应用的奇异值分解(SVD)。由奇异值分解得到的奇异值可以很好地衡量各谱对原始信息重构的贡献。图2.4显示了张量 $A$ 的奇异值分解(SVD)。接下来，截断矩阵 $S$，只保留最大的 $D$ 个奇异值。然后，将 $U$ 的截断版本作为 $A$ 的新版本，并将 $S$ 和 $V^\dagger$ 缩并到后续张量中。SVD 随后可以从左到右(从右到左)进行，并产生键维不大于 $D$ 的左归一化(右归一化)张量(定义见图2.5)。

> **Fig. 2.5** ![[截图-1720759758474.png#R|Fig. 2.5|300]]
> 
> 左归一化和右归一化张量。$\mathbb{1}$ 标记单位矩阵。两者都可以通过 SVD 生成。


张量 $\varPsi$ (视为线性算符)的厄米共轭可以立即从 MPS 形式得到。从图表上看，只需要执行图2.3[^25]中的垂直翻转。

> **Fig. 2.6** ![[截图-1720759956809.png#R|Fig. 2.6|400]]
> 张量 $\varPsi$ 的厄米共轭的 MPS 表示。从图表上看，这只是图 2.3 的垂直翻转。

可观测对象的计算也可以通过使用 ket 和 bra 的 MPS 表示来明确。例如，如果我们有局部可观测值 $O_i$ 和 $O_j$ 分别位于站点 $i$ 和 $j$，关联 $\mel*{\psi}{O_iO_j}{\psi}$ 可以使用图 2.7 所示的图来计算。

> **Fig. 2.7** ![[截图-1721231873082.png#R|Fig. 2.7|350]]
> 使用 MPS 表示的可观察测量。$O_i$ 和 $O_j$ 是分别位于 site $i$ 和 $j$ 的两个局部观测量。

由张量 $A$ 的奇异值分解得到的奇异值具有重要的物理意义。为了理解这一点，我们需要图 2.8 所示的 MPS 的 Lambda-Gamma 形式。在 Lambda-Gamma 形式[^26][^27]中，奇异值矩阵Λ被插入到任意两个秩为3的Γ张量之间。通过将Λ矩阵吸收到相邻的Γ张量中，例如定义Ai <$Λi−1Γi（左归一化）或Bi <$ΓiΛi（右归一化），可以恢复MPS的原始形式。

## 2.3. 费米子统计

在前面的讨论中，我们暗示张量网络遵循玻色子统计。然而，大部分的注意力和努力都集中在包含费米子的强相关系统上。费米子晶格模型(如哈伯德模型)特别具有挑战性，部分原因是最有效的竞争对手量子蒙特卡罗方法存在符号问题。因此，人们对张量网络技术寄予厚望。

### 2.3.1. 宇称守恒

大多数费米子系统保持费米子数量的宇称性，即系统中费米子的数量是奇数还是偶数。这种 $Z_2$ 宇称对称对张量网络[^6][^29]中的张量提出了限制。由于张量只是表示量子态，它们也应该保持宇称对称 $p$，即
$$
A_{\alpha \beta}^\sigma = 0, \qq{if} p(\alpha)p(\beta) p(\sigma)=-1
$$
其中 $p(\alpha) \in \qty{−1,1}$ 表示索引 $\alpha$ 对应的状态奇偶性;

$p =-1$ 表示费米子数为奇数，$p = 1$ 表示费米子数为偶数。可以使用 2.4 节中介绍的对称跟踪技术来记录计算过程中的奇偶传播。

为方便起见，我们要求所有进入算法的张量都符合上述奇偶规则。一些算符，如费米子产生 $c^\dagger$ 和湮灭 $c$ 算符，并不自然地支持宇称守恒。这种情况下所需的额外设置将在本节后面讨论。

### 2.3.2. 费米子交换门

宇称对称本身并不能捕获费米子统计。然而，量子态本身的宇称是确定费米子符号的关键信息。具有*奇数个费米子的量子态可以用奇数个创造算符*来创造。因此，交换奇数奇偶校验的两个索引的顺序会产生一个负号。这个过程可以通过所谓的 fermionic swap gate [^6][^29]来实现，如图 2.11 所示。因此，费米子张量网络图中的每条线交叉都应由交换门代替。

> **Fig. 2.11** ![[截图-1720671024174.png#R|Fig. 2.11|300]]
> 费米子交换门的定义和图解。张量网络中的每条线交叉都需要一个交换门。
> 
> 当 $p(\alpha) = p(\beta) =-1$ 时 $\text{SWAP}(\alpha,\beta) =-1$，否则 $\text{SWAP} (\alpha,\beta) = 1$.

如图 2.11 所示，当交叉线都携带 odd fermionic parity 时，交换门通过增加一个额外的负号来计算费米子统计。对于复杂的张量网络图，特别是二维张量网络图，可能存在许多不可避免的线交叉。然而，增加交换门并不会改变表面上的计算复杂度，因为交换门的每个应用都可以被吸收到一个张量中。因此，只需要在算法中的适当位置添加交换门。

### 2.3.3. 费米子算符
前面已经说过，我们限制进入费米子张量网络算法的张量是宇称保持的。这很容易被描述量子态的张量所满足。然而，一些重要的算符如产生和湮灭算符违反宇称规则。因此，我们使用了一种技巧，即添加一个辅助 leg，该分支只接受一个值和奇数奇偶校验[^6][^29]，如图 2.12 所示。

> **Fig. 2.12** ![[截图-1720671606218.png#R|Fig. 2.12|300]]
> 表示宇称变化费米子算符的张量需要一个辅助 leg，根据定义具有奇宇称，以保持宇称守恒要求。
> 


产生 $c^\dagger$ 和湮灭 $c$ 算符通过增加或减少一个费米子来改变宇称。因此，$\sigma$ 和 $\sigma'$ 的宇称是相反的。通过附加一个带有奇宇称的额外 index $\delta$，可以获得宇称守恒
$$
p(\sigma) p(\sigma')p(\delta) = -p(\delta) = 1
$$
我们通过提到另一个可能的微妙之处来结束本节，这个微妙之处是关于一些 two-site basis 的 two-site 算符的展开。基 $\ket{\sigma_i \sigma_j}$ 的厄米共轭是 $\bra{\sigma_j \sigma_i}$ (注意，$\sigma_i$ 和 $\sigma_j$ 的顺序互换了)，其中 $\sigma_i \in \qty{0,1}$ 表示位置 $i$ 的占有数，$\sigma_j$ 也是如此。因此，建议人们特别注意可能出现在 two-site 算符的某些 components 中的负号.

## 2.4. 对称跟踪

对称是物理学中最基本的概念之一。在量子物理学中，对称产生的量子数是不同量子态的唯一指示。此外，量子相变通常伴随着对称的转换。

在张量网络的背景下，追踪网络中的对称性可能会产生深远的影响。对称性的存在意味着张量可能是高度稀疏的，人们可以利用对称性进行压缩，这可能会导致巨大的数值进步。此外，通过打开不同的对称性，人们可以在特定的感兴趣的模型中研究可能的对称性破坏。

在本文中，对称跟踪的工作移交给QSpace库[30]。在这里，我们只讨论对称记账的基本机制。有关更多技术细节，建议查阅介绍性论文[29]或QSpace库[30]的文档。

### 2.4.1. 对称与群

强相关系统通常包含大量不同的对称性。数学上，对称性可以用群理论来处理。在讨论费米子张量网络 [[#2.3. 费米子统计|2.3]] 时，我们利用了宇称 $Z_2$ 对称性。$U(1)$ 对称是另一种常见的对称，它可以解释电荷守恒。许多*自旋模型*保持了 $SU(2)$ 对称性，从而保持了系统的总自旋。尽管在一些强相关系统中也可能存在更复杂的对称性，但本文并未使用它们。

```ad-note
费米子: parity $Z_2$ 对称性
电荷守恒: $U(1)$ 对称性
总自旋守恒: $SU(2)$ 对称性
```

对称的一个直接结果是哈密顿量 $H$ 和对称群产生子 $T_i$ 的对易，即 $\comm{H}{T_i} = 0$. 这表明哈密顿量可以写成块对角线形式，只包含块(称为对称扇区)内的非零元素。因此，通过去除不必要的零元素，可以获得很大的计算效益。系统越复杂，其数值效益就越明显。



### 2.4.2. 阿贝尔对称

阿贝尔对称是一种简单的对称，其中对称群中的任意两个元素都可以相互交换。量子态 $\ket{ql}$ 可以使用两个数字 $q$ 和 $l$ 来识别保持阿贝尔对称性的ql，其中 $q$ 表示对称量子数，并且 $l$ 进一步解析具有相同量子数的不同状态。以双电子系统中 $U(1)$ 电荷对称性为例。在这种情况下，$q$ 表示系统的总电荷。有三种可能性：$q = 0,-1,-2$. 第一个和第三个状态是由下列等式唯一生成的：$\ket{0}\ket{0}$ 与 $\ket{-1}\ket{-1}$. 而第二状态可以是 $\ket{-1}\ket{0}$ or $\ket{0}\ket{-1}$. 因此，需要额外的 $l$ 来区分这两种状态。

多体状态张量网络描述的基本组成部分是将多个状态组成新的状态的张量。MPS 形式体系中的 rank-3 张量就是一个直接的例子。当打开阿贝尔对称性时，这个张量可以改写为
$$
\ket{q''n} = \sum_{ql, q'm} [A_{q'q''}^q]_{mn}^l \ket{ql} \ket{q'm}
$$

其中量子数作为附加标签输入。从数字上讲，这意味着更多的簿记工作。然而，在对称的情况下，量子数必须服从选择规则，例如在 $U(1)$ 对称中，$q'' = q + q'$. 这导致了相当大的数值加速和降低内存成本。

### 2.4.3. 非阿贝尔对称: $SU(2)$

在这篇论文中，我们将广泛地利用非阿贝尔 $SU(2)$ 对称性。我们需要两个量子数 $q$ 和 $q_z$ 来指定一个独特的 $SU(2)$ 表示。然而，还需要额外的标记 $l$ 来选择唯一的量子态。以三自旋系统中的 $SU(2)$ 自旋对称性为例。$S = 1/2$，$S_z = 1/2$ 有两种状态，即|↑刘晓波（|↑↓−| ↑↓| ↓| ↑↑。根据Wigner-Eckardt定理，张量具有以下形式：

### 2.4.4. 图像特征

保持一定对称性的张量有一个额外的图解特征。如图 2.13 所示，张量的每条腿都有一个箭头，从传入腿（bra）和传出腿（ket）流出的量子数流应该在方程意义下守恒。(2.6)，（2.7）和（2.8）。没有客观的选择的公约的箭头。然而，在整个计算过程中必须保持相同的约定。

> **Fig. 2.13** ![[截图-1721125288520.png#R|Fig. 2.13|400]]
> 张量和对称矩阵乘积状态的图解表示。箭头用来表示量子数的流动。附加一条腿以处理可能的multiplet state.


由于多体态是通过一个对称张量网络构造的，它必须保持相应对称群的某些整体量子数。对于有限大小的张量网络，人们总是可以通过在任何张量上附加一个额外的分支来瞄准具有不同全局量子数的各种状态。然而，这对于无限大小的张量网络是不可能的。因此，无限张量网络总是被限制在 singlet sector.




## 2.5. 投射纠缠对态 PEPS

投影纠缠对态(PEPS)[^9]张量网络是将矩阵积态 (MPS) 分析推广到高维。在本文中，我们只在两个维度上研究PEPS，其中出现了许多强相关现象。像它的一维对应物一样，PEPS 由张量网络组成。然而，由于现在每个位点都有四个相邻的位点，张量需要四个 virtual bonds，如图 2.14 所示.

> **Fig. 2.14**![[截图-1720672254287 1.png#R|Fig. 2.14|350]]
> 构成 PEPS 张量网络的二维张量和张量的厄米共轭。复共轭后箭头方向翻转。
> 

我们采用这样的惯例: 上肢和右肢有向外的箭，下肢和左肢有向内的箭。物理腿，在这里垂直排列，有传入箭头。厄米共轭是通过将张量图颠倒并翻转所有支脚的箭头方向来获得的。

由有限张量组成的有限尺寸PEPS[^31]模拟了有限尺寸晶格上的量子态。图 2.15 显示了描述3×3集群的pep。边界张量可能由于缺少邻近点而具有较少的 legs。在二维空间中，人们面临着安排 PEPS 物理腿的微妙之处。图2.15显示了一种可能的安排，但通常允许其他约定。然而，不同的约定可能导致交换门的不同位置，这迫使人们在整个计算过程中采用相同的约定。

> **Fig. 2.15** ![[截图-1720689245488.png#R|Fig. 2.15|400]]
> 位于 $3\times 3$ cluster 上的有限大小 PEPS。只要在整个计算过程中引用相同的约定，局部索引的排列顺序通常是无关紧要的。

每一对相邻的 local sites 都有一个相互连接的 virtual bond 的构建具有深远的意义。与通过一维张量网络[^32]遍历二维晶格的密度矩阵重整化群(DMRG)等竞争算法相比，*PEPS 能够保持二维系统所需的纠缠特性*。具体来说，对于大小为 $L \times L$ 的子区域，PEPS 张量网络的纠缠熵以
$$
S = \order{N \ln D}
$$
为界[^28].

其中 $D$ 是 PEPS 张量的键维。这符合大多数强相关系统所满足的纠缠熵面积定律。然而，在量子临界附近，可能会出现额外的对数校正项，如 $\order{L \log L}$.

$\bra{\psi}$ 在计算范数 $\ip{\psi}$ 或某些可观测值 $\ev*{O}{\psi}$ 的期望值中都是必需的。图解上，$\bra{\psi}$ 用一个简单的图 2.15 的水平镜像来表示。然而，由于物理位置安排的复杂性和交换门的不规则放置，该过程导致了笨拙的技术实现。

> **Fig. 2.16** ![[截图-1720689988189.png#R|Fig. 2.16|400]]
> 共轭张量和双层复合张量的定义。双层复合张量将用书法字母表示。

另一种方法[^6][^29]如图 2.16 所示。我们首先通过扭曲 $M^\dagger$ 的两条腿来构造共轭张量 $W$，使 $W$ 的四个虚键全部与张量 $M$ 平行。然后缩并相应的 $M$ 和 $W$ 的物理指标，重塑 $M$ 和 $W$ 的平行腿，得到用书法字母 $\mathcal{M}$ 标记的双层复合张量.

> **Fig. 2.17** ![[截图-1721126202803.png#R|Fig. 2.17|400]]
> 
> 多体波函数的范数现在由张量网络表示，该网络仅由复合张量组成，没有任何明确的费米子交换门。

利用复合张量 $\mathcal{M}$，多体波函数的 norm $\ip{\psi}$ 可改写为图2.17。图 2.16 中的过程是通用的，它把*所有的费米子交换门都包含在复合张量中*。因此，我们可以对所有站点重复相同的过程，生成图 2.17 中的张量网络，而*无需显式交换门*。

许多强关联系统位于具有平移对称性的无限大晶格上。相应地，人们可以利用平移不变性来定义无限 PEPS（iPEPS）[^10][^6]张量网络。

> **Fig. 2.18** ![[截图-1721129846392.png#R|Fig. 2.18|300]]
> 
> 具有 2×2 超胞的 iPEPS 张量网络，即整个无限张量网络由超胞的无限副本创建.

iPEPS 张量网络是由一些 supercell 的无限数量的平移副本创建的[^8]。Supercell 充当相应的无限张量网络的“单位原胞”。图 2.18 显示了一个 iPEPS 的 $2 \times 2$ supercell. 某些强关联系统的基态可能自发地打破平移对称性。在这种情况下，可能需要更大尺寸的超级晶胞。

与MPS类似，可以通过为每个虚拟键引入奇异值矩阵来定义 iPEPS 的 Lambda-Gamma 形式。这些奇异值矩阵编码矩阵两侧之间的纠缠。如 [[#2.2. 矩阵乘积态|2.2]] 节所示，奇异值矩阵可以被视为携带周围区域信息的环境。这是基态搜索的简单更新算法的基础，将在 2.7.1 节中进一步讨论。然而，与MPS不同，2 维 iPEPS 不具有标准形式[^25]（例如左归一化或右归一化张量网络）。因此，需要替代方法来获得准确的结果。


## 2.6. Corner transfer 矩阵

IPEPS 张量网络包括无限数量的张量，这在实际中是不可能处理的。因此，人们必须找到一种方法来用有限数量的张量来表示某个无限子区域。在一维中，奇异值完美地完成了这项工作。尽管如此，由于缺乏定义明确的规范形式，同样的战略在二维失败了。

角点转移矩阵(CTM)方案[^6][^33][^34][^35]是解决这一问题的有效方法。对于每个复合张量 $\mathcal{M}$，CTM 方案使用四个角矩阵 $\mathcal{C}$ 和四个转移矩阵(严格地说，张量) $\mathcal{T}$。这八个张量表示围绕复合张量的无限扩展张量网络。

> **Fig. 2.20** ![[截图-1721130508917.png#R|Fig. 2.20|300]]
> 
> 角转移矩阵方案生成四个角矩阵和四个转移矩阵，它们表示围绕复合张量的无限扩展张量网络。

为了精确地模拟无限大小的环境，通常需要比复合张量的键维度 $D^2$ 大得多的 ***environmental bond（连接角和传递矩阵的键）*** 维度 $\chi$。这用不同粗细的线来表示。此外，由于*每个复合张量都需要一组角点矩阵和转移矩阵*，因此所需张量的总数取决于超原胞的大小。例如，具有 $2 \times 2$ supercell 的 iPEPS 总共需要 16 个角矩阵和 16 个传递矩阵。


CTM 方案通过在所有方向上的一系列粗粒化步骤来产生角矩阵和转移矩阵。如图 2.21 所示，粗粒化移动包括两个步骤：首先，将现有*转移矩阵*与最近的复合张量压缩，得到具有更大 environmental bond 维 $\chi D^2$ 的新转移矩阵；然后执行下文所述的重整化，将环境键维降回 $\chi$. 请注意，生成的转移矩阵*属于不同的站点*，例如图 2.21 中的 $\mathcal{T}^\text{L}_{j,i+1}$ 而不是 $\mathcal{T}^\text{L}_{j,i}$. 迭代这个过程，直到传递矩阵的谱达到收敛。

> **Fig. 2.21** ![[截图-1721130810396.png#R|Fig. 2.21|400]]
> 传递矩阵的重正化
> (a) 初始设置
> (b) 将转移矩阵与最近的复合张量进行收缩以得到新的转移矩阵
> (c) 新的转移矩阵具有更大的环境键维数 $\chi D^2$
> (d) 执行重正化以将环境键维数降低回 $\chi$


*角矩阵*的粗粒化可以以类似的方式执行。如图 2.22 所示，在进行重正化以降低环境键维数之前，将角矩阵与最近的转移矩阵收缩。然而，还有一个额外的复杂性：粗粒化有两个不同的方向。两个方向都需要获得收敛。



> **Fig. 2.22** ![[截图-1721131285246.png#R|Fig. 2.22|400]]
> 角点矩阵的重正化
> (a) 初始设置
> (b) 将角矩阵与最近的转移矩阵进行收缩以得到新的角矩阵
> (c) 新的角矩阵具有更大的环境键维数 $\chi^2$
> (d) 执行重正化以将环境键维数降低回 $\chi$.

在重整化过程之前，首先需要初始化作为起点。原则上，可以使用任何随机张量作为初始化。尽管如此，这通常需要更多的重整化步骤来收敛。图 2.23 展示了一个更好的策略，它利用了张量及其共轭。

> **Fig. 2.23** ![[截图-1721131520709.png#R|Fig. 2.23|300]]
> 角矩阵和转移矩阵可以使用张量及其共轭来初始化。这种策略导致比随机初始化更快的收敛特性。

我们还剩下最后一个要素--CTM 重整化小组方案。在每个粗粒化步骤中，需要一个 RG 来截断不断增加的 enviromental bond 维度。接下来，我们详细阐述了如何实现相对最优和数值稳定的截断。


> **Fig. 2.24** ![[截图-1721131746987.png#R|Fig. 2.24|400]]
> 有效张量网络表示 iPEPS 网络的上半部分。SVD 用于数值稳定性的目的。
> 

首先，我们需要对 iPEPS 张量网络的上(下)半部分进行有效描述，如图 2.24 所示。早期的CTMRG[^6]简单地使用了图 2.24 的左侧，而后来[^35]提出了中间的奇异值分解，通过去除微小的奇异值来提高数值稳定性。然后，将奇异值分解得到的张量 $U$ 和奇异值矩阵 $S'$ 进行压缩，得到张量 $\Sigma^U$。类似地，从下半平面可以得到 $\Sigma^D$.

接下来，构造矩阵 $\Sigma^U\Sigma^D$ 并应用 SVD。通过仅保留最大 $\chi$ 奇异值来实现重整化或截断。在图 2.25 的右边，我们还显示了矩阵 $\Sigma^U\Sigma^D$ 的逆矩阵，这是下面构造 projectors 所需要的

> **Fig. 2.25** ![[截图-1721133946451.png#R|Fig. 2.25|400]]
> 对 $\Sigma^U \Sigma^D$ 应用 SVD，并仅保留最大的 $\chi$ 奇异值进行截断。为下一步准备逆矩阵 ${\Sigma^U}^{-1} {\Sigma^D}^{-1}$.


> **Fig. 2.26** ![[截图-1721134190162.png#R|Fig. 2.26|400]]
> CTMRG scheme 的投影建造。每次都会建造两个不同的投影，处理腿指向相反的方向。

最后一步构建两个投影仪，如图 2.26 所示。我们可以很容易地验证 $P^{\text{LU}}P^{\text{LD}}=\mathbb{1}$。投影 $P^{\text{LU}}_{j,i}$ 作用于 $\mathcal{T}^{\text{L}}_{j+1,i+1}$ 或 $\mathcal{C}^{\text{LU}}_{j+1,i+1}$ 的*向下分支*。投影 $P^{\text{LD}}_{j,i}$ 作用于 $\mathcal{T}^{\text{L}}_{j,i+1}$ 或 $\mathcal{C}^{\text{LU}}_{j,i+1}$ 的向上分支。需要对所有 $i$ 和 $j$ 重复该过程以生成完整的 set of projectors. 在图 2.21 和图 2.22 的红框中，投影与张量收缩以实现重整化[^35][^29].





## 2.7. 寻找基态

在本节中，我们讨论如何在给定的相互作用哈密顿量下搜索由 iPEPS 表示的基态。传统的微扰方法只适用于弱相互作用。在这里，我们采用非微扰的虚时间演化[^26]来处理强相关系统。允许最近邻和次最近邻相互作用项。

虚时间演化方法基于这样一个事实：向 $\beta \to \infty$ 的演化 projects out 所有激发态。具体地说，如果将时间演化门 $e^{-\beta H}$应用于任何随机生成的状态 $\ket{\psi}$，有
$$
e^{-\beta H}\ket{\psi}
= e^{-\beta E_g}\ket{\text{GS}} + e^{-\beta E_1}\ket{1}
+ e^{-\beta E_2} \ket{2} + \cdots
$$
其中, $\ket{\text{GS}}, \ket{1}, \ket{2}$ 分别为基态、第一、第二激发态，$E_g$、$E_1$、$E_2$ 为相应的能量。根据定义，$E_g < E_1 < E_2 < \cdots$. 因此，当 $\beta \to \infty$ 时，所有的激发态与基态相比都获得了一个可忽略的小系数，这使得只有基态位于右侧.

> **Fig. 2.27** ![[截图-1721135224015.png#R|Fig. 2.27|300]]
> 应用最近邻的 Suzuki-Trotter 门对状态进行时间演化。执行 SVD 来分离两个张量。新的张量获得更大的键维，这些键维随后会被截断.

直接应用虚时间演化门在数值上是不可能的，因为它是一个具有不可行的高阶张量。一个常见的策略是利用 Suzuki-Trotter 分解
$$
e^{-\beta H}
= \prod_{(x,y)} e^{-\beta H_{x,y}} + \order{\beta^2}
$$
其中 $H_{x,y}$ 为位点 $x$ 和 $y$ 的局部两地相互作用项。Suzuki-Trotter 分解将高阶虚时间演化门转化为 two-site 的 Trotter 门序列 $e^{-\beta H_{x,y}}$。Trotter门的应用要简单得多。图 2.27 举例说明了最近邻情况。然后进行奇异值分解，得到更新后的张量。注意，更新后的张量获得了更大的键维(在本例中为 $D^3d$)。因此，需要额外的截断方案来避免键维的指数增长。

Suzuki-Trotter 分解具有 $\order{\beta^2}$ 的系统误差(命名为 Trotter 误差)。因此，为了达到高精度，通常需要使用小的时间步长 $\beta$，并应用 gate 多次迭代以到达时间边界。



### 2.7.1. 简单更新
简单更新[^36]是一种数值经济但相对不准确的更新方案。如 [[#2.2. 矩阵乘积态|2.2]] 节所述，奇异值可视为 iPEPS 的某个有限区域的环境。这是简单更新的核心思想。

> **Fig. 2.28** ![[截图-1721137406638.png#R|Fig. 2.28|400]]
> 最近邻简单更新
> (a) Trotter gate $g$ 在水平键上的应用
> (b) SVD 给出一个更新的奇异值矩阵和两个张量。(c)(d) unmount environmental 奇异值矩阵。
> (e)垂直键合的简单更新。

如图 2.28 所示，将 Trotter gate 应用于某个水平键，周围的奇异值矩阵收缩为环境。然后，通过奇异值分解得到两个张量 $Q_1$ 和 $Q_2$ 以及更新后的奇异值矩阵 $\tilde{\lambda}_{j,i}^{\text{H}}$. 然后，通过收缩 $Q_1$ 和 $Q_2$ 的逆奇异值矩阵来分离环境，以检索更新的张量 $\tilde{\varGamma}_{j,i}$ 和 $\tilde{\varGamma}_{j,i+1}$. 可以用类似的方法对垂直排列的键进行 simple update.

次近邻项[^7]的 simple update 要复杂得多。通常有两种次近邻项——*反对角线项*(连接位点 $(j, i)$ 和位点 $(j+1, i+1)$)和*对角线项*(连接位点 $(j, i+1)$ 和位点 $(j+1, i)$)。由于没有直接连接次近邻位点的键，因此必须通过第三个辅助位点。对于每种类型的次近邻项，有两种可能的辅助站点选择。因此，对于次近邻简单更新，总共有四个图。

> **Fig. 2.29** ![[截图-1721140070927.png#R|Fig. 2.29|350]]
> 连接站点 $(j, i+1)$ 和站点 $(j +1, i)$ (反对角项)的次近邻项的简单更新图。必须通过第三个站点，并且通过不同辅助站点的两个图用于对称更新。


图 2.29 为更新*反对角键*的两张图。应用 Trotter 门后，进行两次 SVD 将大张量分离为三个张量和两个奇异值矩阵[^7]。请注意，当两个图都包含在一个更新步骤中时，Trotter 门必须是 square-rooted，即 $g = \exp(-\beta H/2)$.

> **Fig. 2.30** ![[截图-1721140070927.png#R|Fig. 2.30|350]]
> 连接站点 $(j, i)$ 和站点 $(j +1, i+1)$ (对角线项)的次近邻项的简单更新图。必须通过第三个站点，并且通过不同辅助站点的两个图用于对称更新。

图 2.30 显示了更新对角键的两张图，这与反对角键的情况完全相似。在每个次近邻简单更新步骤中计算两个图的事实大大增加了数字成本。此外，在次近邻情况下，使用奇异值作为环境也不是最优的，与最近邻更新相比，它产生的结果略微不准确。

### 2.7.2. 完全更新
与简单更新方案相比，(快速)全更新方案[^10]以CTMRG生成的拐角矩阵和转移矩阵为环境，因此更精确，但在数值上更昂贵。这里只考虑最近邻完全更新。

完全更新的目标是在应用 Trotter 门之后找到从 $\tilde{M}$ 到 $M$ 的最佳截断。这是通过找到 $M$ 来最小化 $\norm{\ket{\tilde{M}}-\ket{M}}$，其中 $\ket{\tilde{M}}, \ket{M}$ 是截断之前和之后的状态。然而，直接在张量 $M$ 上操作是不方便的。一种更实用的方法是使用 SVD 将 $M$ 分离为 isometry 的 $m^\text{L}$（或 $m^\text{R}$）和包含 physical legs 和待更新键的 rank-3 的张量 $n^\text{L}$ 和 $n^\text{R}$，如图 2.31 所示。

在分离之后，我们可以构造秩为3的张量的环境，如图2.32所示。注意，张量wL和wR分别是等距线mL和mR的共轭，它们受类似于图2.16的腿的扭曲。

根据nL和nR，最优截断变成成本函数的最小化（其中，n和n表示截断前后的张量）

## 2.8. 可观测值的测量

在得到基态以及相应的角点矩阵和转移矩阵后，就可以实现对可观测量的测量。图2.35和图2.36说明了最近邻和次最近邻两个站点观测值的测量

> **Fig. 2.35** ![[截图-1721203197047.png#R|Fig. 2.35|400]]
> 最近邻水平 two-site 观测量的测量。关于垂直对齐的的两个 sites 可观测量可以以类似的方式测量。




# 3. 模拟结果
本文研究的量子点阵模型包括海森堡模型、自由费米子模型和哈伯德模型，它们都具有最近邻和次近邻相互作用。本章给出了仿真结果。第3.1节讨论了寻找基态和计算可观测值的一般策略。3.2节给出了最近邻和次近邻海森堡模型的仿真结果。它们通过将我们的结果与已发表的结果进行比较，作为iPEPS程序的完整性检查。3.3节给出了一个精确可解的自由费米子模型的仿真，验证了费米子iPEPS方法的实现。第3.4节给出了最近邻和次近邻哈伯德模型的模拟。最近邻哈伯德模型被用来证实有刺费米子的实现。最近邻居Hubbard模型的新发现为1/8空穴掺杂附近基态的自旋和电荷序提供了新的线索。分析表明，SU(2)对称均匀态比U(1)对称条纹态能量更低。

## 3.1. 一般策略
本节描述用于计算所有模型的初始设置和参数选择的技术细节。除非特别指出，否则本章中的参数设置遵循本节的描述。

**初始化**。所有的计算都从随机初始化开始。在对称张量网络中，初始张量有几个不同的量子数组合通常是有益的。一个有用的做法是首先构造一个等距，然后为每个数据条目分配一个范围为 $\qty[0,1]$ 的随机数。

简单更新。Trotter误差为O(τ2)阶。因此，高精度需要小的(虚的)时间步长。然而，如果从一个很小的时间步长开始，可能需要大量的迭代才能达到收敛。一个有用的策略是从一个较大的时间步长开始，并随着迭代的进行逐渐减少它。具体地说，首先使用一个固定的、大的初始时间步长，因为随机初始状态通常离基态相当远。在实践中，发现τ = 0.1是一个非常好的选择，作为所有模型的初始时间步长。这个初始时间步长通常在几十次迭代中保持固定，直到平均光谱变化∆¯Λ降至阈值以下，例如10−4。然后，根据∆¯Λ的值改变时间步长。一个有用的策略是，当∆¯Λ降至Kτ2以下(其中K是某个常数)时，将时间步长减少一半，因为Trotter误差为τ2阶。根据经验，K = 1在大多数情况下是一个不错的选择。在特殊情况下，当单元胞的尺寸较大时，可能需要较小的k值。当τ降至例如10−5的阈值以下时，简单更新停止。

## 3.2. 海森堡模型

海森堡模型是研究最广泛的量子晶格模型之一。其中，最近邻海森堡模型得到了精确的量子蒙特卡罗模拟，结果可以用来验证我们的算法。

在本节中，我们关注自旋-1/2海森堡模型。3.2.1 节通过与蒙特卡罗模拟的比较，给出了几种基于最近邻海森堡模型的 iPEPS 算法的基准。第3.2.2节考察了下近邻海森堡模型在下近邻相互作用和磁挫折作用下的典型相位，并验证了简单更新检测不同相位的能力。

### 3.2.1. 最近邻海森堡模型

最近邻海森堡模型是只有最近邻相互作用项的最简单海森堡模型。本节使用的哈密顿量是


为简单起见，我们在式(1.1)中设置J = 1。图3.1给出了计算得到的基态能量与参考值Eg =−0.669437[^38][^39]的偏差。

从图中可以看出，U(1)自旋对称的简单更新产生了10−3阶的相对误差，而完全更新提供了10−4阶的更好精度。然而，由于完全更新消耗更多的计算资源，而它只会导致精度的微小提高，因此这将是本文中唯一的完全更新模拟。

同时，SU(2)自旋对称的模拟得到的基态能量要高于仅U(1)自旋对称的模拟得到的基态能量，如图3.1所示。因此，结果支持SU(2)对称破缺在最邻近的Heisenberg模型的基态，这与已知其基态为nsamel反铁磁体的事实相一致。

### 3.2.2. 次最近邻海森堡模型
次近邻海森堡模型(也称为 $J_1-J_2$ 海森堡模型)引入了次近邻相互作用。这里用的汉密尔顿函数是

# 4. 结论

在本文中，我们采用对称 iPEPS 方法模拟了几种具有最近邻和次近邻相互作用的二维量子晶格模型。PEPS 张量网络使用了一个 rank-5 张量网络，其中一个物理指标表示局部状态，四个连接相邻张量的指标 encodes 纠缠。无限 PEPS 利用平移不变性，能够使用有限数量张量的 supercell 来处理无限大小的系统。CTMRG 方案使用有限数量的角矩阵和转移矩阵编码无限扩展的环境。费米子统计量是通过考虑 parity preserving 张量和在线交叉处添加交换门来获得的。使用 QSpace 张量库自动跟踪张量的对称性。基态可以通过基于虚时间演化的算法和截断方案 (如简单更新和完全更新) 来抵消键维的指数增长。在计算了基态和相应的角矩阵和转移矩阵后，可以测量可观测值。




[^1]: M. Imada, A. Fujimori, and Y. Tokura, Metal-insulator transitions, Rev. Mod. Phys., 70, 1039 (1998).
[^2]: P. W. Anderson, The Theory of Superconductivity in the High-Tc Cuprate Superconductors, Princeton University Press (1997).
[^3]: E. Dagotto, Correlated electrons in high-temperature superconductors, Rev. Mod. Phys., 66, 763 (1994).
[^4]: A. P. Ramirez, Strongly Geometrically Frustrated Magnets, Annu. Rev. Mater. Sci., 24, 453 (1994).
[^5]: H. L. Stormer, Nobel Lecture: The fractional quantum Hall effect, Rev. Mod. Phys., 71, 875 (1999).
[^6]: P. Corboz, R. Orús, B. Bauer, and G. Vidal, Simulation of strongly correlated fermions in two spatial dimensions with fermionic projected entangled-pair states, Phys. Rev. B, 81, 165104 (2010).[[通过费米 PEPS 模拟二维强关联费米子]]
[^7]: P. Corboz, J. Jordan, and G. Vidal, Simulation of fermionic lattice models in two dimensions with projected entangled-pair states: Next-nearest neighbor Hamiltonians, Phys. Rev. B, 82, 245119 (2010).
[^8]: B. Ponsioen, S. S. Chung, and P. Corboz, Period 4 stripe in the extended two-dimensional Hubbard model, Phys. Rev. B, 100, 195141 (2019).
[^9]: F. Verstraete and J. I. Cirac, Renormalization algorithms for Quantum-Many Body Systems in two and higher dimensions (2004), arXiv:cond-mat/0407066.
[^10]: J. Jordan, R. Orús, G. Vidal, F. Verstraete, and J. I. Cirac, Classical Simulation of Infinite-Size Quantum Lattice Systems in Two Spatial Dimensions, Phys. Rev. Lett., 101, 250602 (2008).[[二维空间无限大量子点阵系统的经典模拟]]
[^11]: W. Heisenberg, Zur theorie des ferromagnetismus, Z. Phys., 49, 619 (1928).
[^12]: J. Hubbard, Electron correlations in narrow energy bands V. A perturbation expansion about the atomic limit, Proc. R. Soc. London A, 296, 82 (1967).
[^13]: D. J. Scalapino, The 2D Hubbard Model and the High Tc Cuprate Problem, J. Supercond. Nov. Magn., 19, 195 (2006).
[^14]: A. Weiße and H. Fehske, Exact Diagonalization Techniques, Computational Many-Particle Physics, Springer Berlin Heidelberg, 529–544 (2008).
[^15]: G. Sugiyama and S. Koonin, Auxiliary field Monte-Carlo for quantum many-body ground states, Ann. Phys., 168, 1 (1986).
[^16]: E. Gull, A. J. Millis, A. I. Lichtenstein, A.N. Rubtsov, M.Troyer, and P.Werner, Continuous-time Monte Carlo methods for quantum impurity models, Rev. Mod. Phys., 83, 349 (2011).
[^17]: W. M. C. Foulkes, L. Mitas, R. J. Needs, and G. Rajagopal, Quantum Monte Carlo simulations ofsolids, Rev. Mod. Phys., 73, 33 (2001).
[^18]: M. Troyer and U.-J. Wiese, Computational Complexity and Fundamental Limitations to Fermionic Quantum Monte Carlo Simulations, Phys. Rev. Lett., 94, 170201 (2005).
[^19]: K. G. Wilson, The renormalization group: Critical phenomena and the Kondo problem, Rev. Mod. Phys., 47, 773 (1975).
[^20]: R. Bulla,T. A. Costi, andT. Pruschke, Numerical renormalization group method for quantum impurity systems, Rev. Mod. Phys., 80, 395 (2008).
[^21]: A. Weichselbaum, Tensor networks and the numerical renormalization group, Phys. Rev. B, 86, 245124 (2012).
[^22]: S. R. White, Density matrix formulation for quantum renormalization groups, Phys. Rev. Lett., 69, 2863 (1992).
[^23]: U. Schollwöck, The density-matrix renormalization group in the age of matrix product states, Ann. Phys., 326, 96 (2011).
[^24]: F. Verstraete, V. Murg, and J. Cirac, Matrix product states, projected entangled pair states, and variational renormalization group methods for quantum spin systems, Adv. Phys., 57, 143 (2008).
[^25]: B. Bruognolo, Tensor network techniques forstrongly correlated systems, Ph.D. thesis, Ludwig-Maximilian-Universität München (2017).
[^26]: G. Vidal, Classical Simulation ofInfinite-Size Quantum Lattice Systems in One Spatial Dimension, Phys. Rev. Lett., 98, 070201 (2007).
[^27]: G. Vidal, Efficient Classical Simulation of Slightly Entangled Quantum Computations, Phys. Rev. Lett., 91, 147902 (2003).
[^28]: J. Eisert, Entanglement and tensor network states, Model. Simul., 3 (2013), arXiv:1308.3318.
[^29]: B. Bruognolo, J.-W. Li, J. v. Delft, and A.Weichselbaum, A beginner’s guide to non-abelian iPEPS for correlated fermions, arXiv (2020), arXiv:2006.08289.
[^30]: A. Weichselbaum, Non-abelian symmetries in tensor networks: A quantum symmetry space approach, Ann. Phys., 327, 2972 (2012).
[^31]: M. Lubasch, J. I. Cirac, and M.-C. Bañuls, Algorithms for finite projected entangled pair states, Phys. Rev. B, 90, 064425 (2014).
[^32]: E. Stoudenmire and S. R. White, Studying Two-Dimensional Systems with the Density Matrix Renormalization Group, Annu. Rev. Condens. Matter Phys., 3, 111 (2012).
[^33]: T. Nishino and K. Okunishi, Corner Transfer Matrix Renormalization Group Method, J. Phys. Soc. Japan, 65, 891 (1996).
[^34]: R. Orús and G. Vidal, Simulation oftwo-dimensional quantum systems on an infinite lattice revisited: Corner transfer matrix for tensor contraction, Phys. Rev. B, 80, 094403 (2009).
[^35]: P. Corboz, T. M. Rice, and M. Troyer, Competing States in the t-J Model: Uniform d-Wave State versus Stripe State, Phys. Rev. Lett., 113, 046402 (2014).
[^36]: H. C. Jiang, Z. Y. Weng, and T. Xiang, Accurate Determination of Tensor Network State of Quantum Lattice Models in Two Dimensions, Phys. Rev. Lett., 101, 090603 (2008).
[^37]: H.N. Phien, J. A. Bengua, H. D. Tuan, P. Corboz, and R. Orús, Infinite projected entangled pair states algorithm improved: Fast full update and gauge fixing, Phys. Rev. B, 92, 035142 (2015).
[^38]: A. W. Sandvik, Finite-size scaling of the ground-state parameters of the two-dimensional Heisenberg model, Phys. Rev. B, 56, 11678 (1997).
[^39]: C. Hubig, Abelian and non-abelian symmetries in infinite projected entangled pair states, SciPost Physics, 5, 047 (2018).
[^40]: R. Haghshenas and D. N. Sheng, U(1)-symmetric infinite projected entangled-pair states study ofthe spin-1/2 square J1-J2 Heisenberg model, Phys. Rev. B, 97, 174408 (2018).
[^41]: W.-Y. Liu, S.-S. Gong, Y.-B. Li, D. Poilblanc, W.-Q. Chen, and Z.-C. Gu, Gapless quantum spin liquid and global phase diagram of the spin-1/2 J1-J2 square antiferromagnetic Heisenberg model, arXiv (2020).
[^42]: W. Li, L. Ding, R. Yu, T. Roscilde, and S. Haas, Scaling behavior of entanglement in two- and three-dimensional free-fermion systems, Phys. Rev. B, 74, 073103 (2006).
[^43]: H.-C. Jiang andT. P. Devereaux, Superconductivity in the doped Hubbard model and its interplay with next-nearest hopping t’, Science, 365, 1424 (2019).
[^44]: J. P. F. LeBlanc, A. E. Antipov, F. Becca, I. W. Bulik, G. K.-L. Chan, C.-M. Chung, Y. Deng, M. Ferrero, T. M. Henderson, C. A. Jiménez-Hoyos, E. Kozik, X.-W. Liu, A. J. Millis, N. V. Prokof’ev, M. Qin, G. E. Scuseria, H. Shi, B. Svistunov, L. F. Tocchio, I. S. Tupitsyn, S. R. White, S. Zhang,B.-X. Zheng, Z. Zhu, and E. Gull, Solutions of the Two-Dimensional Hubbard Model: Benchmarks and Results from a Wide Range ofNumerical Algorithms, Phys. Rev. X, 5, 041041 (2015).
[^45]: P. Corboz, Improved energy extrapolation with infinite projected entangled-pair states applied to the two-dimensional Hubbard model, Phys. Rev. B, 93, 045116 (2016).
[^46]: B.-X. Zheng, C.-M. Chung, P. Corboz, G. Ehlers, M.-P. Qin, R. M. Noack, H. Shi, S. R. White, S. Zhang, and G. K.-L. Chan, Stripe order in the under doped region of the two-dimensional Hubbard model, Science, 358, 1155 (2017).
[^47]: J. M. Tranquada, B. J. Sternlieb, J. D. Axe, Y. Nakamura, and S. Uchida, Evidence for stripe correlations of spins and holes in copper oxide superconductors, Nature, 375, 561 (1995).
[^48]: A. Mesaros, K. Fujita, S. D. Edkins, M. H. Hamidian, H. Eisaki, S.-i. Uchida, J. C. S. Davis, M. J. Lawler, and E.-A. Kim, Commensurate 4a0-period charge density modulations throughout the Bi2Sr2CaCu2O8+x pseudo gap regime, Proc. Natl. Acad. Sci., 113, 12661 (2016).
[^49]: J. M. Tranquada, J. D. Axe, N. Ichikawa, A. R. Moodenbaugh, Y. Nakamura, and S. Uchida, Coexistence of, and Competition between, Superconductivity and Charge-Stripe Order in La1.6−xNd0.4SrxCuO4, Phys. Rev. Lett., 78, 338 (1996).
[^50]: P. Corboz, S. R. White, G. Vidal, and M. Troyer, Stripes in the two-dimensional t-J model with infinite projected entangled-pair states, Phys. Rev. B, 84, 041108 (2011).
[^51]: J.-W. Li, B. Bruognolo, A. Weichselbaum, and J. von Delft, Study of spin symmetry in the doped t-J model using infinite projected entangled pair states, Phys. Rev. B, 103, 075127 (2021).
[^52]: N. J. Robinson, P. D. Johnson, T. M. Rice, and A. M. Tsvelik, Anomalies in the pseudogap phase of the cuprates: competing ground states and the role of umklapp scattering, Rep. Prog. Phys., 82, 126501 (2019).
