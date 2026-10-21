# Differential flatness

A robot is **differentially flat** when a few quantities, its **flat outputs**, can be made to
follow any sufficiently smooth trajectory, and the control inputs that achieve it and the full
state trajectory that results can both be computed from that trajectory and its time derivatives.
For such a robot, planning with dynamics reduces to planning a smooth curve in the flat output
space. ROB 345/549 introduces the idea in [Lecture 5](05-differential-flatness.md) as a way to give
the [RRT](rrt.md) an extension step the robot can actually execute. Equation numbers on this page
are those of the Lecture 5 notes ([as text](../raw/notes/05-differential-flatness.md)), and
timestamps refer to Lecture 5.

## The problem it answers

An RRT extends its tree by moving in a straight line through configuration space, from the nearest
vertex toward a random sample. A robot with dynamics often cannot follow that line. A drone cannot
translate sideways while level, because it has no way to thrust horizontally without tilting, and
a car cannot drive sideways (notes p. 1, ≈3:19–4:52). Planning has to respect the equations of
motion, written in the course's general form $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ (see
[state and dynamics](state-and-dynamics.md)). Differential flatness is one way to do this, for a
special but fairly broad class of systems: the car, the car with a trailer, the planar quadrotor and
the 3D quadrotor, among others (notes p. 2).

## Definition

Let the dynamics be $\dot{\bar{x}} = f(\bar{x}, \bar{u})$, with state $\bar{x} \in \mathbb{R}^n$ and
control input $\bar{u} \in \mathbb{R}^m$. Bars denote vectors, and $\bar{u}^{(p)}$ is the $p\text{th}$ time
derivative. The system is differentially flat if there are flat outputs

$$\bar{z} = \alpha(\bar{x}, \bar{u}, \dot{\bar{u}}, \ddot{\bar{u}}, \ldots, \bar{u}^{(p)})$$

for some function $\alpha$, such that the state and the control input are both functions of the
flat outputs and their first $q$ time derivatives (notes p. 2, ≈39:19–45:35):

$$\bar{x} = \beta(\bar{z}, \dot{\bar{z}}, \ddot{\bar{z}}, \ldots, \bar{z}^{(q)}), \qquad \bar{u} = \gamma(\bar{z}, \dot{\bar{z}}, \ddot{\bar{z}}, \ldots, \bar{z}^{(q)}).$$

Read it as a recipe. Choose a trajectory $\bar{z}(t)$ for $t \in [0, T]$. Then $\gamma$ gives the
control inputs that make the robot follow it, and $\beta$ gives the state trajectory the robot then
traces out.

![Notes drawing, p. 2 — specify z̄(t); differential flatness (via β, γ) gives the inputs ū(t) and the state x̄(t)](../raw/images/05-differential-flatness/notes-figure-3.jpg)

