# State estimation

How a robot works out its state, where it is and how it is moving, from imperfect sensing, and how it
combines imperfect information over time into a better estimate. It is the subject of the course's second
module, "State estimation, localization, mapping" (see the [course map](course-map.md)). This page
collects what the knowledge base has on it so far: why it is needed ([Lecture 9](09-optical-flow.md)), and
the first estimator, the nondeterministic filter ([Lecture 10](10-nondeterministic-filter.md)). The
probabilistic filters that follow (Bayes filtering, then Kalman and particle filtering) are scheduled next
and are not yet in this knowledge base.

Citations are to Lecture 10 unless another lecture is named: "notes p. N" for its written notes (which
number no equations) and (≈M:SS) for the video.

## Why a robot needs it

The course's motion planning and [feedback control](feedback-control.md) assumed two things: that the
robot's sensors let it estimate its state $\bar{x}(t)$ perfectly at any time, and that it knows exactly
where the obstacles are (notes p. 1). Neither holds. The second module drops them: first estimating the
state from noisy or imperfect measurements, then building a map, and finally doing both at once, which is
SLAM, simultaneous localization and mapping (notes p. 1, ≈2:27). Lecture 7 already listed imperfect
knowledge of the state or map among the uncertainties planning ignores (see
[uncertainty](uncertainty.md)).

Sensing is imperfect in practice. Integrating the drone's accelerometer twice gives a very noisy position,
which is why the course drone uses a downward-facing optical flow camera to estimate its velocity, and any
method of computing [optical flow](optical-flow.md) is itself imperfect (see
[Lecture 9, "Sensing is imperfect"](09-optical-flow.md#sensing-is-imperfect)). Whatever algorithm produces
an estimate, it will have errors, so what is needed is a way to aggregate many imperfect estimates over
time into a better one (≈3:13–3:59).

## Measurements and the sensor model

A **measurement** or **observation** $\bar{z}$ is the vector of the robot's sensor readings (notes p. 2). A
**sensor model** (sensor mapping, sensor function)

$$\bar{z} = h(\bar{x})$$

says which measurement the sensors produce from each state $\bar{x}$ (notes pp. 2–3). Lecture 10's example
is a point robot in the plane measuring its distances to fixed points: $h$ maps its position $(x, y)$ to
those distances, so with three sensors $\bar{z} \in \mathbb{R}^3$ (notes p. 2, ≈15:01–15:47).

## The preimage: which states fit a measurement

Going backwards, the **preimage** of a measurement is the set of states that could have produced it
(notes p. 3):

$$h^{-1}(\bar{z}) = \lbrace \bar{x} \in \mathcal{X} \mid h(\bar{x}) = \bar{z} \rbrace$$

where $\mathcal{X}$ is the state space. One distance measurement puts the robot on a circle, two on the
crossing points of two circles, three at a single point (notes pp. 1–2, ≈5:31–11:49). The notation is not a
true inverse: $h$ is generally not invertible, and $h^{-1}(\bar{z})$ is a set. Only when every preimage is
a single state is $h$ invertible and the measurement enough to determine the state (notes p. 3,
≈19:38–21:10).

## Combining measurements over time: the nondeterministic filter

With discrete-time dynamics $\bar{x}_ {t+1} = f(\bar{x}_ t, \bar{u}_ t)$, or $\bar{x}_ {t+1} = f(\bar{x}_ t)$
for a closed-loop system (notes p. 3; see [state and dynamics](state-and-dynamics.md)), the robot can carry
what it knows from one time step to the next. The **nondeterministic filter** keeps a set $\hat{X}_ t$ of
states the robot might be in, starting from a set $\hat{X}_ 0$ that may be the whole state space, and at
every time step $t$ (notes p. 4, ≈37:35–39:10):

1. the **dynamics update** computes $f(\hat{X}_ {t-1})$, every state the dynamics can carry a state of
   $\hat{X}_ {t-1}$ to;
2. the **measurement update** computes the preimage $h^{-1}(\bar{z}_ t)$ of the new measurement;
3. the two are fused by intersection: $\hat{X}_ t = f(\hat{X}_ {t-1}) \cap h^{-1}(\bar{z}_ t)$.

![Notes drawing, p. 4 — a starting set, its image under the dynamics, the dashed preimage of a measurement, and their hatched overlap](../raw/images/10-nondeterministic-filter/notes-figure-5.jpg)

*Lecture 10 notes, p. 4 — one step of the filter: the starting set (left), where the dynamics take it (the pear-shaped set), the preimage of the measurement (dashed), and their hatched overlap, the new estimate.*

It is called non-deterministic because the state is not determined, only confined to a set, and because
it is not probabilistic: no state in the set is considered more likely than another (≈39:58–40:43). The
details, with the questions asked in class, are on the
[Lecture 10 page](10-nondeterministic-filter.md#the-nondeterministic-filter).

## Uncertainty can grow

The estimate does not necessarily improve over time. With unstable dynamics, such as $x_{t+1} = \lambda x_t$
for a one-dimensional state $x_t$ and a scalar $\lambda$ that moves states away from the origin, a small
starting interval $[-\epsilon, \epsilon]$ becomes $[-\lambda\epsilon, \lambda\epsilon]$ after one step, and
a robot with no sensor, whose preimage is always the whole state space, grows more uncertain at every step
(≈43:47–49:17). A good sensor counteracts this: a perfect one makes the dynamics irrelevant (≈50:02). The
uncertainty comes from not knowing the initial state, amplified by the dynamics, not from the dynamics
being random (≈46:52–47:39). See [stability](stability.md).

## Models of uncertainty

Real dynamics and sensors are uncertain too. In a **non-deterministic model of uncertainty** each one gives
a set of possible outcomes, with no probabilities: from a state, the next state may be anywhere in a set;
a distance sensor accurate to $\pm\epsilon$ puts the robot in a ring rather than on a circle (notes p. 5,
≈52:19–57:46). The nondeterministic filter extends to these with the same structure (notes p. 5,
≈58:33). A **probabilistic** model instead puts a distribution over the outcomes (notes p. 6).

## Why the nondeterministic filter is not used directly, and what replaces it

It is conservative, tracking every state the system could be in and so reasoning about the worst case, and
its sets can grow very large; it is hard to compute, since representing the sets in a 12-dimensional
quadrotor state space is extremely inefficient and the preimage of a camera or lidar measurement is hardly
even representable; and a nondeterministic model of uncertainty is hard to specify (notes p. 6,
≈58:33–1:00:52). It is the conceptual basis for the methods that are used (notes p. 6). The next of them is
the **Bayes filter**, which keeps a probability distribution over states instead of a set and follows the
same steps: a dynamics update of the distribution, then a measurement update in which Bayes rule plays the
role of the preimage and the intersection (≈1:01:42–1:04:00).

## Lectures

- [Lecture 9 — Optical Flow](09-optical-flow.md): why state estimation is needed on the drone; optical flow
  as its velocity sensor; and why every sensing method is imperfect.
- [Lecture 10 — Nondeterministic Filter](10-nondeterministic-filter.md): the sensor model and its
  preimage, the nondeterministic filter, an example where the uncertainty grows, non-deterministic models
  of uncertainty in the dynamics and the sensor, the filter's limitations, and a preview of the Bayes
  filter.
- Lectures 11 (Bayes filtering) and 12 (Kalman filtering and particle filtering) are next in the
  schedule. They are not yet in this knowledge base.
