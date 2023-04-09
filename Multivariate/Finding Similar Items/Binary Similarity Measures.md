# Binary Similarity Measures
## Simple matching coefficient
(Rand similarity coefficient)

$$\begin{align}
SMC&=\frac{\text{number of matching attributes}}{\text{number of attributes}} \\
&=\frac{M_{00}+M_{11}}{M_{00}+M_{11}+M_{01}+M_{10}}
\end{align}$$

## Jaccard coefficient
$$\begin{align}
J
&=\frac{M_{11}}{M_{01}+M_{10}+M_{11}} \\
&=\frac{M_{11}}{M_{+1}+M_{1+}-M_{11}} \\
&=\frac{M_{11}}{n-M_{00}}
\end{align}
$$

- Extended Jaccard coefficient (Tanimoto coefficient)