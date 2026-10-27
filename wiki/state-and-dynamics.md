# State and dynamics

From Lecture 4 on, ROB 345/549 describes every robot by its **state**, its **control input**,
and a first-order differential equation that says how the state changes:

$$\dot{\bar{x}} = f(\bar{x}, \bar{u})$$

Here $\bar{x}$ is the state vector, $\bar{u}$ the control input vector, $\dot{\bar{x}}$ the time
derivative of the state, and $f$ a function that also involves the robot's physical constants.
The course writes vectors with a bar (notes p. 3). This page explains the terms and how equations
of motion are brought into this form. The worked example is the planar quadrotor of
[Lecture 4](04-quadrotor-dynamics.md), whose full model is on [the quadrotor model](quadrotor-model.md).
Equation numbers are those of the Lecture 4 notes
([as text](../raw/notes/04-quadrotor-dynamics.md)), and timestamps refer to Lecture 4.

## Why dynamics enter the course

[Geometric motion planning](configuration-space.md) finds a collision-free path and ignores how
the robot moves. Two things go wrong with that (slide 4, ≈0:13–4:04):

- **Dynamic feasibility.** "Not all motion plans are physically executable by our robot." A
  quadrotor cannot translate sideways while level, because its thrust is always perpendicular to
  its body, and a car without omni-directional wheels cannot drive sideways (notes p. 1).
- **Errors and disturbances.** Even a feasible plan may not be followed exactly, because the model
  is imperfect or because of disturbances such as wind gusts.

The course takes up the first in Lectures 4–6, planning with dynamics, and the second afterwards
with feedback control (≈4:04, notes p. 1; see the [course map](course-map.md)). Both need a model
of the dynamics in the form above.

## Equations of motion are second order

Equations of motion come from Newton's second law: total force equals mass times acceleration. For
the planar quadrotor, with $u_1$ the total thrust, $u_2$ the total moment, $m$ the mass and $I$ the
moment of inertia (notes eqs. (9)–(11)):

$$\ddot{x} = -\frac{u_1}{m}\sin\theta, \qquad \ddot{y} = \frac{u_1}{m}\cos\theta - g, \qquad \ddot{\theta} = \frac{u_2}{I}.$$

Because acceleration is the second derivative of position, Newton's second law always produces
**second-order** differential equations, with double time derivatives (≈13:26).

## Converting to first order

Introduce a new variable for each first derivative (notes eqs. (12)–(14), ≈14:57):

$$v_x \triangleq \dot{x}, \qquad v_y \triangleq \dot{y}, \qquad \omega \triangleq \dot{\theta},$$

where $\triangleq$ means "is defined as". The definitions are three first-order equations, and
the equations of motion supply the derivatives of the new variables, $\dot{v}_ x = \ddot{x}$ and
so on: three more (≈15:43–17:16). In general, **$n$ second-order equations become $2n$
first-order equations** (≈17:16–18:01). The planar quadrotor's three become six (notes eqs.
(15)–(20)); the 3D quadrotor's six become twelve (≈41:23).

## State, configuration variables, control input

- **State** $\bar{x}$: everything needed to predict the system's motion (notes p. 3). For the
  planar quadrotor, $\bar{x} = [x, y, \theta, \dot{x}, \dot{y}, \dot{\theta}]^T$.
- **Number of states**: the dimension of $\bar{x}$. The planar quadrotor has 6; constrained to move
  only along $y$ it has 2; the 3D quadrotor has 12.
- **Configuration variables**: the part of the state that gives the configuration, without the
  time derivatives, here $[x, y, \theta]$. They are the coordinates of the
  [configuration space](configuration-space.md), one per degree of freedom (≈25:03, notes p. 3).
- **Control input** $\bar{u}$: what the robot can directly command. For the planar quadrotor,
  $\bar{u} = [u_1, u_2]^T$ (notes p. 3). There is often a choice: the 3D quadrotor's inputs could
  be the four propeller thrusts, but the course uses total thrust and three moments, which carry
  the same information (notes eq. (22)).
- **Physical parameters**: constants that appear in $f$ but are neither state nor input, such as
  $m$, $I$ and the thrust coefficient $k_f$. The model is fully specified only once their values
  are known (notes p. 4).

The choice of state is not unique either. The 3D quadrotor could use the Euler-angle rates in its
state, but the course uses the angular velocity $p, q, r$ because it makes the equations more
compact (≈42:59–43:47).

## The general form, and what it is for

Stacking the first-order equations gives (notes eq. (21))

$$\dot{\bar{x}} = f(\bar{x}, \bar{u}) \tag{21}$$

"We will always be able to write EoMs in this form" (notes p. 3). The left-hand side has a single
dot. The right-hand side involves only the state, the control input and physical constants
(≈21:10–21:58).

Its use is **prediction**. Give the state at an initial time and the control inputs over a time
horizon, and the equations determine the state at every future time, solved analytically or
numerically (notes p. 3, ≈23:32). In Majumdar's words, this is "basically the starting point for
doing motion planning in a way that accounts for the dynamics of the system, or to do feedback
control to correct for errors" (≈23:32–24:17). A fuller justification for the first-order form is
promised for later lectures (≈24:17).

The course does not ask students to derive equations of motion. It assumes they are provided, in
this form, and uses them (notes p. 3, ≈25:48–26:34).

## Lectures

- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): introduces the state, control input
  and first-order form on the planar quadrotor, and extends them to the 3D quadrotor.
- [Lecture 2](02-discrete-motion-planning.md) and [Lecture 3](03-rrts.md): configuration space,
  whose coordinates become the configuration variables of the state.
- [Lecture 5 — Differential Flatness](05-differential-flatness.md) builds on this form: a
  [differentially flat](differential-flatness.md) system's state and control input can be computed
  from a few flat outputs and their time derivatives.
- [Lecture 6 — Trajectory Optimization](06-trajectory-optimization.md) grows an RRT in state space,
  then [linearizes](linearization.md) $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ about a nominal state and
  input to $\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)$ for
  [trajectory optimization](trajectory-optimization.md).
- [Lecture 7 — Stability and PD Control](07-stability-and-pd-control.md) plugs a feedback controller
  $\bar{u}(\bar{x})$ into $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ to get the closed-loop dynamics
  $\dot{\bar{x}} = f_{\text{cl}}(\bar{x})$, and defines fixed points and [stability](stability.md) for them.
- [Lecture 8 — The Linear Quadratic Regulator](08-lqr.md) shifts the linearized dynamics to the
  deviations $\tilde{x} = \bar{x} - \bar{x}_ 0$, $\tilde{u} = \bar{u} - \bar{u}_ 0$, giving
  $\dot{\tilde{x}} = A\tilde{x} + B\tilde{u}$, and designs an optimal feedback controller for it
  ([LQR](lqr.md)).
- [Lecture 10 — Nondeterministic Filter](10-nondeterministic-filter.md#adding-dynamics-in-discrete-time)
  switches to discrete time for state estimation, $\bar{x}_ {t+1} = f(\bar{x}_ t, \bar{u}_ t)$, or
  $\bar{x}_ {t+1} = f(\bar{x}_ t)$ for a closed-loop system, obtained by discretizing a continuous-time
  model or given in discrete time from the start, and uses it to predict the set of states a robot can
  reach. See [state estimation](state-estimation.md).
