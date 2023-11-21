---
doi: https://doi.org/10.1016/j.cosrev.2021.100419
tags:
  - quantum-walk
  - review
---
## Background
### classical random walk
A random walk is a process that describes a path consisting of a sequence of random steps in space. A random process is often described as a Markov process in which the next position of the walker depends only on its current position and does not depend on previous positions of the walker.

### types of classical random walk
#### Discrete-time Random Walk (DTRW)
Time is measured in discrete time steps. A walk in discrete time is defined by a chain of random variables $(X_t) = (X_1, X_2, . . . , X_n)$.

#### Continuous-time Random Walk (CTRW)
Time used to measure the probability at each position is a continuous function. The probability $P(X,t)$ that process takes value $X$ at time $t$:
$$P(X,t)=\sum_{n=0}^{\infty}{P(n,t)P_n(X)}$$
$P(n,t):$ the probability of having taken n steps or jumps after time $t$.
$P_n(X):$ the probability of taking value $X$ after $n$ jumps.

#### Recurrent Random Walk (RRW)
Guaranteed to return to its starting position.
Only feasible in 1-D and 2-D.

#### Transient Random Walk (TRW)
Has a positive probability of never returning to its starting position.
Occurs for spaces with dimension $\gt 2$.

#### Correlated Random Walk (CoRW)
**Direction** of motion of the walker at one instance of time is correlated with the direction of motion at the next time step.

#### Branching Random Walk (BRW)
A stochastic process which generalizes the branching process and the random walk process.

### Parameter in classical random walk
Given an undirected graph $G(V,E)$, where $V$ and $E$ are the set of vertices and edges. We usually consider the following parameters to measure the efficiency of the walk.

- Access time or hitting time
	- $H_{uv}:$  expected count of steps to visit node $v$ starting from node $u$.
- Commute time
	- $\mathcal{K}_{uv}:$ expected count of steps for a round-trip between node $u$ and $v$.
	- $\mathcal{K}_{uv} = H_{uv} + H_{vu}$ 
- Cover time
	- $\mathcal{C}_{i,n}:$ expected count of steps to reach every node of graph $G(n)$ starting from node $i$.
- Mixing time
	- the expected count of steps before the distribution will be approximately uniform of reaches its limiting distribution.

### Coined quantum walk
#### notations
- Total Hilbert space
	- $\mathcal{H}_t = \mathcal{H}_p \otimes \mathcal{H}_c$
	- $\mathcal{H}_c:$ coin Hilbert space, internal degrees of freedom
	- $\mathcal{H}_p:$ position Hilbert space, external degrees of freedom
- Observables
	- Venegas-Andraca[^1] suggests doing sequential measurements on coin and position sites of the quantum walker using the observables defined as 
		- $$\begin{align}&\hat{M}_{coin}=\beta_0\ket{0}_c\bra{0} + \beta_1\ket{1}_c\bra{1} \\ &\hat{M}_{ops}=\sum_i{\beta_i\ket{i}_p\bra{i}} \end{align}$$

### Parameter in quantum walk
A quantum walk evolution whether discrete or continuous on a graph $G(V, E)$ has the following parameters.

- Quantum hitting time
	- The time needed by a quantum particle to reach the target node as determined by a measurement of the target node.[^2]
	- **remark**
		- In classical random walk, the time required to detect or find a target node is equivalent. Hitting time usually refers to both. However, in the quantum case, there could be a difference in terms of time complexity between detecting and finding, making it harder to define the hitting time.[^3]
- Quantum commute time
	- The time required by walker to travel to a node and back from some initial node.
- Quantum mixing time
	- The minimum time after which the average probability distribution of the quantum system becomes approximately similar to its limiting distribution.
	- **remark**
		- Although the limiting distribution does not exist for the quantum case, however, for a set of nodes, it can be defined as a long time average probability distribution of finding the quantum walker at each node.
- One-shot hitting time
	- The hitting time of a node with only one final measurement and no intermediate measurements. A quantum walk has a $(T,p)$ one-shot $(\ket{\psi_0},\ket{u})$ hitting time if the probability to measure $\ket{u}$ at time $T$ starting initially in $\ket{\psi_0}$ is larger than $p$, i.e. $$\Vert{\braket{u\vert U^T\vert \psi_0}}\Vert^2\ge p$$
	- **remark**
		- Introduced by Kempe[^4]
		- only applicable to quantum walks.
