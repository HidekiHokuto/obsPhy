
抽象地说，模型代表要描述的某种物理（量子）系统。对于张量网络算法，该模型通常被指定为以二次量子化的形式写成的哈密顿量。例如，让我们考虑一个自旋为1/2的海森堡模型，

请注意，有些东西或多或少是隐式定义的。
- 局部希尔伯特空间：它由自旋为1/2的自由度和通常的自旋为1/2的算子 $S^x, S^y, S^z$ 组成。
- 几何（lattice）结构：在上面，我们谈到了一维“链”。
- 边界条件, 我们有开放的或周期性的边界条件吗？“链”意味着开放边界，在大多数情况下，这对于基于MPS的方法是更可取的。
- $i$ 的范围：我们考虑多少个站点（对于2D系统：在每个方向上）？

显然，如果我们想定义一个模型，这些东西需要在 TeNPy 中以这样或那样的方式指定。最终，我们的目标是运行一些算法。然而，不同的算法需要以不同的形式指定模型和哈密顿量。我们有一个类为每一个这样的要求形式。例如，`dmrg` 需要一个 `MPOModel`，它包含写为 `MPO` 的 Hamiltonian。因此，适合于 DMRG 的新模型类应该具有这样的一般结构：
```python
class MyNewModel(MPOModel):
	def __init__(self, model_params):
		lattice = somehow_generate_lattice(model_params)
		H_MPO = somehow_generate_MPO(lattice, model_params)
		# initialize MPOModel
		MPOModel.__init__(self, lattice, H_MPO)
```
