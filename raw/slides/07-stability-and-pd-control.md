---
title: Lecture 7 — Feedback Control (slide deck)
lecture: 7
slides: 7
source_pdf: https://www.dropbox.com/scl/fi/6jzh0fey1mnfs8drq3905/Lecture7_slides.pdf?rlkey=nqo1qiqzhktzpy5klid7hyvgs&dl=0
numbering: PDF page N = Slide N for all 7 pages (1:1). Pages 1 and 2 print no number; their labels (1, 2) are inferred from position. Pages 3–7 print 3–7.
images: 2 slides are rendered and shown under their headings (3, 6). Not rendered — the title page (1); the course outline (2), a layout repeated from earlier decks; slide 4, whose only picture is a stock photograph of a road sign; slide 5, the build step before slide 6 (the same figure with a different caption); and slide 7, text only. The notes' three drawings are rendered in the notes file.
figure_audit: An independent reader checked slides 3, 4, 5 and 6 against the PDF at 400–600 dpi. Nothing described is absent from the page; slides 4–6 agree. Fixed: on slide 3 the planned path cuts through the dashed margins of both obstacles (it touches neither disc). Added: the bottom drone's arrow lengths on slides 5–6 compared with the others. Renders of slides 3 and 6 were also checked in the parent.
---

# Lecture 7 — Feedback Control: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 7 deck (title "Lecture 7: Feedback Control", speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Figures are described in prose since the KB is read as text. The deck is short: it motivates feedback control and states the goal and the plan for the lecture. The definitions (fixed point, stability, stabilizability) and the PD controller are in the separate written lecture notes, not on the slides.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 7 pages, and the last printed number is 7. Slides 1 and 2 print no number in the corner, so their labels (1, 2) are inferred from position (title page and outline page).

Companion pages: [wiki page for this lecture](../../wiki/07-stability-and-pd-control.md) · [transcript](../transcripts/07-stability-and-pd-control.md) · [lecture notes](../notes/07-stability-and-pd-control.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Course outline: where "Feedback control" sits |
| 3–4 | Challenges with motion planning: a planned path versus execution; uncertainty |
| 5–6 | Feedback control for hovering: the vector field of control inputs; the feedback control law |
| 7 | Plan for today and next lecture |

---

## Slide 1 — Lecture 7: Feedback Control

Title page. Title in blue in a rounded light-grey box: "Lecture 7: Feedback Control". Below it, a faded wide photograph of a small quadrotor seen from the front: black propellers on the left and right arms, a circuit board in the centre carrying a vertical board with a camera and lens, red and black wires. Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred from position).

## Slide 2 — Course outline (Planning and control)

No title bar and no number printed (label inferred from position). Three rounded cards side by side. The left card is in full colour; the other two are faded.

- Left card, heading in blue "Planning and control". Below it a blue-tinted image of a car on a road with a drawn curved lane path and a second car ahead. Below, four lines: "Geometric planning", "Robot dynamics", "Planning with dynamics", "**Feedback control**" (bold, the current topic).
- Middle card (faded), heading "Localization, mapping", an image of a forest with a coloured point-cloud overlay; lines "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card (faded), heading "Robot learning", an image of a humanoid robot and a person in a kitchen; lines "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

## Slide 3 — Challenges with motion planning

![Slide 3 — Challenges with motion planning](../images/07-stability-and-pd-control/slide-3.jpg)

Title bar: "Challenges with motion planning" (blue). Printed number 3.

The slide is one large screenshot of a 2D planar-quadrotor simulation on a light-grey square grid, filling the width of the slide below the title bar. It looks like a single frame of a simulation or animation; the PDF holds only that frame, so the executed-path state in it is not a result. What is visible:

