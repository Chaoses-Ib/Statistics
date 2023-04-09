# Missing Values
Several strategies for dealing with missing data:
- Eliminate data objects or attributes
- Estimate missing values
- Ignore the missing value during analysis
  
  Many data mining approaches can be modified to ignore missing values.

## Finding missing values
```python
df.dtypes
```
```python
df.isnull().sum()
```

## Imputation of missing values
[6.4. Imputation of missing values — scikit-learn 1.0.2 documentation](https://scikit-learn.org/stable/modules/impute.html)

One type of imputation algorithm is univariate, which imputes values in the i-th feature dimension using only non-missing values in that feature dimension (e.g. `impute.SimpleImputer`). By contrast, multivariate imputation algorithms use the entire set of available feature dimensions to estimate the missing values (e.g. `impute.IterativeImputer`).

### Univariate feature imputation
[sklearn.impute.SimpleImputer — scikit-learn 1.0.2 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.impute.SimpleImputer.html#sklearn.impute.SimpleImputer)
```python
imp = SimpleImputer(missing_values=np.nan, strategy='mean')
imp.fit(
    [[1, np.nan, np.nan],
     [3, 4, np.nan]]
    )
imp.statistics_
```
```python
array([ 2.,  4., nan])
```
可如果我只想 fit 一个列，我该怎么把列转成 fit 要求的样子？

`df[[col]]`

对不起，是我的想象力拖了后腿

strategy 可以为：
- mean
- median
- most_frequent
- constant (fill_value)

~~因为方差就是样本减去均值的平方之和，mean 显然具有最小方差。~~

插入的值会影响均值，进而对方差产生影响。

不依赖其它 feature 时，mean 插值具有最小的方差吗？

[最优插值法_百度百科](https://baike.baidu.com/item/%E6%9C%80%E4%BC%98%E6%8F%92%E5%80%BC%E6%B3%95/5018339)

[Kriging - Wikipedia](https://en.wikipedia.org/wiki/Kriging)

### Multivariate feature imputation
```python
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer
imp = IterativeImputer(max_iter=10, random_state=0)
```

[请教一个深度学习的问题 - V2EX](https://www.v2ex.com/t/843403#reply18)
