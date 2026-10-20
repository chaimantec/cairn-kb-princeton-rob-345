---
title: Lecture 3 — Rapidly Exploring Randomized Trees (RRTs) (slide deck)
lecture: 3
slides: 62
source_pdf: https://www.dropbox.com/scl/fi/5uv2vt76nqj4b32vr4i37/Lecture3.pdf?rlkey=nx8jjqjlvmgcqqhb8r1p6okzp&dl=0
numbering: PDF page N = Slide N for all 62 pages (1:1). Pages 1 and 2 print no number; their labels (1, 2) are inferred from position.
figure_audit: Two independent readers checked 24 slides against the PDF (13, 21, 36, 37, 41, 44, 46, 47, 50, 58, then 7, 9, 10, 12, 19, 24–35, 38–40, 42, 43, 45, 51), covering every step of the RRT worked example. Fixed: which point is in collision on slide 36 (the extended point, not the nearest node), the node count on slide 41, the solid edges already drawn on slides 40 and 43, the extent of the tree on slide 50, and several small positions and counts.
---

# Lecture 3 — Rapidly Exploring Randomized Trees (RRTs): slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 3 deck (speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Diagrams, worked examples, photographs and video stills are described in prose since the KB is read as text.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 62 pages, and the last printed number is 62. Slides 1 and 2 print no number in the corner, so their labels are inferred from position (slide 1 is the title page; slide 2 is the topic-map page before printed slide 3).

Companion pages: [wiki page for this lecture](../../wiki/03-rrts.md) · [transcript](../transcripts/03-rrts.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Topic map (Planning and control highlighted) |
| 3–4 | Geometric motion planning: geometric model of the environment, getting from A to B without collisions |
| 5–13 | Accounting for robot geometry: point robot (recap), circle approximation, inflating obstacles, cluttered environments |
| 14–20 | Configuration space: degrees of freedom, free space and obstacle space, configuration-space obstacles |
| 21 | Curse of dimensionality |
| 22–24 | Rapidly exploring randomized tree (RRT): readings and key ideas (continuous space, no explicit $C_{\text{obs}}$, collision checking, GJK) |
| 25–47 | RRT worked example: iterations 0 to 6 on a two-obstacle map, step by step |
| 48 | Algorithm 1: RRT (pseudocode) |
| 49–50 | RRT animations (GIF and video frame) |
| 51–52 | Extend() step size; why RRTs avoid constructing $C_{\text{obs}}$ |
| 53–56 | RRT demos (house with piano, quadrotor trajectory planning, PR2 arm); recovering the path |
| 57–59 | RRT variants: RRT*, bi-directional RRT; RRT versus RRT* comparisons |
| 60–62 | Completeness, RRTs not complete, probabilistic completeness |

---

## Slide 1 — Lecture 3: Rapidly Exploring Randomized Trees (RRTs)

Title page. Title in blue in a rounded box: "Lecture 3: Rapidly Exploring Randomized Trees (RRTs)". Below it, a faded wide photograph of a small quadrotor drone seen from the front (black propellers on left and right arms, circuit board in the centre with a small camera module on a vertical board, red and black wires). Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred).

## Slide 2 — Topic map (Planning and control highlighted)

No printed title and no printed number (label inferred). Three rounded cards side by side, each with a blue heading, a picture and four lines of topics. Only the left card is at full strength; the other two are faded to light grey.

- Left card, "Planning and control": picture of a blue wireframe rendering of two cars on a road with a planned path curving ahead. Topics: "**Geometric planning**" (bold), "Robot dynamics", "Feedback control", "Planning with dynamics".
- Middle card (faded), "Localization, mapping": picture of a forest trail with a coloured map overlay. Topics: "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card (faded), "Robot learning": picture of a humanoid robot in a kitchen beside a person wearing a headset. Topics: "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

## Slide 3 — Geometric Motion Planning

