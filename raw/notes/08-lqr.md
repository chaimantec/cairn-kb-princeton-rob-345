---
title: Lecture 8 — The Linear Quadratic Regulator (lecture notes)
lecture: 8
pages: 4
source_pdf: https://www.dropbox.com/scl/fi/j89tx4kp1skacdhuz918r/Lecture8_notes.pdf?rlkey=4gyqm6qumqutg1lzx83uuac4d&dl=0
numbering: PDF page N = page N; page 1 prints no number (pages 2–4 print 2–4). Only one equation carries a printed number: the first cost function on page 2, printed (1).
images: The two drawings are rendered as crops of the page and shown just above their descriptions (`notes-figure-1.jpg` and `notes-figure-2.jpg` in this lecture's image folder, numbered in order of appearance; the notes print no figure numbers or captions).
figure_audit: An independent reader checked both drawings, the page-1 pipeline and annotations, and the page-2 equations against the PDF; every display was also compared with the PDF's text layer in the parent. Fixed: in the page-3 sketch the circled entry is the third on the diagonal (the one for $z$), not the first, and the arrow points from it to the words "Crank this up"; in the page-1 sketch the dashed vertical line runs above, through and below the quadrotor.
---

# Lecture 8 — The Linear Quadratic Regulator: lecture notes

Full text of the course's written notes for Lecture 8 (A. Majumdar), transcribed from the PDF. Cite as "notes p. N" or "notes eq. (1)". The notes number exactly one equation, the first cost function on page 2; every other displayed equation is unnumbered and is cited by page. The two pasted drawings (a hand-drawn quadrotor sketch on page 1 and a typeset matrix sketch on page 3) carry no printed figure numbers or captions; they are numbered `notes-figure-1` and `notes-figure-2` in order of appearance and described in prose. Vectors are written with an overbar ($\bar{x}$, $\bar{u}$) and the shifted coordinates with a tilde ($\tilde{x}$, $\tilde{u}$), as in the notes.

[wiki page for this lecture](../../wiki/08-lqr.md) · [slides](../slides/08-lqr.md) · [transcript](../transcripts/08-lqr.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| Last lecture; Goal: linearize about a fixed point and design on the linear system | 1 | none numbered |
| Linear Quadratic Regulator: change of coordinates, cost functions, $Q$ and $R$ | 1–2 | (1) and unnumbered displays |
| The solution: algebraic Riccati equation, $K^\ast$, `lqr` | 2–3 | unnumbered displays |
| Interpretation of $S^\ast$, stability, how to choose $Q$ and $R$ | 3–4 | unnumbered displays |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 1, the fixed-point line is printed with the second subscript as an italic letter o, in the expression $f(\bar{x}_ 0, \bar{u}_ o)$, where the first subscript is a zero (the same $\bar{u}_ 0$ elsewhere in the notes is a zero).
- Page 1: "(e.g.; hover)" has a stray semicolon after "e.g.".
- Page 2: "Maybe we want to minimize derivations of the state from the desired state" reads "derivations" where "deviations" is meant (the next bullet says "deviations").
- Page 2: "A symmetric matrix $Q$ is positive definite if $\bar{x}^T Q \bar{x} \gt 0$, for all $\bar{x}$": at $\bar{x} = \bar{0}$ the quantity is zero, so the condition can only hold for all non-zero $\bar{x}$. The lecture states it that way, correcting itself: "for all z, or for all z not equal to zero. If you take z equal to 0, then this quantity is zero" (≈29:09).
- Pages 2 and 3: "Algebraic Riccatti Equation" and "Riccatti equation" (page 2, page 3) spell the name with a double t; the name is Riccati.

---

## Page 1

Header: "Intro to Robotics", "Lecture #8", "Instructor: A. Majumdar". No page number is printed on this page.

**Last Lecture:** Started discussion of feedback control.

(1) Some important ideas/definitions:

- Fixed point: $\dot{\bar{x}} = f(\bar{x}_ 0, \bar{u}_ o) = \bar{0}$.
- Global/Local asymptotic stability (for linear systems, local $\iff$ global)
- Stabilizability (saw that not all systems are stabilizable)
- Discussed proportional-derivative (PD) control. Saw how we could choose a controller of the form:

$$
\bar{u}(\bar{x}) = \bar{u}_ 0 + K(\bar{x} - \bar{x}_ 0)
$$

A small up-arrow under $K$ points to it from the label "Gain Matrix" (in quotation marks, small type): $K$ is the gain matrix.

to stabilize the planar quadrotor constrained to move in the y-direction.

![Notes drawing, p. 1 — the quadrotor constrained to move vertically, with a mark labelled y0 on a dashed vertical line](../images/08-lqr/notes-figure-1.jpg)

**Drawing (notes-figure-1).** A small hand-drawn sketch in black ink on white, with no caption, centred under the bullet. At the top is a quadrotor seen from the side: two loop-shaped propellers, one on each side of a dashed vertical line, above a long thin rectangular body. The dashed vertical line runs through the middle of the body, extends above the propellers and continues below. Just below the body a short thick horizontal bar crosses the line, with the handwritten label $y_0$ to its right. Further down, a dashed horizontal line extends to both sides of the vertical line and crosses it at a small T-shaped tick; its right end trails off in small dashes and dots. The vertical line continues, dashed, below the tick. The drawing has no other labels and no arrowheads.

(2) Ended lecture with a discussion of other considerations beyond stability (e.g., different performance criteria)

**Goal:** Explore (2) in more detail and complete discussion of control.

The techniques we will develop today will only be directly applicable to *linear* systems. For nonlinear systems, we can linearize our system about a fixed point (e.g.; hover) and apply the techniques we develop to the linearized system. The hope is then that the controller we obtain for the linearized system is also a "good" controller for the original nonlinear system.

The page then draws this as a left-to-right pipeline, with annotations:

$$
\dot{\bar{x}} = f(\bar{x}, \bar{u}) \approx \dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0) \rightarrow \text{Controller based on A, B}
$$

An underbrace sits under the expression $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ (the nonlinear system), and a second underbrace sits under "Controller based on A, B". An up-arrow rises from the first underbrace, and a vertical bar drops from the second. A long dashed line joins the foot of that bar to the foot of the up-arrow along the bottom, with the label "Apply on nonlinear system." under it. So the dashed arrow runs from the controller, back along the bottom, and up into the nonlinear system: the controller designed from the linearization $A$, $B$ is applied to the nonlinear system.

**Linear Quadratic Regulator (LQR):** We will develop a technique that *simultaneously* achieves two things:

(1) It stabilizes your (linear) system (assuming it is stabilizable)

(2) It optimizes a performance metric.

We start by assuming we have a linear system:

$$
\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)
$$

