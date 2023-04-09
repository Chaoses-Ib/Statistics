# Model Evaluation
Let $\theta$ be the performance measure.

## Holdout method
Randomly partition the labeled set $D$ into disjoint training set and test set.

The holdout method can be repeated several times to obtain a distribution of the test error sets, an approach known as *random subsampling* or *repeated holdout method*.

## $K$-fold cross-validation
Cross-validation is a widely-used evaluation method that aims to make effective use of all labeled instances in $D$ for both training and testing. It divides the dataset $D$ into $K$ equal-sized parts, called *folds*, namely $D_1,D_2,...,D_k$. Each fold $D_i$ is, in turn, treated as the testing set, with the remaining folds comprsing the training set $D \backslash D_i = U_{j\ne i}D_j$ . After training the model $M_i$ on $D\backslash D_i$, we assess its performance on the testing set $D_i$ to obtain the $i$th estimate $\theta_i$ . The expected value of the performance of the performance measure can then be estimated as

$$\hat{\mu_\theta}=E(\theta)=\frac{1}{K}\sum_{i=1}^K \theta_i$$

and its variance as

$$\sigma^2_\theta=\frac{1}{K}(\theta_i-\hat{\mu_\theta})^2$$

The special case, when $K=n$, is called *leave-one-out* cross-validation, where the testing set comprises a single point and the remaining data is used for training purposes. This approach has the advantage of utilizing as much data as possible for training. However, leave-one-out can be computationally expensive and produce quite misleading results in some special scenarios.

## Bootstrap resampling
Instead of partitioning the input dataset $D$ into disjoint folds, the bootstrap method draws $K$ random samples of size $n$ *with replacement* from $D$.

The probablity that a given point is selected is given as $p=\frac{1}{n}$, and thus the probablity that it is not selected is

$$q=1-\frac{1}{n}$$

The probablity that $x_j$ is not selected even after $n$ tries is given as

$$P(x_j\notin D_i)=q^n=(1-\frac{1}{n})^n \approx e^{-1} \ \approx 0.368$$

On the other hand, the probablty that $x_j\in D_j$ is given as

$$P(x_j\in D_j)=1-P(x_j\notin D_i)\approx0.632$$

This means that each bootstrap sample contains approximately 63.2% of the points from $D$.

The bootstrap samples can be used to evaluate the classifier by training it on each of samples $D_i$ and then using the full input dataset $D$ as the testing set. However, it should be borne in mind that the estimates will be somewhat optimistic owing to the fairly large overlap between the training and testing datasets (63.2%).

## Comparing classifiers: paired $t$-test
We perform a *paired test* with both classifiers trained trained and tested on the same data. Let $\theta_1^A,\theta_2^A,...,\theta_K^A$ and $\theta_1^B,\theta_2^B,...,\theta_K^B$ denote the performance values for $M_A$ and $M_B$, respectively. Define the random variable $\delta_i$ as the difference in their performance on the $i$th dataset:

$$\delta_i=\theta_i^A-\theta_i^B$$

Now consider the estimates for the expected difference and the variance of the differences:

$$\begin{align}
\hat{\mu_\delta}&=\frac{1}{K}\sum_{i=1}^K \delta_i \\
\hat{\sigma_\delta^2}&=\frac{1}{K}\sum_{i=1}^K(\delta_i-\hat{\mu_\delta})^2
\end{align}$$

We can set up a hypothesis testing framework to determine if there is a statistically significant difference between the performance of $M^A$ and $M^B$.