Title bar: "Geometric Motion Planning". Text: "**Assume:** we have a geometric model of environment" ("geometric model" in blue). Below, a large point-cloud image of a street scene seen from street level, in false colour: road surface in dark blue, trees and building walls in green, utility poles and overhead wires in yellow-orange, cars and other objects in orange; black background; green crosswalk stripes. No source credit is printed.

## Slide 4 — Geometric Motion Planning (question)

Title bar: "Geometric Motion Planning". Text in a rounded box: "**Question:** how can we get robot from A to B without collisions?" ("without collisions" in blue). The same point-cloud street image as slide 3 is below it.

## Slide 5 — Last lecture: discrete planning

Title bar: "Last lecture: discrete planning". Text in a rounded box: "Assumed that robot is a **point**" ("point" bold blue). Below, a plot frame (white square with thin grey border) from the previous lecture's search demo: a light-blue obstacle shaped like a "7" (a horizontal bar across the top and a vertical bar down the right side, with the empty notch below the bar on the left). A black dot labelled "A" with a small orange and yellow marker sits just left of the vertical bar, about halfway down. A black star labelled "B" sits at the upper right, outside the obstacle. Beneath the plot is the caption "expanded: 4". This is a single frame of an animation of a search; the counter is not a result of this lecture.

## Slide 6 — How do we account for robot geometry?

Title bar: "How do we account for robot geometry?". A diagram on white: two dark-red rectangles labelled "Obstacle" (white text), one in the upper middle and one in the lower middle, stacked vertically with a wide horizontal gap between them. A drawing of a planar quadrotor (grey rotors on two arms, black central body with a red dome) labelled "A" is at the lower left, below and left of the gap. A faded copy of the quadrotor labelled "B" is at the right, higher up, level with the space above the upper obstacle's bottom edge.

## Slide 7 — Simple approach: circle approximation

Title bar: "Simple approach: circle approximation". The same layout as slide 6 (two dark-red obstacle rectangles, now without the word "Obstacle"), with quadrotor A at lower left and quadrotor B at right. Each quadrotor now sits inside a pale-blue circle that encloses the whole drawing, labelled "A" and "B" inside the circles.

## Slide 8 — Equivalently: inflate obstacles

Title bar: "Equivalently: inflate obstacles". The same two dark-red rectangles, now each surrounded by a larger pale-pink rounded region (the inflated obstacle). The quadrotors A (lower left) and B (right, faded) are drawn without circles; a small blue dot is on the centre of each quadrotor body, marking the point that represents the robot.

## Slide 9 — Equivalently: inflate obstacles (path for a point)

Title bar: "Equivalently: inflate obstacles". The same inflated obstacles. The quadrotor drawings are replaced by blue dots at A (lower left) and B (right). A black curved line starts at A, rises, runs horizontally through the gap between the two pink inflated regions, and curves up to B.

## Slide 10 — Equivalently: inflate obstacles (path of the real robot)

Title bar: "Equivalently: inflate obstacles". The pink inflated regions are removed, leaving the two dark-red rectangles. The same black curved path from A to B runs through the gap, now with a sequence of translucent quadrotor drawings along it (A at lower left in full colour, B at upper right in full colour, six faded copies in between, tilting slightly along the path), showing the real robot body moving along the path without touching the obstacles.

## Slide 11 — Challenge: cluttered environments

Title bar: "Challenge: cluttered environments". A diagram like slide 6 with a third, thinner dark-red rectangle added in the middle of the gap between the two obstacles (so there are two narrow gaps, one above and one below the thin rectangle). Quadrotor A at lower left, faded quadrotor B at right. No obstacle labels. The page number is partly cut off at the bottom edge.

## Slide 12 — Challenge: cluttered environments (path through the lower gap)

Title bar: "Challenge: cluttered environments". The same three rectangles. A sequence of translucent quadrotor drawings runs horizontally from A (full colour, lower left) through the narrow lower gap (between the thin middle rectangle and the lowest rectangle), then rises past the right end of the thin rectangle to B at the right. The drones are drawn nearly level as they pass through the gap, and tilt as they climb toward B.

