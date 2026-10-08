# Supervised Learning

tags: #msc #jmsc #ml #supervised

# Supervised Learning

links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## General 

Supervised learning is the approach of training a predictor to predict a possible outcome $Y$ given the inputs $X$. $X$ is also called *features* and $Y$ the *target*. Supervised learning models are good fit if enough good (!) data is available to train a model using a training set which is a subset of all available data. The model will "learn" from the existing data to predict data in the future. The goal of supervised learning is to *find* / *learn* parameters $\theta$ of a function $h_{\theta}: \mathcal{X} \to \mathcal{Y}$, such that $h_{\theta}(x)$ predicts $y$ within an acceptable deviation. $h_{\theta}$ is also called the Hypothesis. 

When the *target* is continously distributed, we say that the learning problem is a *regression problem*. When the *target* is discretely distributed, the learning problem is called a *classification problem*.

## Inputs / Features

The input-vector $\mathcal{X}$ to a learning problem defines all variables relevant to predict the future values.

## Weights

The weights $\theta$ are the result of solving the learning problem and the defining aspect of each machine learning algorithm. $\theta$ is a vector which is used to parameterize a model. Finding the weights which most accurately model the correct prediction to an input $x$ is the art of machine learning.

## Outputs / Targets

The output-vector $\mathcal{Y}$ (also *targets*), define the structure of the prediction (the result) of a machine learning model.

## Cost function / Objective function / Loss function

The cost function or also the objective function defines the difference of a perfect result $y$ and the corresponding result reached using the hypothesis function $h(x)$: $h(x) - y$. The lower this result is for $x \in \mathcal{X}, y \in \mathcal{Y}$, the better the hypothesis $h(x)$ fits the problem at hand. The cost function can be defined for input ($\mathcal{X}$) and output ($\mathcal{Y}$)  vectors in general like:

$$
J(\theta) = \frac{1}{2} \sum_{i = 1}^n (h_{\theta}(x^{(i)}) - y^{(i)})^2
$$

Be aware that this function depends on the weights $\theta$ and therefore directly implicates how we can solve the learning problem: We minimize the cost function / objective! The lower the deviation from an expected result, the better the model performs.

## Discriminative vs. Generative Models

There are a few categorizations of supervised learning models. We used the categories of the discriminative and generative supervised learning models. They share that they both learn from labeled data (X, y). They differ in *what* they try to model:

While discriminative learning models learn decision boundaries, generative models learn the distribution of the data.

**Discriminative models** model $P(y | X)$: When given the input $X$, what's the probability of $y$?

**Generative models** model $P(X | y)$ ***and*** $P(y)$: When given an output $y$ what's the probability of $X$ being the input vector? How is the data (and the labels) generated (distributed)?

The neat thing about generative models is that they can easily be used to "simulate" discriminative models using the [[Probabilities#Bayes rule|Bayes rule]]:

$$
P(y | X) = \frac{P(X | y)P(y)}{\sum_{y \in Y} P(X | y)P(y)}
$$

The left side of the equivalence is exactly the probability modeled by discriminative approaches.

So discriminative approaches do not learn how the data is distributed and just jump to a conclusion.

## Supervised Learning Algorithm

The general algorithm of supervised learning problems is as follows:

1. Initialize $\theta$  (can be random or any more sophisticated approach)
2. Calculate the step-function (objective function embedded in another function) and evaluate deviation constraints (is the result good enough?)
	1. if the result is within the expected range, you found your $\theta$
	2. if the result is *not* within the expected range, update $\theta$ and go on from 2.

---
links: [[1400 ML MOC|ML MOC]] - [[1000 MSC MOC|MSc MOC]]  - [[themes/000 Index|Index]]