---
tags:
  - 论文
created: 2023-09-29 06:42:36
aliases:
  - Nonlinear response of the Kitaev honeycomb lattice model in a weak magnetic field
DOI: https://doi.org/10.1103/PhysRevB.107.134404
author:
  - M. Kazem Negahdari
  - Abdollah Langari
original title: Nonlinear response of the Kitaev honeycomb lattice model in a weak magnetic field
year: "2023"
---

# 0. 摘要

我们使用二维相干光谱理论研究了在弱磁场下 Kitaev 蜂窝格子模型的非线性响应。我们观察到，在该模型的非阿贝尔相中的各向同性点，二维频域的非线性谱由来自通量激发和 Majorana 束缚态的尖锐信号组成。在这个谱中，可以清晰地观察到不同通量激发的特征，因此可以观察到具有 4 相邻、2 非相邻和 4 远离的通量的状态的迹象，这在线性响应光谱（例如中子散射实验）中是不可见的。此外，在阿贝尔相中，我们观察到频率域中的谱由条纹状信号组成。这些信号，就像在纯 Kitaev 模型的非线性响应中一样，代表了漫游的 Majorana 费米子的明显特征。然而，在阿贝尔相的深处，每当 Kitaev 交换耦合远远强于其他耦合时，这些条纹信号会减弱，只能看到响应中的单个尖锐点，这类似于传统的 toric code 的无色散响应。

# 1. 引言

在量子自旋液体(QSL) [^1][^2][[量子自旋液体：综述|]][^3][^4][^5][^6][^7][^8][^9][^10][^11]中，即使在非常低的温度下，量子涨落也能克服传统的磁序。因此，对QSL状态的描述超出了传统磁性相的框架。自从Anderson于1973年首次引入QSL以来，新颖的概念，如演生规范场（emergent gauge fields）、分数自旋激发（fractional spin excitations）以及实现可靠的量子存储器的潜在可能性，使得QSL的研究一直是一个重要的课题。

在寻找 QSL 相的过程中，具有精确QSL基态的Kitaev蜂窝格子模型（KM）为在实际材料中实现QSL相打开了一条有希望的途径。根据 Kitaev 的部分子构造，在该构造中，格点上的每个自旋被四个 Majorana 费米子取代，初始哈密顿量的键相关 Ising 相互作用在演生 $Z_2$ 规范场的存在下被转化为 Majorana 费米子的跃迁哈密顿量。在 KM 上施加一个弱磁场后，无能隙激发会产生能隙，系统有效地由在三自旋相互作用项存在的情况下的 Kitaev 模型来描述，我们简称为扩展 Kitaev 蜂窝格子模型（EKM），这仍然是*可以精确求解*的。施加的磁场增强了 EKM 的相图，显示出阿贝尔和非阿贝尔的有能隙相。在非阿贝尔相中，任何 $2n$ 规范通量的存在都会在能隙内施加 $n$ 个 Majorana 束缚态，这是该模型中非阿贝尔任子的特征。

# 3. 模型

扩展 Kitaev 模型描述了由纯 Kitaev 项和三种自旋相互作用组成的蜂窝晶格上的自旋 $1/2$ 自由度。这个模型是一个有效的理论，它是通过微扰扩张得到的，用来解释弱磁场对基塔耶夫模型的影响

$$
H_{EK} = -\sum_{\ev{ij}_\alpha}J_\alpha \hat{\sigma}_i^\alpha
\hat{\sigma}_j^\alpha - K\sum_{\begin{array}\ev{ik}_\alpha,\ev{kj}_\beta\\ \gamma \perp \alpha, \beta \end{array}}\hat{\sigma}_i^\alpha \hat{\sigma}_k^\gamma \hat{\sigma}_j^\beta
$$
