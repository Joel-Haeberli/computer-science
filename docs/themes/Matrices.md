tags: #msc #jmsc #linalg #math #basics #matrices

# Matrices

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Definition

A matrix is a scheme of the form:

$$
A = 
\begin{pmatrix}
a_{11} & \dots & a_{1n} \\
a_{21} & \dots & a_{2n} \\
\vdots & & \vdots\\
a_{m1} & \dots & a_{mn} \\
\end{pmatrix}
, a_{ij} \in \mathbb{R}, i = 1,...,m, j = 1,...,n
$$
If $m = n$ we call it a *quadratic matrix*. When each cell of the matrix is zero but the main diagonal, we call the matrix a *diagonal matrix*. 

### Identity Matrix

If the diagonal is a diagonal matrix __and__ each cell of the diagonal is $1$, then we have the *identity matrix* which is also written like:

$$
I_n = 
\begin{pmatrix}
1 & 0 & ... & 0 & 0\\
0 & 1 & 0 & ... & 0\\
\vdots & & & & \vdots\\
0 & 0 & ... & 0 & 1\\
\end{pmatrix}
$$

## Transposition

The transposed matrix $A^T$ of a matrix $A$ is defined as:

$$
A = 
\begin{pmatrix}
a_{11} & \dots & a_{1n} \\
a_{21} & \dots & a_{2n} \\
\vdots & & \vdots\\
a_{m1} & \dots & a_{mn} \\
\end{pmatrix}
, a_{ij} \in \mathbb{R}, i = 1,...,m, j = 1,...,n
$$

$$
A^T = 
\begin{pmatrix}
a_{11} & \dots & a_{m1} \\
a_{12} & \dots & a_{m2} \\
\vdots & & \vdots\\
a_{1n} & \dots & a_{nm} \\
\end{pmatrix}
, a_{ij} \in \mathbb{R}, i = 1,...,m, j = 1,...,n
$$

The transposition of the matrix is like placing a mirror on the main diagonal of the matrix and exchange the elements along the mirrored perspective.

## Matrix operations

Let $A, B, C \in \mathbb{R}^{m \times n}$ be three matrices and $\lambda, \eta \in \mathbb{R}$ then:

$$
\begin{aligned}
A + B = B + A &&& \text{Commutative Law}\\
A + (B + C) = (A + B) + C &&& \text{Associative Law}\\
A + \mathbb{0} = \mathbb{0} + A = A &&& \text{Addition with Zero Matrix}\\
A - A = \mathbb{0} &&& \\
\lambda(A + B) = \lambda A + \lambda B &&& \text{Distributive Law I}\\
(\lambda + \eta) A = \lambda A + \eta A &&& \text{Distributive Law II}\\
\lambda \eta A = \lambda (\eta A) &&& \\
\end{aligned}
$$

### Addition

The addition is simple and is done adding up the cells with the same indices. This also means you can only add matrices to one another if they have the same dimensions.

Addition of two matrices $A = (a_{ij}), B = (b_{ij}) \in \mathbb{R}^{m \times n}$ is defined as:

$$
A + B = 
\begin{pmatrix}
a_{11} + b_{11} & ... & a_{1n} + b_{1n} \\
a_{21} + b_{21} & ... & a_{2n} + b_{2n} \\
\vdots & & \vdots\\
a_{m1} + b_{m1} & ... & a_{mn} + b_{mn} \\
\end{pmatrix}
$$

### Multiplication

#### With a scalar $\lambda \in \mathbb{R}$

When calculating the product of a scalar and a matrix, the product of each cell and the scalar is calculated:

$$
\lambda A = 
\begin{pmatrix}
\lambda a_{11} & ... & \lambda a_{1n} \\
\vdots & & \vdots \\
\lambda a_{m1} & ... & \lambda a_{mn}
\end{pmatrix}
$$

#### With a different Matrix $B$

You can only derive a product of to matrices $A, B$ if the satisfy:

$$
A \in \mathbb{R}^{m \times n}, B \in \mathbb{R}^{n \times t}, m,n,t \in \mathbb{N} 
$$

The produc of the matrices $C = AB, (c_{ij} \in \mathbb{R}^{m \times t}$ can be created as follows:

$$
c_{ij} = a_{i1} b_{1j} + a_{i2} b_{2j} + ... + a_{in} b_{nj} = \sum_{k=1}^{n} a_{ik} b_{kj}
$$
This means to calculate the cell $c_{ij}$ we calculate the [[Vectors#Scalar Product / Dot Product|scalar product]] of the $i$-th row of $A$ with the $j$-th column of $B$.

## Inverse Matrix

A matrix $A$ is called *invertible* or *regular* if there exists a matrix $B$ for which holds:

$$
BA = I \text{ and } AB = I
$$

$I$ is the [[#Identity Matrix]]. $B$ is called to inverse (matrix) to $A$ and is denoted as $A^{-1}$

## Determinant

The determinant $det(A)$ of a *quadratic* matrix $A \in \mathbb{R}^{n \times n}$ can tell us if a linear equation system has a solution or not. 

### Definition

The general definition of the determinant of a matrix is given by:

$$
det(A) = \sum_{j=1}^n (-1)^{i+j} a_{ij} det(A_{i,j}) 
$$

We see that the definition is recursive. For this reason we define the base cases $n=2$

### $n=2$

$$
det(A) = 
\begin{vmatrix}
a_{11} a_{12}\\
a_{21} a_{22}
\end{vmatrix}
= a_{11}a_{22} - a_{12}a_{21}
$$

So the determinant is defined as the product of the main diagonal minus the product of all other diagonals.

For quadratic matrices $A, B \in \mathbb{R}^{n \times n}$ holds:

$$
det(AB) = det(A) det(B)
$$

## Trace

The trace of a matrix is the sum of all elements on the main diagonal of a quadratic matrix $A$:

$$
tr(A) = \sum_{i=1}^n a_{ii}, A \in \mathbb{R}^{n \times n}
$$
The trace might be denoted as: $tr(A) = trace(A) = spur(A)$

## Linear Equation Systems

With the elimination process of Gauss we can solve linear equation systems by hand.


---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]