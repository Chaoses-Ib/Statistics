# Measures of Similarity and Dissimilarity
Informally, the **similarity** between two objects is a numerical measure of the degree to which the two objects are alike. Similarities are usually non-negative and are often between 0 (no similarity) and 1 (complete similarity).

The **dissimilarity** between two objects is a numerical measure of the degree to which the two objects are different. Frequently, the term distance is used as a synonym for dissimilarity, although, as we shall see, distance often refers to a special class of dissimilarities. Dissimilarities sometimes fall in the interval $[0, 1]$, but it is also common for them to range from $0$ to $\infty$.

For convenience, the term proximity is used to refer to either similarity or dissimilarity.

### Transformations
Transformations are often applied to convert a similarity to a dissimilarity, or vice versa, or to transform a proximity measure to fall within a particular range, such as $[0,1]$.

### Single attribute
![](images/Single%20Attribute.png)

## Multiple attributes
### Dissimilarities

### Distances
Metrics
- Positivity
  
  $d(x,y)\ge 0$
  $d(x,y)=0 \iff x=0$
- Symmetry
  
  $d(x,y)=d(y,x)$
- Triangle Inequality
  
  $\forall x,y,z,\ d(x,z)\le d(x,y)+d(y,z)$


Minkowski distance

$$d(x,y)=(\sum_{k=1}^n{|x_k-y_k|}^r)^{\frac{1}{r}}$$

- $r=1$: City block distance
  - Hamming distance
  
    The Hamming distance between two strings of equal length is the number of positions at which the corresponding symbols are different.
- $r=2$: Euclidean distance
  
  $d(x,y)={(\sum_{k=1}^n{(x_k-y_k)^2})}^{\frac{1}{2}}$
- $r=\infty$: Supremum distance


### Similarities
- Similarity coefficients
  - Simple matching coefficient
  
    $$\begin{align}
    SMC&=\frac{\text{number of matching attributes}}{\text{number of attributes}} \\
    &=\frac{M_{00}+M_{11}}{M_{00}+M_{11}+M_{01}+M_{10}}
    \end{align}$$

- Jaccard coefficient
  
  $$J=\frac{M_{11}}{M_{01}+M_{10}+M_{11}}$$

  [Jaccard Similarity – LearnDataSci](https://www.learndatasci.com/glossary/jaccard-similarity/)
  - Extended Jaccard coefficient (Tanimoto coefficient)
- Cosine similarity
  
  $$\text{cosine similarity}=S_C(A,B)=cos(\theta)=\frac{A\cdot B}{|A||B|}
  =\frac{ \sum_{i=1}^n A_i B_i }{ \sqrt{\sum_{i=1}^n A_i^2} \sqrt{\sum_{i=1}^n B_i^2 } }$$

- Correlation
  
  [NumPy, SciPy, and Pandas: Correlation With Python – Real Python](https://realpython.com/numpy-scipy-pandas-correlation-python/)
  - Pearson's correlation
    $$\rho_{X,Y}=\frac{cov(X,Y)}{\sigma_X\sigma_Y}$$

![](images/Properties%20of%20distances.png)


### Mutual information
Can be used as a measure of similarity between values having non-linear relationship.

```python
df_sample = df.sample(100000)
X = df_sample.drop(['Class'], axis=1)
y = df_sample['Class']
feature_selection.mutual_info_regression(X, y)
```

### Maximal information coefficient
[On Maximal Information Coefficient: A Modern Approach for Finding Associations in Large Data sets | by Rhondene Wint | Medium](https://medium.com/@rhondenewint93/on-maximal-information-coefficient-a-modern-approach-for-finding-associations-in-large-data-sets-ba8c36ebb96b)
