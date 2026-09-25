tags: #msc #jmsc #analysis #math #basics 

# Functions

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Properties 

Functions can have several properties. Properties describe characteristics of a function. These characteristics allow the creation of groups of functions. These groups then allows us to select feasible functions to solve problems in an easier way.

### Monotonicity

A function $f: \mathbb{R} \to \mathbb{R}$ is called monotonic if:

$$
\begin{aligned}
\text{monotonically growing} &&& f(x) \leq f(x+1), x \in \mathbb{N} \\
\text{strict monotonically growing} &&& f(x) < f(x+1), x \in \mathbb{N} \\
\text{monotonically decreasing} &&& f(x) \geq f(x+1), x \in \mathbb{N} \\
\text{strict monotonically decreasing} &&& f(x) > f(x+1), x \in \mathbb{N} \\
\end{aligned}
$$

### Linearity

#### Formal Definition

A function $f: \mathbb{R}^n \to \mathbb{R}$ is **linear** if it satisfies:

$$
f(x) = \sum_{i = 1}^n c_i x_i
$$

Interesting about **linear functions** is the fact that they per definition are:

- [continuous](#Continuity)
- [convex](#convexity)
- [concave](#concavity)
- [differential](#differentiability)

### Continuity

#### Formal Definition

A function $f: X \subseteq \mathbb{R}^n \to \mathbb{R}$ is *continuous* if and only if:

$$
\lim_{x \to x_0} f(x) = f(x_0), \forall x_0 \in X
$$

### Affinity

#### Formal Definition

A function $f: \mathbb{R}^n \to \mathbb{R}$ is **affine** when it is *[linear](#linearity)*  and it can be written like:

$$
f(x) = \sum_{i = 1}^n c_i x_i + d
$$

### Differentiability

#### Formal Definition

To understand the formal definition of the differentiability, one must understand some rules and aspects of [[Derivatives|derivations]]. 

That said, the differentiability of a function $f: \mathbb{R}^n \to \mathbb{R}$ is given, when $f$ is **[continuous](#continuity)** and the **directional derivative** exists for any $d \in \mathbb{R}^n$.

### Convexity

#### Formal Definition

A function $f: \mathbb{R}^n \to \mathbb{R}$ is *convex* if for any $x, y \in \mathbb{R}^n$ and any $\lambda \in [0,1]$ we have:
$$
f(\lambda x + (1-\lambda)y) \leq \lambda f(x) + (1-\lambda)f(y)
$$

A function $f: \mathbb{R}^n \to \mathbb{R}$ is ***strictly** convex* if for all $x, y \in \mathbb{R}^n, x \neq y$ and for all $\lambda \in (0,1)$ we have:
$$
f(\lambda x + (1-\lambda)y) < \lambda f(x) + (1-\lambda)f(y)
$$
The difference of the two definitions is just the operator. A *strictly* convex function satisfies the $<$ operator, while a convex function satisifies the $\leq$ operator.

### Concavity

#### Formal Definition

A function $f: \mathbb{R}^n \to \mathbb{R}$ is concave if $-f$ is a convex function, when for all $x, y \in \mathbb{R}^n$ and for any $\lambda \in [0,1]$ we have (consider the operator):
$$
f(\lambda x + (1-\lambda)y) \geq \lambda f(x) + (1-\lambda)f(y)
$$

## Extreme values

A function which is [[#Differentiability|differential]] can have *no*, *local* or *global* extreme values. Extreme values can describe a local or a global extreme and can represent a maximum or a minimum. An extreme value (either local or global, maximum or minimum) can be found using the first derivative $f'$ of a function and searching for a $x_0$ for which holds:
$$
f'(x_0) = 0
$$
This means the slope is 0 which indicates, that the function is at a "turning" point indicating an extreme value. This fact doesn't say if the extreme value is a local or a global extreme nor if the extreme value is a maximum or minimum.

### Local Extreme

Given a function $f: ]a,b[ \in \mathbb{R}$ a point $(x_0, f(x_0))$ is called a local extreme (local maximum or local minimum) if there exists an $\epsilon > 0$ such that

$$
\begin{aligned}
\text{local maximum} &&& f(x_0) \geq f(x), \forall x \in ]x_0 - \epsilon, x_0 + \epsilon [ \cap [a,b] \\
\text{local minimum} &&& f(x_0) \leq f(x), \forall x \in ]x_0 - \epsilon, x_0 + \epsilon [ \cap [a,b]
\end{aligned}
$$

### Global Extreme

A function $f: ]a,b[ \to \mathbb{R}$ reaches her global extreme $x_0$ if the following holds:

$$
\begin{aligned}
\text{global maximum} &&& f(x_0) \geq f(x), \forall x \in [a,b] \\
\text{global minimum} &&& f(x_0) \leq f(x), \forall x \in [a,b]
\end{aligned}
$$

## Convergence / Limit

To understand what a limit $\lim_{x \to c} f(x)$ of a function is, we need to know the convergence property of a function. The convergence of a function is defined as:

$$
|f(x) - a| < \epsilon, \text{for all x} \geq \mathbb{N}
$$
The coefficient $a$ is called the limit / limes of the function $f$ and is written as:

$$
\lim_{x \to \infty} f(x) = a
$$
Only functions which converge have a limit. All others do not.

A function which does *not have a limit* and therefore does not converge, we say the function diverges and is therefore **divergent**.


---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]