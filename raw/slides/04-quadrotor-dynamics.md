---
title: Lecture 4 — Quadrotor Dynamics (slide deck)
lecture: 4
slides: 13
source_pdf: https://www.dropbox.com/scl/fi/v8bp2gyhpixill7c70u7q/Lecture4_slides.pdf?rlkey=h44i0kp1bpmxk3zdg65gvqu29&dl=0
numbering: PDF page N = Slide N for all 13 pages (1:1). Pages 1, 2 and 3 print no number; their labels (1, 2, 3) are inferred from position. Pages 4–13 print 4–13.
images: 4 slides are rendered and shown under their headings (7, 8, 9, 10). Not rendered — the title page (1); the topic maps (2, 3), which repeat Lecture 3's slide 2 apart from the bold line; text-only slides (4, 5, 6, 11, 12); and slide 13, whose photograph is a faded copy of slide 7 under transcribed text. The lecture's technical figures are in the notes, whose three figures are rendered in the notes file.
figure_audit: An independent reader checked slides 2, 3, 7, 8, 9, 10 and 13 against the PDF at high resolution. Fixed: the number of foam poles on slides 7 and 9, and the pipe lettering on slide 10. No person is visible in any photograph apart from the small faded topic-map picture on slides 2 and 3.
---

# Lecture 4 — Quadrotor Dynamics: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 4 deck (speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Photographs and diagrams are described in prose since the KB is read as text. The derivation of the quadrotor dynamics is not in this deck; slide 5 points to the separate lecture notes.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 13 pages, and the last printed number is 13. Slides 1, 2 and 3 print no number in the corner, so their labels are inferred from position (slide 1 is the title page; slides 2 and 3 are the two topic-map pages before printed slide 4).

Companion pages: [wiki page for this lecture](../../wiki/04-quadrotor-dynamics.md) · [transcript](../transcripts/04-quadrotor-dynamics.md) · [lecture notes](../notes/04-quadrotor-dynamics.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Topic map (Geometric planning bold) |
| 3 | Topic map (Robot dynamics bold) |
| 4 | Two challenges with geometric motion planning: dynamic feasibility, errors and disturbances |
| 5 | Today's goal: understand quadrotor dynamics (see notes) |
| 6 | Section divider: Lab logistics |
| 7–8 | The two lab spaces: EQuad G109 and the SEAS Robotics lab (photographs) |
| 9–10 | Lab setup: RRT-planned trajectory on a measured map (photographs) |
| 11 | What is in the lab spaces |
| 12–13 | Lab safety and logistics |

---

## Slide 1 — Lecture 4: Quadrotor Dynamics

Title page. Title in blue in a rounded box: "Lecture 4: Quadrotor Dynamics". Below it, a faded wide photograph of a small quadrotor drone seen from the front (black propellers on the left and right arms, a circuit board in the centre with a small camera module on a vertical board, red and black wires). Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred).

## Slide 2 — Topic map (Geometric planning bold)

No printed title and no printed number (label inferred). Three rounded cards side by side, each with a blue heading, a picture and four lines of topics. Only the left card is at full strength; the middle and right cards are faded to light grey.

- Left card, "Planning and control": picture of a blue wireframe rendering of cars on a road with a planned path curving ahead. Topics in order: "**Geometric planning**" (bold, the only bold line on this slide), "Robot dynamics", "Planning with dynamics", "Feedback control".
- Middle card (faded), "Localization, mapping": picture of a forest trail with a coloured map overlay. Topics: "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card (faded), "Robot learning": picture of a humanoid robot in a kitchen beside a person (a person is visible in this small faded picture). Topics: "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

## Slide 3 — Topic map (Robot dynamics bold)

No printed title and no printed number (label inferred). Identical in layout, pictures and faded cards to slide 2; the only difference is which topic is bold. Here "**Robot dynamics**" (second line of the left card) is bold, and "Geometric planning" is in regular weight. The left card "Planning and control" is at full strength with lines "Geometric planning", "**Robot dynamics**", "Planning with dynamics", "Feedback control". The middle card ("Localization, mapping": Bayes filtering, Kalman filters, Particle filters, SLAM) and the right card ("Robot learning": Imitation learning, Generative architectures, Reinforcement learning, World models) are faded to light grey exactly as on slide 2.

## Slide 4 — Two challenges with geometric motion planning

Plain grey header bar with no title text. Printed number 4. A rounded box: "**Two challenges** with geometric motion planning:" ("Two challenges" bold blue). Then:

1. "**Dynamic feasibility:** not all motion plans are physically executable by our robot." ("Dynamic feasibility:" bold blue.)

"Question: can you think of an *infeasible* plan for a quadrotor?" ("Question:" in blue, "infeasible" in blue italics.)

2. "**Errors and disturbances:** even if the plan is feasible, there may be errors or external disturbances (e.g., wind gusts)" ("Errors and disturbances:" bold blue.)

## Slide 5 — Today: understand dynamics of a quadrotor

Plain grey header bar with no title text. Printed number 5. A rounded box: "**Today:** understand dynamics of a quadrotor" ("Today:" bold blue, "dynamics" blue). Below it, in bold blue: "See notes". The derivation is in the separate lecture notes, not in this deck.

