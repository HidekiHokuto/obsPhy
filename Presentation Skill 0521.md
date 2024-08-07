
## 0521

Essential criteria for conclusion

1. Repeat topic + objective
2. Summarize main points
3. Present conclusion, predicted conclusions
4. Reference to possible future works due to inconclusive data/results.
5. Thank the audience
6. Welcome questions.


Pausing
1. Before a conditional, eg. whether/if
2. Before a conjunction, eg. as long as, but, and, or, so
3. After punctuations
	- ? ! . long
	- , ; : short
4. Before relative pronouns
		that, who, where, what

## Script

### **Introduction**

Imagine a future where quantum computers can solve problems really fast and be able to overcome their biggest problems-decoherence and errors. This future could be possible by studying special particles called anyons.

The main reason we're looking into anyons is to see how they can help make quantum computers better. These computers face big challenges like errors, but anyons might help us fix these problems. Our goal is to understand these particles well enough to use them in real quantum computers construction, making these machines more powerful and reliable.

Today's talk has three main parts. First, I'll explain some basic ideas about topological quantum computing and anyons so we all understand what they are and why they're important. Next, we'll look at what other researchers have found out about using anyons in quantum computers. Lastly, I'll talk about what we plan to do next, including some simulation we want to run to see if our ideas will work in real life.

### **Main Body**

我们都知道, 对于现在的经典计算机, 我们利用比特, 0 or 1, 对信息进行编码. 类比的, 在量子计算机中, 我们也可以通过可分辨的量子态, 来进行信息的编码, 存储, 以及读取. 并且, 与传统的二进制计算不同，量子位可以同时处于0和1的叠加状态，这使得量子计算机在处理某些特定问题时，具有超越传统计算机的潜力。但是, 量子系统是脆弱的, 以至于微小的环境扰动, 就有可能使得这样的处理不再可行, 或者称之为退相干, 导致计算的错误. 因此, 探索如何进行可以容错的量子计算, 是当前的目标之一. 而可容错量子计算的实现方法之一, 称之为拓扑量子计算.

拓扑性质是数学和物理学中描述空间或物体在连续变形（如拉伸、扭曲，但不包括撕裂或粘合）下保持不变的性质。这些性质与物体的具体形状或大小无关，而是与物体的全局结构有关。It was shown that the ground-state degeneracy of a topologically-ordered state is robust against any perturbations, then it can be used for implementing the topological quantum computation.

但是, 在这世界上真的存在这样的拓扑不变性么? 想象一下, 一个圆柱形金属导体, 我们将其切断, 它的拓扑结构并没有发生变化. 但是他的各种性质, 包括电阻, 电导都不可避免的会产生变化. 乍看起来, 拓扑的解决方案只是纯粹数学的, 而无法在物理上实现. 但随着量子霍尔效应的发现以及一系列的研究, 分数量子霍尔效应, 以及有阻挫自旋系统等, 有机会被用于实现拓扑量子计算. 

#### Anyons

上述系统之所以可以被用于实现拓扑计算, 因为它们都可以产生任意子的激发. So, we need to first understand anyons.

##### What are Anyons?

Anyons are quasiparticles that occur in two-dimensional systems. Unlike fermions and bosons, which obey the Pauli exclusion principle and Bose-Einstein statistics, respectively, anyons obey fractional statistics. When anyons are exchanged, the quantum state of the system acquires a phase factor that can be any value, not just 0 or π.

##### Braiding of Anyons

One of the most intriguing properties of anyons is their ability to "braid" around each other. When two anyons are swapped, they trace out a path in space-time that can be thought of as a braid. The sequence of these braidings is used to perform quantum computations. The resulting quantum state depends only on the topology of the braiding pattern, not on the specific details of how the braiding is performed.


在之前的研究中, 我数值计算了某个特定模型, 在小尺寸的情况下, 通过绝热的方式, 得到基态的可行性. 目前以及未来, 计划学习更多关于拓扑量子计算的算法实现, 并且数值方法, 分析该模型在研究在不同的外部扰动下，拓扑相是否保持稳定。这有助于我们理解拓扑系统对外界扰动的鲁棒性。通过模拟不同的错误模型，评估拓扑量子计算中的错误率，并研究拓扑纠错方案的有效性, 以及改良方式.


**Conclusion**



Finish the slide in 3 weeks


这几天完成 script
下周讲 Q/A part
下下周练习
下下下周实际 presentation


---

## Script (EN)

Imagine a future where quantum computers can solve problems really fast and be able to overcome their biggest problems-decoherence and errors. This future could be possible by studying special particles called anyons.