*Lecture 5 notes p. 2 — choose the flat output trajectory z̄(t) on the left; β and γ give the control inputs ū(t) and the resulting state x̄(t). Each plot is a scalar stand-in for a vector. [Notes](https://www.dropbox.com/scl/fi/d0g09pk1opfkwdw7udmsi/Lecture5_notes.pdf?rlkey=l1sriwzrnb499bsbcyo3cylm9&dl=0)*

Four facts go with the definition:

- **Smoothness is required.** The chosen trajectory must have a $q\text{th}$ time derivative. That rules
  out teleporting and sharp corners, and $q$ depends on the system (≈47:07).
- **Only the flat outputs are chosen.** The rest of the state does whatever the dynamics make it
  do. In the notes' words, it "might end up being a bit wacky… but the flat outputs will behave as
  desired" (notes p. 3). The planar quadrotor might flip around while its center of mass follows
  the requested path exactly (≈21:58).
- **Number of flat outputs = number of control inputs.** The course states this theorem without
  proof (notes p. 3, ≈51:03–51:55).
- **There is no general test.** Showing that a system is flat takes "some cleverness on your part"
  (notes p. 4). Entire papers have been devoted to one system (≈48:41).

In principle the flat outputs may depend on the control input and its derivatives. In the systems
the course meets they are functions of the state alone, and in both of Lecture 5's examples simply
a subset of the state (≈43:16, ≈52:41–53:26, ≈58:09).

## Worked example: the planar quadrotor

The planar quadrotor has thrusts $F_1$ and $F_2$, mass $m$, arm length $L$, moment of inertia $I$
and state $[x, y, \theta, \dot{x}, \dot{y}, \dot{\theta}]^T$ (see
[the quadrotor model](quadrotor-model.md#the-planar-quadrotor)). Its equations of motion are (notes
eqs. (1)–(3))

$$\ddot{x} = -\frac{(F_1 + F_2)}{m}\sin(\theta) \tag{1}$$

$$\ddot{y} = \frac{(F_1 + F_2)}{m}\cos(\theta) - g \tag{2}$$

$$\ddot{\theta} = \frac{(F_2 - F_1)L}{I} \tag{3}$$

Its flat outputs are the center of mass position, $\bar{z} = [x, y]^T$: two flat outputs for two
control inputs. The proof runs as follows (notes p. 3; worked in
[Lecture 5](05-differential-flatness.md#proof-part-two-recovering-the-state)).

**$\beta$, the state.** Differentiating $x(t)$ and $y(t)$ gives $\dot{x}$, $\dot{y}$, $\ddot{x}$
and $\ddot{y}$. Dividing (1) by (2) cancels $F_1 + F_2$ and $m$:

$$\theta = \arctan\left(\frac{-\ddot{x}}{\ddot{y} + g}\right) \tag{4}$$

Differentiating $\theta$ gives $\dot{\theta}$, and the state is complete.

**$\gamma$, the control inputs.** Differentiating (4) twice gives $\ddot{\theta}$. Then (3) and
(1), or (3) and (2), are two equations that are linear in the two unknowns $F_1$ and $F_2$, and
solving them gives the inputs at every time.

Because $\ddot{\theta}$ differentiates second derivatives twice more, the inputs depend on the
fourth derivatives $\frac{d^4 x(t)}{dt^4}$ and $\frac{d^4 y(t)}{dt^4}$, so $q = 4$ (notes p. 3,
≈46:21).

## The 3D quadrotor

The 3D quadrotor is differentially flat with four flat outputs, its center of mass position and its
yaw (notes p. 3, ≈54:13–57:22):

$$\bar{z} = \begin{bmatrix} x \cr y \cr z \cr \psi \end{bmatrix}.$$

Any sufficiently smooth trajectory of position and yaw can be flown. The roll and pitch are not
chosen: they follow, and can be computed. The course does not prove this result. The notes point to
Section 16.2.6 of Powers, Mellinger and Kumar, "Quadrotor Kinematics and Dynamics", in the
*Handbook of Unmanned Aerial Vehicles* (notes p. 4). The 3D quadrotor's model is on
[the quadrotor model](quadrotor-model.md#the-3d-quadrotor).

## Planning in the flat output space

For a flat system the RRT can be run in the flat output space. It samples random flat outputs, for
the 3D quadrotor random $x$, $y$, $z$ and yaw, rather than whole configurations, and the extension
step becomes straightforward (notes p. 4, ≈58:57–1:01:16). The joined-up trajectory must still be
smooth enough at the tree's vertices, where segments meet. One way is to make each segment a
polynomial in time and constrain derivatives up to the needed order, such as the fourth, to match
at each vertex.

The videos in Lecture 5 show the approach on real vehicles (slides 2–6): Mellinger and Kumar's
quadrotors flying through thrown hoops, drone racing at the University of Zurich, a tail-sitter
drone from MIT, and the MIT drone flight of Lecture 3, planned with an RRT in the flat output space.
See [Lecture 5](05-differential-flatness.md#flatness-in-practice-the-videos).

## Lectures

- [Lecture 5 — Differential Flatness](05-differential-flatness.md): the motivation, the planar
  quadrotor proof, the general definition, the 3D quadrotor's flat outputs, the RRT in flat output
  space, and the videos.
- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): the equations of motion this rests on.
- [Lecture 3 — RRTs](03-rrts.md#rrts-in-action): the MIT drone video, first shown as an RRT and
  revisited in Lecture 5 as an RRT in flat output space.
- Lecture 6 (trajectory optimization) continues planning with dynamics. It is not yet in this
  knowledge base; see the [course map](course-map.md).
