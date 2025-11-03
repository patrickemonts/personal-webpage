---
title: Research
date: '2015-11-03T00:00:00+01:00'
draft: false
share: false
commentable: false
editable: false

# Optional header image (relative to `static/media/` folder).
header:
  caption: ''
  image: ''
---

With quantum computers hosting more and more qubits, we have to think about quantum information in the many-body regime. 
This is exactly what we are doing in the "Computational Quantum Information and Many-Body Physics" group.  
Using modern methods from the intersection of quantum information and quantum many-body physics like tensor networks, variational Monte Carlo and semi-definite programs, we help to shape the future of quantum technologies.

## Device Certification
Bell nonlocality is a fundamental feature of quantum mechanics that reveals the impossibility of explaining quantum correlations through any local hidden variable theory. 
Demonstrated through **violations of Bell inequalities**, nonlocality highlights the intrinsic quantum nature of entanglement—showing that measurements on spatially separated particles can exhibit correlations that defy classical intuition.

Traditionally, Bell nonlocality is tested through statistical violations of specific inequalities. 
However, finding these inequalities for many-party settings like modern quantum processors is extremely challenging. 
By assuming a less strict certification scenario, a powerful alternative approach has emerged: detecting nonlocality via energy minimization. 
In this framework, one constructs a Bell operator -- analogous to a Hamiltonian -- whose expectation value is bounded for all local (classical) strategies. 
A quantum system exhibits nonlocality if its ground-state energy falls below this classical threshold.

This **energy-based perspective** connects Bell nonlocality to methods from many-body physics and optimization, allowing the use of variational techniques, semidefinite programming, and even tensor networks to detect nonlocal correlations. It also enables the exploration of nonlocality in more complex systems, such as spin chains or lattice models, where traditional Bell tests are difficult to implement.

### Selected Publications
1. K. Wang et al., Probing Many-Body Bell Correlation Depth with Superconducting Qubits, Phys. Rev. X 15, 021024 (2025).
2. W. Li et al., Improved Nonlocality Certification via Bouncing between Bell Operators and Inequalities, arXiv:2407.12347.


## Lattice Gauge Theories
In modern physics, most of the fundamental forces in nature are described by **gauge theories**—a special class of quantum field theories that have a built-in local symmetry. These theories are central to everything from the behavior of materials to our understanding of the universe at the smallest scales in the form of the Standard Model of particle physics. The strong nuclear force, which holds protons and neutrons together, is described by **quantum chromodynamics (QCD)**. At very high energies, QCD behaves in a way that is relatively easy to handle mathematically, but at lower energies it becomes much more complex and strongly interacting.

One of the most successful ways to study low-energy QCD is through **lattice gauge theory** (LGT), which uses powerful computational techniques to simulate the theory on a discrete grid of spacetime. This approach works well for many problems, but it has key limitations: it struggles to describe real-time dynamics, and it can into the so-called the _sign problem_. In certain situations—such as when dealing with systems at high density—the mathematical expressions involved no longer behave like probability distributions, making standard simulation techniques fail. This roadblock prevents us from directly studying important phenomena like the interiors of neutron stars, color superconductivity, and the quark-gluon plasma.

In the Hamiltonian formulation of LGTs, the focus shifts from path integrals to quantum states in a Hilbert space. This perspective is particularly well-suited to quantum simulation and the application of variational many-body methods. We combine a class of tensor networks, so-called Gauged Gaussian Projected Entangled Pair States (GGPEPS), with a variational Monte Carlo procedure to find the ground states of lattice gauge theories.

### Selected Publications
1. A. Kelman, U. Borla, I. Gomelski, J. Elyovich, G. Roose, P. Emonts, and E. Zohar, Gauged Gaussian projected entangled pair states: A high dimensional tensor network formulation for lattice gauge theories, Phys. Rev. D 110, 054511 (2024).
2. A. Kelman, U. Borla, P. Emonts, and E. Zohar, Projected Entangled Pair States for Lattice Gauge Theories with Dynamical Fermions, arXiv:2412.16951.
3. P. Emonts, M. C. Bañuls, I. Cirac, and E. Zohar, Variational Monte Carlo simulation with tensor networks of a pure $\mathbb{Z}_3$ gauge theory in $( 2 + 1 )$ D, Phys. Rev. D 10*, 074501 (2020).

## Quantum Networks
Quantum networks are engineered systems for distributing and processing quantum information across distant nodes, enabling possibilities such as quantum communication, distributed quantum computing, and secure information transfer. 
At the heart of these networks is **entanglement, a uniquely quantum resource** that allows for correlations stronger than any classical system can support. 

A central challenge in building large-scale quantum networks is the **distribution of entanglement** over long distances: quantum information cannot be copied according to the non-cloning theorem and thus, quantum repeaters are fundamentally different from commonly used amplifiers in fiber networks.

By considering a quantum network as a genuine quantum many-body system, we can apply techniques from statistical mechanics and machine learning to optimize the topology and the operation of the network.

### Selected Publications
1. J. Li, T. Coopmans, P. Emonts, K. Goodenough, J. Tura, and E. van Nieuwenburg, Optimising entanglement distribution policies under classical communication constraints assisted by reinforcement learning, Mach. Learn.: Sci. Technol. 6, 035024 (2025).


## Topological Data Analysis
Topological Data Analysis (TDA) is a rapidly growing field that applies concepts from topology — the mathematical study of shape and space — to uncover the underlying structure in complex datasets. By focusing on features like connected components, loops, and voids, TDA provides robust, multi-scale insights that are often resilient to noise and deformations in data.

To make TDA amenable to methods typically used in physics, we need to find a description that taslk more about Hilbert spaces and less about simpilcial complices. A connection between cohomology and super-symmetric quantum mechnics was already discovered by Witten in his seminal 1982 paper. Here, we use a closely related version of this correspondence: the structure of data (e.g., simplicial complexes) is mapped to a constrained Hilbert space of fermionic states. This connection allows tools from many-body quantum physics like tensor networks to be applied to problems in data analysis, opening up new computational strategies and theoretical insights.