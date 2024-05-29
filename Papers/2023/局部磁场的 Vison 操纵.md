---
tags:
  - 论文
created: 2023-10-20 09:14:33
aliases:
  - Vison manipulation with local magnetic fields
DOI: https://doi.org/10.48550/arXiv.2306.11092
author:
  - "[[Haoran Wang]]"
  - "[[Alessandro Principi]]"
original title: Vison manipulation with local magnetic fields
year: "2023"
---
# Abstract

最近，量子自旋液体中出现了对非阿贝尔任子的浓厚兴趣，这是由于在这些量子相附近发现了各种材料。它们的任子激发对拓扑量子计算有潜在应用，但要设计具有降低污染的逻辑操作，需要开发能够忠实地创建、移动和读取这种准粒子的协议。在本文中，我们提出了一种用于操作小幅均匀磁场扰动下的铁磁和反铁磁 Kitaev 模型的 $Z_2$ 通量 visons 的协议。我们的设计采用局部驱动磁场，可以实现在模型的 $A_z$ 和 $B$ 相中生成和移位 flux pairs 的高概率。

实现大规模量子计算的主要挑战之一是量子状态的退相干（decoherence）[^1][^2][^3][^4][^5]。虽然已经设计了纠错编码[^6][^7][^8][^9][^10][^11][^12]，但通常需要在多个物理量子比特上复制信息以编码一个单一的逻辑量子比特。这个事实阻碍了量子计算架构的可扩展性。因此，开发能够自身设计抵抗噪声的量子比特是非常值得期待的。

拓扑量子计算[^13][^14][^15][^16][^17]提供了解决退相干问题的潜在解决方案。在某些具有拓扑序的量子系统中，例如在Kitaev环形码[^14]中，希尔伯特空间的基态流形分裂为不同独立的部分[^18]。为了从一个部分过渡到另一个部分，必须应用一系列算符链，其长度与系统的维度成比例。因此，在宏观系统中，不同部分中的量子态的量子叠加天生受到保护而避免退相干。实际上，环境噪声很难产生足够长（且非局域）的算符链，从而无法不可逆地损害系统的量子态。在这种计算方案中，量子态的操作是通过编织激发[^19]来实现的，这些激发通常是任子（即它们既不表现为玻色子也不表现为费米子）。当将其中一个粒子绕另一个粒子移动时，系统的状态在基态流形中进行了幺正旋转，并等效地应用了一个量子门。因此，可以通过编织任子激发来优雅地设计量子算法。

Kitaev模型[^20][^21][^22][^23][^24]是一个量子自旋液体的模型，与环形码[^20]是亲属关系，它为生成和操作阿贝尔和非阿贝尔任子[^20][^25]提供了一个平台。这些任子具有从每个晶格点的自旋变量的分数化中产生的有效规范场的 flux-like 激发形式。在*没有外部磁场*的情况下，这种激发是*守恒*的。在这里，我们研究了在 Kitaev 模型的两个不同相中通过*局部磁场*的应用生成这种 flux（也称为涡旋或visons）的过程。我们发现在这两种相中，都有可能以相当高的 fidelity 来生成和 displace 涡旋。因此，我们的工作为在拓扑有序系统中执行量子计算的算法开发铺平了道路，在这些系统中，visons 可以通过 local scanning techniques 生成和移位。

# 1. 模型

我们对存在均匀（扰动性）磁场 $\vb*{h}$ 的情况下的 Kitaev 模型进行了数值研究，这允许激发获得非阿贝尔任子统计。系统的哈密顿量为：
$$
\hat{H}_0 = \hat{H}_K + \hat{H}_h
$$
其中

$$
\hat{H}_K = \sum_{\ev{j,k}} J_{\alpha_{jk}}\sigma_j^{\alpha_{jk}}\sigma_k^{\alpha_{jk}} \tag{1}
$$

^1fd5e5


为定义在蜂窝格上的 Kitaev 模型的哈密顿量[^20]，$\hat{H}_h = \sum_j \vb*{h} \vdot \vb*{\sigma}_j$ 则表示与外部磁场的 Zeeman coupling. 在这些方程中，$\sigma_i^\alpha$ 表示作用在位于 $i$ 号位置的自旋 $1/2$ 希尔伯特空间上的 $\alpha$-th Pauli 矩阵。在方程 (1) 中，$\ev{j,k}$ 表示最近邻键，而 $\alpha_{jk}$ 则根据键 $\ev{j,k}$ 的方向取值为 $x$, $y$ 或 $z$ [^20]. 为了使模型尽可能一般化，Ising 型耦合 $J_{\alpha_{jk}}$ 的大小也允许取决于键的方向。在这之后，我们将能量按 $J$ 进行 scale（在下文定义），并设置 $\hs = 1$. 因此，时间以 $J^{-1}$ 为单位。

