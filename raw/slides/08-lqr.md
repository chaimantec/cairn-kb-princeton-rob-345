---
title: Lecture 8 — Linear Quadratic Regulator (slide deck)
lecture: 8
slides: 13
source_pdf: https://www.dropbox.com/scl/fi/vg2cumj4cs2kuqb3942fg/Lecture8_slides.pdf?rlkey=uthhn11zguqubxdgo0zrv5viv&dl=0
numbering: PDF page N = Slide N for all 13 pages (1:1). Pages 1, 2 and 9 print no number; their labels (1, 2, 9) are inferred from position. Pages 3–8 and 10–13 print their own number.
images: 4 slides are rendered and shown under their headings (6, 7, 11, 12). Not rendered — the title page (1); slides 2–5, identical to Lecture 7's slides 2, 4, 5 and 6 (its slide 6 is rendered in that lecture's slide file); slides 8 and 9, whose drawing is the Lecture 7 notes' quadrotor drawing (rendered there) and whose equations are transcribed below; the section divider (10); and slide 13, a video title card whose text is transcribed. The notes' two drawings are rendered in the notes file.
figure_audit: An independent reader checked slides 6, 7, 8, 9, 11, 12 and 13 against the PDF. Nothing described is absent from the page; slides 6, 7, 9 and 13 agree, including the direction of every arrow on slides 6 and 7. Fixed: the vertical axis of slide 8's drawing (solid through the body, dotted above the arrowhead); on slide 11 the inset's layout, the second quadrotor and the "UZH" on the sign; on slide 12 how the aeroplane is mounted. Renders of slide 7 and both notes drawings were also checked in the parent.
---

# Lecture 8 — Linear Quadratic Regulator: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 8 deck (title "Lecture 8: Linear Quadratic Regulator", speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Figures are described in prose since the KB is read as text. The deck is short: slides 2–5 repeat slides from Lecture 7, slide 6 draws the sense-think-act loop, slides 7–9 recall Lecture 7's stability and PD-control material, slide 10 introduces LQR, and slides 11–13 are single frames of three videos. The LQR formulation itself (cost function, gain matrix, Riccati equation) is not on the slides; it is in the separate written lecture notes.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 13 pages, and the last printed number is 13. Slides 1, 2 and 9 print no number in the corner, so their labels are inferred from position (title page, outline page, and the page between printed 8 and printed 10).

Companion pages: [wiki page for this lecture](../../wiki/08-lqr.md) · [transcript](../transcripts/08-lqr.md) · [lecture notes](../notes/08-lqr.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Course outline: where "Feedback control" sits |
| 3 | Challenges with motion planning: uncertainty |
| 4–5 | Feedback control for hovering: the vector field of control inputs; the feedback control law |
| 6 | Sense-think-act loop |
| 7–9 | Last lecture: stability, PD control |
| 10 | Section divider: Linear quadratic regulator (LQR) |
| 11–13 | LQR videos: quadrotor, airplane (prop-hang), humanoid |

---

## Slide 1 — Lecture 8: Linear Quadratic Regulator

Title page. Title in blue in a rounded light-grey box: "Lecture 8: Linear Quadratic Regulator". Below it, a faded wide photograph of a small quadrotor seen from the front: black propellers on the left and right arms, a circuit board in the centre carrying a vertical board with a camera and lens, red and black wires. Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred from position).

## Slide 2 — Course outline (Planning and control)

This slide is identical to Lecture 7's slide 2 (the course outline, "Feedback control" in bold). No title bar and no number printed (label inferred from position). Three rounded cards side by side. The left card is in full colour; the other two are faded.

- Left card, heading in blue "Planning and control". Below it a blue-tinted image of a car on a road with a drawn curved lane path and a second car ahead. Below, four lines: "Geometric planning", "Robot dynamics", "Planning with dynamics", "**Feedback control**" (bold, the current topic).
- Middle card (faded), heading "Localization, mapping", an image of a forest with a coloured point-cloud overlay; lines "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card (faded), heading "Robot learning", an image of a humanoid robot and a person in a kitchen; lines "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

## Slide 3 — Challenges with motion planning

This slide is identical to Lecture 7's slide 4 ("Challenges with motion planning", the uncertainty slide). Title bar: "Challenges with motion planning" (blue). Printed number 3.

Left column, three text blocks with some words in blue: "**Imperfect dynamics** model" (the words "Imperfect dynamics" in blue, "model" black); "External **disturbances** (e.g., wind)" ("disturbances" in blue); "**Imperfect** knowledge of robot **state** or **map**" ("Imperfect", "state" and "map" in blue). Right column: a stock photograph of a green road sign, tilted, reading "Uncertainty" in white, on two wooden posts against a blue sky with clouds.

## Slide 4 — Feedback control for hovering

This slide is identical to Lecture 7's slide 5 ("Feedback control for hovering", the "vector field" goal). Title bar: "Feedback control for hovering" (blue). Printed number 4.

