tags: #msc #jmsc #ml #generative #gen-ai #generative-learning #naive-bayes

# Naive Bayes

links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Naive Bayes

As also described in the [[Probabilities#Naive Bayes|math section about probabilities]], Naive Bayes is a special case of the Bayes rule, where we assume that any $x_i, x_j \in X,\ with , i,j = 1,...,n,\ and\ i \neq j,\ and\ n = |X|$ are conditionally independent.

This gives us for inputs $X$ and $Y$ the following probability which we can use to classify inputs in a generative model:

$$
P(y=1|x_i) = \frac{P(y=1)\Pi_i{P(x_i | y = 1)}}{\Pi_k P(y=k) \Pi_iP(x_i|y=k)}, x_i \in X, k \in Y
$$

## Laplace Smoothing

Laplace Smoothing is used for the case that a model receives an input it does not know from its training. This will lead to the prediction $0$ or in the worse case even to a division by zero which is not defined. Laplace Smoothing therefore introduces a summand to the numerator and denominator of a Naive Bayes model $f_X(x)$:

$$
f_X(x) = \frac{g(x) + 1}{h(x) + k}, k = \text{number of classes in Y}
$$

So for a Naive Bayes model with Laplace Smoothing applied this leads to:

$$
P(y=1|X) = \frac{P(y=1)\Pi_i{P(x_i | y = 1)+1}}{\Pi_k P(y=c) \Pi_iP(x_i|y=c)+k}, x_i \in X, c \in Y, k = \text{number of classes in Y}
$$

This makes sure the denominator is never zero and the entire quotient is never zero. So every unseen input is possible with a probability higher than 0.

---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]