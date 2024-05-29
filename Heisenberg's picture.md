---
tags: QuantumMechanics
number headings: first-level 1, max 6, 1.1.
created: 2023-05-13 00:49:37
---

The **Heisenberg picture** or **Heisenberg representation** is a formulation (largely due to [[Werner Heisenberg]] in 1925) of quantum mechanics in which the operators (observables and others) incorporate a dependency on time, but the state vectors are time-independent, an arbitrary fixed basis rigidly underlying the theory.

It stands in contrast to the [[Schrödinger picture]] in which the operators are constant, instead, and the states evolve in time. The two pictures only differ by a basis change with respect to time-dependency, which corresponds to the difference between active and passive transformations. The Heisenberg picture is the formulation of matrix mechanics in an arbitrary basis, in which the Hamiltonian is not necessarily diagonal.

It further serves to define a hybrid picture, the [[interaction picture]].

# Mathematical details

In the Heisenberg picture of quantum mechanics the state vectors $\ket{\psi}$ do not change with time, while observables $A$ satisfy
$$
\dv{t}A_\text{H}(t) = \frac{\mi}{\hslash}\comm{H_\text{H}}{A_\text{H}}
+ \qty(\pdv{A_\text{S}}{t})_\text{H}
$$
