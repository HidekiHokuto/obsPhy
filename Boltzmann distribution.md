---
tags:
- StatisticalMechanics
number headings: auto, first-level 1, max 6, 1.1.
created: 2023-04-23 01:02:46
---

In statistical mechanics, **Boltzmann distribution** is one kind of distributions. According to it, the probability that a system is in a certain state is a function of the *energy* and *temperature of that state* as below
$$p_i \propto \exp{\qty(-\beta \varepsilon_i)}$$
其中 $p_i$ 是系统处于状态 $i$ 的概率，$\varepsilon_i$ 是该状态的能量，$k_\text{B}T$ 为玻尔兹曼常数和热力学温度 $T$ 的乘积。

两种状态的概率比称为***Boltzmann factor***，其特征在于其仅取决于***两状态之能量差***：
$$
\frac{p_i}{p_j} = \text{e}^{(\varepsilon_j - \varepsilon_i)/(k_\text{B} T)}
$$

玻尔兹曼分布以[[Ludwig Eduard Boltzmann|Boltzmann]]的名字命名，他于1868年研究[[thermal equilibrium]]中气体的统计力学时首次提出了这一分布。

玻尔兹曼的统计力学成果证明于他的论文《论热力学第二定律与热平衡状态的概率之间的关系》。该分布后来被[[Josiah Willard Gibbs]]以现代通用的形式进行了广泛的研究。

广义玻尔兹曼分布是[[熵]]的统计力学定义（[[吉布斯熵公式]] $S = -k_\text{B} \sum_i p_i \ln p_i$）和[[熵]]的热力学定义 $\dd{S} = \dfrac{\delta Q_{\text{rev}}}{T}$ 等价的充分必要条件。