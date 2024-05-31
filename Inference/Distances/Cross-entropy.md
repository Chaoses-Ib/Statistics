# Cross-entropy
[Wikipedia](https://en.wikipedia.org/wiki/Cross-entropy)

$$H(p,q)=-\sum_{x\in X} p(x) \log{q(x)}$$
where the true probability $p_i$ is the true label, and the given distribution $q_i$ is the predicted value of the current model.

[Intuitively, why is cross entropy a measure of distance of two probability distributions? - Cross Validated](https://stats.stackexchange.com/questions/209107/intuitively-why-is-cross-entropy-a-measure-of-distance-of-two-probability-distr)

## Implementations
- PyTorch: [CrossEntropyLoss](https://pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html), [cross_entropy()](https://pytorch.org/docs/stable/generated/torch.nn.functional.cross_entropy.html)
  
  ```python
  import torch.nn.functional as F

  F.cross_entropy(input, target)
  ```
  - The order of `input` and `target` are different from the math definition.
  - `input` is always normalized with softmax.
  - `target`'s value can be in $[0,1]$ or $[0,C)$. In the latter case, `weight` can be used to specify the probability for each class.

    [Cross Entropy Calculation in PyTorch tutorial - Stack Overflow](https://stackoverflow.com/questions/62161194/cross-entropy-calculation-in-pytorch-tutorial)

  [Cross-Entropy, Negative Log-Likelihood, and All That Jazz | by Remy Lau | Towards Data Science](https://towardsdatascience.com/cross-entropy-negative-log-likelihood-and-all-that-jazz-47a95bd2e81)
  - [NLLLoss](https://pytorch.org/docs/stable/generated/torch.nn.NLLLoss.html#torch.nn.NLLLoss) (negative log likelihood loss) does not apply `log` to `input`.

    [Understanding of Pytorch NLLLOSS - Stack Overflow](https://stackoverflow.com/questions/69325760/understanding-of-pytorch-nllloss)

    [PyTorch LogSoftmax vs Softmax for CrossEntropyLoss - Stack Overflow](https://stackoverflow.com/questions/65192475/pytorch-logsoftmax-vs-softmax-for-crossentropyloss)