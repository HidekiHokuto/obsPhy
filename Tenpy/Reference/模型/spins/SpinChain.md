
```python
class tenpy.models.spins.SpinChain(model_params)
```


```python
add_coupling(strength, u1, op1, u2, op2, dx, op_string=None, category=None, plus_hc=False)
```

在哈密顿方程中加入两点耦合项，在晶格点上求和。

代表形式为 
$$
\sum_{x_0 \cdots x_{dim-1}} \text{strength}[\text{shift}(\vec{x})] \ast \text{OP}0 \ast \text{OP}1
$$

其中 `OP0 := lat.unit_cell[u0].get_op(op0)` 作用于点阵 `(x_0, ..., x_{dim-1}, u1)`，`OP1 := lat.unit_cell[u1].get_op(op1)` 作用于点阵 `(x_0+dx[0], ..., x_{dim-1}+dx[dim-1], u1)`。可能的组合 `x_0，...，x_{dim-1}` 由 `possible_couplings()` 中的边界条件决定。

如果给定的耦合强度是一个 numpy 数组，则耦合强度可能在空间上有所不同。这个数组的正确形状是由 `tenpy.models.lattice.coupling_shape()` 返回的 coupling_shape，并取决于边界条件。`shift(...)` 取决于 `dx`，其选择是这样的：如果假设边界条件是开放的，则强度的第一个条目 `strength[0, 0, ...]` 是第一个可能的耦合拟合到晶格中的前因子。

必要的项只需添加到 `coupling_terms`；该函数不会重建 MPO。

参数


当初始化一个模型时，你可以在所有最近邻键上添加一个项 $J \sum_{\ev{ij}} S_i^z S_j^z$ 像这样：

```python
J = 1.0
for u1, u2, dx in self.lat.pairs['nearest_neighbors']:
	self.add_coupling(J, u1, 'Sz', u2, 'Sz', dx)
```
Strength 可以是一个数组，它得到“导致正确的形状。例如，在具有偶数个站点和周期性（或无限）边界条件的1D链中，您可以使用以下直线添加交替的强耦合和弱耦合：

```
