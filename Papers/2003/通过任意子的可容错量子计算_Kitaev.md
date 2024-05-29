---
tags:
  - 论文
created: 2023-06-12 14:02:54
aliases:
  - Fault-tolerant quantum computation by anyons_Kitaev
  - Kitaev(2003)
DOI: https://doi.org/10.1016/S0003-4916(02)00018-0
original title: Fault-tolerant quantum computation by anyons
author:
  - "[[Alexei Kitaev]]"
year: "2003"
---
# Abstract

具有任意子激发的二维量子系统可以看作是量子计算机。幺正变换可以通过移动激发来实现。测量可以通过成对地联合激发并观察融合的结果来进行。这种计算由于其物理性质而具有容错性。

# 序言

量子计算机可以为某些计算问题(例如，分解和离散对数[^1])提供快速解决方案，而这些问题在普通计算机上需要指数时间。量子计算机的物理实现对科学家来说是一个巨大的挑战。一个重要的问题是发生在真实量子系统中的幺正变换中的退相干和系统误差。从纯理论的角度来看，由于 [[Peter Shor|Shor]] 发现了容错量子计算[^2]，该问题得到了解决，并进行了后续的改进[^3][^4][^5][^6]。任意的量子电路都可以用 imperfect gates 来模拟，只要这些门接近理想的门，达到恒定的精度 $\delta$. 不幸的是，$\delta$ 的阈值相当小; 要达到这样的精度是非常困难的。

不用说，经典计算也可以进行容错。然而，在实践中很少这样做，因为经典的门是足够可靠的。为什么会这样?让我们试着理解最简单的事情——为什么经典信息可以可靠地存储在磁性介质上。磁性产生于单个原子的自旋。每一个自旋对热波动都非常敏感。但是自旋相互作用并且趋向于朝向相同的方向。如果某个自旋翻转到相反的方向，相互作用迫使它翻转回其他自旋的方向。这个过程与重复代码的标准纠错过程非常相似。我们可以说，错误是在物理层面上被纠正的。我们能在量子的情况下提出类似的东西吗? 是的，但事情没那么简单。首先，我们需要一个带有局部稳定算子的量子码。

我从与环面和其他二维表面上的晶格相关的一类稳定量子码开始[6,8]。量子位元位于晶格的边缘，而稳定算子则对应于顶点和面。这些算符可以合在一起构成具有局域相互作用的哈密顿量。(这是一种惩罚函数; 违反每个稳定器条件将消耗能量)。这个哈密顿量的基态与密码的保护空间一致。它是 $4^g$-fold 的简并，其中 $g$ 是表面的 genus. 简并性对局部摄动是持久的。在足够小的扰动下，基态的分裂估计为 $\exp(−aL)$，其中 $L$ 是晶格的最小维数。这个模型可以被认为是一个量子存储器，其中稳定性是在物理水平上获得的，而不是通过一个显式的错误修正程序。

这个模型中的激发是任意子，这意味着当一个激发绕另一个激发运动时，全局波函数需要一些相位因子。一个可以在基态空间中工作通过产生一个激发对，移动环面上的一个激发，然后和另一个湮灭。不幸的是，这种行动并不是一个完备基。这个问题似乎可以在更一般的模型(或模型)中解决，其中一个量子比特的希尔伯特空间的维数为 $>2$. 该模型与 Hopf 代数有关。

在新模型中，我们不需要环面就能有简并度。平面上的 $n$ 粒子激发态已经是简并的，除非粒子(激发)彼此靠近。这些粒子是非阿贝尔任意子，即当一个粒子绕另一个粒子运动时，简并态经历了一个非平凡幺正变换。这种运动(“编织”)可以被认为是容错量子计算。最终状态的测量可以通过成对地将粒子连接起来并观察融合的结果来进行。

在场理论的背景下，Anyons 得到了广泛的研究[9,10,11,12,13]。对于它们的代数性质，我几乎没有发现什么新东西。然而，我的方法在以下几个方面有所不同:

