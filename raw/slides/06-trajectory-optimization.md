---
title: Lecture 6 — Trajectory Optimization (slide deck)
lecture: 6
slides: 18
source_pdf: https://www.dropbox.com/scl/fi/9wnsc9wkmxmvwbugm7rps/Lecture6_slides.pdf?rlkey=9dsf9cbn7sjy9b5m6dieznycs&dl=0
numbering: PDF page N = Slide N for all 18 pages (1:1). Pages 1 and 2 print no number; their labels (1, 2) are inferred from position. Pages 3–18 print 3–18.
images: 6 slides are rendered and shown under their headings (3, 6, 8, 12, 14, 16). Not rendered — the title page (1); the course outline (2); the section dividers (4, 10, 13, 15); the text slides (5, 7, 9; slide 7 is also the build step before slide 8's figure); slide 11, the build step before slide 12 (the same plot without the constraints); and slides 17 and 18, video title cards whose text is transcribed. The notes have no drawings.
figure_audit: An independent reader checked slides 2, 3, 6, 8, 11, 12, 14, 16, 17 and 18 against the PDF, cropping the figures at 300-500 dpi and counting slide 14's dots by pixel colour. Nothing described is absent from the page. Fixed: slide 14 has 10 brackets (not about 13) and one visible thrust line (u1 hidden under u2), and only the Start quadrotor has teal arrows; slide 12's arrow is perpendicular to the constraint edge (not aimed at the unconstrained minimum), and one constraint label's position. Renders of slides 12 and 14 were also checked in the parent.
---

# Lecture 6 — Trajectory Optimization: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 6 deck (title "Planning with dynamics", speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Figures are described in prose since the KB is read as text. The deck states the problem and the ideas; the linearization, discretization and the quadratic program itself are in the separate lecture notes (slide 10 says "See lecture notes"). Slides 16–18 are video slides: the PDF holds one frame of each video.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 18 pages, and the last printed number is 18. Slides 1 and 2 print no number in the corner, so their labels (1, 2) are inferred from position (title page and outline page).

Companion pages: [wiki page for this lecture](../../wiki/06-trajectory-optimization.md) · [transcript](../transcripts/06-trajectory-optimization.md) · [lecture notes](../notes/06-trajectory-optimization.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Course outline: where "Planning with dynamics" sits |
| 3 | Last lecture: differential flatness, and its limits |
| 4–9 | RRT with dynamics: Idea 1 (RRT in state space) and Idea 2 (boundary value problem) |
| 10–12 | Trajectory optimization with linear dynamics; quadratic programs (contour plots) |
| 13–14 | Trajectory optimization for nonlinear systems: sequential QP |
| 15–18 | Examples of trajectory optimization: Acrobot, airplane (videos) |

---

## Slide 1 — Lecture 6: Planning with dynamics

Title page. Title in blue in a rounded light-grey box: "Lecture 6: Planning with dynamics". Below it, a faded wide photograph of a small quadrotor seen from the front: black propellers on the left and right arms, a circuit board in the centre carrying a vertical board with a camera and lens, red and black wires. Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred from position).

## Slide 2 — Course outline (Planning and control)

No title bar and no number printed (label inferred from position). Three rounded cards side by side. The left card is in full colour; the other two are faded.

- Left card, heading in blue "Planning and control". Below it a blue-tinted image of a car on a road with a drawn curved lane path and a second car ahead. Below, four lines: "Geometric planning", "Robot dynamics", "**Planning with dynamics**" (bold, the current topic), "Feedback control".
- Middle card (faded), heading "Localization, mapping", an image of a forest with a coloured point-cloud overlay; lines "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card (faded), heading "Robot learning", an image of a humanoid robot and a person in a kitchen; lines "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

## Slide 3 — Last lecture

![Slide 3 — Last lecture](../images/06-trajectory-optimization/slide-3.png)

Title bar: "Last lecture" (blue). Printed number 3.

Left column. In blue bold, "**Differential flatness:**" followed by "Ability to control flat outputs (almost) arbitrarily" (blue). Then in black: "Very powerful concept, but restrictive". Then, in a rounded grey box: "What if we want to control states beyond the flat outputs?" and "What if our system is not differentially flat?"

Right column. A drawing of the planar quadrotor (side view, slightly tilted: a light-grey arm with a black motor block and a grey propeller disc at each end, a black central body with a red dome and a red dot). Beneath it, the formula $\bar{z} = [x, y]$. Below that, a black rectangle where a video would be; the frame is entirely black, nothing else shows. No video link is printed on this slide. The lecture does not say that a video was played here. On this slide Majumdar recalls the fixed-wing tail-sitter shown in Lecture 5 (≈2:28), but nothing on the page identifies the black frame as that video.

## Slide 4 — RRT with dynamics (divider)

Grey header bar with no title text. Printed number 4. A rounded grey box in the middle with the blue text "RRT with dynamics".

## Slide 5 — RRT with dynamics: Idea 1

Title bar: "RRT with dynamics: Idea 1" (blue). Printed number 5.

Dynamics: $\dot{\bar{x}} = f(\bar{x}, \bar{u})$

Construct the RRT in state space ("state space" in blue).

In a rounded grey box:

Initialize the tree with the starting state $\bar{x}_ A$

On each iteration:

Step 1. Sample a random state, $\bar{x}_ {\text{rand}}$, *from the existing tree*

Step 2. Select a random control input, $\bar{u}_ {\text{rand}}$

Step 3. Compute

$$
\bar{x}_ {\text{s}} = \bar{x}_ {\text{rand}} + \int_ 0^{\Delta T} f(\bar{x}(t), u_ {\text{rand}}) \thinspace dt
$$

Step 4. Check collision of $\bar{x}_ {\text{s}}$. If in collision, continue. Else, add it to the tree. If close enough to goal, terminate.

(As printed, the integrand has $u_ {\text{rand}}$ without a bar.)

## Slide 6 — RRT with dynamics: Idea 1

![Slide 6 — RRT with dynamics: Idea 1](../images/06-trajectory-optimization/slide-6.jpg)

Title bar: "RRT with dynamics: Idea 1" (blue). Printed number 6.

Text: "One can show that this algorithm is probabilistically complete" and "Unfortunately, it doesn't actually work well".

Figure: a MATLAB-style plot with black axes, no gridlines. The horizontal axis is labelled with ticks −10, −5, 0, 5, 10, 15, 20, 25; the vertical axis with ticks −10, −5, 0, 5, 10, 15, 20, 25. Near the origin, at roughly x from −4 to 4 and y from −4 to 4, is a small dense black tangle of short line segments (the tree), a roughly round cloud about 8 units across. In the upper right, at roughly x from 15 to 20 and y from 15 to 20, is a green filled square with a black outline, labelled "Goal" in black. The tree has not grown anywhere near the goal; the rest of the plot is empty. Source line at the bottom: "[Source: "Underactuated Robotics", Russ Tedrake]".

## Slide 7 — RRT with dynamics: Idea 2

Title bar: "RRT with dynamics: Idea 2" (blue). Printed number 7.

Text: "Again, keep RRT algorithm structure the same, but change the "extension" operation". Then: "Solve the boundary value problem for connecting $\bar{x}_ {\text{near}}$ to $\bar{x}_ {\text{s}}$" ("boundary value problem" in blue). The rest of the slide is empty (this is the build step before the figure of slide 8).

## Slide 8 — RRT with dynamics: Idea 2

![Slide 8 — RRT with dynamics: Idea 2](../images/06-trajectory-optimization/slide-8.png)

Title bar: "RRT with dynamics: Idea 2" (blue). Printed number 8. Same text as slide 7, plus a figure below it.

Figure: three blue filled dots on a white background.

- $\bar{x}_ {\text{near}}$: a dot at the lower left, label below it.
- $\bar{x}_ {\text{s}}$: a dot in the middle, up and to the right of $\bar{x}_ {\text{near}}$, label below it.
- $\bar{x}_ {\text{rand}}$: a dot at the upper right, label below it.

A black dotted straight line runs from $\bar{x}_ {\text{near}}$ through $\bar{x}_ {\text{s}}$ to $\bar{x}_ {\text{rand}}$, so $\bar{x}_ {\text{s}}$ lies on that line, about 40 percent of the way to $\bar{x}_ {\text{rand}}$. A solid black curve connects $\bar{x}_ {\text{near}}$ to $\bar{x}_ {\text{s}}$: it leaves $\bar{x}_ {\text{near}}$ going up (a bit leftward), arcs over to the left and top, and comes down to $\bar{x}_ {\text{s}}$ from the upper left. This curve, not the straight dotted line, is the dynamically feasible connection. No arrowheads are drawn.

## Slide 9 — RRT with dynamics: Idea 2

Title bar: "RRT with dynamics: Idea 2" (blue). Printed number 9.

In a rounded grey box: "**Boundary value problem:** find control inputs that drive the system from $\bar{x}_ {\text{near}}$ to $\bar{x}_ {\text{s}}$" (the words "Boundary value problem:" in blue).

Then, as separate lines:

- "Also known as "trajectory optimization"" ("trajectory optimization" in blue)
- "Can be tackled using techniques from nonlinear optimization" ("nonlinear optimization" in blue)
- "Will discuss special case today → computationally efficient"
- "Briefly describe general version"

## Slide 10 — Trajectory optimization with linear dynamics

Grey header bar with no title text. Printed number 10. A rounded grey box with the blue text "Trajectory optimization with linear dynamics". Below it, in large black text: "See lecture notes".

## Slide 11 — Quadratic programs

Title bar: "Quadratic programs" (blue). Printed number 11. The slide holds one pasted image and no other text.

Figure: a contour plot on white. A vertical axis labelled $x_2$ with ticks 1, 2, 3, 4, and a horizontal axis labelled $x_1$ with ticks 1, 2, 3, 4 (both in grey; the axes cross at the origin at the lower left, and the plot is cut off at the right edge, so the ellipses are clipped at about $x_1 = 5$ to 6). Five nested ellipses in shades of lavender, all centred at the point (4, 3), the innermost darkest and the outer ones fainter. At the centre is a small circled dot with the label "unconstrained min (4, 3)" on two lines below it. The ellipses are wider than they are tall. These are level sets of a quadratic objective whose unconstrained minimum is at $(x_1, x_2) = (4, 3)$. The slide gives no equation.

## Slide 12 — Quadratic programs

![Slide 12 — Quadratic programs](../images/06-trajectory-optimization/slide-12.jpg)

Title bar: "Quadratic programs" (blue). Printed number 12. The same plot as slide 11 with the constraints added; again no other text.

Figure, added to slide 11's picture:

- A light-green shaded polygon, the "feasible region" (label in grey inside it at the bottom, "feasible region"), outlined in dark green. Its corners are at about (0, 0), (4, 0), (1.33, 2.67) at the top and (0, 2) on the left axis. Its left side is the $x_2$ axis from 0 to 2; its bottom is the $x_1$ axis from 0 to 4.
- The upper-left edge, from (0, 2) up to the top corner, is labelled by a grey dashed leader line and the text $2x_2 - x_1 \le 4$ (in grey, at the upper left of the plot).
- The right edge, from the top corner down to (4, 0), is the constraint $x_1 + x_2 \le 4$. Its grey label has no leader line: it sits outside the polygon to its right, at about $x_1$ from 3.3 to 4.1 and $x_2$ about 1.1, in the gap below the thick ellipse's lower-right arc.
- One ellipse, the second from the outside, is drawn thicker in brown/orange. It touches the feasible region's right edge at the point (2, 2), marked with a filled brown dot, and lies outside the polygon elsewhere.
- A short brown arrow starts at that dot and points up and to the right at 45 degrees, ending near (2.5, 2.5), perpendicular to the edge $x_1 + x_2 = 4$ (not aimed at the unconstrained minimum). It is labelled $-\nabla f$ in grey text to the right of its lower part.
- The dot is labelled "x* = (2, 2)" in black text at the lower left of the dot, joined to the dot by a dashed grey leader line.

So the constrained minimum $x^\ast = (2, 2)$ lies on the boundary $x_1 + x_2 \le 4$, not at the unconstrained minimum (4, 3), which is outside the feasible region. As drawn, the objective's thicker contour is tangent to that edge at (2, 2).

## Slide 13 — Trajectory optimization for nonlinear systems: sequential QP

Grey header bar with no title text. Printed number 13. A rounded grey box with the blue text "Trajectory optimization for nonlinear systems:" and, on a second line, "sequential QP".

## Slide 14 — Idea: iteratively approximate as QP

![Slide 14 — Idea: iteratively approximate as QP](../images/06-trajectory-optimization/slide-14.jpg)

Title bar: "Idea: iteratively approximate as QP" (blue). Printed number 14. The slide is a screenshot of an interactive demo (light blue-grey background panel), with two white callout labels added. The PDF holds one frame; the panel reads "iteration 0 / 23" at the top right.

Left plot, a position plot with a light grid. Axis labels: "y [m]" at the top left and "x [m]" at the bottom right; no tick numbers. A horizontal grey line runs across near the bottom (a floor or ground line).

- Start: a planar quadrotor (a side-view drawing: grey propeller discs on a thin arm, black motor blocks, a black body with a red dome and red dot, a small crosshair under the body, and two small teal up-arrows flanking the body) at the lower left, with a white rounded callout "Start" in blue beneath it.
- Goal: the same quadrotor drawing at the upper right, with the crosshair but no teal arrows, and a white rounded callout "Goal" in blue above it.
- Two grey filled circles (obstacles), each surrounded by a larger dashed grey circle (a safety margin): the first is left of centre and lower, the second is right of centre and higher. A straight dark blue line runs from Start to Goal, passing through the middle of both obstacles; it is the initial trajectory, and it goes right through both circles.
- Along the line are 23 small orange dots in two groups: 11 running from the left edge of the first obstacle's dashed margin to its right side, and 12 starting inside the second obstacle's margin, just left of the grey circle, and ending at its right edge. There are also 10 short dark horizontal brackets (error-bar-like ticks, wider than the dots), evenly spaced along the line: the first partly hidden behind the Start quadrotor, the last just left of the Goal quadrotor. The 3rd to 9th brackets carry orange dots; the 1st, 2nd and 10th have none. Small blue dots mark the other points of the line: near the start, two between the two orange groups, and near the goal.

Right plot, titled "rotor thrust u₁ u₂ [N]" in small text, with the line "iteration 0 / 23" above it. Vertical axis with ticks 0, 4, 8; horizontal axis from "0 s" to "3 s". A dashed upper line at about 7.5 and a dashed lower line at 0 mark the input limits. Only one line is visible: a flat teal line at about 3 across the whole time range. The legend at the bottom has a dark blue swatch for "u₁" and a teal swatch for "u₂", so the blue $u_1$ line is evidently hidden under the teal $u_2$ line (both inputs equal and constant).

This frame is iteration 0, before any QP has been solved; it is not the final trajectory. In the lecture the demo is run (≈1:01:02–1:02:36): Majumdar says it was vibe coded with Claude, starts from this straight-line guess through the obstacles, and describes the iterations that follow: linearize the dynamics about the current trajectory, solve a QP, raise the penalty on obstacle violation, repeat. The PDF holds only this first frame.

## Slide 15 — Examples of trajectory optimization (divider)

Grey header bar with no title text. Printed number 15. A rounded grey box with the blue text "Examples of trajectory optimization".

## Slide 16 — Acrobot (video)

![Slide 16 — Acrobot (video)](../images/06-trajectory-optimization/slide-16.jpg)

Title bar: "Acrobot" (blue). Printed number 16. Video slide: the PDF holds a single frame.

Left text: "Underactuated double pendulum: only actuated at "elbow"" ("Underactuated" in blue), then "Trajectory found using trajectory optimization techniques" ("trajectory optimization" in blue).

Right, a portrait-shaped video frame: a room with white, angled walls and a window with a closed grey blind at the left. In the lower centre is a dark grey metal table holding a small grey box and a laptop or monitor; a thin dark vertical pendulum rod stands upright above the table, extending up toward a thin line near the top of the frame. A reddish-brown floor is at the bottom, an orange-edged table at the right edge. Grey metal rails and wooden planks lean against the right wall, and a small yellowish frame sits at the top of the pendulum rod. No person is visible.

Link at the bottom: https://www.youtube.com/watch?v=FeCwtvrD76I

In the lecture the video is played (≈1:06:25–1:07:11): the acrobot swings up from hanging down to upright on a trajectory found by sequential quadratic programming, and does not quite stabilize at the top because of friction.

## Slide 17 — Airplane (video)

Title bar: "Airplane" (blue). Printed number 17. Video slide: the PDF holds a single frame.

The frame is a title card on black. Text in white: "Fast and Accurate Knife-Edge Maneuvers for Autonomous Aircraft" (two lines, large); "Andrew Barry, Anirudha Majumdar, Tim Jenks, Russ Tedrake" (two lines); "Robot Locomotion Group, MIT/CSAIL". No aircraft or trajectory is in this frame.

Link at the bottom: https://www.youtube.com/watch?v=voN9CCmzxYk

In the lecture the video is played (≈1:07:11–1:08:03): a fixed-wing airplane is shot off a launcher, flies a knife-edge maneuver between PVC-pipe obstacles less than a wingspan apart, and lands in a net.

## Slide 18 — Airplane (video)

Title bar: "Airplane" (blue). Printed number 18. Video slide: the PDF holds a single frame.

The frame is a title card on black. Text in blue, bold: "Funnel Libraries for Realtime Obstacle Avoidance" (two lines); below, in white bold, "Anirudha Majumdar and Russ Tedrake". At the lower left, the orange and grey outline "CSAIL" logo with the word "CSAIL" in orange; at the lower right, the red and grey "MIT" logo. No aircraft or trajectory is in this frame.

Link at the bottom: https://www.youtube.com/watch?v=cESFpLgSb50

In the lecture the video is played (≈1:08:03–1:10:41) and explained afterwards: a library of funnels, precomputed offline, from which the plane picks one that does not collide with the obstacles at runtime.
