# Bayesian Inference
[Wikipedia](https://en.wikipedia.org/wiki/Bayesian_inference)

One of the many applications of Bayes' theorem is **Bayesian inference**, a particular approach to statistical inference. When applied, the probabilities involved in the theorem may have different probability interpretations. With Bayesian probability interpretation, the theorem expresses how a degree of belief, expressed as a probability, should rationally change to account for the availability of related evidence. Bayesian inference is fundamental to Bayesian statistics, being considered by one authority as; "to the theory of probability what Pythagoras's theorem is to geometry."[^theorem-wiki]

The frequentist perspective is that the true parameter value $\theta$ is ﬁxed but unknown, while the point estimate $\hat{\theta}$ is a random variable on account of it being a function of the dataset (which is seen as random).

The Bayesian perspective on statistics is quite diﬀerent. The Bayesian uses probability to reﬂect degrees of certainty in states of knowledge. The dataset is directly observed and so is not random. On the other hand, the true parameter $\theta$ is unknown or uncertain and thus is represented as a random variable.

Before observing the data, we represent our knowledge of $\theta$ using the **prior probability distribution (the prior)**, $p(\theta)$. Generally, the machine learning practitioner selects a prior distribution that is quite broad (i.e., with high entropy) to reﬂect a high degree of uncertainty in the value of $\theta$ before observing any data.

Now consider that we have a set of data samples $\{x^{(1)},\cdots,x^{(m)}\}$. We can recover the eﬀect of data on our belief about $\theta$ by combining the data likelihood $p(x^{(1)},\cdots,x^{(m)}|\theta)$ with the prior via Bayes' rule:

$$p(\theta|x^{(1)},\cdots,x^{(m)})= {p(x^{(1)},\cdots,x^{(m)}|\theta) p(\theta) \over p(x^{(1)},\cdots,x^{(m)})}$$
In the scenarios where Bayesian estimation is typically used, the prior begins as a relatively uniform or Gaussian distribution with high entropy, and the observation of the data usually causes the posterior to lose entropy and concentrate around a few highly likely values of the parameters.

Relative to maximum likelihood estimation, Bayesian estimation oﬀers two important diﬀerences. First, unlike the maximum likelihood approach that makes predictions using a point estimate of $\theta$, the Bayesian approach is to make predictions using a full distribution over $\theta$. For example, after observing $m$ examples, the predicted distribution over the next data sample, $x^{(m+1)}$, is given by

$$p(x^{(m+1)}|x^{(1)},\cdots,x^{(m)})=
\int{p(x^{m+1}|\theta) p(\theta|x^{(1)},\cdots,x^{(m)})d\theta}$$

Here each value of $\theta$ with positive probability density contributes to the prediction of the next example, with the contribution weighted by the posterior density itself. After having observed $\{x^{(1)},\cdots,x^{(m)}\}$, if we are still quite uncertain about the value of $\theta$, then this uncertainty is incorporated directly into any predictions we might make.

The frequentist approach addresses the uncertainty in a given point estimate of $\theta$ by evaluating its variance. The variance of the estimator is an assessment of how the estimate might change with alternative samplings of the observed data. The Bayesian answer to the question of how to deal with the uncertainty in the estimator is to simply integrate over it, which tends to protect well against overﬁtting. This integral is of course just an application of the laws of probability, making the Bayesian approach simple to justify, while the frequentist machinery for constructing an estimator is based on the rather ad hoc decision to summarize all knowledge contained in the dataset with a single point estimate.

The second important diﬀerence between the Bayesian approach to estimation and the maximum likelihood approach is due to the contribution of the Bayesian prior distribution. The prior has an inﬂuence by shifting probability mass density towards regions of the parameter space that are preferred a priori. In practice, the prior often expresses a preference for models that are simpler or more smooth. Critics of the Bayesian approach identify the prior as a source of subjective human judgment aﬀecting the predictions.

Bayesian methods typically generalize much better when limited training data is available but typically suﬀer from high computational cost when the number of training examples is large.[^deeplearning]


[^theorem-wiki]: [Bayes' theorem - Wikipedia](https://en.wikipedia.org/wiki/Bayes%27_theorem)
[^deeplearning]: Goodfellow, Ian, Yoshua Bengio, and Aaron Courville. _Deep Learning_. MIT Press, 2016.