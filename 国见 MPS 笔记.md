翻译自[[国見昌哉|Masaya Kunimi]]的 MPS 笔记

# 1. 奇异值分解
在本节中，我们总结了奇异值分解（SVD）方法。考虑 $M \times N$ 的复矩阵 $A$ .在 MKL 表示法中，矩阵 $A$ 可以被分解为
$$
A = USV^\dagger \tag{1}
$$
其中 $U$ 是 $M \times M$ 酉矩阵，$V$ 是 $N \times N$ 酉矩阵，$S$ 是 $M \times N$ 矩阵，且其元素对于 $\min (M, N)$ 个对角元素非负。$S$ 的对角元素称为奇异值。在文献[1]的符号中，U是M × min（M，N）矩阵，V是min（M，N）×N矩阵，S是min（M，N）× min（M，N）对角矩阵。U和V满足

# 2. 矩阵乘积态
## 2.1. 左正则表示
在这里，我们考虑以下量子态：
$$
\ket{\Psi} = \sum_{n_1, \cdots, n_M} c_{n_1, \cdots, n_M} \ket{n_1, \cdots, n_M}\tag{21}
$$
其中我们考虑 $M$ 个 sites 系统，$n_i$ 是 site $i$ 的占用数。我们假设局部希尔伯特空间的维数为 $d$. 系数 $c_{n_1, \cdots, n_M}$ 可以被视为 $d^M$ 维向量。我们将这个向量 reshape 为一个 $d \times d^{M-1}$ 矩阵：
$$
\Psi_{n_1(n_2, \cdots, n_M)} \equiv c_{n_1, \cdots, n_M} \tag{22}
$$
将 SVD 应用于 $\Psi_{n_1(n_2, \cdots, n_M)}$, 我们得到
$$
\begin{align}
c_{n_1,\cdots, n_M} &= \Psi_{n_1(n_2 \cdots n_M)}\\
&= \sum_{a_1} U_{n_1 a_1} S_{a_1} (V^\dagger)_{a_1 (n_2 \cdots n_M)}\\
&\equiv \sum_{a_1} U_{n_1a_1} c_{a_1 n_2\cdots n_M}\\
&\equiv \sum_{a_1} A_{a_1}^{n_1} c_{a_1 n_2\cdots n_M}
\end{align}
$$
其中 $U_{n_1a_1}$ 是一个 $r_1 \times r_1$ 矩阵，$r_1 \leq d$ 是矩阵 $\Psi_{n_1(n_2 \cdots n_M)}$ 的秩，$c_{a_1n_2 \cdots n_M}$ 是 $r_1 d^{M-1}$ 维向量，$A^{n_1}$ 是 $1 \times r_1$ 矩阵。我们重复这个过程：

## 2.2. 右正则表示

## 2.3. 混合正则表示

## 2.4. 矩阵元的计算

## 2.5. 正则形式的生成

# 3. TEBD
## 3.1. Suzuki-Trotter 分解

## 3.2. $\Gamma \Lambda$ 记法
## 3.3. Single-Site 操作

## 3.5. 改进算法

## 3.7. 守恒律

## 3.8. Swapping 算符

# 4. 矩阵乘积算符

## 4.2. DMRG

## 4.3. 利用 MPOs 进行时间演化

# 附录 A: 张量积

# 附录 B: Lanczos 方法


[^1]: U. Schollw¨ock, Ann. Phys. 326, 96 (2011). [[矩阵乘积态时代的密度矩阵重整化群]]
[^2]: J. Hauschild and F. Pollmann, SciPost Phys. Lect. Notes 5 (2018).
[^3]: G. Vidal, Phys. Rev. Lett. 91, 147902 (2003).
[^4]: G. Vidal, Phys. Rev. Lett. 93, 040502 (2004).
[^5]: J. J. Garc´ıa-Ripoll, New J. Phys. 8, 305 (2006).
[^6]: M. B. Hastings, J. Math. Phys. 50, 095207 (2009).
[^7]: F. Fr¨owis, V. Nebendahl, and W. D¨ur, Phys. Rev. A 81, 062337 (2010).
[^8]: B. Pirvu, V. Murg, J. I. Cirac, and F. Verstraete, New J. Phys. 12, 025012 (2010).
[^9]: M. P. Zaletel, R. S. K. Mong, C. Karrasch, J. E. Moore, and F. Pollmann, Phys. Rev. B 91, 165112 (2015).
[^10]: C. K.-L. Chan, A. Keselman, N. Nakatani, Z. Li, and S. R. White, J. Chem. Phys. 145, 014102 (2016).
[^11]: S. Goto and I. Danshita, Phys. Rev. A 96, 063602 (2017).
[^12]: S. Paeckel, T. K¨ohler, A. Swoboda, S. R. Manmana, U. Schollw¨ock, and C. Hubig, Ann. Phys. (N. Y.) 411, 167998 (2019).
[^13]: N. Hatano and M. Suzuki, Finding Exponential Product Formulas of Higher Orders. In: Das, A., K. Chakrabarti, B. (eds) Quantum Annealing and Other Optimization Methods. Lecture Notes in Physics, vol 679. Springer, Berlin, Heidelberg. https://doi.org/10.1007/11526216_2.
[^14]: M. Hochbruck and C. Lubich, SIAM J. NUMER. ANAL. 34, 1911 (1997). Krylov 法で時間発展。