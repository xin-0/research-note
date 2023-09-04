
## 0.1 Representing objects as strings
$\{0,1\}^n$ : the set of all strings of length $n$.
$\{0,1\}^*$ : the set of all strings. $:= \cup_{n \ge 0}\{0,1\}^n$.

$\llcorner x\lrcorner$ : some canonical binary representation of the object $x$. Usually $x$ itself is used to denote both the object and its representation.

$\circ$ : string concatenation operator. 

### An example of encoding: Representing pairs and tuples
To Encode $\braket{x, y}$ into binary
1. encode $\braket{x, y}$ as the string $\llcorner x\lrcorner \circ \# \circ \llcorner y\lrcorner$ over the alphabet $\{0, 1, \#\}$
2. then use mapping: $0\mapsto00, 1\mapsto11, \#\mapsto01$,

## 0.2 Decision problem / languages
Given a [[Boolean function]] $f: \{0,1\}^*\mapsto \{0, 1\}$. We define a [[language]] or a [[decision problem]] as:
$$L_f=\{x\in\{0,1\}^*:f(x)=1\}$$

## 0.3 Big-O notation
Efficient of an algorithm is typically measured by a function $T:\mathbb {N \mapsto N}$ that outputs the maximum number of some basic operations given problem input length $n$.

### definition
If $f, g$ are two functions from $\mathbb N$ to $\mathbb N$, then we say:
1. $f=O(g)$ if $\exists c\in \mathbb R: f(n) \le c\cdot g(n)$ for every sufficiently large $n$.
2. $f=\Omega(g)$ if $g = O(f)$.
3. $f=\Theta(g)$ if $f = O(g)$ and $g = O(f)$.
4. $f = o(g)$ if $\forall \epsilon \gt 0: f(n) \le \epsilon \cdot g(n)$ for every sufficiently large $n$.
5. $f = \omega(g)$ if $g = o(f)$.

#### example & remark
1. For $f(n)=10n^2$, $g(n) = n^2$ $g'(n)=n^2 + n$, $f=O(g)$ and $f=O(g’)$. Big O notation let us be able to ignore constant coefficient and lower order terms in a function.