- 模型的哈密顿量是不同的
- 我们允许一个一般的(但足够弱的)扰动，它移除了哈密顿量的*任何*对称性
- Ribbon 和局部运算符的语言(见第5.2节)提供了对任何电子激发和基态中的长距离纠缠态的统一描述。

G. Castagnoli 和 M. Rasetti[14]曾尝试使用一维任意子进行量子计算，但没有考虑容错问题。

# 1. Toric code 和相应的哈密顿量

# 2. 阿贝尔任意子

让我们对哈密顿函数的低能激发进行分类(4)。哈密顿函数的一个特征向量是所有算符 $A_s, B_p$ 的一个特征向量。当仅违反 $As \ket{\xi} =  \ket{\xi}$, $B_p \ket{\xi} = \ket{\xi}$ 的约束之一时，就会发生基本激发或粒子。由于 $\sum_s A_s = 1$ 和 $\sum_p B_p = 1$ 的关系，不可能产生单个粒子。然而，我们也可以建立一个双粒子态 $\ket{\psi^z(t)} = S^z(t) \ket{\xi}$ 或 $\ket{\psi^x(t')} = S^x(t') \ket{\xi}$ ，其中 $\ket{\xi}$ 是任意基态，且
$$
S^z(t) = \prod_{j \in t} \sigma_j^z,
\quad S^x(t') = \prod_{j \in t'} \sigma_{j}^x \tag{5}
$$
(见图3)在第一种情况下，在“弦”(非封闭路径) $t$ 的端点上产生了两个粒子。这些粒子位于晶格的顶点上。我们称它们为 $z$ 型粒子，或“电荷”。相应地，$x$ 型粒子或“磁涡”也存在于这些表面上。操作符Sz(t)， Sx(t ')被称为字符串操作符。它们的特性如下:它们与每一个a和Bp对易，除了少数几个对应于字符串端点的a(即2)。注意状态| z(t)i = Sz(t)| i仅依赖于路径t的同伦类，而算符Sz(t)则依赖于t本身。允许偶数个z型粒子和偶数个x型粒子的任何构型。我们可以用任意的方式用字符串将它们连接起来。每个粒子构型在全局希尔伯特空间n中定义了一个4g维的子空间。这个子空间独立于弦，但有一个特定的向量Sa1 (t1)···Sam (tm)|ξi依赖于t1，…， tm。如果我们用不同的拓扑方式画出这些弦，我们就会得到另一个在相同的4维子空间中的向量。因此，弦是非物质的，但我们无法在形式主义中摆脱它们。

让我们看看如果这些粒子在环面(或其他表面)周围运动会发生什么。沿着路径cz1或cz2移动z型粒子(见图2)相当于应用算符Z1或Z2。因此，我们可以在基态空间中操作，通过创建一个粒子对，使其中一个粒子绕环面运动，并使其与另一个粒子相湮灭。因此，我们可以实现一些量子门。不幸的是，太简单了——我们只能对基态编码的2(或2g)量子位元中的每一个应用算子z和x。

现在我们可以给出基态分裂的物理解释。在摄动条件下，二粒子态|ψz(t)i不再是本征态。更确切地说，两个粒子都会传播，而不是停留在相同的位置。传播过程用有效质量为mz的Schr¨odinger方程描述。(x型粒子有另一个质量mx)。在无摄动模型中，mz = mx =∞。在基态中不存在真正的粒子，但它们可以被创造出来并在虚拟中湮灭。虚粒子在与另一个粒子湮灭之前可以在环面周围穿隧。这些过程将bz1Z1, bz2Z2, bx1X1, bx2X2项贡献给基态有效哈密顿量。其中，bαi ~ exp(−aα li)为隧穿振幅，而aα ~√2m∆E为隧穿粒子的虚波矢量。

下一个问题:如果我们让粒子围绕彼此移动会发生什么?(我们不需要环面;我们可以在飞机上工作)。例如，让我们移动一个x型粒子围绕一个z型粒子(见图4)
# 3. 物质化的对称: 这是个奇迹吗?

# 4. 基于群代数的模型

# 5. 代数结构

## 5.1. 粒子和局部算子

## 5.2. Ribbon 算符

## 5.3. Local 和 Ribbon 算符的进一步属性

## 5.4. 空间 $\mathcal{L}(a,b)$

# 6. 拓扑算子，编织和融合

# 7. 任意子的通用计算


[^1]: P. Shor, Algorithms for quantum computation: discrete logarithms and factoring. In Proceedings of the 35th Annual Symposium on Fundamentals of Computer Science. Los Alamitos, CA: IEEE Press, pp. 124–134 (1994).
[^2]: P. Shor, Fault-tolerant quantum computation. In Proceedings of the Symposium on the Foundations of Computer Science. Los Alamitos, CA: IEEE Press (1996); e-print quant-ph/9605011.
[^3]: E. Knill and R. Laflamme, Concatenated quantum codes, e-print quant-ph/9608012 (1996)
[^4]: E. Knill, R. Laflamme and W. Zurek, Accuracy threshold for quantum computation, e-print quant-ph/9610011 (1996).
[^5]: D. Aharonov and M. Ben-Or, Fault tolerant quantum computation with constant error, e-print quant-ph/9611025 (1996).
[^6]: A. Yu. Kitaev, Quantum computing: algorithms and error correction, Russian Math. Surveys, to be published (1997).
[^7]: C. Zalka, Threshold estimate for fault tolerant quantum computing, e-print quant-ph/9612028 (1996).
[^8]: A. Yu. Kitaev, Quantum error correction with imperfect gates. In Proceedings of the Third International Conference on Quantum Communication and Measurement, September 25-30, 1996, to be published (1997).
[^9]: F. Wilczek, Fractional statistics and anyon superconductivity, World Scientific, Singapore (1990).
[^10]: R. Dijkgraaf, V. Pasquier and P. Roche, Quasi-Hopf algebras, group cohomology and orbifold models, Nucl. Phys. B (Proc. Suppl.) 18B (1990).
[^11]: F. A. Bais P. van Driel and M. de Wild Propitius, Quantum symmetries in discrete gauge theories, Phys. Lett. B280, 63 (1992).
[^12]: F. A. Bais and M. de Wild Propitius, Discrete gauge theories, e-print hep-th/9511201 (1995).
[^13]: H. K. Lo and J. Preskill, Non-abelian vortices and non-abelian statistics, Phys. Rev. D48, 4821 (1993).
[^14]: G. Castagnoli and M. Rasetti, The notion of symmetry and computational feedback in the paradigm of steady, simultaneous quantum computation, Int. J. of Mod. Phys. 32, 2335 (1993).
[^15]: D. Gottesman, Phys. Rev. A54, 1862 (1996).
[^16]: A. R. Calderbank, E. M. Rains, P. M. Shor and N. J. A. Sloane, Quantum error correction and orthogonal geometry, Phys. Rev. Lett. 78, 405 (1997).
[^17]: A. R. Calderbank and P. W. Shor, Good quantum error-correcting codes exist, e-print quant-ph/9512032 (1995)
[18] D.Arovas, J.R.Schrieffer, and F.Wilczek, Fractional statistics and the quantum Hall Effect,
Phys. Rev. Lett. 53, 722–723 (1984).
[19] T.Einarsson, Fractional statistics on a torus, Phys. Rev. Lett. 64, 1995-1998 (1984).
[20] V. G. Drinfeld, Quantum groups. In Proc. Int. Cong. Math. (Berkley, 1986), pp. 798-820
(1987).
[21] M. Sweedler, Hopf algebras, W. A. Benjamin, Inc., New York (1969).
[22] S. Majid, Quasi-triangular Hopf algebras and Yang-Baxter equation, Intern. J. ofModern
Phys. A5, 1-91 (1990).
[23] C. Kassel, Quantum groups, Springer-Verlag, New York (1995).
[^24]: A. Yu. Kitaev, Quantum measurements and Abelian stabilizer problem, e-print quant-ph/9511026 (1995).
[^25]: G. t’Hooft, Nucl. Phys. B138, 1 (1978).