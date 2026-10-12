tags: #msc #jmsc #ml #generative #gen-ai #generative-learning

# Generative Learning

links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Definition

Generative models are defined by any joint probability distribution:

$$
P(X, y) = P(X | y; \theta)
$$

"What is the probability of input $X$, when given a target $y$ under parameters/weights $\theta$?"


The name comes from the fact, that given a desired target $y$ the model can come up with an input $X$. So the model is able to *generate*  - or *predict* - input $X$ given some target value $y$.

A generative model does not only learn $P(X | y)$ but also $P(y)$.

A generative model is more complex than a [[Discriminative Learning]] model, but it is also more powerful. With the [[Probabilities#Bayes rule|Bayes rule]] we can easily simulate a [[Discriminative Learning]] model:

$$
P(y | X) = P(X | y) \cdot \frac{P(y)}{P(X)} = \frac{P(X | y) \cdot P(y)}{P(X)}
$$
BUT: because $P(X | y)$ is harder to model than $P(y | X)$. This justifies the use of [[Discriminative Learning]] models in some cases (especially classification).

Also important to mention (also when it is clear by the structure of the documentation): [[Discriminative Learning]] and [[Generative Learning]] models are both [[Supervised Learning]] models.

---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]