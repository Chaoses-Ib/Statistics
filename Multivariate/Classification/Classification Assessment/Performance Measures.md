# Performance Measures
Let $D$ be the testing set comprising $n$ points in a $d$ dimensional space, let $\{c_1,c_2,...,c_k\}$ denote the set of $k$ class labels, and let $M$ be a classifier. For $x_i\in D$, let $y_i$ denote its true class, and let $\hat{y_i}=M(x_i)$ denote its predicated class.

## Accuracy and error rate

$$Accuracy+Error\ Rate=1$$

### Accuracy
Accuracy is an astimate of the probability of a correct prediction. It is defined as the fraction of correct predictions over the testing set:

$$\begin{align}
Accuracy &= \frac{1}{n} \sum_{i=1}^{n}I(y_i=\hat{y_i}) \\
&=  \sum_{i=1}^k(\frac{m_i}{n})acc_i = \frac{1}{n} \sum_{i=1}^k n_{ii} \\
&=  \sum_{i=1}^k(\frac{n_i}{n})recall_i = \frac{1}{n} \sum_{i=1}^k n_{ii}
\end{align}$$

### Error rate
Error rate is an estimate of the probability of misclassification. It is defined as the fraction of incorrect predications for the classifier over the testing set:

$$Error\ rate=\frac{1}{n} \sum_{i=1}^{n} I(y_i\ne \hat{y_i})$$

### Top-n accuracy
[classification - ImageNet: what is top-1 and top-5 error rate? - Cross Validated](https://stats.stackexchange.com/questions/156471/imagenet-what-is-top-1-and-top-5-error-rate)
> In the case of the top-1 score, you check if the top class (the one with the highest probability) is the same as the target label.
> 
> In the case of the top-5 score, you check if the target label is one of your top 5 predictions (the 5 ones with the highest probabilities).

## Contingency table-based measures
Let $D=\{D_1,D_2,...,D_k\}$ donote a partitioning of the testing points based on their true class labels, where

$$D_j=\{x_i^T|y_i=c_j\}\ \land\ n_i=|D_i|$$

Let $R=\{R_1,R_2,...,R_k\}$ donote a partitioning of the testing points based on their true class labels, where

$$R_j=\{x_i^T|\hat{y_i}=c_j\}\ \land\ m_i=|D_i|$$

The partitionings $R$ and $D$ induce a $k\times k$ contingency table $N$, also called *confusion matrix*, defined as follows:

$$N(i,j)=n_{ij}=|R_i \cap D_j|=|\{ x_a\in D | \hat{y_a}=c_i \land y_a=c_j \}|$$

即真实分类与预测分类的交集的点数。

### Precision and recall
Precision/Accuracy:

$$prec_i=acc_i=\frac{n_{ii}}{m_i}$$

预测分类中预测正确的比例。

Recall/Coverage:

$$recall_i=coverage_i=\frac{n_{ii}}{n_i}$$

真实分类中预测正确的比率。

只用 precision 或只用 recall 来评价对单个分类的性能是不准确的，只用 precision 的话，只要只保留高把握的分类结果就可以提高 precision；只用 recall 的话，只要把其它分类的点放进分类充数就可以提高 recall。作为一种调和方法，可以用 F-measure 来评价单个分类的性能。

需要注意的是，precision 或 recall 的问题只存在于对单个分类的评价中，对总体进行评价时不存在问题。并且 precision 与 recall 推广到总体后是等同的。

### F-measure
The harmonic mean of precision and recall values:
$$F_i=\frac{2}{\frac{1}{prec_i}+\frac{1}{recall_i}}=\frac{2\cdot prec_i\cdot recall_i}{prec_i+recall_i}=\frac{2 n_{ii}}{n_i+m_i}$$

![|400](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Precisionrecall.svg/800px-Precisionrecall.svg.png) [^wiki]

[^wiki]: [Precision and recall - Wikipedia](https://en.wikipedia.org/wiki/Precision_and_recall)

## Averaging methods
Micro-averaging takes all samples as qually important, while macro-averaging takes all classes as qually important. For macro-averaging, two different formulas have been used: the F-score of class-wise precision and recall means or the arithmetic mean of class-wise F-scores, where the latter exhibits more desirable properties. [^F-score]

Weighted-averaging takes the support-weighted mean per class.

The following code demonstrates a specific calculation process:
```python
from sklearn import metrics
print(metrics.classification_report([0, 1, 2, 2, 2], [0, 0, 2, 2, 1]))

f1 = [0.6666666666666666, 0, 0.8]

print('micro avg:', 2*3 / (2*3 + 2 + 2))  # 2TP / (2TP + FP + FN)
print('macro avg:', 1/3 * f1[0] + 1/3 * f1[1] + 1/3 * f1[2])
print('weighted avg:', 1/5 * f1[0] + 1/5 * f1[1] + 3/5 * f1[2])
```

[^F-score]: [F-score - Wikipedia](https://en.wikipedia.org/wiki/F-score)