# Probabilistic Graphical Models
[Wikipedia](https://en.wikipedia.org/wiki/Graphical_model)

A **graphical model (probabilistic graphical model (PGM), structured probabilistic model)** is a probabilistic model for which a graph expresses the conditional dependence structure between random variables.[^wiki]

In a probabilistic graphical model, each node represents a random variable (or group of random variables), and the links express probabilistic relationships between these variables. The graph then captures the way in which the joint distribution over all of the random variables can be decomposed into a product of factors each depending only on a subset of the variables.

In **Bayesian networks**, also known as directed graphical models, the links of the graphs have a particular directionality indicated by arrows. The other major class of graphical models are **Markov random ﬁelds**, also known as undirected graphical models, in which the links do not carry arrows and have no directional signiﬁcance. For the purposes of solving inference problems, it is often convenient to convert both directed and undirected graphs into a different representation called a **factor graph**.[^prml]

![](images/relationship.png)

## Convertion between directed and undirected graphs
To convert a directed graph into an undirected graph, we ﬁrst add additional undirected links between all pairs of parents for each node in the graph and then drop the arrows on the original links to give the undirected graph. The process of ‘marrying the parents’ has become known as **moralization**, and the resulting undirected graph, after dropping the arrows, is called the **moral graph**.[^prml]


[^wiki]: [Graphical model - Wikipedia](https://en.wikipedia.org/wiki/Graphical_model)
[^prml]: Bishop, Christopher M., and Nasser M. Nasrabadi. Pattern Recognition and Machine Learning. Vol. 4. 4. Springer, 2006.