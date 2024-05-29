---
tags:
  - 论文
created: 2023-11-15 11:14:14
aliases:
  - A Lanczos approach to the Adiabatic Gauge Potential
DOI: 10.48550/ARXIV.2302.07228
author:
  - Budhaditya Bhattacharjee
original title: A Lanczos approach to the Adiabatic Gauge Potential
year: "2023"
---
# 摘要

绝热规范势（AGP）是量子本征态之间绝热变形的生成器。构建AGP算符和评估AGP范数有许多方法。最近提出可以使用一种类似于Gram-Schmidt的算法来明确评估AGP的表达式[1]。我们采用了这种方法的一种版本，使用Lanczos算法来评估Krylov向量的AGP算符和 Lanczos 系数的AGP范数。这种方法的优势在于在分析表达式中评估AGP算符的嵌套对易子时最小化冗余。该算法用于明确构建一些简单系统的AGP算符。我们推导了AGP范数与变形算符的自相关函数之间的积分变换关系。我们提出了对变分方法的修改，以导出调节后的AGP范数。利用这一点，我们对AGP进行了不同程度的近似。最后，我们根据算子增长假设比较和对比了AGP和K-复杂度在探测量子混沌方面的能力。

# 2. 绝热本征态变形

考虑一个依赖于可调参数 $\lambda$ 的哈密顿量 $H(\lambda)$。在 $\lambda$ 的瞬间，$H$ 的本征态定义如下
$$
H(\lambda) \ket{n(\lambda)} = E_n(\lambda) \ket{n(\lambda)}
$$
其中 $\ket{n(\lambda)}$ 是具有对应本征值 $E_n(\lambda)$ 的本征态。绝热规范势，或 AGP，是通过转换到以 $\lambda$ 为特征的瞬时能量基的运动参考系引入的。在这个运动参考系中，哈密顿量是对角化的。这可以通过考虑在运动参考系中状态 $\ket{\psi}$ 的时间演化来观察，其中它变成 $\ket{\tilde{\psi}} = U^\dagger(\lambda(t)) \ket{\psi}$. 这里，$U$ 是在两个基之间进行转换的幺正算符. 出于通用性考虑，参数 $\lambda$ 被认为是时间 $t$ 的函数。

在运动参照系中，状态演化为
$$
\mi \hs \partial_t \ket{\tilde{\psi}} = (U^\dagger H U -\mi \hs \dot{\lambda} U^\dagger \partial_\lambda U) \ket{\tilde{\psi}}
$$
第一项 $U^\dagger H U$ 根据定义是对角的。非对角的贡献来自第二项 $\mi \hs \dot{\lambda} U^\dagger \partial_\lambda U$. 这个项负责描述本征态之间的激发，由速度 $\dot{\lambda}$ 量化。在移动参照系中，AGP 被定义为这个非对角项.



# 3. Lanczos 算法和 Krylov 复杂度

Krylov 复杂度的概念涉及选择适当的基（在算符或状态的希尔伯特空间中），以描述算符的时间演化。虽然可能存在无限多种这样的基础，但存在一种唯一的选择，对应于相对于某个适当定义的 cost functional 而言的最小基础。本文仅讨论算符复杂度。关于状态复杂度及其应用，读者可参阅文献[20, 45, 46, 50]。

确定适当的基础（称为 Krylov 基础）涉及将时间演化算符 $\mathcal{O}(t)$ 表示为嵌套对易子的形式。这是根据 Baker-Campbell-Hausdorff 公式得出的。

$$
\begin{align}
\mathcal{O}(t) &= \me^{\mi Ht/\hs} \mathcal{O} \me^{-\mi Ht/\hs}\\
&= \mathcal{O} + \frac{\mi t}{\hs} \comm{H}{\mathcal{O}}
+ \frac{(\mi t)^2}{2!\ \hs^2} \comm{H}{\comm{H}{\mathcal{O}}}
+ \frac{(\mi t)^3}{3!\ \hs^3} \comm{H}{\comm{H}{\comm{H}{\mathcal{O}}}}+\cdots
\end{align}
$$




## A. Universal 算符增长假说

# 4. THE FORMALISM

## A. 响应函数

# 5. 矩阵方程

## A. 一组线性方程

# 6. 分析实例

## A. 两能级系统

## B. 二量子位系统

# 8. 数值结果

# 9. 探索量子混沌: AGP 和算子生长假说

