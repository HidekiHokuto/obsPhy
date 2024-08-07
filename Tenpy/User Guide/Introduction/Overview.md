
# 代码库

git 仓库的根目录包含以下文件夹：

- tenpy

库的实际源代码。每个子文件夹都包含一个 `__init__.py` 文件，其中有一个总结，说明了其中模块的作用。(This要将该文件夹标记为python包的一部分，还需要一个文件。因此，git repo 的其他子文件夹中不应该包含 `__init__.py` 文件。）

- 玩具代码
完全独立于剩余库的简单玩具代码（即，`tenpy/` 的代码）。这些代码应该是相当可读的，并试图给出一个味道如何（一些）的算法工作。

- 示例
一些示例文件演示了！ng库的用法和接口，包括纯python文件，jupyter笔记本和示例参数文件。
- doc
用户指南包含在 `*.rst` 文件中。在线文档！会从这些档案和程式库的文件字串自动产生。此文件夹包含一个用于构建documenta！快去帮其他人！上。“doc/reference中引用所需的文件可以使用make src 2 html自动生成/更新。tests包含带有测试rou的文件！与pytest一起使用。如果您的设置正确并且安装了pytest，那么您可以从tests/文件夹中使用pytest运行测试套件。构建

# 层结构
在TeNPy中有几个层次的抽象。虽然概念之间存在一定的层次结构，但用户可以自行决定。只选择其中的一些。基于类的面向对象风格提供了最大的灵活性，可以根据个人需求进行继承和调整。

下图给出了 TeNPy 最重要的模块、类和 functions。灰色背景表示(子)模块，黄色背景表示类。红色箭头表示继承关系. 黑色虚线箭头表示直接使用。(各个模型可能来自 `NearestNeighborModel`，取决于 lattice 的几何形状。) 从顶级模拟中有一个相当清晰的层次结构，从顶层模拟到你想在一个作业中做的所有事情，从 `tenpy.algorithms` 模块中的高级算法到 `tenpy.linalg` 模块中的线性代数的基本操作。

# 高级模拟

高级接口由模拟提供，它可能处理您想要在计算集群作业上运行的所有内容：给定一组参数（以参数输入文件的形式存在），模拟包括初始化模型，张量网络和算法，运行算法，执行一些测量，最后将结果保存到磁盘。它还提供了一些额外的功能，如恢复中断的模拟的能力，例如，如果您的作业由于运行时限制而在群集上被终止。理想情况下，模拟（子）类表示从开始到结束的整个模拟，仅根据给定的参数给出可重现的结果。

例如，从终端调用 `tenpy-run parameters.yml`，`parameters.yml` 文件中包含以下内容，将为 `SpinChain` 运行 DMRG：

```yml
simulation_class: GroundStateSearch

output_filename: results.h5

model_class: SpinChain
model_params:
	L: 32
	bc_MPS: finite
	Jz: 1.
initial_state_params:
	method: lat_product_state
	product_state: [[up], [down]]
	
algorithm_class: TwoSiteDMRGEngine
algorithm_params:
	trunc_params:
		svd_min: 1.e-10
		chi_max: 100
	mixer: True
```

# 模型

从技术上讲，`MPO` 的显式定义已经足以在 `dmrg` 中调用类似DMRG的算法。然而，写下 $W$ 张量是很麻烦的，特别是对于更复杂的模型。因此，TeNPy 为模型的定义提供了另一个抽象层，我们首先讨论。不同类型的算法需要不同的哈密顿量表示。因此，库提供了指定的模型抽象的各个现场项和耦合项的哈密顿。下面的例子说明了这一点，同样是海森堡模型。

```python
"""Definition of a model: the XXZ chain."""

from tenpy.networks.site import SpinSite
from tenpy.models.lattice import Chain
from tenpy.models.model import CouplingModel, NearestNeighborModel, MPOModel

class XXZChain(CouplingModel, NearestNeighborModel, MPOModel):
def __init__(self, L=2, S=0.5, J=1., Delta=1., hz=0.):
spin = SpinSite(S=S, conserve="Sz")
# the lattice defines the geometry
lattice = Chain(L, spin, bc="open", bc_MPS="finite")
CouplingModel.__init__(self, lattice)
# add terms of the Hamiltonian
self.add_coupling(J * 0.5, 0, "Sp", 0, "Sm", 1) # Sp_i Sm_{i+1}
self.add_coupling(J * 0.5, 0, "Sp", 0, "Sm", -1) # Sp_i Sm_{i-1}
self.add_coupling(J * Delta, 0, "Sz", 0, "Sz", 1)
# (for site dependent prefactors, the strength can be an array)
self.add_onsite(-hz, 0, "Sz")
# finish initialization
# generate MPO for DMRG
MPOModel.__init__(self, lattice, self.calc_H_MPO())
# generate H_bond for TEBD
NearestNeighborModel.__init__(self, lattice, self.calc_H_bond())
```