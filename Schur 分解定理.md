---
tags: 
created: 2023-11-01 02:11:07
aliases:
  - Schur decomposition theorem
---

> [!math|{"type":"theorem","number":"auto","setAsNoteMathLink":false,"title":"Schur decomposition theorem","label":"schur-decomposition-theorem","_index":0}] Theorem 1 (Schur decomposition theorem).
> 任意 $A \in \mathbb{C}^{n \times n}$, 一定存在幺正变换 $U$, 使得
>$$
>U^{-1}AU = U^\dagger AU = \mqty[\lambda_1 & \tilde{a}_{12} & \cdots & \tilde{a}_{1n}\\
>0 & \lambda_2 && \tilde{a}_{2n}\\
>\vdots & 0 & \ddots & \vdots\\
>0 & \cdots &0 &\lambda_n]
>$$


Schur 分解定理告诉我们，一个任意的复矩阵一定可以利用某个 (不一定唯一) 幺正变换 $U$ 化为一个*上三角矩阵*，变换后的矩阵之对角元为原矩阵的本征值。这个形式的上三角矩阵称为原先矩阵 A 的*舒尔形式*. 

```ad-note
需要着重指出的是，虽然任何复矩阵都可以利用幺正矩阵化为上三角矩阵，但这并不意味着任何的矩阵都是 diagonalizable. 后者要求矩阵 $A \in \mathbb{C}^{n \times n}$ 必须与一个对角矩阵 (而不仅仅是上三角矩阵) 相似.
```



