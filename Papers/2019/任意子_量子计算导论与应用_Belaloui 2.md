---
tags:
  - 论文
created: 2024-04-30 14:46:35
aliases:
  - "Anyons: Introduction and Application to Quantum Computation_Belaloui"
DOI: 10.13140/RG.2.2.34212.71042
author:
  - Nacer eddine BELALOUI
original title: "Anyons: Introduction and Application to Quantum Computation"
year: "2019"
---
这是一篇硕士论文

# 导言

量子计算已经进入了信息处理的世界，带来了更高效、更快的计算机的承诺，这将帮助我们在解决当前经典计算机过于复杂和困难的问题方面取得巨大飞跃。然而，它带来了退相干的失望和与此现象相关的信息丢失。正是这个实际问题阻碍了下一个里程碑——量子计算机的发展。目前正在研究许多可以克服这一障碍的方法。他们中的大多数人都专注于将量子比特的物理介质与环境和外部扰动隔离开来[^1][^2]，同时寻找方法来纠正这些支撑体的脆弱性所导致的错误[^1][^2]。

除了这些看似直接的解决退相干问题的方法之外，还有一种截然不同的方法: 与其将信息隐藏在环境之外，为什么我们不传播它，让它变得难以——不是难以发现，而是难以改变? 这意味着量子比特不会在脆弱的物理介质(例如电子)上编码，而是在足够大的介质上编码，这种介质将更难操纵，因此小的扰动将很难改变其量子特性。换句话说，这些信息将由一个更大、更健壮的物质属性来实现。其中一个性质就是物质的拓扑状态[^2]。

这就是拓扑量子计算(TQC)的意义所在! 本工作的目标是简要描述这种实现的理论框架，并在数值上解决实现量子门的问题。

我们将首先从第一章开始描述一个重要的中心概念，即任意子准粒子。它的统计特性对于在TQC框架中实现量子比特和量子门是必不可少的。我们将看到这些准粒子，它们只能存在于二维空间，有一个有趣的统计演化，可以被认为是介于玻色子和费米子之间的粒子。我们将看到为什么它们只能存在于二维中，以及为什么它们是实现拓扑量子计算机的适当工具。

在第2章中，我们将提出一个量子计算模型——量子比特和量子门——它利用任意子首先存储信息，然后对其进行操作。这个模型被称为斐波那契模型，因为它利用了所谓的斐波那契任意子。在本章中，我们还描述了在这样一个模型中我们需要使用的所有工具和概念。

第三章将简短地讨论斐波那契模型中的量子比特和量子门。我们如何使用任意子实现量子位以及我们如何通过编织或编织这些任意子来改变这些量子位的状态。我们将展示Solovay和Kitaev的一个定理，保证这些编织可以实现任何量子门。

第四章是本文的核心。我们将介绍寻找辫子或编织的方法，它可以将任何量子门实现到一定的精度。我们将展示一些结果，并解释用于获得这些结果的算法。

最后，附录将为读者提供第4章中描述的算法的Python实现。

# 1. 任意子

## 1.1. 二维统计

不像在通常的三维量子力学中，粒子可以是费米子或玻色子，分别对应于自旋的半整数和整数值，二维粒子的行为可以不属于这两种类别[^3][^4]。

让我们考虑两个难以区分的粒子在三维空间中演化。这些粒子应该有相同的量子数[^5]。在量子力学中，两个粒子的波函数可能会重叠，因此不可能分别跟踪它们。因此，当描述一个由两个粒子组成的系统时，我们应该对它们两个使用一个共同的波函数[^4]。

设 $\psi(1,2)$ 是这样一个波函数，描述两个全同粒子:粒子 1 和粒子 2。将质点 2 绕质点 1 旋转一个角 $\Delta \phi$，得到 $\psi(1,2)$ 的复相，如
$$
\psi(1,2) \to \psi'(1,2) = \me^{\mi \nu \Delta \phi} \psi(1,2) \tag{1.1.1}
$$

这表明在三维空间中交换两个不可区分的粒子给波函数 $\psi(1,2)$ 一个 $\pm 1$ 的相位因子。这两个可能的相位因子对应于三维空间中玻色子和费米子的两种唯一可能的统计量。

