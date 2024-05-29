---
tags:
- Scattering
---

# 刚球散射
$$b=R \sin \alpha = R \sin \qty(\frac{\pi}{2}-\frac{\theta}{2}) = R \cos \qty(\frac{\theta}{2})$$

$$\theta = \left\{\begin{eqnarray}&2 \arcsin(b/R) &\quad (b \leq R)\\&0 &\quad (b > R)\end{eqnarray}\right.$$

---

## 散射截面

![[散射角.jpg|500]]

可见 $\dd{\sigma}$ 越大，[[solid angle]] $\dd{\varOmega}$ 范围也越大，存在比例系数 $D(\theta)$，称作**散射截面**
$$\dd{\sigma} = D(\theta) \dd{\varOmega}$$
分别写下表达式
$$
\dd{\sigma} = b \dd{b}\dd{\phi}, \quad \dd{\varOmega} = \sin \theta \dd{\theta} \dd{\phi}
$$
$$D(\theta) = \frac{b}{\sin \theta} \abs{\dv{b}{\theta}}$$

于是刚体球的**散射截面**为
$$
\begin{align}
D(\theta) &= \frac{R \cos \frac{\theta}{2}}{\sin \theta}
\frac12 R \sin \frac{\theta}{2}\\
&= \frac{R^2}{4}
\end{align}
$$

然后计算刚球散射的**总散射截面**
$$
\begin{align}
\sigma &= \int_0^{4\pi} D(\theta) \dd{\varOmega}\\
&= \frac{R^2}{4} \int_0^{4\pi} \dd{\varOmega}\\
&= \pi R^2
\end{align}
$$
刚好就是刚体球的横截面积.

---
### 粒子数角度

另一方面，设入射粒子束的强度为 $J$，则单位时间内通过 $\dd{\sigma}$，散射到[[solid angle]] $\dd{\varOmega}$ 的粒子数为
$$\dd{N} = J\dd{\sigma} = J D(\theta)\dd{\varOmega}$$
$$D(\theta) = \frac1J \dv{N}{\varOmega}$$
即只要测定单位[[solid angle]]的散射粒子数，再除以粒子束强度，就可以得到散射截面.

---


# 卢瑟福散射（Rutherford scattring）


通过[[角动量]]守恒得到

$$b = \frac{1}{8 \pi \epsilon_0} \frac{q_1 q_2}{E} \cot{\qty(\frac{\theta}{2})}$$

然后计算散射截面，先计算 $\dv{b}{\theta}$

$$
\dv{b}{\theta} = -\frac{1}{16 \pi \epsilon_0} \frac{q_1 q_2}{E} \csc^2 \qty(\frac{\theta}{2})
$$

散射截面
$$
\begin{align}
D(\theta) &= \frac{b}{\sin \theta} \abs{\dv{b}{\theta}}\\
&= \frac{1}{8 \pi \epsilon_0} \frac{q_1 q_2}{E} \cot{\qty(\frac{\theta}{2})} \frac{1}{\sin \theta}
\frac{1}{16 \pi \epsilon_0} \frac{q_1 q_2}{E} \csc^2 \qty(\frac{\theta}{2})\\
&= \qty[
\frac{1}{16 \pi \epsilon_0} \frac{q_1q_2}{E}\csc^2 \qty(\frac{\theta}{2})
]^2
\end{align}
$$
![[散射截面.jpeg|400]]

$$\sigma = \qty(\frac{1}{16 \pi \epsilon_0} \frac{q_1 q_2}{E})^2
\int_{\theta=0}^\pi \int_{\phi=0}^{2\pi} \frac{\sin \theta}{\sin^4 \qty(\theta/2)}\dd{\theta}\dd{\phi} \to \infty$$

总散射截面发散，这与[[Coulomb Potential]]**作用距离无穷大**这一事实相符.

