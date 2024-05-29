---
tags:
  - 论文
  - Kitaev磁体
  - 马约拉纳费米子
created: 2023-07-25 23:18:59
aliases:
  - Hunting Majorana Fermions in Kitaev Magnets
原标题: Hunting Majorana Fermions in Kitaev Magnets
author:
  - "[[求 幸年]]"
  - "[[那須 讓治]]"
DOI: https://doi.org/10.7566/JPSJ.89.012002
year: "2020"
---

# 0. 摘要

[[Majorana 费米子|马约拉纳费米子]]是一种[[费米子|费米子]]，它的反粒子是它本身。自1937年[[Ettore Majorana|埃托雷·马约拉纳]]的理论发现以来，粒子物理学一直在研究这种奇异粒子。然而，在过去的几十年里，它重新引起了人们对凝聚态物理学的兴趣。在凝聚态物理学中，它可以作为物质的量子态(如[[分数量子霍尔效应|分数量子霍尔]]态和拓扑超导体)中的基本激发([[准粒子|准粒子]])。在这篇综述中，我们讨论了[[Majorana 费米子|马约拉纳费米子]]的另一个平台——[[量子自旋液体]]。量子自旋液体是1973年[[Philip W. Anderson|Philip Anderson]]首次提出的绝缘磁体的一种奇异量子相，在强量子涨落下，相互作用磁矩保持无序直至最低温度.

它们的特点是*拓扑纠缠*和*分数激发*，其在拓扑量子计算中的应用近来得到了广泛的讨论。作为这种奇异状态的主要候选者，我们在这里关注的是 *Kitaev 磁铁*，它是*自旋轨道 Mott 绝缘体*的一个子群，是 2006 年 [[Alexei Kitaev]] 和2009年 [[G. Jackeli]] 和 [[G. Khaliullin]] 的开创性研究的一个主题。在简要概述了Kitaev模型和自旋在精确基态下的*分数化*之后，我们回顾了这个快速发展的领域最近的爆炸性发展，重点是有限温度下 Kitaev 模型的数值解以及与实验的比较。

关键的概念是热分数化(*thermal fractionalization*)——两种类型的分数激发在很大程度上不同的温度下表现出来。这导致了各种实验可测量的量拥有不同的热力学和自旋动力学。

我们讨论了分数化准粒子的特征，并与 Kitaev 磁体候选材料的实验数据进行了比较。本文综述了 Kitaev 磁体中马约拉那费米子的识别现状，为进一步的拓扑量子计算中操纵奇异粒子的实验和理论研究奠定了基础。


# X. 笔记

# 1. 引言

## 1.1. 马约拉纳费米子

马约拉纳费米子是电荷中性的, 自旋为 $1/2$ 的粒子，是它们自己的反粒子。它们在理论上是由[[Ettore Majorana|埃托雷·马约拉纳]]于1937年在[[狄拉克方程|狄拉克方程]]的一个实数解中发现的[^1]. [[Majorana 费米子|马约拉纳费米子]]区别于复数解中的普通费米子，即[[费米子|狄拉克费米子]]。

[[费米子|狄拉克费米子]]不是它们自己的反粒子，可以分别用[[生成与消灭算符|生灭算符]] $f, f^\dagger$ 来描述。
马约拉纳算符可以被定义为
$$
\gamma_1 = \frac{f - f^\dagger}{\mi}, \quad \gamma_2 = f + f^\dagger\tag{1}
$$
可见它的生成和消灭是等价的
$$\gamma_i^\dagger = \gamma_i\tag{2}$$
满足*反对易关系*
$$
\acomm{\gamma_i}{\gamma_j} = 2 \delta_{ij}\tag{3}
$$

```ad-note
由 (1) 可知
$$
f^\dagger = \frac{\gamma_2 - \mi \gamma_1}{2}
, \quad f = \frac{\gamma_2 + \mi \gamma_1}{2}
$$
狄拉克费米子的*占据态*和*未占据态*可以用一对马约拉纳费米子来描述。这意味着一个马约拉纳费米子具有一个狄拉克费米子的半自由度。
```

自从埃托雷·马约拉纳提出这个有趣的建议以来，粒子物理学一直在寻找奇异粒子的物理例子。在标准模型中，除了中微子外，所有的费米子都是狄拉克费米子。因此，中微子长期以来一直被当作马约拉纳费米子的主要候选粒子来研究，但它的性质尚未确定[^2][^3][^4]。在超对称模型中，已经讨论了另一个候选 superpartners，但迄今为止还没有建立证据。

在过去的几十年里，马约拉纳费米子因其在凝聚态物理学中的可能应用[[马约拉纳归来|]][^5]而重新引起了人们的兴趣. 在这种情况下，它们不是作为基本粒子出现，而是作为物质的量子态中的*基本激发*(准粒子)出现。

一般来说，在电子关联下的量子多体态中可以存在与组成电子性质不同的演生准粒子。在某些情况下，元激发是由*一种以上*的准粒子来描述的，这些准粒子看起来像是电子被*分数化*成几个粒子。这就是所谓的*分数化*。

```ad-example
例如，在二维[[量子霍尔效应|分数量子霍尔态]]中，基本的电荷 $-e$ 被分数化成分数电荷，例如，$e/3$，因此，系统的基本激发被称为不服从狄拉克-费米或玻色-爱因斯坦统计的任何一个出现的准粒子所描述。
```
例如，在二维[[量子霍尔效应|分数量子霍尔态]]中，基本的电荷 $-e$ 被分数化成分数电荷，例如，$e/3$，因此，系统的基本激发被称为不服从[[费米-狄拉克统计|狄拉克-费米]]或[[玻色-爱因斯坦统计|玻色-爱因斯坦统计]]的[[任意子|任意子]]所描述。

在分数化的背景下，马约拉纳费米子的演生, 已经在几个不同的量子态中讨论过了，例如
1. $\nu = 5/2$ 分数量子霍尔态的*边界模*[^6][^7][^8][^9][^10]
2. $p$ 波超导体中的零模[^8][^11]
3. 拓扑超导体中的束缚态[^12][^13][^14][^15]