然而，在二维空间中，不存在 eq.(1.1.2) 这样的等式，因为图 1.1 中的路径是不相等的，因为不存在将我们从路径(a)带到路径(b)的连续变形。因此，我们对统计量 $\nu$ 没有约束，我们应该有不止两个统计量[^3][^6][^4]。在这种情况下，粒子既不是玻色子也不是费米子。它们可以有任何统计数据，被称为Anyons[^16]。

这是拓扑量子计算的一个关键特性! 与费米子或玻色子进行多次交换时，任意子都能显示出更丰富的统计演化。这是因为不会如同玻色子和费米子的情况一样, 最终相位因子只是 $\pm 1$，相反，它可以根据统计值 $\nu$ 取一个大范围的值[^3]。

## 1.2. 创造一个二维世界


# 2. 斐波那契模型

由于拓扑量子计算机使用任意子及其统计演化来进行计算，任何 TQC 模型都应该描述这些任意子相互作用的方式以及任意子系统如何随时间演化。

我们可以简单地总结如下:
$$
\text{TQC Model}=\text{Anyons}+\text{Fusion/Splitting}+\text{Braiding}
$$
在我们的模型中，我们将使用斐波那契任意子。对应式 (1.1.1) 中的 $\nu = 12/5$[^9].

## 2.1. 斐波那契任意子和融合规则
### 2.1.1. 阿贝尔和非阿贝尔任意子

如前所述，任意子可以在真空中成对产生，也可以通过将一个任意子分裂成两个任意子产生。

让我们这样定义任意子电荷的概念: 任意子的电荷为 $1$，真空的电荷为 $0$. 这个电荷在有限的空间区域内是守恒的。因此，从真空中产生的两个任意子的总电荷为 $0$，而母任意子分裂后产生的两个任意子的总电荷为 $1$。在接下来的工作中，任意子和真空也将被称为它们各自的电荷。这两对任意子的聚变过程如图 2.1 所示。这些融合的结果被称为融合通道[^3]。

在我们的模型中，从上面所述的电荷守恒规则可以清楚地看出，任何一对任意子都可能融合成两个粒子: 一个任意子或真空，这取决于它们是如何产生的。然后说这些对具有多个聚变通道。在其他模型中，它们可能有一个独特的融合通道。属于第一类的任意子称为非阿贝尔子，而后者称为阿贝尔子。在斐波那契模型中，只使用非阿贝尔任意子。

### 2.1.2. Fusion 规则

