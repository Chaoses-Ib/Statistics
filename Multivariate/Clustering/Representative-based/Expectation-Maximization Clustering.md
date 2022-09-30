# Expectation-Maximization Clustering
## Gaussian mixture model
Assume that each cluster $C_i$ is characterized by a multivariate normal distribution:

$$f_i(x)=f(x|\mu_i,\Sigma_i)=\frac{1}{(\sqrt{2\pi})^d \sqrt{|\Sigma_i|}}
\exp{\{-\frac{(x-\mu)^T \Sigma_i^{-1}(x-\mu_i)}{2}\}}$$

where the cluster mean $\mu\in R^d$ and covariance matrix $\Sigma_i\in R^{d\times d}$ are both unknown parameters. $f_i(x)$ is the probablity density at $x$ attributable to cluster $C_i$.

Let $X=(X_1,X_2,...,X_d)$ denote the vector random variable across the $d$-attributes. We assume that the probability density function of $X$ is given as a **Gaussian mixture model** over all the $k$ normals:

$$f(x)=\sum_{i=1}^k f_i(x)P(C_i)=\sum_{i=1}^k f(x|\mu_i,\Sigma_i)P(C_i)$$

where the prior probabilities $P(C_i)$ are called the **mixture parameters**, which must satisfy the condition:
$$\sum_{i=1}^k P(C_i)=1$$

The set of all the model parameters is:
$$\theta=\{\mu_1,\Sigma_1,P(C_1),...,\mu_k,\Sigma_k,P(C_k)\}$$

## Maximum likelihood estimation
We define the **likelihood** of $\theta$ as the conditional probability of the data $D$ given the model parameters $\theta$, denoted as $P(D|\theta)$. Because each of the $n$ points $x_j$ is considered to be a random sample from $X$ (i.e., independent and identically distributed as $X$), the likelihood of $\theta$ is given as

$$P(D|\theta)=\prod_{i=1}^n f(x_j)$$

The goal of MLE is to choose the parameters $\theta$ that maximize the likelihood, that is,

$$\theta^* = \arg\max_\theta\{P(D|\theta)\} =
\arg\max_\theta\{\ln P(D|\theta)\}$$

where the log-likelihood function is given as

$$\ln P(D|\theta)=\sum_{j=1}^n\ln f(x_j)=\sum_{j=1}^n \ln(
\sum_{i=1}^k f(x|\mu_i,\Sigma_i)P(C_i)
)$$

Directly maximizing the log-likelihood over $\theta$ is hard. Instead, we can use the **expectation-maximization**.

## Expectation-maximization
EM is a two-step iterative approach:
- Initialization  
  Start from an initia guess for the parameters $\theta$ .
- Expectation step  
  Compute the cluster posterior probabilities $P(C_i|x_j)$ via the Bayes theorem:
  
  $$w_{ij}=P(C_i|x_j)=\frac{P(C_i \land x_j)}{P(x_j)}=
  \frac{ P(x_j|C_i)P(C_i) }{ \sum_{a=1}^k P(x_j|C_a) P(C_a) }
  =\frac{ f_i(x_j)P(C_i) }{ \sum_{a=1}^k f_a(x_j)P(C_a) }$$
  
- Maximization step  
  Using the weights $P(C_i|x_j)$ EM re-estimates $\theta$. The re-estimated mean is given as the weighted average of all the points, the re-estimated covariance matrix is given as the weighted covariance over all pairs of dimensions, and the re-estimated prior probability for each cluster is given as the fraction of weights that contribute to that cluster.
  
  $$\mu_i=\frac{ \sum_{j=1}^n w_{ij}\cdot x_j }{ \sum_{j=1}^n w_{ij} }$$
  
  $$\sigma^2_i=\frac{ \sum_{j=1}^n w_{ij}(x_j-\mu_i)^2 }{ \sum_{j=1}^n w_{ij} }$$
  
  $$P(C_i)=\frac{ \sum_{j=1}^n w_{ij} }{ \sum_{a=1}^k \sum_{j=1}^n w_{aj} }
  = \frac{ \sum_{j=1}^n w_{ij} }{ n }$$

- Iteration  
  Until $\sum_{i=1}^k ||\mu_i^t - \mu_i^{t-1}||^2 \le \epsilon$ .

Q:
- [ ] 为什么叫做“Expectation-Maximization”？