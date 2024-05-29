---
tags:
  - 论文
created: 2023-08-18 15:53:09
aliases: 
DOI: 10.1088/1751-8113/41/7/075001
author:
  - "[[Han-Dong Chen]]"
  - "[[Zohar Nussinov]]"
original title: Exact results on the Kitaev model on a hexagonal lattice spin states, string and brane correlators, and anyonic excitations
alises:
  - Exact results on the Kitaev model on a hexagonal lattice spin states, string and brane correlators, and anyonic excitations
year: "2008"
---

# 摘要

在这项工作中，我们阐述了如何将 [[Jordan-Wigner 变换]] 与对称性考虑相结合，从而直接解决了蜂窝晶格上的 Kitaev 模型。我们
1. 通过原始自旋表达了该系统的 $p$ 波型费米子基态
2. 说明了仅通过对称性就能够决定弦和平面膜类型关联及其复合体的存在
3. 通过使用 Jordan-Wigner 变换计算了这种非局域关联的值
4. 确认谱对于拓扑量子序的存在无关紧要，而此类信息被编码在态之中
5. 通过费米子的形式表达了 Kitaev 模型的局部对称性和激发的任意子特性

# I. 引言

拓扑量子序（Topological Quantum Order，TQO）[1, 2] 是一种超越[[Lev Landau|朗道]]的局域序参量理论[3, 4] 范畴的新范式。TQO 直观地与对局部扰动的不敏感性相关：这种序是拓扑性的。因此，TQO 不能用局域序参量来描述。

一个典型的拥有 TQO 的系统例子是蜂窝晶格上的Kitaev模型[5–7]。在本文中，我们将研究这个模型。我们的新中心结果包括：
1. 对于实空间中基态的显式表达，扩展和补充了[6, 7]的工作
2. 我们在该系统中发现的非局域关联（二维弦或膜类型的关联）
3. 通过直接的Jordan-Wigner变换如何重新检验Kitaev模型的已知任意子激发。除了提供一个突显了先前被忽视的方面的直接解决方案外，我们的结果还将充实关于TQO的一些更一般的观念[8, 9]。


# II. 大纲

本文的组织结构如下。

在[[#III. 费米子化|第3节]]，我们回顾了蜂窝晶格上 Kitaev 模型的费米化[^9][^10]。原始的蜂窝晶格自旋模型被映射到具有用于方格晶格上无自旋费米子的 $p$ 波 BCS 模型，其中化学势依赖于位点。

在第4节，我们讨论了模型中体现的对称性的费米表示。通过规范固定，证明了Kitaev[^6]研究的平面上的局域守恒量与费米表示中的守恒键量等效。

在第5节，我们精确求解了费米表示中的基态构型，它在自旋表示中是无涡的，而在费米表示中具有均匀的化学势。还研究了基态的自旋基础形式。结果表明，基态可以被写成将给定的参考态投影到希尔伯特空间的一个部分上，该部分具有一组选择的拓扑数，这些数与其他表现出TQO的系统（如Rokhsar-Kivelson二聚体模型[11]和Kitaev toric code模型[2]）类似，但稍微更复杂。还获得了相图和Bogliubov激发。

在第6节中，我们展示了在带隙态中已知的有关任意子涡激发的结果如何在费米表示中轻松研究。

在第7节中，提出了一个关于消失关联函数的对称性论证，最近也通过Majorana费米化构造重新推导出来[12]。我们还展示了在Kitaev模型中自然出现的弦关联。

在第8节中，简要总结了本文。在附录中，我们提供了关于确定基态和回顾Elitzur定理的技术细节。

# III. 费米子化

我们从对蜂窝晶格上的Kitaev模型进行费米化开始[[精确可解模型及其他中的任意子_Kitaev]][^6][[任意子的波函数|]][^7]，该模型由以下 $S = 1/2$ 哈密顿量定义：
$$
H = -J_x \sum_{x\text{-bonds}}\sigma_R^x \sigma_{R'}^x
-J_y \sum_{y\text{-bonds}}\sigma_R^y \sigma_{R'}^y
-J_z \sum_{z\text{-bonds}}\sigma_R^z \sigma_{R'}^z
\tag{1}
$$
其中 $R$ 和 $R'$ 是晶格位点。这个系统可以通过 Jordan-Wigner 变换[^9][^10]来进行费米化。通过将六边形晶格变形成一个与之在拓扑上等价的“砖墙晶格”，我们可以在这个“砖墙晶格”上进行一维 Jordan-Wigner 变换，从而使这一维费米化更加生动。示意图如图 1 所示。![[截图-1692726499473.png#R|图 1|300]]

在接下来的讨论中，我们将以“白色”或“黑色”（w/b）来标记所有的位点，以表示它们属于哪个亚晶格。在这个晶格上，两个最近邻位点之间的距离将设置为单位距离。

除非另有说明，我们将始终考虑具有开放边界条件的系统。图 1 中所示的对角方向 $\vu*{e}_x$ 和 $\vu*{e}_y$ 将在我们的最终解决方案中至关重要。我们用 $(i,j)$ 表示图 1 晶格上每个位点 $R$ 的笛卡尔坐标。接下来，让我们考虑由一个简单的一维轮廓定义的 Jordan-Wigner 变换，该轮廓贯穿整个晶格（见图2）：![[截图-1692726802285.png#R|图 2|300]]

$$
\sigma_{ij}^+=2\qty[\prod_{j'<j}\prod_{i'}\sigma_{i'j'}^z]
\qty[
\prod_{i'<i}\sigma_{i'j}^z
]c_{ij}^\dagger\tag{2}
$$
$$
\sigma_{ij}^z = 2c_{ij}^\dagger
c_{ij}-1\tag{3}
$$

这条路径在每个晶格位点上恰好经过一次，如图 2 所示。在方程（2）中，$σ^+ = σ_x + \mi σ^y$ 是在给定位点的自旋升算符的两倍，因此有因子 2.

式 (1) 的Kitaev模型变为

$$
\begin{align}
H = J_x\sum_{x\text{-bonds}}
(c^\dagger-c)_w(c^\dagger+c)_b
\end{align}
$$

# IV. 局部对称性的费米表示

# V. 基态



[^6]: [[精确可解模型及其他中的任意子_Kitaev]]
[^7]: [[任意子的波函数]]
[^9]: [[二维自旋系统中经典序拓扑序间的精确映射]]
[^10]: [[Topological Characterization of Quantum Phase Transitions in a Spin-12 Model]]