由于这些马约拉纳费米子起源于*基本粒子*的*分数化*，它们具有*拓扑纠缠*和本质上的*非局域性*。由于其不寻常的性质，演生马约拉纳费米子在拓扑量子计算中的应用引起了广泛的关注[[通过任意子的可容错量子计算_Kitaev]][^16][^17].

在这篇综述中，我们重点介绍了马约拉纳费米子在绝缘磁体中被称为 [[Mott 绝缘体]] 的另一种实现。在这些系统中，由于强电子关联，电子在空间上是局域化的，因此，自由电荷度是不活跃的。相反，这里可以分数化的是自旋自由度。[[量子自旋液体|量子自旋液体]] (QSL) 是 Mott 绝缘体中的一种量子无序态，这种自旋分分化的可能性已经在QSL中被讨论过。局域自旋仍然是无序的，但是量子纠缠。根据系统的对称性预测了几种类型的QSLs，它们有自己的分数准粒子。例如，在所谓的 $Z_2$ QSLs中，自旋激发应该分数化成两种元激发:自旋子和粘子;自旋子是电荷中性自旋 $1/2$ 的粒子状激发，而粘子是拓扑激发，由它们的弦状轨迹定义。

然而，大多数这样的论点都缺乏严格的依据，因为在不止一个维度上存在较少定义良好的 QSL. 到目前为止，对于二维和三维的几何阻挫反铁磁体已经做出了巨大的努力，但很少有例子严格地证明基态是 QSL.[^23][^24][^25][^26] 

主要的困难在于缺乏合适的理论方法: 任何近似理论都可能忽略量子态纠缠的本质，而数值方法需要极高的精确度才能从强阻挫的准简并态中选择出真正的基态。因此，在 QSLs 中识别分数自旋激发仍然是一个很大的挑战。

这种情况在过去十年中通过两个突破而发生了戏剧性的变化。一个是阿列克谢·基塔耶夫在2006年的开创性论文中提出的精确可解模型[^27]，该模型现在被称为基塔耶夫模型。该模型是一个自旋 $1/2$ 的模型，定义在具有键依赖相互作用的二维蜂窝结构上。基态恰好是一个QSL，其中自旋激发分数化成两种类型的准粒子激发: 巡回的类自旋子激发，由马约拉纳费米子描述; 局域的类 vison 激发。

另一个突破是 [[G. Jackeli|Jackeli]] 和 [[G. Khaliullin|Khaliullin]] 在2009. [^28][^29] 他们指出 Kitaev 模型可以在一类具有强自旋-轨道耦合的 Mott 绝缘磁体中实现。在他们的论证的刺激下，有几种材料被提名为 Kitaev QSL 的候选材料，如氧化铱 $\text{A}_2\text{IrO}_3$ (A = Li and Na) 和三氯化钌 α-RuCl3。这两个突破从理论和实验两方面推动了对基塔耶夫QSL的深入研究。

在本文中，我们概述了这一快速增长领域的最新进展。在这里，我们特别关注有限温度 ($T$) 方面的分数激发，这是相关的，以确定他们在候选材料。

由于Kitaev模型的精确解仅限于*基态*，作者和他们的合作者开发了几种数值技术来研究其有限-$T$ 性质，并计算了实验观测值，如比热和熵、静态自旋-自旋相关[^38]、磁化率、非弹性中子散射谱, 核磁共振(NMR)中的自旋晶格弛豫速率[^39][^40][^41], 拉曼散射谱[^43]和热导率的纵向和横向分量。44)通过理论结果与实验数据的详细比较，对于Kitaev候选材料，已经积累了分数激发的特征。我们将在本文中详细讨论这种比较。

## 1.2. 文章结构

本文的结构如下: 在第2节中，我们介绍了Kitaev模型和从QSL基态精确解导出的分数阶激发。在第 2.1 节中引入哈密顿量后，我们简要讨论了第2.2节中Kitaev模型中特殊键依赖相互作用的起源。在2.3节中，我们描述了自旋算符的一种马略阿纳表示，它不同于Kitaev引入的原始表示，但对于有限-$T$ 计算的数值技术开发很有用。在概述了精确的QSL基态和2.4节和2.5节的分式激发之后，我们分别讨论了2.6节、2.7节和2.8节中有限T、外加磁场和其他交换相互作用的影响。这些对基塔耶夫QSL的附加效应在2.9节的势相图中概述。

在第三节中，我们讨论 Kitaev 模型热力学中一个独特的方面，我们称之为热分数化。在 3.1 节中，作为原型行为，讨论了二维蜂窝结构上Kitaev模型的两个连续交叉。然后，在3.2节中概述了二维三角形蜂窝结构具有时间反演对称性破缺的特殊相变。在第3.3节中，我们展示了在Kitaev模型的三维(3D)扩展中发现的几个非常规相变，它们可以根据自旋自由度被视为气-液-固相变。我们还简要讨论了三维情况下时间反演对称性的自发破缺。这些交叉和相变在第3.4节中进行了总结。

在第四节，我们介绍几个候选材料为基塔耶夫QSL。我们在4.1节中讨论了准二维氧化铱的基本方面，在4.2节中讨论了三氯化钌，在4.3节中讨论了三维氧化铱。在第5节中，我们比较了Kitaev模型的理论结果和候选材料的实验数据，重点是准二维材料。我们讨论了5.1节中比热和熵的两个连续交叉，5.2节中从光学探针测量到的静态自旋相关的饱和，以及5.3节中磁化率特有的T依赖性。然后，我们转向自旋动力学中分数激发的特征:在5.4节测量到的非弹性中子散射中的动态自旋结构因子和5.5节测量到的核磁共振弛豫率。通过比较，我们讨论了作为热分馏特征的静态和动态自旋关联的二分法。讨论了费米子激发的更直接特征，如第5.6节中的导热系数和第5.7节中的拉曼散射;在后者中，不寻常的费米性质在很宽的t范围内被清楚地识别出来。最后，在第5.8节中，讨论了热霍尔电导率的马约拉纳性质和拓扑状态的直接证据。第6节专门讨论摘要和观点。在附录中，我们描述了基于马约拉纳的数值技术的细节。
# 2. Kitaev 模型和 Majorana Fermions 模型

## 2.1. 哈密顿量

