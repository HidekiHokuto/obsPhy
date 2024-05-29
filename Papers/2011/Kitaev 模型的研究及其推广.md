---
tags:
  - 论文
created: 2023-11-08 22:47:21
aliases:
  - Investigations on the Kitaev Model and some of its generalisations
DOI: 
author:
  - "[[Saptarshi Mandal]]"
original title: Investigations on the Kitaev Model and some of its generalisations
year: "2011"
---

# 摘要

我们研究了一个六方晶格上的失意量子自旋 $1/2$ 模型[a]，该模型最初是由a . Kitaev提出和分析的。为了在拓扑量子计算领域中可能实现，引入了该模型。它具有各向异性最近邻自旋自旋相互作用这取决于键的方向可以写成这样，

## Jordan-Wigner 费米子化的精确解决方案

# 1. 导言

传统的凝聚态物理学基于Landau的相变理论和对称破缺机制[1,2]，在解释各种现象方面相当成功。这个理论的实质是物质的不同相对应于组成原子或分子的不同顺序。是组成粒子之间的顺序或对称性决定了相。当一种物质从一种顺序变化到另一种顺序(即，当物质经历相变)时，所发生的是组成粒子的组织的对称性改变。最简单的例子是液体到固体的转变。我们发现在液相中存在连续平移对称，而在固相中不存在，这种差异完全表征了相变。基于对称破缺机制的朗道相变理论的成功实现，可以解释磁性的不同相、He4和He3的超流体相、金属中的超导性等。

# 2. Kitaev 模型

本章简要介绍了Kitaev模型，并讨论了其由Kitaev本人获得的形式化解[33]。这个自旋 1/2 模型定义在蜂窝状晶格上，每个点的自旋为1/2。

