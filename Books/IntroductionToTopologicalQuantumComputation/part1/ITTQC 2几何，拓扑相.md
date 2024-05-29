---
tags: Book
number headings: first-level 1, max 6, 1.1.
created: 2023-05-13 00:49:37
---

Anyonic statistics 通过交换两个 anyons 时的 phase factor 来展现。这个物理过程与 [[Aharanov-Bohm 效应]] 非常类似，一个带电粒子的波函数在环绕一个被限制在一个无限长螺线管内的磁通时会获得一个相位因子。这个相位与路径细节无关，而只与绕行次数有关。

在 highly correlated systems 中可以出现有效的磁通和电荷。我们描述这些有效磁通，电荷间相互作用的最好方式就是通过所谓的 geometric phases，或者说 [[Berry 相位|Berry phases]].

复杂相位在考虑系统部分的演化时变得重要。这是不同部分之间的干涉实验的情况，可以确定它们的相对相位。这样的例子包括[[double slit experiment]]、[[Aharanov-Bohm 效应]] 和 [[Berry 相位]]。此外，量子相位是量子物理学中一些奇特效应的核心，如 [[adiabatic approximation]] 和 [[Anderson localisation]]。

我们将在 [[gauge field]] 和 [[geometric evolutions]] 的背景下研究量子相位的出现。这将有助于我们直观地了解任意子物理学。我们将详细研究几何相位，因为它们的许多性质都适用于任意子的编织演化情况。最后，我们将介绍整数量子霍尔效应的主要机制，它涉及到规范场和几何相位的物理。

# 规范场中的量子相

当一个带电粒子在 [[gauge field]] 中的运动，将会导致它的波函数获得一个 quantum phase. [[Aharanov-Bohm 效应]] 描述了带电粒子绕过无法到达的磁通是产生的相位变化。

## 磁场中的带电粒子

磁场可以通过磁矢势 $\vb*{A} = (A_x,A_y,A_z)$ 描述
$$\vb*{B} = \curl \vb*{A}$$

$$H^A = -\frac{\hslash^2}{2m} \qty(\grad - \mi \frac{q}{c\hslash}\vb*{A})^2$$

如果当 $\vb*{A} = 0$ 时，$\psi(\vb*{r})$ 是哈密顿量的本征态，则当 $\vb*{A}\neq0$ 时，相同能量的本征态可表示为

$$
\psi^A(\vb*{r}) = \exp \qty[\mi \frac{q}{c\hslash}\int_{\vb*{r}_0}^\vb*{r} \vb*{A} \qty(\vb*{r}')\vdot \dd{\vb*{r}'}]\psi(\vb*{r})
$$

本征态 $\psi^A(\vb*{r})$ 显示了相位因子与 [[gauge field]] 的关系。如果某个粒子沿着闭合回路 $\mathcal{C}$ 进行绝热移动，且忽略其他的相互作用，如电荷 $q$ 与磁场 $\vb*{B}$.

则此时相位变化为
$$\varphi = \frac{q}{c \hslash} \oint_{\mathcal{C}} \vb*{A} \vdot \dd{\vb*{r}}$$

利用 [[斯托克斯定理]] 
$$\frac{q}{c \hslash} \oint_{\mathcal{C}} \vb*{A} \vdot \dd{\vb*{r}} = \frac{q}{c \hslash} \iint_\mathcal{S} \curl \vb*{A} \vdot \vu*{n} \dd{s} = \frac{q}{c\hslash} \iint_\mathcal{S} \vb*{B} \vdot \vu*{n} \dd{s} = \frac{q}{c\hslash} \Phi$$

$\Phi$ 是通过了曲面 $\mathcal{S}$ 的磁通。所以，相位变化是 [[gauge invariant]]，即相位变化并不依赖于 $\vb*{A}$ 的选择。如果我们施加一个单位磁通 $\Phi_0 = hc/q$，则相位变化 $\varphi = 2\pi$. 

## Aharonov-Bohm effect

让我们考虑一个磁通被限制在一个无限不可穿透的管道中的情况。我们让一个带电粒子在垂直于管道的平面上移动。即使粒子在没有任何电磁场的区域内运动，它也可以获得相位因子。这个相位由矢势 $\vb*{A}$ 的线积分给出，该矢势在螺线管外部是非平凡的。 

特别地，我们考虑一个磁场被限制在一个无限小的螺线管内，通过它有有限的磁通 $\Phi$。如果我们把螺线管放在坐标系的原点，相应的矢势
$$\vb*{A}(\vb*{r}) = \qty(-\frac{y \Phi}{2 \pi r^2}, \frac{x\Phi}{2 \pi r^2}, 0)$$

## 任意子与AB效应
