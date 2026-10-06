tags: #msc #jmsc #ml #machinelearning #estimation #optimization #methods

# Principles of Estimation and Optimization Methods

links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## General 

Once a [[Model selection and Regression|model was selected]], the parameters of the models must be estimated and optimizied in order to guarantee the best solution. Therefore it is important which [[#Principles|principles]] are to be applied in the process and which [[#Optimization|optimization]] shall be used. In the end we will receive an [[#Estimation|estimation]] which defines the parameters we will use when running the model.

## Principles and picking loss

*Answers the question*: "What makes a parameter value ***good*** in respect to the conditions given by the problem at hand?"

The principle defines *which* loss / objective we want to optimize. The optimization is the tool we use to find the best estimation. So the principle defines which objective function we use for the problem at hand.

### Least Squares (LS)

Minimizing errors (to be precise: minimize squared errors in respect to some expected value. Stay within a certain threshold)

Principle: Minimizing the error to some expected [[Supervised Learning#Outputs / Targets|target]] $t_x$

[[Supervised Learning#Cost function / Objective|Objective Function]]: We assume minimizing a function representing an error in respect to some expected value is good enough for our estimation. This approach works but does most of the time not give satisfying results (because it is not very accurate). On the other hands it most of the time allows a closed-form solution which is very efficient computing wise.

Definition: $\theta_{LS} = argmin_{\theta}\ \sum_i\ (y_i - f_{\theta}(x_i))$

### Maximum Likelihood (ML)

Maximizing the likelihood -> minimizing the loss (to 100% accuracy) by fitting the problem onto a probabilistic likelihood

Principle: Minimizing a loss / delta to some expected [[Supervised Learning#Outputs / Targets|target]] $t_x$

[[Supervised Learning#Cost function / Objective|Objective Function]]: Some "Likelihood" function (uses a [[Distributions|probability model]]). We first try to find out which [[Distributions|probabilistic distribution]] the data (training data) resembles to. Then we use this distribution and optimize it using an optimization algorithm. Using the a distribution to predict targets, will lead to some error. So in the end ML is just another way to minimize an error. But we do not start at the error, but with a probability model.

Definition: $\theta_{ML} = argmax_{\theta}\ P(\mathcal{Y}\ |\ \theta)$

## Optimization

*Answers the question*: "How do we find the ***best estimate*** for a models parameters?"

### Closed Form

Any closed-form problem can be used as an optimization tool. When a closed-form solution exists for a problem, this closed-form is the optimization of this problem. When a closed-form solution exists, we can write an *explicit formula* solving the problem which can be directly evaluated (no algorithm needed, just a mathematical function taking an input and calculating an output / result). Linear problems can often be converted to a closed-form solution using [[Model selection and Regression#Linear Regression|linear regression]]. This kind of optimization is often not leading to the best results but is the starting point for other, more precise optimizers.

### Gradient Descent

The Gradient Descent (GD) is an iterative optimization algorithm, which allows to minimize a *[[Functions#Differentiability|differentiable function]]*. It is a general-purpose algorithm which lays the basis of a lot of optimization algorithms.

The algorithm is defined as follows:

1. We initialize $\theta_{k=0}$ to some guessed or random state.
2. Calculate $\nabla L(\theta_k)$ ([[Derivatives|first-order derivative]] of $L$)
3. We "take a step" towards the steepest descent: $\theta_{k+1} = \theta_k - \alpha \cdot \nabla L(\theta_k)$
	1. repeat recursively from step 2 until convergence
		1. $\nabla L \eqsim 0$
		2. The resulting change to $\theta_{k+1}$ is negligible

When the recursion stops, the last $\theta$ is our estimation of the parameters $\theta$ we are looking for and the result of the "learning" / best approximation of the original problem using the objective / loss function $L$.

Just for the sake of readability here once again the definition and beauty of the step-function which is the fundamental part of the Gradient Descent:
$$
\theta_{k+1} = \theta_k - \alpha \cdot \nabla L(\theta_k), \alpha\ \text{the learning rate}, L\ \text{the loss/objective function}
$$
Know one can also see why the GD is so elementary and useful for optimization tasks like this: you can hand it any feasible loss function and will receive an approximation / estimation under the specified loss function. The only condition is that $L$ must be [[Functions#Differentiability|differentiable]].

#### "What the heck is this $\alpha$ doing?"

**$\alpha$** is the so called "learning rate" and indicates "how fast" or "in how big steps" we approach the best approximation. You can imagine that the step-function of the GD is like a bicycle riding around on the curve of the first-order derivative $\nabla L$ of $L$. It is driving towards the lowest (local) point and $\alpha$ decides how fast we are going there. Choosing $\alpha$ is not exact science. It's just a value which can again be approximated through iterations. A bad chosen $\alpha$ can lead to over- or underfitted models, because we may "not reach" or "drive past" the best point on the curve. 

#### Variants of GD

There are three common variants of GD we will discover in the wild:

1. Batch GD
2. Stochastic GD
3. Mini-Batch GD

#### Least Mean Squares (LMS) / Widrow-Hoff Rule

The LMS is a special step-function and therefore a special case of the [[#Gradient Descent]]. The step-function is defined as follows:

$$
\theta_{k+1} = \theta_k - \alpha \cdot (y_i - \theta_k \cdot x_i) \cdot x_i, \alpha\ \text{the learning rate}, i\ \text{the current training sample}
$$

We see that $(y_i - \theta_k \cdot x_i) \cdot x_i$ is the equal to $\nabla (y_i - \theta_k \cdot x_i)^2$ with respect to $\theta_k$.

## Estimation

*Answers the question*: "Which are the ***estimated, optimized parameters*** of the model?"

The estimation is the concrete result of an optimizer. In terms of machine learning this means the weights $\theta$ (parameters) of a model.

A general definition of an estimation of $\theta$ can be given using

$$
\theta = argmin_{\theta}\ L(\theta_{k})
$$
$L$ is the loss function defined by the applying principle. The way to find the minimized arguments is defined by the chosen optimization algorithm. 

---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]