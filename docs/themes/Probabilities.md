tags: #msc #jmsc #math #probabilistic #proba

# Probabilities

links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]

---

## Probability Spaces

A space of probability is defined by three objects:

1. Target set $\Omega$: the set of possible outcomes
2. Event set $\mathcal{A}$: set of events that can occur
3. Probability Metric $\mathbb{P}$ (or sometimes just $P$): The metric of a probability define how elements of events and targets relate to each other.

A probability space is defined as: $(\Omega, \mathcal{A}, \mathbb{P}) = (\Omega, \mathcal{A}, P)$

## Probability Metrics

A probability metric is a denoted as $P(A), A \in \mathcal{A}$ and describes the probability of the event $A$ in a given a space of probability $(\Omega, \mathcal{A}, P)$.

### Addition of Probabilities

$P(A \cup B) = P(A) + P(B) - P(A \cap B)$

### Dependent and Independent Events

Two events $A, B \in \mathcal{A}$ are called independent if holds: $P(A \cap B) = P(A) \cdot P(B)$

If this property is not given, $A, B$ are said to be dependent.

For a general definition of independence let $k$ be a tuple of indices $1 \leq i_1 < i_2 < ... < i_k \leq n, 1 \leq k \leq n$:

$P(A_{i1} \cap A_{i2} \cap ... \cap A_{ik} = P(A_{i1}) \cdot P(A_{i2}) \cdot ... \cdot P(A_{ik})$

### Inclusion-Exclusion Formula

For events $A_1, A_2, ..., A_n \in \mathcal{A}$ holds:

$$
P(\bigcup_{i = 1}^n A_i) = \sum_{k = 1}^n (-1)^{k+1}(\sum_{1 \leq i_1 < i_2 < ... < i_k \leq n} P(A_{i_1} \cap A_{i_2} \cap ... \cap A_{i_k}))
$$

For three events $A, B, C \in \mathcal{A}$ this gives:

$$
P(A \cup B \cup C) = P(A) + P(B) + P(C) - P(A \cap B) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C)
$$

### Conditional Probability

The conditional probability models the situation "given B, what is the probability of A", where $A, B \in \mathcal{A}$. The definition of this conditional probability is

$$
P (A | B):= \frac{P(A \cap B)}{P(B)}
$$

#### Multiplication of probabilities

Similar to the addition of probability, the multiplication of probabilities is defined as:

$$
P(A \cap B) = P(B|A) \cdot P(A)
$$
For an arbitrary number of events $A_1, A_2, ..., A_n \in \mathcal{A}$ with $P(A_1 \cap A_2 \cap ... \cap A_n) > 0$ then holds

$$
P(A_1 \cap ... \cap A_n) = P(A_1) \cdot P(A_2 | A_1) \cdot P(A_3 | A_1 \cap A_2) \cdot ... \cdot P(A_n | A_1 \cap ... \cap A_{n-1})
$$

## Partition of probabilities

We call a series $B_1, B_2, ... B_n \in \mathcal{A}$ a partition of the target set $\Omega$, when for the conditions $P(B_i) > 0$ and $B_i$ disjoint from $B_j$ for $i \neq j$ holds: $\Omega = B_1 \cup B_2 \cup ... \cup B_n$

### Total Probability

The partition gives the total probability theorem

$$
P(A) = P(B_1)P(A|B_1) + P(B_2)P(A|B_2) + ... + P(B_n)P(A|B_n)
$$
or in short

$$
\sum_{i = 1}^n P(B_i)P(A|B_i)
$$

When we have a an event $B$ then the events $B, B^C$ are a partition of $\Omega$:

$$
P(A) = P(B)P(A|B) + P(B^C)P(A|B^C)
$$

### Bayes rule

The rule of Bayes states for an event $A \in \mathcal{A}$ and a partition $B_1, B_2, ... , B_n \in \mathcal{A}$ of $\Omega$ with $P(A) > 0$, then for each $j = 1, ..., n$ holds:

$$
P(B_j | A) = \frac{P(B_j)P(A | B_j)}{P(A)} = \frac{P(B_j)P(A | B_j)}{\sum_{i = 1}^n P(B_j)P(A | B_j)}
$$

For the case we have a partition with only two events $B, B^C \in \mathcal{A}$ then the rule of Bayes expands to

$$
P(B | A) = \frac{P(B)P(A|B)}{P(B)P(A|B)+P(B^C)P(A|B^C)}
$$

---
links: [[1100 MATH MOC|Mathematics]] - [[1000 MSC MOC|MSc MOC]] - [[themes/000 Index|Index]]