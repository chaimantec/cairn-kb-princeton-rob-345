---
title: Lecture 9 — Optical Flow (lecture notes)
lecture: 9
pages: 5
source_pdf: https://www.dropbox.com/scl/fi/az52bpcoly0ophkzc7sqj/Lecture9_notes.pdf?rlkey=ijs39xouvybcpqcv3cluaapvu&dl=0
numbering: PDF page N = page N; page 1 prints no number (pages 2–5 print 2–5). Five equations carry printed numbers (1)–(5): (1), (2) and (3) on page 2, (4) on page 3, (5) on page 4. The page-2 and page-3 displays between them, the page-4 matrix display and the page-5 displays are unnumbered. The four pasted drawings (pages 1, 2, 3 and 5) carry no printed figure numbers or captions; they are numbered notes-figure-1 to notes-figure-4 in order of appearance.
images: The four drawings are rendered as crops of the page and shown just above their descriptions (`notes-figure-1.jpg` to `notes-figure-4.jpg` in this lecture's image folder, numbered in order of appearance; the notes print no figure numbers or captions).
figure_audit: An independent reader checked the four drawings and the page-4 matrix display against the PDF at up to 600 dpi; every display was also compared with the PDF's text layer in the parent. Drawings 1 and 4 and the matrix display agree. Tightened: the angles of drawing 3's arrows. The reader took the displacement label of drawing 2 for "(u, x)"; the parent's crop shows "(u, v)", its v drawn as in "x+v", so only the "(x+u, x+v)" label is listed as a slip.
---

# Lecture 9 — Optical Flow: lecture notes

Full text of the course's written notes for Lecture 9 (A. Majumdar), transcribed from the PDF. Cite as "notes p. N" or "notes eq. (N)". The notes number five equations: the brightness-constancy condition (1), its Taylor expansion (2), the scalar flow constraint (3), the perpendicularity condition (4) and the least-squares solution (5). Every other displayed equation is unnumbered and is cited by page. The four pasted drawings are hand-drawn images with no printed numbers or captions: they are numbered `notes-figure-1` to `notes-figure-4` in order of appearance and described in prose. Vectors that are solved for are written with an overbar ($\bar{d}$, $\bar{b}$), as in the notes; the matrix is $A$ and the image gradient is $\nabla I$. The header line on page 1 reads "Lecture #18" although this is Lecture 9 (see Printed slips); pages 2–5 carry no header line, only the page number.

[wiki page for this lecture](../../wiki/09-optical-flow.md) · [slides](../slides/09-optical-flow.md) · [transcript](../transcripts/09-optical-flow.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| 1. Optical Flow - Setting | 1 | none |
| 2. Optical Flow - Key Assumptions & Analysis (brightness constancy, Taylor expansion, aperture problem) | 1–3 | (1)–(3) on page 2, (4) on page 3 |
| 3. Lucas-Kanade Optical Flow (spatial coherence, least squares) | 4 | (5) |
| 4. Challenges for Lucas-Kanade Optical Flow ($A^T A$, low texture, edges, violated assumptions) | 5 | unnumbered displays |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 1, header line: "Lecture #18" for what is Lecture 9 (the only place the notes print a lecture number; pages 2–5 have no header line).
- Page 5: "determininat" for "determinant".
- Page 2, in the hand-drawn figure (notes-figure-2): the label of the displaced point reads "(x+u, x+v)", with an x where y is meant (the x is drawn as in "x+u", the y of "(x, y)" has a descender). The displacement label "(u, v)" is not a slip: its v is drawn like the v of "x+v", with a small crossing stroke that can be mistaken for an x.

The equations were checked by substitution: expanding $I(x+u,y+v,t+1)$ by (2) and using (1) gives $I_x u + I_y v + I_t \approx 0$, which is (3); adding a vector $[u',v']^T$ with (4) to a solution of (3), as on page 3, leaves the left side of (3) unchanged. No equation slip was found.

---

## Page 1

Header: "Intro to Robotics", "Lecture #18", "Instructor: A. Majumdar". No page number is printed on this page.

**1. Optical Flow - Setting**

Optical Flow: Apparent motion of objects (see **slides** for motivation)

![Notes drawing, p. 1 — three objects in a frame, each a solid circle with an arrow to a dashed circle where it has moved](../images/09-optical-flow/notes-figure-1.jpg)

**Notes drawing 1 (p. 1).** A hand-drawn rectangle (a frame, slightly skewed, thick black outline, no label) containing three small circles drawn with a solid outline, each joined by an arrow to a dashed circle of the same size, the arrow's head at the dashed circle. Upper left: a solid circle with a short arrow pointing up and to the right to a dashed circle. Upper right: a solid circle with an arrow pointing down and to the right to a dashed circle. Lower middle: a solid circle at the right of the pair with an arrow pointing down and to the left to a dashed circle. So the solid circles are positions at one time, the dashed circles are where the same objects are afterwards, and the arrows show each object's motion: up-right, down-right and down-left respectively. No other text or labels.

We will work with grayscale images:

$$
I(x, y, t)
$$

with annotations printed under the expression: a small up-arrow under "I" labelled "Int"; an underbrace under "x , y" labelled "pixel loc"; a small up-arrow under "t" labelled "time idx". Beside it, at the right: "Int ⇒ Intensity" and "pixel loc ⇒ Pixel Location".

Goal: Estimate pixel motion from image $I(x,y,t)$ to $I(x,y,t+1)$, with an underbrace under $I(x,y,t+1)$ labelled "next frame in video".

⇒ We will estimate motion of each pixel separately.

**2. Optical Flow - Key Assumptions & Analysis**

Two main assumptions:

(1) Color and Intensity constancy: Point (object) at time $t+1$ looks the same as at time $t$.

(2) Small motion: Points do not move very far from time $t$ to $t+1$

---

## Page 2

Page number "2" at the top left.

![Notes drawing, p. 2 — a point at (x, y) displaced by (u, v) to a dashed circle](../images/09-optical-flow/notes-figure-2.jpg)

**Notes drawing 2 (p. 2).** A second hand-drawn rectangle (thick black outline, no caption). Inside, at the lower left, a small solid circle labelled "(x, y)" beneath it. An arrow points from this circle up and to the right to a small dashed circle, labelled "(x+u, x+v)" at its upper right (as printed, with x in the second entry). To the right of the arrow, in the middle of the frame, is the text "Displacement:" with "(u, v)" underneath it (the v drawn with a small crossing stroke, as in "x+v"). The arrow therefore represents the displacement from the point at $(x, y)$ to the point at $(x+u, y+v)$.

Brightness constancy assumption corresponds to:

$$
I(x, y, t) = I(x + u, y + v, t + 1) \tag{1}
$$

Let's Taylor expand the RHS: (margin note, in a box at the right: "[**Note**: if small motion assumption is satisfied, this is a good approximation]")

$$
I(x + u, y + v, t + 1) \approx I(x, y, t) + I_x u + I_y v + I_t \tag{2}
$$

Notation:

- $I_x$: Image intensity derivative along x
- $I_y$: Image intensity derivative along y
- $I_t$: Difference across frames (i.e. derivative w.r.t. time)

Thus, from (2), we have:

$$
\underbrace{I(x + u, y + v, t + 1) - I(x, y, t)}_ {= 0 \text{ [from (1)]}} \approx I_x u + I_y v + I_t
$$

The underbrace sits under the left-hand difference and is labelled "= 0 [from (1)]".

$$
\Rightarrow \quad I_x u + I_y v + I_t \approx 0
$$

$$
\Rightarrow \quad (\nabla_{x,y} I) \cdot [u, v]^T + I_t = 0 \tag{3}
$$

A label at the right of equation (3): "[Scalar Equation]".

---

## Page 3

Page number "3" at the top right.

Recall: we are trying to recover $(u, v)$.

⇒ How many unknowns : 2

⇒ How many equations : 1

We don't have enough information to recover $(u, v)$.

In particular, we can only identify motion along the gradient $\nabla I$. We cannot identify motion perpendicular to the gradient.

![Notes drawing, p. 3 — the gradient, a flow vector and a second flow vector perpendicular to the gradient](../images/09-optical-flow/notes-figure-3.jpg)

**Notes drawing 3 (p. 3).** A small hand-drawn vector sketch at the left of the page, with no caption. Three arrows leave one black dot. The top arrow points up and to the right and is labelled with the symbol $\nabla I$ at its tip. The middle arrow points to the right, almost horizontal and very slightly downward, and is labelled with $[u, v]^T$. The bottom arrow points down and to the right, at about 40 degrees below the horizontal, and is labelled with $[u', v']^T$. A dashed line runs from the dot towards the upper left, roughly continuing the bottom arrow's line back through the dot. A small right-angle mark (a little square) sits between the dashed line and the $\nabla I$ arrow, marking that $\nabla I$ is perpendicular to that line and so to $[u', v']^T$. A faint grey stray mark sits above the letter I of $\nabla I$.

Suppose $[u', v']^T$ is perpendicular to $\nabla I$.

$$
\Longrightarrow \nabla I \cdot [u', v']^T = 0 \tag{4}
$$

Then,

$$
\nabla I \cdot [u + u', v + v']^T + I_t = \underbrace{I_t + \nabla I \cdot [u, v]^T}_ {= 0 \text{ [from (3)]}} + \underbrace{\nabla I \cdot [u', v']^T}_ {= 0 \text{ [from (4)]}}
$$

The first underbrace sits under $I_t + \nabla I \cdot [u,v]^T$ and the second under $\nabla I \cdot [u',v']^T$, labelled as shown.

Hence, if $[u, v]$ satisfies Eq. (3), so does $[u + u', v + v']$.

⇒ This is the "aperture problem" [See slides]

We need to somehow resolve this ambiguity. This will require an additional assumption.

---

## Page 4

Page number "4" at the top left.

**3. Lucas-Kanade Optical Flow**

**Note**: This work dates from ~ 1981.

**Assumption.** "Spatial Coherence": A pixel's neighbors move together, i.e. have the same $[u, v]$.

Consider a 5x5 window centered on a particular pixel. This gives us 25 equations:

$$
\underbrace{\begin{bmatrix} I_x(p_1) & I_y(p_1) \cr I_x(p_2) & I_y(p_2) \cr \vdots & \vdots \cr I_x(p_{25}) & I_y(p_{25}) \end{bmatrix}}_ {\triangleq A} \underbrace{\begin{bmatrix} u \cr v \end{bmatrix}}_ {\triangleq \bar{d}} = - \underbrace{\begin{bmatrix} I_t(p_1) \cr I_t(p_2) \cr \vdots \cr I_t(p_{25}) \end{bmatrix}}_ {\triangleq \bar{b}}
$$

(The notes print the middle rows as columns of dots.) Each underbrace carries the label printed in it: $\triangleq A$, $\triangleq \bar{d}$ and $\triangleq \bar{b}$.

$$
\Longrightarrow \underbrace{A}_ {25 \times 2} \underbrace{\bar{d}}_ {2 \times 1} = \underbrace{\bar{b}}_ {25 \times 1}
$$

This is overdetermined, ergo we find a least-squares solution for $\bar{d}^\ast$ ($\bar{d}^\ast$ that minimizes $\Vert A\bar{d} - \bar{b}\Vert_ 2^2$).

$$
\bar{d}^\ast = (A^T A)^{-1} A^T \bar{b} \tag{5}
$$

Equation (5) is boxed. Margin note at the right: "(Can also use numpy to solve the least squares problem, as in Assignment 1)".

When can we solve (5)?

⇒ We need $A^T A$ to be invertible. Let's look at $A^T A$ a bit more carefully...

---

## Page 5

Page number "5" at the top right.

$$
A^T A = \underbrace{\begin{bmatrix} \Sigma I_x I_x & \Sigma I_x I_y \cr \Sigma I_x I_y & \Sigma I_y I_y \end{bmatrix}}_ {2 \times 2}
$$

Margin note at the right: "Summations are over pixels in window, i.e. 25 pixels for a 5x5 window".

We can compute the determininat of $A^T A$ and see when it is zero (this is precisely when it is *not* invertible).

$$
\det(A^T A) = (\Sigma I_x I_x)(\Sigma I_y I_y) - (\Sigma I_x I_y)^2
$$

**4. Challenges for Lucas-Kanade Optical Flow**

One case: low-texture region. Here, the gradients $I_x, I_y \approx 0$ for all pixels in the window...

Another case: Edge. All of the gradients corresponding to the different pixels are the same.

![Notes drawing, p. 5 — an edge with the same gradient arrow at each of four pixels along it](../images/09-optical-flow/notes-figure-4.jpg)

**Notes drawing 4 (p. 5).** A small hand-drawn sketch below the "Edge" sentence, with no caption: a thick black line sloping down gently from the upper left to the lower right (drawn as a rope-like or hatched bar), with four short arrows standing on it at roughly equal spacing, all of the same direction. Each arrow points up (slightly tilted to the right, roughly perpendicular to the line). These are the same-direction gradients at the different pixels along the edge.

Another case where this approach will break down is when our assumptions don't hold:

(1) Color or intensity constancy is violated

(2) Small motion violation

(3) Spatial coherence violation

A curly brace groups these three items, with a margin note at the right: "Think about implications for robot. What should robot's environments look like?"

**Note**: See video in slides

There are many, many improvements to the approach I have described. Hopefully, thinking about optical flow has made you realize how challenging sensing is and the need to account for imperfect sensing.