The main reason we're looking into anyons is to see how they can help make quantum computers better. These computers face big challenges like errors, but anyons might help us fix these problems. Our goal is to understand these particles well enough to use them in real quantum computers construction, making these machines more powerful and reliable.

Today's talk has three main parts. First, I'll explain some basic ideas about topological quantum computing and anyons so we all understand what they are and why they're important. Next, we'll look at what other researchers have found out about using anyons in quantum computers. Lastly, I'll talk about what we plan to do next, including some simulation we want to run to see if our ideas will work in real life.


We all know that in classical computers, we use bits, 0 or 1, to encode information. Similarly, in quantum computers, we can encode, store, and read information through distinguishable quantum states. Unlike the binary logic of classical computing, quantum bits, or qubits, have the unique ability to exist in a superposition of 0 and 1 states simultaneously. This superposition gives quantum computers the potential to outperform traditional computers in solving certain types of problems.

However, quantum systems are extremely delicate, and even the slightest environmental disturbances can cause the loss of quantum information, a phenomenon known as decoherence, leading to computational errors. Therefore, developing fault-tolerant quantum computing techniques that can resist these disturbances is one of our current goals. In this field, topological quantum computing offers an innovative solution, harnessing the topological properties of quantum systems to protect information and achieve more stable and reliable quantum computation.

Topological properties are a profound concept in mathematics and physics that describe the properties of space or objects that remain unchanged under continuous deformations, such as stretching and twisting. These properties are not related to the specific shape or size of an object, but are closely connected to its global structure. This global structural invariance makes topological properties very important in many scientific fields, especially in the field of quantum computing.

The ground-state degeneracy of topological order is theoretically robust against any small perturbations. This means that even if the quantum system is affected by the external environment, the ground state of topological order can still remain stable, thus protecting quantum information from destruction.

This robustness is key to implementing topological quantum computing. In topological quantum computing, qubits are not encoded in the traditional physical way, but through different ground states in topological order. In this way, quantum information is encoded in the global structure of the system, not in the local physical state. This encoding method makes quantum information naturally resistant to local perturbations, thereby greatly improving the reliability of quantum computing.

this statement raises a fascinating question: Does topological invariance really exist in the real world? Let's take a cylindrical metal conductor as an example. If we cut it, from a topological perspective, its structure hasn't fundamentally changed—it's still a tube with two openings. However, physically, properties like resistance and conductivity will inevitably change due to this operation.

This seemingly paradoxical phenomenon might make us wonder if topological solutions are purely mathematical and cannot be realized in the physical world. But in fact, with the advancement of science, we have discovered some physical phenomena that, to some extent, demonstrate the practical application of topological invariance.

The quantum Hall effect is a groundbreaking discovery. Under a strong magnetic field, a two-dimensional electron gas exhibits some unconventional transport properties that are related to the topological properties of electrons. The subsequent discovery of the fractional quantum Hall effect further expanded our understanding of topological phases, revealing that electrons in low-dimensional systems can form quasiparticles with fractional charges.

In addition, frustrated spin systems also provide a new perspective for topological quantum computing. In these systems, the arrangement of spins is geometrically constrained, leading to the emergence of certain topological properties that are very useful for designing qubits and quantum logic gates.

In my previous research, I conducted numerical calculations on a specific model, exploring the feasibility of reaching the ground state through adiabatic methods in small-sized systems. Currently, and in the future, I plan to delve deeper into the algorithmic implementation of topological quantum computing, as well as numerical methods, to analyze how this model maintains topological phase stability under different external perturbations. This will help us understand the robustness of topological systems against external disturbances.

Furthermore, I intend to simulate various error models to assess the error rates in topological quantum computing. This will encompass studying the system's performance under a range of potential perturbations and how topological error-correction schemes can mitigate these errors. Through these studies, we can better understand the effectiveness of topological error correction and explore possible improvements to enhance the accuracy and stability of quantum computations.

Ultimately, these research efforts will contribute to the advancement of the field of quantum computing, especially in achieving fault-tolerant quantum computation. By gaining a deeper understanding of the robustness of topological systems, we can develop new strategies and tools to overcome the challenges currently faced in quantum computing.

In summary, today's presentation has outlined a vision for quantum computing where the study of anyons holds the key to addressing the critical issues of decoherence and errors. We've discussed the principles of topological quantum computing, the unique role of anyons in creating stable quantum states, and the importance of these properties for developing robust quantum systems. The talk has also reviewed ongoing research and our future plans, including simulations to test the practicality of these concepts in real-world applications, all in pursuit of a new generation of quantum computers that are both powerful and resilient.




---


Imagine a future where quantum computers can solve problems really fast and be able to overcome their biggest problems-decoherence and errors.\ This future could be possible by studying special particles called anyons.

