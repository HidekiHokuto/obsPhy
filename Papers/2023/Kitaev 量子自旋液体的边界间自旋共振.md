---
tags:
  - 论文
created: 2023-07-26 15:02:36
aliases:
  - Inter-edge spin resonance in the Kitaev quantum spin liquid
DOI: https://doi.org/10.1103/PhysRevB.108.115117
原标题: Inter-edge spin resonance in the Kitaev quantum spin liquid
author:
  - "[[三澤 貴宏]]"
  - "[[那須 讓治]]"
  - "[[求 幸年]]"
year: "2023"
---

# 0. 摘要

[[Kitaev 蜂窝模型]]为[[量子自旋液体]](QSLs)提供了一个平台，其中包括*分数激发*、*巡回马约拉纳费米子*和*局域通量*。***由于这些分数激发可以用于量子计算，如何创建、观察和控制它们的自旋自由度是一个中心问题***。在此，我们通过在系统边缘施加 AC 磁场，研究了Kitaev-Heisenberg模型中的动态自旋输运。

我们发现，在 Kitaev QSL 相位中，尽管静态自旋相关极小，但另一边的自旋极化在特定的自旋分量中共振诱导。***这种边缘间自旋共振出现在宽频率范围内的输入频率附近***。

通过与动态自旋相关的比较，我们阐明了共振是由具有***广泛连续激发谱的马约拉纳费米子***控制的，它可以长距离传播，尽管它在纯 Kitaev 模型中由于*偶然简并*而消失，并且需要*弱海森堡相互作用*。我们还发现，无论输入频率如何，其它自旋分量中的自旋极化在接近局域磁通激发间隙的*几乎恒定频率下被弱诱导*。***这些结果表明，在 Kitaev QSL中，动态自旋输运是对分数阶激发的有力探测***。

讨论了边缘间自旋共振的可能的实验实现。

# 1. 引言

固体中出现的奇异准粒子已经引起了基础物理学和工业应用领域的广泛关注。一个突出的例子是[[Majorana 费米子|马约拉纳粒子]]——带电中性自旋 $1/2$ 的粒子，它们是自己的反粒子。虽然它们通常表现为[[费米子|费米子]]，但在一些二维情况下，它们可以被视为不服从[[费米-狄拉克统计|费米-狄拉克]]或[[玻色-爱因斯坦统计|玻色-爱因斯坦统计]]的任意子。这样的马约拉纳粒子已经被利用 anyonic nature 在量子计算中的应用进行了深入的研究。

蜂窝格子上的 Kitaev 模型为实现马约拉纳粒子提供了一个理想的平台。它是一个基态为量子自旋液体 (QSL) 的精确可解模型。Kitaev QSL 拥有两种来自自旋分数化的演生准粒子: *巡回马约拉纳费米子*和*局域的通量*。

- 当自旋之间的相互作用很大程度上是*各向异性*时，这些准粒子变成*阿贝尔任意子*
- 当外加磁场作用几乎*各向同性*的情况下变成*非阿贝尔任意子*

Kitaev 模型可以在 [[Mott 绝缘体]]中实现，具有强大的*自旋轨道耦合*，如 $\text{Na}_2\text{IrO}_3$ 和 $\alpha \text{-RuCl}_3$. 通过对实验结果和理论计算结果的比较，揭示了这类候选材料中马约拉纳粒子的存在可能性; 参阅参考文献 9。其中，$α\text{-RuCl}_3$ *半量子化热霍尔效应* (half-quantized thermal Hall effect) 的发现是突破性的，为马约拉纳粒子提供了直接证据，但仍存在争论。

由于马约拉纳费米子和 Kitaev QSL 中的通量是由自旋的分数化产生的，所以它们是量子纠缠态，本质上是非局域的。的确，马约拉纳费米子之间的空间相关性是幂律衰减的*长程关联*，***尽管自旋相关性是短程的，并且在最邻近的位置之外消失***。还表明，巡回马约拉纳费米子能诱导长距离的自旋输运。

