tags: #msc #jmsc #ml #machinelearning #regression #logistic #linear #linear-regression #logistic-regression

# Model selection and Regression

links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Selecting the right model

To implement a learning machine we must first formulate our problem and select a suitable model. This model can be a regressive model. There are also other models like polynomial degree and others. For the moment only the three regression models are relevant to us.

## Regression Models

In general the goal of a regression model is to find / "learn" a function from a given set of inputs $\mathcal{X}$ and outputs $\mathcal{Y}$ using a parametric model $f(x, \theta)$. So by finding / estimating $\theta$ the regression leads to a predictor $f(x, \theta)$ which can be used to predict $y_x$ for any seen or unseen $x_x \to f(x_x, \theta) = y_x$.

For the regression models discussed the following process applies in all cases to successfully find a fitting model using regression:

1. We define a hypothesis / model $h_{\theta}(\mathcal{X}) = h(\mathcal{X}, \theta) = \mathcal{Y}$ which represents the form of the prediction
2. Loss / Objective Function $L(\theta)$: Find / Define a loss / objective function given some (good) training data.
3. Optimization: Estimate a good $\theta$ leveraging optimization using closed-form or GD
	1. $\theta = argmin_{\theta_k} L(\theta_k)$
4. Predict: use the optimized model to predict outputs for any inputs.

So the result of a regression is a function (it does not matter which one).

### Linear Regression

target variable is continuous (e.g. estimating financial aspects)

Result: Linear regressions outputs a real number (identity-function)

#### Problem form

Linear regression solves problems of the following form:

$$
y = \theta^T x+b 
\\
\\
h_{\theta}(x) = \theta^T x + b
$$
We try to minimize a loss function $L(\theta)$ to find the specific $\theta$. Therefore we use [[Principles of Estimation Optimization Methods|suitable means of optimization]]

#### Loss function

The Loss function has the form

$$
L(\theta) = \frac{1}{n} \sum_{i=1}^{n} (p_i - y_i)^2,
\\ y_i \in Y \text{ the expected value},
\\ p_i = h_{\theta}(x), x \in X \text{ the predicted value}

$$
Mean Squared error.

### Logistic Regression

target variable is binary (e.g. yes/no questions, exactly two classes/answers)

Result: Logistic regressions outputs the probability ($\sigma(z) \in \{0,1\}$)

#### Problem form

Logistic regression solves problems of the following form:

$$
P(y = 1 | x) = \sigma(\theta^T x+b) = \frac{1}{1+e^{-(\theta^T x+b)}}, 0 \leq P(y=1|x) \leq 1
$$

We can say that $y | x \sim Bernoulli(p)$ with $p = \sigma(\theta^T x + b)$. (See [[Distributions#Bernoulli|Bernoulli distribution]])

#### Loss function

$$
L(\theta) = -\frac{1}{n} \sum_i^n [ y_i \lg (p_i) + (1-y_i) \lg (1-p_i)]
$$
Negative log-likelihood

### Softmax Regression

target variable is a multiclass problem (e.g. image classification)

Result: Softmax regressions outputs a [[Distributions|probability distribution]]

#### Problem form

Softmax regression solves problems of the following form:

$$
P(y = k | x) = softmax_k(a) = \frac{e^{a_k}}{\sum_{i=1}^{|K|} e^{a_i}}, k \in K, K \text{ set of possible classes / outcomes} 
\\
\\
\sum_{k = 1}^{|K|} P(y = k | x) = 1
$$
#### Loss function

$$
L(\theta) = - \sum_i^n \sum_k^{|K|} y_{ik}\ lg\ (p_{ik})
$$
Also a negative log-likelihood

---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]