The main reason we're looking into anyons is to see how they can help make quantum computers better.\ These computers face big challenges like errors, but anyons might help us fix these problems.\ Our goal is to understand these particles well enough to use them in real quantum computers construction, making these machines more powerful and reliable.

Today's talk has three main parts.\ First, I'll explain some basic ideas about quantum computing so we all understand what they are and why topological quantum computing is so important.\ Next, we'll look at what other researchers have found out about using anyons in quantum computers.\ Lastly, I'll talk about what we plan to do next, including some simulation we want to run to see if our ideas will work in real life.

We all know that in classical computers, we use bits, 0 or 1, to encode information.\ Similarly, in quantum computers, we can encode, store, and read information through distinguishable quantum states.\ Unlike the binary logic of classical computing, quantum bits, or qubits, have the unique ability to exist in a superposition of 0 and 1 states simultaneously.\ This superposition gives quantum computers the potential to outperform traditional computers in solving certain types of problems.

However, quantum systems are extremely delicate, and even the slightest environmental disturbances can cause the loss of quantum information, a phenomenon known as decoherence, leading to computational errors.\ Therefore, developing fault-tolerant quantum computing techniques that can resist these disturbances is one of our current goals.\ In this field, topological quantum computing offers an innovative solution, harnessing the topological properties of quantum systems to protect information and achieve more stable and reliable quantum computation.

Topological properties are a profound concept in mathematics and physics that describe the properties of space or objects that remain unchanged under continuous deformations, such as stretching and twisting.\ These properties are not related to the specific shape or size of an object, but are closely connected to its global structure.\ This global structural invariance makes topological properties very important in many scientific fields, especially in the field of quantum computing.

The ground-state degeneracy of topological order is theoretically robust against any small perturbations.\ This means that even if the quantum system is affected by the external environment, the ground state of topological order can still remain stable, thus protecting quantum information from destruction.

This robustness is key to implementing topological quantum computing.\ In topological quantum computing, qubits are not encoded in the traditional physical way, but through different ground states in topological order.\ In this way, quantum information is encoded in the global structure of the system, not in the local physical state.\ This encoding method makes quantum information naturally resistant to local perturbations, thereby greatly improving the reliability of quantum computing.

This statement raises a fascinating question: Does topological invariance really exist in the real world?\ Let's take a cylindrical metal conductor as an example.\ If we cut it, from a topological perspective, its structure hasn't fundamentally changed—it's still a tube with two openings.\ However, physically, properties like resistance and conductivity will inevitably change due to this operation.

This seemingly paradoxical phenomenon might make us wonder if topological solutions are purely mathematical and cannot be realized in the physical world.\ But in fact, with the advancement of science, we have discovered some physical phenomena that, to some extent, demonstrate the practical application of topological invariance.

The quantum Hall effect is a groundbreaking discovery.\ Under a strong magnetic field, a two-dimensional electron gas exhibits some unconventional transport properties that are related to the topological properties of electrons.\ The subsequent discovery of the fractional quantum Hall effect further expanded our understanding of topological phases, revealing that electrons in low-dimensional systems can form quasiparticles with fractional charges.

In addition, frustrated spin systems also provide a new perspective for topological quantum computing.\ In these systems, the arrangement of spins is geometrically constrained, leading to the emergence of certain topological properties that are very useful for designing qubits and quantum logic gates.

In my previous research, I conducted numerical calculations on a specific model, exploring the feasibility of reaching the ground state through adiabatic methods in small-sized systems.\ Currently, and in the future, I plan to delve deeper into the algorithmic implementation of topological quantum computing, as well as numerical methods, to analyze how this model maintains topological phase stability under different external perturbations.\ This will help us understand the robustness of topological systems against external disturbances.

Furthermore, I intend to simulate various error models to assess the error rates in topological quantum computing.\ This will encompass studying the system's performance under a range of potential perturbations and how topological error-correction schemes can mitigate these errors.\ Through these studies, we can better understand the effectiveness of topological error correction and explore possible improvements to enhance the accuracy and stability of quantum computations.

Ultimately, these research efforts will contribute to the advancement of the field of quantum computing, especially in achieving fault-tolerant quantum computation.\ By gaining a deeper understanding of the robustness of topological systems, we can develop new strategies and tools to overcome the challenges currently faced in quantum computing.

In summary, today's presentation has outlined a vision for quantum computing where the study of anyons holds the key to addressing the critical issues of decoherence and errors.\ We've discussed the principles of topological quantum computing, the unique role of anyons in creating stable quantum states, and the importance of these properties for developing robust quantum systems.\ The talk has also reviewed ongoing research and our future plans, including simulations to test the practicality of these concepts in real-world applications, all in pursuit of a new generation of quantum computers that are both powerful and resilient.