这个模型可以通过将 Pauli 矩阵映射到 Majorana 算符来精确求解。就像在[^20]中一样，我们引入了每个晶格点 $j$ 处的四个 Majorana 算符 $b^x_j, b^y_j, b^z_j$ 和 $c_j$，使得 $\sigma^\alpha_j = \mi b^\alpha_j c_j$。在 Majorana 表示中，Kitaev 哈密顿量变为：
$$
\hat{H}_K = \sum_{jk} J_{\alpha_{jk}} b_j^{\alpha_{jk}}b_k^{\alpha_{jk}}c_jc_k \tag{2}
$$



马约拉纳表示的希尔伯特空间, 是原始 Kitaev 模型的希尔伯特空间的两倍[^20]。通过使用合适的投影算符[^20]来移除非物理希尔伯特空间中任何状态的分量。为了定义它，我们引入了规范变换算符 $D_j = b^x_j b^y_j b^z_j c_j$，它满足物理状态的 $D_j = 1$ (与 $-\mi \sigma_j^x \sigma_j^y \sigma_j^z$ 相一致) 和非物理状态的 $D_j = -1$。所寻找的投影被构造为 $P = \prod_j(1+D_j)/2$，其中乘积在所有格点 $j$ 上.

公式 [[#^1fd5e5]] 中的 Kitaev Hamiltonian 拥有一组守恒量 $W_p$, 它被定义为每个 plaquette $p$。在 Majorana 表示中，它们是 $W_p = \prod_{\ev{j,k}} u_{jk}^{\alpha_{jk}}$，其中 $u_{jk}^{\alpha_{jk}} = \mi b_j^{\alpha_{jk}} b_k^{\alpha_{jk}}$，$\ev{j,k}$ 是 plaquette $p$ 的六边，并沿逆时针方向循环。根据 Lieb 定理[^26]，基塔耶夫模型的基态必须满足 $W_p = 1$，这一状态称为“无通量”。在本文中，当 $i (j)$ 属于 $A (B)$ 子格时，通过设 $u^{\alpha_{ij}}_{ij} = 1$ 来定义这种状态。当 $W_p =-1$ 时，称 plaquette $p$ be threaded by one flux.

在 Kitaev 模型中，自旋算符是 $\sigma_j^\alpha$, 而键算符是 $u_{jk}^\alpha$. 因此，将算符 $\sigma_j^\alpha$ 应用于基态，会在共享键合 $\ev{j,k}$ 的两个 plaquettes 中产生两个涡流。这表明，可以应用局部(塞曼)磁场来驱动系统脱离平衡，并操纵涡旋。因此，我们用含时哈密顿量对系统进行扰动

$$
\hat{V}(t) = \sum_{j} \delta \vb*{h}_j(t) \vdot \vb*{\sigma}_j \tag{3}
$$


其中 $\delta \vb*{h}_j(t)$ 在 $\vu*{e}_z$ 方向 (注意，它的大小相对于 $J$ 不一定小)。

# 2. 平均场近似

磁场 $\vb*{h}$ 破坏了模型的精确可解性，即对于所有的 $p$, $\hat{H}_0$ 的基态不需要满足 $W_p = 1$. 因此，为了确定在 [[#^67397e|(3)]] 下的基态及其时间演化，我们借助于 $\hat{H}_K$ 的平均场解耦。我们将 [[#^fd87b9]] 中的四个算子项进行解耦，使用 Wick 定理 (形式化) 作为
$$
b_A^\alpha b_B^\alpha c_A c_B = \ev{b_A^\alpha b_B^\alpha} c_Ac_B
- \ev{b_A^\alpha c_A} b_B^\alpha c_B-\ev{b_B^\alpha c_B}b_A^\alpha c_A+ \ev{b_A^\alpha c_B} b_B^\alpha c_A+\ev{b_B^\alpha c_A}b_A^\alpha c_B
$$

其中我们使用了子格指标 $A$, $B$ 来表示给定 link 的两个位置。我们的处理方法和[^27]相似，这里，$\alpha$ 是沿着键耦合的自旋成分。这样，哈密顿函数 $\hat{H}_0$ 在马约拉纳费米子 $\hat{H}_{MF}=\sum H^{ij}_{MF}m_im_j$ 中被简化成二次型，其中矩阵 $H_{MF}$ 既依赖于初始哈密顿函数的值，也依赖于平均场的值。为了使我们的表示法更简洁，我们用 $\qty{m_j}$ 表示所有 $b_i$ 和 $c_i$ 马约拉纳费米子的集合 (注意这里的 $j$ 不像以前那样表示晶格点)。

取均匀磁场 $\vb*{h} = h \vu*{n}$，其中 $\vu*{n} =(\vu*{e}_x + \vu*{e}_y + \vu*{e}_z)/\sqrt{3}$. 在很大的 $h$ 值下，我们期望自旋在 $\vu*{n}$ 方向极化，系统不再处于自旋液相。我们通过求解平衡平均场自一致性方程来确定, 补充资料[^28]中的这种情况何时发生，并计算 $\vb*{h}$ 产生的自旋极化。为了避免系统极化，在接下来的内容中，我们将使用 $h$ 的小值。

一旦平衡平均场被确定，它们的时间演化是通过求解 $M_{jk}(t) = \mel*{\psi(t)}{m_jm_k}{\psi(t)}$ 的运动方程找到的，其中 $\dd{M}/\dd{t} = 4 \mi \comm{H_{MF}+V(t)}{M}$，其中 $V_{ij}(t)$ 是驱动哈密顿函数的矩阵表示: $\hat{V}(t) = \sum_{ij} V_{ij}(t) m_im_j$.

在接下来的几节中，我们将介绍一种使用*局部*和*时间相关*的 Zeeman 场 $\delta \vb*{h}_j(t)$ 来生成和操作Kitaev模型中通量的 protocol。我们考虑一个包含 64 个单元格的晶格，并采用周期性边界条件。我们研究 Kitaev 模型的 $A_z$ 相和 $B$ 相，分别考虑铁磁（FM）和反铁磁（AFM）的耦合情况。$A_z$ 相具有能隙，当 $\abs{J_z} > \abs{J_x} + \abs{J_y}$ 时出现。在没有外部磁场的情况下，$A_z$ 相的激发是阿贝尔任意子[^20]。由于能隙的大小与 $J_z$ 的量级相近，一个小磁场 $h \ll J_z$ 不应该关闭它。因此，我们得出结论，在小磁场存在的情况下，$A_z$ 相中的激发仍然是阿贝尔任意子。$B$ 相是无间隙的，当 $\abs{J_x}$、$\abs{J_y}$ 和 $\abs{J_z}$ 都满足三角不等式 $J_\alpha < J_\beta + J_\gamma$ 时存在。这一相位的激发是非阿贝尔任意子[^20]。我们设置 $B$ 相的参数为 $J_x = J_y = J_z = J$，而 $A_z$ 相的参数为 $J_x = J_y = J$，$J_z = 2.1J$，其中 $J$ 可以是铁磁（FM），即 $J < 0$，也可以是反铁磁（AFM），即 $J > 0$.



# 3. 铁磁模型中的通量动力学

现在我们展示了 FM 模型的 $A_z$ 和 $B$ 相中的磁通生成和位移。

## 3.1. $B$ 相
我们从 $B$ 相开始。我们选择均匀磁场为 $h = 0.01J$，并且 $\abs{ \delta \vb*{h}_j(t)} = 0.5J$。参考图 1，我们现在展示一个在 $p_1$ 和 $p_7$ plaquettes 中创建一对涡旋的 protocol.

![[截图-1697915725872.png#C|图 1 基塔耶夫模型和通量操纵 protocol|400]]
```ad-info
title: 图 1
蜂窝状晶格的键分为三种类型，分别为 $x$、$y$ 和 $z$，分别用绿色、红色和蓝色表示. 黑白圆点是 $A (B)$ 子格的位置，表示为 $j_l(k_l)$. Sites 通过 bonds 连接，链接用深灰色突出显示。Flux 位于在 plaquette 上，标记为 $p_l$. 在 $t = 0$ 时，$z$ 方向的磁场同时作用于 $j_1$ 和 $k_1$，并在时间 $t$ 后关闭。我们在 $j_l$ 和 $k_l$ 重复这个过程，对于 $l= 2, \cdots, 6$. Protocol 结束后，$p_1$ 和 $p_7$ 中创建了一对通量.
```

我们回忆一下，在图 1 中突出显示的六个键的键算符的平均值，即 $u_l = u_{j_lk_l}$，其中 $l = 1, \cdots, 6$，在无磁通的情况下都等于负一，因此 $W_p$ 在任何地方都是正的。
因此，我们需要翻转所有六个键 $u_1, u_2, \cdots, u_6$，以在 string 的末端 plaquettes 上创建涡旋对（$W_p$ 为负的两个 plaquettes）。我们用于实现涡旋创建的协议可以总结如下：首先，我们打开一个驱动场 $\delta \vb*{h}_l$，其符号相同，作用于两个自旋位点 $l = j_1$ 和 $l=k_1$，结果使键算符 $u_1$ 的平均值增加。在键算符 $u_1$ 的平均值达到最大值的时间 $T$ 后，我们关闭驱动磁场。对于我们的参数，$T = 1.8J^{-1}$. 为了移动通量，然后我们在两个位点 $l = j_2$ 和 $l=k_2$ 上重复该过程，这将导致键算符 $u_2$ 的值（部分）翻转。重复该过程以处理所有其他键，最终我们在 $p_1$ 和 $p_7$ 处创建了一个通量对。

这一 protocol 的结果如图 2(a)(b) 所示。![[截图-1697922345526.png#R|图 2 通量操作协议应用于 FM 模型的 B 相|350]] ^351076

```ad-info
title: 图 2
- (a) 在 $t = T$ 时的通量配置。应用于键 $B_1$（参见图 1）上的磁场部分翻转了平面 $p_1$ 和 $p_2$ 中的通量。

- (b) 协议结束时（$t = 20J^{-1}$）的通量配置。

- (c) 键变量 $u_l$ 的时间演化。

- (d) 不同均匀场 $h$ 值下 $u_1$ 的时间演化。驱动场应用于位点 $k_1$ 和 $j_1$，并在每个曲线达到最大值时关闭。
```

在图 2(a) 中，我们显示应用驱动场 $\delta \vb*{h}_{j_1}$ 和 $\delta \vb*{h}_{k_1}$ 在时间 $T$ 内已经翻转了 $u_1$ 的值，尽管没有完全翻转。对于上面提到的参数，我们得到 $u_1 \approx 0.5$，对应于 $W_{p_1} = W_{p_2} = -0.5$. 这相当于生成一个状态，每个平面 $p$ 中都处于涡旋和非涡旋状态的叠加态，概率为 $(1 - W_p)/2 \approx 0.75$ 来生成一对涡旋，概率为 $(1 + W_p)/2 \approx 0.25$ 没有涡旋.

现在我们研究了通量对随均匀场 $h$ 的变化的稳定性。我们仅在位点 $l = j_1$ 和 $l = k_1$ 上应用局部驱动场 $\delta h_l = 0.5J$，并在 $u_1$ 达到最大值时关闭它。我们在图 2(d) 中显示了 $u_1$ 在不同时间的演化。在没有场 $h$ 的情况下，通量是由未受扰动的 Kitaev 模型的 $Z_2$ 对称性保护的，这可以从图 2(d) 中的直线看出。对于有限的 $h$，我们发现 $u_1$ 的振幅随 $h$ 增加而振荡。对于 $h = 0.02J$，振荡似乎是正弦的。在更大的 $h$ 下，例如 $h = 0.04J$，通量对似乎不再稳定。

在附加信息[^28]中，我们还展示了键变量 $u_1$ 达到的最大值在 $h$ 较大的情况下变得更小。尽管需要均匀场来获得非阿贝耳任意子激发，但我们的结果表明，应该尽量将 $h$ 保持在较小的值，以便以高概率生成和保持稳定的通量。

## 3.2. $A_z$ 相

然后，我们将相同的协议应用于在 FM 模型的 $A_z$ 相中创建一对通量。在这种情况下，我们使用参数 $T = 4.1J^{-1}$, $h = 0.005J$ 和 $\delta h = 0.2J$. 结果如图 3(a)-(b) 所示。![[截图-1697945716434.png#R|图 3 通量操作协议应用于 FM 模型的 Az 相|350]]

```ad-info
title: 图 3

图中显示了在不同时间点的通量配置。

- (a) 在 $t = T$ 时的通量配置。应用于键 $B_1$（参见图 1）的磁场几乎完全翻转了平面 $p_1$ 和 $p_2$ 中的通量。

- (b) 协议结束时（$t = 30J^{-1}$）的通量配置。

- (c) 键变量 $u_l$ 的时间演化。

- (d) 不同均匀场 $h$ 值下 $u_1$ 的时间演化。驱动场应用于位点 $k_1$ 和 $j_1$，并在每个曲线达到最大值时关闭.

```


在图 3(a) 中，我们展示了从均匀无通量的配置开始，应用驱动场 $\delta h_{j_1}$ 和 $\delta h_{k_1}$ 在时间 $T$ 内，$u_1$ 的值几乎完全翻转。对于所使用的参数，我们可以达到 $u_1 \approx 0.97$，对应于以概率 $\approx 1$ 在 $p_1$ 和 $p_2$ 中生成通量。重复这个过程对于 string 中的所有其他键，我们可以实现 $u_l \approx 1$，对于 $l =2, \cdots$. 因此，在这种情况下，中间的 plaquettes 几乎没有通量，通量几乎完全局限在 string 的末端 plaquette. 拥有通量的概率分别约为 $\approx 0.93$ 和 $\approx 0.97$，对于第一个和最后一个 plaquette. 我们创建的涡旋非常稳定，正如图 3(c) 中所示的 $u_l$ 的时间演化呈现出平稳状态。显然，我们的协议在 $A_z$ 相中的效果比 $B$ 相好得多.

接下来，我们分析 $A_z$ 相中通量对的稳定性。与之前一样，我们只在位点 $l = j_1$ 和 $l = k_1$ 应用局部驱动场 $\delta h_l = 0.2J$，并研究 $u_1$ 的时间演化。在图 3(d) 中，我们展示了在关闭局部驱动场 $\delta h$ 并达到最大值后，不同 $h$ 值下 $u_1$ 的时间演化。在没有场 $h$ 的情况下，通量再次受到未受扰动的 Kitaev 模型的 $Z_2$ 对称性的保护。另一方面，对于有限的 $h$，我们发现键 $u_1$ 随着更大的 $h$ 而振荡频率增加。这些振荡似乎对所有的 $h$ 都是正弦的，振幅几乎不依赖于 $h$. 在 $h = 0.005J$ 的情况下，从模式来看，很可能在比我们的模拟所提供的更长时间后也会达到 $-1$.


# 4. 反铁磁模型中的通量动力学

在 AFM 模型中，我们发现上述协议需要进行修改。我们关注 $B$ 相，因为对 $A_z$ 相的修改类似。如图 4 所示，如果场 $\delta h_l$ 在属于不同子晶格的两个位点 $l = j_1$ 和 $l = k_1$ 上取相同的值，那么键操作符 $u_1$ 的值将非常接近 $-1$. 因此，不会产生通量。然而，如果驱动磁场在两个子晶格上取相反的符号，那么我们发现 $u_1$ 的时间演化几乎与铁磁模型的时间演化完全相同。这并非偶然，而是由于模型中的对称性，使我们能够将在 FM 模型中找到的结果几乎完美地转化为 AFM 模型。![[截图-1697948937779.png#R|图 4|500]]

```ad-info
title: 图 4
恒定驱动场 $\abs{\delta h_j} = 0.5J$ 下 $u_1$ 的时间演化。FM 的 $\delta h_A = \delta h_B$ 与 AFM 的 $\delta h_A =-\delta h_B$ 几乎相同。
```

^e52a8e

为了理解这种行为，我们定义算符 $O_A = \prod_{j \in A} \theta_j$, 其中 $\theta_j \equiv b^x_j b^y_j b^z_j$，并且这个乘积只取 $A$ 子格的位置。请注意，因为 $\theta_j$ 是相互反交换的，乘积中的项的顺序必须在整个计算中保持固定。算符 $O_A$ 与子晶格中的自旋是反交换的，但与 $B$ 子晶格中的自旋是交换的。由于 $O_A$ 是*幺正*的，我们可以使用它将每个可观察 $\hat{X}$ 转换为 $\hat{X} \to O_A^\dagger \hat{X} O_A$，并且每个状态 $\ket{\psi}$ 转换为 $\ket{\psi} \to O_A^\dagger \ket{\psi}$. 特别地，哈密顿函数变换为

$$
O_A^\dagger \hat{H}_K O_A = -\hat{H}_K
$$
因此OA将铁磁基塔耶夫模型转化为反铁磁模型，反之亦然。将驱动哈密顿量 [[#^67397e]] 转化为
$$
O_A^\dagger V O_A = \sum_i (-\delta h_{i,A}\sigma_{i,A} + \delta_{i,B} \sigma_{i,B})
$$
这里 $i$ 表示的是两个子格的自旋所属的单元格。因此，算符 $O_A$ 将作用于一个 $A$ 子晶格点磁场 $h_{i,A}$ 的符号颠倒，同时保持 $B$ 子晶格点的磁场不变。

因此，在较小的均匀磁场 $h$ 和驱动磁场 $\delta h = \delta h_A = \delta h_B$ 时 (如[[#^e52a8e|图 4]] 所示)，将 FM 模型映射为 $h$ 和 $\delta h$ 交错的 AFM 模型。这一事实表明，我们对 FM 模型的结果可以在经过少量修改的情况下应用到 AFM 模型中，如图 4 所示。当 $\delta h_A =-\delta h_B$ 时，FM 模型与 AFM 模型的差异很小，这是由于两个子点中均匀场 $h$ 的符号保持一致所致。


# 5. 总结

我们通过平均场和精确对角化技术的组合，对 Kitaev 模型在存在均匀和局部驱动磁场的情况进行了数值研究。我们研究了随时间变化的局部驱动磁场对 Kitaev 模型的影响，采用了动力学均场方法（均场的动力学由施加的磁场生成）。我们证明了这种磁场可以用于在 FM 和 AFM  Kitaev 模型中创建和移动涡旋。我们找到了此类过程的最佳参数，并讨论了所产生的通量的稳定性和质量。我们还表明FM和AFM Kitaev模型之间存在一一对应关系。

我们的涡旋创建和操作协议依赖于施加在*非常小的空间区域的磁场*。在真实实验中，实现这种局部化可能会稍有挑战。我们在这里不讨论这个问题，因为本研究的重点是在*原则上*使用局部场生成通量对。虽然这是我们工作的一个局限，将在未来进行更详细的分析，但我们强调我们的工作可能适用于出现在*扭曲系统*等系统中的量子相。在这些系统中，自旋局域化的典型尺度要大得多，允许减轻所施加场的极端局部性要求。

这份手稿在准备过程中，一项相关研究[^29]已在arXiv上公开。在那里，研究了在局部磁场存在下的“扩展Kitaev模型”的动力学。引用[^29]中的模型在微扰区域 $\abs{h} \ll \abs{J}$ 中近似了均匀磁场的影响，使用了一个三自旋项。后者引起了 $c$-Majorana 费米子的 Haldane 型的次最近邻跃迁项。因此，它负责在 $B$ 相中开启能隙以及边缘 Majorana 粒子的出现。

我们的模型和引用[^29]中研究的模型之间存在重要差异，可以追溯到后者的近似性质。在引用[^29]的模型中，发现了一个阈值行为，即如果局部磁场高于某个值，则通量可以以概率 1 的方式被创建。在我们的模型中，我们以非微扰方式处理均匀磁场，最多只能以概率 $\approx 0.75$ 生成通量。此外，在我们的模型中，均匀场 $\vb*{h}$ 破坏了通量的守恒性，我们展示了在足够大的场下通量实际上非常不稳定。然而，在引用[^29]的模型中，通量在构建时是守恒的。此外，他们选择的均匀磁场值（$\kappa = 0.05 J$）对应于自旋极化非常大（$\approx 0.8$，参见[^28]）。这引发了扩展模型作为 Kitaev 模型在均匀磁场中的良好近似的有效性问题。实际上，这种模型依赖于在无通量区域中微扰地构建 effective Hamiltonian，其中自旋极化为零。

# 6. 附录 自旋极化

为了找到在均场近似内处理的 Hamiltonian $H_0$ 的基态，我们推导并解决静态均场自洽方程如下。首先，我们对 $\ev{m_im_j}$ 假定一个初始值，并对 Hamiltonian $\hat{H}_{MF}$ 进行对角化。我们得到 $\hat{H}_{MF} = \sum_k \epsilon_k a_k^\dagger a_k$, 其中 $k$ 标记了系统的本征模式，而 $m_i$ 与 $a_k$ 之间的关系如下：$m_i = S_{ik}a_k$. 这里，$S_{ik}$ 是一个幺正矩阵。由于我们正在寻找最低能量状态，只要 $\epsilon_k < 0$，平均值 $\ev*{a_k^\dagger a_k}$ 等于 $1$，否则为零。因此，我们得到 $\ev{m_im_j} = \sum_{\epsilon_k < 0} S_{ik}^* S_{jk}$. 这为我们提供了均场的新猜测，我们将其代入 $\hat{H}_{MF}$. 我们重复这个过程直到收敛。当两个连续步骤的平均值之间的差异的绝对值之和低于 $10^{-6}$ 时，我们停止迭代。

磁场方向上的自旋极化 $\ev*{\vb*{\sigma} \vdot \hat{\vb*{n}}}$，对于 FM/AFM 模型的 $B$ 相如图5(a)/(b)所示。在图5(c)和(d)中，我们分别展示了 FM 和 AFM 模型的通量算子 $W_p$ 的平均值。在这两种情况下，$W_p$ 预计会趋近于零，因为在高磁场下，在任何六边形的格子中有一个或没有涡旋的可能性相等。![[截图-1698065579457.png#R|图 5|300]]

```ad-info
title: 图 5
- Panel (a): $FM$ 模型中 $B$ 相沿外部磁场方向的自旋极化。 

- Panel (b): AFM 模型中与 Panel (a) 相同，但存在明显的相变点，发生在 $h \approx 0.85$.

- Panel (c): FM 模型中 $B$ 相的通量算子平均值 $\ev{W_p}$ 随磁场 $h$ 的变化。 

- Panel (d): AFM 模型中与 Panel (c) 相同，但存在明显的相变点，发生在 $h \approx 0.85$. 在这两种情况下，$\ev{W_p}$ 与 $p$ 无关，因为系统具有周期性。
```


类似地，图 6(a)/(b) 显示了 FM/AFM 模型的 $A_z$ 相中的 $\ev*{\vb*{\sigma} \vdot \vu*{n}}$，而图 6(c)/(d) 显示了 FM/AFM 模型的 $W_p$ 的平均值。在 FM 模型中，无论是在 $B$ 相还是 $A_z$ 相，我们发现自旋极化都平稳上升，只有在无限大磁场的极限情况下才趋近于 1. 在这两种情况下，我们没有找到明显的相变点。然而，对于 $B$ 相，自旋极化是在 $\vu*{n}$ 方向，而对于 $A_z$ 相，它主要是在 $z$ 方向，$x$、$y$ 平面的分量远小于 $\ev{\sigma^z}$. ![[截图-1698066466614.png#R|图 6|350]]

```ad-info
title: 图 6
Panel (a): FM 模型中 $A_z$ 相沿外部磁场方向的自旋极化。

Panel (b): AFM 模型中与 Panel (a)相同，但在 $h \approx 1J$ 发生明显的相变。

Panel (c): FM模型中 $A_z$ 相的通量算子平均值 $\ev{W}_p$ 随磁场 $h$ 的变化。

Panel (d): AFM 模型中与 Panel (c) 相同，但在 $h \approx 1J$ 发生明显的相变。在这两种情况下，$\ev{W_p}$ 与 $p$ 无关，因为系统具有周期性。

```

此外，在 $A_z$ 相中，自旋极化 $\ev{\sigma^z}$ 上升得更快，大约在 $h \approx 0.03J$ 时接近 $0.8$，而在 $B$ 相中，需要 $h \approx 0.2J$ 才能达到 $\ev*{\vb*{\sigma} \vdot \vu*{n}} \approx 0.8$. $B$ 相的结果与Ref. [^30]存在分歧，后者使用密度矩阵重整化群方法，在 $h \approx 0.085J$ 附近发现了磁化的一阶导数奇点。我们将这归因于均场方法的局限性。然而，与Ref. [^30]一致，我们发现在这两种情况下，$W_p$ 平滑地趋向于零。在图 5(c) 和Ref. [^30]中，两条曲线都显示了最初是平坦的区域，$W_p$ 变化不大，然后急剧下降，最终在无限大的磁场下平滑趋于零。这些对比结果表明，尽管平均场近似在描述某些热力学量特性方面存在限制，但它能够捕捉旋涡的一般行为，从而增强了正文研究的可信度。

与之前的情况不同，在 AFM 模型中，我们发现在 $B$ 相和 $A_z$ 相中都存在明显的相变迹象。在 $B$ 相中，当 $h$ 约为 $0.85J$ 时，自旋极化出现不连续跃变，如图 5(b) 所示。在相同的临界磁场下，平均通量 $W_p$ 精确消失，并在更高的磁场下保持为零，如图 5(d) 所示。在 $A_z$ 相中，自旋极化在 $h$ 约为 $1J$ 时出现跃变，尽管不太明显，如图 6(b) 所示。相同的临界点在图 6(d) 中更容易识别，显示平均通量 $W_p$ 在h约为 $1J$ 时明显消失，并在更高的磁场下保持为零。

在这里，我们研究了实现通量创建的最佳均匀场 $h$ 的值。在 $B$ 相中，我们仅在 $l = j_1$ 和 $l = k_1$ 的位置施加局部驱动场 $\delta h_l = 0.5J$，并研究了不同均匀场 $h$ 下的时间演化。从中，我们计算了键算子 $u_1$ 随时间（在给定的均匀场 $h$ 下）达到的最大值。我们发现，在 $h = 0$ 时 $u_\text{max}$ 最大，如图 7(a) 所示。这进一步证明，最好将均匀磁场保持得尽可能小。![[截图-1698071508347.png#R|图 7|400]]

```ad-info
title: 图 7
在局部磁场 $\delta h$ 在自旋位点 $k_1$ 和 $j_1$（参见正文中的图 1）上进行急剧变化时，$u_1$ 达到的最大值，对于不同的 $h$ 值.

- Panel (a) FM 模型的 $B$ 相 

- Panel (b) FM 模型的 $A_z$ 相
```


在 $A_z$ 相中，我们仅在 $l=j_1$ 和 $l = k_1$ 的位置施加局部驱动场 $\delta h_l = 0.2J$. 使用与 $B$ 相相同的过程，我们发现 $u_\text{max}$ 随 $h$ 稳步减小，如图 7(b) 所示。因此，在这种情况下，最佳的磁场值是零。

[^1]: I. L. Chuang, R. Laflamme, P. W. Shor, and W. H. Zurek, Science 270, 1633 (1995).
[^2]: W. H. Zurek, Reviews of modern physics 75, 715 (2003).
[^3]: K. Hornberger, Entanglement and Decoherence: Foundations and Modern Trends , 221 (2009).
[^4]: M. A. Schlosshauer, Decoherence: and the quantum-to-classical transition (Springer Science & Business Media, 2007).
[^5]: W. H. Zurek et al., Physics today 44, 36 (1991).
[^6]: P. W. Shor, Physical review A 52, R2493 (1995).
[^7]: S. P. Jordan, E. Farhi, and P. W. Shor, Physical Review A 74, 052322 (2006).
[^8]: E. Knill and R. Laflamme, Physical Review A 55, 900 (1997).
[^9]: P. W. Shor, in Proceedings of37th conference on foundations of computer science (IEEE, 1996) pp. 56–65.
[^10]: D. G. Cory, M. Price, W. Maas, E. Knill, R. Laflamme, W. H. Zurek, T. F. Havel, and S. S. Somaroo, Physical Review Letters 81, 2152 (1998).
[^11]: J. Chiaverini, D. Leibfried, T. Schaetz, M. D. Barrett, R. Blakestad, J. Britton, W. M. Itano, J. D. Jost, E. Knill, C. Langer, et al., Nature 432, 602 (2004).
[^12]: E. Knill, R. Laflamme, R. Martinez, and C. Negrevergne, Physical Review Letters 86, 5811 (2001).
[^13]: M. Freedman, A. Kitaev, M. Larsen, and Z. Wang, Bulletin of the American Mathematical Society 40, 31 (2003).
[^14]: A. Kitaev, Annals of Physics 303, 2 (2003). [[通过任意子的可容错量子计算_Kitaev]]
[^15]: E. Dennis, A. Kitaev, A. Landahl, and J. Preskill, Journal of Mathematical Physics 43, 4452 (2002).
[^16]: A. Stern and N. H. Lindner, Science 339, 1179 (2013).
[^17]: S. Das Sarma, M. Freedman, and C. Nayak, Physics today 59, 32 (2006).
[^18]: X. G. Wen and Q. Niu, Phys. Rev. B 41, 9377 (1990).
[^19]: C. Nayak, S. H. Simon, A. Stern, M. Freedman, and S. D. Sarma, Reviews of Modern Physics 80, 1083 (2008).
[^20]: A. Kitaev, Annals of Physics 321, 2 (2006). [[精确可解模型及其他中的任意子_Kitaev|Anyons in an exactly solved model and beyond]]
[^21]: M. Hermanns, I. Kimchi, and J. Knolle, Annual Review of Condensed Matter Physics 9, 17 (2018).
[^22]: G. Jackeli and G. Khaliullin, Physical review letters 102, 017205 (2009).
[^23]: H. Takagi, T. Takayama, G. Jackeli, G. Khaliullin, and S. E. Nagler, Nature Reviews Physics 1, 264 (2019).
[^24]: S. M. Winter, A. A. Tsirlin, M. Daghofer, J. van den Brink, Y. Singh, P. Gegenwart, and R. Valent´ı, Journal of Physics: Condensed Matter 29, 493002 (2017).
[^25]: M. Gohlke, R. Moessner, and F. Pollmann, Physical Review B 98, 014418 (2018).
[^26]: E. H. Lieb, Physical Review Letters 73, 2158 (1994). [[半填充带的通量相|Flux Phase of the Half-Filled Band]]
[^27]: T. Minakawa, Y. Murakami, A. Koga, and J. Nasu, Physical review letters 125, 047204 (2020). [[Kitaev 量子自旋液体中 Majorana 介导的自旋传输]]
[^28]: See the Supplemental Information online.
[^29]: C. Harada, A. Ono, and J. Nasu, arXiv preprint arXiv:2305.08357 (2023). [[磁场驱动下的 Kitaev 自旋液体中 Majorana 零模的时空操控]]
[^30]: H.-C. Jiang, Z.-C. Gu, X.-L. Qi, and S. Trebst, Physical Review B 83, 245104 (2011).