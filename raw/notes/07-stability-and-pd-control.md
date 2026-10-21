---
title: Lecture 7 — Stability and PD Control (lecture notes)
lecture: 7
pages: 5
source_pdf: https://www.dropbox.com/scl/fi/70lppdz21xpgitd1ohhuo/Lecture7_notes.pdf?rlkey=bkk76zdh9ep0cvryzmpr34y7x&dl=0
numbering: PDF page N = page N; page 1 prints no number. Equations keep the notes' own numbers (1)–(19).
images: The three drawings are rendered as crops of the page and shown just above their descriptions (`notes-figure-1.jpg` to `notes-figure-3.jpg` in this lecture's image folder, numbered in order of appearance; the notes print no figure numbers or captions).
figure_audit: An independent reader checked the three drawings against the PDF at 600 dpi and at the embedded images' native resolution; every equation was compared with the PDF's text layer. Fixed: in both phase portraits, the direction of the outer curves (in the first all three run in to the origin; in the second one comes in and two leave the ball) and the number of spiral loops; the dashed circle in the second runs all the way round; the vertical axis in the third is solid below the body and dotted above it.
---

# Lecture 7 — Stability and PD Control: lecture notes

Full text of the course's written notes for Lecture 7 (A. Majumdar), transcribed from the PDF. Cite as "notes p. N" or "notes eq. (N)". The three pasted drawings (two hand-drawn phase portraits and a quadrotor figure) carry no printed figure numbers or captions; they are numbered `notes-figure-1` to `notes-figure-3` in order of appearance and described in prose. The notes' header line reads "Lecture #4", which is a printed slip (see below).

[wiki page for this lecture](../../wiki/07-stability-and-pd-control.md) · [slides](../slides/07-stability-and-pd-control.md) · [transcript](../transcripts/07-stability-and-pd-control.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| Today; 1. Fixed point (equilibrium point) | 1 | (1)–(3) |
| 2. Stability: closed-loop dynamics, Lyapunov stability, asymptotic stability | 1–2 | (4)–(6) |
| Global versus local asymptotic stability | 2–3 | (7) |
| 3. Stabilizability | 3–4 | (8)–(9) |
| 4. Proportional-derivative (PD) control | 4–5 | (10)–(19) |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 1, header line: "Lecture #4" is evidently "Lecture #7" (this is the Lecture 7 notes).
- Page 5, eq. (16): the proportional term is printed $\frac{k_p}{m}(y - y_0)$. With the dynamics of eq. (10), that controller would give $\frac{k_p}{m^2}\tilde{y}$ in the closed loop, not the $\frac{k_p}{m}\tilde{y}$ of eq. (17); eq. (13) and the lecture's board (≈1:12:16) have $k_p(y - y_0)$, with no $1/m$. The $1/m$ factors in eqs. (14), (15) and (17) are correct: they come from dividing the thrust by $m$ in eq. (10).
- Page 2, last paragraph: "What we have describe above" is evidently "What we have described above".
- Page 4, first paragraph: "in the next lecture.; see MAE 433/434" has a stray period before the semicolon.

---

## Page 1

Intro to Robotics — Lecture #4 — Instructor: A. Majumdar

**Today:** Discuss *what we want* from feedback control. At a high level, we want feedback control to make our system "stable". But what does that mean mathematically? We begin by trying to formalize this.

### 1. Fixed point (equilibrium point)

A **fixed point (a.k.a. equilibrium point)** for a system $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ is a state $\bar{x}_ 0$ such that:

$$
\dot{\bar{x}} = f(\bar{x}_ 0, \bar{u}_ 0) = 0 \text{ for some choice of } u_0. \tag{1}
$$

Recall that the hovering configuration for the quadrotor satisfied this. Intuitively, a fixed point $\bar{x}_ 0$ is a state that you remain at when you apply $\bar{u}_ 0$.

For the planar quadrotor, the fixed point associated with hover was given by:

$$
\bar{x}_ 0 = \begin{bmatrix} x_0 \cr y_0 \cr 0 \cr 0 \cr 0 \cr 0 \end{bmatrix} \text{ and } \bar{u}_ 0 = \begin{bmatrix} mg \cr 0 \end{bmatrix}. \tag{2}
$$

**Question:** Is it possible to have a fixed point of the form:

$$
\bar{x}_ 0 = \begin{bmatrix} x_0 \cr y_0 \cr 0 \cr \dot{x}_ 0 \cr \dot{y}_ 0 \cr \dot{\theta}_ 0 \end{bmatrix} \text{ with } \dot{x}_ 0, \dot{y}_ 0, \text{or } \dot{\theta}_ 0 \text{ being non-zero?} \tag{3}
$$

[Answer: **No!**. Convince yourself of this by writing down the equations of motion for the planar quadrotor.]

### 2. Stability

What are we trying to achieve with feedback? Suppose we come up with some feedback controller $\bar{u}(\bar{x})$. The **closed-loop system** is the system we obtain when we run this controller. The dynamics are then given by:

$$
\dot{\bar{x}} = f(\bar{x}, \bar{u}(\bar{x})) \triangleq f_{\text{cl}}(\bar{x}). \tag{4}
$$

These are known as the **closed-loop dynamics**. What properties would we like $f_{\text{cl}}$ to have?

→ We would like the closed-loop system to be "**stable**". But what does this mean?

There are actually many different definitions/flavors of stability. Here is a reasonable one.

---

## Page 2

**Stability in the sense of Lyapunov:** A system is said to be stable in the sense of Lyapunov (with respect to a fixed point $\bar{x}_ 0$) if for every $\epsilon \gt 0$, there exists a $\delta = \delta(\epsilon)$ such that:

$$
\Vert \bar{x}(0) - \bar{x}_ 0 \Vert \lt \delta \implies \Vert \bar{x}(t) - \bar{x}_ 0 \Vert \lt \epsilon, \quad \forall t \geq 0. \tag{5}
$$

**Asymptotic stability:** A system is asymptotically stable if (i) it is stable in the sense of Lyapunov and (ii) for every initial condition (i.e., initial state) $\bar{x}(0)$, the following holds:

$$
\lim_{t \to \infty} \Vert \bar{x}(t) - \bar{x}_ 0 \Vert = 0, \tag{6}
$$

where $\bar{x}(t)$ is the state at time $t$ when the system starts off at $\bar{x}(0)$ and $\bar{x}_ 0$ is the reference state (which is a fixed point). If this condition holds, we say that the system is asymptotically stable at $\bar{x}_ 0$.

The picture below illustrates this when the state is two-dimensional: $\bar{x} = [x_1, x_2]^T$.

![Notes drawing, p. 2 — global asymptotic stability: trajectories from every starting point spiral in to the fixed point](../images/07-stability-and-pd-control/notes-figure-1.jpg)

**Drawing (notes-figure-1).** A hand-drawn phase portrait in black ink on white, with no caption. A horizontal axis, labelled $x_1$ near its right end, which ends in a dot, and a vertical axis labelled $x_2$ at its top (no arrowhead; it ends in a small hook at the bottom) cross near the middle of the drawing. At the upper right, the handwritten label reads $\bar{x}$ equals a column of $x_1$ over $x_2$ in large square brackets. Around the crossing point is a tight spiral of four to five loops winding in to a dot at the origin. Three longer curves, each starting at a dot, run in towards it. One starts at the upper right and runs left over the top of the spiral, with an arrowhead near the $x_2$ axis pointing left, and then into the spiral. One starts at the top left and sweeps down the left side and round underneath the spiral, joining it at the bottom; a small arrowhead inside the spiral's lower part points left. One starts at the bottom right, rises with an arrowhead pointing up just below the $x_1$ axis, and curls inward. A stray dot sits at the upper left. All three outer curves run towards the origin, which is what the definition asks of every initial state.

What we have describe above is really **global** asymptotic stability. This is a very strong condition (and may be impossible to achieve in practice). For a quadrotor, this is asking for it to go to $\bar{x}_ 0$ no matter what the initial state is, e.g., $0.99 \times$ the speed of light!

---

## Page 3

Here is another (more reasonable) flavor of stability.

**Local asymptotic stability:** A system is locally asymptotically stable if (i) it is stable in the sense of Lyapunov, and (ii) for every initial condition $\bar{x}(0)$ with $\Vert \bar{x}(0) - \bar{x}_ 0 \Vert \leq R$ for some $R$ (i.e., every initial condition in some ball of radius $R$ around $\bar{x}_ 0$), we have:

$$
\lim_{t \to \infty} \Vert \bar{x}(t) - \bar{x}_ 0 \Vert = 0. \tag{7}
$$

![Notes drawing, p. 3 — local asymptotic stability: inside the dashed ball of radius R every trajectory spirals in; outside it some leave](../images/07-stability-and-pd-control/notes-figure-2.jpg)

**Drawing (notes-figure-2).** A second hand-drawn phase portrait, with no caption. The axes are as in the first drawing: $x_1$ near the right end of the horizontal axis, which ends in a dot, and $x_2$ at the top of the vertical axis. A dashed circle, unlabelled, is drawn all the way round the origin, with small ticks where the axes cross it; it stands for the ball of radius $R$ around $\bar{x}_ 0$. Inside it, a spiral of three to four loops winds in to the origin, with small arrowheads showing a counter-clockwise inward flow: one at the top pointing left, one on the left side pointing down, and one at the lower right. Outside the circle are three curves, each starting at a dot. One, a long nearly straight line, starts at the lower left, below the $x_1$ axis, runs right with an arrowhead pointing right, and enters the circle to join the spiral at the bottom. The other two start at dots just outside the circle on the right and run away from it as wavy curves: the upper one to the right and up, with its arrowhead pointing right, and the lower one to the right and down, with its arrowhead pointing right and down. Neither returns. Every state that starts inside the ball goes to the origin; from outside it, one trajectory comes in and two leave.

**Note:** Global asymptotic stability $\implies$ local asymptotic stability.

There are other reasonable flavors of stability too. For example, you could ask that trajectories remain bounded in some region (this is known as *invariance*).

We won't prove this here, but it turns out that for **linear** systems $\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)$, local asymptotic stability implies global asymptotic stability! So these two notions are the same for linear systems. This is *not* true for nonlinear systems.

### 3. Stabilizability

We have described what we want to achieve with feedback (i.e., stability). But can we actually achieve it?

Consider the following system:

$$
\dot{\bar{x}} = \frac{d}{dt} \begin{bmatrix} x_1 \cr x_2 \end{bmatrix} = \begin{bmatrix} x_1 \cr x_2 + u \end{bmatrix}. \tag{8}
$$

Here, the control input $u$ can only affect $x_2$. Moreover, the dynamics of $x_1$ and $x_2$ are completely decoupled. So the control input has no effect on $x_1$. The dynamics of $x_1$ are unstable; hence, no matter what controller you choose, this system cannot be stabilized.

**Stabilizability (w.r.t. a fixed point $\bar{x}_ 0$):** Any initial state can be asymptotically driven to $\bar{x}_ 0$ by choosing the control inputs $\bar{u}$ appropriately, i.e., for any initial state $\bar{x}(0)$,

$$
\lim_{t \to \infty} \Vert \bar{x}(t) - \bar{x}_ 0 \Vert = 0, \tag{9}
$$

by choosing appropriate control inputs.

As the example above shows, not every system is stabilizable (not even all linear systems). But, it turns out that we can *check* stabilizability of linear systems $\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)$ by

---

## Page 4

checking eigenvalue conditions on $A, B$. [We won't describe these conditions here, but I'll say a little bit more about this in the next lecture.; see MAE 433/434 for a thorough treatment.]

The question now is how to actually design a controller that achieves (asymptotic) stability (for linear systems), assuming the system is stabilizable.

### 4. Proportional-Derivative (PD) Control

Consider the planar quadrotor constrained to move **only in the $y$ direction**. This is a 1-DoF system.

![Notes drawing, p. 4 — the planar quadrotor, level, with thrusts F1 and F2 and the X and Y axes](../images/07-stability-and-pd-control/notes-figure-3.jpg)

**Drawing (notes-figure-3).** A colour drawing of the planar quadrotor in side view, inside a thin light-grey rectangle. The quadrotor is level: a black central body with a red dome and a red dot on top, a grey L-shaped arm running out horizontally to each side and bending up to a black motor block, and a grey shaded propeller ellipse above each motor block. Above the left propeller is a short black upward arrow labelled $F_1$, and above the right propeller a short black upward arrow labelled $F_2$. A vertical line runs from a corner labelled "O" below the body up through the red dot and the dome to a label "Y" at its top: it is solid from O up to the body, has a solid arrowhead just above the red dome, and is dotted from there up to "Y". From O a black horizontal arrow runs to the right, labelled "X"; the "O" label sits just below and left of the corner. So O is the origin, the vertical axis is Y and the horizontal axis is X. The thin rectangle frames the body and arms only.

The dynamics are given by:

$$
\ddot{y} = \frac{u_1}{m} - g. \tag{10}
$$

The state is:

$$
\bar{x} = \begin{bmatrix} y \cr \dot{y} \end{bmatrix} \tag{11}
$$

and recall that the control input $u_1$ is the total thrust produced by the propellers.

Suppose we want to stabilize the system to:

$$
\bar{x}_ 0 = \begin{bmatrix} y_0 \cr 0 \end{bmatrix}. \tag{12}
$$

With $u_0 = mg$, this is a fixed point (since $\ddot{y} = mg/m - g = 0$).

How should we choose $u(\bar{x})$ to stabilize the system to $\bar{x}_ 0$? Here is one possibility: choose

$$
u(\bar{x}) \triangleq u_0 + k_p(y - y_0). \tag{13}
$$

The closed-loop system is then:

$$
\ddot{y} = \frac{mg}{m} - g + \frac{k_p}{m}(y - y_0) = \frac{k_p(y - y_0)}{m}, \tag{14}
$$

where $k_p \lt 0$ is a constant that we choose.

Now define $\tilde{y} \triangleq y - y_0$. Then $\dot{\tilde{y}} = \dot{y}$ and $\ddot{\tilde{y}} = \ddot{y}$. Thus:

$$
\ddot{\tilde{y}} = \frac{k_p}{m}(y - y_0) = \frac{k_p}{m}\tilde{y}. \tag{15}
$$

What does this system remind you of?

→ Spring-mass system!

Would this controller work (i.e., stabilize the system)? (Not quite)

---

## Page 5

Here is another option:

$$
u(\bar{x}) = u_0 + \frac{k_p}{m}(y - y_0) + k_d\dot{y}, \tag{16}
$$

where $k_d \lt 0$ is another constant that we can choose.

We then have:

$$
\ddot{\tilde{y}} = \frac{k_p}{m}\tilde{y} + \frac{k_d}{m}\dot{\tilde{y}}. \tag{17}
$$

Now what does this system remind you of?

→ Spring-mass-damper!

This is an example of **proportional-derivative (PD) control**. Such controllers are extremely popular and effective in practice.

Some terminology:

$k_p$ : "proportional gain",

$k_d$ : "derivative gain".

Note that the controller is of the form:

$$
\bar{u}(\bar{x}) = \bar{u}_ 0 + K(\bar{x} - \bar{x}_ 0) \tag{18}
$$

$$
\phantom{\bar{u}(\bar{x})} = \bar{u}_ 0 + [k_p, k_d] \begin{bmatrix} y - y_0 \cr \dot{y} \end{bmatrix}. \tag{19}
$$

The matrix $K$ is referred to as the **gain matrix**.

Also notice that for this example, any choice of $k_p, k_d \lt 0$ leads to (global) asymptotic stability. In general, things will not be so easy!

How can we choose $K$ in general? Maybe we want to ensure asymptotic stability while also optimizing some performance metric?

→ We will do this in the next lecture!