The middle of the slide shows five copies of the same side-view drawing of a planar quadrotor (a grey horizontal body with a red dome and red dot at the centre, a bent arm on each side ending in a grey motor block with a shaded grey propeller ellipse above it). Each drone has a blue arrow at each propeller, drawn straight up from the propeller, except the centre one. They are arranged like the points of a cross:

- Centre: one drone drawn in full black and dark grey (the others are faded light grey), level, with no arrows on it.
- Top: a faded drone tilted, with its right end higher than its left, by roughly 20 degrees (counter-clockwise on the page). Its two blue arrows point vertically up (not perpendicular to the body); the left arrow is about twice as long as the right arrow.
- Left: a faded level drone to the left of the centre one. Its left arrow is long and its right arrow is short (about half as long).
- Right: a faded level drone to the right of the centre one. Its left arrow is short and its right arrow is long (the mirror of the left drone).
- Bottom: a faded level drone below the centre one. Its two arrows are equal in length and of medium size: shorter than the long arrows of the left and right drones, longer than their short ones.

Below, in a rounded grey box: "**Goal:** define this “vector field”" ("**Goal:**" bold blue, "define this" black, "“vector field”" blue), and on the next line in blue "At every state: what control input to apply?".

## Slide 5 — Feedback control for hovering

This slide is identical to Lecture 7's slide 6 (the same figure with the "feedback control law" caption). Title bar: "Feedback control for hovering" (blue). Printed number 5.

The same figure as slide 4: five copies of the planar quadrotor, with the centre one in full black and the other four (top tilted, left, right, bottom) faded, and the same blue upward arrows at each propeller (none on the centre drone; top: left arrow about twice the right; left: left arrow long, right short; right: left short, right long; bottom: two equal arrows). The box below now reads: "This is called a **feedback control law** (or “controller”): $\bar{u}(\bar{x})$" ("feedback control law" and "“controller”" in blue).

## Slide 6 — Sense-think-act

![Slide 6 — Sense-think-act](../images/08-lqr/slide-6.png)

Title bar: "Sense-think-act" (blue). Printed number 6. The slide is drawn in vector graphics (boxes, arrows and text), with no raster image. It is a three-box loop in bold black sans-serif text:

- Three rounded light-blue boxes sit in a row across the middle of the slide. Left box: "**Sense robot state** $\bar{x}(t)$ **at time** $t$". Middle box: "**Compare state with desired state** $\bar{x}_ 0$". Right box: "**Choose control input** $\bar{u}$ **to apply based on** $\bar{x}(t)$ **and** $\bar{x}_ 0$".
- A solid bright-blue block arrow points right from the left box to the middle box, and another points right from the middle box to the right box. So the order is sense, then compare, then choose the input.
- A bright-blue elbow arrow leaves the underside of the right box, runs straight down, then left along a long horizontal bar under all three boxes, and turns up into an arrowhead that points up at the underside of the left box. So the loop closes from the right box back to the left box: the cycle repeats.
- Under the elbow arrow, centred, the word "**Repeat**" (bold, underlined), and below it the line "[For quadrotors, this cycle happens at ~500 Hz for hovering.]".

The slide is not one of the Lecture 7 notes' drawings.

## Slide 7 — Last lecture

![Slide 7 — Last lecture](../images/08-lqr/slide-7.png)

Title bar: "Last lecture" (blue). Printed number 7.

Left, three lines of text: "Discussed what we want from feedback: **stability**" ("what we want" in blue, "**stability**" bold blue), then, indented, "Global / local attractivity", "Lyapunov stability", "Global / local asymptotic stability".

Right, a phase-portrait drawing: a horizontal axis with an arrowhead at both ends, labelled $x_1$ at its right end, and a vertical axis with an arrowhead at both ends, labelled $x_2$ at its top, crossing at the origin. A single thick black curve winds in a spiral around the origin. Its outer end is at the lower left of the picture, below the horizontal axis and left of the vertical axis, with no arrowhead there; from there it runs up and to the left of the axes, over the top, down the right side, under, and round again for about two and a half loops, clockwise on the page, each loop smaller than the last. At the centre it ends in a small solid arrowhead right next to the origin, so the curve runs from the outside in towards the origin, not away from it. It is a clean vector drawing, not the hand-drawn spirals of the Lecture 7 notes' drawings (notes-figure-1 and notes-figure-2, which show the same idea, trajectories spiralling in to a fixed point).

## Slide 8 — Last lecture

Title bar: "Last lecture" (blue). Printed number 8.

Centred above the figure, "Example of **proportional-derivative (PD) control**" ("proportional-derivative (PD) control" in blue).

Left, the planar-quadrotor drawing that appears as notes-figure-3 of the Lecture 7 notes: a side view of a level quadrotor with a black central body, red dome and red dot, grey arms bending up to black motor blocks and a shaded grey propeller ellipse over each. A thin black upward arrow rises from above each propeller, labelled $F_1$ (left) and $F_2$ (right). A vertical line, labelled "Y" at its top, rises from a point labelled "O" below the body through the red dot: it is solid from O up through the body, has an arrowhead above the dome, and is dotted from there up to the Y label. A horizontal arrow from O to the right is labelled "X". A thin light-grey rectangle frames the body and arms.