## Slide 13 — Challenge: cluttered environments (circle approximation fails)

Title bar: "Challenge: cluttered environments". Same as slide 12, with one pale-blue circle drawn over the middle drone in the lower gap. The circle is large enough to overlap both the thin middle rectangle above it and the lowest rectangle below it, showing that a circle enclosing the robot would collide with the obstacles even though the real robot fits through the gap.

## Slide 14 — Configuration space (section divider)

No printed title in the bar. Section title in a grey rounded box, in blue: "Configuration space".

## Slide 15 — Degrees of freedom

No title in the bar. Text in a rounded box: "**Degrees of freedom (DoFs):** number of independent ways a system can move". Below: "Planar quadrotor: **3 DoFs**". A diagram: coordinate axes with origin "O", a vertical arrow labelled "Y" and a horizontal arrow labelled "X". To the right, the quadrotor drawing tilted slightly upward to the right, with a horizontal dotted line and a second dotted line along the drone's arm, the angle between them labelled $\theta$. Below the drone, the label $(x, y, \theta)$.

## Slide 16 — Configuration space (definition)

No title in the bar. Text in a rounded box: "**Configuration space** $C$ : set of possible configurations that a system can be in".

## Slide 17 — Free space

No title in the bar. Text in a rounded box: "**Free space** $C_{\text{free}} \subseteq C$ : set of configurations where system is **not** in collision". Below, a diagram: the quadrotor drawing (slightly tilted) between two blue octagonal obstacles, one above-left of it and one below-right of it. The drone touches neither octagon.

## Slide 18 — Obstacle space

No title in the bar. Text in a rounded box: "**Obstacle space** $C_{\text{obs}} = C \setminus C_{\text{free}}$ : set of configurations where system **is** in collision". Below, the same two blue octagons with the quadrotor now placed so that its upper right rotor overlaps the upper octagon (the drone is in collision).

## Slide 19 — Configuration space obstacles

Title bar: "Configuration space obstacles". A video still (first frame of a video; the link is printed below). Left: a 3D scene on black with a white wireframe box and a light-blue floor, containing a twisted column made of red and green faces with yellow and blue edges, with a small white arrow pointing right at its middle. Right, on white: a red quadrilateral with a small green triangle on top, with a black dot inside the triangle. Yellow-and-black text at lower right: "An Obstacle". Printed link: https://www.youtube.com/watch?v=SBFwgR4K1Gk

## Slide 20 — Geometric motion planning in configuration space

No title in the bar. Text in a rounded box: "Geometric motion planning: Find path in $C_{\text{free}}$ from configuration $q_A$ to configuration $q_B$" ("Geometric motion planning:" in blue). Left, two paragraphs: "Good news: reduced problem back to that of finding path for point (in configuration space)" and "In theory: discretize configuration space and apply graph search" ("Good news:" and "In theory:" in blue). Right, a smaller copy of the twisted red and green column in a wireframe box from slide 19 (a video still, no link printed).

## Slide 21 — Curse of dimensionality

Title bar: "Curse of dimensionality". Top left: a black line drawing of a robot arm (base on a ground line, two links, a gripper at the end) with two dark-red filled circles near it, one near the arm's elbow and one near the gripper. Top centre-right: a rounded box with "$d$ DOFs". Lower left, a rounded box: "Bad news: graph is intractably large: $B^d$" ("Bad news:" in blue). Below it: "How do we even construct $C_{\text{free}}$ or $C_{\text{obs}}$?". Lower right: the twisted red and green column in a wireframe box (video still, as on slide 20). The symbols $B$ and $d$ are not defined on the slide.

## Slide 22 — Rapidly exploring randomized tree (RRT) (section divider with readings)

No title in the bar. Section title in a grey rounded box, in blue: "Rapidly exploring randomized tree (RRT)". Below, two reading references in italics with dash sub-items: "*Principles of Robot Autonomy*" with "Ch. 4.4.2", and "*Planning Algorithms*" with "Ch. 5.5".

