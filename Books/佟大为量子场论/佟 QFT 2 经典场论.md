---
tags:
  - Book
  - 经典场论
  - 场论
created: 2023-06-20 21:05:33
aliases:
---

# 1.1 场的动力学

## 拉格朗日量

场的动力学是由*拉格朗日量*控制的，它是 $\phi(\vb*{x},t), \dot{\phi}(\vb*{x},t), \grad \phi(\vb*{x},t)$ 的函数。
在这门课中，拉格朗日量的形式是，
$$L(t) = \int\dd[3]{x} \mathcal{L}(\phi_a, \partial_\mu \phi_a)$$
其中, $\mathcal{L}$ 为拉格朗日密度. 

作用量为
$$
S = \int_{t_1}^{t_2}\dd{t} \int \dd[3]{x} \mathcal{L} = \int \dd[4]{x} \mathcal{L}
$$

我们可以用最小作用原理来确定运动方程。我们改变路径，保持端点不变，要求 $δS = 0$

最后得到*欧拉-拉格朗日方程*
$$
\partial_\mu \qty(
\pdv{\mathcal{L}}{ \qty(\partial_\mu \phi_a)}
)-\pdv{\mathcal{L}}{\phi_a} = 0
$$

## 1.1.1 Klein-Gordon方程
考虑一个标量场 $\phi(\vb*{x},t)$ 的拉格朗日量.
$$
\begin{align}
\mathcal{L} &= \frac12 \eta^{\mu \nu}\partial_\mu \phi\ \partial_\nu \phi - \frac12 m^2 \phi^2\\
&= \frac12 \dot{\phi}^2 - \frac12 (\grad \phi)^2 - \frac12 m^2 \phi^2
\end{align}
$$