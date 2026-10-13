tags: #msc #jmsc #ml #generative #gen-ai #generative-learning #gda

# Gaussian Discriminant Analysis

links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Definition

The Gaussian Discriminant Analysis (GDA) is a [[Generative Learning]] algorithm used for classification of continuously distributed targets $y$. The GDA assumes that $P(X | y)$ is a [[Distributions#Multivariate Normal Distribution|multivariate normal distribution]] $\mathcal{N}(\mu, \Sigma)$. GDA is applicable to classification problems with input features $x$ which are continuous valued (and random -> normal distribution). The GDA model is defined as:

$$
\begin{aligned}
y &\sim Bernoulli(\phi), \\
x | y = 0 &\sim \mathcal{N}(\mu_1, \Sigma), \\
x | y = 1 &\sim \mathcal{N}(\mu_2, \Sigma)
\end{aligned}
$$
We see that the model has the four parameters $\phi, \mu_1, \mu_2, \Sigma$ and that the [[Distributions#Bernoulli|Bernoulli distribution]] distributes the two classes. Each class has their own mean ($\mu_1, \mu_2$). The $\Sigma$ being the covariance matrix of both conditional probabilities is not necessary but a simplifying assumption the model makes.

The GDA implies [[Model selection and Regression#Logistic Regression|Logistic Regression]] when deriving the GDA model for $P(y | x)$ and is therefore related to a [[Discriminative Learning]] model.

---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]] 