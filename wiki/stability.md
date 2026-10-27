# Stability

**Stability** is what a feedback controller is asked to achieve: a system pushed away from where it
should be, by a gust of wind or an error in its model, comes back. ROB 345 makes this precise in
[Lecture 7](07-stability-and-pd-control.md), with a fixed point, the closed-loop dynamics, and a short
list of definitions, or "flavors", of stability: the few most relevant to robotics out of the many
that exist (≈20:21). It then asks when stability can be achieved at all, which is
**stabilizability**. How to achieve it is on the [feedback control](feedback-control.md) page.

Notation follows the course. The state is $\bar{x}$, the control input $\bar{u}$, and the dynamics are
$\dot{\bar{x}} = f(\bar{x}, \bar{u})$ (see [state and dynamics](state-and-dynamics.md)). Citations are
to Lecture 7: "notes eq. (N)" and "notes p. N" for its written notes, (≈M:SS) for its video. The
definitions were written on a blackboard the video does not show; the notes are their written record.

## Fixed points

A **fixed point**, or **equilibrium point**, of $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ is a state
$\bar{x}_ 0$ such that

$$\dot{\bar{x}} = f(\bar{x}_ 0, \bar{u}_ 0) = 0 \quad \text{for some choice of } \bar{u}_ 0$$

(notes eq. (1)). It is a state that you remain at forever when you apply $\bar{u}_ 0$ (≈14:47–15:40).
The planar quadrotor's hover point, used in Lecture 6 to [linearize](linearization.md) its dynamics,
is one: any position $(x_0, y_0)$, with orientation and all velocities zero, and the input
$\bar{u}_ 0 = [mg, 0]^T$, a total thrust that cancels gravity and no moment (notes eq. (2), ≈13:13–14:00;
see the [quadrotor model](quadrotor-model.md)). The position can be anything, but the velocities must
be zero, since they are the first components of $\dot{\bar{x}}$ (notes eq. (3), ≈17:12–18:44), and so
must the orientation, apart from the "boring case" of a drone flipped upside down with its thrust
flipped too (≈19:35).

## Closed-loop dynamics

A **feedback controller** $\bar{u}(\bar{x})$ maps each state to a control input. Plugging it into the
dynamics gives the **closed-loop system**,

$$\dot{\bar{x}} = f(\bar{x}, \bar{u}(\bar{x})) \triangleq f_{\text{cl}}(\bar{x})$$

(notes eq. (4), ≈22:41–24:14), whose right-hand side depends on the state alone. The definitions below
are properties of this closed-loop system, written $\dot{\bar{x}} = f(\bar{x})$ for short, with respect to
a fixed point $\bar{x}_ 0$. In them $\bar{x}(0)$ is the initial state and $\bar{x}(t)$ the state at time
$t$; Lecture 7 stresses not to confuse $\bar{x}(0)$ with the fixed point $\bar{x}_ 0$ (≈28:12).

## The definitions

The lecture builds them from three basic properties (≈20:21–46:20):

- **Global attractivity**: from every initial state, the state approaches the fixed point as time goes
  to infinity, $\lim_{t \to \infty} \Vert \bar{x}(t) - \bar{x}_ 0 \Vert = 0$ (≈25:51). It is too strong,
  asking a drone to recover even from "0.99 times the speed of light", and too weak, since it allows
  arbitrarily long times and arbitrarily large excursions before the state comes back (≈29:55–31:27).
- **Local attractivity**: the same, but only for initial states within some ball of radius $R$ around
  the fixed point, $\Vert \bar{x}(0) - \bar{x}_ 0 \Vert \leq R$; outside the ball nothing is required
  (notes eq. (7), ≈32:19–34:38).
- **Stability in the sense of Lyapunov (ISL)**: for every $\epsilon \gt 0$ there is a
  $\delta = \delta(\epsilon)$ such that
  $\Vert \bar{x}(0) - \bar{x}_ 0 \Vert \lt \delta \implies \Vert \bar{x}(t) - \bar{x}_ 0 \Vert \lt \epsilon$
  for all $t \geq 0$ (notes eq. (5), ≈40:10–41:43). Lecture 7 poses it as a game: you name any ball
  of radius $\epsilon$, and I must find a ball of radius $\delta$ from which no trajectory leaves
  yours. The state need not approach the fixed point, but it cannot go far from it (≈37:00–39:20).
  $\delta$ can never exceed $\epsilon$. When $\delta = \epsilon$ works, the region is **invariant**
  (≈45:34–46:20; notes p. 3).

