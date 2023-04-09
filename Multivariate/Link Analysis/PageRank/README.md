# PageRank
## PageRank
The **transition matrix** $M$ has $n$ rows and columns, if there are $n$ pages. The element $m_{ij}$ in row $i$ and column $j$ has value $\frac{1}{k}$ if page $j$ has $k$ arcs out, and one of them is to $page$ i. Otherwise, $m_{ij}=0$.

Suppose we start a random surfer at any of the $n$ pages with equal probability. Then the initial vector $v_0$ will have $\frac{1}{n}$ for each component After one step, the distribution of the surfer will be $Mv_0$, and so on.

This sort of behavior is an example of the ancient theory of **Markov processes**. It is known that the distribution of the surfer approaches a limiting distribution $v$ that satisfies $v=Mv$, provided two conditions are met:
- The graph is strongly connected
- There are no dead ends

## Dead ends and Spider traps
Dead-end nodes
- Pruning
- Taxation

A spider trap is a set of nodes with no dead ends but no arcs out (cycle). It cause the PageRank calculation to place all the PageRank within the spider trap.

## Taxation
We modify the calculation of PageRank by allowing each random surfer a small probabilty of *teleporting* to a random page:

$$v'=\beta Mv+(1-\beta)\frac{e}{n}$$

where $\beta$ is a chosen constant, usually in the range 0.8 to 0.9, $e$ is a vector of all 1's with the appropriate number of components, and $n$ is the number of nodes in the Web graph.