此外，在存在缺陷或边缘的情况下，由于缺陷或边缘附近的低能激发以及分数准粒子的非局域性质，自旋相关可以是长程的。对于量子计算，阐明如何通过自旋自由度来控制和探测这种非局域性是至关重要的，但尽管有许多理论工作，这还没有完全阐明。

为了理解分数准粒子与自旋自由度之间的关系，本文研究了 Kitaev QSL 中的非局域自旋动力学。特别地，我们考虑有边的系统, 并且检查自旋激发如何从一条边传播到另一条边。在 Kitaev 模型的边缘，已知局部磁场激发通量, 并伴随着无能隙[[Majorana 费米子|马约拉纳激发]]，这种*通量*被称为*马约拉纳零模*。

在本研究中，我们在一个边缘引入非静态的时间相关的局部磁场，并研究激发的自旋极化如何在系统中传播。通过分析，阐明了分数化激发与自旋自由度的非局部动态关联之间的关系，为利用自旋自由度, *产生和控制分数化激发*提供了一种思路。

本文的组织如下。在第二节中，我们介绍了本研究中使用的模型和设置，以及实时演化的细节和*静态和动态自旋关联*的定义。在第三章A节，我们给出了带边模型的相图和静态自旋关联。在第三节B中，我们展示了边缘的交流局部磁场如何在系统的相反边缘诱导自旋极化. (铁磁相, Kitaev QSL, 条状相) 在第三节C中，我们将结果与边之间的动态自旋相关性进行了比较分析，并讨论了边间动态自旋输运的起源。第四节专门作总结。

# 2. 模型与方法

本文采用 Kitaev-Heisenberg 模型，该模型的哈密顿量
$$
H_{\text{KH}}=
K\sum_{\nu} \sum_{\ev{ij}_{\nu}}
S_i^\nu S_j^\nu + J \sum_{\ev{ij}}\vb*{S}_i \vdot \vb*{S}_j\tag{1}
$$
其中 $S_i^\nu$ 表示第 $i$ 个位置的 spin-$1/2$ 算符的 $\nu$ 分量: $\vb*{S}_i = (S^x_i, S^y_i, S^z_i)$. 
第一项表示键依赖的 [[伊辛模型|Ising 型相互作用]], 称为 [[Kitaev 蜂窝模型|Kitaev 相互作用]]，其中 $\ev{ij}_\nu$ 表示蜂巢晶格上的最近邻居 $ν(= x, y, z)$ 键，第二项表示所有最近邻键的自旋各向同性[[海森堡模型|海森堡相互作用]]; 见图 1.根据之前的研究，我们将两个耦合常数参数化为
$$
(K,J) = \qty(\sin \alpha, \frac12 \cos \alpha)
$$
请注意，与之前相比，相互作用的振幅减半，以便在纯 Kitaev 情况下，即 $α = π/2$ 和 $3π/2$ 时，$|K| = 1$. 

接下来，我们将重点关注 $π ≤ α ≤ 7π/4$ 的范围，其中 Kitaev 相互作用是*铁磁性*的。在这个区域内，具有周期性边界条件的 bulk 系统在基态中显示出三个相: 
1. $π ≤ α \lesssim 1.40π$ 时是铁磁相
2. $1.40π \lesssim α \lesssim 1.58π$ 时是 Kitaev 量子自旋液体（QSL）相
3. $1.58π \lesssim α \lesssim 1.81π$ 时是条纹相 (stripy phase)

为了研究边缘上的自旋关联和动力学，我们考虑了在一个方向上具有*开边界条件*和另一个方向上具有*周期边界条件*的 strip 上的模型。这样的 strip 有两种类型
1. 一个在开放边界上有所谓的 *armchair 式边缘*
2. 另一个有所谓的 *zigzag 状边缘*

