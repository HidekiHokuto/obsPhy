---
tags:
  - 论文
created: 2024-05-14 00:15:16
aliases:
  - Simulation of topological field theories by quantum computers_Freedman
DOI: 10.1007/s002200200635
author:
  - "[[Michael Freedman|Michael H. Freedman]]"
  - "[[Alexei Kitaev]]"
  - "[[Zhenghan Wang]]"
original title: Simulation of topological field theories by quantum computers
year: "2006"
---
量子计算机将通过局部门来演化小(例如二)维希尔伯特空间的高张量功率，这可以通过在时间 $t$ 上应用局部哈密顿量 $H$ 来实现。与此量子工程相反，理论物理最抽象的领域已经产生了“拓扑模型”，它具有有限维的内部状态空间，没有自然张量积结构，并且状态的演化是离散的，$H \equiv 0$. 这些被称为拓扑量子场理论 (tqft)。这些奇异的物理系统被证明可以在量子计算机上有效地模拟。结论有两点:
1. tqft不能用来定义一个比通常的量子模型“BQP”更强的计算模型。
2. tqft提供了一种完全不同的看待量子计算的方式。tqft丰富的数学结构可能提供一种新的量子算法。

# 1. 引言

拓扑量子场论(TQFT)是一种数学抽象，它将共形场论和 Chen-Simons 理论中的拓扑主题进行了编码。拓扑量子场论的严格 2 维部分称为拓扑模函子(TMF)。它(本质上)赋予每个曲面 $\Sigma$ 一个有限维复希尔伯特空间 $V(\Sigma)$，并赋予曲面的任何(自)微分同态 $h$ 一个线性(自)同态 $V(h):V(\Sigma) \to V(\Sigma')$. 我们将注意力限制在幺正拓扑模函子(UTMF)上，并证明量子计算机可以有效地将任意UTMF的变换模拟为其计算状态空间上的变换。我们应该强调，我们讨论的双方目前都是理论性的:执行我们模拟的量子计算机也是一个数学抽象-量子电路模型(QCM) [D][Y]。对于实现这个模型存在非常严肃的建议，也许在硅中，例如[Ka]，但我们不会讨论这方面。
