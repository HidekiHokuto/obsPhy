
Tensor network representation in original lattice (dual lattice)

蜂窝晶格上的张量网络表示

哈密顿量
$$
H = \sum_{\ev{ij}_x} S_i^x S_j^x+\sum_{\ev{ij}_y}S_i^y S_j^y
+\sum_{\ev{ij}_z} S_i^z S_j^z \equiv \sum_{\ev{ij}} K(S_i, S_j)
$$
配分函数
$$
Z = \Tr e^{-\beta H} = \Tr \sum_{\ev{ij}} e^{-\beta K(S_i, S_j)}
\equiv \Tr \sum_{\ev{ij}} W(S_i, S_j)
$$
$W(S_i, S_j)$ 可视作二阶张量, SVD 分解
$$
\begin{align}
W(S_i, S_j) &= \sum_l U(S_i, l)\ \varLambda_l\ V(S_j, l)\\
&= \sum_l Q_a(S_i, l) Q_b(S_j, l)\\
&= Q_a Q_b
\end{align}
$$

$Q_a(S_i, l) = \sqrt{\lambda_l}\ U(S_i, l),\quad Q_b(S_j, l) = \sqrt{\lambda_l}\ V(S_j, l)$.

$Q$ 有方向性, 取决于 $\ev{ij}$.
定义位于 site $i$ 的 local tensor $T_{x,y,z}^i$.
$$
T_{x,y,z}^i \equiv \sum_{S_i} Q^x(S_i)\ Q^y(S_i)\ Q^z(S_i)
$$
The $S_i$ was traced out. 物理指标与一般晶格表达一致, 指标个数 = 3.

于是配分函数可以用 tensor network 表达
$$
\begin{align}
Z &= \Tr \sum_{\ev{ij}} W(S_i, S_j)\\
&= \Tr \prod_i T_{x_i, y_i, z_i}^i
\end{align}
$$
Tensor renormalized group (TRG)
![[IMG_0023.jpg|300]]


![[IMG_0024.jpg|600]]



![[IMG_0026.jpg]]

最终得到六个三阶, 收缩得到一个六阶张量. 由此得到配分函数.