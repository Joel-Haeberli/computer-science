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

### Logistic Regression

target variable is binary (e.g. yes/no questions, exactly two classes/answers)

Result: Logistic regressions outputs the probability ($\sigma(z) \in \{0,1\}$)

### Softmax Regression

target variable is a multiclass problem (e.g. image classification)

Result: Softmax regressions outputs a [[Distributions|probability distribution]]


---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]