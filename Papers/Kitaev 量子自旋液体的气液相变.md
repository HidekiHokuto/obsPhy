---
tags: 
- 量子自旋液体
- Kitaev模型
- 相变
- 马约拉纳费米子
created: 2023-07-04 18:25:54
aliases: []
DOI: 
---

原标题: キタエフ量子スピン液体の“気液”相転移

# 摘要

2006年，[[Alexei Kitaev|A. Kitaev]]提出了一个引人注目的量子多体模型，被称为[[Alexei Kitaev|Kitaev]]模型。这个模型是一个简单的模型，其中带有[[自旋|自旋]] $1/2$ 的量子[[自旋|自旋]]在二维蜂窝格上以伊辛型相互作用进行相互作用。尽管从外观上难以想象，但它包含了丰富的物理内容，因此在物质物理学以及统计基础理论和量子信息等物理学的各个领域都受到了广泛关注。

这个模型的最大特点是能够精确地求解基态。在二维及以上的量子多体模型中，可解的模型非常有限，因此这个特性为我们带来了各种新的见解。特别令人惊讶的是，该模型的基态被认为是物质中一种新的量子态，称为量子自旋液体。此外，在相互作用具有异向性的极限情况下，基态可以被拓扑序描述。这是一种不符合传统对称性破缺分类的新的秩序状态。与此特殊的基态相对应，激发态也展示了有趣的性质。例如，出现了既不遵循费米统计也不遵循玻色统计的非可交换任意子。这些特殊的粒子被认为是拓扑量子计算中的操作单元有希望的候选。另一个有趣的方面是，已经指出Kitaev模型可能在强相关电子系统中实现，如铱酸盐等具有强自旋轨道相互作用的材料，这方面正在进行实验和理论上的积极研究。

在多种多样且有趣的性质中，我们关注了从凝聚态物理的角度来看，[[Kitaev 蜂窝模型|Kitaev模型]]所展示的量子自旋液体态，并解析了其热力学性质。到目前为止，[[量子自旋液体]]的理论研究主要针对具有几何约束的格点上的强关联电子模型，例如三角格点，但由于传统的量子蒙特卡罗方法受到负符号问题的限制，系统性的研究变得困难。这样的情况也出现在没有几何约束的Kitaev模型中。因此，我们开发了基于马约拉纳费米子表示的全新量子蒙特卡罗方法，并成功应用该方法进行了无任何近似的数值分析。

本文介绍了对Kitaev模型进行三维扩展的模型的计算结果。该模型是在最近合成的新型铼酸化物中发现的，具有与二维情况相同的格子结构，并且基态是[[量子自旋液体]]。我们发现在这个三维Kitaev模型中，在低温量子自旋液体到高温常磁性态之间存在有限温度的[[相变]]。这相当于量子自旋系统的“气液”相变。在常规流体中，具有相同对称性的气体和液体可以通过环绕临界点这一*一次相变*的终点而连续连接。然而，我们发现的相变在相互作用参数的整个范围内始终存在。这一结果意味着量子自旋液体与常磁性态始终通过相变明确区分开来，暗示这一相变是一种全新类型的相变，与常规的气液相变有所不同。此外，这一相变的特点是与激发态所具有的拓扑性质的变化相关。这种拓扑性质的变化在量子色动力学中的禁闭/非禁闭相变等中也有讨论，并期望存在跨学科的共通概念。

## 名词解释

### [[量子自旋液体]]
这是一个新的量子状态，其中结晶中每个离子所固有的电子自旋在极低温下不展示磁性序。强烈的量子涨落抑制了磁性序的形成。这种状态在磁性相互作用相互拮抗的情况下产生，特别是在具有几何限制的晶格结构中被期望实现。

### 马约拉纳费米子
玛约拉纳费米子是一种粒子，其自身等效于其反粒子。它由Ettore Majorana在1937年提出。与通常由复数场描述的费米子（狄拉克费米子）不同，玛约拉纳费米子由实数场描述，因此其自由度是通常费米子的一半。

### 量子蒙特卡洛与负号问题
蒙特卡洛方法是一种用于对遵循量子力学运动规律的多粒子系统进行数值计算的方法。通过重点生成统计上出现概率高的状态，可以高效地计算物理量。然而，由于出现概率可能变为负值，导致统计误差呈发散性增长的困难情况被称为负符号问题，因此适用于该方法的系统受到限制。

# 1. 导言

由 [[Alexei Kitaev|A. Kitaev]] 引入的理论模型，涉及多个研究领域, 包括 [[量子自旋液体]]、[[拓扑序|拓扑序]]、拓扑量子计算。这个被称为Kitaev模型的模型非常简单，其中量子自旋为1/2，具有伊辛相互作用，尽管如此，它展示了许多有趣的性质。而且，尽管它是一个二维量子多体模型，但它是可解的。因此，Kitaev模型以及其有效模型，即托里克码模型，在凝聚态物理、统计基础理论、量子信息、格子规范理论等许多不同的研究领域都受到了积极的研究。

