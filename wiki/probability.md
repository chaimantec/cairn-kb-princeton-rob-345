# Probability

The probability the course uses, in its own notation, and where it is used. The course lists basic
probability among its prerequisites and promises a refresher ([Lecture 1](01-intro-to-robotics.md#course-logistics)).
The refresher is the opening of [Lecture 11](11-bayes-filter.md#probability-basics), and it is there to
set up the **Bayes filter**, the probabilistic approach to [state estimation](state-estimation.md). The
course's reference for it is Chapter 2.2 of *Probabilistic Robotics* (Thrun, Burgard and Fox) (Lecture 11
notes p. 1).

Citations are to Lecture 11: "notes eq. (N)" and "notes p. N" for its written notes, (≈M:SS) for the
video.

## Notation

A capital letter is a **random variable** and a lowercase letter one of its values: $p(X = x)$ is the
probability that the random variable $X$ takes on the value $x$ (notes p. 1, ≈4:42–5:28). For a coin toss,
$p(X = \text{heads}) = p(X = \text{tails}) = 0.5$ for a fair coin (notes p. 1); the board's example is a
biased coin with 0.7 and 0.3 (≈5:28–7:01). The course writes $p(x)$ for $p(X = x)$, and $p(x \mid y)$ for
$p(X = x \mid Y = y)$; it is shorthand, always meaning the probability of a random variable taking a value
(≈6:14, ≈10:53). In state estimation the random variables are the state $X_ t$, the sensor measurement
$Z_ t$ and the control input $U_ t$ at time $t$ (notes pp. 2–3).

## The rules

- **Probabilities sum to one**: $\sum_x p(x) = 1$, or, for a continuous random variable,
  $\int p(x) dx = 1$ (notes p. 1, ≈7:01–7:48).
- The **joint distribution** $p(x, y)$ is the probability that $X = x$ and $Y = y$ (notes p. 1, ≈8:34).
- $X$ and $Y$ are **independent** when $p(x, y) = p(x)p(y)$, as for two coins flipped independently
  (notes p. 1, ≈9:21–10:07).
- The **conditional distribution** is defined by $p(x \mid y) = p(x, y) / p(y)$, as long as
  $p(y) \gt 0$. If $X$ and $Y$ are independent it reduces to $p(x)$: learning $y$ tells you nothing more
  about $x$ (notes p. 1, ≈11:39–13:16).
- The **theorem of total probability**: $p(x) = \sum_y p(x \mid y)p(y)$ for a discrete $Y$, or
  $p(x) = \int p(x \mid y)p(y) dy$ for a continuous one. Here $p(x)$ is the **marginal distribution**, and
  summing $Y$ out of the joint distribution is **marginalization** (notes p. 1, ≈14:01–15:34).

## Bayes rule

The rule the Bayes filter is named for (notes eq. (1), ≈16:23):

$$p(x \mid y) = \frac{p(y \mid x)p(x)}{p(y)} = \frac{p(y \mid x)p(x)}{\sum_{x'} p(y \mid x')p(x')} \tag{1}$$

It follows from writing the joint probability both ways, $p(x \mid y)p(y) = p(x, y) = p(y \mid x)p(x)$
(notes eqs. (2)–(3), ≈17:09–17:56), and the second form expands the denominator by the theorem of total
probability. Bayes rule "inverts" a conditional probability: it gives $p(x \mid y)$ from $p(y \mid x)$
(notes p. 2).

That is exactly what a robot needs. A sensor comes with a model of the form $p(Z_ t \mid X_ t)$: if you
knew the state, how likely is each reading? At run time the robot has a reading and wants
$p(X_ t \mid Z_ t)$. Bayes rule does the inversion, in the same role as the preimage $h^{-1}(\bar{z}_ t)$ in
the nondeterministic filter (notes p. 3, ≈43:37–45:55). The door example works it through: a sensor that
reads "open" correctly with probability 0.6 and wrongly with probability 0.2 turns a prior of 0.5 into a
belief of 0.75 after one "open" reading (notes pp. 2–3). See
[Lecture 11, "The first measurement update"](11-bayes-filter.md#the-first-measurement-update).

## Where the course uses it

- **The prior and the belief.** The probability the robot assigns to each state before a measurement is the
  **prior**; the probability given the measurements so far is its **belief**, $\mathrm{bel}$ (notes p. 2).
  A prior of exactly 0 or 1 can never be moved by evidence, so in practice priors are never absolutely
  certain (≈42:03–42:50).
- **Probabilistic models of the dynamics and the sensor.** A dynamics model $p(X_ t \mid X_ {t-1}, U_ {t-1})$
  gives the probability of each next state, and a measurement model $p(Z_ t \mid X_ t)$ the probability of
  each reading (notes pp. 3–4). They are the probabilistic counterparts of the sets of outcomes in a
  [non-deterministic model of uncertainty](10-nondeterministic-filter.md#uncertainty-in-the-measurements)
  (Lecture 10), and they have to be obtained somehow, for example by counting outcomes over many trials
  (≈25:37, ≈49:52). See [uncertainty](uncertainty.md).
- **The Bayes filter.** Its dynamics update is the theorem of total probability and its measurement update is
  Bayes rule (notes p. 4). See [Lecture 11, "The Bayes filter"](11-bayes-filter.md#the-bayes-filter) and
  [state estimation](state-estimation.md).

## Lectures

- [Lecture 1 — Introduction to Robotics](01-intro-to-robotics.md#course-logistics): basic probability
  among the prerequisites, and the poll in which about 70–80% of the room said they could write down
  Bayes' rule.
- [Lecture 10 — Nondeterministic Filter](10-nondeterministic-filter.md#next-the-bayes-filter): models of
  uncertainty without probabilities, why the course moves to probabilistic ones, and the notes' advice to
  review basic probability before the next lecture.
- [Lecture 11 — Bayes Filter](11-bayes-filter.md#probability-basics): the refresher (random variables,
  joint and conditional distributions, independence, total probability, Bayes rule and its proof) and its
  use in the door example and the Bayes filter.
