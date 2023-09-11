#information-theory #cryptography
> AES is arguably the most widely used cipher.  This talk covers a recent line of works targeting *provable* security of AES and other block ciphers.
> We consider *t-wise independence*, a natural and attractive security target for block ciphers.  A block cipher is t-wise independent, if for any t plaintexts, the joint distribution of the t corresponding ciphertexts is statistically close to uniform.  It implies resistance to any statistical attack that only involves a few inputs.
> We have a collection of results showing AES and a few of its variants are t-wise independent, under different parameters (the value of t, the security level, the number of rounds, etc).  Some of them will be presented in this talk.
> The t-wise Independence of Substitution-Permutation Networks. Tianren Liu, Stefano Tessaro, Vinod Vaikuntanathan.  Crypto 2021.   https://eprint.iacr.org/2021/507.
> Layout Graphs, Random Walks and the t-wise Independence of SPN Block Ciphers.  Tianren Liu, Angelos Pelecanos, Stefano Tessaro, Vinod Vaikuntanathan.  Crypto 2023.
## Questions before the talk

What is AES?
Advanced Encryption System.

How to quantify it using tools from information theory?

What is a block cipher?

What is t-wise independence?

What's the general idea to show AES is *provable* secure?

## The talk
random-looking key permutation:
- theory: pseudorandom permutation
- practice block cipher

### Pseudorandom Permutation
- one-way function
- factoring
- lattice problem

provably secure but not practical.

### Block Cipher
AES: very efficient, but not provably secure.

Key-Altering Cipher (KAC)
n-bit(input) --> xor($k_0$) --> $\pi$ --> xor($k_1$) --> $\pi$ --> xor($k_2$) --> n-bit(output)