- Top left, in grey monospaced text: "m = 0.600 kg" and "J = 0.01500 kg·m²".
- Two filled light-grey discs (obstacles), each surrounded by a larger dashed grey circle (a margin around the obstacle). One disc is lower and left of centre; the other is higher and right of centre.
- A thin dark circle with crosshair tick marks at the lower left (the start) and another at the upper right (the goal).
- A smooth blue curve, the planned path, starting at the lower-left circle, rising up and to the right over the top of the left disc, descending between the two discs, passing below the right disc, and then curving up to end at the upper-right circle. It cuts through the top-right of the left disc's dashed margin and clips the lower-left of the right disc's margin, but never touches either filled disc.
- At the start circle, a short horizontal orange bar with small end caps (the executed quadrotor, drawn as a bar) and two teal arrows pointing up, one at each end of the bar. The left arrow is longer than the right one. No orange trace of an executed path is visible anywhere else in the frame.
- Along the bottom, a horizontal line, and a legend: a blue line labelled "planned" and an orange line labelled "executed".

No play button, progress bar or time counter is visible. **In the lecture** this is the trajectory-optimization demo from Lecture 6, and Majumdar runs it: when the planned control inputs are applied, the executed (orange, "yellowish") trajectory matches the plan at first and deviates near the end, with no change to the dynamics, because of numerical integration error (≈1:44–4:02). He then shows runs with the inertia changed by 10% (significant deviations, close to the obstacle) and with the mass changed by 10% (a collision) (≈4:02–4:47). The PDF holds only the frame before execution starts.

## Slide 4 — Challenges with motion planning

Title bar: "Challenges with motion planning" (blue). Printed number 4.

Left column, three text blocks with some words in blue: "**Imperfect dynamics** model" (the words "Imperfect dynamics" in blue, "model" black); "External **disturbances** (e.g., wind)" ("disturbances" in blue); "**Imperfect** knowledge of robot **state** or **map**" ("Imperfect", "state" and "map" in blue). Right column: a stock photograph of a green road sign, tilted, reading "Uncertainty" in white, on two wooden posts against a blue sky with clouds.

## Slide 5 — Feedback control for hovering

Title bar: "Feedback control for hovering" (blue). Printed number 5.

The middle of the slide shows five copies of the same side-view drawing of a planar quadrotor (a grey horizontal body with a red dome and red dot at the centre, a bent arm on each side ending in a grey motor block with a shaded grey propeller ellipse above it). Each drone has a blue arrow at each propeller, drawn straight up from the propeller. They are arranged like the points of a cross:

- Centre: one drone drawn in full black and dark grey (the others are faded light grey), level, with no arrows on it.
- Top: a faded drone tilted, with its right end higher than its left, by roughly 20 degrees (counter-clockwise on the page). Its two blue arrows point vertically up (not perpendicular to the body); the left arrow is about twice as long as the right arrow.
- Left: a faded level drone to the left of the centre one. Its left arrow is long and its right arrow is short (about half as long).
- Right: a faded level drone to the right of the centre one. Its left arrow is short and its right arrow is long (the mirror of the left drone).
- Bottom: a faded level drone below the centre one. Its two arrows are equal in length and of medium size: shorter than the long arrows of the left and right drones, longer than their short ones.

Below, in a rounded grey box: "**Goal:** define this “vector field”" ("**Goal:**" bold blue, "define this" black, "“vector field”" blue), and on the next line in blue "At every state: what control input to apply?".

## Slide 6 — Feedback control for hovering

![Slide 6 — Feedback control for hovering](../images/07-stability-and-pd-control/slide-6.png)

Title bar: "Feedback control for hovering" (blue). Printed number 6.

The same figure as slide 5: five copies of the planar quadrotor, with the centre one in full black and the other four (top tilted, left, right, bottom) faded, and the same blue upward arrows at each propeller (none on the centre drone; top: left arrow about twice the right; left: left arrow long, right short; right: left short, right long; bottom: two equal arrows). The box below now reads: "This is called a **feedback control law** (or “controller”): $\bar{u}(\bar{x})$" ("feedback control law" and "“controller”" in blue).

## Slide 7 — Feedback control

Title bar: "Feedback control" (blue). Printed number 7.

A rounded grey box with: "**Today:**" (bold blue); "Define what we want from feedback control (“stability”)" ("what we want" in blue); "Basic approach: PD control" ("PD control" in blue). Below the box: "**Next lecture:** optimal control for linear dynamics (LQR)" ("**Next lecture:**" bold blue, "optimal control" blue, rest black).
