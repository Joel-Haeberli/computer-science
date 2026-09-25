tags: #msc #jmsc #analysis #math #basics 

# Derivatives

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Derivatives

### Definition

The derivation of a function $f: D \to \mathbb{R}$ is defined as:

$$
f'(x_0)  = \frac{df}{dx}(x) = \frac{d}{dx}f(x) = \lim_{h \to 0} \frac{f(x_0 + h) - f(x_0)}{h}, \in \mathbb{R}
$$

When the [[Functions#Convergence / Limit|limit]] for $f$ exists, $f'(x_0)$ is called the derivation or differential quotient of $f$ for $x_0$. 

A [[Functions|function]] $f$ is called [[Functions#Differentiability|differentiable]] in $D$, if for every $x \in \mathbb{D}$  $f$ is differentiable.

For the Leibniz [[Notations|notation]], read "Derivation of $f$, in respect to $x$"

### Rules of derivation

Let $f,g: D \to \mathbb{R}$ be [[Functions#Differentiability|differentiable]] for $x \in D$ and $\lambda \in \mathbb{R}$, then also the following functions are differentiable:

$$
\begin{gather*}
f + g \\
\lambda f \\ 
f \cdot g \\
\text{ and if } g(x) \neq 0, \text{then also } \frac{f}{g}
\end{gather*}
$$

For the derivations of $f,g$ the following rules apply:

#### [[Functions#Linearity|Linearity]] of a derivation

$$
\begin{gather*}
(f+g)'(x) = f(x) + g(x) \\
(\lambda f )' (x) = \lambda f ' (x)
\end{gather*}
$$

#### Product Rule

$$
(f \cdot g)'(x) = f'(x)g(x) + f(x)g'(x) \\
$$

#### Quotient rule

$$
(\frac{f}{g})'(x) = \frac{f'(x)g(x) + f(x)g'(x)}{g(x)^2}
$$

#### Chain Rule

For the two functions $f: D \to \mathbb{R}$ and $g: E \to \mathbb{R}$ and the conditions $f(D) \subset E$ , $f$ differentiable in $x \in D$ and $g$ differentiable in $f(x) \in E$ we say the composition $g \circ f = g(f(x))$  is also differentiable in  $x$ and

$$
\begin{gather*}
(g \circ f)'(x) = g'(f(x))f'(x)\\
=\\
g(y)' = g'(y)f'(x), y = f(x)
\end{gather*}
$$

#### Rule of de l'Hospital

For the two differentiable functions $f,g: ]a,b[ \to \mathbb{R}$ and $g'(x) \neq 0$ as well as $x \in ]a,b[$  and in case of one of the two conditions

$$
\begin{gather}
i.) \lim_{x \to a+} f(x) = \lim_{x \to a+} g(x) = 0\\
ii.) \lim_{x \to a+} f(x) = \lim_{x \to a+} g(x) = \infty
\end{gather}
$$

, the following holds

$$
\lim_{x \to a+} \frac{f(x)}{g(x)} = \lim_{x \to a+} \frac{f'(x)}{g'(x)}
$$

#### Derivation of the inverse

If an inverse function $f^{-1}$ exists and inverts $f$ then the derivation of $f^{-1}$ is defined as

$$
(f^{-1})'(f(x)) = \frac{1}{f'(x)} = \frac{1}{f'(f^{-1}(f(x)))} 
$$

### Frequently used derivatives

Some well known derivatives:

$$
\begin{gather*}
exp'(x) = exp(x) \\
sin'(x) = cos(x) \\
tan'(x) = \frac{1}{cos^2(x)} \\
ln'(x) = \frac{1}{x} \\
\end{gather*}
$$

## Partial Derivative



## Directional Derivative



## Finding Derivatives

example

---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]