Two small up-arrows point from the labels under the display: the label $\in \mathbb{R}^n$ points up at $\bar{x}$, and the label $\in \mathbb{R}^m$ points up at $\bar{u}$. To the right of the display, a note: "(Here, $\bar{x}_ 0$ is assumed to be a fixed point.)"

---

## Page 2

Page number "2" at the top left.

To make things a bit more convenient, we do a change of coordinates: $\tilde{x} \triangleq \bar{x} - \bar{x}_ 0$, and $\tilde{u} \triangleq \bar{u} - \bar{u}_ 0$. Then $\dot{\tilde{x}} = \dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0) \Rightarrow$

$$
\dot{\tilde{x}} = A\tilde{x} + B\tilde{u}
$$

What would be a reasonable performance metric?

- Maybe we want to minimize derivations of the state from the desired state $\bar{x}_ 0$
- Maybe we want to minimize deviations from the nominal (i.e., reference) control input $\bar{u}_ 0$

Combining these, we could define:

$$
J\left(\tilde{x}(0)\right) \triangleq \int_ 0^\infty \left[ \underbrace{\tilde{x}(t)^T \tilde{x}(t)}_ {\substack{\text{scalar} \cr =\Vert\tilde{x}(t)\Vert^2}} + \underbrace{\tilde{u}(t)^T \tilde{u}(t)}_ {\substack{\text{scalar} \cr =\Vert\tilde{u}(t)\Vert^2}} \right] dt
\tag{1}
$$

Under the first underbrace the labels read "scalar" and, below it, $=\Vert\tilde{x}(t)\Vert^2$; under the second, "scalar" and, below it, $=\Vert\tilde{u}(t)\Vert^2$.

Here, $\tilde{x}(t)$ is $\tilde{x}$ at time $t$ assuming you started from $\tilde{x}(0)$.

In (1), we are penalizing all states (and control inputs) equally. Maybe some states/control inputs are more important than others.

$$
\underbrace{J\left(\tilde{x}(0)\right)}_ {\text{"Cost function"}} \triangleq \int_ 0^\infty \left[ \tilde{x}(t)^T Q \tilde{x}(t) + \tilde{u}(t)^T R \tilde{u}(t) \right] dt
$$

The underbrace is under $J(\tilde{x}(0))$ and is labelled "Cost function" (in quotation marks). Two up-arrows point from labels under the display: the label $n \times n$ points up at $Q$, and the label $m \times m$ points up at $R$.

$Q$ and $R$ are user defined matrices that specify relative importance of different states and control inputs. We will need to choose them to be *positive definite* and *symmetric*. (Recall: A symmetric matrix $Q$ is positive definite if $\bar{x}^T Q \bar{x} \gt 0$, for all $\bar{x}$. This is equivalent to the eigenvalues of $Q$ being positive.) In practice, we typically choose *diagonal* $Q$, $R$.

Our goal is to find some way to map states to control inputs in order to minimize the cost function. We won't go through the derivation (which is complicated), but will just talk about the solution.

It turns out that a *linear* controller:

$$
\tilde{u}(\tilde{x}) = K^\ast \tilde{x}
$$

gives us the solution. This is pretty magical! To obtain this controller, there are two steps:

**Step 1** Solve this *matrix equation* to find an $n \times n$ matrix $S$:

$$
0 = Q - SBR^{-1}B^T S + SA + A^T S
$$

Note that $S$ is the only unknown in this equation. This equation is called the *Algebraic Riccatti Equation*. Denote the solution by $S^\ast$.

**Step 2** Compute:

$$
K^\ast = -R^{-1}B^T S^\ast
$$

Our feedback controller is then:

$$
\tilde{u}(\tilde{x}) = K^\ast \tilde{x}
$$

$$
\Longrightarrow \bar{u}(\bar{x}) = \bar{u}_ 0 + K^\ast(\bar{x} - \bar{x}_ 0)
$$

---

## Page 3

Page number "3" at the top right.

Now, you might be wondering how to go about doing Step 1... That equation seems nasty. Thankfully, people figured out how to solve the Riccatti equation a while ago (using numerical techniques).

We can just use Python/Matlab:

$$
[K^\ast, S^\ast] = \mathit{lqr}(A, B, Q, R).
$$

This is super convenient! *Note*: Python/Matlab will also check if your system is stabilizable (and will complain if not). This is also convenient!

**Warning**: Matlab and Python use a slightly different convention than we do. In particular, they use controllers of the form $\tilde{u} = -K^\ast \tilde{x}$, instead of $\tilde{u} = K^\ast \tilde{x}$. So, the $K^\ast$ they return is the negation of what we want to make things work.

**Interpretation of $S^\ast$**: It turns out that the solution $S^\ast$ has a nice interpretation. It gives us the optimal cost:

$$
J^\ast\left(\tilde{x}(0)\right) = \tilde{x}(0)^T S^\ast \tilde{x}(0)
$$

where $J^\ast(\tilde{x}(0))$ is the cost incurred by applying $K^\ast \tilde{x}$ assuming we start from $\tilde{x}(0)$.

**Stability**: So far, we haven't said anything about the stability (we just talked about minimizing the cost function). It turns out that the feedback controller stabilizes (global asymptotic stability) the system to the fixed point $\tilde{x} = 0$ (i.e. $\bar{x} = \bar{x}_ 0$).

Thus, the system $\dot{\bar{x}} = A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)$ is stabilized to the fixed point $\bar{x}_ 0$, as desired. So, LQR does two things for us:

- It minimizes a (reasonable) performance metric (that tries to minimize deviations of $\bar{x}$ from $\bar{x}_ 0$ and $\bar{u}$ from $\bar{u}_ 0$).
- It results in a globally asymptotically stable closed-loop system:

$$
\dot{\tilde{x}} = A\tilde{x} + B\tilde{u} = A\tilde{x} + BK\tilde{x} = (A + BK)\tilde{x}.
$$

**How to choose $Q$ and $R$?** In theory, any (positive definite) choices of $Q$ and $R$ will make the system stable. In reality, things are more complicated:

(1) Our system is actually nonlinear

(2) There are imperfections in our model

(3) We need to sense the state perfectly in order to apply the controller.

So, we can choose/tune $Q$ and $R$ to get the behavior we want. This is a bit of an art... you will get to do a bit of this tuning in the assignment.

**Example**: Suppose you see that the system is not stabilizing the $z$ (height) well. What should you do?

![Notes drawing, p. 3 — the diagonal 12×12 matrix Q for the quadrotor, with its third diagonal entry circled and labelled "Crank this up"](../images/08-lqr/notes-figure-2.jpg)

**Drawing (notes-figure-2).** A small typeset sketch at the bottom of the page, with no caption. On the left, the expression $Q =$ with an up-arrow beneath $Q$ and, below the arrow, the label $12 \times 12$ and then "for quadrotor". To its right is a large pair of square brackets enclosing a matrix drawn only as a diagonal of twelve dots, written as four runs of three dots going down and to the right, with nothing off the diagonal. The first two dots are plain; the third diagonal entry is a dot inside a small circle. An arrow starts at that circled dot and points up and to the right at the words "Crank this up" above the matrix. Under the matrix is an underbrace labelled "Diagonal". The third entry of the state is $z$ (page 4 recalls the ordering), so the sketch marks the diagonal entry of $Q$ that penalizes $z$ as the one to raise. The page does not write this answer out in words.

---

## Page 4

Page number "4" at the top left.

Suppose you see that roll ($\phi$) is not being stabilized well. Then you can increase the $4^{\text{th}}$ element (on the diagonal) of $Q$. This places a higher penalty on roll.

(Recall: $\bar{x} = [x, y, z, \phi, \theta, \psi, \dot{x}, \dot{y}, \dot{z}, p, q, r]$.)

It takes some practice/tuning to get things right! But, usually, with some effort things work well! (See videos in slides.)
