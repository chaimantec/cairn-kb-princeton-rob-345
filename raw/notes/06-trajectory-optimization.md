---
title: Lecture 6 — Trajectory Optimization (lecture notes)
lecture: 6
pages: 3
source_pdf: https://www.dropbox.com/scl/fi/ctybyh0a1gdrvaywbcylu/Lecture6_notes.pdf?rlkey=i9tmfyhkjiws7gboip2a8fkvl&dl=0
numbering: PDF page N = page N; page 1 prints no number. Equations keep the notes' own numbers (1)–(10); (1)–(5) are on page 1 and (6)–(10) on page 2. Page 3 has unnumbered displays only.
images: none — the notes contain no drawings
figure_audit: The notes have no figures. Every displayed equation, (1)-(10), was compared with the PDF's text layer in the parent, including the position of each equation number and every entry of the evaluated A and B matrices in eqs. (7) and (8); all agree.
---

# Lecture 6 — Trajectory Optimization: lecture notes

Full text of the course's written notes for Lecture 6 (A. Majumdar), transcribed from the PDF. Cite as "notes p. N" or "notes eq. (N)". The notes have no figures. The optimization problem on page 3 is unnumbered and is laid out below as an aligned display.

[wiki page for this lecture](../../wiki/06-trajectory-optimization.md) · [slides](../slides/06-trajectory-optimization.md) · [transcript](../transcripts/06-trajectory-optimization.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| 1. Linearizing the dynamics: planar quadrotor dynamics, nominal point, Taylor expansion | 1 | (1)–(5) |
| Jacobians A and B of the planar quadrotor | 2 | (6)–(8) |
| 2. Trajectory optimization with linear dynamics: linear model, discretization | 2 | (9), (10) |
| The convex quadratic program (find, minimize, subject to) | 3 | unnumbered display only |

## Printed slips

None found.

---

## Page 1

Intro to Robotics — Lecture #6 — Instructor: A. Majumdar

**1. Linearizing the dynamics**

The dynamics of many robotic systems are **nonlinear**. This makes things much more complicated for trajectory optimization (and later, for feedback control). Often, it is very helpful to approximate the dynamics using **linear** approximations.

For the planar quadrotor, we saw that the equations of motion are:

$$
\dot{\bar{x}} = \frac{d}{dt} \begin{bmatrix} x \cr y \cr \theta \cr \dot{x} \cr \dot{y} \cr \dot{\theta} \end{bmatrix} = f(\bar{x}, \bar{u}) = \begin{bmatrix} \dot{x} \cr \dot{y} \cr \dot{\theta} \cr -\frac{u_1}{m} \sin\theta \cr \frac{u_1}{m} \cos\theta - g \cr \frac{u_2}{I} \end{bmatrix}
\tag{1}
$$

We need some "nominal" (i.e., reference) point to linearize dynamics around. For example:

$$
\bar{x}_ 0 = \begin{bmatrix} x_0 \cr y_0 \cr 0 \cr 0 \cr 0 \cr 0 \end{bmatrix}, \qquad \bar{u}_ 0 = \begin{bmatrix} mg \cr 0 \end{bmatrix}.
\tag{2}
$$

Note: we can just take $x_0, y_0$ to be 0 if we want (by shifting the origin of our coordinate system). The nominal control input $u_0$ corresponds to the total thrust ($mg$) and moment (0) required to remain in the hover configuration if the robot starts off there.

**Note:**

$$
\dot{\bar{x}} = f(\bar{x}_ 0, \bar{u}_ 0) = \bar{0}.
\tag{3}
$$

Intuitively, if the quadrotor starts off at $\bar{x}_ 0$ and applies $\bar{u}_ 0$, it will stay at $\bar{x}_ 0$.

We can linearize $f(\bar{x}, \bar{u})$ about $\bar{x}_ 0, \bar{u}_ 0$ to get:

$$
\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0),
\tag{4}
$$

where $A$ and $B$ are constant matrices (of size $6 \times 6$ and $6 \times 2$ respectively for the planar quadrotor).

In particular, we can use a Taylor expansion (from multivariable calculus):

$$
\dot{\bar{x}} = f(\bar{x}, \bar{u}) \approx \underbrace{f(\bar{x}_ 0, \bar{u}_ 0)}_ {=0} + \underbrace{\left. \left[ \frac{\partial f}{\partial \bar{x}} \right] \right\vert_ {\substack{\bar{x} = \bar{x}_ 0 \cr \bar{u} = \bar{u}_ 0}}}_ {:= A} (\bar{x} - \bar{x}_ 0) + \underbrace{\left. \left[ \frac{\partial f}{\partial \bar{u}} \right] \right\vert_ {\substack{\bar{x} = \bar{x}_ 0 \cr \bar{u} = \bar{u}_ 0}}}_ {:= B} (\bar{u} - \bar{u}_ 0).
\tag{5}
$$

---

## Page 2

For the planar quadrotor:

$$
A = \left. \begin{bmatrix} \frac{\partial \dot{x}}{\partial x} & \frac{\partial \dot{x}}{\partial y} & \frac{\partial \dot{x}}{\partial \theta} & \frac{\partial \dot{x}}{\partial \dot{x}} & \frac{\partial \dot{x}}{\partial \dot{y}} & \frac{\partial \dot{x}}{\partial \dot{\theta}} \cr \frac{\partial \dot{y}}{\partial x} & \frac{\partial \dot{y}}{\partial y} & \frac{\partial \dot{y}}{\partial \theta} & \frac{\partial \dot{y}}{\partial \dot{x}} & \frac{\partial \dot{y}}{\partial \dot{y}} & \frac{\partial \dot{y}}{\partial \dot{\theta}} \cr \frac{\partial \dot{\theta}}{\partial x} & \frac{\partial \dot{\theta}}{\partial y} & \frac{\partial \dot{\theta}}{\partial \theta} & \frac{\partial \dot{\theta}}{\partial \dot{x}} & \frac{\partial \dot{\theta}}{\partial \dot{y}} & \frac{\partial \dot{\theta}}{\partial \dot{\theta}} \cr \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial x} & \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial y} & \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial \theta} & \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial \dot{x}} & \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial \dot{y}} & \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial \dot{\theta}} \cr \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial x} & \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial y} & \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial \theta} & \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial \dot{x}} & \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial \dot{y}} & \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial \dot{\theta}} \cr \frac{\partial \left(\frac{u_2}{I}\right)}{\partial x} & \frac{\partial \left(\frac{u_2}{I}\right)}{\partial y} & \frac{\partial \left(\frac{u_2}{I}\right)}{\partial \theta} & \frac{\partial \left(\frac{u_2}{I}\right)}{\partial \dot{x}} & \frac{\partial \left(\frac{u_2}{I}\right)}{\partial \dot{y}} & \frac{\partial \left(\frac{u_2}{I}\right)}{\partial \dot{\theta}} \end{bmatrix} \right\vert_ {\substack{\bar{x} = \bar{x}_ 0 \cr \bar{u} = \bar{u}_ 0}}
\tag{6}
$$

$$
= \begin{bmatrix} 0 & 0 & 0 & 1 & 0 & 0 \cr 0 & 0 & 0 & 0 & 1 & 0 \cr 0 & 0 & 0 & 0 & 0 & 1 \cr 0 & 0 & -g & 0 & 0 & 0 \cr 0 & 0 & 0 & 0 & 0 & 0 \cr 0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix}
\tag{7}
$$

Similarly,

$$
B = \left. \begin{bmatrix} \frac{\partial \dot{x}}{\partial u_1} & \frac{\partial \dot{x}}{\partial u_2} \cr \frac{\partial \dot{y}}{\partial u_1} & \frac{\partial \dot{y}}{\partial u_2} \cr \frac{\partial \dot{\theta}}{\partial u_1} & \frac{\partial \dot{\theta}}{\partial u_2} \cr \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial u_1} & \frac{\partial \left(-\frac{u_1}{m}\sin\theta\right)}{\partial u_2} \cr \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial u_1} & \frac{\partial \left(\frac{u_1}{m}\cos\theta - g\right)}{\partial u_2} \cr \frac{\partial \left(\frac{u_2}{I}\right)}{\partial u_1} & \frac{\partial \left(\frac{u_2}{I}\right)}{\partial u_2} \end{bmatrix} \right\vert_ {\substack{\bar{x} = \bar{x}_ 0 \cr \bar{u} = \bar{u}_ 0}} = \begin{bmatrix} 0 & 0 \cr 0 & 0 \cr 0 & 0 \cr 0 & 0 \cr \frac{1}{m} & 0 \cr 0 & \frac{1}{I} \end{bmatrix}.
\tag{8}
$$

**Note:** In practice, these matrices can be annoying to calculate by hand. In the next assignment, you will use Python to compute these matrices automatically. But it's good to understand how it works and go through the exercise of computing these by hand on your own for simpler systems like the planar quadrotor above.

**2. Trajectory Optimization with Linear Dynamics**

Suppose we have computed our linear approximation of the dynamics:

$$
\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0).
\tag{9}
$$

For trajectory optimization, it is useful to **discretize** these continuous-time dynamics:

$$
\bar{x}[t + \Delta t] \approx \bar{x}[t] + \Delta t \left[ A(\bar{x}[t] - \bar{x}_ 0) + B(\bar{u}[t] - \bar{u}_ 0) \right].
\tag{10}
$$

---

## Page 3

We can then formulate an optimization problem as follows:

$$
\begin{aligned}
\textbf{Find:} \quad & \bar{x}[t], \thinspace \bar{u}[t] \quad \text{for } t = 0, \Delta t, 2\Delta t, \ldots, T \cr
\textbf{Minimize:} \quad & \sum_ {t=0}^{T} \Vert \bar{u}[t] \Vert_ 2^2 \cr
\textbf{Subject to:} \quad & \bar{x}[t + \Delta t] = \bar{x}[t] + \Delta t \left[ A(\bar{x}[t] - \bar{x}_ 0) + B(\bar{u}[t] - \bar{u}_ 0) \right], \quad t = 0, \ldots, T - \Delta t \cr
& \bar{x}[0] = \bar{x}_ {\text{start}} \cr
& \bar{x}[T] = \bar{x}_ {\text{goal}} \cr
& C \thinspace \bar{x}[t] \le \bar{d}, \quad t = 0, \ldots, T.
\end{aligned}
$$

The first constraint ensures that the states and control inputs follow the linearized and time-discretized dynamics. The second and third constraints fix the start and end states of the trajectory. The final constraint ensures that states are bounded within a polytopic region (i.e., a region in state space defined by linear inequalities). The matrix $C$ has size $n \times n$, where $n$ is the dimension of the state; the vector $\bar{d}$ has dimension $n \times 1$.

This is a **convex quadratic program (QP)**. Importantly, convex QPs can be solved very efficiently using solvers such as Mosek, Gurobi, and many others. If you are interested in optimization, there are entire courses devoted to this (e.g., ORF 363 at Princeton).
