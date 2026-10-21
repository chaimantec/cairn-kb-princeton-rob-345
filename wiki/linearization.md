# Linearization

**Linearizing** a robot's dynamics means approximating them, near a chosen operating point, by a
linear function of the state and control input. Most robots' dynamics are nonlinear, which makes
trajectory optimization "and later, feedback control" much more complicated (Lecture 6 notes p. 1).
A linear approximation makes [trajectory optimization](trajectory-optimization.md) a convex quadratic
program that can be solved very efficiently. ROB 345 introduces it in
[Lecture 6](06-trajectory-optimization.md#linearizing-the-planar-quadrotors-dynamics) and works it out
for the planar quadrotor.

Notation follows the course. The state is $\bar{x} \in \mathbb{R}^n$, the control input
$\bar{u} \in \mathbb{R}^m$, and the dynamics are $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ (see
[state and dynamics](state-and-dynamics.md)). Citations are to Lecture 6: "notes eq. (N)" for its
written notes and (≈M:SS) for its video.

## The nominal point

A linear approximation is made about some **nominal** (reference) state $\bar{x}_ 0$ and control input
$\bar{u}_ 0$. Which point to use depends on the system and the application (≈21:14). A natural choice
is a point where the system stays put: applying $\bar{u}_ 0$ at $\bar{x}_ 0$ keeps it at
$\bar{x}_ 0$, so

$$f(\bar{x}_ 0, \bar{u}_ 0) = \bar{0}.$$

For the planar quadrotor (see [the quadrotor model](quadrotor-model.md#the-planar-quadrotor)) that
point is **hover**: level, at rest, at any position $(x_0, y_0)$, with total thrust $u_1 = mg$
cancelling gravity and no moment, $u_2 = 0$ (notes eqs. (2)–(3), ≈22:00–26:46):

$$\bar{x}_ 0 = \begin{bmatrix} x_0 \cr y_0 \cr 0 \cr 0 \cr 0 \cr 0 \end{bmatrix}, \qquad \bar{u}_ 0 = \begin{bmatrix} mg \cr 0 \end{bmatrix}$$

Here the state is $(x, y, \theta, \dot{x}, \dot{y}, \dot{\theta})$, $m$ is the mass and $g$ gravity.
$x_0$ and $y_0$ can be taken as 0 by moving the origin.

## The first-order Taylor expansion

Since $f$ depends on both $\bar{x}$ and $\bar{u}$, its first-order Taylor expansion about the nominal
point has a term for each. The constant term $f(\bar{x}_ 0, \bar{u}_ 0)$ is zero at a point like hover,
which leaves (notes eqs. (4)–(5), ≈27:34–29:54)

$$\dot{\bar{x}} \approx A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0), \qquad A = \left. \left[ \frac{\partial f}{\partial \bar{x}} \right] \right\vert_ {\substack{\bar{x} = \bar{x}_ 0 \cr \bar{u} = \bar{u}_ 0}}, \quad B = \left. \left[ \frac{\partial f}{\partial \bar{u}} \right] \right\vert_ {\substack{\bar{x} = \bar{x}_ 0 \cr \bar{u} = \bar{u}_ 0}}$$

$A$ is the $n \times n$ matrix of partial derivatives of $f$ with respect to the state and $B$ the
$n \times m$ matrix of partial derivatives with respect to the control input, both evaluated at the
nominal point, so both are constant. Row $i$ of each holds the derivatives of the $i$-th component of
$f$ (≈30:39–32:12).

## Worked example: the planar quadrotor about hover

The planar quadrotor's dynamics are (notes eq. (1))

$$f(\bar{x}, \bar{u}) = \begin{bmatrix} \dot{x} \cr \dot{y} \cr \dot{\theta} \cr -\frac{u_1}{m} \sin\theta \cr \frac{u_1}{m} \cos\theta - g \cr \frac{u_2}{I} \end{bmatrix}$$

with $u_1$ the total thrust, $u_2$ the total moment and $I$ the moment of inertia, so $n = 6$ and
$m = 2$. They are nonlinear because of $\sin\theta$ and $\cos\theta$.

**$A$** (notes eq. (7), ≈32:58–36:55). The first three components of $f$ are the velocities, so rows 1–3
each have a single 1, where a velocity is differentiated with respect to itself. In rows 4–6 only one
derivative survives evaluation at hover:
$\partial(-\frac{u_1}{m}\sin\theta)/\partial\theta = -\frac{u_1}{m}\cos\theta$, which is $-g$ at
$\theta = 0$, $u_1 = mg$. So

$$A = \begin{bmatrix} 0 & 0 & 0 & 1 & 0 & 0 \cr 0 & 0 & 0 & 0 & 1 & 0 \cr 0 & 0 & 0 & 0 & 0 & 1 \cr 0 & 0 & -g & 0 & 0 & 0 \cr 0 & 0 & 0 & 0 & 0 & 0 \cr 0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix}$$

**$B$** (notes eq. (8), ≈37:42–43:07). Only two entries are non-zero. The derivative of
$\frac{u_1}{m}\cos\theta - g$ with respect to $u_1$ is $\cos\theta / m$, which is $1/m$ at hover, and
the derivative of $u_2/I$ with respect to $u_2$ is $1/I$:

$$B = \begin{bmatrix} 0 & 0 \cr 0 & 0 \cr 0 & 0 \cr 0 & 0 \cr \frac{1}{m} & 0 \cr 0 & \frac{1}{I} \end{bmatrix}$$

## How good it is, and computing it in practice

The linearized dynamics are "not going to be a perfect approximation, but kind of good enough if you're
close to the nominal state, close to the nominal control input" (≈43:07). The nonlinear method of
Lecture 6, sequential quadratic programming, re-linearizes the dynamics about each new trajectory
rather than about one fixed point (≈1:01:49; see
[trajectory optimization](trajectory-optimization.md#nonlinear-systems-sequential-quadratic-programming)).

Doing it by hand is tedious, but worth doing once or twice for a simple system. For larger ones, such as
the full 3D quadrotor, a few lines of Python compute $A$ and $B$, and the assignment posted with Lecture
6 does exactly that (notes p. 2, ≈43:56–44:42).

## Lectures

- [Lecture 6 — Trajectory Optimization](06-trajectory-optimization.md): the method and the planar
  quadrotor worked through, for trajectory optimization.
- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): the equations of motion being linearized.
- Lectures 7 and 8 (stability and PD control, LQR) turn to feedback control, for which, the notes say,
  nonlinear dynamics also make things more complicated (notes p. 1). They are not yet in this knowledge base; see the
  [course map](course-map.md).