我们可以把两个粒子 $a$ 和 $b$ 融合成一个粒子 $c$ 的过程写成如下的代数形式:
$$a \times b = c.$$
> **Fig. 2.1** ![[截图-1715659300068.png#R|Fig. 2.1|300]]
> 
> (a): 两个总电荷为 $0$ 的任意子 fuse 成真空
> 
> (b):两个总电荷为 $1$ 的任意子 fuse 成另一个任意子

现在我们可以详细说明模型的融合规则如下
$$
\begin{align}
1 \times a &= a\\
a \times 1 &= a\\
0 \times 0 &= 0\\
1 \times 1 &= 0+1
\end{align}
$$

## 2.2. 在斐波那契模型中操纵任意子: $F$ 和 $R$ 矩阵

一旦我们的任意子被创造出来，人们就可以操纵它们来改变它们融合的结果。

### 2.2.1. 改变融合的顺序: $F$ 矩阵
对于三个任意子或更多，我们可以选择我们想要融合它们的顺序。然而，最终结果不会受到影响，因为这些任意子在聚变前的总电荷总是守恒的。

通过 $F$ 矩阵 $\qty(F_{abc}^d)_j^i$ 的一个或多个应用，将一种 fusion 的顺序映射到另一个种 fusion 的顺序，如图2.2所示。

> **Fig. 2.2** ![[截图-1715664302555.png#R|Fig. 2.2|300]]这张图显示了不同顺序的融合是如何相互映射的。$a, b, c$ 是最初的 3 个任意子，$i$ 和 $j$ 是第一次聚变的结果，$d$ 是最终的任意子[^3].




为了计算 $F$ 矩阵的元素，我们可以构造一个一致性方程: 考虑四个从左到右标记为1,2,3和4的任意子，以及一个聚变过程，在这个过程中，我们聚变最左边的任意子，直到我们最终只得到一个任意子(从左到右聚变)。现在我们来考虑一下左右融合。如图2.2所示，我们总是可以使用f矩阵从一个过程转到另一个过程。图2.3显示了两种可能的方法。因为这两种方法是等价的，我们有

# 3. 斐波那契模型中的量子比特和量子门

现在我们已经描述了允许我们处理斐波那契任意子的框架，我们可以开始处理使用它们来实现量子比特和量子门的任务。

## 3.1. 实现一个量子位

在我们的拓扑量子计算机模型中，我们将在一组三个任意子[^10]中编码一个量子位。这些任意子可以从左到右融合成一个定义良好的中间和最终任意子序列。根据上一章描述的聚变规则，我们得到了三个初始任意子的三种可能的聚变，如图3.1所示。



# 4. 拓扑量子门结构

在描述了我们的拓扑量子计算机模型之后，我们需要继续寻找方法来实际操作我们的量子比特以用于计算目的。在本章中，我们将重点讨论一种蛮力方法，用于寻找给定长度的 weaves，它近似于最佳的目标量子门。

## 4.1. 近似于单量子位量子门

如前所述，在我们的斐波那契模型中，将量子门应用于单个量子比特是通过编织量子比特的三个任意子来实现的。找到与给定量子门对应的编织可以通过简单的蛮力搜索来完成，我们尝试所有可能的编织模式，直到给定数量的交换，并保留最接近目标门的那个。

# 5. 附录: Python代码


[^1]: M. A. Nielsen and I. L. Chuang, Quantum computation and quantum information. Cambridge University Press, 2010.[[量子计算和量子信息_Nielsen,Chuang]]
[^2]: G. P. Collins, “Computing with quantum knots,” Scientific American, vol. 294, no. 4, p. 56–63, 2006.
[^3]: J. K. Pachos, Introduction to topological quantum computation. Cambridge University Press, 2012.[[拓扑量子计算导论_Pachos]]
[^4]: A. Lerda, Anyons: quantum mechanics of particles with fractional statistics. Springer-Verlag, 1992.
[^5]: Y. Omar, “Indistinguishable particles in quantum mechanics: an introduction,” Contemporary Physics, vol. 46, no. 6, p. 437–448, 2005.
[^6]: A. Khare, Fractional statistics and quantum theory. World Scientific, 2005.
[^7]: L. Hormozi, N. E. Bonesteel, and S. H. Simon, “Topological quantum computing with read-rezayi states,” Physical Review Letters, vol. 103, no. 16, 2009.
[^8]: A. Tounsi, “Topological phase of matter and application to quantum computation,” Master’s thesis, Universit´e des Frères Mentouri - Constantine 1, 2019.
[^9]: S. Trebst, M. Troyer, Z. Wang, and A. W. W. Ludwig, “A short introduction to fibonacci anyon models,” Progress of Theoretical Physics Supplement, vol. 176, p. 384–407, 2008.
[^10]: L. Hormozi, G. Zikos, N. E. Bonesteel, and S. H. Simon, “Topological quantum compiling,” Physical Review B, vol. 75, Nov 2007.
[^11]: N. E. Bonesteel, L. Hormozi, G. Zikos, and S. H. Simon, “Braid topologies for quantum computation,” Physical Review Letters, vol. 95, no. 14, 2005.
[^12]: I. Khiat, “Braid theory and knot theory: Introduction and application to quantum computation,” Master’s thesis, Universit´e des Frères Mentouri - Constantine 1, 2019.
[^13]: B. Field and T. Simula, “Introduction to topological quantum computation with non-abelian anyons,” Quantum Science and Technology, vol. 3, p. 045004, Oct 2018.
[^14]: S. H. Simon, N. E. Bonesteel, M. H. Freedman, N. Petrovic, and L. Hormozi, “Topological quantum computing with only one mobile quasiparticle,” Physical Review Letters, vol. 96, no. 7, 2006.
[^15]: A. Benslama, “Weekly group meeting presentations (tqc team, lpms, constantine 1),” 2019.
[^16]: F. Wilczek, “Quantum mechanics of fractional-spin particles,” Physical Review Letters, vol. 49, p. 957–959, Apr 1982.