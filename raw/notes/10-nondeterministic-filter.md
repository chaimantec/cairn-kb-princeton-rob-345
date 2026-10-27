---
title: Lecture 10 — Nondeterministic Filter (lecture notes)
lecture: 10
pages: 6
source_pdf: https://www.dropbox.com/scl/fi/ccgwqi9i2wr1fzcc690dd/Lecture10_notes.pdf?rlkey=cffu8ofmveu1jaokpqdl0zhzg&dl=0
numbering: PDF page N = page N; page 1 prints no number (pages 2–6 print 2–6). The notes print no equation numbers; the "(1)" and "(2)" on page 1 are items of a list, not equations. Every display is unnumbered and cited by page. The nine pasted drawings (pages 1, 2, 4 and 5) carry no printed figure numbers or captions; they are numbered notes-figure-1 to notes-figure-9 in order of appearance.
images: The nine drawings are rendered as crops of the page and shown just above their descriptions (`notes-figure-1.jpg` to `notes-figure-9.jpg` in this lecture's image folder, numbered in order of appearance; the notes print no figure numbers or captions).
figure_audit: An independent reader checked the nine drawings against the PDF at 400–1500 dpi. Drawings 3 and 8 agree. Corrected or added: the tick marks of drawings 1 and 2 and where drawing 2 puts "s"; drawing 4's label and the ending of each of its four arrows (open arrowheads); drawing 6's dots and outlines; drawing 5's connector. Drawing 7's arrow most plausibly points left, at the state, with low confidence. The parent read drawing 5's label "f(x̂₀)" and drawing 9's words from the renders.
---

# Lecture 10 — Nondeterministic Filter: lecture notes

Full text of the course's written notes for Lecture 10 (A. Majumdar), transcribed from the PDF. The course posts no slide deck for this lecture, which was given at the board, so these notes are the only written record. Cite as "notes p. N". The notes print no equation numbers: the "(1)" and "(2)" on page 1 number the two things the robot should be able to do (estimate its state; construct a map), and every displayed equation is unnumbered and cited by page. The nine pasted drawings are hand-drawn images with no printed numbers or captions: they are numbered `notes-figure-1` to `notes-figure-9` in order of appearance and described in prose. Underlining in the notes is not reproduced; where a phrase is underlined for emphasis it is noted in brackets or left as plain text. Notation, as the PDF's fonts show it: vectors (the state, the measurement, the control input) carry an overbar ($\bar{x}$, $\bar{z}$, $\bar{u}$); the state space $\mathcal{X}$ and the measurement space $\mathcal{Z}$ are calligraphic capitals; the sets of possible states (the estimates) are italic capital $X$ with a hat ($\hat{X}_ 0$, $\hat{X}_ t$); the dynamics is $f$ and the sensor mapping is $h$. The header line on page 1 reads "Lecture #11" although this is Lecture 10 (see Printed slips); pages 2–6 carry no header line, only the page number.

[wiki page for this lecture](../../wiki/10-nondeterministic-filter.md) · [transcript](../transcripts/10-nondeterministic-filter.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| 1. Introduction (the two assumptions of planning and control; estimating the state, building a map) | 1 | none |
| 2. Motivation (a point robot with distance sensors) | 1–2 | $\bar{x}$ on page 1 and $\bar{x}_ 0$ on page 2, unnumbered |
| 3. State Estimation for Robots - Single Step (measurement, sensor mapping, preimage) | 2–3 | unnumbered displays on pages 2 and 3 |
| 4. State Estimation for Robots - Idealized Multi-Step Case (dynamics, $f(\hat{X}_ 0)$, $\hat{X}_ 1$) | 3–4 | unnumbered displays on pages 3 and 4 |
| 5. Non-deterministic Filter (the general step at time $t$) | 4–5 | unnumbered display on page 4 |
| 6. State Estimation in Robotics - Realistic Multi-Step Case (uncertainty in dynamics and measurements) | 5 | none |
| 7. Concluding Notes | 6 | none |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 1, header line: "Lecture #11" for what is Lecture 10 (the only place the notes print a lecture number; pages 2–6 have no header line).
- Page 4, in drawing 5: the label of the pear-shaped set reads "f(x̂₀)", its x drawn as two arcs like this hand's lowercase x and smaller than the capital X of "X̂₀" beside it, for the set $f(\hat{X}_ 0)$.
- Page 4: the prose before the final set of the idealized case reads "our new estimate $\hat{x}_ 1$" with a lowercase $x$, while the display just below and everywhere else the estimate is the set $\hat{X}_ 1$ with a capital $X$.
- Page 5, in drawing 9: "accont" for "account". The strokes show a, c, c, a round letter, n, t; whether the missing letter is the u or the o cannot be settled.

The displays were checked by substitution: the page-4 step $\hat{X}_ 1 = f(\hat{X}_ 0) \cap h^{-1}(\bar{z}_ 1)$ is the general step 3 on page 4 $\hat{X}_ t = f(\hat{X}_ {t-1}) \cap h^{-1}(\bar{z}_ t)$ at $t = 1$, and the preimage display for $\bar{z}_ 1$ is the page-3 preimage definition at $\bar{z} = \bar{z}_ 1$. No equation slip was found.

---

## Page 1

Header: "Intro to Robotics", "Lecture #11", "Instructor: A. Majumdar". No page number is printed on this page.

**1. Introduction**

Our discussion of motion planning and feedback control made two *big* assumptions (the word "big" is italic and underlined):

The robot is equipped with sensors that allow it to **perfectly estimate its state $\bar{x}(t)$ at any given time.** (Bullet, bold as printed.)

The robot knows exactly where all of the obstacles in the environment are (i.e. it has a *map* of the environment). (Bullet.)

In reality, neither assumption is completely valid. As we saw in the last lecture on optical flow, estimating the robot's state is a non-trivial challenge. In the next few lectures, we will develop approaches that allow a robot to:

(1) Estimate its state (given some noisy / imperfect sensor measurements);

(2) Construct a map of some environment.

**Note**: Towards the end of this module, we will see that we can actually do (1) and (2) simultaneously!

The classic reference for the material that we will cover is the book "Probabilistic Robotics" (one of the reference textbooks for this course).

**2. Motivation**

Let's start with a *simple example* - imagine that we have a 2DOF (point) robot, with state:

$$
\bar{x} = \begin{bmatrix} x \cr y \end{bmatrix}
$$

Suppose that the robot is able to measure its distance to the origin using a sensor.

![Notes drawing, p. 1 — a dashed circle about the origin with the robot as a dot on it and the radius r marked](../images/10-nondeterministic-filter/notes-figure-1.jpg)

**Notes drawing 1 (p. 1).** A hand-drawn pair of coordinate axes, the horizontal axis labelled "X" at its right end (a small cross that may be a capital or a lowercase x) and the vertical axis labelled "Y" at its top (a capital, written in script). A dashed circle is centred on the origin, where the axes cross, with small tick marks where it meets the axes. On the circle, in the upper right quadrant, is one solid black dot (the robot). A short dashed segment (three or four dashes) runs from the origin to this dot, and beside it, inside the circle, is the label "r" (lowercase, as in the "r" of the text). So the circle is the set of positions at distance $r$ from the origin, and the dot is one point on it. A few faint stray marks lie to the upper right of the dot (not legible, not part of the drawing). No other labels.

Given a sensor measurement $r$, what can the robot conclude about its state?

→ It just knows that it is in a state $\bar{x}$ such that

$$
\sqrt{x^2 + y^2} = r
$$

(It's on a circle of radius $r$).

---

## Page 2

Page number "2" at the top left.

Now, suppose that the robot has another sensor that corresponds to distance from another point:

$$
\bar{x}_ 0 = \begin{bmatrix} 1 \cr 1 \end{bmatrix}
$$

![Notes drawing, p. 2 — two dashed circles, one about (0,0) with radius r and one about (1,1) with radius s, crossing each other](../images/10-nondeterministic-filter/notes-figure-2.jpg)

**Notes drawing 2 (p. 2).** Hand-drawn axes (horizontal and vertical, unlabelled, with a small tick on the negative side of each) and two dashed circles. The first circle is centred on the origin, marked by a solid dot labelled "(0,0)" at its lower left. From the origin a solid arrow runs down and to the right, curving slightly, to the lower right part of this circle, with its head on the circle; to the left of the arrow's lower part is the label "r". The second circle is centred up and to the right, at a solid dot labelled "(1,1)" just below and to the right of the dot. From this dot a solid arrow runs up and to the right to the upper right part of the second circle, its head on the circle; up and to the left of the arrow, beside its upper part, is the label "s". Both arrows run from a circle's centre to the circle. The two circles overlap and cross each other at two points: one in the upper part, near the vertical axis, and one to the right of the origin near the horizontal axis. So each label ($r$ or $s$) names a circle's radius, the measured distance of the sensor at that centre.

The robot can conclude that it is somewhere on the intersection of the two circles. Unfortunately, even this does not completely specify its state. (Printed at the right of the drawing.)

Let us now assume that there is a third sensor:

![Notes drawing, p. 2 — three dashed circles with a dot at each centre and one larger dot at the point they have in common](../images/10-nondeterministic-filter/notes-figure-3.jpg)

**Notes drawing 3 (p. 2).** Three dashed circles of about the same size, one at the upper right, one at the left and one at the bottom right, arranged around a common point. Each circle has a small solid dot at its centre. At the middle of the arrangement, where all three circles meet, is one larger solid black dot. No labels. There are no arrows. The three circles pass through this one point, so the intersection of the three is that single dot. (A few stray white or grey marks at the top edge of the crop are artefacts of the pasted image.)

The robot knows that it is located at the intersection of the three circles. (Printed at the right of the drawing.)

*How can we make this more general?* (italic, underlined)

**3. State Estimation for Robots - Single Step**

Let $\bar{z}$ be a measurement (a.k.a. observation) corresponding to sensor measurements. (The words "measurement" and "observation" are underlined as printed.)

So, in the example above with three sensors, $\bar{z} \in \mathbb{R}^3$, because there are three measurements, each of which are scalar distances.

We assume that we have a model of the sensors:

$$
\bar{z} = h(\bar{x})
$$

**Note**: This is sometimes referred to as a 'sensor mapping' or 'sensor function' (printed at the right of the display).

---

## Page 3

Page number "3" at the top right.

This tells us what measurements will be made at any given state. [Think about what $h$ is for the example above.]

*Definition*: The preimage of the sensor mapping is defined as:

$$
h^{-1}(\bar{z}) = \lbrace \bar{x} \in \mathcal{X} \mid h(\bar{x}) = \bar{z} \rbrace
$$

with two annotations printed under the display: an underbrace under $h^{-1}(\bar{z})$ labelled "preimage of meas $\bar{z}$", and a small up-arrow under $\bar{x} \in \mathcal{X}$ labelled "state space" (the arrow points at the $\mathcal{X}$).

The preimage associated with measurement $\bar{z}$ can be thought of in words as "the set of all states $\bar{x} \in \mathcal{X}$ that are consistent with having received measurement $\bar{z}$." (The phrase from "consistent" to the end is underlined.)

**Math Note**: The function $h : \mathcal{X} \mapsto \mathcal{Z}$ is not generally invertible; as examples, think of the above cases with 1 or 2 distance sensors. Therefore, $h^{-1}(\bar{z})$ is *not* the formal, mathematical inverse of the function $h(\cdot)$ in general. This is just a standard (if potentially confusing) notation. One may think of it as "h-reverse;" that is, to go in the reverse direction (from observations to (observation-consistent) states).

In the simple example we started with, we are *really* computing the preimage of the sensor mapping. In the case that the preimage has exactly one element (i.e. is singleton), we have uniquely determined the state. **Note**: This corresponds to the function $h(\cdot)$ being ('locally') invertible.

So far, though, we have ignored the actual *dynamics* of the robot...

**4. State Estimation for Robots - Idealized Multi-Step Case**

For state estimation, it will be useful to consider a discrete-time model of the dynamics:

$$
\left\lbrace \bar{x}_ {t+1} = f(\bar{x}_ t, \bar{u}_ t), \quad \text{[OR } \bar{x}_ {t+1} = f(\bar{x}_ t) \text{]} \right\rbrace
$$

with the aside "[We will ignore control inputs for now]" printed below the display and two small arrows pointing up from it: one at $\bar{u}_ t$ in the first form, one at the second form, $f(\bar{x}_ t)$. (The opening brace is drawn larger than the closing one.)

This could be obtained by starting with a continuous-time model and discretizing it, or somehow obtaining a discrete-time model at the outset.

Now, suppose that we have an estimate of what the state will be at time 0. Denote this by $\hat{X}_ 0 \subseteq \mathcal{X}$. [Again, $\mathcal{X}$ is the state space].

Using our dynamics model, we can figure out the set of states the system may end up in at time step $t = 1$ (we can do this at least in principle, computational considerations aside).

---

## Page 4

Page number "4" at the top left.

![Notes drawing, p. 4 — a blob labelled X-hat-0 with four dashed arrows to a second blob, the set f of X-hat-0](../images/10-nondeterministic-filter/notes-figure-4.jpg)

**Notes drawing 4 (p. 4).** Two closed hand-drawn blobs side by side. The left one is a bean or egg shape, with the label $\hat{X}_ 0$ at its lower left (a large bold capital X with a caret at its upper left and a subscript 0 drawn as a small loop at its lower right). The right one is a larger, rounder blob that overlaps the left blob's right edge slightly, so the two outlines cross. Above them, centred over the gap, is the label "f" (a script f with a looped stem). Four dashed arrows run from left to right, one above another, each starting at a point inside or at the edge of the left blob and ending in an open ">" arrowhead. The top arrow's head is just outside the right blob's left edge, followed by one solid dot inside the right blob. The second arrow's head and its dot are both just outside the right blob's left edge. The third arrow's head is inside the right blob, with a dashed continuation to a dot well inside it. The bottom arrow, whose shaft turns from dashed to a solid curve near its end, has its head inside the right blob and no dot. So four sample states of $\hat{X}_ 0$ are each carried by $f$ to a point of the right blob, which is the set $f(\hat{X}_ 0)$ defined below.

$$
f(\hat{X}_ 0) \triangleq \left\lbrace \bar{x} \in \mathcal{X} \mid \exists \bar{x}_ 0 \in \hat{X}_ 0 \text{ s.t. } f(\bar{x}_ 0) = \bar{x} \right\rbrace
$$

Now, at time step $t = 1$, we also receive a sensor measurement $\bar{z}_ 1$ (in general, $\bar{z}_ t$ will denote the sensor measurement at time $t$).

We can compute the preimage corresponding to $\bar{z}_ 1$:

$$
h^{-1}(\bar{z}_ 1) = \lbrace \bar{x} \in \mathcal{X} \mid h(\bar{x}) = \bar{z}_ 1 \rbrace
$$

![Notes drawing, p. 4 — the blob X-hat-0, the blob f of X-hat-0, the dashed blob h-inverse of z-1 and their hatched overlap](../images/10-nondeterministic-filter/notes-figure-5.jpg)

**Notes drawing 5 (p. 4).** Two groups. At the left, a closed bean-shaped blob with the label $\hat{X}_ 0$ at its lower left (a large bold capital X with a caret above it and subscript 0), joined to the blob by a faint dotted stroke. At the right, a solid-outlined pear-shaped blob labelled "f(x̂₀)" below its lower left: the letter inside the parentheses is drawn as two arcs, as this hand writes a lowercase x, and is smaller and thinner than the capital X of the left-hand label, so the label reads with a lowercase x although the set is $f(\hat{X}_ 0)$ (see Printed slips). Overlapping the pear's right side is an oval drawn with a dashed outline, labelled "h⁻¹($\bar{z}_ 1$)" to its right (an h with a superscript −1, then "(", a z with an overbar and subscript 1, then ")"). The part where the pear and the dashed oval overlap is filled with dense diagonal hatching. A curved arrow starts below and to the right of the pear, curves up and to the left, and ends with a small open head at the lower end of the hatched region; it has no label of its own. So the hatched overlap is the intersection of $f(\hat{X}_ 0)$ and $h^{-1}(\bar{z}_ 1)$, which the next sentence of the text calls the new estimate.

And our new estimate $\hat{x}_ 1$ will include our knowledge of the dynamics and the new measurement. Specifically, we can conclude that the robot must be somewhere in the intersection of $f(\hat{X}_ 0)$ and the preimage of the sensor measurement $h^{-1}(\bar{z}_ 1)$, i.e. the set:

$$
\hat{X}_ 1 = f(\hat{X}_ 0) \cap h^{-1}(\bar{z}_ 1)
$$

**5. Non-deterministic Filter**

Now we can repeat this iteratively......

![Notes drawing, p. 4 — the sets X-hat-1, f of X-hat-1, the preimage of z-2 and their hatched overlap, which is X-hat-2](../images/10-nondeterministic-filter/notes-figure-6.jpg)

**Notes drawing 6 (p. 4).** A wide pasted image, mostly blank white, with the drawing in its left-centre part. At the far left, the label $\hat{X}_ 1$ (X with a caret above it and subscript 1), and to its right a small closed blob with a heavy stroke at its top left and scribbled loops inside (the set $\hat{X}_ 1$). From this small blob, dashed lines (two short "=" shaped groups and several longer dashes) run to the right into a taller, narrow pear-shaped blob with a solid outline, where they end in three solid dots, as in drawing 4; they have no arrowheads. The narrow blob is labelled below it $f(\hat{X}_ 1)$. At the upper right, overlapping the upper part of this narrow blob, is a second, rounder blob, also with a solid outline, labelled to its right "h⁻¹($\bar{z}_ 2$)" (z with an overbar and subscript 2). The overlap of the two blobs is filled with dense hatching. Above, the label $\hat{X}_ 2$ (X with a caret, subscript 2) at the top, with a curved arrow whose tail is at the label and which curves down and to the left to end with its head at the top of the hatched overlap. So $\hat{X}_ 2$ is the hatched intersection of $f(\hat{X}_ 1)$ and $h^{-1}(\bar{z}_ 2)$, and the dashes and dots show $f$ carrying points of $\hat{X}_ 1$ into the narrow blob.

In general, at any time-step $t$, we do the following steps:

$$
\begin{aligned}
&1.\ f(\hat{X}_ {t-1}) && \leftarrow \text{Dynamics Update} \cr
&2.\ h^{-1}(\bar{z}_ t) && \leftarrow \text{Measurement Update} \cr
&3.\ \hat{X}_ t = f(\hat{X}_ {t-1}) \cap h^{-1}(\bar{z}_ t) && \leftarrow \text{Fuse information from 1. and 2.}
\end{aligned}
$$

(The three steps are printed in a list inside a large left brace, each with an arrow pointing left at its annotation: step 1 is the "Dynamics Update", step 2 the "Measurement Update", and step 3 "Fuse information from 1. and 2.".)

---

## Page 5

Page number "5" at the top right.

This is called the "*Non-Deterministic Filter*"

[**Exercise**: Think about how this works with control inputs.]

**6. State Estimation in Robotics - Realistic Multi-Step Case**

So far, we have assumed a perfect model of the dynamics and sensor. In reality, there may be some uncertainty. [What might be a cause of this uncertainty?]

**Uncertainty in the dynamics**: we may not know precisely which state the robot will end up in from a given state.

![Notes drawing, p. 5 — a state with an arrow to a blob, showing that one state can lead to a set of states](../images/10-nondeterministic-filter/notes-figure-7.jpg)

**Notes drawing 7 (p. 5).** A small drawing at the right of the text. At the left, the label $\bar{x}_ t$ (an x with a bar over it and a subscript t). Just to its right is a thick, wedge-shaped stroke that rises from a lower-left tip to a sharp upper point, with a thin line continuing from it to the right and a short separate dash above that line: read as drawn, this is a "<" arrowhead pointing left, at $\bar{x}_ t$, though the strokes are rough and a reading with the thick stroke as the tail cannot be excluded. Then come three short dashes and, at the right, a closed teardrop-shaped blob (rounded at the bottom, pointed at the top) with several black dots drawn inside it. The text beside it says what the drawing shows: from the state $\bar{x}_ t$ the robot may end up not in one state but anywhere in a set of states, the dots in the blob. A faint stray mark lies above the label.

**Uncertainty in the measurements**: we may not know exactly which measurement will be received at any given state.

Going back to our example, maybe instead of a precise distance measurement, we get some measurement that is $\pm\epsilon$ away from the (true) distance.

![Notes drawing, p. 5 — two concentric dashed circles around a dot with the handwritten note that the state is somewhere in this ring](../images/10-nondeterministic-filter/notes-figure-8.jpg)

**Notes drawing 8 (p. 5).** At the left, two concentric dashed circles (an inner and an outer, close together) around one small solid dot at their common centre. The ring between the two circles is the annulus. At the right is handwritten text in two lines: "We know that the state is somewhere" and, below it, "in this ring / annulus." (the slash and period as drawn). An arrow runs from the start of the text, at the right, curving to the left and pointing at the ring, its head touching the gap between the two dashed circles on the upper right of the circles. The ring is the set of states consistent with a distance measurement that is only known up to $\pm\epsilon$.

These kinds of uncertainty models are called "*non-deterministic*" models of uncertainty. It is relatively straightforward conceptually to extend the non-deterministic filter to account for non-deterministic uncertainty.

![Notes drawing, p. 5 — the non-deterministic filter step with uncertainty: X-hat-t, the larger f of X-hat-t, the preimage of z-t and their hatched overlap, each set labelled in words](../images/10-nondeterministic-filter/notes-figure-9.jpg)

**Notes drawing 9 (p. 5).** A wide hand-drawn figure with handwritten words. At the left, a label $\hat{X}_ t$ (X with a caret, subscript t) touching a small closed blob. In the middle, a taller, narrow oval blob with a solid outline, labelled below it $f(\hat{X}_ t)$, with a wavy underbrace beneath the label. At the upper right of this oval, overlapping its top, is a dashed circle; the overlap is filled with dense hatching. To the right of the dashed circle is the label "h⁻¹($\bar{z}_ t$)" (z with an overbar, subscript t), followed by a curly brace "}" and the handwritten text "Set of states I could have" and, below it, "received $\bar{z}_ t$ from." (the h of "have" is closed into a loop, so the word can look like "kare"). Below the whole figure, under the wavy underbrace, is the handwritten text "Set of states I could end up in if I start from $\hat{X}_ t$," (a small "⌋" mark follows) and on the next line "taking into account uncertainty in dynamics.", with "account" written "accont", one letter short (see Printed slips). So the underbrace says that $f(\hat{X}_ t)$ is the set of states reachable from $\hat{X}_ t$ when the dynamics are uncertain, and the brace at the right says that $h^{-1}(\bar{z}_ t)$ is the set of states from which $\bar{z}_ t$ could have been received. There are no arrows.

[**Exercise**: Write out the formal non-deterministic filter with non-deterministic uncertainty]

---

## Page 6

Page number "6" at the top left.

**7. Concluding Notes**

*Notes*:

⇒ In practice, the nondeterministic filter isn't really utilized directly

⇒ Its primary challenge is *computational*. Representing and computing the sets $f(\hat{X}_ {t-1})$ and $h^{-1}(\bar{z}_ t)$ can be computationally challenging.

⇒ Specifying a nondeterministic model of uncertainty can be challenging in practice.

⇒ The filter can be very conservative. It is reasoning about worst-case events (because it keeps track of *every* possible state that the system can end up in). In practice, we may want to work with a *probabilistic* model of uncertainty.

Despite these drawbacks, the nondeterministic filter forms a solid conceptual basis for techniques that *are* used in practice.

Next Lecture: Probabilistic methods for state estimation.

**Note**: Please make sure to review basic concepts in probability. (I will do a brief review too.)

**Note**: There is a good, quick review in Chapter 2.2 of *Probabilistic Robotics*.

⇒ In particular, Bayes' rule will be of fundamental importance.