从物性物理的角度来看，Kitaev模型最有趣的性质之一是其基态是*量子自旋液体*。在许多磁性绝缘体中，通过*强电子相关性*，每个晶格点上局部化的电子的自旋决定了其物性。在高温下，这些自旋由于热涨落而变成无序的顺磁态，但在低于某个温度时，自旋之间的相互作用导致自旋有序排列，实现了破缺对称性的磁性秩序。前者对应于物质的三种状态中的“气体”，后者对应于破缺了平移对称性的“固体”。另一方面，尽管自旋之间强烈相互关联，但它们不显示磁性序的“液体”状态被称为自旋液体。特别是根据液体氦在极低温下由于强量子涨落而不会凝固（有序化）的类比，[[Philip W. Anderson|P. W. Anderson]] 于1973年提出了量子自旋液体作为一种新的量子态。至今，它仍然是实验和理论的前沿研究课题。

我们通过开发和应用基于Kitaev模型的可解性的大规模数值计算方法，首次成功地阐明了该模型所展示的量子自旋液体状态的热力学性质 [5-7]。作为值得注意的成果，我们发现了量子自旋系统的"气液"相变，即从低温量子自旋液体到高温常磁性状态的有限温度相变。在本文中，我们将从介绍Kitaev模型的基本性质开始，概述我们开发的数值计算方法，并讨论我们通过应用这些方法发现的相变及其特征。

---

# 2. Kitaev 模型

哈密顿量
$$H = -J_x \sum_{\ev{ij}_x}\sigma_i^x \sigma_j^x
-J_y \sum_{\ev{ij}_y}\sigma_i^y \sigma_j^y
-J_z \sum_{\ev{ij}_z}\sigma_i^z \sigma_j^z \tag{1}$$


```ad-quote
title: 图 1
 - (a) 蜂窝格子是定义Kitaev模型的结构。蓝色、绿色和红色的键分别表示相互作用项为 $-J_x \sigma_i^x \sigma_j^x$, $-J_y \sigma_i^y \sigma_j^y$, $-J_z \sigma_i^z \sigma_j^z$. ![[截图-1688465278005.png#R|图 1|400]]在这个模型中, 每个六边形都存在*局部守恒量* $W_p$. 例如，黄色标记的六边形的 $W_p$ 由 $W_p = σ_1^z \sigma_2^y \sigma_3^x \sigma_4^z \sigma_5^y \sigma_6^x$.
 
 - (b) $J_x + J_y + J_z=1$ 参数面的 Kitaev 模型基态相图.
 
 - (c) $J_z \gg J_x, J_y$ 时的有效模型 ([[toric code model]]). 红色格点对应于 (a) 中的红色键，黄色的四边形对应于 (a) 中的六边形。
```



这个模型的特点在于具有许多*局部守恒量*。为了观察这一点，让我们考虑如图1（a）所示的六边形 $p$。蜂窝格子的配位数为 $3$，因此在这个六边形的每个顶点上都有一个不属于该六边形的键存在。我们定义一个由这些键的成分构成的由6个Pauli矩阵乘积组成的算符Wp。例如，在图1（a）的六边形中，$W_p = σ_1^z \sigma_2^y \sigma_3^x \sigma_4^z \sigma_5^y \sigma_6^x$. 根据不同成分的 Pauli 矩阵的反对易关系，可以容易地证明*哈密顿量与 $W_p$ 是可交换的*，并且*不同六边形的 $W_p$ 之间也是可交换的*。此外，$W_p^2 = 1$ 成立。由于这些事实，可以看出每个六边形的 $W_p$ 都是守恒量，而Kitaev模型的本征态可以通过每个六边形上 $W_p$ 的值的集合 $\qty{W_p = ±1}$ 来指定。这些局部守恒量的存在在讨论[[Kitaev 蜂窝模型|Kitaev模型]]的性质时起着最重要的作用。

```ad-note
1. $\comm{H}{W_p} = 0$
2. $W_p^2 = 1$
```


局部守恒量的另一种观点是考虑以下变换。这个变换在我们后来引入的新数值计算方法中非常重要。首先看图1（a），可以看出包含 $σ^x$ 和 $σ^y$ 相互作用的 $x$、$y$ 键形成一维链。沿着这条链进行 [[Jordan-Wigner 变换]]，每个 site $i$ 的量子自旋可以用两种类型的 [[Majorana 费米子]] $c_i$ 和 $\overline{c}_i$ 来表示。作为结果，式（1）的哈密顿量可以写成[8, 9, 10]：

