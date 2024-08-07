---
tags:
  - 论文
created: 2024-08-07 13:11:16
aliases:
  - Tensor Network Python (TeNPy) version 1_Johannes
DOI: https://arxiv.org/abs/2408.02010
author:
  - Johannes Hauschild
original title: Tensor Network Python (TeNPy) version 1
year: "2024"
---
# Abstract

TeNPy（Tensor Network Python的缩写）是一个Python库，用于模拟具有张量网络的强相关量子系统。该库的理念是为新来者实现可读性和可用性的平衡，同时为专家提供强大的算法。重点是 1D 和 2D 晶格的 MPS 算法，如 DMRG 基态搜索，以及使用 TEBD，TDVP 或 MPO 演化的 dynamics. 本文是 TeNPy 最新版本 1.0 的配套文章，并简要介绍了该软件包。

# 1. 引言

大尺度数值模拟在理解强关联量子物质中起重要作用。张量网络方法，特别是基于矩阵乘积状态（MPS）[^1]的方法，已经成为研究这些系统的最新工具，特别是在费米子或受阻挫 setting 中，其中臭名昭著的符号问题抑制了大多数蒙特卡罗模拟技术。

对于 1D 中的局域带隙哈密顿量，纠缠的面积定律[^2]保证了将基态有效地表示为 MPS，并使得密度矩阵重整化群（DMRG）方法[^3][^4]能够成功地在数值上找到这些基态。已经证明，DMRG 基态搜索在长程相互作用[^5]或临界[^6][^7]系统的更广泛设置中也是一种有效工具，并且还可以通过模拟圆柱体几何形状[^8]应用于研究2D模型。只要演化态的纠缠保持可控，动力学可以用 TEBD[^9]、矩阵乘积算子（MPO）演化[^10]和时间相关变分原理（TDVP）[^11][^12]方法有效地模拟。各种其他应用领域包括模拟热态、非平衡动力学、激发光谱等。利用阿贝尔[^13][^14]或非阿贝尔[^15][^16]对称性导出的守恒律，可以显著提高这些方法的性能和精度。在本文中，我们不对这些过多的方法、概念和算法进行详细介绍，而是请感兴趣的读者参考现有的综述[^17][^18][^19][^20]。

用于张量网络模拟的 TeNPy 包基于参考文献[^21][^22]中使用的代码，并且在参考文献[^23]中首次作为开源 Python 包引入。它旨在为适合初学者的张量网络算法提供灵活，易于使用和记录良好的界面，同时为专家提供高性能模拟。模块化的包结构允许用户根据需要访问复杂性的嵌套层-从高级观点，例如建立相图，具体的 MPS 算法及其各种参数，到单个张量的底层线性代数。特别关注的是用户友好的张量网络初始化，不需要技术知识，也不需要与单个张量条目进行任何交互。这包括从乘积态，singlet coverings 或随机幺正演化生成 MPS，以及特定哈密顿量[^24][^25]或其（近似）时间演化算子[^10]的MPO表示。这允许用户以给定晶格几何形状上的位点之间的耦合的自然语言来指定模型，并且在几行 Python 代码或 yaml 配置文件中，执行例如有效的 DMRG 模拟，其负责
1. MPS的 1D 线性几何形状与物理晶格之间的映射
2. MPS 的规范形式，并使用迭代本征解算器找到局部基态
3. 利用阿贝尔对称的模型，使用块稀疏线性代数

TeNPy 是开源的，在 GitHub 上公开维护，有大量的在线文档，以及一个活跃的社区论坛。

本文随 TeNPy 的最新 1.0 版本一起发布，其结构如下。首先，我们将在第 2 节中对该软件包及其功能进行全面概述。在第 3 节和第 4 节中，我们先用代码片段展示了具体的示例模拟，然后在第 5 节中对性能进行基准测试。最后，我们在第 6 节中详细介绍了 TeNPy 张量的存储格式，并在第 7 节中对当前和未来的发展方向进行了展望。

# 2. 软件包概述

TeNPy 包由子模块组成，这些子模块可以被概念化为抽象层。在本节中，我们将介绍从高级用户友好的 `simulation` 模块到低级 `linalg` 模块的主要子模块及其最相关的内容。图 1 直观地概括了该结构。