## Slide 23 — RRT: key ideas

Title bar: "RRT: key ideas". Two numbered items: "1. Work directly in continuous configuration space" ("Work directly" in blue) and "2. Do not explicitly construct $C_{\text{obs}}$" ("Do not" in blue). On the right, the twisted red and green column in a wireframe box (video still).

## Slide 24 — RRT: key ideas (collision checking)

Title bar: "RRT: key ideas". The same two items as slide 23, plus "3. Leverage efficient collision checking algorithms (e.g., GJK)" ("collision checking" in blue). On the right, a still on black: on the left two faceted polyhedra (a dodecahedron-like shape in green, blue and purple above a pyramid-like shape in green, teal and purple) touching or overlapping; a rightward implication arrow (⟹); on the right a large translucent teal polyhedron with a purple tetrahedron inside it drawn with yellow edges and yellow vertex dots. Below, a rounded box: "Nice explanation of GJK:" with the link https://www.youtube.com/watch?v=ajv46BSqcK4

## Slide 25 — Rapidly-Exploring Randomized Tree (RRT): Iteration 0

Title bar: "Rapidly-Exploring Randomized Tree (RRT)". Subtitle "Iteration 0". This starts a step-by-step RRT example in a 2D space. Two dark-red rectangular obstacles: a tall vertical rectangle at the left-centre, and a shorter wide horizontal rectangle in the upper centre-right, higher than the first. A blue dot labelled $\bar{q}_A$ at the lower left (start), below and left of the vertical rectangle. A green dot labelled $\bar{q}_B$ at the upper right (goal), just right of the horizontal rectangle's top right. The tree so far is only the blue dot $\bar{q}_A$. Slides 25 to 40 all use this same layout, with the same obstacles and the same $\bar{q}_A$ and $\bar{q}_B$; only the changes are listed below.

## Slide 26 — RRT: Iteration 1, random sample

Subtitle "Iteration 1". New: a blue dot labelled $\bar{q}_{\text{rand}}$ in free space at the bottom, right of the vertical rectangle and below the horizontal one (about the lower-middle of the plot).

## Slide 27 — RRT: Iteration 1, direction to the sample

Subtitle "Iteration 1". New: a dotted line from $\bar{q}_A$ to $\bar{q}_{\text{rand}}$ (the only tree node is $\bar{q}_A$, so it is the nearest node).

## Slide 28 — RRT: Iteration 1, step of distance d

Subtitle "Iteration 1". New: a blue dot labelled $\bar{q}_s$ on the dotted line a short distance right of $\bar{q}_A$, and a black double-headed arrow between $\bar{q}_A$ and $\bar{q}_s$ labelled $d$ (the step size).

## Slide 29 — RRT: Iteration 1, edge added

Subtitle "Iteration 1". The dotted line, the $\bar{q}_{\text{rand}}$ dot and its label are gone. A solid black edge now joins $\bar{q}_A$ and $\bar{q}_s$; both are blue tree nodes. Label $\bar{q}_s$ remains.

## Slide 30 — RRT: Iteration 2, random sample

Subtitle "Iteration 2". The tree is $\bar{q}_A$ with the edge to the second node (the label $\bar{q}_s$ is gone). New: $\bar{q}_{\text{rand}}$ as a blue dot in free space just right of the vertical rectangle, at about its lower-middle height.

## Slide 31 — RRT: Iteration 2, nearest node

Subtitle "Iteration 2". New: the second tree node (the one added in iteration 1) is labelled $\bar{q}_{\text{near}}$, and a dotted line runs from it up and to the right to $\bar{q}_{\text{rand}}$ (in free space, right of the vertical rectangle); the dotted line clips the lower right corner of the vertical rectangle on its way.

## Slide 32 — RRT: Iteration 2, step toward the sample

Subtitle "Iteration 2". New: a blue dot labelled $\bar{q}_s$ on the dotted line, a short distance from $\bar{q}_{\text{near}}$, just below the bottom edge of the vertical rectangle (in free space). The dotted line continues past $\bar{q}_s$, across the rectangle's corner, to $\bar{q}_{\text{rand}}$.

