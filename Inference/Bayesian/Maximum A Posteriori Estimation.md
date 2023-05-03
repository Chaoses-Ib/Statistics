# Maximum A Posteriori Estimation
[Wikipedia](https://en.wikipedia.org/wiki/Maximum_a_posteriori_estimation)

While the most principled approach is to make predictions using the full Bayesian posterior distribution over the parameter $\theta$, it is still often desirable to have a single point estimate. One common reason for desiring a point estimate is that most operations involving the Bayesian posterior for most interesting models are intractable, and a point estimate oﬀers a tractable approximation.

Rather than simply returning to the maximum likelihood estimate, we can still gain some of the beneﬁt of the Bayesian approach by allowing the prior to inﬂuence the choice of the point estimate. One rational way to do this is to choose the **maximum a posteriori (MAP)** point estimate. The MAP estimate chooses the point of maximal posterior probability (or maximal probability density in the more common case of continuous $\theta$):

$$\theta_{MAP}=\arg\max_\theta{p(\theta|x)} = \arg\max_\theta{\log p(x|\theta)+\log p(\theta)}$$

We recognize, on the righthand side, $\log p(x | \theta)$, that is, the standard log-likelihood term, and $\log p(\theta)$, corresponding to the prior distribution.[^deeplearning]

Maximum likelihood estimation 估计的是最可能观察到指定样本时的参数，但没有考虑观察到对应参数本身的可能性，而 maximum a posteriori estimation 则利用 prior probability distribution 的知识补上了这一缺陷。

As with full Bayesian inference, MAP Bayesian inference has the advantage of leveraging information that is brought by the prior and cannot be found in the training data. This additional information helps to reduce the variance in the MAP point estimate (in comparison to the ML estimate). However, it does so at the price of increased bias.

Many regularized estimation strategies, such as maximum likelihood learning regularized with weight decay, can be interpreted as making the MAP approximation to Bayesian inference. This view applies when the regularization consists of adding an extra term to the objective function that corresponds to $\log p(\theta)$. Not all regularization penalties correspond to MAP Bayesian inference. For example, some regularizer terms may not be the logarithm of a probability distribution. Other regularization terms depend on the data, which of course a prior probability distribution is not allowed to do.

MAP Bayesian inference provides a straightforward way to design complicated yet interpretable regularization terms. For example, a more complicated penalty term can be derived by using a mixture of Gaussians, rather than a single Gaussian distribution, as the prior.[^deeplearning]


[^deeplearning]: Goodfellow, Ian, Yoshua Bengio, and Aaron Courville. _Deep Learning_. MIT Press, 2016.