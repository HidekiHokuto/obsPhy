---
tags: 
created: 2023-06-26 13:09:50
aliases: [威克定理, Wick's theorem]
DOI: 
---
设 $O_i$ 是 $a_k$ 和 $a_k^\dagger$ 的一个线性组合:
$$O_i = \int \dd{k} \qty[u_i(k) a_k + v_i(k) a_k^\dagger]$$

令 $W = \prod_{i=1}^N O_i$, $W_{i_1,i_2}=\prod_{i=1, i \neq i_1, i\neq i_2} O_i$.

$$
\begin{align}
W =& :W: + \sum_{(i_1,j_1)} :W_{i_1,j_1}: \ev*{O_{i_1}O_{j_1}}{0}\\
&+ \sum_{\smqty{(i_1,j_1),(i_2,j_2)\\(i_1,j_1)\neq(i_2,j_2)}}
:W_{i_1,j_1,i_2,j_2}:
\ev*{O_{i_1}O_{j_1}}{0}
\ev*{O_{i_2}O_{j_2}}{0} + \cdots
\end{align}
$$