The two definitions used most in practice combine them (≈47:09–48:46):

- **Global asymptotic stability** = global attractivity + stability ISL.
- **Local asymptotic stability** = local attractivity + stability ISL.

The notes do not use the word "attractivity". They define asymptotic stability directly as (i) stable
ISL and (ii) the limit holding from every initial condition (notes eq. (6)), remark that this is really
**global** asymptotic stability, "a very strong condition (and may be impossible to achieve in
practice)", and define local asymptotic stability with (ii) required only within a ball of radius $R$
(notes pp. 2–3). The content is the same.

![Notes drawing, p. 3 — local asymptotic stability: inside the dashed ball of radius R every trajectory spirals in; outside it some leave](../raw/images/07-stability-and-pd-control/notes-figure-2.jpg)

*Lecture 7 notes p. 3 — local asymptotic stability in a two-dimensional state space: inside the dashed ball of radius R every trajectory spirals in to the fixed point; outside it, some trajectories leave.*

## How the definitions relate

- Global attractivity does **not** imply stability ISL: there are systems that approach the fixed
  point from every initial state without being stable in the sense of Lyapunov (≈49:33). This is why
  ISL is part of asymptotic stability: it rules out states that start close to the goal, move very far
  away and only eventually come back (≈1:04:25).
- Global asymptotic stability implies local asymptotic stability (notes p. 3, ≈49:33–50:18).
- For **linear** systems, $\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)$, local
  asymptotic stability also implies global, so the two notions coincide. This is not true for nonlinear
  systems (notes p. 3, ≈50:18–51:52). The lecture states it without proof.
- "Asymptotically" means in the limit: a stable first-order system such as $\dot{x}_ 1 = -x_1$ gets
  closer and closer to the origin and never reaches it in finite time (≈1:02:52–1:04:25).

## Stabilizability

Not every system can be made stable by feedback. Lecture 7's example (notes eq. (8), ≈52:42–54:13) is

$$\dot{\bar{x}} = \frac{d}{dt} \begin{bmatrix} x_1 \cr x_2 \end{bmatrix} = \begin{bmatrix} x_1 \cr x_2 + u \end{bmatrix}.$$

The input $u$ has no effect on $x_1$, and $\dot{x}_ 1 = x_1$ pushes $x_1$ away from the origin from every
starting point other than the origin, so no controller can stabilize the system (notes p. 3,
≈56:38–58:11). Not affecting a component is not the whole reason, though: with $\dot{x}_ 1 = -x_1$
instead, $u$ still cannot touch $x_1$, but $x_1$ goes to the origin by itself, and the system is
stabilizable, for instance with $u = -2x_2$, which makes $\dot{x}_ 2 = -x_2$ (≈55:52–56:38,
≈1:00:34–1:02:07).

A system is **stabilizable** with respect to a fixed point $\bar{x}_ 0$ if any initial state can be
asymptotically driven to $\bar{x}_ 0$ by choosing the control inputs appropriately (notes eq. (9)); in
the lecture's spoken version, if some feedback controller makes it globally asymptotically stable
(≈59:47). Not even every linear system is stabilizable. For linear systems it can be checked by
eigenvalue conditions on $A$ and $B$, which the notes do not state; they point to MAE 433/434 (notes
pp. 3–4).

## Lectures

- [Lecture 7 — Stability and PD Control](07-stability-and-pd-control.md): all the definitions, with
  the board's and the notes' versions, the questions asked about them, and the stabilizability example.
- [Lecture 6 — Trajectory Optimization](06-trajectory-optimization.md): the hover point of the planar
  quadrotor as a nominal point for [linearization](linearization.md), the first fixed point the course
  meets.
- [Lecture 8 — The Linear Quadratic Regulator](08-lqr.md) designs a controller that makes a linear
  system globally asymptotically stable while minimizing a cost; its slide 7 recaps these definitions.
  See [the linear quadratic regulator](lqr.md).
- [Lecture 10 — Nondeterministic Filter](10-nondeterministic-filter.md#does-the-set-always-shrink): why
  instability matters for estimation. Unstable dynamics, for example from a bad feedback controller,
  push states apart, so a small uncertainty about the state grows from step to step unless a good
  sensor counteracts it.
- [Lecture 11 — Bayes Filter](11-bayes-filter.md#can-the-belief-get-worse): the same for a probability
  distribution over the state. With unstable dynamics and a useless sensor, a robot that starts out
  confident about its state becomes less and less so (≈1:12:37–1:13:24).
