# The linear quadratic regulator (LQR)

The **linear quadratic regulator** is a way of choosing the gain matrix of a feedback controller
optimally. For linear dynamics and a quadratic cost it gives a controller that minimizes the cost from
every initial state and makes the system globally asymptotically stable. ROB 345 covers it in
[Lecture 8](08-lqr.md), the last lecture of the first module. It builds on
[Lecture 7](07-stability-and-pd-control.md), which defined [stability](stability.md) and introduced PD
control, and on the [linearization](linearization.md) of Lecture 6. The next lab implements it on the
course drone.

Notation follows the course. The state is $\bar{x} \in \mathbb{R}^n$ and the control input
$\bar{u} \in \mathbb{R}^m$. $\bar{x}_ 0$ is a fixed point, such as hover, and $\bar{u}_ 0$ the control
input that keeps the system there. Citations are to Lecture 8: "notes eq. (1)" and "notes p. N" for its
written notes, "slide N" for its deck, and (≈M:SS) for its video.

## The problem

Lecture 7's PD controller had the general form $\bar{u}(\bar{x}) = \bar{u}_ 0 + K(\bar{x} - \bar{x}_ 0)$,
where $K$ is the **gain matrix**: a nominal input plus a correction linear in the error in the state
(notes p. 1, ≈7:12–8:44). For the quadrotor moving only up and down, any negative gains made it stable.
But some choices are better than others, more energy-efficient or quicker to reach the goal (≈9:30).
LQR picks $K$ to stabilize the system and, simultaneously, to optimize a performance metric (notes p. 1).

"Linear" refers to the dynamics. Real systems are nonlinear, $\dot{\bar{x}} = f(\bar{x}, \bar{u})$, so
LQR is applied to their linearization about the fixed point,

$$\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0),$$

and the resulting linear controller is then applied to the nonlinear system, in the hope that it is
also a good controller for it (notes p. 1, ≈10:17–11:49). In the deviations
$\tilde{x} \triangleq \bar{x} - \bar{x}_ 0$ and $\tilde{u} \triangleq \bar{u} - \bar{u}_ 0$, the dynamics
are $\dot{\tilde{x}} = A\tilde{x} + B\tilde{u}$ (notes p. 2).

## The cost

"Quadratic" refers to the cost. Two things are worth minimizing: deviations of the state from the fixed
point, and deviations of the control input from the nominal one, which is a measure of effort (≈15:02–16:39).
Weighted, and integrated over all time, they give the **cost function** (notes p. 2)

$$J\left(\tilde{x}(0)\right) \triangleq \int_ 0^\infty \left[ \tilde{x}(t)^T Q \tilde{x}(t) + \tilde{u}(t)^T R \tilde{u}(t) \right] dt,$$

a function of the initial state deviation $\tilde{x}(0)$. With $Q$ and $R$ identity matrices it is
notes eq. (1), the integral of $\Vert \tilde{x}(t) \Vert^2 + \Vert \tilde{u}(t) \Vert^2$. A state that
stays away from the fixed point forever makes the cost infinite. The control term stops the controller
from simply cranking the inputs up to reach the goal as fast as possible (≈21:22–22:09).

The **cost matrices** $Q$ ($n \times n$) and $R$ ($m \times m$) are chosen by the designer, not by the
theory. They set the relative importance of the states and inputs, which do not share units: meters,
radians, meters per second, newtons, newton meters (≈25:15–28:22). They must be symmetric and positive
definite: $z^T Q z \gt 0$ for every non-zero vector $z$ (≈29:09; notes p. 2). Strictly, $Q$ need only be
positive semidefinite (≈34:31). In practice both are diagonal, so that each diagonal entry weighs one
component of the state or input (notes p. 2, ≈32:59–33:44).

## The solution

The derivation is complicated and the course skips it (notes p. 2). The gain comes from the
**algebraic Riccati equation**, a matrix equation in the unknown $n \times n$ matrix $S$:

$$0 = Q - SBR^{-1}B^TS + SA + A^TS.$$

The results (≈40:08–49:32, notes pp. 2–3):

1. **The optimal controller is linear in the state**, $\tilde{u}(\tilde{x}) = K^\ast \tilde{x}$. A single
   matrix, applied at whatever state the system is in, is optimal from every initial state. "This is
   pretty magical!" (notes p. 2).
2. **Step 1**: solve the algebraic Riccati equation for $S$. Call the solution $S^\ast$.
3. **Step 2**: $K^\ast = -R^{-1}B^TS^\ast$.
4. In the original coordinates, the controller is $\bar{u}(\bar{x}) = \bar{u}_ 0 + K^\ast(\bar{x} - \bar{x}_ 0)$:
   a PD controller in the general form, with its gain computed rather than hand-picked.
