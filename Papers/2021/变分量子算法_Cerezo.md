---
tags:
  - 论文
created: 2024-05-22 16:15:36
aliases:
  - Variational quantum algorithms_Cerezo
DOI: 10.1038/s42254-021-00348-9
author:
  - "[[M. Cerezo]]"
original title: Variational quantum algorithms
year: "2021"
---
# 摘要

由于计算成本极高，模拟复杂量子系统或解决大规模线性代数问题等应用对于经典计算机来说是非常具有挑战性的。量子计算机有望提供一个解决方案，尽管容错量子计算机在不久的将来可能无法实现。目前的量子设备有严重的限制，包括有限的量子比特数量和限制电路深度的噪声过程。变分量子算法(VQAs)使用经典优化器来训练参数化量子电路，已经成为解决这些限制的主要策略。VQA 现在已经被提出用于研究人员为量子计算机设想的几乎所有应用，它们似乎是获得量子优势的最佳希望。然而，挑战仍然存在，包括vqa的可训练性、准确性和效率。在这里，我们概述了 VQA 领域，讨论了克服其挑战的策略，并强调了使用它们获得量子优势的令人兴奋的前景。

# 1. 引言

量子计算为许多应用带来了希望，这些应用推动了数十年来构建必要物理硬件的探索。例如，与经典方法相比，量子算法可以分解数字[^1]，模拟量子系统[^2]，或求解线性方程组[^3]。

2016年，第一台基于云的量子计算机[^4]可用，但噪声和量子位限制阻碍了上述量子算法[^5]的认真实施。然而，对于这些被称为*噪声中等规模量子*(NISQ)计算机[^6]的新设备，人们越来越兴奋。目前最先进的设备尺寸从 50 到 100 量子位不等，这使得人们可以实现“量子霸权”: 在某些人为的数学任务中，优于最好的经典超级计算机[^7][^8]。

然而，量子计算机的真正承诺，加速实际应用，这通常被称为量子优势，尚未实现。此外，容错量子计算机的可用性似乎还需要很多年，甚至几十年的时间。因此，关键的技术问题是如何充分利用当今的 NISQ 设备来实现量子优势。任何这样的策略都必须考虑到: 量子位的数量有限，量子位的连接有限，以及限制量子电路深度的相干和非相干错误。

变分量子算法 (VQAs) 已成为在 NISQ 器件上获得量子优势的主要策略。使用单一策略来考虑 NISQ 计算机施加的所有约束需要基于优化或基于学习的方法，这正是 VQAs 所使用的。VQAs 可以说是非常成功的机器学习方法(如神经网络)的量子模拟。此外，VQAs 利用经典优化工具箱，因为 VQAs 使用参数化量子电路在量子计算机上运行，然后将参数优化外包给经典优化器。与为容错时代开发的量子算法相比，这种方法具有保持量子电路深度较浅从而减轻噪声的额外优势。

 VQAs 已经被考虑用于大量的应用(见图3)，基本上涵盖了研究人员为量子计算机设想的所有应用。虽然它们可能是获得近期量子优势的关键，但 VQA 仍然面临着重要的挑战，包括其可训练性、准确性和效率。在这篇综述中，我们讨论了 VQA 令人兴奋的前景，并强调了实现量子优势的最终目标必须克服的挑战。


