---
tags:
- QuantumMechanics
---

# 坐标表象

## 坐标本征函数

坐标算符 $\hat{x}$ 的本征方程为
$$
\hat{x}\ \delta(x-x') = x'\ \delta(x-x')
$$
>[!proof] 证明
>$$
>\int_{-\infty}^\infty f(x)\ \delta(x)\dd{x} = f(0)
>$$
>$$
>\int_{-\infty}^\infty x\ \delta(x)\dd{x} = 0
>$$
>由于 $x\ \delta(x)$ 在 $x \neq 0$ 处都为 $0$，得到 $x\ \delta(x) = 0$.
>由 $x$ 的任意性，替换成 $x-x'$
>
>$$
>\begin{align}
>(x-x') \delta(x-x') &= 0\\
>x\ \delta(x-x') &= x'\ \delta(x-x')
>\end{align}
>$$



$$\ip{x}{x'} = \delta(x-x')$$
$$
\ket{\psi(t)} = \mathbb{1}\ \ket{\psi(t)} = \int \dd{x} \ket{x} \ip{x}{\psi(t)} = \int \dd{x} \ket{x} \psi(x,t)
$$


---

# 动量表象

---


# 能量表象










