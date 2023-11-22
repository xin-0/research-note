## definition

A function $T:\mathbb{N \to N}$ is *time constructible* if $T(n)\ge n$ and there is a TM $M$ that computes the function $x \mapsto {}_\llcorner T(\vert x\vert) {}_\lrcorner$ in time $T(n)$. ^[1]

## examples
Examples for time constructible functions: $n, n\log{n}, n^{2}, 2^{n}$.

## why useful
When defining a Turing machine $M$, if we let its runtime $T(n)$ to be a time constructible function then $M$ can "know" its running time without any overhead in runtime by simply use a counter. it is because the counting can be done in $T(n)$, by the time-constructible property.

[1]: [[1 Computational Model | Arora]]