$$
H = \mi J_x \sum_{\ev{ij}_x}c_ic_j
-\mi J_y \sum_{\ev{ij}_y} c_ic_j - \mi J_z \sum_{\ev{ij}_z} \eta_r c_i c_j\tag{2}
$$
在这种情况下，最近邻 $\ev{ij}$ 中，$i$ 位点被设定为, 位于左侧（对于 $z$ 键而言则是向下）。在此，$η_r = \mi \overline{c}_i \overline{c}_j$ 定义在每个 $z$ 键 $r$ 上, 与哈密顿量对易，并满足 $η^2_r = 1$. 此外，$W_p$ 和 $η_r$ 之间存在着关系 $W_p = \prod_{r∈p} η_r$ (乘积仅适用于定义 $W_p$ 的六角形中的 $z$ 键). 因此，由于 $η_r$ 也是守恒量，因此可以通过集合 $\qty{η_r＝±1}$ 来指定Kitaev模型的本征态。另外，根据式（2），对于每个｛ηr＝±1｝，它都成为自由的玛约拉纳费米子系统，因此其本征态可以通过对角化轻松求解。基态由所有ηr取＋1给出，11）根据激发能隙的有无，可以得到基态的相图如图1（b）所示。当交互作用常数Jx，Jy，Jz相差不大时，基态不具有激发能隙，但当某个常数相较于其他常数更大时，就会出现异向性并打开激发能隙。

# 3. 量子自旋液体

在Kitaev模型中，已经严格证明了自旋相关性仅在最近邻键之间具有非零值[2]。由此可知，Kitaev模型的基态是具有*短程自旋相关性*的量子自旋液体。特别地，在*各向异性极限*下，已经证明了[[toric code model|Toric Code模型]]的基态是由[[拓扑序|拓扑序]]定义的 $Z_2$ 自旋液体。因此，可以将Kitaev模型的基态视为具有与各向异性极限和连续的激发能隙相对应的 $Z_2$ 自旋液体。

在Kitaev模型中，不仅可以精确计算基态，还可以计算激发态。因此，不仅可以计算同时刻的自旋相关性，还可以计算动态自旋相关性。正如式（2）所给出的，Kitaev模型可以用*遍历*的 Majorana 粒子 $c_i$ 和*局域化*的 Majorana粒子 $\overline{c}_i$ 表示，而*动态自旋相关函数*则通过使用局域化的 Majorana 粒子被激发的中间态给出，这与*X射线吸收边异常*问题等价。正如上述所述，[[Kitaev 蜂窝模型|Kitaev模型]]的基态性质和激发结构已经被详细研究，但在有限温度下的行为分析几乎没有进行过。

# 4. 基于马约拉纳费米子的量子蒙特卡洛法

迄今为止，对量子自旋液体的理论研究大多局限于绝对零度，这是因为分析的困难性。在有限温度下的分析在原理上可以通过*世界线量子蒙特卡洛方法*进行，但由于符号问题的存在，其适用范围受到限制。实际上，即使对于Kitaev模型，应用世界线量子蒙特卡洛方法也很困难。然而，我们发现通过巧妙地利用Kitaev模型的可解性，可以实现一种不受符号问题困扰的全新量子蒙特卡洛方法。在接下来的内容中，我们将概述该方法。

Kitaev模型可以被视为与每个 $z$ 键相关联的伊辛变量耦合的*自由马约拉那费米子系统*。这种与经典自由度耦合的自由费米子问题在各种系统中都会出现。例如，*双重交换模型*，它是为了理解锰氧化物中的巨大磁电阻效应而进行的研究，涉及到遍历电子和经典自旋的耦合。从式（2）的形式中，我们意识到通过这样的研究所培养的分析方法也可以应用于Kitaev模型。我们将应用于*遍历电子系*的算法来模拟量子自旋系统。

在实际的计算中, Kitaev 模型的配分函数
$$
Z = \Tr_{\qty{\eta_r}} \Tr_{\qty{c_i}} \me^{-\beta H}
= \Tr_{\qty{\eta_r}} \me^{-\beta F_f(\qty{\eta_r})}
$$
通过蒙特卡洛法计算. 为此，我们需要计算在给定配置 $\qty{η_r}$ 下的马约拉那费米子系统的自由能 $F_f(\qty{\eta_r})$，并通过蒙特卡洛方法更新 $\qty{η_r}$ , 使得热平衡分布符合 $\me^{-\beta F_f(\qty{η_r})}$. 

在本研究中，我们通过*严格对角化*来计算 $F_f(\qty{\eta_r})$, 但也可以利用多项式展开等技术，借鉴在双重交换模型中发展起来的知识和技巧，以提高模拟的效率。[25,26]

# 5. 量子自旋展示出的气液相变

# 6. [[toric code model|Toric code]] 极限