> **Fig. 1** ![[截图-1716362337266.png#R|Fig. 1|500]]VQA的输入是: 一个成本函数 $C(\vb*{\theta})$，$\vb*{\theta}$ 是一组编码问题解决方案的参数，一个 ansatz，其参数被训练以最小化成本，(可能)一组在优化过程中使用的训练数据 $\qty{\rho_k}$。这里，对于某些函数集 $\qty{f_k}$，代价通常可以用公式 (3) 的形式表示。*此外，ansatz 显示为参数化量子电路 (在左边)*，它类似于神经网络(也在右边显示示意图)。在循环的每次迭代中，使用量子计算机有效地估计成本(或其梯度)。该信息被输入到经典计算机中，该计算机利用优化器的功能来导航 cost landscape $C(\theta)$ 并解决 Eq.(1) 中的优化问题。一旦满足终止条件，VQA 输出对问题解决方案的估计。输出的形式取决于手头的精确任务。红色框表示一些最常见的输出类型。


# 2. 基本概念和工具

VQA 的主要优点之一是，它们*提供了一个可用于解决各种问题的通用框架。尽管这种多功能性转化为具有不同复杂程度的不同算法结构，但大多数(如果不是全部) VQA 都有一些共同的基本元素*。在本节中，我们将回顾 VQA 的构建模块。让我们从考虑一个希望解决的任务开始。这意味着要访问问题的描述，还可能访问一组训练数据。如图 1 所示，开发 VQA 的第一步是定义成本(或损失)函数 $C$，它编码问题的解决方案。然后人提出一种 ansatz, 即依赖于一组可以优化的连续或离散参数 $\vb*{\theta}$ 的量子操作(见下文对分析的更深入讨论)。然后在*hybrid quantum-classical loop*中训练这个 ansatz 来解决优化任务.

$$
\vb*{\theta}^* = \underset{\vb*{\theta}}{\arg \min}\ C(\vb*{\theta})\tag{1}
$$
VQA 的标志是它们使用量子计算机来估计成本函数 $C(\vb*{\theta})$ (或其梯度)，同时利用经典优化器的功能来训练参数 $\vb*{\theta}$. 在接下来的内容中，我们将为图 1 所示的 VQAs 体系结构的每个步骤提供额外的细节。

## 2.1. 成本函数

VQA 的一个关键方面是将问题编码成成本函数。与经典机器学习类似，成本函数将可训练参数θ的值映射为实数。更抽象地说，成本定义了一个超表面，通常称为成本全景 (见图1)，这样优化器的任务就是浏览全景并找到全局最小值。在不丧失一般性的前提下，成本可以表示为
$$
C(\vb*{\theta}) = f(\qty{\rho_k}, \qty{O_k}, U(\vb*{\theta})) \tag{2}
$$

其中 $f$ 为某个函数，$U(\vb*{\theta})$ 为参数化幺正，θ由离散参数和连续参数组成，$\qty{\rho_k}$ 为训练集的输入状态，$\qty{O_k}$ 为一组可观测值。通常，用这种形式来表示成本是有用的，也是可能的
$$
C(\vb*{\theta}) = \sum_k f_k (\Tr[O_k U(\vb*{\theta}) \rho_k U^\dagger(\vb*{\theta})])\tag{3}
$$
对于一些函数集 $\qty{f_k}$. 注意，选择 (2) 中的 $f$ 或者 (3) 中的 $\qty{f_k}$ 取决于手头的任务. 在优化过程中，使用 cost 或其梯度的 finite statistic estimator. (下面是用于训练代价函数的优化器的概述。)

现在让我们讨论成本函数应该满足的理想标准。首先，cost 必须是“*忠实的*”，因为 $C(\vb*{\theta})$ 的最小值对应于问题的解。其次，必须能够通过在量子计算机上进行测量并可能进行经典的后处理来“有效地估计” $C(\vb*{\theta})$. 这里隐含的假设是，*成本不应该用经典计算机有效地计算*，因为这意味着没有量子优势可以通过 VQA 实现。此外，$C(\vb*{\theta})$ 具有“操作意义”也是有用的，因此较小的成本值表示较好的解决方案质量。最后，代价必须是“可训练的”，这意味着它应该能够有效地优化参数θ。稍后我们将更详细地讨论vqa的可训练性问题。

为了在NISQ硬件中实现给定的VQA，用于估计C(θ)的量子电路必须保持电路深度和辅助要求小。这是由于NISQ器件容易发生门错误，量子位计数有限，并且这些量子位具有短的退相干时间。因此，构建高效的成本评估电路是VQA研究的一个重要方面。

## 2.2. Ansatzes

VQA 的另一个重要方面是它的分析。一般来说，ansatz 的形式决定了参数 $\vb*{\theta}$ 是什么，因此，如何训练它们以最小化代价。ansatz的具体结构通常取决于手头的任务，因为在许多情况下，可以使用有关问题的信息来定制ansatz。这些都是所谓的“问题启发型 ansatze”。然而，一些ansatz架构是通用的和“问题不可知论的”，这意味着即使在没有相关信息的情况下也可以使用它们。对于Eq.(3)中的代价函数，参数θ可以编码成一个幺正U(θ)，该U(θ)应用于量子电路的输入状态。如图 2 所示，$U(\vb*{\theta})$ 可以一般表示为 $L$ 个顺序应用的幺正变换的乘积
$$
U(\vb*{\theta}) = U_L(\vb*{\theta}_L) \cdots U_2(\vb*{\theta}_2) U_1(\vb*{\theta}_1)\tag{4}
$$
其中
$$
U_l(\vb*{\theta}_l) = \prod_m \me^{-\mi \theta_m H_m}W_m \tag{5}
$$

这里 $W_m$ 是一个未参数化的幺正, $H_m$ 是一个厄米算符; $\vb*{\theta}_l$ 是 $\vb*{\theta}$ 中的第 $l$ 个元素。下面我们将描述一些在文献中最广泛使用的分析，从那些可以表示为 Eq.(4) 的分析开始，然后呈现更一般的架构。

### 2.2.1. 硬件高效 ansatz

硬件效率 ansatz[^9]是用于, 旨在减少使用给定量子硬件时实现 $U(\vb*{\theta})$ 所需的电路深度的 ansatz 的通用名称。这里我们使用幺正 $W_m$ 和 $\me^{-\mi \theta_m H_m}$，它们取自一个门字母表(量子门的集合)，这个门字母表是由量子硬件特定的连通性和相互作用决定的，它避免了将任意幺正单位转换为易于在设备中实现的门序列所产生的电路深度开销。硬件高效 ansatz 的主要优点之一是它的多功能性，因为它可以适应编码对称性[^10][^11]，并使相关量子位更接近 depth reduction[^12]，同时对于研究类似于 device's 相互作用[^13]的哈密顿量特别有用。例如，局部自旋哈密顿量就是这种情况，尽管在这种情况下，启发式地表明，接近临界状态的 ansatz 需要与系统大小成比例的深度[^14]。此外，‘layered’ hardware efficient ansatzes，其中门作用于砖状结构中交替的量子比特对，已被突出地用作问题不可知论架构。然而，这种方法在随机初始化时可能导致可训练性问题。


### 2.2.2. Unitary coupled clustered ansatz

幺正耦合(UCC) ansatz 是一种 problem-inspired 型分析，广泛应用于量子化学问题，其目标是获得费米子分子哈密顿量 $H$ 的基态能量。UCC方法提出了一个候选的基态，该基态基于激发某个参考态 $\ket{\psi_0}$（通常是 $H$ 的 Hartree-Fock 态），形式为 $\me^{T(\vb*{\theta})−T(\vb*{\theta})^\dagger} \ket{\psi_0}$. 其中，$T =\sum_k T_k$ 为 cluster 算符[^15][^16]，$T_k$ 为激发算符。在所谓的 UCCSD ansatz (SD 代表 single 和 double)中，求和被截断以包含 single 激发 $T_1 =\sum_{i,j}\theta_i^j a_i^\dagger a_j$ 和 double 激发 $T_2 =\sum_{i,j,k,l} \theta_{i,j}^{k,l} a^\dagger_i a^\dagger_j a_ka_l$，其中 $\qty{a^\dagger_i}$ ($\qty{a_i}$) 是费米子产生(湮灭)算符。为了在量子计算机中实现这种解析，可以使用 Jordan-Wigner 或 Bravyi-Kitaev 变换[^17]将费米子算符映射到自旋算符，从而得到形式为 Eq.(4) 的 ansatz. 其中一些通过考虑更有效的编译费米子算符的方法来减小电路深度[^19][^20][^21][^22].

### 2.2.3. 量子 alternating 算符 ansatz

量子近似优化算法 (QAOA) 最初是为了求解组合优化问题[^23]的近似解而提出的。QAOA 中使用的 ansatz 涉及一个交替结构，通常称为量子交替算符 ansatz[^24]，与算法共享相同的首字母缩略词(尽管我们将在本评论中使用 QAOA 来指代算法)。在参考文献[^25]中，首先证明了该 ansatz 对某些哈密顿量具有计算上的通用性，并在参考文献[^26]中对由图集和超图集定义的 ansatz 族进行了推广证明。QAOA中的 ansatz 受到 Trotter 化绝热变换的启发，其中 Trotter 化的阶 $p$ 决定了解的精度。

这个 ansatz 的目标是将一个输入态 $\ket{\psi_0}$ 映射到一个给定问题哈密顿量 $H_P$​ 的基态，通过依次应用一个 problem unitary $\me^{-\mi \gamma_l H_P}$, 和一个 mixer unitary $\me^{-\mi \beta_l H_M}$​，其中 $H_M$​ 是一个称为 mixer 哈密顿量的厄米算符（参考文献[^27]）. 具体来说，该 ansatz 的形式为
$$
U(\vb*{\gamma}, \vb*{\beta}) = \prod_{l=1}^p
\me^{-\mi \beta_l H_M}\me^{-\mi \gamma_l H_P}
$$

### 变分哈密顿 ansatz
### 变量结构 ansatz

### sub-logical ansatz 与量子最优控制

## 2.3. 梯度





# 3. 应用

VQA 范式的主要优点之一是它允许面向任务的编程。也就是说，VQA 提供了一个可用于处理各种任务的框架。这导致 VQA 被提出用于量子计算机设想的基本上所有应用，事实上，已经证明 VQA 允许通用量子计算[^103]。在本节中，我们概述了 VQA 的一些主要应用程序及其实现状态。这些应用程序也在图 3 中进行了总结。我们还建议读者参阅第 V 节，概述 VQA 可能用于获得量子优势的应用程序。

## 3.1. 找到基态和激发态

最著名的 VQA 应用是估计给定哈密顿量的低特征态和相应的本征值。以前寻找给定哈密顿 $H$ 的基态的量子算法是基于绝热状态制备和量子相位估计子程序[^104][^105]，这两种算法都有超出 NISQ 时代的电路深度要求。因此，第一个被提出的 VQA，变分量子特征求解器 (VQE, variational quantum eigensolver)，被开发出来，为这项任务提供了一个近期的解决方案。在这里，我们回顾了原始的 VQE 体系结构和一些更先进的寻找基态和激发态的方法。

### 3.1.1. 变分量子特征求解器
> **Fig. 4** ![[截图-1716877175075.png#R|Fig. 4|200]]*变分量子特征求解器(VQE)的实现*。VQE 算法可以用来估计分子的基态能量 $E_G$。系统的相互作用用哈密顿量 $H$ 编码，通常表示为带系数 $c_k$ 的简单算符 $h_k$ 的线性组合。以 $H$ 为输入，VQE 输出基态能量的估计值 $\tilde{E}_G$. 图的下半部分显示了对 $H_2$ 分子电子结构问题的 VQE 实现的结果，其确切能量用虚线表示。实验结果是使用 IBM 超导量子处理器中五个量子比特中的两个获得的 (插图说明了量子比特的连接, 其中 $Q_0, \cdots, Q_4$ 表示量子位)。由于硬件噪声的存在，估计的能量 $\tilde{E}_G$ 与真实能量有差距。实际上，增大噪声强度(即 quantity $s$)会降低解的质量。然而，正如下面所讨论的，可以使用错误 mitigation 技术来提高解决方案的质量。图改编自参考文献[^106]，施普林格Nature Limited。

如图 4 所示，VQE 旨在寻找哈密顿 $H$ [^16]的基态能量 $E_G$. 这里的 cost 函数定义为 $C(\vb*{\theta}) = \ev*{H}{\psi(\vb*{\theta})}$. 也就是说，人们寻求最小化H在一个试态|ψ(θ)= U(θ)|ψ0上的期望值，对于一些状态U(θ)和初始态|ψ0。根据瑞利-里兹变分原理，如果|ψ(θ)是H的基态|ψ g，则代价为C(θ)EG是有意义且可靠的。在实践中，哈密顿函数H通常表示为泡利算符σk的乘积的线性组合:H =k ckσk (ck∈R)。使得成本函数C(θ)由σk期望值的线性组合得到。由于实际物理系统通常用稀疏哈密顿量来描述，因此成本函数可以在量子计算机上有效地估计，其计算成本通常最多随系统大小多项式增长。


[^1]: Peter W Shor, “Algorithms for quantum computation: discrete logarithms and factoring,” in Proceedings 35th annual symposium on foundations of computer science (Ieee, 1994) pp. 124–134.
[^2]: Seth Lloyd, “Universal quantum simulators,” Science 273, 1073–1078 (1996).
[^3]: Aram W Harrow, Avinatan Hassidim, and Seth Lloyd, “Quantum algorithm for linear systems of equations,” Physical Review Letters 103, 150502 (2009).
[^4]: “IBM Makes Quantum Computing Available on IBM Cloud to Accelerate Innovation,” (2016), press release at https://www-03.ibm.com/press/us/en/pressrelease/49661.wss.
[^5]: Adetokunbo Adedoyin, John Ambrosiano, Petr Anisimov, Andreas Bärtschi, William Casper, GopinathChennupati, Carleton Coffrin, Hristo Djidjev, David Gunter, Satish Karra, et al., “Quantum algorithm implementations for beginners,” arXiv preprint arXiv:1804.03719 (2018).
[^6]: J. Preskill, “Quantum computing in the NISQ era and beyond,” Quantum 2, 79 (2018).
[^7]: Frank Arute et al., “Quantum supremacy using a programmable superconducting processor,” Nature 574, 505–510 (2019).
[^9]:: A. Kandala, A. Mezzacapo, K. Temme, M. Takita, M. Brink, J. M. Chow, and J. M. Gambetta, “Hardware-efficient variational quantum eigensolver for small molecules and quantum magnets,” Nature 549, 242–246 (2017).
[^16]: A. Peruzzo, J. McClean, P. Shadbolt, M.-H. Yung, X.-Q. Zhou, P. J. Love, A. Aspuru-Guzik, and J. L. O’Brien, “A variational eigenvalue solver on a photonic quantum processor,” Nature Communications 5, 4213 (2014).
[^104]: Daniel S. Abrams and Seth Lloyd, “Quantum algorithmproviding exponential speed increase for finding eigenvalues and eigenvectors,” Phys. Rev. Lett. 83, 5162–5165 (1999).