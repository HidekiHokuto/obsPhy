---
tags:
  - 论文
  - 费米液体
  - Kitaev-Kondo晶格
  - Kondo晶格模型
created: 2023-06-08 03:45:47
aliases: 
原标题: Fractionalized Fermi liquids and exotic superconductivity in the Kitaev-Kondo lattice
---

# Abstract

分数化费米液体（FL$^*$）被引入作为非费米液体金属相，其特征是共存的类电子荷载体和形成 fractionalized spin liquid 的局域磁矩。在这里，我们研究了一个基于蜂窝格子上的 Kondo lattice model，其中局域磁矩之间存在 Kitaev 相互作用，这是一个基于 [[Alexei Kitaev|Kitaev]] 的 $Z_2$ 自旋液体构建的具体模型，可以产生 FL$^*$ 相。我们通过微扰论表征 FL$^*$ 相，并采用 Majorana-fermion 平均场理论绘制出完整的相图。最引人注目的是，我们发现了一种 nematic triplet superconducting phases，它掩盖了分数化和传统费米液体相之间的量子相变。它们的配对结构继承自 Kitaev 自旋液体，也就是说，超导性是由 Majorana glue 引起的。

# I. INTRODUCTION

具有 strong electronic correlations 的金属可以拥有多种迷人的相，包括 unconventional spin 和 charge density waves 以及高温超导。此外，它们通常表现出与 Fermi-liquid phenomenology 有显著偏离的特征。这些偏离可以有各种来源：异常低的coherence temperatures，nearby quantum critical points，quenched disorder，或者它们可能是真正的非费米液体相的特性[1-4]。

尽管稳定的非费米液体行为对一维相互作用电子是普遍的，但在更高维度中，理论上确立的例子是罕见的。其中一个例子是 fractionalized Fermi-liquid phases，被称为 FL$^*$ 相。受 heavy-fermion non-Fermi liquids 的启发，FL$^*$ 最初被提议作为近藤格子模型的相，其中 Kondo screening 是无效的，而局域磁矩则形成了一个分数化自旋液体态[5,6]。在多轨道或多带 Hubbard 模型的背景下，FL$^*$ 相是一种 orbital-selective Mott 相，其中一组带经历了 Mott transition [7,8]。FL$^*$ 的一个定义特征是存在一个常规电荷-自旋 1/2 准粒子的费米面，然而，它围绕的动量空间体积仅由导电电子决定，因此通常以一种 quantized fashion 违反了 [[Luttinger's theorem]]。

最近，分数化费米液体被提议作为低掺杂铜氧化物的 pseudogap regime 的候选相[9-11]，这个概念受到早期将铜氧化物描述为掺杂自旋液体的想法的启发[12]。与重费米子情况的主要区别在于，对于对铜氧化物的单带描述，局域磁矩和掺杂空穴在同一带中共存，因此无法达到两个 FL$^∗$ components 的 asymptotic
decoupling.