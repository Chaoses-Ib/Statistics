# Similarity-Preserving Summaries of Sets
## Matrix representation of sets
Element | $S_1$ | $S_2$ | $S_3$ | $S_4$
--- | --- | --- | --- | ---
 $a$ | 1 | 0 | 0 | 1
 $b$ | 0 | 0 | 1 | 0
 $c$ | 0 | 1 | 0 | 1
 $d$ | 1 | 0 | 1 | 1
 $e$ | 0 | 0 | 1 | 0

## Minhashing
按给定元素排列进行测试，集合中含有的第一个元素就是 minhash 的值。

$$SIM(S_1,S_2)=p[h(S_1)=h(S_2)]$$

The probability that the minhash function for a random permutation of rows produces the same value for two sets equals the Jaccard similarity of those sets.

For two sets:
- $x$ : number of rows have 1 in both columns
- $y$ : number of rows have 1 in one of the columns and 0 in the other
- $z$ : number of rows have 0 in both columns

$$SIM(S_1,S_2)=p[h(S_1)=h(S_2)]=\frac{x}{x+y}$$

## Minhash Signatures
To represent sets, we pick at random some number $n$ of permutations of the rows of $M$. From the column representing set $S$, construct the *minhash signature* for $S$, the vector $[h_1(S),h_2(S),...,h_n(S)]$.

We normally represent a minhash signature as a column, thus we can form a *signature matrix*. The signature matrix has the same number of columns as $M$ but only $n$ rows.

## Computing Minhash Signatures
Instead of picking $n$ random permutations of rows, we pick $n$ randomly chosen hash functions $h_1, h_2,..., h_n$ on the rows. Let $SIG(i, c)$ be the element of the signature matrix for the $i$th hash function and column $c$. Initially, set $SIG(i, c)$ to $\infty$ for all $i$ and $c$. We handle row $r$ by doing the following:
1. Compute $h_1(r), h_2(r),..., h_n(r)$
2. For each column $c$ having 1, for each $i=1,2,...,n$ set $SIG(i,c)$ to the smaller of the current value of $SIG(i,c)$ and $h_i(r)$.