## Slide 6 — Lab logistics

Plain grey header bar with no title text. Printed number 6. A single rounded box containing "Lab logistics" in blue. Section divider.

## Slide 7 — EQuad, G109

![Slide 7 — EQuad, G109](../images/04-quadrotor-dynamics/slide-7.jpg)

Title bar: "EQuad, G109" (blue). Printed number 7. A full-width photograph of an indoor lab room, taken from the left side. On the right is a drone flight area enclosed by black netting hung from the ceiling on metal poles, with a lighter white net panel hanging in the middle. The flight area floor is green artificial turf. Standing on the turf are about eight blue foam-covered vertical poles (obstacles) on round metal bases: one at the left, a cluster of three at the back left, and four on the right; two small white taped markers (one an X in a square) are visible on the turf. On the left, outside the netting, are white desks with teal office chairs, a few small boxes (dark with green labels) and a tape measure on the desk, and a whiteboard with illegible handwriting on the far left. The ceiling has acoustic tiles, fluorescent lights and a wooden beam. No person is visible. No room sign is visible; the only text is the slide title.

## Slide 8 — SEAS Robotics lab (F-wing, EQuad)

![Slide 8 — SEAS Robotics lab (F-wing, EQuad)](../images/04-quadrotor-dynamics/slide-8.jpg)

Title bar: "SEAS Robotics lab (F-wing, EQuad)" (blue). Printed number 8. A full-width photograph of a smaller netted drone area, seen through white netting that hangs in the foreground. Inside are green artificial turf, two blue foam-covered vertical poles, and a white X-in-a-square tape marker on the turf in the foreground. The back wall has a window or dark panel on the left and a lime-green wall on the right; a small dark object (possibly equipment mounted on that wall; it is too small to identify) is at the right edge. Bright green chairs are on the left outside the net, and part of a white table is at the lower right. No person is visible. No text other than the slide title is legible.

## Slide 9 — Setup

![Slide 9 — Setup](../images/04-quadrotor-dynamics/slide-9.jpg)

Title bar: "Setup" (blue). Printed number 9. Left side text: "Use RRT to plan trajectory" ("RRT" blue). Then: "Will assume map of environment (you'll create this by measuring obstacle locations)" ("map" and "measuring" blue).

Right side: a tall photograph (not a simulation screenshot) of the corner of the netted flight area, taken from above at an angle. Green artificial turf; four blue foam-covered poles on round silver bases stand as obstacles; black netting and white wall behind with wall outlets. A white tape X-in-a-square marker lies on the turf at the lower left. At the upper right, white tape forms a rectangle with the word "END" in tape letters. No person is visible. There is no RRT tree or path drawn on this picture.

## Slide 10 — RRT

![Slide 10 — RRT](../images/04-quadrotor-dynamics/slide-10.jpg)

Title bar: "RRT" (blue). Printed number 10. A wide photograph, apparently a frame from a video (the slide shows only one still), of a small quadrotor with a white frame sitting on or just above the green turf near the bottom centre, with a blue light visible. Several white vertical pipes (one printed vertically with "J-M MANUFACTURING" and a few smaller characters, and one teal pipe in the distance) stand as obstacles in the upper half. Small white paper or tape dots are scattered on the turf, forming a rough line from the foreground towards the pipes. White netting is on the left and right edges, and a cable loop lies at the upper right. This is a photograph, not a drawing of an RRT: no tree, nodes, edges or start/goal markers are drawn on it. No person is visible.

## Slide 11 — What is in the lab space(s)?

Title bar: "What is in the lab space(s)?" (blue). Printed number 11. A numbered list:

1. 4 drones in G109; 3 drones in SEAS Robotics Lab
2. Spare parts (propellers, extra motors, prop guards, …)
3. Measuring tape (for creating "map")
4. Safety glasses

## Slide 12 — Lab safety and logistics

Title bar: "Lab safety and logistics" (blue). Printed number 12. Text, one item per line:

"Labs can be used anytime (weekdays/weekends)" ("anytime" blue).

"Everyone who has completed online safety training can access space" ("online safety training" blue).

"**Occupancy guidelines:**" (bold blue).

"Take turns testing hardware / debugging" ("Take turns" blue).

"This organic model works better than sign-up sheet"

In a rounded box at the bottom: "**Drone issues:** please post in Ed "Drone issues" thread" ("Drone issues:" bold blue).

## Slide 13 — Lab safety and logistics (rules)

Title bar: "Lab safety and logistics" (blue). Printed number 13. The background is a faded copy of slide 7's photograph of the G109 netted flight area (the same room, desks and blue poles; no person visible), with two translucent rounded boxes over it.

Upper box: "Please wear **safety glasses** at all times!" and "Stand **outside netted area** when drone is operating" ("safety glasses" and "outside netted area" bold blue).

Lower box: "Please treat the drones with care!" (blue), then "Non-trivial operating cost for this course: ~ 600 / drone", with a dollar sign before the 600 (about 600 dollars per drone).
