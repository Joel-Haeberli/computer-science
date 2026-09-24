tags: #mmlo #modeling #basics

# Modeling Basics

links: [[1200 MMLO MOC]] - [[themes/000 Index|Index]]

---

## Model / Optimization Problem $P$

A model represents a problem with $n$ *[variables](#variable)* influencing its outcome. A model tries to optimize a certain aspect described by the *[objective](#Objective)*. The objective can be subject to certain *[constraints](#Constraints)*. To optimize and solve the model *[solvers](#Solver)* are used. They define how the model is solved and therefore can lead to varying results. The model can also be seen as the Optimization Problem $P$ more mathematically speaking.

### Formal Notation

Models (or optimization problems) are formulated using the following notation:

$$
\begin{aligned}
&\text{min} && z = f(x) \\
&\text{s.t.} && g(x) < 10 \\
&&& h(x) = 0 \\
&&& x \in X \subseteq \mathbb{R}^n
\end{aligned}
$$

This example describes a model which wants to minimize the objective function $f(x)$ which is subject to ($s.t.$) the constraints $g(x) < 10$ and $h(x) = 0$

## Variable

A model has $n$ variables. The variables describe aspects in the system which vary. The model outcomes heavily depend on the variables. If one variable changes, chances are that also the outcome of the model changes.
### Variable Types

The type of the variable $x$ also describes the nature of the variable $x$:

$$
\begin{aligned}
x \in R && \text{continuous variable, quantities}\\
x \in Z && \text{discrete variable, number of units}\\
x \in \{0,1\} && \text{binary variable, yes or no}\\
\end{aligned}
$$

## Objective

The Objective or Objective Function is the function which describes for what variable(s) a certain model shall be optimized. The optimization can be minimizing or maximizing the value of the objective function. A point on the graph of the objective function is associated with exactly one configuration. The objective function is defined as follows: 
$$f: X \subseteq \mathbb{R}^n \to \mathbb{R}$$
Optimization algorithms leverage [properties](Functions.md#properties) of $f$. Therefore it is of interest to know the [properties](Functions.md#properties) of the objective function.

## Constraint

The constraints of the model describe aspects which apply to the model. These constraints describe the environment of the model and can represent boundaries for the solution space. The constraints are important to establish feasible solutions for the model.

### Feasible Region

The constraints of a model together form the **feasible region** $\mathcal{F}$ of the optimization problem $P$:

$$
\mathcal{F} = \{ x \in X \subseteq \mathbb{R}^n | c_i \in C\}, \text{let } C \text{ be the set of all constraints, } i \in \{1,...,|C|\}
$$

#### Bounded Feasible Region

We call the feasible region **bounded** if there exists a constant $M$, that 

$$
\mathcal{F} = \{ x \in \mathbb{R}^n | |x_i| \leq M, \forall i \in \{1,...,n\}
$$

An empty feasible region $\mathcal{F} = \{\}$ indicates, that the problem is infeasible. By convention we write $z = \infty$ 

#### Unbounded Feasible Region 

A feasible region is unbounded if no $M$ as defined [[#Bounded Feasible Region|above]] exists.

In case the feasible region is unbounded it could be that $z = - \infty$

### Activeness

A constraint can be active or inactive depending on the operator used to describe the constraint. 

- An inequality constraint $\leq$ is called **active** in $x^*$, when the **equality $=$ holds**. 
- The inequality constraint is called **inactive** if the constraint holds **strict inequality** $<$. 
- The equality constraint is **active** in $x^*$, if it is satisfied at $x^*$. 

## Solution

A solution to an optimization problem is the assignment of values to all the variables of the problem. A solution can be represented as an $n$-dimensional vector, where each element represents a variable.

The value $x$ of the [[#Objective|objective function]] of a solution is obtainted by evaluating the objective function at $x \to f(x)$.

### Feasability

Any point $x \in \mathbb{R}^n$ is called a **feasible** solution for the problem $P$ if it satisfies all the constraints $C$. Feasible solutions are sometimes also called feasible vectors.

### Optimality

A solution $x^*$ is called optimal to $P$ if it is *feasible* and for $f(x^*)$ holds:

$$
z = f(x^*) \leq f(x), \forall x \in \mathcal{F}
$$

Notice: this is the optimal solution for a problem in which we minimize the objective function. When maximizing the operator would need to be inverted.

### Local Optimal Solution

Defined by [[Functions#Local Extreme|Local Extreme]]

### Global Optimal Solution

Defined by [[Functions#Global Extreme|Global Extreme]]

### Solver

A Solver is a program / calculation which can take the model consisting of an objective and possibly constraints and solve the problem. However, not all models are solvable.

## Transformations



---
links: [[1200 MMLO MOC]] - [[themes/000 Index|Index]]