## Slide 33 — RRT: Iteration 2, edge added

Subtitle "Iteration 2". The dotted line and $\bar{q}_{\text{rand}}$ are gone. A solid black edge joins $\bar{q}_{\text{near}}$ to the new node $\bar{q}_s$, which touches the bottom edge of the vertical rectangle from below. The tree is now a chain of three nodes, $\bar{q}_A$, $\bar{q}_{\text{near}}$ and $\bar{q}_s$, joined by two edges. Labels $\bar{q}_s$ and $\bar{q}_{\text{near}}$ remain.

## Slide 34 — RRT: Iteration 3, random sample

Subtitle "Iteration 3". The tree is the three-node chain (labels removed except $\bar{q}_A$). New: $\bar{q}_{\text{rand}}$ as a blue dot just left of the vertical rectangle, near its top (its label overlaps the rectangle's left edge).

## Slide 35 — RRT: Iteration 3, nearest node

Subtitle "Iteration 3". New: the top node of the chain (the one touching the bottom of the vertical rectangle) is labelled $\bar{q}_{\text{near}}$, and a dotted line runs from it up through the vertical rectangle to $\bar{q}_{\text{rand}}$.

## Slide 36 — RRT: Iteration 3, step toward the sample

Subtitle "Iteration 3". New: a blue dot labelled $\bar{q}_s$ on the dotted line, a short distance above $\bar{q}_{\text{near}}$. $\bar{q}_s$ lies **inside** the vertical dark-red rectangle (in the obstacle); $\bar{q}_{\text{near}}$ itself is just below the rectangle's bottom edge, in free space. A short solid line joins $\bar{q}_{\text{near}}$ to $\bar{q}_s$. $\bar{q}_{\text{rand}}$ is still shown, a blue dot left of the rectangle's left edge (in free space), with the dotted line running to it through the rectangle.

## Slide 37 — RRT: Iteration 3, sample rejected

Subtitle "Iteration 3". The dotted line, $\bar{q}_{\text{rand}}$, the node inside the rectangle and its edge are gone. The tree is unchanged from the end of iteration 2 (three nodes, two edges, only $\bar{q}_A$ labelled): no node was added in this iteration.

## Slide 38 — RRT: Iteration 4, random sample

Subtitle "Iteration 4". The tree is the three-node chain. New: $\bar{q}_{\text{rand}}$ as a blue dot in free space below and to the right of the tree, at the bottom of the plot.

## Slide 39 — RRT: Iteration 4, nearest node

Subtitle "Iteration 4". New: the top node of the chain (touching the bottom of the vertical rectangle) is labelled $\bar{q}_{\text{near}}$, with a dotted line to $\bar{q}_{\text{rand}}$ running down and to the right.

## Slide 40 — RRT: Iteration 4, step toward the sample

Subtitle "Iteration 4". New: a blue dot labelled $\bar{q}_s$ on the dotted line, a short distance down and to the right of $\bar{q}_{\text{near}}$, in free space, and a solid edge already joining $\bar{q}_{\text{near}}$ to it. The dotted line continues on to $\bar{q}_{\text{rand}}$. This is the last slide of iteration 4: the deck has no separate "edge added" slide for it, and slide 41 starts iteration 5 with $\bar{q}_s$ in the tree.

## Slide 41 — RRT: Iteration 5, random sample

Subtitle "Iteration 5". Same layout as slides 25 to 40. The tree now has four nodes: $\bar{q}_A$ at the lower left; a second node up and right of it; a third node just below the bottom edge of the vertical rectangle; and a fourth node down and to the right of the third, joined to it by a solid edge (this fourth node was added in iteration 4; the deck has no separate "edge added" slide for iteration 4). Edges: $\bar{q}_A$ to second node, second node to third node, third node to fourth node. New: $\bar{q}_{\text{rand}}$ as a blue dot inside the horizontal rectangle, near its lower right corner (the sample lies in an obstacle). No dotted line is drawn yet.

## Slide 42 — RRT: Iteration 5, nearest node

Subtitle "Iteration 5". New: the fourth node (the rightmost node in the tree) is labelled $\bar{q}_{\text{near}}$, and a long dotted line runs from it up and to the right to $\bar{q}_{\text{rand}}$ in the horizontal rectangle.

## Slide 43 — RRT: Iteration 5, step toward the sample

Subtitle "Iteration 5". New: a blue dot labelled $\bar{q}_s$ on the dotted line a short distance up and to the right of $\bar{q}_{\text{near}}$, in free space (right of the vertical rectangle), although $\bar{q}_{\text{rand}}$ lies inside the horizontal rectangle. A solid edge already joins $\bar{q}_{\text{near}}$ to $\bar{q}_s$, and the dotted line still continues to $\bar{q}_{\text{rand}}$.

## Slide 44 — RRT: Iteration 5, edge added

Subtitle "Iteration 5". The dotted line, $\bar{q}_{\text{rand}}$ and the labels $\bar{q}_{\text{near}}$ and $\bar{q}_s$ are gone. A solid edge joins the previous fourth node to the new fifth node $\bar{q}_s$. The tree now has five nodes in a chain that zigzags below and to the right of the vertical rectangle's bottom edge: $\bar{q}_A$, second, third (just below the rectangle), fourth (lower, to the right), fifth (up again, right of the rectangle).

## Slide 45 — RRT: Iteration 6, random sample

Subtitle "Iteration 6". The five-node tree is unchanged. New: $\bar{q}_{\text{rand}}$ as a blue dot below the tree, near the bottom edge of the plot, a bit right of the second node's x position. The label is near the bottom edge of the page.

## Slide 46 — RRT: Iteration 6, step toward the sample

Subtitle "Iteration 6". The five-node tree of slide 44 is unchanged. New: a short dotted segment from the second node (the one next to $\bar{q}_A$) down to the blue dot $\bar{q}_{\text{rand}}$, and a blue dot labelled $\bar{q}_s$ on it, a short distance below the second node and just above $\bar{q}_{\text{rand}}$; both dots are in free space below the tree. The dotted line, a solid short edge to $\bar{q}_s$ and the dots overlap closely here; the nearest node is not labelled on this slide but is the second node from which the segment starts.

## Slide 47 — RRT: Iteration 6, edge added

Subtitle "Iteration 6". The dotted line, $\bar{q}_{\text{rand}}$ and $\bar{q}_s$ labels are gone. A solid edge joins the second node to a new sixth node just below it (down and slightly right). The tree now has six nodes: the five-node zigzag plus this branch off the second node. Only $\bar{q}_A$ and $\bar{q}_B$ are labelled.

## Slide 48 — RRT (Algorithm 1)

Title bar: "RRT". Pseudocode, in a boxed algorithm environment. The text is reproduced line by line (a typo "fo" in the third step is as printed; $q_A$ is typed without a bar in the comment and $\bar{q}_s$ appears once as $\bar{q}_S$ with a capital S subscript in the collision test).

**Algorithm 1:** Rapidly-Exploring Randomized Tree (RRT)

1. Initialize graph G with vertex set $V = \{\bar{q}_A\}$ // Here, $q_A$ is the starting configuration ;
2. **while** *Goal not reached* **do**
    1. $\bar{q}_{\text{rand}} \leftarrow$ Randomly sample a configuration (i.e., a point in configuration space) ;
    2. $\bar{q}_{\text{near}} \leftarrow$ Find vertex in $V$ that is nearest fo $\bar{q}_{\text{rand}}$ ;
    3. $\bar{q}_{\text{s}} \leftarrow$ **Extend**($\bar{q}_{\text{near}}$, $\bar{q}_{\text{rand}}$) ;
    4. **if** *$\bar{q}_S$ is in collision* **then**
        1. continue ;
    5. **else**
        1. Add $\bar{q}_{\text{s}}$ to $V$ ;
        2. Add edge between $\bar{q}_{\text{near}}$ and $\bar{q}_{\text{s}}$ ;
        3. **if** $\|\bar{q}_S - \bar{q}_B\| < \epsilon$ **then**
            1. // If we are close enough to the goal ;
            2. **Return** SUCCESS
            3. **end**
        4. **end**
    6. **end**
3. **end**

(The listing closes the nested blocks with "end" lines as printed: after "Return SUCCESS" an "end", then an "end" closing the else branch, then an "end" closing the while loop.)

## Slide 49 — RRT (animation frame)

Title bar: "RRT". A single frame of an animation (a GIF). The pale white-grey square panel is almost empty: only a tiny green dot near the centre (the root of the tree before it has grown). Underneath, the underlined link: https://en.wikipedia.org/wiki/Rapidly-exploring_random_tree#/media/File:Rapidly-exploring_Random_Tree_(RRT)_500x373.gif. Nothing else in the frame should be read as a result.

## Slide 50 — RRT (video frame, tree in a 2D map)

Title bar: "RRT". A single frame of a video; link below: https://www.youtube.com/watch?v=FAFw8DoKvik. A square 2D plot with a thick dark-red border, both axes running from -10 to 10 with a dotted grid, and the number "25" printed above the plot (a frame or iteration counter; its meaning is not stated). Red rectangular obstacles: a wide bar at the upper left (about x from -8 to -1, y from 5.6 to 7.1); a very tall rectangle in the upper centre-right (about x from 0.7 to 5, y from -1.2 to 8.8); a shorter wide bar at the right attached to the tall rectangle's right side (about x from 5 to 8.4, y from 3.3 to 4.5); a large square at the lower left (about x from -8 to -3.2, y from -7.6 to -2.7); and a narrow tall rectangle at the lower right (about x 5.5 to 6.4, y from -8.4 to -4.7). A yellow square at the origin (0, 0) marks the start. A magenta square at about (5.8, 5.2), just above the right-hand bar, marks the goal. A thin blue-teal tree with roughly 40–45 small green nodes spreads from the yellow square through the free space to the left, above and below: left to about (-5.2, -2) and (-4.7, 0.8), up the tall rectangle's left side to about (0.8, 5.4) (well short of its top at 8.8), and from there left along the underside of the upper-left bar to about (-3.5, 5), and down and to the right to about (4.4, -2.8). The tree has not reached the goal in this frame.

## Slide 51 — RRT: the Extend() step size

Title bar: "RRT". Text: "For the **Extend**() operation, we need to specify a "step-size" parameter: d". A small diagram: a blue dot labelled $\bar{q}_{\text{near}}$ at the left, a blue dot labelled $\bar{q}_s$ a short distance to its right along a dotted line that continues to a blue dot labelled $\bar{q}_{\text{rand}}$ far to the right and slightly higher; a black double-headed arrow above the first two dots labelled $d$. Below: "We ignored the fact that points along the segment joining $\bar{q}_{\text{near}}$ and $\bar{q}_s$ may be in collision even if $\bar{q}_s$ is not. We should really be checking the entire segment if collision-free. But, for small step-size, it's reasonable to just check $\bar{q}_s$ ."

## Slide 52 — RRT: no explicit construction of the obstacle space

Title bar: "RRT". Text in a rounded box: "Important: RRTs don't require an explicit construction of $C_{\text{obs}}$. We just need to check if the robot is in collision with an obstacle for some *specific* configuration." ("Important:" and "don't require an explicit construction" in blue). Two bullets: "Collision checking can be done very efficiently. Lots of software (developed for video game engines!)" and "This is the primary reason RRTs work so well."

## Slide 53 — RRT (video: piano mover's problem in a house)

Title bar: "RRT". A video still (first frame; link below). An isometric, cut-away 3D view of a small building with three rooms separated by grey walls, in light grey. Furniture: bookshelves (beige), round and rectangular tables with chairs, floor lamps, and a black grand piano in the upper room. Printed link: https://www.youtube.com/watch?v=HdfAzUXvmOQ&ab_channel=RoboticsLibrary

## Slide 54 — RRT (video: polynomial trajectory planning)

Title bar: "RRT". A video still showing a title card: "Polynomial Trajectory Planning for Quadrotor Flight", "Charles Richter, Adam Bry, Nicholas Roy", "Robust Robotics Group", with the logos MIT, MIT AeroAstro and CSAIL at the bottom, on a white card with black side bars. Printed link: https://www.youtube.com/watch?v=ul7YboQA5OY

## Slide 55 — RRT: recovering the path

Title bar: "RRT". Text in a rounded box: "We can recover the actual path from A to B by keeping track of parents (similar to discrete search)" ("keeping track of parents" in blue). Below: "The path returned by RRT can be quite jagged".

## Slide 56 — RRT (video: PR2 robot arm planning)

Title bar: "RRT". A video still (first frame; link below) of a laboratory room: a white and grey two-armed PR2 robot (the label "PR2" is on its chest) standing behind a wooden table. On the table are a book (left) and a black mug (centre). Behind: filing cabinets, a whiteboard with diagrams, computer monitors, yellow chairs, a side table with a basket and cups, and a white cabinet with an open door at the left; a dark-blue carpet. Printed link: https://www.youtube.com/watch?v=vW74bC-Ygb4

## Slide 57 — RRT: variants

Title bar: "RRT". Text in a rounded box: "There are many variants of RRTs (see Ch. 5 of Planning Algorithms for a few)" ("many" in blue). Then three paragraphs: "One important variant is RRT* (pronounced RRT-star)"; "RRT* returns (approximately) optimal paths (in contrast to standard RRTs, which just tries to find a feasible path)"; "Another variant: "bi-directional" RRT".

## Slide 58 — RRT vs RRT* (2D map, video frames)

Title bar: "RRT vs RRT*". Two side-by-side plots, headed "RRT" (left) and "RRT*" (right), each a frame of the same video; link below: https://www.youtube.com/watch?v=YKiQTJpPFkA. Both plots show the same map as slide 50 (axes -10 to 10, five red obstacles, yellow start square at the origin, magenta goal square near (5.8, 5.2), the counter "25" above each plot) and the same tree. The two panels are the same image (a pixel comparison finds them identical but for two pixels), and the same frame as slide 50. The PDF holds only this opening frame; the comparison itself is in the video.

## Slide 59 — RRT vs RRT* (PR2 robot, video frames)

Title bar: "RRT vs RRT*". Two side-by-side video stills headed "RRT" (left) and "RRT*" (right), both showing the same PR2 laboratory scene as slide 56 (PR2 robot behind a table with a book and a mug). The two frames look identical; they are first frames of two videos and no link is printed.

## Slide 60 — Completeness

Title bar: "Completeness". Text: "Suppose there exists a path from $\bar{q}_A$ to $\bar{q}_B$. Will an RRT find it?" Then a rounded box: "Completeness: A planning algorithm is complete if it finds a path from start to goal if one exists (and does so in a finite amount of time). If a path doesn't exist, the algorithm will still terminate and return "failure" (as opposed to running forever)." ("Completeness:" in blue).

## Slide 61 — Completeness (RRTs are not complete)

Title bar: "Completeness". Two paragraphs: "The discrete search algorithms we discussed are complete (for discrete problems)." and "However, RRTs are not complete. They may run forever if there is no path from start to goal." ("not complete" in blue).

## Slide 62 — Probabilistic Completeness

Title bar: "Probabilistic Completeness". Text in a rounded box: "RRTs are probabilistically complete:" ("probabilistically complete" in blue), then "If a path exists, the probability that RRT finds a solution converges to one as the # of iterations goes to infinity". Below the box, smaller: "(under some mild technical conditions having to do with enough separation between obstacles; you will explore this in next assignment)".
