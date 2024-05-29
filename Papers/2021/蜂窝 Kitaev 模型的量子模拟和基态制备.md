---
tags:
  - 论文
created: 2024-05-21 19:55:16
aliases:
  - Quantum simulation and ground state preparation for the honeycomb Kitaev model_Bespalova
DOI: 10.48550/ARXIV.2109.13883
author:
  - Tatiana A. Bespalova
  - Oleksandr Kyriienko
original title: Quantum simulation and ground state preparation for the honeycomb Kitaev model
year: "2021"
---
# Abstract

我们提出了一种量子协议，允许准备蜂窝基塔耶夫模型的基态(GS)。我们的方法有效地利用了底层对称性和拓扑纠错技术。它基于 stabilization 过程，the developed centralizer ansatz，并利用涡旋基描述作为最有利的量子比特模拟。我们演示了为原始 Kitaev 模型制备自旋液体基态的高保真度，使用 230 个双量子比特操作获得 $N = 24$ 个自旋的精确 GS。然后，我们将变分过程扩展到非零磁场，研究揭示相变的可观测值和相关性。最后，我们进行了动态模拟，其中基态准备为强相关动力学的研究开辟了一条道路，并具有潜在的量子优势。

# 引言

强相关材料是由相互作用的电子和自旋[^1]模型描述的，由于符号问题和远程纠缠[^2]，有效的经典描述是不适用的。强相关性代表着一个巨大障碍的领域是磁性[^3]。当自旋之间的耦合相互竞争时，挫折会导致物质的奇异相[^4][^5]。一个显著的例子是量子自旋液体 (QSL) 相[^3][^6]，即使在低温 $T$ 下，强量子涨落也会持续存在。QSL 是模拟高 $T_c$ 超导的潜在候选者，并有助于研究非常规磁性材料[7,8]。它们包括蜂窝铱酸盐(Na2IrO3, Li2IrO3) [9-11]， 4d过渡金属基材料(αRuCl3)[12-14]和herbertsmithite[15]。从理论角度来看，QSL材料通常用键相关海森堡耦合的自旋晶格模型来描述[3,6]。蜂窝格的对应模型为Kitaev模型[16-18]。在许多情况下，自旋液体物理不能通过有效的经典方法获得，因为这需要研究低能行为并要求精确对角化(ED)[^19][^20][^21]。密度矩阵重整化群可以以截断波函数为代价推进该边界[22,23]。在这里，量子模拟(QS)提供了另一种解决方案[24-26]，其中强相关模型可以在经典无法达到的尺度上对固有量子器件进行研究[27,28]。

材料和化学的量子算法允许使用基态制备协议(GSP)获取多体哈密顿量的低 $T$ 特性[29-31]。他们可以使用不同的原则。一些人倾向于更好的扩展，同时增加门和量子位计数，并瞄准容错实现[^30][^32][^33][^34][^35][^36]。其他人则利用量子动力学和重叠测量在中等规模量子模拟器上有效地学习低 $T$ 物理[37-42]。对于近期操作，领先的方法是基于变分量子特征求解器(VQE, variational quantum eigensolver)中引入的变分原理和混合量子-经典环路[43-45]。这种变分 GSP 依赖于优化参数化量子电路(ansatz)，该电路在最佳参数下制备最小能量状态[^47][47 - 52]。这种操作模式在实验中受到青睐[44 - 46,53 - 55]，因为电路深度通常会减少。

VQE的效率关键取决于ansatz选择[56-59]。性能限制是由非凸多参数优化造成的，其中梯度消失的区域(贫瘠的高原)阻碍了大电路深度下的有效优化[60,61]。在结构不合适的深度电路失效的情况下，正确的参数化电路可以在合理的深度进行GSP。在化学中，由耦合簇理论指导的分析可以提供良好的收敛性[55,62 - 64]，尽管由于费米-量子位映射而牺牲了深度。硬件高效分析(HEA) VQE使用易于运行的浅电路，同时缺少对称性并迅速接近2-设计[65]。基于自适应生成器筛选[66-69]、进化和修剪方法[70-76]，提出了各种ansatz搜索技术。在这里，对称性保持电路提供了关键的优势[77-81]。对于自旋系统，许多研究针对的是更简单的模型，如横向Ising链、XXZ链和Heisenberg链[45,82 - 86]。最近的发展包括XXZ的哈密顿变分分析[87]，Ising模型的自然梯度优化[88]，二维XY模型的动态QS[89]，方形Heisenberg模型[90]和 $J_1\text{-}J_2$ 模型的张量网络分析[91]。许多更具挑战性的自旋模型仍未被探索。


