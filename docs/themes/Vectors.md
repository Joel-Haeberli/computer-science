tags: #msc #jmsc #linalg #math #basics #vectors

# Vectors

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Basic Operations

### Addition

$$
\vec{a} + \vec{b} = 
\begin{pmatrix}
a_1 + b_1\\
a_2 + b_2\\
\vdots \\
a_n + b_n
\end{pmatrix}, n \in \mathbb{N}
$$
$$
\lambda \vec{a} = 
\begin{pmatrix}
\lambda a_1\\
\lambda a_2\\
\vdots \\
\lambda a_n
\end{pmatrix}
, \lambda \in \mathbb{R}, n \in \mathbb{N}
$$

For the operation of addition the following rules apply:

$$
\begin{aligned}
\vec{a} + \vec{b} = \vec{b} + \vec{a} &&& \text{Commutative Law}\\
\vec{a} + (\vec{b} + \vec{c}) = (\vec{a} + \vec{b}) + \vec{c} &&& \text{Associative Law}\\
\vec{a} + \vec{0} = \vec{0} + \vec{a} = \vec{a} &&& \text{Zero Vector}\\
\vec{a} + (-\vec{a}) = \vec{0} &&& \text{Opposite Vector}\\
\lambda (\vec{a} + \vec{b}) = \lambda \vec{a} + \lambda \vec{b} &&& \text{Distributive Law I}\\
(\lambda + \eta)\vec{a} = \lambda \vec{a} + \eta \vec{a} &&& \text{Distributive Law II}\\
(\lambda \eta)\vec{a} = \lambda (\eta \vec{a})
\end{aligned}
$$

### Dot Product

$$
\begin{aligned}
\vec{a} \cdot \vec{b} = \vec{b} \cdot \vec{a} &&& \text{Commutative Law}\\
\vec{a} \cdot (\vec{b} + \vec{c}) = \vec{a} \cdot \vec{b} + \vec{a} \cdot \vec{c} &&& \text{Distributive Law}\\
\lambda \vec{a} \cdot \eta \vec{b} = \lambda \eta (\vec{a} \cdot \vec{b}), \text{for all } \lambda, \eta \in \mathbb{R} \\
\vec{a} \cdot \vec{a} > 0 \text{ and } \vec{a} \cdot \vec{a} \Leftrightarrow \vec{a} = \vec{0}
\end{aligned}
$$

## Magnitude / Norm / Length

$\|\mathbf{\vec{a}}\| := \sqrt{\sum_{i=1}^{n} a_i} = \sqrt{a_1^2 + a_2^2 +\ ... + a_n^2}$ 

## Unit Vector

A vector $\vec{a}$ is called a Unit Vector, when $\vec{u} = \frac{\vec{a}}{\|\mathbf{\vec{a}}\|}$ and $\|\mathbf{\vec{u}}\| = 1$
Each coordinate system can be created using Unit Vectors for all "directions". For Example $\mathbb{R}^3$ can be constructed with the three unit vectors $(1,0,0)^T, (0,1,0)^T, (0,0,1)^T$. These vectors are also called the Standard Basis.

## Linear Depdendency

Linear dependency or independency describes the position of vectors leading to the dependent or independent vector.
### Linearly Dependent Vectors

$\vec{d} = a\vec{v} +b\vec{w}$

Linear dependent vectors allow the formation of a vector in the same direction by combining them.
### Linearly Independent Vectors

$\vec{d} \neq a\vec{v} +b\vec{w}$

Linear independent vectors do not allow the formation of a vector in the same direction by combining them.

---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]