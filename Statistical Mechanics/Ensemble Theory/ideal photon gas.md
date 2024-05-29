---
tags:
- Statistical_Mechanics
- Boson
- Photon
---

考虑一边长为 $L$ 的立方体容器，体积为 $L^3$. 内部的光子的动量为 $\require{physics}\hslash \vb*{k}$，螺旋度为 $\lambda=\pm 1$.

---

# $T$ 为[[绝对温标]]

令 $\require{physics}n_{\vb*{k}, \lambda}$ 为波矢为 $\require{physics}\vb*{k}$, 螺旋度为 $\lambda$ 的光子数目.
$$\require{physics} n_{\vb*{k},\lambda} = 0, 1, 2,\cdots$$
对任意的一组 $\require{physics} \qty{n_{\vb*{k}, \lambda}}$，对应的体系能量为
$$
E = \sum_{\qty{n_{\vb*{k}, \lambda}}} n_{\vb*{k}, \lambda} \hslash \omega, \quad \omega=ck
$$
因为是研究光子气系统的[[thermal equilibrium]]态，可将其看作无粒子交换的[[正则系综]]中的一个系统，光子作为[[理想玻色气体#玻色子|boson]]，其[[正则系综#配分函数|partition function]]为
$$\require{physics}\begin{aligned}
	Z &= \sum_{ \qty{n_{\vb*{k}, \lambda}}} e^{- \beta E}\\
	&= \prod_{\vb*{k}, \lambda} \qty(1 + e^{-\beta \hslash \omega} + e^{-2 \beta \hslash \omega} + \cdots)\\
	&= \prod_{\vb*{k}, \lambda} \frac{1}{1-e^{-\beta \hslash \omega}}
\end{aligned}$$
得到配分函数后，进而可以得到[[亥姆霍兹自由能]]
$$\begin{aligned}
A &= -k_B T \ln Z\\
&= -\sum_{\vb*{k}, \lambda} \ln \qty({1-e^{-\beta \hslash \omega}})
\end{aligned}$$

系统能量为
$$
	E = -\pdv{\beta} \ln Z
	= \sum_{\vb*{k}, \lambda} \frac{\hslash \omega e^{-\beta \hslash \omega}}{1 - e^{-\beta \hslash \omega}}
$$
[[blackbody radiation]]