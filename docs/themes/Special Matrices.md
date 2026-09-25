tags: #msc #jmsc #linalg #math

# Special Matrices

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Jacobian Matrix

The Jacobian matrix of a vector-valued function $f: \mathbb{R}^m \to \mathbb{R}^n$ holds all the first-order [[Derivatives#Partial Derivative|partial derivatives]] as its elements. A vector-valued function is also called a [[Functions#Multivariable Functions|multivariable function]].

Given a [[Functions#Multivariable Functions|multivariable function]] $f: \mathbb{R}^m \to \mathbb{R}^n$, we can write
$$
f(x_1, x_2, ... , x_n) = (f_1, f_2, ..., f_m)
$$
From this the definition, the Jacobian matrix definition follows:

$$
J(x) = 
\begin{pmatrix}
\frac{\partial f_1}{\partial x_1} & \frac{\partial f_1}{\partial x_2} & ... & \frac{\partial f_1}{\partial x_n} \\
\frac{\partial f_2}{\partial x_1} & \frac{\partial f_2}{\partial x_2} & ... & \frac{\partial f_2}{\partial x_n} \\
\vdots &  &  & \vdots \\
\frac{\partial f_m}{\partial x_1} & \frac{\partial f_m}{\partial x_2} & ... & \frac{\partial f_m}{\partial x_n} \\
\end{pmatrix}
$$

Notice that $x$ in the matrix is not a scalar but a vector $\vec{x}$ of all the inputs with $len(\vec{a}) = n$, $n$ the number of inputs to $f$. Calculating a Jacobian matrix over an arbitrary function $f$ with $n$ variables is "simply" calculating all required first-order derivatives and arranging them correctly into the matrix.

## Hessian Matrix

The Hessian matrix (also referred to as "the Hessian") holds all the second-order [[Derivatives#Partial Derivative|partial derivatives]] of a function $f$ as its elements. The dimension of a Hessian is defined by the number of input parameters $n$ of the function $f$. A function $f: \mathbb{R}^4 \to \mathbb{R}$ with $4$ inputs will lead to a Hessian matrix $H \in \mathbb{R}^{4 \times 4}$. For a function with $n$ inputs this leads to $H \in \mathbb{R}^{n \times n}$. The Hessian is always a squared matrix. Why follows directly from its definition:

$$
H_f(x) = 
\begin{pmatrix}
\frac{\partial^{2} f}{\partial x_1^2} & \frac{\partial^{2} f}{\partial x_1 \partial x_2} & ... & \frac{\partial^{2} f}{\partial x_1 \partial x_n} \\

\frac{\partial^{2} f}{\partial x_2 \partial x_1} & \frac{\partial^{2} f}{\partial x_2^2} & ... & \frac{\partial^{2} f}{\partial x_2 \partial x_n} \\

\vdots &  &  & \vdots \\

\frac{\partial^{2} f}{\partial x_n \partial x_1} & \frac{\partial^{2} f}{\partial x_n \partial x_2} & ... & \frac{\partial^{2} f}{\partial x_n^2} \\
\end{pmatrix}
$$

Notice that $x$ in the matrix is not a scalar but a vector $\vec{x}$ of all the inputs with $len(\vec{a}) = n$, $n$ the number of inputs to $f$. Calculating a Hessian matrix over an arbitrary function $f$ with $n$ variables is "simply" calculating all required second-order derivatives and arranging them correctly into the matrix. The Hessian $H$ is in the dimension $n \times n$ because the second-order derivative is created over all possible input pairs as depicted above.


---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]