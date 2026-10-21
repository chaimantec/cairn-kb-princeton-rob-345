---
title: Lecture 5 — Differential Flatness (lecture notes)
lecture: 5
pages: 4
source_pdf: https://www.dropbox.com/scl/fi/d0g09pk1opfkwdw7udmsi/Lecture5_notes.pdf?rlkey=l1sriwzrnb499bsbcyo3cylm9&dl=0
numbering: PDF page N = page N; page 1 prints no number. Equations keep the notes' own numbers (1)–(4), which are on page 3 only.
images: to be filled in by the parent
---

# Lecture 5 — Differential Flatness: lecture notes

Full text of the course's written notes for Lecture 5 (A. Majumdar), transcribed from the PDF. Cite as "notes p. N" or "notes eq. (N)". The four pasted hand-drawn figures carry no printed captions and are described in prose, since the descriptions are the only representation of them here. Two displayed equations on page 2 (the definition) are unnumbered, as is the flat-output vector on page 3.

[wiki page for this lecture](../../wiki/05-differential-flatness.md) · [slides](../slides/05-differential-flatness.md) · [transcript](../transcripts/05-differential-flatness.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| Goal; the RRT extension problem; wheeled-robot example (unnumbered) | 1 | none |
| Differentially flat systems: definition, main idea, pipeline figure | 2 | unnumbered displays only |
| Flat outputs of the 3D quadrotor; theorem; planar quadrotor example and proof | 3 | (1)–(4) |
| Further notes and reference | 4 | none |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 3, first line: "it turns out the at the system" is evidently "it turns out that the system".
- Page 3, proof: "for $t \in [0, t]$" in the last sentence of the paragraph after eq. (4) is evidently $[0, T]$, as in the preceding paragraph.
- Page 3, last paragraph before "Notes": "control inputs require to execute" is evidently "control inputs required to execute".

---

## Page 1

Intro to Robotics — Lecture #5 — Instructor: A. Majumdar

**Goal for these lectures:** Understand how to take into account the dynamics of our robot during motion planning. Our discussion of motion planning (via graph search or the RRT algorithm) assumed that any path produced by a planning algorithm is physically executable. As we discussed last time, this is not true in general.

Let's consider the RRT algorithm. We have some current tree at iteration $k$ of the algorithm:

**Figure (p. 1, drawing):** a 2D picture of an RRT in the plane. A tree of small black dots joined by black line segments sits in the lower left and centre, its root being the larger black dot near the middle left; branches fan out from it up, left, right and down, with two branches reaching the upper left. Three circular obstacles drawn with grey diagonal hatching lie in the upper half and the right half: one at the top centre-left, one at the top right, and one lower right of centre. In the upper right of the tree is a short red dashed segment from a tree vertex (black dot) to a red dot labelled $\bar{q}_s$; from the red dot $\bar{q}_s$ a thin dotted grey line continues up and to the right to a second red dot labelled $\bar{q}_{\text{rand}}$. No other labels are present.

We sample a random configuration $\bar{q}_{\text{rand}}$, find the closest vertex in the tree, and then perform an *extension* operation. Our extension operation from the last lecture was very simple. We just move in the direction of $\bar{q}_{\text{rand}}$ (by some distance $d$). For a system that has dynamics, it may not be possible to just follow a straight line in the configuration space to get from one configuration to another.

**Example:** Wheeled robot/Car

**Figure (p. 1, drawing):** the label "Top view" at the top centre. Below it, two identical rectangles side by side, each a car seen from above: an outlined rectangle with two short black wheel blocks on each of its left and right sides (four wheels). A black arrow above each car points straight up. The left car is labelled $A$ underneath and the right car is labelled $B$ underneath. The two cars are at the same height with the same orientation, $B$ being displaced sideways to the right of $A$.

Suppose we want to go through configuration $A$ to configuration $B$. We can't just move sideways. We have to do some potentially complicated maneuver to get from $A$ to $B$. How do we find such a maneuver?

**Previous lecture:** Discussed *equations of motion*: differential equations that describe robot dynamics.

---

## Page 2

Today: Start thinking about how we can do motion planning in a way that obeys the equations of motion for a given robotic system. Today, we will discuss a special class of systems known as **differentially flat systems**. This is a class of systems with special properties that makes it easy to plan motions while obeying the dynamics of the robot. There are many examples of differentially flat systems: car, car with trailer, planar quadrotor, and the full 3D quadrotor (among others).

For this discussion, we will ignore obstacles and just focus on doing the "extension" operation for the RRT, i.e., given A and B, we will try to find a path that is *dynamically feasible* (It won't quite be possible to do this, but we will come close to doing this...). In the lecture slides, I have videos showing how differential flatness can be combined with RRTs.

**Definition** (differential flatness): Suppose the dynamics of our system are given by:

$$
\dot{\bar{x}} = f(\bar{x}, \bar{u}), \qquad \bar{x} \in \mathbb{R}^n, \qquad \bar{u} \in \mathbb{R}^m.
$$

The system is said to be *differentially flat* if there exists a function $\alpha$ such that:

$$
\underbrace{\bar{z}}_{\text{Flat outputs}} = \alpha(\bar{x}, \bar{u}, \dot{\bar{u}}, \ddot{\bar{u}}, \ldots, \underbrace{\bar{u}^{(p)}}_{p\text{th time derivative}})
$$

(In the notes the two annotations sit under the formula with small upward arrows: "Flat outputs" under $\bar{z}$ and "$p^{\text{th}}$ time derivative" under $\bar{u}^{(p)}$.)

and we can write the solution of the nonlinear system as:

$$
\bar{x} = \beta(\bar{z}, \dot{\bar{z}}, \ddot{\bar{z}}, \ldots, \bar{z}^{(q)})
$$

$$
\bar{u} = \gamma(\bar{z}, \dot{\bar{z}}, \ddot{\bar{z}}, \ldots, \bar{z}^{(q)})
$$

Why is this useful?

**Main idea:** For a differentially flat system, we can plan a trajectory in the flat output space and then *easily* figure out what control inputs we need to apply in order to execute this flat output trajectory (by using the function $\gamma$). We can also easily figure out the resulting trajectory in the state space. Moreover, *any* (sufficiently smooth) trajectory in the flat output space can be executed.

So, here is how things work in practice:

**Figure (p. 2, drawing):** a pipeline of three plots and one labelled arrow, left to right, each plot an orange curve ending in an orange dot.

1. Left plot: axes with the vertical axis labelled $\bar{z}$ and the horizontal axis labelled $t$. A smooth S-shaped orange curve rises from a low starting value, steepens, then flattens near the top, ending in an orange dot. Beneath the plot is a brace and the caption "We specify this desired trajectory of flat outputs: i.e., we specify $\bar{z}(t)$".
2. Between the first plot and the other two: a horizontal black arrow pointing right. Above it the words "Differential Flatness" (on two lines), below it "(via $\beta$, $\gamma$)".
3. Middle plot: axes with the vertical axis labelled $\bar{u}$ and the horizontal axis $t$. An orange curve starts at a positive value, falls below the horizontal axis, reaches a minimum, then rises back above the axis and ends in an orange dot. Beneath it, a brace and the caption "Control inputs we need to apply to achieve desired flat output trajectory".
4. Right plot, immediately to the right of the middle plot and in the same style: axes with vertical axis labelled $\bar{x}$ and horizontal axis $t$. The orange curve rises to a peak, falls steeply to a deep trough below the $t$ axis (and below its starting value), rises again and ends in an orange dot at the upper right. Beneath it, a brace and the caption "Resulting state trajectory".

The only arrow is the one labelled "Differential Flatness (via $\beta$, $\gamma$)", which points from the $\bar{z}$ plot to the pair of plots on the right; none is drawn between the $\bar{u}$ and $\bar{x}$ plots.

---

## Page 3

For the 3D quadrotor, it turns out the at the system is differentially flat with flat outputs

$$
\bar{z} = \begin{bmatrix} x \cr y \cr z \cr \psi \end{bmatrix}
$$

In the notes, a brace on the right of the vector spans its first three entries and is labelled "COM position", and a second brace beside the last entry $\psi$ is labelled "yaw".

**Theorem:** # of flat outputs = # of control inputs. (We won't prove this, but it's good to know.)

**Example:** Differential Flatness of Planar Quadrotor

$$
\ddot{x} = -\frac{(F_1 + F_2)}{m} \sin(\theta)
\tag{1}
$$

$$
\ddot{y} = \frac{(F_1 + F_2)}{m} \cos(\theta) - g
\tag{2}
$$

$$
\ddot{\theta} = \frac{(F_2 - F_1)L}{I}
\tag{3}
$$

**Figure (p. 3, drawing):** to the right of the equations, a side view of the planar quadrotor, tilted: a light-grey arm outlined in black running up to the right, with a black motor block and a grey propeller disc at each end (the left one lower, the right one higher), and a red dome on the black central body (with a tiny red dot on it). A horizontal dashed line runs to the right from the central body; a second dashed line, an extension of the arm, rises from the body to the right; the angle between them is marked $\theta$ near their right-hand ends. Below the drawing, the label "$(x, y, \theta)$" in bold. No force arrows, $L$ or frame axes are drawn in this figure.

Under the figure: States: $[x, y, \theta, \dot{x}, \dot{y}, \dot{\theta}]^T$

Control inputs: $F_1, F_2$ (propeller thrusts).

**Claim:** This system is differentially flat with flat outputs:

$$
\bar{z} = \begin{bmatrix} x \cr y \end{bmatrix}.
$$

**Proof:** Observe from (1) and (2) that:

$$
\begin{aligned}
\tan(\theta) &= \frac{(F_1 + F_2) \sin(\theta)}{(F_1 + F_2) \cos(\theta)} = \frac{-m\ddot{x}}{m\ddot{y} + mg} = \frac{-\ddot{x}}{\ddot{y} + g} \cr
\Rightarrow \theta &= \arctan\left(\frac{-\ddot{x}}{\ddot{y} + g}\right)
\end{aligned}
\tag{4}
$$

Thus, given a trajectory for the flat outputs, i.e.: given $x(t)$ and $y(t)$ for $t \in [0, T]$. We can reconstruct the state from the flat output trajectory (as long as the flat output trajectory is sufficiently smooth; we need to compute $\ddot{x}$ and $\ddot{y}$).

Now, given (4), we can differentiate this twice (with respect to time) to obtain $\ddot{\theta}$. We can then combine (3) with (1) or (2) to obtain two linear equations for $F_1$ and $F_2$, which are easily solved to obtain the required control inputs $F_1(t), F_2(t), t \in [0, t]$. Note that these will depend on $\ddot{\theta}$, which in turn depends on $\frac{d^4 x(t)}{dt^4}$ and $\frac{d^4 y(t)}{dt^4}$ since we differentiate (4) twice to obtain ($\ddot{\theta}$).

Don't let the technical details throw you off: this is *extremely powerful*! We can specify *any* (sufficiently smooth) trajectory in the flat output space and then *easily* compute the control inputs require to execute this flat output trajectory. We can also easily compute the trajectory of the full state.

Notes:

- We only get to specify the trajectory in the flat output space. The full state trajectory might end up being a bit wacky... but the flat outputs will behave as desired.

---

## Page 4

- For a differentially flat system, you can implement RRT in the flat output space. The extension operation is then straightforward.
- For some new robotic system, how can we figure out if it is differentially flat? Unfortunately, there is no general technique. It requires some cleverness on your part. The realization that the 3D quadrotor is differentially flat led to some pretty amazing results (see slides for videos).

See Section 16.2.6 of the reference below if you're curious how to prove differential flatness of the 3D quadrotor:

C. Powers, D. Mellinger, and V. Kumar, "Quadrotor Kinematics and Dynamics", Handbook of Unmanned Aerial Vehicles.