在这篇论文中，我们提出了一个研究量子自旋液体物理的量子协议。我们开发了一种初始化技术和一种由*对称性驱动*的分析方法，以越来越大的规模模拟基态制备，具有可验证的优势。利用数字 QS，研究了强相关状态下 QSL 的动态特性。注意到开发的技术与量子纠错的路线图一致，我们认为自旋液体的模拟是迈向材料科学优势的自然步骤。


(a) 在环面上排列有N = 18个自旋的Kitaev晶格。ZZ, YY和XX型的海森堡耦合作用于六边形瓦片(斑块)周围的键。斑块算符(粉红色六边形，- wp)和循环算符(蓝色实体蛇)表示守恒量。
(b) 由稳定电路S - plq和S - str组成的量子协议，它们准备了一个具有固定数量旋涡的初始状态，可以通过A - w进行修改。接下来，我们使用d层变分中心器(- U(c) θc)和旋涡操作(- U(w) θw)来调整状态以匹配真实基态。![[截图-1716363088154.png#R|Fig. 1|300]]

# 模型
完整的基塔耶夫哈密顿式是H = H0 + Hm。在这项工作中，我们专注于各向同性的Kitaev模型Jx,y,z = J，同时注意到我们的方法也适用于各向异性的情况。虽然在没有H - 0描述的磁场的情况下，基塔耶夫模型是精确可解的，但它的解依赖于用马约拉纳费米子来描述系统[16,92]。具体来说，在进行Jordan-Wigner变换后，Kitaev模型可以简化为静态Z2规范场中的自由费米子[93]。这最近被用于在动量基础上对Kitaev模型的编织进行模拟[94]。这主要允许在热力学极限下预测性质和计算光谱[95]，但不提供在有限系统中制备GS的方法。与化学中的har特里-福克过程类似，自由费米子模型具有多项式复杂度，但如果想要使用它们的基态作为相关方法的垫脚石，它们确实需要复杂的GSP bb0。此外，由于量子比特和费米子之间的映射是非局域的，这就产生了一个开销，使看似原生的自旋-1/2模型的QS预算膨胀。相反，我们展示了如何有效地利用对称性可以产生一个成功的和可扩展的GSP协议，并为非零场的动态模拟和QSL开辟了道路.

其中X i, Y i, Z i是泡利算符P α i (α = X, Y, Z)，作用于点i(或顶点或量子位)。Jα是无量纲相互作用常数。X, Y, Z是一组最近邻的位点(键)，其中XX, YY和ZZ键在六边形上交替。它们在图1(a)中以不同颜色的链接表示。我们考虑把基塔耶夫模型放在一个环面上，使得晶格在两个空间维度上都是周期性的。晶格由N个顶点和N = Lx × Ly = N/2个六边形斑块组成，其中Lx (Ly)为水平(垂直)方向斑块的数量。通过增加两个额外的顶点来排列圆环边界，对于18量子位的圆环晶格，这两个顶点被标记为17和18[图1(a)]。用偏置项来描述具有笛卡尔分量的局域磁场h

# 对称性

# 变分搜索

要达到一个强关联哈密顿量的基态 $\ket{\psi_{GS}}$，我们需要设计一个酉算符 $\hat{\mathcal{U}}_{GS}$​，当作用在某个初始态 $\ket{\psi_0}$ 上时，准备出 $\hat{\mathcal{U}}_{GS} \ket{\psi_0} = \ket{\psi_{GS}}$. 为此，我们使用了一种变分量子协议。在变分搜索过程中，我们训练了一个参数化向量 θ 的 ansatz 电路 Uθ​，使得在最优参数 $\vb*{\theta}_{\text{opt}} = \arg \min_{\vb*{\theta}} \mel*{\psi_0}{\mathcal{U}_{\vb*{\theta}}^\dagger \mathcal{H} \mathcal{U}_{\vb*{\theta}}}{\psi_0}$ 下，系统的能量被最小化，并且 $U_{\theta_{\text{opt}}}$ 接近于 $U_{GS}$. 接下来，我们构建一个包含 $d$ 层 unitary 算符的 ansatz，形式为

$$
U_{\theta} = \prod_{k=1}^d U_{\theta_w}^{(w)} U_{\theta_c}^{(c)}
$$


这里，$U_{θ_c}^{(c)}$​ 是一个保持对称性和 $W_{tot}$​ 的酉算符，在没有磁场的情况下对快速 GSP（Ground State Preparation）至关重要。而单位算符 $U_{θ_w}^{(w)}$​ 引入了不保持涡旋的过程，在 $h \neq 0$ 时添加。
# 状态准备

对于一个有效的变分方法，我们需要从一个合适的涡数特征空间开始。在热力学极限下，$\hat{\mathcal{H}}_0$ 的简并基态集合对应于零涡扇区( $W_{\text{tot}} = 0$ )，对于小系统，这可能不同。为了初始化系统，我们准备了一个量子比特晶格作为 stabilizer 群 $\mathcal{S}$ 的特征态之一。该过程起源于拓扑量子计算中使用的技术，表明对于基于 Kitaev 模型的拓扑子系统代码，可以通过 2-量子比特投影来实现 stabilization[^98]。这类似于简单的 2 量子位情况下的 GHZ 状态准备，以及 surface code 矩形网格的 4-量子位稳定[^101]。为了应用投影，我们使用带有 $N_a$ 量子位的辅助量子位寄存器。初始化电路如图 1(b) 所示，其中幺正算符 $\hat{S}_{\text{plq}}$ 和 $\hat{S}_{\text{str}}$ 由 CNOTs 和 hadamards 组成，随后进行辅助测量。稳定后，我们可以额外应用基于单量子比特旋转的 $\hat{A}_w$，使涡旋成对产生和湮灭，将 $W_{tot}$ 调整为零(或任何其他扇区)，并准备 $\ket{\psi_0}$ (详见SM，第A节)。

[^1]: W. Witczak-Krempa, Gang Chen, Yong Baek Kim, and L. Balents, Correlated quantum phenomena in the strong spin-orbit regime, Annu. Rev. Condens. Matter Phys., 5, 57 (2014). 
[^2]: E. Y. Loh, Jr., J. E. Gubernatis, R. T. Scalettar, S. R. White, D. J. Scalapino, and R. L. Sugar, Sign problem in the numerical simulation of many-electron systems, Phys. Rev. B 41, 9301 (1990). 
[^3]: L. Savary and L. Balents, Quantum spin liquids: a review, Rep. Prog. Phys. 80, 016502 (2017). 
[^4]: L. Balents, Spin liquids in frustrated magnets, Nature 464, 199 (2010). 
[^5]: B. Tomasello, C. Castelnovo, R. Moessner, and J. Quintanilla, Correlated Quantum Tunneling of Monopoles in Spin Ice, Phys. Rev. Lett. 123, 067204 (2019). 
[^6]: H. Takagi, T. Takayama, G. Jackeli, G. Khaliullin, and S. E. Nagler, Kitaev quantum spin liquid - concept and materialization, Nat. Rev. Phys. 1, 264 (2019). 
[^7]: P. W. Anderson, The resonating valence bond state in La2CuO4 and superconductivity, Science 235, 1196 (1987). 
[^8]: P. A. Lee, From high temperature superconductivity to quantum spin liquid: progress in strong correlation physics, Rep. Prog. Phys. 71, 012501 (2007). 
[^9]: G. Jackeli and G. Khaliullin, Mott Insulators in the Strong Spin-Orbit Coupling Limit: From Heisenberg to a Quantum Compass and Kitaev Models, Phys. Rev. Lett. 102, 017205 (2009). 
[^10]: J. Chaloupka, G. Jackeli, and G. Khaliullin, KitaevHeisenberg Model on a Honeycomb Lattice: Possible Exotic Phases in Iridium Oxides A2IrO3, Phys. Rev. Lett. 105, 027204 (2010).

[^47]: M. Cerezo, A. Arrasmith, R. Babbush, S. C. Benjamin, S. Endo, K. Fujii, J. R. McClean, K. Mitarai, Xiao Yuan, L. Cincio, and P. J. Coles, Variational Quantum Algorithms, Nat. Rev. Phys. 3, 625 (2021).
[^98]: M. Suchara, S. Bravyi, and B. Terhal, Constructions and noise threshold of topological subsystem codes, J. Phys. A: Math. Theor. 44, 155301 (2011).