Right, in a rounded grey box, two equations:

$$
\text{EoM:}\quad \ddot{y} = \frac{u_1}{m} - g
$$

$$
u(\bar{x}) = u_0 + \frac{k_p}{m}(y - y_0) + k_d \dot{y}
$$

Here $y$ is the height, $y_0$ the desired height, $u_1$ the thrust input, $m$ the mass and $g$ gravity. The controller is transcribed as printed: the proportional term is divided by $m$ and the derivative term $k_d \dot{y}$ is not. Below the box, two lines: the symbol $k_p$ followed by a colon and the quoted words proportional gain, and the symbol $k_d$ followed by a colon and the quoted words derivative gain.

## Slide 9 — Last lecture

Title bar: "Last lecture" (blue). No number printed (label inferred from position, between printed 8 and printed 10).

Everything on slide 8 is repeated unchanged (the subtitle, the quadrotor drawing, the grey box with the equation of motion and $u(\bar{x})$, with the same printed $\frac{k_p}{m}$ and $k_d \dot{y}$). The two lines for $k_p$ and $k_d$ are gone, and in their place, below the figure, is a displayed equation, with a rounded grey highlight around its last part:

$$
\bar{u}(\bar{x}) = \bar{u}_ 0 + [k_p, k_d] \begin{bmatrix} y - y_0 \cr \dot{y} \end{bmatrix} = \bar{u}_ 0 + K(\bar{x} - \bar{x}_ 0)
$$

The highlighted part is the right-hand side $\bar{u}_ 0 + K(\bar{x} - \bar{x}_ 0)$. At the bottom right, in blue and black: "General form of PD control" ("General form" in blue).

## Slide 10 — Linear quadratic regulator (LQR)

Section divider. An empty light-grey title bar, no title text. Below the middle of the slide, a rounded light-grey box with "Linear quadratic regulator (LQR)" in blue, and under it, in black, "“Optimal” control for linear dynamics". Printed number 10.

## Slide 11 — LQR on quadrotor

![Slide 11 — LQR on quadrotor](../images/08-lqr/slide-11.jpg)

Title bar: "LQR on quadrotor" (blue). Printed number 11 (partly covered by the video frame's lower edge, but legible). The slide shows a single frame of a video that was played in the lecture; the PDF holds only that frame. Below the frame, the underlined link https://www.youtube.com/watch?v=8OVsJNgNfa0.

The frame is a wide photograph of an indoor room: a white wall with a dark door at the right, ceiling lights, a few small cameras mounted high on the wall and a shelf with equipment at upper right, and a floor covered with a grey-and-green play-mat printed with roads, partly rippled. A white sign on the wall reads "University of Zurich" with a seal at its left and a small "UZH" after "Zurich". A white curtain hangs at the left edge of the frame. In mid-air in front of the wall, a small dark quadrotor with green propeller tips is flying. In the upper-left corner, an inset shows a second, wider view of the same room, with a door at the left and cameras along the wall: a small quadrotor hovers near the middle of the inset, and a grey-and-white patterned box stands on the floor at its right. So two quadrotors are visible, one large in the main view and one small in the inset. Whatever the quadrotor does in the video is not in the frame.

## Slide 12 — LQR on airplane (prop-hang)

![Slide 12 — LQR on airplane (prop-hang)](../images/08-lqr/slide-12.jpg)

Title bar: "LQR on airplane (prop-hang)" (blue). Printed number 12. The slide shows a single frame of a video that was played in the lecture; the PDF holds only that frame. Below the frame, the underlined link https://www.youtube.com/watch?v=wBhS77cAJ0s.

The frame is a photograph of an indoor space with white walls, a net hung along the walls, white padded panels, a wooden door with frosted glass panels at the right and a red tile floor. Four black tripods stand around the space. In the middle of the picture a small white model aeroplane hangs nose-up (fuselage vertical, its single propeller at the top), mounted on top of a white pole that stands in a small wooden stand on the floor. Its wide wing is two black panels with white upper edges. A smaller tripod stands behind the aeroplane, and a red exit sign shows at the upper right. Whatever the aeroplane does in the video is not in the frame.

## Slide 13 — LQR on humanoid

Title bar: "LQR on humanoid" (blue). Printed number 13. The slide shows a single frame of a video that was played in the lecture; the PDF holds only that frame, which is the video's title card. Below the frame, the underlined link https://www.youtube.com/watch?v=tnbR5gaWmGk.

The frame is a black rectangle with red monospaced text in two lines: "Full Dynamics LQR Control of a Humanoid Robot"; below it, in white monospaced text, "Sean Mason, Ludovic Righetti, and Stefan Schaal". At the bottom left a dark-red banner with the University of Southern California seal and the text "USC University of Southern California"; at the bottom right a teal circular seal with a profile head and the text "MAX-PLANCK-GESELLSCHAFT". No robot is visible in the frame.
