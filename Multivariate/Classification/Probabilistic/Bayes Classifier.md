# Bayes Classifier
The Bayes classifier directly uses the Bayes theorem to predict the class for a new test instance, $x$. It estimates the posterior probability $P(c_i|x)$ for each class $c_i$, and chooses the class that has the largest probability. The prodicated class for $x$ is given as

$$\hat{y}=argmax_{c_i}\{P(c_i|x)\}$$

The Bayes theorem allows us to invert the posterior probability in terms of the likelihood and prior probablity, as follows:

$$P(c_i|x)=\frac{P(x|c_i)P(c_i)}{P(x)}$$

where $P(x|c_i)$ is the *likelihood*, defined as the probablity of observing $x$ assuming that the true class is $c_i$, $P(c_i)$ is the *prior probablity* of class $c_i$, and $P(x)$ is the probablity of observing $x$ from any of the $k$ classes, given as

$$P(x)=\sum_{j=1}^k P(x|c_j)P(c_j)$$

Because $P(x)$ is fixed for a given point, Bayes rule can be rewritten as

$$\begin{align}
\hat{y}&=argmax_{c_i}\{P(c_i|x)\} \\
&=argmax_{c_i}\{P(x|c_i)P(c_i)\}
\end{align}$$

In other words, the predicted class essentially depends on the likelihood of that class taking its prior probability into account.

## Estimating the prior probablity
$$\hat{P}(c_i)=\frac{n_i}{n}$$

## Estimating the Likelihood
### Numeric Attributes
Assuming all dimensions are numeric, we can estimate the joint probability of $x$ via either a nonparametric or a parametric approach.

In the parametric approach we typically assume that each class $c_i$ is normally distributed around some mean $\mu_i$ with a corresponding covariance matrix $\Sigma_i$, both of which are estimated from $D_i$. For class ci, the probability density at $x$ is thus given as

$$f_i(x)=f(x|\mu_i,\Sigma_i)=\frac{1}{(\sqrt{2\pi})^d \sqrt{|\Sigma_i|}}
\exp{\{-\frac{(x-\mu)^T \Sigma_i^{-1}(x-\mu_i)}{2}\}}$$