> **Fig. 1**![[截图-1723005912048.png#R|Fig. 1|400]]
> 概述了 TeNPy 最重要的模块、类和函数。灰色背景表示模块，黄色背景表示类。红色箭头表示类继承关系，黑色箭头表示直接使用。在自然的阅读方向上，存在从高级（`tenpy.simulations`）到低级（`tenpy.linalg`）功能的层次结构。


`tenpy.simulations` 模块为整个模拟提供了一个高级接口，从一些输入参数，如哈密顿量中的系数，系统大小，键尺寸等，到一些感兴趣的量，如期望值，纠缠熵等。模拟运行大致包括初始化物理模型，定义哈密顿量和晶格几何，初始化张量网络（例如 MPS），运行算法（例如 DMRG），执行一些测量，可选的后处理，最后将结果保存到磁盘。如第 4.2 节所示，输入参数可以以易于阅读的 yaml 格式指定，这也有助于模拟结果的再现性和输入参数的寿命。模拟是高度灵活的，例如，允许参数按顺序改变，如逐渐增加键的尺寸或 sweeping a parameter through the phase diagram。它们还可以在定期检查点后恢复，这在计算集群上运行长时间模拟时通常需要。

`tenpy.algorithms` 模块实现了对张量网络状态进行操作的算法。这包括 MPS 压缩、DMRG、TEBD、TDVP 和 MPO 时间演化，以及变分均匀矩阵积状态（VUMPS）的实验实现[^26]。每个算法及其每个 notable variations（例如 two-site 与 one-site DMRG）都在专用类中实现，例如`SingleSiteDMRGEngine`。该模块包含一个多层的类继承层次结构，以便集中实现和维护几个算法之间通用的算法步骤。例如，DMRG 和 TDVP 都需要计算环境张量，这在 `Sweep` 类中实现。

`tenpy.models` 模块提供了两种类型的类。首先，表示任意维数的格的 `lattice` 类，尽管一维、准一维和二维系统是最常见的。这些类有助于在晶格几何和张量网络几何之间进行映射，例如如何将 MPS 缠绕在 2D 圆柱体上。第二，`model` 类，其在晶格上实现物理模型的细节，主要是在哈密顿量方面，其可以方便地在耦合方面指定，例如在晶格的最近邻居对之间。因此，非专家也可以定义新模型，并且不需要将哈密顿量表示为张量网络的技术知识。

`tenpy.networks` 模块实现了表示物理晶格的 sites 的类，定义了守恒电荷和局部算子的局部希尔伯特空间。此外，它还为支持的张量网络（如 `MPS` 和 `MPO`）定义了类，大量方便的函数来提取感兴趣的量，如期望值、纠缠谱等等。创建哈密顿量或其指数的 MPO 表示是完全自动化的，初始化大量精确的 MPS，例如 product state, singlet coverings 等.

`tenpy.linalg` 模块实现数值线性代数，（可选）利用任意阿贝尔对称群诱导的电荷守恒。它提供了 `Array` 类，表示具有块稀疏结构的对称张量，沿着它们的线性代数运算，例如张量收缩，特征分解，SVD 等。因此，`tenpy.linalg.np_conserved` 实现了与流行的 `numpy` 包类似的角色，尽管提供的函数范围较小。此外，迭代特征值求解器，如 DMRG 中常用的 Lanczos 算法，被实现为作用于块稀疏阵列的线性算子。流行的 NCON-style [^27]用于指定多个张量的收缩，也被实现为 `tenpy.ncon`。

# 3. 例子：海森堡链中的动力学
在本节中，我们将介绍一个示例用例，模拟自旋 $1/2$ 海森堡链中的非平衡动力学
$$
H = J \sum_{\ev{i,j}} \vec{S}_i \vdot \vec{S}_j, \tag{1}
$$
其中 $\vec{S}$ 是自旋算子 $S^\alpha = \sigma^\alpha/2$ 的向量。我们通过 TEBD 模拟-近似时间演化 $\ket{\psi(t)} = \me^{-\mi Ht} \ket{\psi(t=0)}$, 以及提取时间相关的可观测值-在Python代码片段中。代码在 GitHub 库中找到。

TeNPy 可以从 pip 和 conda 包管理器安装. 安装后，我们可以将包导入为
```python
import tenpy
```
首先，我们将模型 (1) 配置在 $L = 50$ 个 sites 的 1D 链上，设置 $J = 1$.
```python
model_params = dict(L=50, Jx=1, Jy=1, Jz=1)
model = tenpy.SpinChain(model_params)
```

默认情况下，边界条件是开放的，并使 TeNPy 使用有限 MPS。默认情况下，模型会对给定的模型参数强制执行最大（阿贝尔）对称性的守恒，在这种情况下，$U(1)$ 对称性保持 $Q = \sum_i S_i^z$. 这可以通过向模型参数添加 `conserve=None` 来禁用，或者通过添加例如 `conserve = 'parity'` 来放松到更小的对称性，以仅强制 $Z_2$ 子群保持 up-spins 数量的 parity $\tilde{Q} = \sum_i (S_i^z + 1/2) \mod 2$. 在线文档中有这些选项及其可能值的完整索引。

其次，我们初始化 Néel 状态 $\ket{\psi(t=0)} = \ket{\uparrow \downarrow \uparrow \downarrow \cdots}$,
```python
psi = tenpy.MPS.from_lat_product_state(
	model.lat , [[’up’], [’down’]]
)
```
以及 TEBD 引擎
```python
engine_params = dict(
	dt=0.01,
	N_steps=5,
	trunc_params=dict(
		chi_max =50,
		svd_min =1e-10,
	),
)
engine = tenpy.TEBDEngine(psi , model , engine_params)
```

它在每次调用它的 `.run()` 方法时执行 Trotterized 时间演化的五个步骤，每个步骤的大小 $\dd{t} = 0.01$. 在本例中，它配置了最大键维数 $\chi = 50$，并丢弃小于 $10^{-10}$ 的奇异值.



> **Fig. 2**![[截图-1723011104972.png#R|Fig. 2|400]]
> 从 $t = 0$ 的 Néel 态开始的海森堡链 (1) 的动力学。左上图示出了局部 $z$-磁化（在 $\chi = 1600$ 处），其随时间平衡到均匀值，如由左下图中的子晶格不平衡 (2) 量化的。右侧面板分别显示 half-chain 纠缠熵 $S_{\text{vN}}$ 和累积截断误差。请注意，图中显示的时间尺度数据具有较大的截断误差，即使在最大的键尺寸下也是如此，因此在分析时应忽略不计。我们在这里包括它们来展示纠缠熵的饱和行为。

为了运行模拟，我们在多个时间步长的外部循环中执行以下步骤：让引擎演化状态 `psi`，就地修改它，然后测量可观测值
```python
t = [0]
S = [psi.entanglement_entropy()]
Sz = psi.expectation_value('Sz')
mag_z = [Sz]
imbalance = [sum(Sz [::2] - Sz [1::2]) / psi.L]
for n in range (100):
	engine.run() # evolves psi in-place
	t.append(engine.evolved_time)
	S.append(psi.entanglement_entropy())
	Sz = psi.expectation_value('Sz')
	mag_z.append(Sz)
	imbalance.append(sum(Sz[::2] - Sz[1::2]) / psi.L)
```
在这里，`imbalance` 累积 每个时间 step 的 sublattice imbalance.
$$
\mathcal{I} = \frac1L \sum_j (-1)^j \ev{S_j^z}
= \frac1L \qty(\sum_{j\in A} \ev{S_j^z} - \sum_{j \in B} \ev{S_j^z})\tag{2}
$$
结果如图 2 所示。正如对于全局猝灭[^28]所预期的那样，纠缠随时间线性增长，使得在键维度 $\chi$ 处的精确模拟仅可能达到时间尺度 $\sim \log \chi$，并且使键维度加倍仅将该时间尺度推动一个常数。

# 4. 示例：2D 伊辛模型的 DMRG 研究

在本节中，作为第二个例子，我们使用 DMRG 描述了无限圆柱正方形晶格上横场伊辛模型的基态相图。文档中提供了 TeNPy 中 DMRG 模拟的更深入指南。

## 4.1. Python 代码
我们首先介绍如何在python代码片段中执行模拟。我们在二维正方晶格上构造了自旋1 2横场伊辛模型.下面几行用哈密顿量初始化模型


[^1]: M. Fannes, B. Nachtergaele and R. F. Werner, Finitely correlated states on quantum spin chains, Communications in Mathematical Physics 144(3), 443 (1992), doi:10.1007/BF02099178.
[^2]: M. B. Hastings, An area law for one-dimensional quantum systems, Journal of Statistical Mechanics: Theory and Experiment 2007(08), P08024 (2007), doi:10.1088/17425468/2007/08/P08024.
[^3]: S. R. White, Density matrix formulation for quantum renormalization groups, Physical Review Letters 69(19), 2863 (1992), doi:10.1103/PhysRevLett.69.2863.
[^4]: U. Schollwoeck, The density-matrix renormalization group in the age of matrix product states, Annals of Physics 326(1), 96 (2011), doi:10.1016/j.aop.2010.09.012, ArXiv:1008.3477.
[^5]: G. M. Crosswhite, A. C. Doherty and G. Vidal, Applying matrix product operators to model systems with long-range interactions, Physical Review B 78(3), 035116 (2008), doi:10.1103/PhysRevB.78.035116, ArXiv:0804.2504 [cond-mat, physics:quant-ph].
[^6]: L. Tagliacozzo, T. R. de Oliveira, S. Iblisdir and J. I. Latorre, Scaling of entanglement support for matrix product states, Physical Review B 78(2), 024410 (2008), doi:10.1103/PhysRevB.78.024410, Publisher: American Physical Society.
[^7]: F. Pollmann, S. Mukerjee, A. M. Turner and J. E. Moore, Theory of Finite-Entanglement Scaling at One-Dimensional Quantum Critical Points, Physical Review Letters 102(25), 255701 (2009), doi:10.1103/PhysRevLett.102.255701, Publisher: American Physical Society.
[^8]: E. M. Stoudenmire and S. R. White, Studying Two-Dimensional Systems with the Density Matrix Renormalization Group, Annual Review of Condensed Matter Physics 3(Volume 3, 2012), 111 (2012), doi:10.1146/annurev-conmatphys-020911-125018, Publisher: Annual Reviews.
[^9]: G. Vidal, Efficient Simulation of One-Dimensional Quantum Many-Body Systems, Physical Review Letters 93(4), 040502 (2004), doi:10.1103/PhysRevLett.93.040502, Publisher: American Physical Society.
[^10]: M. P. Zaletel, R. S. K. Mong, C. Karrasch, J. E. Moore and F. Pollmann, Time-evolving a matrix product state with long-ranged interactions, Physical Review B 91(16), 165112 (2015), doi:10.1103/PhysRevB.91.165112.
[^11]: J. Haegeman, J. I. Cirac, T. J. Osborne, I. Pižorn, H. Verschelde and F. Verstraete, Time-Dependent Variational Principle for Quantum Lattices, Physical Review Letters 107(7), 070601 (2011), doi:10.1103/PhysRevLett.107.070601.
[^12]: J. Haegeman, C. Lubich, I. Oseledets, B. Vandereycken and F. Verstraete, Unifying time evolution and optimization with matrix product states, Physical Review B 94(16), 165116 (2016), doi:10.1103/PhysRevB.94.165116.
[^13]: S. Singh, R. N. C. Pfeifer and G. Vidal, Tensor network decompositions in the presence of a global symmetry, Physical Review A 82(5), 050301 (2010), doi:10.1103/PhysRevA.82.050301, ArXiv: 0907.2994.
[^14]: S. Singh, R. N. C. Pfeifer and G. Vidal, Tensor network states and algorithms in the presence of a global U(1) symmetry, Physical Review B 83(11), 115125 (2011), doi:10.1103/PhysRevB.83.115125, ArXiv: 1008.4774.
[^15]: I. P. McCulloch and M. Gulácsi, The non-Abelian density matrix renormalization group algorithm, Europhysics Letters 57(6), 852 (2002), doi:10.1209/epl/i2002-00393-0, Publisher: IOP Publishing.
[^16]: S. Singh and G. Vidal, Tensor network states and algorithms in the presence of a global SU(2) symmetry, Physical Review B 86(19), 195114 (2012), doi:10.1103/PhysRevB.86.195114, Publisher: American Physical Society.
[^17]: R. Orús, A practical introduction to tensor networks: Matrix product states and projected entangled pair states, Annals of Physics 349, 117 (2014), doi:10.1016/j.aop.2014.06.013.
[^18]: J. C. Bridgeman and C. T. Chubb, Hand-waving and interpretive dance: an introductory course on tensor networks, Journal of Physics A: Mathematical and Theoretical 50(22), 223001 (2017), doi:10.1088/1751-8121/aa6dc3, Publisher: IOP Publishing.
[^19]: R. Orús, Tensor networks for complex quantum systems, Nature Reviews Physics 1(9), 538 (2019), doi:10.1038/s42254-019-0086-7, Publisher: Nature Publishing Group.
[^20]: M. C. Bañuls, Tensor Network Algorithms: A Route Map, Annual Review of Condensed Matter Physics 14(Volume 14, 2023), 173 (2023), doi:10.1146/annurev-conmatphys-040721-022705, Publisher: Annual Reviews.
[^21]: J. A. Kjäll, M. P. Zaletel, R. S. K. Mong, J. H. Bardarson and F. Pollmann, The phase diagram of the anisotropic spin-2 XXZ model: an infinite system DMRG study, Physical Review B 87(23), 235106 (2013), doi:10.1103/PhysRevB.87.235106, ArXiv:1212.6255 [cond-mat].
[^22]: M. P. Zaletel, R. S. K. Mong and F. Pollmann, Topological characterization of fractional quantum Hall ground states from microscopic Hamiltonians, Physical Review Letters 110(23), 236801 (2013), doi:10.1103/PhysRevLett.110.236801, ArXiv:1211.3733 [cond-mat].
[^23]: J. Hauschild and F. Pollmann, Efficient numerical simulations with Tensor Networks: Tensor Network Python (TeNPy), SciPost Physics Lecture Notes p. 5 (2018), doi:10.21468/SciPostPhysLectNotes.5, ArXiv: 1805.00055.
[^24]: G. M. Crosswhite and D. Bacon, Finite automata for caching in matrix product algorithms, Physical Review A 78(1), 012356 (2008), doi:10.1103/PhysRevA.78.012356, Publisher: American Physical Society.
[^25]: S. Paeckel, T. Köhler and S. R. Manmana, Automated construction of $U(1)$-invariant matrix-product operators from graph representations, SciPost Physics 3(5), 035 (2017), doi:10.21468/SciPostPhys.3.5.035.
[^26]: V. Zauner-Stauber, L. Vanderstraeten, M. T. Fishman, F. Verstraete and J. Haegeman, Variational optimization algorithms for uniform matrix product states, Physical Review B 97(4), 045145 (2018), doi:10.1103/PhysRevB.97.045145, Publisher: American Physical Society.
[^27]: R. N. C. Pfeifer, G. Evenbly, S. Singh and G. Vidal, NCON: A tensor network contractor for MATLAB, doi:10.48550/arXiv.1402.0939, URL http://arxiv.org/abs/1402.0939, ArXiv:1402.0939 [cond-mat, physics:physics, physics:quant-ph] (2015).
[^28]: H. Kim and D. A. Huse, Ballistic spreading of entanglement in a diffusive nonintegrable system, Physical Review Letters 111(12), 127205 (2013), doi:10.1103/PhysRevLett.111.127205, ArXiv:1306.4306 [cond-mat, physics:quant-ph].
[^29]: S. R. White, Density matrix renormalization group algorithms with a single center site, Physical Review B 72(18), 180403 (2005), doi:10.1103/PhysRevB.72.180403, Publisher: American Physical Society.
[^30]: M. Fishman, S. R. White and E. M. Stoudenmire, The itensor software library for tensor network calculations, SciPost Phys. Codebases p. 4 (2022), doi:10.21468/SciPostPhysCodeb.4, Publisher: SciPost.
[^31]: M. Fishman, S. R. White and E. M. Stoudenmire, Codebase release 0.3 for itensor, SciPost Phys. Codebases pp. 4–r0.3 (2022), doi:10.21468/SciPostPhysCodeb.4-r0.3, Publisher: SciPost.