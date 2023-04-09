# Model Overfitting
A phenomenon that a model fits well over the training data but shows poor generalization performance.

## Reasons
- Limited traning size
- High model complexity

## Incorporating model complexity
$$gen.error(m)=train.error(m,D.train)+\alpha \cdot complexity(M)$$

when learning a classification model $m$ that belongs to a certain class of models $M$.

## Minimum Description Length Principle
The overall transimission cost, which is equal to the total length of the message, is:

$$Cost(model,data)=Cost(data|model)+\alpha \cdot Cost(model)$$

where the first term is the number of bits needed to encode the misclassified instances, while the second term is the number of bits required to encode the model.

A good model must have a total description length less than the number of bits required to encode the entire sequence of class labels.