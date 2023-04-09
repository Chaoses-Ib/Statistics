# Decision Tree Classifier
## Hyperplane
A hyperplane $h(x)$ is defined as the set of all points $x$ that satisfy the following equation:

$$h(x):w^Tx+b=0$$

where $w\in R^d$ is a *weight vector* that is normal to the hyperplane, and $b$ is the offset of the hyperplane from the origin.

A hyperplane specifies a decision or *split point* because it splits the data space $R$ into two half-spaces.

## Data partition
A split point of the form $X_j\le v$ induces the data partition:

$$\begin{align}
D_Y=\{x^T|x\in D,x_j\le v\} \\
D_N=\{x^T|x\in D,x_j> v\}
\end{align}$$

where $D_Y$ is the subset of data points that lie in region $R_Y$ and $D_N$ is the subset of input points that line in $R_N$.

## Purity
The purity of a region $R_j$ is defined in terms of the mixture of classes for points in the corresponding data partition $D_j$.

$$purity(D_j)=max_i\{\sum\frac{n_{ji}}{n_j}\}$$

where $n_j=|D_j|$ is the total number of data points in the region $R_j$, and $n_{ji}$ is the number of points in $D_j$ with class label $c_i$.

## Impurity measures
Let $t$ be the node, $c$ be the number of classes, $p_i(t)$ be the relative frequency of training instances that belong to class $i$ at node $t$.

$$\begin{align}
Entropy=-\sum_{i=0}^{c-1} p_i(t) \log_2{p_i(t)} \\
(\log_2{0}=0)
\end{align}$$

$$Gini\ index=1-\sum_{i=0}^{c-1}p_i(t)^2$$

$$Classification\ error=1-max_i[p_i(t)]$$

Consider an attribute test condition that splits a node containing $N$ training instances into $k$ children ${v_1,v_2,...,v_k}$. Let $N(v_j)$ be the number of traning instances associated with a child node $v_j$, whose impurity is $I(v_j)$.

$$Collective\ impurity=I(children)=\sum_{j=1}^k\frac{N(v_j)}{N}I(v_j)$$


## Identifying the best attribute test condition
To determine the goodness of an attribute test condition, we need to compare the degree of impurity of the parent node (before splitting) with the weighted degree of impurity of the child nodes (after splitting). This difference, termed as the $gain$ in purity of an attribute test condition, can be defined as follows:

$$\Delta=I(parent)-I(children)\ge0$$

When entropy is used as the impurity measure, the difference in entropy is commonly known as *information gain*, $\Delta_{info}$.

因为分支越多越容易导致 overfitting，将分支数纳入 gain 可以提高模型泛化性。其中的一种方法是 *gain ratio*：

$$Gain\ ratio
=\frac{\Delta_{info}}{Split\ info}
=\frac{Entropy(parent)-\sum_{i=1}^k \frac{N(v_i)}N Entropy(v_i)}
{-\sum_{i=1}^k \frac{N(v_i)}N\log_2\frac{N(v_i)}N}
$$

即 $\Delta_{info}$ 除以分支 entropy。


## Esimating the complexity of decision trees
The complexity of a decision tree can be estimated as the ratio of the number of leaf nodes $k$ to the number of training instances $N_{train}$, i.e. $\frac{k}{N_{train}}$.

Pessimistics error estimate:

$$err_{gen}(T)=err(T)+\Omega\cdot\frac{k}{N_{train}}$$

where $\Omega$ is a hyperparameter.

On the other hand, simply using the training error rate as an estimate of the generalization error rate is called the *optimistic error esitimate* or the *resubstitution estimate*.


## Pruning
为降低过拟合的风险，可以在决策树学习过程中进行 pruning。其中
- Prepruning 是在划分节点时将泛化性能纳入考察
- Post-pruning 是在生成决策树后，尝试将子树替换为叶节点（subtree replacement）或替换为高频分支（subtree raising），并根据泛化性能是否提升选择是否应用

prepruning 是局部最优算法，可能会导致 underfitting；post-pruning 的泛化性能更好，但是会加大训练开销。


## Characteristics
### Applicability
Decision trees are a nonparametric approach for building classification models.

### Expressiveness
A decision tree provides a universal represatation for discrete-valued functions.

### Computational efficiency
Many decision tree algorithms employ a heuristic-based approach to guide their search in the vast hypothesis space. And once a decision tree has been built, classifying a test record is extremely fast.

### Handling missing values
A decision tree classifier can handle missing attribute values in a number of ways, both in the training and the test sets.

### Handling interactions among attributes
Attributes are considered interacting if they are able to distinguish between classes when used together, but individually they provide little or no information. Due to the greedy nature of the splitting criteria in decision trees, they can perform poorly when there are interactions among attributes.

### Handling irrelevant attributes
The presence of a small number of irrelevant attributes will not impact the decision tree construction process. However, if there are a large number of irrelevant attributes, then some of these attributes may be accidentally chosen since these they may provide a better gain than a relevant attribute just by random chance.

### Handling redundant attributes
Since redundant attributes show similar gains in purity if they are selected for splitting, only one of them will be selected as an attribute test condition in the decision tree.

### Using rectilinear splits
Using only a single attribute in each test conition limits the expressiveness of decision trees in representing decision boundaries of data sets with continuous attributes. *Oblique decision tree* may overcome this limitation by allowing the test condition to be specified using more than one attribute.

### Choice of impurity measure
The choice of impurity measure often has little effect on the performance of decision tree classifiers since many of the impurity measures are quite consistent with each other.