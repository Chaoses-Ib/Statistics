# Kernel Density Estimation
[Wikipedia](https://en.wikipedia.org/wiki/Kernel_density_estimation)

$$p(x)={K\over NV}$$
where $N$ is the number of observations drawm from $p(x)$, $K$ is the total number of points that lie inside a sufficiently small regison $R$, $V$ is the volume of $R$.

We can exploit this formula in two different ways. Either we can ﬁx $K$ and determine the value of $V$ from the data, which gives rise to the $K$-nearest-neighbour technique, or we can ﬁx $V$ and determine $K$ from the data, giving rise to the kernel approach. It can be shown that both the $K$-nearest-neighbour density estimator and the kernel density estimator converge to the true probability density in the limit $N \to\infty$ provided $V$ shrinks suitably with $N$, and $K$ grows with
$N$.[^prml]

Kernel functions:
- Parzen window
- Gaussian

[Kernel Density Estimation (mathisonian.github.io)](https://mathisonian.github.io/kde/)


[^prml]: Bishop, Christopher M., and Nasser M. Nasrabadi. _Pattern Recognition and Machine Learning_. Vol. 4. 4. Springer, 2006.