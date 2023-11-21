Given a k-tape Turing machine $M=(Q, \Gamma, \delta)$  with 
$$\begin{align}
& Q = \{q_{0}, q_{1},...q_{N},q_{accept},q_{reject}\}\\ 
& \Gamma = \{a_{0},...,a_{M} \} \\
& \delta: Q\times \Gamma^{k}\mapsto Q \times \Gamma^{k-1} \times \{L,S,R\}^{k}
\end{align}$$
$q_{0},q_{accept},q_{reject}$ are special states.

## Simulated steps

start with a tape that only has the input string
$$|\triangleright|x_{0}|x_{1}|\cdots |x_{n-1}|\square|\square|\cdots$$
Construct the following single tape Turing machine $M'=(Q',\Gamma',\delta')$ with


