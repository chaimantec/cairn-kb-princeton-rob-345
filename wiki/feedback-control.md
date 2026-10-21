# Feedback control

**Feedback control** chooses the robot's control input from the state it is actually in, instead of
applying a planned sequence of inputs blindly. It is how a robot corrects for an imperfect dynamics
model and for external disturbances such as wind. ROB 345 introduces it in
[Lecture 7](07-stability-and-pd-control.md), which defines what a controller should achieve
([stability](stability.md)) and gives a first design, PD control; Lecture 8 continues with the linear
quadratic regulator.

Notation follows the course. The state is $\bar{x}$, the control input $\bar{u}$, and the dynamics are
$\dot{\bar{x}} = f(\bar{x}, \bar{u})$ (see [state and dynamics](state-and-dynamics.md)). Citations are
to Lecture 7: "slide N", "notes eq. (N)" and "notes p. N", and (≈M:SS) for its video.

## Why a plan needs feedback

[Trajectory optimization](trajectory-optimization.md) produces a plan: a control input for every moment
in time. Applied open loop, it drifts. In Lecture 7's replay of Lecture 6's planar quadrotor demo
(slide 3), the executed trajectory matches the plan at first and deviates near the end, with the
dynamics unchanged, from numerical integration error alone. With the inertia changed by 10% the flight
comes close to an obstacle; with the mass changed by 10% it hits one (≈2:29–4:47). Small differences
between the dynamics used for planning and the real dynamics are enough.

These are forms of the course's central theme, [uncertainty](uncertainty.md). Slide 4 lists three that
planning has so far ignored: an imperfect dynamics model (unmodeled aerodynamics, physical parameters
estimated from simple pendulum experiments, thrust that changes with the battery level), external
disturbances such as wind gusts, and imperfect knowledge of the robot's state or map (≈4:47–6:19).
Feedback control addresses the first two. The course's second module, on state estimation,
localization and mapping, addresses the third (≈6:19).

## A controller is a vector field

The course's running example is hovering, "the simplest thing that a drone can do" (≈7:05). A drone
that finds itself too low should increase its thrust. One to the left of its goal should tilt right,
by cranking up its left rotor and cranking down its right one, and one to the right the mirror image.
One above the goal and tilted should lower both thrusts while righting itself (slides 5–6,
≈7:05–8:36).

![Slide 6 — Feedback control for hovering](../raw/images/07-stability-and-pd-control/slide-6.png)

*Lecture 7, slide 6 — the goal state in the middle and four displaced copies, each with the rotor thrusts that bring it back. The rule that gives such an input at every state is the feedback control law.*

Doing this at every possible state defines a "vector field", a map from each state to the control
input to apply. That map is a **feedback control law**, or **controller**, $\bar{u}(\bar{x})$ (slides
5–6, ≈8:36–9:21). Plugged into the dynamics, it gives the **closed-loop dynamics**
$\dot{\bar{x}} = f(\bar{x}, \bar{u}(\bar{x})) \triangleq f_{\text{cl}}(\bar{x})$ (notes eq. (4)), and what we
want of them is [stability](stability.md): a fixed point, such as hover, to which the system returns.

## Replanning as feedback: model predictive control

Trajectory optimization can itself be used for feedback: plan to the goal, execute a portion of the
plan, sense where the robot actually is, replan from there, and repeat. Because the plan is constantly
adapted to the robot's real state, this is feedback. It is called **receding horizon control** or
**model predictive control (MPC)**, and it is common. Its challenge is solving the trajectory
optimization very quickly: feasible for linear systems, harder for nonlinear systems with complex
obstacles. The controllers the course develops next do not need iterative replanning (Lecture 7,
≈10:06–11:40).

## PD control

**Proportional-derivative (PD) control** is a basic structure for feedback controllers, and PD
controllers "are extremely popular and effective in practice" (notes p. 5). Lecture 7 develops it for
a planar quadrotor that can only move up and down, with $\ddot{y} = u_1/m - g$, state
$\bar{x} = [y, \dot{y}]^T$, and the goal of hovering at height $y_0$, a fixed point with $u_0 = mg$
(notes eqs. (10)–(12), ≈1:05:12–1:07:30).

**Proportional feedback alone** sets $u(\bar{x}) = u_0 + k_p (y - y_0)$ (notes eq. (13)). With
$\tilde{y} = y - y_0$, the closed loop is $\ddot{\tilde{y}} = \frac{k_p}{m} \tilde{y}$ (notes eq. (15)), a
spring-mass system with no damping, which "is just going to keep oscillating" (≈1:11:29).

**Adding a derivative term** sets $u(\bar{x}) = u_0 + k_p (y - y_0) + k_d \dot{y}$ (≈1:12:16; the notes'
eq. (16) prints the first gain as $k_p/m$, a slip), giving

$$\ddot{\tilde{y}} = \frac{k_p}{m} \tilde{y} + \frac{k_d}{m} \dot{\tilde{y}},$$

a spring-mass-damper (notes eq. (17), ≈1:13:48). Any choice of $k_p, k_d \lt 0$ makes it globally
asymptotically stable. A positive $k_d$ would be negative damping, which makes errors in the speed grow
(notes p. 5, ≈1:15:19).

$k_p$ is the **proportional gain** and $k_d$ the **derivative gain**. A PD controller is a nominal input
plus a constant times the deviation in position plus a constant times the deviation in speed (≈1:16:04).
In matrix form, $\bar{u}(\bar{x}) = \bar{u}_ 0 + K(\bar{x} - \bar{x}_ 0)$, where $K$, here
$[k_p, k_d]$, is the **gain matrix** (notes eqs. (18)–(19)). PD control does not consider obstacles: it
tracks a planned trajectory as tightly as it can (≈11:40–12:25).

## Choosing the gains

For the one-dimensional example any negative gains work, but "in general, things will not be so easy!"
How to choose $K$ in general, ensuring asymptotic stability while optimizing a performance metric, is
the subject of Lecture 8, the **linear quadratic regulator (LQR)**, optimal feedback control for linear
dynamics (notes p. 5; slide 7). A lab has students implement an LQR controller on the real drone
(≈10:06). Lecture 8 is not yet in this knowledge base; see the [course map](course-map.md).

## Lectures

- [Lecture 7 — Stability and PD Control](07-stability-and-pd-control.md): why plans need feedback, the
  controller as a vector field, the stability definitions, stabilizability and PD control.
- [Lecture 6 — Trajectory Optimization](06-trajectory-optimization.md): the planner whose open-loop
  execution motivates feedback, and the hover point of the planar quadrotor, used there for
  [linearization](linearization.md).
- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): the equations of motion being controlled.
- Lecture 8 (the linear quadratic regulator) is not yet in this knowledge base.