![[截图-1699799116830.png#C|图 2.1|500]]


## 2.1. 自旋 $1/2$ 算符的费米子化

假设每个晶格点都有两个费米子，分别标记为 “1” 和 “2”. 于是我们有了与这两个费米子有关的生成和湮灭算符，$c_1$, $c_2$, $c_1^\dagger$, $c_2^\dagger$. 这意味着我们处理的是一个四维 fock 空间，状态为 $\ket{0,0}$, $\ket{1,0}$, $\ket{0,1}$, $\ket{1,1}$，其中 '0' 和 '1' 表示费米子的占有数，第一个数字和第二个数字分别表示第一个和第二个费米子的占有数。对于一个给定的 site，我们用下面的方法从这两个复费米子中构造出四个马约拉纳费米子

$$
\begin{align}
c &= (c_1 + c_1^\dagger)\tag{2.4}\\
c^x &= \frac{1}{\mi} (c_1 - c_1^\dagger) \tag{2.5}\\
c^y &= (c_2 + c_2^\dagger) \tag{2.6}\\
c^z &= \frac{1}{\mi} (c_2 - c_2^\dagger) \tag{2.7}
\end{align}
$$
在上面的表达式中，我们没有显式地显示 site 索引。我们可以很容易地验证以下这些 Majorana 费米子算符之间的对易关系
$$
\acomm{c^\alpha}{c^\beta} = \delta_{\alpha, \beta},
\quad c^\alpha = (c^\alpha)^\dagger,
\quad \alpha, \beta = x,y,z \tag{2.8}
$$
在自旋哈密顿算符中出现的原始自旋 $1/2$ 算符用 Majorana 费米子算符表示如下
$$
\begin{align}
\sigma^x = \mi c^x c\\
\sigma^y = \mi c^y c\\
\sigma^z = \mi c^z c
\end{align}
$$
可以检查任意两个运算符: $\sigma^\alpha, \sigma^\beta$. 当 $\alpha \neq \beta$ 时, 反对易. 
然而，这并没有完成泡利自旋代数。条件 $\sigma^x \sigma^y \sigma^z = \mi$ 表示约束条件 $c^xc^yc^zc=1$. 我们称 $c^xc^yc^zc=D$, $D$ 可以写成
$$D = (2c_1^\dagger c_1-1)(2c_2^\dagger c_2-1)$$
现在 $D$ 仅在由状态 $\ket{0,0}$ 和 $\ket{1,1}$ 张成的子空间中为 $1$。另外两种状态 $\ket{0,1}$ 和 $\ket{1,0}$, $D$ 为 $-1$. 由于这个原因，只包含 $\ket{0,0}$ 和 $\ket{1,1}$ 的子空间被称为*物理子空间*，因为在这个子空间中，以 Majorana 费米子的定义表示的自旋是精确的。可以看出，算子 $D$ 作为局部 $Z_2$ 规范群的生成器。上述定义意味着我们必须应用投影算子 $P$，它将 project out 非物理状态。在第 $i$ 个位置的投影算子 $P_i$ 定义如下：
$$
P_i = (1+D_i)/2 \tag{2.12}
$$

## 2.2. 二次型哈密顿量

现在我们用费米算符来表示哈密顿函数。将方程(2.9,2.10,2.11)中给出的关系插入式(2.1)后，原来的自旋哈密顿量简化为

我们观察到上述哈密顿量中的每一项在马略阿纳费米翁算符中都是四次函数。然而，可以很容易地注意到，在上述哈密顿变换的每一项的括号内的算子与哈密顿变换和它们之间的变换。这意味着它们是守恒量就费米化哈密顿量而言。这一事实使得Eq.(2.13)在马约拉纳费米子中是有效的二次型。对于x-link，我们称ica x,icb x,j = ux i,j。类似地，我们在y和z连杆上分别定义uy i j和uz i j。显然，ui、j =−uj、i及其特征值可以取值±1。这里我们遵循的惯例是先保留属于' a '子晶格的位置的指标然后是' b '子晶格在ui,j的表达式中。哈密顿函数的形式如下，

## 2.3. 基态

我们已经论证过，只有在 $B_p = 1$ 的均匀构形中才包含谱的全局最小值。在这里，我们考虑为每个链接选择 $u_{ij} =1$，这是每个 plaquette $B_p =1$ 的*实现之一*。在此之后，我们注意到马约拉纳费米子跳变哈密顿量简化为一个*平移不变*的哈密顿量，便于使用傅里叶变换来轻松求解。平移不变哈密顿量由，

为了求解上面的哈密顿量, 我们定义马约拉纳费米子算符的傅里叶变换为
$$
c_{i}^{a,b} = \sum_k \frac{1}{\sqrt{MN}}\me^{\mi \vb*{k} \vdot \vb*{r}} c_k^{a,b} \tag{2.19}
$$
在这里，我们取了一个在 $\vu*{e}_1$ 和 $\vu*{e}_2$ 方向上分别有 $M$ 和 $N$ 个单元格的晶格(图 2.1). 这里 $\vb*{r} = m \vu*{e}_1 + n \vu*{e}_2$ 和 $\vb*{k} = \dfrac{p}{M} \vb*{G}_1 + \dfrac{q}{N} \vb*{G}_2$，其中 $\vb*{G}_{1,2}$ 是倒易的晶格向量

$$
\vb*{G}_1 = \frac{4\pi}{\sqrt{3}}
\qty(\frac{\sqrt{3}}{2} \vu*{e}_x + \frac{1}{2} \vu*{e}_y); \quad
\vb*{G}_2 = \frac{4 \pi}{\sqrt{3}} \vu*{e}_y \tag{2.20}
$$



# 3. 精确本征态: J-W 变换

Jordan-Wigner变换在成功应用于涉及局部相互作用的一维自旋1/2模型时是相当著名的[135, 136]。我们知道，在这个特定的过程中，自旋算符通常以新的费米子算符的形式重新表达，这些算符在一般情况下是*非局部*的。但在一维情况下，如果哈密顿量涉及局部自旋-自旋相互作用，它通常产生易于解决的局部费米子哈密顿量。最近，在[136]中提出了将 Jordan-Wigner 变换推广到更高维度的方法。

在这一章中，我们展示 Kitaev 模型的新颖性使我们能够应用一维 Jordan-Wigner 变换（JWT）来解决这个二维自旋 1/2 模型。在先前的章节中，我们使用了四个 Majorana 费米子（或等效地是两个复费米子）来费米化给定位置上的自旋算符。这意味着每个位置的局部 Fock 空间维度为 4，尽管最初的自旋 1/2 在每个位置上定义了二维的 Fock 空间维度。Jordan-Wigner 变换的重要性在于，它不会扩大给定位置的希尔伯特空间维度，因为它处理的是给定位置上的一个*无自旋*的复费米子。此外，我们能够构建守恒量和哈密顿量的显式本征态。我们还确认先前章节中获得的谱解是精确的[^77][^78]。值得注意的是，尽管先前已经使用 Jordan-Wigner 变换解决了 Kitaev 模型[^78][^79]，但我们的方法具有一些优势，因为它可以应用于任何边界条件。此外，我们的构建也可以推广到更高维的Kitaev模型。

在 Kitaev 模型中，我们可以定义具有*开放*和*周期边界条件*的 Jordan-Wigner 变换。在这一章中，我们将 JWT 应用于周期性边界条件，即在 torus 上。有关开放边界条件的JWT的详细信息可以在[[#A. 针对 OBC 的 J-W 变换|附录 A]]中找到。

在开始JWT之前，我们将更详细地讨论具有周期性边界条件的格点模型的守恒量。这有助于解释该模型的简并性。

## 3.1. 守恒量

![[截图-1699800607181.png#C|图 3.1|400]]
```ad-info
title: 图 3.1
在图 1a 中，我们展示了蜂窝格子的一部分。链接用 $x$、$y$ 和 $z$ 标记，以指示自旋-自旋相互作用的键相关性。对于这个二维模型的每条一维链，存在一个非平凡的环算符。我们用索引 1 到 8 表示了这样一条链。在图 1c 中，我们展示了一个单独的六边形来解释 $B_p$. 更多解释请参阅文本。
```


我们之前提到过，晶格的每一个 plaquette 都有一个守恒量。如果 plaquette 用 $p$ 表示，其顶点标记如图 (3.1, 1c) 所示，则根据 Kitaev 的标记，守恒量为:
$$
B_p = \sigma_1^y \sigma_2^z \sigma_3^x \sigma_4^y \sigma_5^z \sigma_6^x 
$$
我们有 $B_p^2 = 1$，这意味着 $B_p$ 的特征值可以取 $\pm 1$。很明显，任意数目的 $B_p$ 的乘积都可以与哈密顿量交换。

实际上，与格子上的每个闭合 self avoiding 环有关的守恒量可以如下定义。如果 $C$ 的 sites 为 $i_1$, $i_2$, $\cdots$, $i_N$，那么与之相关的守恒量是：
$$
B_C = \prod_{n=1}^N \sigma_{i_n}^{\alpha_n} \tag{3.2}
$$
在这里，$\alpha_n$ 表示在 site $n$ 处的 link. 可以验证
$$
\comm{B_C}{H} = 0; \quad B_C^2 = 1
$$

我们称 $C$ 为*拓扑平凡*的，如果它可以被仅由 $B_p$ 的乘积写成。在环面上，我们有两个环算符，它们沿两个正交方向围绕环面旋转，不能表示为 $B_p$ 的乘积。这两个拓扑非平凡的环被表示为 $B_{c1}$ 和 $B_{c2}$. 从图 (3.1, 1a) 中，我们得到了沿完整 $x-y$ 链的水平旋绕的以下守恒算符 $B_{c1}$

$$
B_{c1} = \sigma_1^z \sigma_2^z \sigma_3^z \sigma_4^z \sigma_5^z \sigma_6^z \sigma_7^z \sigma_8^z \tag{3.4}
$$

对于每个 $x-y$ 链，我们可以找到一个类似上述的守恒算符. 然而，其中只有一个是独立的。沿 $x-z$ 链环绕也是如此，它给出另一个非平凡的环守恒算符 $B_{c2}$. 然而，沿 $y-z$ 链的环绕并不会产生另一个独立的守恒环算符，因为它可以由 $B_{c1}$、$B_{c2}$ 和 $B_p$ 的适当组合构建出来。我们注意到，由于 torus 上的以下约束，所有的 $B_p$ 并不是独立的：
$$
\prod_p B_p = 1
$$
因此存在 $N_{p}-1$ 个独立的 $B_p$，其中 $N_p = MN$ 是 plaquettes 的数量。加上 $B_{c1}$ 和 $B_{c2}$，我们在环面上有 $N_{p}+1$ 守恒量。让我们数一数我们可以选择某个 $B_p$ 构型的独立方式的数量 (即每个 plaquette 的 $B_p$ 特征值的分布)，我们得到

$$
\frac{2^{N_p+1}}{2^{N_p-1}} = 4 \tag{3.6}
$$

上述计数表明，有四种不同的状态具有相同的 $B_p$ 配置。因此，如果基态部分属于 $B_p$ 的均匀配置，我们应该得到四个简并状态，其基态能量相同，因为谱只依赖于 $B_p$ 而不依赖于 $B_{c1}$ 和 $B_{c2}$. 事实上，稍后我们将证明这是正确的。现在我们可以讨论 Kitaev 模型的 JWT 变换了.


## 3.2. 周期边界条件的 J-W 变换


要定义 Jordan-Wigner 变换，我们需要在格子上定义一条路径，我们称之为 Hamilton 路径。这个 Hamilton 路径应该包含格子上的所有站点，而且应该是 self-avoiding 的. 六边形格子的*连接度*为 3，这意味着一个站点连接到三个相邻的站点。如果我们考虑一个特定的站点，我们会发现 Hamilton 路径包含从该站点出来的两个键。我们将这两个键称为 tangent bonds. 从 Hamilton 路径出去的剩余键称为 normal bond. 在图 (3.2) 中，我们解释了我们对法线键和切线键的概念.

![[截图-1699803185766.png#C|图 3.2|300]]

```ad-info
title: 图 3.2
这是 JW path 的一部分。红色的 links 构成 normal 键，黑色的 links 构成 tangential 键。Jordan-Wigner 路径由箭头的方向表示.
```

当我们找到这样的Hamilton路径时，我们观察到法线键形成了一个格子的二聚体覆盖，如图3.3所示。
![[截图-1699806046954.png#C|图 3.3|300]]
我们为两个切线键关联两个切线向量，$\vu*{t}_{1i}$ 和 $\vu*{t}_{2i}$，根据传入键和传出键的方向，它们分别是 $\vu*{x}$、$\vu*{y}$ 或 $\vu*{z}$. 下标 $i$ 指的是 Hamilton 路径上的一个特定 site. 然后我们定义一个法线向量 $\vu*{n}_i$，如下所示：
$$
\vu*{n}_i = \vu*{t}_{1i} \cross \vu*{t}_{2i}
$$

我们现在明确地定义了在本文中使用的周期边界条件。蜂窝状点阵是一种以两个点阵为基的三角形点阵。三角形点阵的位置由

$$
\vb*{R}_I = I_1 \vb*{e}_1 + I_2 \vb*{e}_2 \tag{3.8}
$$


其中，$I_1$、$I_2$ 为整数，$\vb*{e}_1 \vdot \vb*{e}_2 =−1/2$$, $\vb*{e}_1 \vdot \vb*{e}_1 = 1 = \vb*{e}_2 \vdot \vb*{e}_2$. 因此，用于表示蜂窝状点阵的位置的标号 $i$ 表示 $(I_1, I_2, r)$，其中 $r = 1,2$ 是子点阵指标。*周期边界条件*定义为
$$
\sigma_{I_1,I_2,r}^\alpha = \sigma_{I_1+M, I_2+N, r}^\alpha
$$
### 3.2.1. JWT 的“无序”变量

我们定义 Jordan-Wigner 变换如下。我们取一个在格子上的 Hamilton 路径，由站点的序列 $i_n$，$n = 1, \cdots, N_S$ 定义，其中 $N_S$ 是格子上站点的数量。接下来，我们引入一些有助于以简单方式定义 JWT 的无序变量。

### 3.2.2. 规范不变 Jordan-Wigner 费米子

### 3.3.3. 规范固定哈密顿量

### 3.2.4. 费米守恒量

## 3.3. 基态的四倍简并

### 3.3.1. 选择 1
### 3.3.2. 选择 2

## 3.4. ‘8’ site 问题


# 4. 自旋-自旋相关

在本章中，我们介绍了我们在Kitaev模型中对自旋-自旋关联的研究。我们证明，对于这个模型，我们可以精确地计算出所有特征态的所有自旋-自旋关联。我们采用的推导自旋-自旋关联的方法是在[^33]中实现的费米化过程的扩展。我们已经看到，在[^33]中进行的费米化过程扩大了局部希尔伯特空间维数，但由于在 Kitaev 模型中存在局部守恒量，希尔伯特空间扩大只产生“规范副本”，而不改变能谱。这有助于我们在这种形式下准确地确定自旋-自旋关联。

当使用扩大的费米子希尔伯特空间进行研究时，这种显著的特征在标准的二维海森堡模型中是不存在的[55,68]。

## 4.1. 键费米子形式

我们在第二章已经看到两个复费米子产生四个马约拉纳费米子。基本上每个复费米子可以改写成两个马约拉纳费米子。为了简化自旋-自旋相关的计算，我们通过重新组合两个不同的马约拉纳费米子来定义一个复费米子，从而颠倒了上面的步骤。

我们已经看到，在每一个环节上都有一个守恒量，命名为 $u_{ij}^\alpha$，由马约拉纳费米子 $b_{a,i}^\alpha$ 和$b^\alpha_{b,j}$ 组成。这里 $i$ 和 $j$ 表示一个键的两个位点，$a$ 和 $b$ 区分不同 sublattice，$\alpha$ 表示一个特定的 bond. 我们将这两个 bond 上的马约拉纳费米子重新组合，来描述一个复费米子 $\chi_{{\ev{ij}}_{\alpha}}$，它位于连接位点 $i$ 和 $j$ 的键上。我们称这个过程为*键费米子形式论* (bond fermion formalism).

从现在开始，我们遵循键 $\chi_{{\ev{ij}}_{\alpha}}$ 中的位置 $i$ 属于 $a$ 亚晶格，而位置 $j$ 属于 $b$ 亚晶格。从现在开始，我们不再明确地提到子格索引 $a$ 和 $b$. 我们把每个键上的复费米子定义为
$$
\begin{align}
\chi_{\ev{ij}_\alpha} = \frac12 (b_i^\alpha + \mi b_j^\alpha) \tag{4.1}\\
\chi_{\ev{ij}_\alpha}^\dagger = \frac12 (b_i^\alpha - \mi b_j^\alpha) \tag{4.2}
\end{align}
$$
![[截图-1699622678932.png#C|图 4.1|400]]
例如，参考图 4.1，对于 $z$ 键连接位点 $2$ 和 $3$，以及 $y$ 键连接位点 1 和 2，我们定义
$$
\chi_{\ev{23}_z} = \frac12 (b_2^z + \mi b_3^z);
\quad \chi_{\ev{21}_y} = \frac12 (b_2^y + \mi b_1^y)
\tag{4.3}
$$
于是，对于 sites 2 和 3，$\sigma^z$ 算符变成
$$
\sigma_2^z = \mi b_2^z c_2 = \mi \qty(\chi_{\ev{23}_z}+\chi_{\ev{23}_z}^\dagger) c_2
$$
$$
\sigma_3^z = \mi b_3^z c_3
= \mi \frac{\chi_{\ev{23}_z}-\chi_{\ev{23}_z}^\dagger}{\mi} c_3 = \qty(\chi_{\ev{23}_z}-\chi_{\ev{23}_z}^\dagger)c_3
$$
下面我们写出了连接 $i$ 和 $j$ 位点的 $\alpha$ 型键 re-fermionisation 的结果

$$
\chi_{\ev{ij}_\alpha} = \frac12 (b_i^\alpha + \mi b_j^\alpha); \quad \chi_{\ev{ij}_\alpha}^\dagger = \frac12 (b_i^\alpha - \mi b_j^\alpha)\tag{4.5}
$$
$$
\sigma_i^\alpha = \mi \qty(\chi_{\ev{ij}_\alpha} + \chi_{\ev{ij}_\alpha}^\dagger)c_i;
\quad \sigma_j^\alpha = \qty(\chi_{\ev{ij}_\alpha} - \chi_{\ev{ij}_\alpha}^\dagger)c_j
$$

很明显，一个 site 上的自旋算符的三个分量与定义在从它发出的三个不同键上的三个不同的 $\chi$ 费米子相连接. 键变量与这些费米子的 number operator 有关
$$
\hat{u}_{\ev{ij}_\alpha} \equiv \mi b_i^\alpha b_j^\alpha
= 2 \chi_{\ev{ij}_\alpha}^\dagger \chi_{\ev{ij}_\alpha}-1
$$

因此，从图 4.1 容易理解有效图景。我们在每个键上识别一个 $\chi$ 费米子，其占据数可以是 0 或 1. 这个占据数确定了该键上 $u_{\ev{ij}}$ 的值。但这些费米子是守恒的，并且充当 $c$ 费米子跃迁的有效 $Z_2$ 规范势。由于 $\chi$ 费米子是守恒的，因此可以选择所有本征态具有确定的 $\chi$ 费米子占据数。然后，哈密顿量在占据数配置中是*块对角*的，每个块对应于每个键的不同 $\chi$ 费米子占据数的一组明确的集合。因此，扩展希尔伯特空间中的所有本征态采用以下分解形式：

$$
\begin{align}
\ket{\tilde\Psi} = \ket{\mathcal{M}_{\mathcal{G}}; \mathcal{G}} &= \ket{\mathcal{M}_{\mathcal{G}}} \ket{\mathcal{G}}\\
\text{with}\quad \chi_{\ev{ij}_\alpha}^\dagger \chi_{\ev{ij}_\alpha} \ket{\mathcal{G}} &= n_{\ev{ij}_\alpha} \ket{\mathcal{G}}
\end{align}
$$

其中，$n_{\ev{ij}}^α = (u_{\ev{ij}}^\alpha + 1)/2$，而 $\ket{\mathcal{M}_{\mathcal{G}}}$ 是在由 $c$ 费米子确定的物质部分中的多体本征态，对应于由 $\ket{\mathcal{G}}$ 确定的给定 $Z_2$ 场配置.

![[截图-1699643088960.png#C|Fig 4.2|400]]
```ad-info
title: 图 4.2
给出了自旋如何分成两个静态 $π$ 通量和一个动态的马约拉纳费米子。$\ket{\psi}$ 是零通量状态。我们将 $\sigma^z_i$ 应用到位置 $i$ 与位置 $j$ 相连接的地方。得到了具有两个静态 $\pi$ 通量的状态 $\ket{\psi'}$ 和一个用黑圆表示的动态马约拉纳费米子。
```

现在我们详细讨论上述规范转换的优点。写成上述形式 (见式 4.5)，$\sigma_i^\alpha$ 对任何本征态的影响变得简单。除了在位点 $i$ 上增加一个马约拉那费米子外，它还改变了键费米子数，从 0 到 1，反之亦然 (相当于在键 $\ev{ij}_\alpha$ 上，$u_{\ev{ij}_\alpha} \to -u_{\ev{ij}_\alpha}$)。最终的结果是，在两个由键 $\ev{ij}_\alpha$ 共享的 plaquettes 上分别添加一个 $\pi$ 通量 (图 4.2)。我们用符号表示它为

$$
\sigma_i^\alpha =
\mi \qty(\chi_{\ev{ij}_\alpha} + \chi_{\ev{ij}_\alpha}^\dagger)c_i
= \mi \hat{\pi}_{1\ev{ij}_\alpha}
\hat{\pi}_{2 \ev{ij}_\alpha} c_i
$$

其中，$\hat{\pi}_{1\ev{ij}_\alpha}$ 和 $\hat{\pi}_{2\ev{ij}_\alpha}$ 被定义为向由键 $\ev{ij}_\alpha$ 共享的两个相邻的平面添加 $\pi$ 通量的算符（图4.2）。此外，$\hat{\pi}_{1\ev{ij}_\alpha}^2 = 1$，因为添加两个 $\pi$ 通量等效于添加（对 $2\pi$ 取模）零通量。很显然，具有不同通量配置的两个状态之间的重叠为零，因为它们属于不同的 $\chi$ 费米子占据数分布。这一观察是准确计算自旋-自旋相关性的关键要素。首先，我们呈现两个自旋相关函数的计算。其他多自旋相关性可以通过这个程序的直接推广来计算。

## 4.2. 双自旋相关系数

在这里，我们在扩展的希尔伯特空间中计算*自旋-自旋相关函数*。我们注意到，出于以下原因，这个结果可以在物理希尔伯特空间中得到精确的扩展。由于自旋算符是规范不变的，我们可以在任何规范固定的部分计算相关性，答案将与在物理规范不变的子空间中相同（我们已通过在投影的物理子空间中的计算确认过这一点，详细信息请参见[[#C. 自旋-自旋相关注释|附录 C]]）。首先，我们考虑在某个固定规范场配置 $\mathcal{G}$ 下的 Kitaev 哈密顿量的任意本征态中的两个自旋动力学相关函数

$$
S_{ij}^{\alpha \beta} (t) =
\bra{\mathcal{M}_{\mathcal{G}}}
\bra{\mathcal{G}} \sigma_{i}^\alpha(t) \sigma_j^\beta (0) \ket{\mathcal{G}} \ket{\mathcal{M}_{\mathcal{G}}}
\tag{4.10}
$$
这里 $A(t) = \me^{\mi Ht} A \me^{-\mi Ht}$ 是算符 $A$ 的海森堡表象，保持 $\hs= 1$。我们之前讨论过自旋算符作用于任意特征态，
$$
\begin{align}
\sigma_j^\beta(0) \ket{\mathcal{G}} \ket{\mathcal{M}_{\mathcal{G}}}
&= c_j(0) \ket{\mathcal{G}^{j \beta}} \ket{\mathcal{M}_{\mathcal{G}}}\\
\sigma_i^\alpha(t) \ket{\mathcal{G}} \ket{\mathcal{M}_{\mathcal{G}}}
&= \me^{\mi (H-E)t} c_i(0) \ket{\mathcal{G}^{i \alpha}} \ket{\mathcal{M}_{\mathcal{G}}}
\end{align}
$$

其中，$\ket{\mathcal{G}^{i \alpha (j \beta)}}$ 表示在与键 $\ev{ik}(\ev{lj})$ 相邻的两个 plaquettes 上添加额外的 $\pi$ fluxes 到 $\mathcal{G}$ 上的状态，$E$ 是本征态 $\ket{\mathcal{G}} \ket{\mathcal{M}_{\mathcal{G}}}$ 的能量本征值。由于每个 plaquette 上的 $Z_2$ 通量是一个守恒量，因此可以清楚地看出，方程 (4.10) 中的关联为方程 (4.11,4.12) 中两种状态的重叠为零，除非自旋在相邻的位置上。即证明了动态自旋自旋关联具有

$$
S_{ij}^{\alpha \beta}(t) = 
\begin{cases}
g_{\ev{ij}_\alpha} (t) \delta_{\alpha,\beta} & \text{for } i,j\text{ nearest neighbours}\\
0 & \text{otherwise}
\end{cases}
$$
计算 $g_{ij}(0)$ 在任何本征态 $\ket{\mathcal{M}_\mathcal{G}}$ 中都是直截了当的。对于具有在所有平面上都是 unity 的守恒 $Z_2$ 荷的基态，键 $\ev{ij}_\alpha$ 的等时二自旋相关函数由解析表达式给出：
$$
\ev*{\sigma_i^\alpha \sigma_j^\beta}
\equiv S_{\ev{ij}_\alpha}^{\alpha \alpha}
= \frac{\sqrt{3}}{16 \pi^2}
\int_{\text{BZ}} \cos \theta(k_1, k_2) \dd{k_1}\dd{k_2}
$$

在这里，$\cos \theta(k_1, k_2) = \dfrac{\epsilon_k}{E_k}$，其中 $E_k = \sqrt{\epsilon_k^2 + \Delta_k^2}$，在布里渊区域内。$\epsilon_k = 2(J_x \cos k_1 + J_y \cos k_2 + J_z)$，$\Delta k = 2(J_x \sin k_1 + J_y \sin k_2)$，$k_1 = \vb*{k} \vdot \vb*{n}_1$，$k_2 = \vb*{k} \vdot \vb*{n}_2$，$\vb*{n}_{1,2} = \frac12 \vu*{e}_x \pm \frac{\sqrt{3}}{2} \vu*{e}_y$ 是沿 $x$ 和 $y$ 键的单位矢量。在点 $J_x = J_y = J_z$ 处，得到 $S^{\alpha \alpha}_{\ev{ij}_{\alpha}}(0) = −0.52$. 图 (4.3) 显示了最近邻 z−z 相关性在参数 $(J_x, J_y, J_z)$ 空间中的变化。
![[截图-1699811534547.png#C|图 4.3|300]]
为了计算ghijiα(t)，我们从方程(4.1)和(4.2)中替换σ。我们选择了一个规范，其中uhijiα = −1，意味着χ† hljiβ |Gi = χ† hikiβ |Gi = 0。我们注意到，在t = 0时强加的上述条件在所有时刻都持续存在，因为键上的费米子数是守恒的。然后我们有：
# 5. Kitaev 模型的量子纠缠研究


# 6. 二维 Kitaev 模型的 toric code 极限

# 7. Kitaev 模型在 Ising 微扰下的稳定性


在第二章中，我们已经看到Kitaev模型的精确解是可能的，因为最初的自旋哈密顿量被映射到描述马约拉纳费米子的最近邻居跳跃相互作用的非相互作用哈密顿量。耦合到跳跃矩阵单元的规范场是静态的。这两个事实使得马约拉纳费米子的原自旋哈密顿二次函数是完全可解的。在这一章中，我们初步地研究规范场的动力学。通过在原基塔耶夫模型的哈密顿量基础上加入适当的相互作用，使规范场具有动态性。当规范场不守恒时，哈密顿函数中的一个泛型项描述了四个马约拉纳费米子之间的相互作用。在Kitaev模型中，有许多可能的方法将这种动力学引入 $Z_2$ 规范场。达到这个目的的一种方法是在基塔夫哈密顿量中加入塞曼项，这已经在[^33]中讨论过了。结果表明，在原始基塔耶夫模型中加入这种相互作用会导致无间隙相获得间隙。但本研究主要是研究模型的拓扑性质，而不是规范场动力学。在这里，我们通过在基塔耶夫哈密顿量中加入一个最近邻居Ising相互作用，将动力学引入规范场。我们证明，根据伊辛相互作用的强度，哈密顿量描述了一个Z2规范场为静态(守恒)的自旋液体态和一个Z2规范场为动态的磁有序态。当我们改变伊辛相互作用的强度时，可以观察到这两个相之间的量子相变。

## 7.1. Kitaev-Ising 模型

K-I 模型的哈密顿量 $H_{\text{K-I}} = H_{\text{K}}+H_{\text{I}}$
$$
H_K = -J_\alpha \sum_{\alpha} \sigma_i^\alpha \sigma_j^\alpha
,\quad H_I = -\lambda \sum \sigma_i^z \sigma_j^z \tag{7.1}
$$
如果耦合常数 $\lambda$ 是正的，那么伊辛哈密顿量的耦合是铁磁的，否则就是反铁磁的。我们研究了这两种情况。让我们解释一下伊辛相互作用是如何引入规范场动力学的。我们知道Kitaev模型(即 $\lambda= 0$)包含了与每个蜂窝状晶格点阵 plaquette 相关联的守恒算子($B_p$) (Eq. 2.3)。可以很容易地看出，$B_p$ 与 $H_{K−I}$ 的 Ising 相互作用不对易。我们知道，当我们对自旋算符进行费米化时，$B_p$ 可以重新表示为与 plaquette $p$ 键相关的适当 $Z_2$ 规范场的乘积。我们将证明这个 $Z_2$ 规范场不再是守恒的，因为它们与由伊辛摄动导出的费米化相互作用项不对易.

## 7.2. 经典基态

在进一步研究由 $H_{K−I}$ 得到的费米哈密顿量之前，我们首先讨论哈密顿量可能的经典基态(7.1)，以便我们能够描述这些经典极小值周围适当的平均场分析。对于 $λ$ 正 (铁磁Ising相互作用)，经典极小值是通过将所有自旋在正 $z$ 方向或负 $z$ 方向对齐来获得的[^83]。对于这种构型，每单元胞的经典能量密度为:
$$
E_{FM} = -(3\lambda+1) \tag{7.2}
$$

当 $λ$ 为负值时，存在两个经典的极小值，这两个极小值取决于 $J$ 和 $λ$ 的相对大小。在图 (7.1) 中，我们画出了这两个经典构型。左边的是 dimer 状态. 右边的是我们熟悉的 Neel 态。
![[截图-1700722391283.png#C|dad|400]]

**图 7.1.** 两种不同的经典构型在不同参数下最小化经典能量密度。当λ≤J时，二聚体状态使经典能量最小化。当λ≥J时，尼尔态产生最小的经典能量密度。

这两种构型的经典能量密度由
$$
E_{\text{Dimer}} = -J-\lambda;\quad E_{\text{Neel}}=-3\lambda+J
$$
$$
E_{\text{Dimer}}-E_{\text{Neel}} = 2(\lambda-J)
$$
由此可见，λ≤J 时，经典极小值对应的是 dimer 状态.

![[截图-1700722667371.png#C|Fig. 7.2|400]]

在讨论了使 $H_{K−I}$ 最小化的自旋的经典构型之后，我们继续使用公式 (7.1) 中给出的哈密顿量。我们将围绕这些经典构型展开适当的平均场分析。现在我们讨论由式 (7.1) 给出的自旋哈密顿量的费米化形式。

## 7.3. Kitaev-Ising 模型的费米化

根据 Kitaev 的马约阿纳费米子化[^33]，我们用马约拉纳费米子的适当组合替换spin $1/2$ 算子，即 $\sigma_i^\alpha = \mi c_i b_i^\alpha$，则有
$$
\begin{align}
H_K &= \sum_x J_x \mi b_i^x b_j^x \mi c_i c_j
+\sum_y J_y \mi b_i^y b_j^y \mi c_i c_j
+\sum_z J_z \mi b_i^z b_j^z \mi c_i c_j \tag{7.5}\\
H_I &= \sum_{\text{all link}} \mi b_i^z b_j^z \mi c_i c_j \tag{7.6}
\end{align}
$$

$\mi b_i^x b_j^x$ 和 $\mi b_i^y b_j^y$ 作为 $x, y$ link 上的 $Z_2$ 规范场, 仍然和哈密顿对易. 但是 $\mi b_i^z b_j^z$ 不对易. 应用 JW formalism, 令 x, y 的规范场为 1. 得到如下哈密顿
$$
\begin{align}
H_K &= \sum_x J_x \mi c_i c_j
+\sum_y J_y \mi c_i c_j
+\sum_z J_z \mi b_i^z b_j^z \mi c_i c_j \tag{7.7}\\
H_I &= \sum_{\text{all link}} \mi b_i^z b_j^z \mi c_i c_j \tag{7.8}
\end{align}
$$

此时 $B_p$ 的表达式
$$
B_p = \mi b_{1,i}^z b_{2,i}^z \mi b_{1,j}^z b_{2,j}^z
$$
其中 1, 2 表示不同的 sublattice; i, j 表示一个 plaquette 的两条 $z$-bonds.

## 7.4. 平均场分解

写出哈密顿量的一个一般项的[[平均场分解]] (mean field decomposition)
$$
\begin{align}
\mi b_i^z b_j^z \mi c_ic_j
=& \ev{\mi b_i^z b_j^z} \mi c_i c_j
+ \mi b_i^z b_j^z \ev{\mi c_i c_j}\\
&- \ev{\mi c_i b_i^z} \mi c_j b_j^z - \ev{\mi c_j b_j^z} \mi c_i b_i^z\\
&- \ev{\mi b_i^z b_j^z} \ev{\mi c_ic_j}+\ev{\mi c_ib_i^z} \ev{\mi c_jb_j^z}
\end{align}\tag{7.10}
$$
引入序参量
$$
\begin{align}
\ev{\mi c_i b_i^z} &= \Delta_z^1 \tag{7.11}\\
\ev{\mi c_j b_j^z} &= \Delta_z^2 \tag{7.12}\\
\ev{\mi b_i^z b_j^z} &= \gamma_\alpha, \quad \alpha = x,y,z \tag{7.13}\\
\ev{\mi c_i c_j} &= \gamma_{0\alpha},\quad \alpha = x,y,z \tag{7.14}
\end{align}
$$
我们观察到，通过进行这种平均场分解，我们将哈密顿量简化为一个包含 Majorana 费米子算子的二次项的哈密顿量。$\gamma_\alpha$ 可以用前面提到的规范场来识别（仅对Kitaev哈密顿量守恒）。项 $\Delta_z^1$ 只不过是 $\ev{\sigma_i^1}$，因此测量系统的*自旋序*。这里索引“1”和“2”指的是*子晶格*索引。根据我们问题的对称性，我们期望 $\gamma_x = \gamma_y$，我们称之为 $\gamma_h$。类似地，我们将 $\gamma_{0x} = \gamma_{0y} = \gamma_{0h}$. 

$\Delta_z^1$ 的非零值意味着由于伊辛相互作用而出现自旋阶。另一方面，$\gamma_\alpha$ 的 non-vanishing value 是与纯 Kitaev 模型相关的 residual 守恒 $Z_2$ 规范场的度量。将方程（7.10）插入方程（7.7）中，在方程（7.8）中，






# 8. 三维 Kitaev 模型

# 9. 三维 Kitaev 模型的 toric code 极限

# 10. 总结与讨论

# A. 针对开放边界条件的 J-W 变换

# B. 规范固定算法和 J-W 规范

# C. 自旋-自旋相关注释

## C.1. 物理子空间中的相关函数

在第四章中，我们推导了 Kitaev 模型的自旋-自旋关联。然而，我们在 Kitaev [33]采用的费米化过程中工作。我们已经看到这个费米化过程扩大了局部希尔伯特空间维数。但是我们认为，由于自旋算符是规范不变的，在扩大的希尔伯特空间中得到的结果与在物理希尔伯特空间中应该得到的结果是一致的。在本附录中，我们将对此进行解释。我们已经看到在等式第一章中定义的算符 $D_i$ 在位置 $i$ 处进行如下操作
$$
\begin{align}
D_i
\end{align}
$$

# D. 三维 KM 谱分析

# E. Kitaev 模型 toric code 极限中的有效哈密顿量

# F. Kitaev 模型的摄动理论


[^32]: [[通过任意子的可容错量子计算]]
[^33]: [[精确可解模型及其他中的任意子_Kitaev|Anyons in an exactly solved model and beyond]]