Kitaev 模型是一个具有局域自旋 $S=1/2$ 磁矩的量子自旋模型，具有键依赖的各向异性相互作用。而它可以扩展到任何空间维度的任何三坐标结构(一些例子将在第3节中展示)。在这篇综述中，我们主要关注蜂窝情况。交换相互作用均为伊辛型，但自旋分量取决于三坐标结构上的三种最近邻键。哈密顿量由

$$H=-\sum_{\mu =x,y,z} J_\mu \sum_{\ev{i,j}_\mu} S_i^\mu S_j^\mu\tag{4}$$
其中 $J_\mu$ 为键上的交换耦合常数，$S_i$ 为 $i$ 处自旋 $1/2$ 算符的分量; $h_i$ 的总和; 用 $j_i$ 表示 $μ$ 键上的 NN 自旋对。模型示意图如图 1 所示。![[截图-1690308410242.png#C|图 1|300]]

*由于不可能同时优化所有的键能，键依赖的各向异性相互作用导致了严重的阻挫，尽管在晶格结构中没有几何挫折*。

*经典版本*的 Kitaev 模型中，自旋被看作是经典向量，有无数的能量简并基态[^45].

然而在*量子情况*下，这种宏观经典简并被解除，QSL基态被实现，如章节[[#2.3. 马约拉纳表述|2.3.]]和[[#2.4 量子自旋液态基态|2.4.]]所述。

## 2.2 bond-dependent 各向异性相互作用的起源

式 (4) 中特殊形式的相互作用通常被称为 Kitaev 耦合，可以在一类具有*强自旋轨道耦合*(SOC)的*莫特绝缘体*中实现。这个有趣的可能性是由 [[G. Jackeli|Jackeli]] 和 [[G. Khaliullin|Khaliullin]][^29], 在 [[G. Khaliullin|Khaliullin]] 的开创性工作[^28]之后从理论上提出的。他们指出了 Kitaev 耦合的两个必要条件:
1. 自旋-轨道纠缠产生的局域磁矩，每个局域磁矩都携带一个有效角动量 $j_{\text{eff}}=1/2$
2. 局域电子通过配体间接跳跃交换过程之间的量子干涉

## 2.3. 马约拉纳表述

Kitaev 证明了 (4) 中模型的基态是通过引入自旋算符的马约拉纳表示来精确得到的[[精确可解模型及其他中的任意子_Kitaev]][^27]。在精确解中，每个自旋 $1/2$ 的算符由四个马约拉纳费米子算符表示。后来，又引入了另一种马约拉纳表示，给出了同样的解[^57][^58][[六边形晶格上 Kitaev 模型的精确结果：自旋态、弦和膜关联，以及任意子激发|]][^59].

在这种情况下，自旋 $1/2$ 的算符由*两个*马约拉纳费米子表示。在本文中，我们将简要回顾后一种 Majorana 表示，因为它在后面部分的数值模拟中使用。

后者的优势在于希尔伯特空间的大小。前者 Kitaev 的表示将希尔伯特空间加倍，并需要将其投影到原始子空间中以获得物理结果。在数值方法中处理投影并不直观[^60]. 另一方面，在后者的表示中，不需要进行这样的投影，因为希尔伯特空间的大小保持不变。


### Jordan-Wigner 变换

在 Majorana 表示法中，我们首先对式 (4) 中的模型应用 [[Jordan-Wigner 变换|Jordan-Wigner 变换]]，将系统视为由 $x$ 键和 $y$ 键组成的一维链, 见图 3.![[截图-1690349098743.png#C|图 3|400]]
```ad-info
title: 图 3
图示是由 $x$ 键和 $y$ 键组成的一维链的示意图，分别用粗蓝线和绿线表示。图 1 中的蜂窝结构变形为砖墙结构。虚线方框表示包括第 $r$ 个 $z$ 键的单位单元；

两个格点分别表示为 $r, b$ 和 $r, w$ (见方程(10)和(13)).在方程(8)中的 Jordan-Wigner 变换中，格点从左下角开始编号，如图中部分所示。
```

在 [[Jordan-Wigner 变换|Jordan-Wigner 变换]] 中，自旋算符被*无自旋*费米子算符重写为
$$
\begin{align}
S_i^+ &=(S_i^-)^\dagger
= S_i^x + \mi S_i^y
=\prod_{i'=1}^{i-1} (1-2n_{i'}) a_i^\dagger\\
S_i^z &= n_i - \frac12\tag{8}
\end{align}
$$
其中 $a_i^\dagger$ 和 $a_i$ 分别是无旋费米子的生灭算符，$n_i = a_i^\dagger a_i$ 是粒子数算符;
$a_i^\dagger$ 和 $a_i$ 满足反对易关系
$$
\acomm*{a_i^\dagger}{a_j}=\delta_{ij}, \quad \acomm*{a_i^\dagger}{a_j^\dagger}=\acomm{a_i}{a_j}=0\tag{9}
$$

考虑蜂窝结构是 bipartite 的，将式 (4) 中的哈密顿量转化为
$$\begin{aligned}
\mathcal{H}= & \frac{J_x}{4} \sum_{\left\langle r^{\prime}, w ; r, b\right\rangle_x}\left(a_{r^{\prime}, w}-a_{r^{\prime}, w}^{\dagger}\right)\left(a_{r, b}+a_{r, b}^{\dagger}\right) \\
& -\frac{J_y}{4} \sum_{\left\langle r, b ; r^{\prime}, w\right\rangle_y}\left(a_{r, b}+a_{r, b}^{\dagger}\right)\left(a_{r^{\prime}, w}-a_{r^{\prime}, w}^{\dagger}\right) \\
& -\frac{J_z}{4} \sum_r\left(2 n_{r, b}-1\right)\left(2 n_{r, w}-1\right)
\end{aligned}\tag{10}$$

其中下标 $b$ 和 $w$ 用一个 $z$ 键标记第 $r$ 单元细胞中的两个子晶格(见图 1 和图 3 ); 
第一, 第二项的 $r,b$ 以及 $r',w$ 求和范围是 $x, y$ 方向的所有最近邻 bond.

注意，对于周期性边界条件下的系统，所谓的边界项出现在Jordan-Wigner变换中。边界项是非局部的，数值模拟中难以处理。避免这种情况的一种方法是考虑开边界条件下的方程组。另一种方法是忽略边界项; 在热力学极限下，它们的贡献可以忽略不计。

接下来，我们用马约阿纳费米子算子替换无旋量费米子算子。这是由
$$\begin{align}
& \gamma_{r, w}=\frac{a_{r, w}-a_{r, w}^{\dagger}}{i}, \quad \bar{\gamma}_{r, w}=a_{r, w}+a_{r, w}^{\dagger}, \tag{11}\\
& \gamma_{r, b}=a_{r, b}+a_{r, b}^{\dagger}, \quad \bar{\gamma}_{r, b}=\frac{a_{r, b}-a_{r, b}^{\dagger}}{i},\tag{12}
\end{align}$$
其中 $\gamma, \bar{\gamma}$ 为马约拉纳费米子算符. 它们与式 (1) 相同。利用 (11), (12)，将式(10)改写为

$$\begin{align}
\mathcal{H}= & \frac{i J_x}{4} \sum_{\left\langle r^{\prime}, w ; r, b\right\rangle_x} \gamma_{r^{\prime}, w} \gamma_{r, b}-\frac{i J_y}{4} \sum_{\left\langle r, b ; r^{\prime}, w\right\rangle_y} \gamma_{r, b} \gamma_{r^{\prime}, w} \\
& -\frac{i J_z}{4} \sum_r \eta_r \gamma_{r, b} \gamma_{r, w},\tag{13}
\end{align}$$

最后一项中的 $\eta_r$ 被定义在 z bond 上, 定义为
$$
\eta_r = \mi \bar{\gamma}_{r,b} \bar{\gamma}_{r,w}\tag{14}
$$
式 (14) 中的键变量 $\eta_r$ 满足如下关系:
$$
\begin{align}
&\comm{H}{\eta_r} = 0,\quad \eta_r^2 = 1, \quad \forall r\tag{15}\\
&\comm{\eta_r}{\eta_{r'}}=0.\tag{16}
\end{align}
$$
这意味着每个 $\eta_r$ 都是一个运动常数，取 $\pm 1$。因此，$\qty{\eta_r}$ 是 $Z_2$ 守恒量。值得注意的是，它们与 Kitaev 论文中引入的另一个守恒量 $Z_2$ 通量 $W_p$ 有关[^27]。对于蜂窝结构上的每个六边形斑 plaqiette，$W_p$ 被定义为
$$
W_p = \prod_{j \in p} \sigma_j^{\bar{\mu}}\tag{17}
$$
在图 4(a) 中，按顺时针方向取 plaqutte $p$ 上六个 sites 的乘积; $\bar{\mu}$ 是连接到 $j$ 位置, 而不属于 $p$ 的键的指标. $\sigma_j^\mu$ 是泡利矩阵的第 $\mu$ 个分量 ($S_j^\mu = \frac{\hs}{2} \sigma_j^\mu$)。

利用泡利矩阵的代数和上述方程，$W_p$ 也表示为
$$W_p = \prod_{r\in p}\eta_r\tag{18}$$
其中乘积范围为, 属于六边形 plaquette $p$ 的两个 $z$ 键, 见图4(b).
![[截图-1693547027526.png#C|图 4|400]]

## 2.4 量子自旋液态基态


等式（13）中的 Hamiltonian 的 Majorana 表示表明，等式（4）中的原始自旋模型被映射到与漫游 Majorana 费米子 $\qty{\gamma_j}$ 与 $Z_2$ 守恒变量 $\qty{\eta_r}$ 或 $Z_2$ 通量 $\qty{W_p}$ 通过等式（18）耦合的系统中。

这在图 5 中以示意图的形式显示出来。
![[截图-1692925377085.png#C|图 5|600]]


```ad-info
title: 图 5
图(a)展示了方程（4）中的自旋表示的Kitaev模型，而图(b)展示了方程（13）中的马约拉纳表示的Kitaev模型。

图(a)中的箭头代表自旋 $\vb*{S}_i$. 

在图 (b) 中，漫游的马约拉纳费米子 $\gamma_i$ 由粉色球体表示，而取值为 $+1(-1)$ 的局域 $Z_2$ 变量 $\eta_r$ 由白色（蓝色）球体表示。

图(b)中的灰色六边形代表*激发*的通量，其 $W_p$ 值为 $+1$.
```

Hamiltonian 以 $\qty{\gamma_j}$ 的二次型形式存在，换句话说，Majorana 费米子 $\qty{\gamma_j}$ 之间没有量子相互作用；它们只与 $Z_2$ 变量 $\qty{\eta_j}$ 相互作用。这意味着 Hamiltonian 可以按照不同的 $\qty{\eta_j}$ 或 $\qty{W_p}$ 配置分类，以块对角化的形式表示。

具有 $2^N$ 维度的总 Hamiltonian 矩阵被分解为由 $\qty{W_p}$ 配置指定的扇区的直和。 $\qty{W_p}$ 配置的数量是 $2^{N/2}$. 因此，每个扇区的块 Hamiltonian 具有 $2^N/2^{N/2} = 2^{N/2}$ 的维度，并且它由包含 $\qty{W_p}$ 的 hopping 矩阵元素的 Majorana 算符的 $N×N$ 二次型形式表示为 $c$-数。这种分解原则上使人们能够通过比较所有扇区中的能量来找到基态，因为每个扇区中的能量对于非相互作用的费米子问题很容易获得。

对于这个问题，有一个数学证明，叫做[[Lieb 定理|Lieb 定理]]，提供了最低能态的精确解[^61]. 这个定理告诉我们，在具有镜面对称性的系统中，最低能量态对应的是不包括晶格点的平面上的磁通配置。

在当前的蜂窝结构模型中，当三个 $J_\mu$ 中至少有两个相等时，我们可以将这个定理应用于这些对称情况。这些对称情况的确切基态位于所有 $W_p=+1$ 的扇区中，这被称为*无磁通状态*。然而，Lieb 的定理不适用于具有一般 $J_\mu$ 的情况。尽管如此，通过比较不同 $\qty{W_p}$ 配置的能量，可以推断出在整个 $J_\mu$ 参数空间中，无磁通状态是基态[^27]。

无磁通状态是一种量子自旋液体（QSL）。通过计算自旋相关性[^62]，已经明确证明了这一点。自旋相关性仅在最近邻 $μ$ 键上的 $μ$ 分量以及相同的站点上具有非零值，即 ^36d814

$$
\ev{S_i^\mu S_j^\nu} \neq 0\qq{only for} \mu=\nu\qq{and} i,j \in\ev{i,j}_\mu\tag{19}
$$

所有其他自旋相关性都消失了。这是因为自旋算符 $S_i^\mu$ 翻转了包括 site $i$ 的 $μ$ 键两侧的 $W_p$，只有满足等式（19）中条件的 $S_i^\mu$ 和 $S_j^\nu$ 的组合才能保持 $W_p$ 的无磁通配置（见图6）。

![[截图-1693552236728.png#C|图 6|500]]
因此，自旋相关性在无磁通状态下是极短程的。这意味着无磁通基态不会破坏系统的任何对称性，因此，它是在多于一维的条件中, 严格 QSL 的罕见实现。

请注意，等式（19）适用于任意的磁通配置。这表明，除了等式（19）中的自旋相关性之外，在磁通为 $W_p = -1$ 的情况下，即使在有限的温度下，其他自旋相关性也总是为零。这在第2.6节和附录中介绍的数值研究中得到了证实。

## 2.5 分数激发

对于无磁通基态，存在两种类型的激发。一种是通过流动的 Majorana 费米子 $\qty{\gamma_j}$ 引起的激发，另一种是对于 $Z_2$ 磁通 $\qty{W_p}$ 引起的激发。这些是由自旋自由度的分数化引起的准粒子激发。

前者的激发态是通过激发复费米子 $\qty{f_k^\dagger}$ 构建的，它们由复幅度的 Majorana 费米子 $\qty{\gamma_j}$ 的线性组合构成（见附录A.1）。它们是在蜂窝结构上进行 NN 跃迁的非相互作用费米子。色散关系为[^27]

$$
E(\vb*{k}) = \abs{\epsilon(\vb*{k})}\tag{20}
$$
其中
$$
\epsilon(\vb*{k}) = \frac12 \qty[
J_x \exp(\mi \vb*{k} \vdot \vb*{a}_1)
+J_y \exp(\mi \vb*{k}\vdot \vb*{a}_2+J_z)
]\tag{21}
$$
在这里，$\vb*{a}_1 = \qty(\frac12, \frac{\sqrt{3}}{2})$ 和 $\vb*{a}_2 = \qty(-\frac12, \frac{\sqrt{3}}{2})$ 是原始的平移矢量（见图 1 ），其长度被取为 1. 对于几组参数 $J_x$、$J_y$ 和 $J_z$，式（20）中的色散关系如图 7 所示。

![[截图-1693553040132.png#C|图 7|700]]
在 $J_x = J_y = J_z$ 的各向同性情况下，$E(\vb*{k})$ 在布里渊区的角点节点处（ K 和 K' 点）无能隙，如图 7(d) 的上图所示。在接近无能隙节点点附近，E(k)具有线性色散，类似于石墨烯 $π$ 电子色散中的 Dirac 节点，如图7(d)的插图所示。

这导致了在低能极限下的态密度（DOS）呈 $ω$-线性依赖性，如图 7(d) 的下图所示。

即使在 $J_x$、$J_y$ 和 $J_z$ 的小的*各向异性*情况下，无能隙特性仍然保持不变，尽管节点点发生位移；见图 7(c) 和 7(e)。当通过增加 $\abs{J_z}$ 来增加各向异性时，两个节点点接近并最终合并在某一点，如图7(b)所示。随着各向异性的进一步增加，$E(\vb*{k})$ 在整个布里渊区都有能隙，如图7(a)所示。

激发能隙 $\Delta_\gamma$ 的大小在图 8(a) 中的整个参数空间中绘制。
![[截图-1693553493969.png#C|图 8|500]]

在由条件 $\abs{J_x} \leq \abs{J_y}+\abs{J_z}, \abs{J_y} \leq \abs{J_z}+\abs{J_x},\abs{J_z} \leq \abs{J_x}+\abs{J_y}$ 定义的中心三角形中为零（图中的虚线）。与此同时，在其他三个外部三角形中变为非零值，并且随着Kitaev 耦合的各向异性增加而增加；等高线与无能隙-有能隙边界平行。

图 8(b) 显示了沿图 8(a) 中的中垂线的 $J_z$ 依赖性 ( $J_x = J_y = (3 - J_z)/2$ )，表明在 $J_z > 1.5$ 的有能隙相中，$\Delta_\gamma$ 随着 $J_z$ 的增加而线性增加。因此，关于与游走的 Majorana 费米子相关的费米子激发存在两种不同的相：
- 包括各向同性点的无能隙相
- 包括各向异性极限的有能隙相。

另一方面，其他类型的激发是通过从无能隙基态翻转 $W_p$ 而产生的[[精确可解模型及其他中的任意子_Kitaev]][^27]。结果表明，它们始终具有能隙并且无色散，反映了 $W_p$ 的局域性质。最低能量的激发态是由相邻的两个 $W_p$ 翻转形成的。

在图8(c)的 $J_x\text{-}J_y\text{-}J_z$ 相图上绘制了激发能隙 $\Delta_f$. 在整个参数空间中，除了相图的三个角的各向异性极限外，激发能隙都不为零。在图 8(a) 的有能隙相中，它保持较小，但在无能隙相中迅速增大。如图 8(d) 所示，在图 8(c) 的中心垂直线上，$\Delta_f$ 在 $J_x = J_y = J_z$ 的各向同性点处达到最大值。

因此，这两种不同类型的分数激发具有不同的激发谱。从漫游的 Majorana 费米子中的费米子激发是色散的，并且取决于交换耦合常数的各向异性而成为*有间隙*和*无间隙*。与此同时，$Z_2$ 通量激发总是有间隙的，且呈平坦色散。这两种激发的能量尺度也有很大的不同；前者的带宽大致由三个 $J_\mu$ 之和的一半确定，而后者的激发能隙小得多，小于一个数量级。这两种激发的能量尺度差异影响了热力学和自旋动力学，如后面的部分所讨论的那样。
## 2.6. 有限温度效应

## 2.7. 磁场的作用

让我们回到无通量基态, 并讨论 $T = 0$ 时外部磁场的影响。磁场的塞曼耦合 $-\vb*{h} \vdot \sum_{i} \vb*{S}_i$ 破坏了精确可解性，因为它使等式（17）中的通量算符 $W_p$ 和等式（14）中的 $\eta_r$ 不再守恒。（注意，$g$ 因子的符号与电子自旋的符号相反，如 [[#2.2 bond-dependent 各向异性相互作用的起源|2.2]] 节所讨论。）尽管如此，Kitaev 提出了一种有趣的可能性，即使用相对于磁场强度的微扰理论[^27]）在微扰理论中，最低阶相关项在 $\vb*{h}$ 的三阶
$$
\mathcal{H}' = -\tilde{h} \sum_{\qty{i,j,k}} S_i^xS_j^yS_k^z
\propto - \frac{h_xh_yh_z}{J^2}\sum_{\qty{i,j,k}} S_i^xS_j^yS_k^z\tag{22}
$$
其中 $\vb*{h} = (h_x, h_y, h_z)$，为简单起见，Kitaev 耦合设置为各向同性，$J_x= J_y= J_z = J$；这里，假设所有中间态具有 $J$ 的激发能量。$\qty{i,j,k}$ 的总和是针对相邻的三个 sites 进行的, 见图9(a)。![[截图-1693564507927.png#R|图 9|200]]

请注意，在微扰理论中，由于根据定义，通量配置在初始状态和最终状态之间是相同的，所以 $\qty{W_p}$ 和 $\qty{\eta_r}$ 保持不变。

通过使用第 [[#2.3. 马约拉纳表述|2.3]] 节中的 Majorana 表示，可以将等式(22)写成以下形式：

$$
\begin{align}
\mathcal{H}'= -\frac{\mi \tilde{h}}{8}
\sum_p (\gamma_{p_1}\gamma_{p_3}&+\eta_{b_2}\gamma_{p_3}\gamma_{p_5}+\eta_{b_1}\gamma_{p_5}\gamma_{p_1}\\&+\gamma_{p_4}\gamma_{p_6}+\eta_{b_1}\gamma_{p_6}\gamma_{p_2}+\eta_{b_2}\gamma_{p_2}\gamma_{p_4})\tag{23}
\end{align}
$$

如图 9(b) 所示[^44]，其中 $p_1$-$p_6$ 位点和键 $b_1$ 和 $b_2$ 被定义为属于 plaquette $p$. 式 (23) 表明弱磁场诱导了流动的马约拉纳费米子与 $Z_2$ 键变量 $\qty{\eta_r}$ 的 complex second-neighbor hopping. 这调节了色散关系从式 (20) 到[^27]
$$
E(\vb*{k}) = \pm \sqrt{\abs{\epsilon(\vb*{k}}^2 + \Delta(\vb*{k})^2}\tag{24}
$$

其中 $$
\Delta(\vb*{k}) = \frac{\tilde{h}}{2} \qty{
-\sin (\vb*{k} \vdot \vb*{a}_1) + \sin(\vb*{k}\vdot \vb*{a}_2)
+ \sin [\vb*{k} \vdot(\vb*{a}_1-\vb*{a}_2)]
}\tag{25}
$$

因此，在具有 $J_x = J_y = J_z$ 各向同性的情况下，费米子的激发在 K 和 K' 点具有无能隙的节点, 见图7(d)，而磁场会以正比于 $\tilde{h}$ 得打开一个能隙 $\Delta_{\gamma} = \frac34 \sqrt{3}\tilde{h},\quad \tilde{h} \propto h_xh_yh_z$. 
另一方面，通量能隙 $\Delta_f$ 几乎不受 $\tilde{h}$ 的影响。这些行为在图 11 中有所描述。

有趣的是，具有方程（23）中的第二邻跳跃的模型，在形式上等同于由 [[Duncan Haldane]] 提出的自发量子霍尔效应模型的马约拉纳费米子版本。

这个等价性表明, 磁场中的能隙费米子带是拓扑非平凡的。这个有能隙的状态是一个马约拉纳-陈-绝缘体，陈数 $C = \pm1$（符号由 $h_xh_yh_z$ 的符号确定[^27]）。

因此，类似于其他具有非零陈数的拓扑非平凡绝缘体，弱磁场中的有能隙拓扑态预计具有无能隙的手性边缘模式[^27]。与整数量子霍尔态不同，这种手性边缘电流不能用电磁测量检测到，因为马约拉纳费米子不携带任何电荷.

但是，它们可以通过热测量来观察（见图12）。![[截图-1693566221840.png#R|图 12|300]]

马约拉纳费米子的热霍尔效应具有两个明显特点。
1. 热霍尔电导率除以 $T$ 被预测为整数量子霍尔态的一半.[^27] 这是因为每个马约拉纳费米子携带了一个电子的半自由度，正如第 1 节所提到的。
2. 半量子化的热霍尔效应可以由任何方向的磁场引发，甚至是平面方向。这是因为手性马约拉纳边缘电流是由靠近边缘的自旋增强的泽曼效应引发的（见补充材料III节[^44]），与由洛伦兹力引发的电边缘电流不同。这一有趣的现象是马约拉纳费米子特有的，将在第5.8节中讨论。

到目前为止，除了微扰理论之外，还没有任何严格的论证。尽管如此，已经进行了许多数值研究，以阐明在 $T = 0$ 时磁场的影响。最早的研究之一是针对 Kitaev-海森堡模型进行的密度矩阵重整化群研究 (见第2.8节).[^67] 假设 Kitaev 耦合是各向同性的, 且铁磁的（$J_x = J_y = J_z = J> 0$），磁场沿 $[111]$ 方向施加，强度为 $h$。结果表明，微扰理论预测的具有拓扑非平凡性质的 QSL 状态在临界场 $h_c \simeq 0.018J$ 之前仍然存在，并且在 $h_c$ 以上变成了具有拓扑平凡性质的 forced 铁磁状态。这已经得到了验证，例如通过[[精确对角化]]和其他密度矩阵重整化群计算。[^68][^69][^70][^71][^72]

最近，人们对具有反铁磁（AFM）Kitaev 耦合的情况引起了相当多的关注。虽然上面的微扰理论适用于铁磁和反铁磁情况，但在超出微扰的情况下，这两种情况之间出现了不同的方面。

其中最有趣的方面是在中间磁场区域可能存在另一个拓扑 QSL. [^69][^70][^71][^73][^74][^75][^76] 有人认为，AFM Kitaev 模型在增加磁场时会经历从与微扰区域的拓扑 QSL 相关的低场 QSL 到另一个拓扑 QSL，然后再到 forced 铁磁状态的连续相变。尽管迄今为止尚未确定具有 AFM Kitaev 耦合的候选材料，但这一有趣的可能性引起了广泛的关注。需要注意的是，最近有几个关于实现 AFM Kitaev 耦合的材料的理论提议，例如通过使用 $f$ 电子[^54] 和垂直于蜂窝平面的极性不对称性.[^77]

在磁场下进行有限温度计算更加困难。例如，我们不能应用无符号的基于 Majorana 的 QMC 方法，因为它假定 $\qty{W_p}$ 和 $\qty{\eta_r}$ 的守恒。然而，可以使用无符号的基于 Majorana 的QMC方法研究从微扰中得到的具有有效磁场的 Eqs.（22）和（23）的 Hamiltonian 的有限温度性质。这类应用将在第 5.8 节讨论。此外，最近已经开发了一种 CTQMC 技术，并应用于负符号问题不严重的区域，如第 5.1、5.4 和 5.5 节所讨论的.[^78]
## 2.8. 其它交换作用的效应

## 2.9. 形式化相图

# 3. 热分数化

## 3.1. 二维蜂窝情形的连续 crossovers
### 3.1.1. 热分数化导致的 crossover

### 3.1.2. Crossovers 温度尺度

### 3.1.3. 马约拉纳金属

## 3.2. 相变至二维手性自旋液体

## 3.3. 三维相变

# 4. 材料候选



# 5. 理论与实验的比较研究

## 5.7. 拉曼散射

## 5.8. 热霍尔电导

# 附录: 基于马约拉纳的数值技术

## A.1. 量子蒙特卡洛方法

## A.2. Cluster 动态平均场理论

## A.3. 连续时间量子蒙特卡洛方法





[^1]: E. Majorana, Il Nuovo Cimento 14, 171 (1937).
[^2]: M. Doi, T. Kotani, and E. Takasugi, Prog. Theor. Phys. Suppl. 83, 1 (1985).
[^3]: R. N. Mohapatra and A. Y. Smirnov, Annu. Rev. Nucl. Part. Sci. 56, 569 (2006).
[^4]: E. Akhmedov, in Majorana neutrinos and other Majorana particles: Theory and experiment (The Physics of Ettore Majorana), ed. S. Esposito (Cambridge University Press, Cambridge, U.K., 2015) Chap. 15.
[^5]: F. Wilczek, Nat. Phys. 5, 614 (2009). [[马约拉纳归来]]
[^6]: G. Moore and N. Read, Nucl. Phys. B 360, 362 (1991).
[^7]: H. L. Stormer, D. C. Tsui, and A. C. Gossard, Rev. Mod. Phys. 71, S298 (1999).
[^8]: N. Read and D. Green, Phys. Rev. B 61, 10267 (2000).
[^9]: C. Nayak, S. H. Simon, A. Stern, M. Freedman, and S. D. Sarma, Rev. Mod. Phys. 80, 1083 (2008).
[^10]: J. K. Jain, Annu. Rev. Condens. Matter Phys. 6, 39 (2015).
[^11]: S. Das Sarma, C. Nayak, and S. Tewari, Phys. Rev. B 73, 220502 (2006).
[^12]: R. Jackiw and P. Rossi, Nucl. Phys. B 190, 681 (1981).
[^13]: L. Fu and C. Kane, Phys. Rev. Lett. 100, 096407 (2008).
[^14]: M. Sato and S. Fujimoto, J. Phys. Soc. Jpn. 85, 072001 (2016).
[^15]: M. Sato and Y. Ando, Rep. Prog. Phys. 80, 076501 (2017).
[^16]: A. Kitaev, Ann. Phys. 303, 2 (2003). [[通过任意子的可容错量子计算_Kitaev]]
[^17]: M. H. Freedman, A. Kitaev, M. J. Larsen, and Z. Wang, Bull. Am. Math. Soc. 40, 31 (2003).
[^18]: P. W. Anderson, Mater. Res. Bull. 8, 153 (1973).
[^19]: X.-G. Wen, Quantum Field Theory of Many-Body Systems (Oxford University Press, Oxford, U.K., 2004).
[^20]: L. Savary and L. Balents, Rep. Prog. Phys. 80, 016502 (2017). [[量子自旋液体：综述]]
[^21]: N. Read and B. Chakraborty, Phys. Rev. B 40, 7133 (1989).
[^22]: X. G. Wen, Phys. Rev. B 44, 2664 (1991). [[拥有有限能隙和拓扑序的自旋液体态的平均场理论]]
[^23]: L. Balents, Nature 464, 199 (2010).
[^24]: C. Lacroix, P. Mendels, and F. Mila, Introduction to Frustrated Magnetism (Springer, New York, 2011).
[^25]: H. T. Diep, Frustrated Spin Systems (World Scientific, Singapore, 2013) 2nd ed.
[^26]: Y. Zhou, K. Kanoda, and T.-K. Ng, Rev. Mod. Phys. 89, 025003 (2017).
[^27]: A. Kitaev, Ann. Phys. 321, 2 (2006). [[精确可解模型及其他中的任意子_Kitaev]]
[^28]: G. Khaliullin, Prog. Theor. Phys. Suppl. 160, 155 (2005).
[^29]: G. Jackeli and G. Khaliullin, Phys. Rev. Lett. 102, 017205 (2009).
[^30]: Z. Nussinov and J. van den Brink, Rev. Mod. Phys. 87, 1 (2015).
[^31]: S. Trebst, arXiv:1701.07056.
[^32]: S. M. Winter, A. A. Tsirlin, M. Daghofer, J. van den Brink, Y. Singh, P. Gegenwart, and R. Valentí, J. Phys.: Condens. Matter 29, 493002 (2017).
[^33]: M. Hermanns, I. Kimchi, and J. Knolle, Annu. Rev. Condens. Matter Phys. 9, 17 (2018). [[Kitaev 模型分数化, 动态纠错的物理以及材料联系]]
[^34]: J. Knolle and R. Moessner, Annu. Rev. Condens. Matter Phys. 10, 451 (2019).
[^35]: H. Takagi, T. Takayama, G. Jackelli, G. Khaliullin, and S. E. Nagler, Nat. Rev. Phys. 1, 264 (2019).
[^36]: L. Janssen and M. Vojta, J. Phys.: Condens. Matter 31, 423002 (2019).
[^37]: J. Nasu, M. Udagawa, and Y. Motome, Phys. Rev. Lett. 113, 197205 (2014).
[^38]: J. Nasu, M. Udagawa, and Y. Motome, Phys. Rev. B 92, 115122 (2015).
[^39]: J. Yoshitake, J. Nasu, and Y. Motome, Phys. Rev. Lett. 117, 157203 (2016).
[^40]: J. Yoshitake, J. Nasu, Y. Kato, and Y. Motome, Phys. Rev. B 96, 024438 (2017).
[^41]: J. Yoshitake, J. Nasu, and Y. Motome, Phys. Rev. B 96, 064433 (2017).
[^42]: P. A. Mishchenko, Y. Kato, and Y. Motome, Phys. Rev. B 96, 125124 (2017).
[^43]: J. Nasu, J. Knolle, D. L. Kovrizhin, Y. Motome, and R. Moessner, Nat. Phys. 12, 912 (2016).
[^44]: J. Nasu, J. Yoshitake, and Y. Motome, Phys. Rev. Lett. 119, 127204 (2017).
[^45]: G. Baskaran, D. Sen, and R. Shankar, Phys. Rev. B 78, 115116 (2008).
[^46]: A. Abragam and B. Bleaney, Electron Paramagnetic Resonance of Transition Ions (Clarendon, Oxford, U.K., 1970).
[^47]: H. Liu and G. Khaliullin, Phys. Rev. B 97, 014407 (2018).
[^48]: R. Sano, Y. Kato, and Y. Motome, Phys. Rev. B 97, 014408 (2018).
[^49]: J.-Q. Yan, S. Okamoto, Y. Wu, Q. Zheng, H. D. Zhou, H. B. Cao, and M. A. McGuire, Phys. Rev. Mater. 3, 074405 (2019).
[^50]: W. Yao and Y. Li, arXiv:1908.09427.
[^51]: R. Zhong, T. Gao, N. P. Ong, and R. J. Cava, arXiv:1910.08577.
[^52]: F.-Y. Li, Y.-D. Li, Y. Yu, A. Paramekanti, and G. Chen, Phys. Rev. B 95, 085132 (2017).
[^53]: J. G. Rau and M. J. P. Gingras, Phys. Rev. B 98, 054408 (2018).
[^54]: S.-H. Jang, R. Sano, Y. Kato, and Y. Motome, Phys. Rev. B 99, 241106(R) (2019).
[^55]: Z.-X. Luo and G. Chen, arXiv:1903.02530.
[^56]: J. Xing, H. Cao, E. Emmanouilidou, C. Hu, J. Liu, D. Graf, A. P. Ramirez, G. Chen, and N. Ni, arXiv:1903.03615.
[^57]: H.-D. Chen and J. Hu, Phys. Rev. B 76, 193101 (2007).
[^58]: X.-Y. Feng, G.-M. Zhang, and T. Xiang, Phys. Rev. Lett. 98, 087204 (2007).
[^59]: H.-D. Chen and Z. Nussinov, J. Phys. A 41, 075001 (2008). [[六边形晶格上 Kitaev 模型的精确结果：自旋态、弦和膜关联，以及任意子激发]]
[^60]: A numerical method was recently developed for the former Majorana representation in M. Udagawa, Phys. Rev. B 98, 220404(R) (2018);
[^61]: E. H. Lieb, Phys. Rev. Lett. 73, 2158 (1994).
[^62]: G. Baskaran, S. Mandal, and R. Shankar, Phys. Rev. Lett. 98, 247201 (2007).
[^63]: L. M. Falicov and J. C. Kimball, Phys. Rev. Lett. 22, 997 (1969).
[^64]: C. Zener, Phys. Rev. B 82, 403 (1951).
[^65]: Y. Motome and N. Furukawa, J. Phys. Soc. Jpn. 70, 1487 (2001).
[^66]: F. D. M. Haldane, Phys. Rev. Lett. 61, 2015 (1988).
[^67]: H.-C. Jiang, Z.-C. Gu, X.-L. Qi, and S. Trebst, Phys. Rev. B 83, 245104 (2011).
[^68]: R. Yadav, N. A. Bogdanov, V. M. Katukuri, S. Nishimoto, J. van den Brink, and L. Hozoi, Sci. Rep. 6, 37925 (2016).
[^69]: Z. Zhu, I. Kimchi, D. N. Sheng, and L. Fu, Phys. Rev. B 97, 241110(R) (2018).
[^70]: M. Gohlke, R. Moessner, and F. Pollmann, Phys. Rev. B 98, 014418 (2018).
[^71]: C. Hickey and S. Trebst, Nat. Commun. 10, 530 (2019).
[^72]: J. S. Gordon, A. Catuneanu, E. S. Sorensen, and H.-Y. Kee, Nat. Commun. 10, 2470 (2019).
[^73]: J. Nasu, Y. Kato, Y. Kamiya, and Y. Motome, Phys. Rev. B 98, 060416(R) (2018).
[^74]: S. Liang, M.-H. Jiang, W. Chen, J.-X. Li, and Q.-H. Wang, Phys. Rev. B 98, 054433 (2018).
[^75]: D. C. Ronquillo, A. Vengal, and N. Trivedi, Phys. Rev. B 99, 140413(R) (2019).
[^76]: N. D. Patel and N. Trivedi, Proc. Natl. Acad. Sci. U.S.A. 116, 12199 (2019).

