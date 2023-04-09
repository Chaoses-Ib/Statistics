# Polynomial Feature Transform
[sklearn.preprocessing.PolynomialFeatures](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.PolynomialFeatures.html)
```python
import sklearn

poly = preprocessing.PolynomialFeatures(degree=2, interaction_only=False)
X_poly = pd.DataFrame(poly.fit_transform(df.drop(['Class'], axis=1)))
X_poly.head()
```
