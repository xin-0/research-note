---
tags:
  - quantum-chemistry
  - quantum-simulation
Ref:
---
Main problem in solving : many-electron-problem 

tensor network: solve 1-D problem

chem sim work flow: Cornelius Hempel PRX 8, 031022, 2018

1. hardware structure
2. hardware + problem structure
	- Qubit coupled cluster ansatz
	- Iterative qubit coupled cluster ansatz
3. provlem structure 
	- Unitary coupled cluster ansatz
	- Fermionic ADAAPT-ansatz
4. other
	1. Imaginary time evolution and QAOA inspired ansatz

Problem structure inspired algorithm

Energy sorting algorithm
- in evolving according to $U = e^{T-T^\dagger}$, $T^\dagger$ may bring $n^4$ terms, but not all of them are essential for getting the ground. For each term, evaluate their impact on the ground state energy, i.e. sort the ground state energy by applying these $n^4$ terms individually and sort the energy, choose the term that gives the lowest ground state energy
Point group symmetry reduction
- Assuming that the initial state has the same symmetry as the final state(ground state), we only need to evolve the initial state in a specific compact subspace.
Quantum Embedding theory
- Density matrix embedding theory
	- converts the original system into a system composed of a fragment, the corresponding bath and the pure environment