tags: #msc #jmsc #linalg #math #probabilistic #proba #distribution

# Distributions

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## General

Each distribution is a [[Random Variables#Measure of Probability|mesaure of probability or a distribution of probability]]. The general definition of a **distribution functions** is

$$
\begin{aligned}
F_X : &&&\mathbb{R} \to [0,1]\\
&&&a \to F_X(a) = \mathbb{P}(X \leq a) := \mathbb{P}(\{\omega \in \Omega : X(\omega) \leq a\})
\end{aligned}
$$

### Discrete Distributions

Each **discrete** distribution has a weight function, which is also called the discrete density (de:diskrete Dichte) of $X$ and is defined as

$$
\begin{aligned}
f_X : &&&\mathbb{R} \to [0,1]\\
&&&a \to f_X(a) = \mathbb{P}(X = a) := \mathbb{P}(\{\omega \in \Omega : X(\omega) = a\})
\end{aligned}
$$

A **continuous** distribution on the other hand must have a positive function $f_X : \mathbb{R} \to [0, \infty[$ for which

$$
\begin{aligned}
F_X(a) = \int_{- \infty}^a f_X(x)dx, a \in \mathbb{R} \\
\int_{- \infty}^\infty f_X(x)dx = 1
\end{aligned}
$$
$f_X$ is called the density of $X$, $F_X$ is the distribution function
### Misc

An interesting fact is that thanks to 

$$
\{X \leq a\} = \biguplus_{x \in S, x \leq a} \{X = x\}
$$

$\biguplus$ means the disjoint union. This makes sense since the probabilities of an event $x_1 \neq x_2$ sum up and are disjoint when we want to calculate $\mathbb{P}(X = x_1 \lor X = x_2)$. Given this fact we can find the following equivalence

$$
F_X(a) = \mathbb{P}(X \leq a) = \sum_{x \in S, x\leq a} f_X(x)
$$
A distribution function can either be discretely distributed or continuously. Discrete distributions can be used to model classification tasks where an event is either in one or another class or domain and the set of all possible events is bounded or at least can be counted towards infinity according to a rule, while continuous distributions allow us to model probabilities of more continuous problems and the events are endless and underlie no strict rule for elements when counting towards infinity.

## Discrete Random Variables

### Uniform

The uniform distribution can be used on discrete and continuous problems. The definition varies a little bit.
#### Definition 

$$
\mathbb{P}(X = x_k) = \frac{1}{n}, k = 1,...,n 
$$

#### Metrics

##### $\mathbb{E}[X]$

$$
\mathbb{E}[X] = \frac{x_1 + ... + x_n}{n}
$$

##### $Var(X)$

$$
Var(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = \frac{1}{n}\sum_{k=1}^{n}x_k^2-(\frac{1}{n} \sum_{k=1}^n x_k)^2
$$

### Bernoulli

#### Definition $X \sim Ber(p)$

$X$ is a Bernoulli distribution if with a parameter $p \in [0,1]$ holds:

$$
\begin{aligned}
&&&\mathbb{P}(X = 1) = p\\
&&&\mathbb{P}(X = 0) = (1-p)
\end{aligned}
$$

#### Metrics

##### $\mathbb{E}[X]$

$$
\mathbb{E}[X] = p
$$

##### $Var(X)$

$$
Var(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = p - p^2 = p(1-p)
$$

### Binomial

#### Definition $X \sim Bin(n,p)$

$$
\mathbb{P}(X = k) = \begin{pmatrix} n \\ k \end{pmatrix} p^k (1-p)^{n-k}, k = 0,1,...,n
$$

#### Metrics

##### $\mathbb{E}[X]$

$$
\mathbb{E}[X] = np
$$

##### $Var(X)$

$$
Var(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = np(1-p)
$$

### Geometric
#### Definition $X \sim Geom(p)$

$$
\mathbb{P}(X = k) = (1-p)^{k-1}p, k = 1,2,...
$$

#### Metrics

##### $\mathbb{E}[X]$

$\mathbb{E}[X] = \frac{1}{p}$

##### $Var(X)$

$Var(X) = \frac{1-p}{p^2}$

### Poisson
#### Definition $X \sim Poi(\lambda)$

$$
\mathbb{P}(X = k) = \frac{\lambda^k}{k!}e^{-\lambda}, k = 0,1,2,...
$$

#### Metrics

##### $\mathbb{E}[X]$

$\mathbb{E}[X] = \lambda$

##### $Var(X)$

$Var(X) = \lambda$

## Continuous Random Variables

### Uniform
#### Definition 

$$
\mathbb{P}(X = x_k) =
$$

#### Metrics

##### $\mathbb{E}[X]$

##### $Var(X)$

### Exponential
#### Definition 

$$
\mathbb{P}(X = x_k) =
$$

#### Metrics

##### $\mathbb{E}[X]$

##### $Var(X)$

### Normal

The normal distribution is also often called the Gauss-distribution
#### Definition $X \sim \mathcal{N}(\mu, \sigma^2)$

$$
f_X(x) = \frac{1}{\sigma \sqrt{2 \pi}}e^{\frac{(x-\mu)^2}{2 \sigma^2}}
$$
Reminding you of the [[#General|definition of a continuous distribution]]. The $\mu$ shifts the middle of the curve on the x axis, while $\sigma^2$ reduces or increases the maximum height of the curve (flattens the curve or makes it peakier). $\mu$ is also called the *mean* and $\sigma^2$ is called the covariance. 

When $\mu = 0$ and $\sigma^2 = 1$, then the distribution $\mathcal{N}(0, 1)$ is also called the standard normal distribution.

#### Metrics

##### $\mathbb{E}[X]$

$\mathbb{E}[X] = \mu$

##### $Var(X)$

$Var(X) = \sigma^2$


---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]