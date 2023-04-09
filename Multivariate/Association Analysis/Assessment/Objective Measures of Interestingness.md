# Objective Measures of Interestingness
| | $B$ | $\bar{B}$ | |
--- | --- | --- | ---
$A$ | $f_{11}$ | $f_{10}$ | $f_{1+}$
$\bar{A}$ | $f_{01}$ | $f_{00}$ | $f_{0+}$
|  | $f_{+1}$ | $f_{+0}$ | $N$

This table shows an example of a contingency table for a pair of binary variables, $A$ and $B$. We use notation $\bar A$ to indicate that $A$ is absent from a trasaction. Each entry $f_{ij}$ in this $2\times 2$ table denotes a frequency count. The row sum $f_{1+}$ represents the support count for $A$, while the column sum $f_{+1}$ represents the support count for $B$.

### Confidence
$$conf(A\rightarrow B)=\frac{s(A,B)}{s(A)}=\frac{Nf_{11}}{f_{1+}}$$

### Interest factor (lift)
$$I(A,B)=\frac{s(A,B)}{s(A)s(B)}=\frac{Nf_{11}}{f_{1+}f_{+1}}$$

### Piatesky-Shapiro measure
$$PS=s(A,B)-s(A)s(B)=\frac{f_{11}}{N}-\frac{f_{1+}f_{+1}}{N^2}$$

### Correlation analysis
For binary variables, correlation can be measured using the $\phi$-coefficient, which is defined as

$$\begin{align}
\phi&=\frac{f_{11}f_{00}-f_{01}f_{10}}{\sqrt{f_{1+}f_{+1}f_{0+}f_{+0}}} \\
&=\frac{ s(A,B)-s(A)s(B) }{ \sqrt{ s(A)s(B)(1-s(A))(1-s(B)) } }
\end{align}$$

### IS measure
$$\begin{align}
IS(A,B)&=\sqrt{I(A,B)\cdot s(A,B)}=\frac{s(A,B)}{\sqrt{s(A)s(B)}}=\frac{f_{11}}{\sqrt{f_{1+}f_{+1}}} \\
&=\sqrt{conf(A\rightarrow B)conf(B\rightarrow A)}
\end{align}$$

## Properties
### Inversion
If a measure is invariant under the inversion opertion, then its value for the vector pair $\{\bar{A},\bar{B}\}$ should be identical to its value for $\{A,B\}$. That is to say, an objective measure $M$ is invariant under the inversion operation if its value remains the same when exchanging the frequency counts $f_{11}$ with $f_{00}$ and $f_{10}$ with $f_{01}$.

### Scaling
A measure that is invariant to scaling does not change its value after any row or column scaling operation.

### Null Addition
An objective measure $M$ is invariant under the null addition operation if it is not aﬀected by increasing $f_{00}$, while all other frequencies in the contingency table stay the same.

### Asymmetric
Asymmetric measures are more suitable for analyzing association rules, since the items in a rule do have a speciﬁc order.