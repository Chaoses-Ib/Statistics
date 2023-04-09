# Itemset and Association Rule
Let $I=\{x_1,x_2,...,x_m\}$ be a set of elements called items. A set $X\subset I$ is called an *itemset*. We donote by $I^{(k)}$ the set of all k-itemsets, that is, subsets of $I$ with size $k$.

Let $T=\{t_1,t_2,...,t_n\}$ be another set of elements called *transaction identifiers* or *tids*. A *trascation* is a tuple of the form $<t, X>$, where $t\in T$ is a unique tid, and $X$ is an itemset. We refer to a trascation by its identifier $t$.

## Data representation
### Binary database
$t$ | A | B | C
--- | --- | --- | ---
1 | 1 | 1 | 0
2 | 0 | 1 | 1
3 | 1 | 1 | 1

### Transaction database
$t$ | $i(t)$
--- | ---
1 | AB
2 | BC
3 | ABC

$i(T)$ is the set of items that are common to all the trasactions in the tidset $T$:

$$\begin{align}
i(T)&=\{x|\forall t \in T, t\ contains\ x\} \\
&=\{x|\forall t \in T, t \in t(x)\}
\end{align}$$

### Vertical databse
$t(A)$ | $t(B)$ | $t(C)$
--- | --- | ---
 | 1 | 1 | 2
 | 3 | 2 | 3
 |   | 3 | 

$t(X)$ is the set of tids that contain all the items in the itemset $X$:

$$\begin{align}
t(X) &=\{t|t\in T \land t\ contains\ X\} \\
&=\{t|t\in T \land <t,i(t)> \in D\}
\end{align}$$

## Support and frequent itemsets
The *support* of an itemset $X$ in a dataset $D$ is the number of transactions in $D$ that contain $X$:

$$sup(X,D)=|t(X)|$$

The *relative support* of $X$ is the fraction of transactions that contain $X$:

$$rsup(X,d)=\frac{sup(X,D)}{|D|}$$

It is an estimate of the *joint porbability* of the items comprising $X$.

An itemset $X$ is said to be *frequent* in $D$ if $sup(X,D)\ge minsup$, where *minsup* is a user defined *minimum support threshold*. If *minsup* is spcified as a fraction, then we assume that relative support is implied. We use the set $F$ to denote the set of all frequent intemsets, and $F^{(k)}$ to donote the set of frequent $k$-itemsets.

## Association rules
An association rule is an expression $X\xrightarrow{S,C} Y$, where $X$ and $Y$ are disjoint itemsets. Let the itemset $X\cup Y$ be denoted as $XY$.

The support of the rule is the number of transactions in which both $X$ and $Y$ co-occur as subsets:

$$s=sup(X\rightarrow Y)=|t(XY)|=sup(XY)$$

The relative support of the rule is defined as the fraction of transactions where $X$ and $Y$ co-occur, and it provides an estimate of the joint probability of $X$ and $Y$:

$$rsup(X\rightarrow Y)=\frac{sup(XY)}{|D|}=P(X\land Y)$$

The confidence of a rule is the conditional probablity that a transaction contains $Y$ given that it contains $X$:

$$c=conf(X\rightarrow Y)=P(Y|X)=\frac{P(X\land Y)}{P(X)}=\frac{sup(XY)}{sup(X)}$$

A rule is *frequent* if the itemset $XY$ is frequent, that is, $sup(XY)\ge minsup$. A ruile is *strong* if $conf\ge minconf$, where $minconf$ is a user-specified minimum confidence threshold.

## Itemset and Rule Mining
Given a binary database $D$ and a user defined minimum support threshold $minsup$, the task of frequent itemset mining is to enumerate all itemsets that are frequent, i.e., those that have support at least $minsup$.

Next, given the set of frequent itemsets $F$ and a minimum confidence value $minconf$, the association rule mining task is to find all frequent and strong rules.