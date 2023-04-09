# Locality-Sensitive Hashing for Documents
为了在 minhash 的基础上进一步减小寻找相似文档的开销，可以通过 hash 函数将相似的 minhash signature 往相近位置映射，也就是 locality-sensitive hashing（或 near-neighbor search）。

Suppose we use $b$ bands of $r$ rows each. We can calculate the probablity that the signatures agree in all the rows of at least one band, and therefore become a candidate pair, is:

$$1-(1-s^r)^b$$

The *threshold*, that is, the value of similarity $s$ at which the probablity of becoming a candidate is $\frac{1}{2}$, is approximately:

$$(\frac{1}{b})^{\frac{1}{r}}$$
