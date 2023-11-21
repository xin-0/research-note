## 3.1 Time Hierarchy Theorem
> **Theorem 3.1** Time Hierarchy Theorem
> If $f, g$ are time constructible functions satisfying $f(n)\log{f(n)}=o(g(n))$, then 
> $$\textbf{DTIME}(f(n))\subsetneq\textbf{DTIME}(g(n))$$

### prove the weaker version
> $\textbf{DTIME}(n)\subsetneq\textbf{DTIME}(n^{1.5})$

#### idea
Construct a language $L\in\textbf{DTIME}(n^{1.5})$ that is not in $\textbf{DTIME}(n)$.
$\implies$ Construct a TM $D$, running in $cn^{1.5}$ steps, such that the language decided by it can not be decided by any TM runs in $c'n$ steps.

#### observation 1
- Prove in the direct way, i.e. without using contradiction, seems hard. (Is it so?)

#### construction of the contradiction
For the sake of contradiction, we assume that $\exists M$ that runs in $c'n$ steps that can determine $L_D$, the language decided by $D$.
- By the assumption, two TM decides the same language thus $D(x)=M(x), \forall x\in\{0,1\}^{*}$.
- We want a contradiction. So on the other hand, it is required that $D$ and $M$ output different results at least on some inputs, i.e. $D(x)=1-M(x)$ for some $x$. Thus leads to $D\neq M$, a contradiction.
	- Since we want the contradiction holds for an arbitrary TM $M$ that runs in $\Omega(n)$, $D$'s construction has something to do with $M$.

#### observation 2
Have to use the fact that:
- any TM $M$ can be represented by infinite number of strings.
- $\exists$ a (deterministic) universal TM $\mathcal{U}$ such that $\mathcal{U}({}_\llcorner M_\lrcorner, x) =M(x)$. 

## 3.2 Nondeterministic Time Hierarchy Theorem
> **Theorem 3.2** Nondeterministic Hierarchy Theorem
> If $f,g$ are time constructible functions satisfying $f(n+1)=o(g(n))$, then
> $$\textbf{NTIME}(f(n))\subsetneq\textbf{NTIME}(g(n))$$

### prove the weaker version
> $\textbf{NTIME}(n)\subsetneq\textbf{NTIME}(n^{1.5})$

#### idea
the main idea again is to construct a Turing Machine $D$ that runs in $cn^{1.5}$ and thus the language decided by it is in $\textbf{NTIME}(n^{1.5})$. Then, we want to show that such language cannot be decided by any TM runs in $c'n$ steps.

#### observation 1
why can't we directly borrow the construction in proving the deterministic version: $\textbf{DTIME}(n)\subsetneq\textbf{DTIME}(n^{1.5})$? 
- There is no obvious way to flip the output of an NDTM in polynomial time in the size of the Turing machine.
	- Can't use "run a NDTM, return its value and flip it" setting, it is in fact using the NDTM as an oracle: $M^{\textbf{NP}}$.
	- To use the NDTM not as a black box, we have to simulate it either on a DTM or NDTM
		- DTM(NDTM): can flip NDTM's result, but the cost is exponential.
		- NDTM(NDTM): cost is polynomial($O(n\log n)$), but no obvious way to flip its result.

## "NP-intermediate" problem
> Suppose that $\mathbf{P\ne NP}$, then there exists a language $L\in \mathbf{NP\backslash P}$  that is not $\mathbf{NP}$-complete.


## Non-relativization of P vs NP
> Exist oracles $A, B$ such that $\mathbf{P}^{A}= \mathbf{NP}^{A}$ and $\mathbf{P}^{B} \ne \mathbf{NP}^{B}$.

### part A
Let oracle $A$ be the language $\texttt{EXPCOM}$:
$$\{\langle{M, x, 1^{n}}\rangle:M \text{ outputs 1 on }x\text{ within }2^{n} \text{ steps}\}$$
Then we'll have $\mathbf{P}^{A}= \mathbf{NP}^{A}$.

### part B
For any language $B$, let $U_{B} = \{i^{n}: \text{some string of length } n \text{ is in } B\}$. Obviously, $U_{B}\in\mathbf{NP}^B$ for all $B$.
#### idea
We want to construct a language $B$ such that $U_{B}\notin \mathbf{P}^B$, thus separating $\mathbf{NP}^B$ and $\mathbf{P}^{B}$.

#### construct B


### Remark
- For two Turing machines, $M, N$ and an oracle $O$, $M^{O}\ne N^{O} \nRightarrow M \ne N$. In other words, two complexity class that are equal may be different relativized to an oracle.
	- An example: it has been proved that $\mathbf{IP = PSPACE}$, but there exists oracle $A$ such that $\mathbf{IP}^{A}\ne \mathbf{PSPACE}^{A}$.
- More on the previous topic:
	- [stackexchange](https://cstheory.stackexchange.com/questions/21590/is-relativization-well-defined)
	- [mathoverflow](https://mathoverflow.net/questions/35664/why-relativization-cant-solve-np-p)
	- [Terence Tao's blog post](https://terrytao.wordpress.com/2009/08/01/pnp-relativisation-and-multiple-choice-exams/)

