tags: #msc #jmsc #linalg #math #probabilistic #proba #distribution

# Random Variables

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Measure of Probability

The function $\mathbb{P}: \mathcal{A} \to \mathbb{R}$ on $(\Omega, \mathcal{A})$ is called a *measure of probability* or *distribution of probability* if:

$$
\begin{aligned}
A \in \mathcal{A} \text{ is } 0 \leq P(A) \leq 1\\
\\
\mathbb{P}(\Omega) = 1\\
\\
\text{For } A_i \in \mathcal{A} \text{ and } A_i \cap A_j = \emptyset, i \neq j \text{ is } \mathbb{P}(\bigcup_{i = 1}^{\infty} A_i) = \sum_{i = 1}^{\infty} \mathbb{P} (A_i)
\end{aligned}
$$

## Variable $X$

The random variable $X$ is defined as:

$$
\begin{aligned}
X:\ & \Omega \to S \\
& \omega \to X(\omega)
\end{aligned}
$$

## Expected Value $\mathbb{E}[X]$

The expected value $\mathbb{E}[X]$ of a random variable $X$ is defined:

$$
\mathbb{E}[X] := \sum_{a \in S} a \cdot \mathbb{P}(X = a) = \sum_{a \in S} a \cdot f_X(a)
$$

The expected value describes the most likely value when getting the next value from a number source of the random variable $X$.

## Variance $Var[X]$

The variance $Var[X]$ of a random variable $X$ is defined as:

$$
Var(X) := \mathbb{E}[(X - \mathbb{E}[X])^2] = \mathbb{E}[X^2] - \mathbb{E}[X]^2
$$
The variance describes the mean squared deviation from the expected value of a random variable $X$.

## Covariance $cov(X, Y)$

The covariance of two random variables is defined as:

$$
cov(X, Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])]
$$

The covariance describes how similar the variance of two random variables $X$ and $Y$ is.

## Bayes's Rule

The rule of Bayes allows to easily calculate the probability of a partition $B_j \in \Omega$ given an event $A \in \mathcal{A}$:

$$
\mathbb{P} (B_j | A) = \frac{\mathbb{P}(B_j)\mathbb{P}(A | B_j)}{\mathbb{P}(A)}
$$

## Dependency of variables

Random variables $X_i, i = 1,...,n$ are independend if:

$$
\mathbb{P}(X_1 = s_1, X_2 = s_2, ..., X_n = s_n) = \mathbb{P}(X_1 = s_1) \cdot \mathbb{P}(X_2 = s_2) \cdot ... \cdot \mathbb{P}(X_n = s_n) 
$$

$S_i$ be the set of values for which $f(X_i) = S_i$

---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]