5. **The optimal cost** is $J^\ast(\tilde{x}(0)) = \tilde{x}(0)^T S^\ast \tilde{x}(0)$ (notes p. 3).
6. **Stability**: the closed loop $\dot{\tilde{x}} = (A + BK^\ast)\tilde{x}$ is globally asymptotically
   stable about the fixed point (notes p. 3, ≈1:01:13–1:02:04).

LQR therefore takes four inputs, $A$, $B$, $Q$ and $R$ (≈44:47). The Riccati equation is quadratic in $S$
and is solved numerically. In Python or Matlab, $[K^\ast, S^\ast] = \mathit{lqr}(A, B, Q, R)$, which
also complains if the system is not stabilizable (notes p. 3). **Those libraries return the negative of
the course's $K^\ast$**, because they use $\tilde{u} = -K^\ast \tilde{x}$; applied unchanged, it
destabilizes the drone (notes p. 3, ≈54:15–55:03).

The assumptions are many: a linear system, a fixed point, and the state known at every time (≈49:32).
A time-varying version, from a matrix differential equation, tracks a trajectory instead of a fixed
point (≈51:05–51:51).

## Tuning Q and R

In theory, any positive definite $Q$ and $R$ give a stable system. In reality the system is nonlinear,
the model is imperfect and the state is not sensed perfectly, so $Q$ and $R$ are tuned until the
behavior is right, "a bit of an art" (notes p. 3). For the 3D quadrotor, $Q$ is $12 \times 12$, over
the state $[x, y, z, \phi, \theta, \psi, \dot{x}, \dot{y}, \dot{z}, p, q, r]$, and $R$ is $4 \times 4$,
over the total thrust and three moments (notes p. 4, ≈1:05:54–1:07:27; see the
[quadrotor model](quadrotor-model.md)).

![Notes drawing, p. 3 — the diagonal 12×12 matrix Q for the quadrotor, with its third diagonal entry circled and labelled "Crank this up"](../raw/images/08-lqr/notes-figure-2.jpg)

*Lecture 8 notes, p. 3 — if the height z is not stabilized well, raise the third diagonal entry of Q, the one that weighs z.*

The lecture's rules of thumb (≈1:06:41–1:12:02):

- The height drifts: increase the diagonal entry of $Q$ for $z$, maybe tenfold.
- The height oscillates: increase the entry for $\dot{z}$, the ninth.
- The drone rolls: increase the fourth entry, for roll $\phi$ (also notes p. 4).
- Nothing tracks and the drone falls: decrease $R$, usually by scaling the whole matrix, which allows
  more control effort. Too small an $R$ makes the motion jerky.

## In practice

LQR is "usually surprisingly effective", a good starting point whenever a system must be stabilized to a
fixed point; in Majumdar's PhD work a simple LQR baseline more often than not beat his fancier nonlinear
controllers (≈1:15:52). The lecture's videos show it on a quadrotor, on a fixed-wing airplane hovering in a
prop hang, and on a humanoid robot, where it beats a hand-tuned PD controller (slides 11–13,
≈1:11:17–1:15:52). Planning and feedback are typically combined in this way: a planner such as an
[RRT](rrt.md) or [trajectory optimization](trajectory-optimization.md) supplies a nominal trajectory, and
a feedback controller, such as time-varying LQR, corrects for deviations from it (≈1:16:38).

## Lectures

- [Lecture 8 — The Linear Quadratic Regulator](08-lqr.md): the cost function, $Q$ and $R$, the
  Riccati equation and $K^\ast$, the sign convention, the optimal cost, stability, tuning for the lab,
  and the three videos.
- [Lecture 7 — Stability and PD Control](07-stability-and-pd-control.md): the stability definitions LQR
  guarantees, stabilizability, and PD control with its gain matrix.
- [Lecture 6 — Trajectory Optimization](06-trajectory-optimization.md): linearizing the planar quadrotor
  about hover, which gives the $A$ and $B$ that LQR needs.
- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): the 3D quadrotor's 12 states and four
  control inputs.
- [Lecture 11 — Bayes Filter](11-bayes-filter.md#from-sets-to-beliefs): LQR assumes the state is known.
  The notes ask how to apply $\bar{u} = K\bar{x}$ when the estimate is a set of possible states, which is
  one reason to estimate the state probabilistically (notes p. 1).
