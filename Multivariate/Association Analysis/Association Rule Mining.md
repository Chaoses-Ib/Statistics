# Association Rule Mining
Given a frequent itemset $Z\in F$, we look at all proper subsets $X\subset Z$ to compute rules of the form

$$X\xrightarrow{S,C}Y,\text{where }Y=Z\backslash X$$

The rule must be frequent because

$$s=sup(XY)=sup(Z)\ge minsup$$

Thus, we have to only check whether the rule confidence satisfies the $minconf$ threshold:

$$c=\frac{sup(X\cup Y)}{sup(X)}=\frac{sup(Z)}{sup(X)}\ge minconf$$

If $c\ge minconf$, then the rule is a strong rule. On the other hand, if $c<minconf$, then $conf(W\rightarrow Z\backslash W)<c<minconf$ for all subsets $W\subset X$, as $sup(W)\ge sup(X)$. We can thus avoid checking subsets of $X$.

![](images/Association%20Rule%20Mining.png)