- $\ket{u}$ - Stopped walk
	- The $\ket{u}$ stopped walk starting with initial state $\ket{\psi_0}$ is a procedure defined as an iteration of measurement with two projectors: $\pi_0=\pi_u=\ket{u}\bra{u}$ and $\pi_1=1-\pi_0$. 
	- If $\pi_1$ is measured, then it states an application of quantum walk $W$ , and if $\pi_0$ is measured, then it means the process is stopped.
- Concurrent hitting time
	- A quantum walk $W$ has a $(T,p)$ concurrent $(\ket{\psi_0},\ket{u})$ hitting time if $\ket u$ -stopped walk from $W$ and initial starting state $\ket{\psi_0}$ has a probability $\ge p$ of stopping at a time $t \le T$.
	- Applicable to walks with partial measurements or absorbing boundaries at each step of the walk.
	- **remark**
		- Introduced by Kempe[^4] and Ying and Ying [^5]

### Why quantum walk is needed

- Spreading behavior of the quantum walk is way faster than the classical random walk
- Quantum walk is reversible. Quantum walk uses unitary matrix as opposed to stochastic matrix in classical random walk.
- Different statistical properties
	- Classical random walk may be ergodic as in Markov-chain or non-ergodic as in the case of bipartite graphs
	- Quantum walk is non-ergodic, thus do not converge to limiting distribution at any point during the evolution 
- Different origin of randomness
	- stochastic transition for the classical.
	- measurement operation for the quantum.

## Quantum walk models

### Discrete time quantum walk model
Conventional on Hilbert space follows [[#notations]] and 
- $P(v, t)$ denotes the probability distribution over a set of states/position $v$ at time $t$.
- $P(v,u,t)$ denotes the probability distribution of $v$ at time $t$ with coin state $u$.
#### quantum walk on a line
##### State space
Total space: $\mathcal{H}_t=\mathcal{H}_p \otimes \mathcal{H}_c$
- $\ket{v, u} \in \mathcal{H}_t$ 
	- $\ket{u}\in \mathcal{H}_c = \mathcal{H}$, for a single qubit coin
##### Operation
Unitary on the whole system: $\hat{U} = \hat{S}(\hat{I}\otimes\hat{C})$
$\hat{C}:$ coin operator, act only on the coin state
$\hat{S}:$ shift operator, act on the whole system, a permutation on position state conditioned on the coin state.

A commonly used coin operator, $SU(2)$ operator:
$$\hat{SU}(p,\alpha, \beta) = 
\begin{pmatrix}
\sqrt{p} & \sqrt{1-p}e^{i\alpha} \\
\sqrt{1-p}e^{i\beta} & -\sqrt{p}e^{(\alpha + \beta)}
\end{pmatrix}
$$
$p, 1-p:$ the probability of quantum walker moving left or right.

##### Evolution
With defined $\hat{C}$ and $\hat{S}$, the quantum state after $t$ steps of walk is:
$\ket{\Psi}_t=(\hat{U})^t\ket{\Psi}_0$ 

[^1]: Salvador Elías Venegas-Andraca, Quantum walks: a comprehensive review, Quantum Inf. Process. 11 (5) (2012) 1015–1106.
[^2]: Alexey A. Melnikov, Aleksandr P. Alodjants, Leonid E. Fedichkin, Hitting time for quantum walks of identical particles, in: International Conference on Micro-and Nano-Electronics 2018, Vol. 11022, International Society for Optics and Photonics, 2019, p. 110222J.
[^3]: Frédéric Magniez, Ashwin Nayak, Peter C. Richter, Miklos Santha, On the hitting times of quantum versus random walks, Algorithmica 63 (1–2) (2012) 91–116.
[^4]: Julia Kempe, Discrete quantum walks hit exponentially faster, Probab. Theory Related Fields 133 (2) (2005) 215–235.
[^5]: [Shenggang Ying, Mingsheng Ying, Removing measurements from quantum walks, Phys. Rev. A 87 (1) (2013) 012337.](https://link.aps.org/doi/10.1103/PhysRevA.87.012337)