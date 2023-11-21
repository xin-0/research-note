5.3

Definition related to *alternating TM*:
- Focus only on running time: $\mathbf{ATIME}(T(n))$  
- Also considering alternating time:
	- $\mathbf{\Sigma}_i\mathbf{TIME}(T(n))$: start with $\exists$ and alternate $i$ times.
	- $\mathbf{\Pi}_i\mathbf{TIME}(T(n))$: start with $\forall$ and alternate $i$ times.
- Focus on polynomial running time has no limitation on alternating time: 
	- $\mathbf{AP}=\cup_c{\mathbf{ATIME}(n^{c})}$ 