图 1 ![[截图-1690466141992.png#R|图 1|400]]显示了以下计算中使用的 24 sites cluster 的这两种类型。

对于这两个 cluster，我们研究了一个随时间变化的局部磁场如何在一个边缘诱导另一个边缘的自旋极化。

具体来说，我们在自旋空间中边缘上的 $i$ 号 spin 上 (如图 1 中的黄色圆圈所示) 施加一个 $\qty[111]$ 方向的交流磁场

$$H(t) = H_{\text{KH}} + \vb*{h}_{\text{in}}(t) \vdot \vb*{S}_{i_{\text{in}}}\tag{3}$$
其中
$$
\vb*{h}_\text{in}(t) = h \vb*{e}_c \cos(\Omega t)
$$
$h$ 是交流场的振幅, $\vb*{e}_c = (1,1,1)/\sqrt{3}$ 是单位矢量, $\Omega = 2\pi / T$ 是交流场频率.

[[薛定谔方程|含时薛定谔方程]]
$$\mi \dv{\ket{\Phi(t)}}{t} = H(t) \ket{\Phi(t)}\tag{5}$$
初始条件 $\ket{\Phi(t = 0)} = \ket{\Phi_{\text{GS}}}$，其中 $\ket{\Phi_{\text{GS}}}$ 为 $H_{\text{KH}}$ 的归一化基态。

对边的自旋极化计算为
$$
S_{i_\text{out}}^\nu(t)= \ev*{S_{i_\text{out}}^\nu(t)}{\Phi(t)}
$$

其中 $i_{\text{out}}$ 表示与 $i_{\text{in}}$ 位点直接相对的另一个边缘上的位点. 

在下面的计算中，我们在等式 (4) 中取 $h = 0.05$. 利用 $H\Phi$ 解方程 (5); 令 $\Delta t = 0.05$, 它足够小以保持实时演化的幺正性.

除了自旋极化的实时动力学外，我们还计算了*基态* $\ket{\Phi_{\text{GS}}}$ 两个边之间的*静态和动态自旋关联*, 定义为
$$
S_{\text{edge}}^{\nu\nu} = \ev{S_{i_\text{in}}^\nu S_{i_\text{out}}^\nu}{\Phi_{\text{GS}}}\tag{7}
$$
$$
S_{\text{edge}}^{\nu\nu}(\omega)
= \frac{1}{2\pi} \int_{-\infty}^\infty
\ev{\delta S_{i_{\text{in}}}^\nu(t)\ \delta S_{i_{\text{in}}}^\nu(t)}{\Phi_{\text{GS}}}\ \me^{\mi \omega t}\dd{t}\tag{8}
$$
$\delta S_i^\nu = S_i^\nu - \ev*{S_i^\nu}{\Phi_{\text{GS}}}$

$\delta S_{i_{\text{in}}}^\nu (t) = \me^{\mi H_{\text{KH}}t}\ \delta S_{i_{\text{in}}}^\nu\ \me^{-\mi H_{\text{KH}}t}$

请注意，在方程 (8) 我们将考虑与基态的期望值的*偏差*之间的相关性，以在*存在磁有序*的情况下减去*弹性分量*。在方程 (8) 的实际运算中, 我们在*频谱表示*中采用以下公式：
$$
\begin{align}
S_{\text{edge}}^{\nu \nu}(\omega)
= \frac{1}{4\pi} \text{Im} \Big[
\ev{\qty(E_{\text{GS}}-H_{\text{KH}}+\omega+ \mi \eta)^{-1}}{\Psi_+}\\
+ \ev{\qty(E_{\text{GS}}-H_{\text{KH}}+\omega+ \mi \eta)^{-1}}{\Psi_-}
\Big]\tag{9}
\end{align}
$$

其中
- $\ket{\Psi_\pm} = \qty(\delta S_{i_{\text{in}}}^\nu \pm \mi \delta S_{i_{\text{out}}}^\nu) \ket{\Phi_{\text{GS}}}$
- $E_{\text{GS}}$ 为基态能量
- $η$ 为无穷小的 positive constant

在下面的计算中我们取 $η = 0.05$. 我们计算方程 (9) 使用基于 Lanczos 方法的连分数展开.

在方程 (7) 和 (9) 的计算中，我们对边界上第 $i$ 个边的所有自旋施加了一个弱静态磁场，其中 $\vb*{h}_s = 0.005 \vb*{e}_c$, 以消除具有 $α = π$ 的[[海森堡模型|铁磁海森堡模型]]和 $α = 3π/2$ 的纯 Kitaev 模型中的基态简并 (详见附录A). 对于其他情况，基态并不简并，但我们为了进行比较而同样施加了这个弱场.

# 3. 实验结果

## A. 相图和静态自旋关联

在进入自旋动力学之前，我们讨论了具有图 1 所示边缘的 clusters 的基态。图 2(a) 和 2(b)![[截图-1690560746877.png#R|图 2|350]] 分别显示了 armchair 和 zigzag 边缘系统基态能量二阶导数的 $α$ 依赖性。在 $α = α_{c1}$ 和 $α = α_{c2}$ 处的两个峰表示[[相变|一级相变]]. 

图 2(c) 和图 2(d) 显示了由方程 (7) 定义的*静态边缘间自旋关联*。从这些数据中，我们确定了三个不同的阶段：

- 当 $α < α_{c1}$ 时，*铁磁相*自旋正相关;
- 当 $α_{c1} < α < α_{c2}$ 时，Kitaev QSL 自旋相关*几乎为零*; 
- $\alpha > \alpha_{c2}$ 时, *条纹相*在 armchair 和 zigzag 型边间分别有负, 正相关.

从图 2(e) 和图 2(f) 的示意图中可以分别理解条状相位中的反铁磁和铁磁自旋相关。我们注意到，在铁磁相和条带相中，自旋相关在一个特定的自旋分量 $S^z$ 中占主导地位，这是由于边的存在，除了在弱磁场 $\vb*{h}_s$ 下基态简并的 $\alpha = \pi$ 之外。

在周期性边界条件下，我们得到的有边界 cluster 的相图与同样大小的 clusters 的相图几乎相同。对于 armchair(zigzag) 边缘的系统，我们发现铁磁性与 Kitaev QSL 相的相界在 $\alpha_{c1} \simeq 1.41π\ (1.49π)$，而 Kitaev QSL 与条状相的相界在 $α_{c2} \simeq 1.57π\ (1.65π)$. 这些估计与具有周期边界条件的 clusters, $α_{c1} \simeq 1.40π$ 和$α_{c2} \simeq 1.58π$ 的估计接近。

这表明，即使对于这种大小的 clusters，引入 edge 对 bulk 属性的影响也不大。

在接下来的部分中，我们将计算三个相的自旋动力学: 在 armchair 和 zigzag edge 的情况下, 对于铁磁相、Kitaev QSL 和 条纹相，我们分别取 $α = 1.25π$、$1.52π$ 和$1.67π$.

# 附录A：带边的纯 Kitaev 模型的简并性

在本附录中，我们证明了 $α=3π/2$ 的纯 Kitaev 模型的基态在 armchair 和 zigzag 两种情况下都具有简并性。 在纯Kitaev模型中，我们可以用每个六边形p的六个自旋的乘积来定义通量算符 $W_p$. 我们展示了图的例子 9； 注意(a)[(b)]中的w p与s y iin（sz iin）交换，因为六边形在iinth位置缺少y(z)键，如SEC中所讨论的。 III B1(iii)B2)。 除了六自旋通量算符外，在系统的边缘处还有附加的通量算符，这些通量算符仅由边缘自旋定义。 例如，包括输出位置的通量运算符由 






















