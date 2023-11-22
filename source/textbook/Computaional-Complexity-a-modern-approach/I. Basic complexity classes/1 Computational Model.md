## 1.1 Modeling Computation
Advantages of Turing's model
1. Robustness of definition.
2. Fluidity of algorithm/machine. An algorithm can be an input to another algorithm.
3. Existence of an universal machine that can efficiently simulate other machines.
4. Due to 2 and 3, it's easy to discuss uncomputability in this framework.

## 1.2 Turing Machine

### definition: TM
A **Turing Machine** $M$ is described by a tuple $(\Gamma, Q, \delta)$ containing:
- A finite set $\Gamma$ of the symbol that $M$'s tapes can contain. We assume that $\Gamma$ contains a designated blank symbol, denoted $\square$ ; designated start symbol, denoted  $\triangleright$ . $\Gamma$ is called the alphabet of $M$.
- A finite set $Q$ of possible states $M$'s register can be in. We assume that $Q$ contains a designated start state, denoted $q_{start}$, and a designated halting state, denoted $q_{halt}$.
- A function $\delta: Q\times\Gamma^{k}\to Q\times\Gamma^{k-1}\times\{L,S,R\}^k$, where $k\ge2$, describing the rules $M$ use in performing each step. This function is called the transition function of $M$.

#### start configuration on input $x$
1. The tapes are initialized to:
	- Input tape: $\triangleright$ | $x$ | $\square$ | $\square$ | ...
		- contains initially the start symbol $\triangleright$, a finite nonblank string $x$(the input string) and the blank symbol $\square$ on the rest of the cells.
	- Other tapes:  $\triangleright$ | $\square$ | $\square$ | ...
		- All tapes except for the input are initialized in their first location to the start symbol $\triangleright$ and in all other locations to the blank symbol $\square$.
2. All heads start at the left ends of tapes and 
3. The machine is in the special starting state $q_{start}$.

#### each step
Apply transition function $\delta$ on the machine.

#### halt
Once the machine is in $q_{halt}$ the transition function $\delta$ does not allow it to further modify the tape or change states.

### remark
- How will the start configuration be defined if it is a single-tape TM?
## 1.3 Efficiency and Running Time

### definition: running time
(Computing a function and running time)
Let $f:\{0,1\}^* \to \{0,1\}^*$ and let $T:\mathbb{N\to N}$ be some functions, and let $M$ be a Turing machine.
>We say that $M$ *computes* $f$ if for every $x \in \{0,1\}^*$, whenever $M$ is initialized to the start configuration on input $x$, then it halts with $f(x)$ written on its output tape. 

>We say $M$ computes $f$ in *$T(n)$-time* if its computation on every input $x$ requires at most $T(\vert{x}\vert)$ steps.
#### remark
- In the definition, the function measuring runtime, $T$ only have to be a map from $\mathbb N\to \mathbb N$ and no other requirements.
### definition: Time-constructible
>A function $T:\mathbb{N \to N}$ is [[time constructible]] if $T(n)\ge n$ and there is a TM $M$ that computes the function $x \mapsto {}_\llcorner T(\vert x\vert) {}_\lrcorner$ in time $T(n)$.

#### remark
- $T(n)\ge n$ restriction in the definition is to allow the algorithm time to read its input.
- Examples for time constructible functions: $n, n\log{n}, n^{2}, 2^{n}$.
- Time bounds in this book is restricted to the time constructible functions.
- Allowing time bounds that are not time constructible can lead to anomalous results 
	- What result?

### robustness of the TM
Some modifications on definition does not significantly increase of decrease the power of the model.

- Smaller alphabet gives $\log$ times slow down in runtime
	- Simulate a TM $M$ that has alphabet $\Gamma$ runtime $T(n)$ with $\tilde{M}$ that has binary alphabet results in $O(\log{\vert\Gamma\vert}T(n))$ runtime.
- Fewer tape gives poly level slow down
	- $k$-tape TM $\to$ single tape TM: $T(n)\to O(kT(n)^2)$.
- Bidirectional tape TM can be efficiently simulated
	- One-directional tape simulates bidirectional tape:
		- $T(n)\to 4T(n)$
		- $\Gamma\to \Gamma^2$

#### Oblivious Turing machines

A TM that the head location at the $i$th step of execution on input $x$ in only a function of $\vert x\vert$ and $i$.

## 1.4 Universal Turing Machine
### represent TM as string
we want the representation scheme have the following properties:
1. Every string in $\{0, 1\}^{*}$ represents some Turing machine.
	- Achievable by mapping the illegal strings to trivial Turing Machines.
2. Every TM is represented by infinitely many strings.
	- Achievable by allowing a TM's representation to end with arbitrarily long string of "1"s
	- This condition will simplify some proofs lately.

#### notations
- Given Turing machine $M$, ${}_\llcorner M_\lrcorner$ is the binary representation of $M$.
- Given binary string $\alpha$, $M_\alpha$ is the Turing machine that $\alpha$ represents.

### the universal Turing machine
>**Theorem 1.9** (Efficient universal Turing machine)
There exists a TM $\mathcal{U}$ such that for every $x,\alpha\in\{0,1\}^{*}$, $\mathcal{U}(x,\alpha)=M_{\alpha}(x)$.
Moreover, if $M_{\alpha}$ halts on input $x$ within $T$ steps then $\mathcal{U}(x,\alpha)$ halts within $CT\log{T}$ steps where $C$ is a number independent of $\vert x\vert$ and depending only on $M_{\alpha}$'s alphabet size, number of tapes and number of states.

####  UTM with time bound
A variant of the universal Turing machine gets a number $T$ as an extra input in addition to $x, \alpha$.
Such variant outputs $M_{\alpha}(x)$ if and only if $M_{\alpha}$ halts on $x$ within $T$ steps (otherwise outputting some special failure symbol).

#### remark

