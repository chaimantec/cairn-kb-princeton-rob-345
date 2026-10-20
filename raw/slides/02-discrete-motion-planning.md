---
title: Lecture 2 — Discrete Motion Planning (slide deck)
lecture: 2
slides: 79
source_pdf: https://www.dropbox.com/scl/fi/pnwucnirlwgviqwaj67hl/Lecture2.pdf?rlkey=6s2et2apw9rtnvr8x2ke243sp&dl=0
numbering: PDF page N = Slide N for all 79 pages (1:1). Pages 1, 3 and 4 print no number; their labels (1, 3, 4) are inferred from position.
figure_audit: An independent reader checked seven figure-heavy slides (24, 33, 45, 56, 63, 73, 76) against the PDF. All agreed in substance; the path on slide 24 was confirmed cell by cell, slide 56's red set was listed in full, and a label position on slide 73 was corrected.
images: 22 slides are rendered and shown under their headings (2, 5, 7, 9–11, 15, 17–19, 22, 24, 27, 31, 32, 34, 41, 46, 59, 72, 74, 76). Not rendered — the title page and section dividers (1, 13, 21, 29, 30, 50, 61, 67, 78); slides 3 and 4, the course topic map already rendered as Lecture 1 slide 33; text-only slides (8, 12, 14, 16, 20, 64, 65, 69); pseudocode transcribed in full (35–38, 79); repeats and build steps of a rendered slide (6 repeats 5; 23, 25, 26 and 28 repeat the grid of 24; 33, 63 and 68 repeat the graph of 34; 39, 40, 42–45, 47–49, 51–58 and 60 are steps of the BFS and DFS walk-throughs, of which 41, 46 and 59 are rendered; 70, 71, 73 and 75 are steps of the A* walk-through, of which 72 and 74 are rendered; 62 shows the same panel as 76); slide 66, a news-article screenshot whose content is its headline, transcribed; and slide 77, a video frame of title text, transcribed.
---

# Lecture 2 — Discrete Motion Planning: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 2 deck (speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Diagrams, grid worked examples, photographs and video stills are described in prose since the KB is read as text.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 79 pages, and the last printed number is 79. Slides 1, 3 and 4 print no number in the corner, so their labels are inferred from position (slide 1 is the title page; slides 3 and 4 are the topic-map pages between printed slides 2 and 5).

Companion pages: [wiki page for this lecture](../../wiki/02-discrete-motion-planning.md) · [transcript](../transcripts/02-discrete-motion-planning.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Motivating goal: autonomous vision-based navigation |
| 3–4 | Topic map (Planning and control, Localization and mapping, Robot learning) |
| 5–11 | Geometric motion planning and the piano mover's problem; examples of planning (Zoox, protein folding, Rubik's cube) |
| 12 | Problem statement and assumptions of geometric motion planning |
| 13–20 | Configuration space: degrees of freedom, free space and obstacle space, configuration-space obstacles |
| 21–26 | Discrete planning: discretization of the workspace into a grid |
| 27–28 | Graph search; planning as graph search |
| 29–34 | Worked example setup: 5-by-5 grid, vertices, edges, vertex labels |
| 35–38 | Algorithm 1: Forward Search (pseudocode) |
| 39–49 | Forward search with FIFO queue (breadth-first search) worked on the grid |
| 50–60 | Depth-first search (LIFO queue) worked on the same grid |
| 61–62 | A* search: two limitations of BFS |
| 63–66 | Cost of a plan, the A* key idea, Dijkstra's algorithm |
| 67–75 | A* worked example (C, H, F values; alive and dead vertices) |
| 76–77 | BFS vs A* comparison; learned search heuristics (Tesla AI Day) |
| 78–79 | A*: full algorithm (pseudocode) |

---

## Slide 1 — Lecture 2: Discrete Motion Planning

Title page. Title in blue in a rounded box: "Lecture 2: Discrete Motion Planning". Below it, a faded wide photograph of a small quadrotor drone seen from the front (black propellers on left and right arms, circuit board in the centre with a small camera module on a vertical board, red and black wires). Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred).

## Slide 2 — Motivating goal for course: autonomous vision-based navigation

![Slide 2 — Motivating goal for course: autonomous vision-based navigation](../images/02-discrete-motion-planning/slide-2.jpg)

Text in a rounded box: "Motivating goal for course: autonomous vision-based navigation" (the last three words in blue). Below, a video still: an indoor flight arena with netting and a white wall, green artificial turf marked with white tape lines, and five tall orange cylindrical columns hanging or standing in the space. A very small drone with a blue light sits on the turf at the bottom left near a tape line. A table with a blue box is at the upper right. This is the first frame of a video; no URL is printed.

## Slide 3 — Topic map (Planning and control highlighted in context)

No printed title and no printed number (label inferred). Three rounded cards side by side, each with a blue heading, a picture and four lines of topics:

- Left card, "Planning and control": picture of a blue wireframe rendering of two cars on a road with a planned path curving ahead. Topics: "**Geometric planning**" (bold), "Robot dynamics", "Feedback control", "Planning with dynamics". This card has a slightly heavier border.
- Middle card, "Localization, mapping": picture of a forest trail with a coloured voxel/point map overlay and a small figure on the path. Topics: "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card, "Robot learning": picture of a humanoid robot in a kitchen beside a person wearing a headset. Topics: "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

All three cards are shown at full strength.

## Slide 4 — Topic map with Planning and control emphasised

No printed title and no printed number (label inferred). The same three-card topic map as slide 3, but the "Localization, mapping" and "Robot learning" cards (headings, pictures and topic lists) are faded to light grey, leaving only the "Planning and control" card at full strength, with "Geometric planning" in bold.

## Slide 5 — Geometric Motion Planning

![Slide 5 — Geometric Motion Planning](../images/02-discrete-motion-planning/slide-5.jpg)

Title bar: "Geometric Motion Planning". Text: "**Assume:** we have a geometric model of environment" ("geometric model" in blue). Below, a large point-cloud image of a street scene seen from street level, in false colour: road surface in dark blue, trees and building walls in green, utility poles and wires in yellow-orange, and cars and other objects in orange; background black. Crosswalk stripes are green. No source credit is printed.

## Slide 6 — Geometric Motion Planning (question)

Title bar: "Geometric Motion Planning". Text in a rounded box: "**Question:** how can we get robot from A to B without collisions?" ("without collisions" in blue). Same point-cloud street image as slide 5 below it.

## Slide 7 — Piano Mover's Problem (video)

![Slide 7 — Piano Mover's Problem (video)](../images/02-discrete-motion-planning/slide-7.jpg)

Title bar: "Piano Mover's Problem". A video still on a flat purple-blue background showing a red cartoon grand piano with its lid propped open, tilted, with brown legs. Below the video, the underlined link: https://www.youtube.com/watch?v=cXm3WW-geD8

## Slide 8 — Piano Mover's Problem

Title bar: "Piano Mover's Problem". Three paragraphs:

- "Piano mover's problem: long history in robotics (since ~1980s)" ("Piano mover's problem:" in blue)
- "Lots of early work on understanding computational complexity of problem (PSPACE-complete)" ("computational complexity" in blue)
- "Today, the term "piano mover's problem" is synonymous with "motion planning"" ("motion planning" in blue)

## Slide 9 — Examples of Planning (Zoox)

![Slide 9 — Examples of Planning (Zoox)](../images/02-discrete-motion-planning/slide-9.jpg)

Title bar: "Examples of Planning". A two-part video still. Top: a camera view from a vehicle at a San Francisco intersection (street sign "Pacific"), with a white van at the left, a small black pill label "A  3x SPEED · SAN FRANCISCO", and pink and blue 3D bounding boxes drawn around pedestrians (pink, many crowded near the crosswalk at the right) and vehicles (blue). Bottom: a rendered 3D scene of the same intersection from behind a white car in the centre, with blue box-shaped cars, pink cylinders for pedestrians, grey blocks for buildings and kerbs, white crosswalk stripes, and a green-teal patch on the road ahead of the white car. Caption: "Source: Zoox".

## Slide 10 — Examples of Planning (protein folding)

![Slide 10 — Examples of Planning (protein folding)](../images/02-discrete-motion-planning/slide-10.jpg)

Title bar: "Examples of Planning". Heading "Protein folding". Two rows of four images each, left to right showing progress from an unfolded to a folded structure. Top row: four pale-green square panels of coloured 3D blocks (orange, purple, blue, green, grey) that assemble into a more compact shape; the last panel shows a single purple Z-shaped block. Bottom row: four rainbow-coloured ribbon renderings of a protein chain, loose and extended at the left and compact with helices at the right. Caption: "Source: https://parasollab.web.illinois.edu/research/protein-folding/".

## Slide 11 — Examples of Planning (Rubik's cube video)

![Slide 11 — Examples of Planning (Rubik's cube video)](../images/02-discrete-motion-planning/slide-11.jpg)

Title bar: "Examples of Planning". A video still of a Rubik's cube held by metal rods and motor shafts in a machine, with blurred metal fixtures around it; the cube faces show blue, red, yellow, green, orange and white squares. Below, the underlined link: https://www.youtube.com/watch?v=OZu9gjQJUQs

## Slide 12 — Geometric motion planning

Title bar: "Geometric motion planning". First box: "**Problem:** find path from configuration A to configuration B without collisions". Second box, "**Assumptions:**", numbered:

1. Any path is feasible to follow (ignore dynamics)
2. Robot state is perfectly known
3. Map of environment is provided

(The first words of each item, "Any path is feasible", "Robot state" and "Map", are in blue.)

## Slide 13 — Configuration space

Section divider: the single text "Configuration space" in blue in a grey rounded box.

## Slide 14 — Degrees of freedom (DoFs)

No title in the title bar. Box: "**Degrees of freedom (DoFs):** number of independent ways a system can move". Then "**Examples:**" and four bullets:

- Point in d-dimensional space: **d DoFs**
- N points in d-dimensional space: **N·d DoFs**
- Pendulum: **1 DoF**
- Planar quadrotor: **3 DoFs**

## Slide 15 — Degrees of freedom: planar quadrotor

![Slide 15 — Degrees of freedom: planar quadrotor](../images/02-discrete-motion-planning/slide-15.png)

No title in the title bar. Same definition box as slide 14. Text: "Planar quadrotor: **3 DoFs**". Figure: a pair of black axes with an arrow up labelled "Y", an arrow right labelled "X" and the origin labelled "O" at the corner. To the right, a side-view drawing of a quadrotor (a black body with a red dome, two arms with a propeller disc on each) tilted slightly with the right side higher; a dotted horizontal line extends from the body to the right, a second dotted line extends along the tilted arm, and the angle between them is labelled $\theta$. Below the quadrotor the label $(x, y, \theta)$.

## Slide 16 — Configuration space

No title in the title bar. Box: "**Configuration space** $C$**:** set of possible configurations that a system can be in". Then "**Examples:**" and four bullets:

- Point in d-dimensional space: $C = \mathbb{R}^d$
- N points in d-dimensional space: $C = \mathbb{R}^{N \cdot d}$
- Pendulum: $C = S^1$ (circle)
- Planar quadrotor: $\mathbb{R}^2 \times S^1$

## Slide 17 — Free space

![Slide 17 — Free space](../images/02-discrete-motion-planning/slide-17.jpg)

No title in the title bar. Box: "**Free space** $C_{free} \subseteq C$**:** set of configurations where system is **not** in collision". Figure: the planar quadrotor drawing (tilted, left propeller lower) in the centre, with two blue octagons as obstacles, one above and slightly left of the quadrotor's body and one below and to the right. The quadrotor touches neither octagon.

## Slide 18 — Obstacle space

![Slide 18 — Obstacle space](../images/02-discrete-motion-planning/slide-18.jpg)

No title in the title bar. Box: "**Obstacle space** $C_{obs} = C \setminus C_{free}$**:** set of configurations where system **is** in collision". Figure: the same two blue octagons, but the quadrotor is moved up and to the left so that its right propeller disc passes behind the upper octagon (overlapping it); the second octagon is still at the lower right.

## Slide 19 — Configuration space obstacles (video)

![Slide 19 — Configuration space obstacles (video)](../images/02-discrete-motion-planning/slide-19.jpg)

Title bar: "Configuration space obstacles". A video still. Left: a black background with a white perspective grid, a vertical blue line down the centre, an orange sphere with a pink/magenta arrow pointing up and two white arrows pointing down-left and down-right from it (looks like a 3D axis/coordinate-frame gizmo). Right: on white, a small green triangle with a black dot inside it; a yellow-and-brown caption "Rotation" at the bottom right. Below, the underlined link: https://www.youtube.com/watch?v=SBFwgR4K1Gk

## Slide 20 — Geometric motion planning: path in free space

No title in the title bar. Box: "Geometric motion planning: Find path in $C_{free}$ from configuration $q_A$ to configuration $q_B$" ("Geometric motion planning:" in blue).

## Slide 21 — Discrete Planning

Section divider: the single text "Discrete Planning" in blue in a grey rounded box.

## Slide 22 — Discretization

![Slide 22 — Discretization](../images/02-discrete-motion-planning/slide-22.jpg)

Title bar: "Discretization". A continuous workspace with four solid blue obstacles on white and two letters: "A" at the bottom left and "B" at the upper right. Obstacles: a tilted square at the upper left; a tall tilted rectangle at the right; a small ellipse in the centre-bottom; a tilted rectangle at the lower left just above "A". No grid yet.

## Slide 23 — Discretization (grid overlay)

Title bar: "Discretization". The same workspace, with a thin black grid overlaid: 11 columns by 13 rows of square cells. "A" sits in the bottom-left region (column 1, second row from the bottom) and "B" in column 10, second row from the top. The blue obstacles are unchanged and are not snapped to the grid (they cut across cell boundaries).

## Slide 24 — Discretization (path on the grid)

![Slide 24 — Discretization (path on the grid)](../images/02-discrete-motion-planning/slide-24.jpg)

Title bar: "Discretization". Same 11-by-13 grid and obstacles as slide 23, plus a thick green path made of whole grid cells from A to B, drawn four-connected (no diagonal steps). Reading from A: along the second-to-last row from column 1 to column 5; up column 5 for several rows; one cell left into column 4 at the lower end of a short vertical run; up column 4 to the sixth row from the top; right along that row from column 4 to column 7; up column 7 to the second row from the top; then right along that row from column 7 to column 10, ending at B. Counting rows from the top: row 12 from column 1 to column 5, column 5 up to row 9, one step left to column 4, column 4 up to row 6, row 6 to column 7, column 7 up to row 2, row 2 to column 10 (checked against the page at 600 dpi).

## Slide 25 — Discretization allows graph search

Title bar: "Discretization". Left text: "Discretization allows us to apply powerful algorithms for graph search to solve planning problem" ("graph search" in blue). Right: the same 11-by-13 grid, obstacles and green A-to-B path as slide 24, drawn smaller and moved to the right half of the slide.

## Slide 26 — Discretization (choices we made)

Title bar: "Discretization". Left text: "Choices we made:" followed by three bullets:

- Uniform grid
- 4-connected (e.g., instead of allowing diagonal motion, i.e., 8-connected)
- Resolution of grid (finer grid is better approximation, but makes planning harder)

Right: the same grid, obstacles and green path as slide 25.

## Slide 27 — Graph Search (definition of a graph)

![Slide 27 — Graph Search (definition of a graph)](../images/02-discrete-motion-planning/slide-27.jpg)

Title bar: "Graph Search". Text: "Graph: collection of vertices (nodes) and edges" ("Graph:", "vertices (nodes)" and "edges" in blue), then a bullet "Edges define connectivity". Figure: six blue dots joined by black line segments. Dots are at roughly: top-left-centre, upper right, far left, centre, lower right, bottom centre. Edges: far-left to top-left-centre; far-left to upper-right (a long line crossing another); top-left-centre to upper-right; top-left-centre to bottom-centre; upper-right to lower-right; centre to lower-right; centre to bottom-centre; bottom-centre to lower-right. No labels.

## Slide 28 — Planning as Graph Search

Title bar: "Planning as Graph Search". Left text, three paragraphs: "Associate a vertex with each cell in grid" ("vertex" in blue); "Connect vertices with edges based on 4-connectivity (or 8-connectivity)" ("edges" in blue); "Delete any vertices (and corresponding edges) that have obstacle" ("Delete" and "obstacle" in blue). Right: the 11-by-13 grid with the four blue obstacles and the letters A and B, without the green path.

## Slide 29 — Planning as graph search: Example

Section divider: the single text "Planning as graph search: Example" in blue in a grey rounded box.

## Slide 30 — Planning as graph search: Example (readings)

The same divider box "Planning as graph search: Example", with a reading list below it in italics and plain text:

*Principles of Robot Autonomy*
- Ch. 4.2

*Planning Algorithms*
- Ch. 1.1, 1.2, 1.3
- Ch 2.1, 2.2

## Slide 31 — Example (the 5-by-5 grid)

![Slide 31 — Example (the 5-by-5 grid)](../images/02-discrete-motion-planning/slide-31.jpg)

Title bar: "Example". A 5-by-5 grid of square cells (5 columns, 5 rows). Letters: "B" in the top-right cell and "A" in the cell in column 2, third row from the bottom. Solid blue obstacle cells form an upside-down "L"/"T" shape: two cells in the second row from the top (columns 2 and 3) and two more cells below the right one (column 3, the third and fourth rows from the top). In coordinates (column, row) with (1,1) at the bottom left and (5,5) at the top right, the obstacle cells are (2,4), (3,4), (3,3) and (3,2). A is at (2,3) and B is at (5,5).

Numbered text below:

1. Associate a vertex with each cell
2. Edges connect vertices that we can travel between in one step
3. Remove vertices (and associated edges) that are occupied by obstacles

## Slide 32 — Example (full graph)

![Slide 32 — Example (full graph)](../images/02-discrete-motion-planning/slide-32.jpg)

Title bar: "Example". Same grid as slide 31, with the obstacle cells now pale blue and a black vertex dot at the centre of every one of the 25 cells, including the obstacle cells. Black edges join every pair of horizontally or vertically adjacent vertices, forming a complete 5-by-5 lattice (4-connectivity). The same three numbered lines of text as slide 31.

## Slide 33 — Example (obstacle vertices removed)

Title bar: "Example". Same as slide 32 but the vertices in the four obstacle cells, (2,4), (3,4), (3,3) and (3,2), and all edges touching them are removed, leaving 21 vertices. Remaining edges, by coordinate: the whole top row (1,5) to (5,5); the whole bottom row (1,1) to (5,1); the whole left column (1,1) to (1,5); the whole column 4 from (4,1) to (4,5) and the whole column 5 from (5,1) to (5,5); horizontal edges (4,4)-(5,4), (4,3)-(5,3), (4,2)-(5,2); horizontal edges (1,3)-(2,3) and (1,2)-(2,2); and a vertical edge column 2 from (2,3) down to (2,1) via (2,2). Vertex (1,4) stays connected only vertically. The same three numbered lines of text.

## Slide 34 — Example (vertex labels)

![Slide 34 — Example (vertex labels)](../images/02-discrete-motion-planning/slide-34.jpg)

Title bar: "Example". Same graph as slide 33, with corner labels "(5,5)" to the right of the top-right vertex and "(1,1)" to the left of the bottom-left vertex. Text below: "We will label vertices: (i,j) = (x, y) = (column, row)" (the formula in blue). Then "Examples: A : (2,3)" and "B : (5,5)".

## Slide 35 — Algorithm: Forward Search

Title bar: "Algorithm: Forward Search". Typeset algorithm box, reproduced line by line (indentation shows nesting; the slide shows vertical rules for the blocks):

```
Algorithm 1: Forward Search
Q.Insert(A) and mark A as visited;
while Q not empty do
    x <- Q.GetVertex();
    if x in x_G then
        // x_G is goal set, e.g., {B};
        Return SUCCESS;
    end
    for all neighbors x' of x do
        if x' not visited then
            Parent(x') <- x;
            Mark x' as visited;
            Q.Insert(x');
        end
    end
end
Return FAILURE;
```

In the typeset slide: $x \leftarrow$ Q.GetVertex(); the test is $x \in x_G$; the goal set is $x_G$; the neighbours are $x'$ ("x prime"); and "Parent($x'$) $\leftarrow x$".

## Slide 36 — Algorithm: Forward Search (while loop highlighted)

Title bar: "Algorithm: Forward Search". Same algorithm as slide 35. The line "while Q not empty do" is circled in a rounded grey outline, with the blue callout to its right: "Data structure: queue of vertices we are still exploring".

## Slide 37 — Algorithm: Forward Search (GetVertex highlighted)

Title bar: "Algorithm: Forward Search". Same algorithm as slide 35. The line "x <- Q.GetVertex();" is circled, with the blue callout: "Remove vertex from $Q$ to explore".

## Slide 38 — Algorithm: Forward Search (neighbour loop highlighted)

Title bar: "Algorithm: Forward Search". Same algorithm as slide 35. The whole "for all neighbors x' of x do ... end" block (through its inner "end") is enclosed in a rounded grey box, with the blue callout: "Incrementally explore graph by visiting neighbors".

## Slide 39 — Example (A marked visited)

Title bar: "Example". Left text: "Q = {(2,3)} = {A}" (blue); "Mark A as visited"; "(visited vertices will be marked in red)" (the word "red" in red). Right: the 21-vertex graph of slide 34 drawn larger, with corner labels "(5,5)" and "(1,1)". Vertex A at (2,3) is now an orange-red dot; every other vertex is black. No parent arrows.

## Slide 40 — Example (Iteration 1: GetVertex)

Title bar: "Example". Centred blue heading "Iteration 1". Left text: "Q = {(2,3)} = {A}" (blue), then "x <- Q.GetVertex()" (typeset with a left arrow). Graph on the right is identical to slide 39: only A at (2,3) is red.

## Slide 41 — Example (BFS, iteration 1: neighbours of A)

![Slide 41 — Example (BFS, iteration 1: neighbours of A)](../images/02-discrete-motion-planning/slide-41.jpg)

Title bar: "Example". Centred blue heading "Iteration 1". Left text, top to bottom:

- "Q = {(2,3)} = {A}" (blue)
- "x <- Q.GetVertex()" (typeset, left arrow)
- "x = (2,3)"
- "Neighbors of x: {(1,3), (2,2)}"
- "Mark these as visited and add to Q"
- "Q = {(1,3), (2,2)}" (blue)

Graph on the right (corner labels "(5,5)" and "(1,1)"), same 21-vertex graph as slide 34: three vertices are now red (visited): (2,3), (1,3) and (2,2). All others black. No parent arrows are drawn.

## Slide 42 — Example (BFS, iteration 2 begins)

Title bar: "Example". Heading "Iteration 2". Left text: "Q = {(1,3), (2,2)}" (blue); "x <- Q.GetVertex()". Graph unchanged from slide 41: red vertices (2,3), (1,3), (2,2).

## Slide 43 — Example (BFS, iteration 2: FIFO)

Title bar: "Example". Heading "Iteration 2". Left text: "Q = {(1,3), (2,2)}" (blue); "x <- Q.GetVertex()"; "x = (1,3)  [Here, we implement "First-in-first-out"]". Graph unchanged: red vertices (2,3), (1,3), (2,2).

## Slide 44 — Example (BFS, iteration 2: neighbours of (1,3))

Title bar: "Example". Heading "Iteration 2". Left text:

- "Q = {(1,3), (2,2)}" (blue)
- "x <- Q.GetVertex()"
- "x = (1,3)  [Here, we implement "First-in-first-out"]"
- "Neighbors of x: {(1,4), (1,2), (2,3)}", where "(2,3)" is struck through with a blue line (already visited)
- "Mark unvisited as visited and add to Q"
- "Q = {(2,2), (1,4), (1,2)}" (blue)

Graph: red vertices are now (2,3), (1,3), (2,2), (1,4) and (1,2); the new reds are (1,4) and (1,2).

## Slide 45 — Example (BFS, iteration 3)

Title bar: "Example". Heading "Iteration 3". Left text:

- "Q = {(2,2), (1,4), (1,2)}" (blue)
- "x <- Q.GetVertex()"
- "x = (2,2)  ["First-in-first-out"]"
- "Neighbors of x: {(1,2), (2,1), (2,3)}", with "(1,2)," and "(2,3)" struck through
- "Mark unvisited as visited and add to Q"
- "Q = {(1,4), (1,2), (2,1)}" (blue)

Graph (corner labels "(5,5)" and "(1,1)"): new red vertex (2,1). Red vertices: (2,3), (1,3), (2,2), (1,4), (1,2), (2,1).

## Slide 46 — Example (BFS, iteration 4)

![Slide 46 — Example (BFS, iteration 4)](../images/02-discrete-motion-planning/slide-46.jpg)

Title bar: "Example". Heading "Iteration 4". Left text:

- "Q = {(1,4), (1,2), (2,1)}" (blue)
- "x <- Q.GetVertex()"
- "x = (1,4)  ["First-in-first-out"]"
- "Neighbors of x: {(1,5), (1,3)}", with "(1,3)" struck through
- "Mark unvisited as visited and add to Q"
- "Q = {(1,2), (2,1), (1,5)}" (blue)

Graph: new red vertex (1,5), the top-left corner. Red vertices: (2,3), (1,3), (2,2), (1,4), (1,2), (2,1), (1,5).

## Slide 47 — Example (BFS, iteration 5: and so on)

Title bar: "Example". Heading "Iteration 5". Left text: "… and so on …" and "(until x hits goal vertex B)". Graph unchanged from slide 46 (same seven red vertices).

## Slide 48 — Example (computing the path)

Title bar: "Example". Left text: "How to compute path?" and, indented, "Recursively follow "parent" from goal vertex to start vertex". Graph unchanged from slide 46 (same seven red vertices; no parent arrows are drawn).

## Slide 49 — Example (BFS)

Title bar: "Example". Left bullets:

- "We implemented Q.GetVertex() using "first-in-first-out (FIFO)""
  - "Breadth First Search (BFS)" (blue)
- "BFS searches all paths of length k before searching paths of length k+1"

Graph unchanged from slide 46.

## Slide 50 — Depth-first search (DFS)

Section divider: the single text "Depth-first search (DFS)" in blue in a grey rounded box.

## Slide 51 — Depth-First Search (DFS): LIFO

Title bar: "Depth-First Search (DFS)". Left text: "Let's explore another way to implement Q.GetVertex(): "Last-in-first-out" (LIFO)" ("Last-in-first-out" in blue). Graph (corner labels "(5,5)", "(1,1)"): the 21-vertex graph with only A at (2,3) red.

## Slide 52 — Depth-First Search (DFS): iteration 1

Title bar: "Depth-First Search (DFS)". Heading "Iteration 1". Left text:

- "Q = {(2,3)} = {A}" (blue)
- "x <- Q.GetVertex()"
- "x = (2,3)"
- "Neighbors: {(2,2), (1,3)}"
- "Q = {(2,2), (1,3)}" (blue)

Graph: red vertices (2,3), (2,2) and (1,3).

## Slide 53 — Depth-First Search (DFS): iteration 2

Title bar: "Depth-First Search (DFS)". Heading "Iteration 2". Left text:

- "Q = {(2,2), (1,3)}" (blue)
- "x <- Q.GetVertex()"
- "x = (1,3)" (the last-inserted vertex of Q is taken)
- "Neighbors: {(2,3), (1,2), (1,4)}", with "(2,3)," struck through
- "Q = {(2,2), (1,2), (1,4)}" (blue)

Graph: red vertices (2,3), (2,2), (1,3), (1,2), (1,4).

## Slide 54 — Depth-First Search (DFS): iteration 3

Title bar: "Depth-First Search (DFS)". Heading "Iteration 3". Left text:

- "Q = {(2,2), (1,2), (1,4)}" (blue)
- "x <- Q.GetVertex()"
- "x = (1,4)"
- "Neighbors: {(1,3), (1,5)}", with "(1,3)," struck through
- "Q = {(2,2), (1,2), (1,5)}" (blue)

Graph: red vertices as on slide 53 plus (1,5).

## Slide 55 — Depth-First Search (DFS): iteration 4

Title bar: "Depth-First Search (DFS)". Heading "Iteration 4". Left text:

- "Q = {(2,2), (1,2), (1,5)}" (blue)
- "x <- Q.GetVertex()"
- "x = (1,5)"
- "Neighbors: {(1,4), (2,5)}", with "(1,4)," struck through
- "Q = {(2,2), (1,2), (2,5)}" (blue)

Graph: red vertices as on slide 54 plus (2,5).

## Slide 56 — Depth-First Search (DFS): iteration 5

Title bar: "Depth-First Search (DFS)". Heading "Iteration 5". Left text:

- "Q = {(2,2), (1,2), (2,5)}" (blue)
- "x <- Q.GetVertex()"
- "x = (2,5)"
- "Neighbors: {(1,5), (3,5)}", with "(1,5)," struck through
- "Q = {(2,2), (1,2), (3,5)}" (blue)

Graph (corner labels "(5,5)" and "(1,1)"): eight red vertices, (1,5), (2,5), (3,5), (1,4), (1,3), (2,3), (1,2) and (2,2); (2,1) is still black. No ring marks the current vertex.

## Slide 57 — Depth-First Search (DFS): iteration 6

Title bar: "Depth-First Search (DFS)". Heading "Iteration 6". Left text:

- "Q = {(2,2), (1,2), (3,5)}" (blue)
- "x <- Q.GetVertex()"
- "x = (3,5)"
- "Neighbors: {(2,5), (4,5)}", with "(2,5)," struck through
- "Q = {(2,2), (1,2), (4,5)}" (blue)

Graph: red vertices as on slide 56 plus (4,5).

## Slide 58 — Depth-First Search (DFS): iteration 7

Title bar: "Depth-First Search (DFS)". Heading "Iteration 7". Left text:

- "Q = {(2,2), (1,2), (4,5)}" (blue)
- "x <- Q.GetVertex()"
- "x = (4,5)"
- "Neighbors: {(3,5), (5,5)}", with "(3,5)," struck through
- "Q = {(2,2), (1,2), (5,5)}" (blue)

Graph: red vertices as on slide 57 plus (5,5), the goal B (the red dot partly covers the faded "B").

## Slide 59 — Depth-First Search (DFS): iteration 8, done

![Slide 59 — Depth-First Search (DFS): iteration 8, done](../images/02-discrete-motion-planning/slide-59.jpg)

Title bar: "Depth-First Search (DFS)". Heading "Iteration 8". Left text:

- "Q = {(2,2), (1,2), (5,5)}" (blue)
- "x <- Q.GetVertex()"
- "x = (5,5)"
- "Done!" (bold, blue)

Graph unchanged from slide 58. The red vertices at the end of DFS are (2,3), (2,2), (1,3), (1,2), (1,4), (1,5), (2,5), (3,5), (4,5) and (5,5); the vertices (2,1), (3,1), (4,1), (5,1), (4,2), (5,2), (4,3), (5,3), (4,4), (5,4) are still black.

## Slide 60 — Depth-First Search (DFS): discussion

Title bar: "Depth-First Search (DFS)". Left bullets:

- "In general, DFS will keep exploring some path deeply until it hits a dead-end or the goal"
- "If it hits a dead-end, it will pick some other avenue and explore until the end, and so on…"
- "DFS may work well in certain cases (as compared to BFS)"
- "e.g., when the path is long and there are only few ways to get to the goal"

Graph unchanged from slide 59.

## Slide 61 — A* search

Section divider: the single text "A* search" in blue in a grey rounded box.

## Slide 62 — Two limitations of BFS

No title in the title bar. (The number "62" is in the PDF text layer at the right edge but is not visible in the rendered page.) Left text: "Two limitations of BFS:" ("Two limitations" in blue), then numbered:

1. Only optimal for path length
2. Slow exploration

Right: a white square panel with a thin grey border containing a light-blue obstacle shaped like an upside-down "L" or "7": a wide block across the top (about the left two-thirds of the obstacle) and a narrower vertical stem running down from its right end. A small black dot with an orange/yellow mark around it sits just left of the stem, below the wide block, labelled "A" (below and to the right of the dot). Near the top right corner, a black star with the label "B" to its lower left. The cells are too small to count. No search marks other than A are drawn.

[Ed: in the lecture this is an animation of BFS expanding uniformly from A (transcript ≈53:41, "maybe I'll play it again"); the PDF holds a single frame.]

## Slide 63 — Cost of a plan

Title bar: "Cost of a plan". Left text:

- "Suppose with every edge $e$, we associate:"
- $l(e)$ : Cost (or "loss") associated with traversing edge $e$. The words from $l(e)$ through "loss" are in blue.
- "Total cost of a plan: sum of costs along path from A to B" ("Total cost" in blue)
- In a rounded box: "Our goal: find path that minimizes total cost" ("Our goal:" and "minimizes" in blue)

Right: the 5-by-5 grid graph from slide 33/34 (21 black vertices, obstacle cells (2,4), (3,4), (3,3), (3,2) shaded blue-grey, faint "A" at (2,3) and faint "B" at the top-right cell; same edges as slide 33). No colours on vertices and no numbers.

## Slide 64 — A* algorithm: key idea

Title bar: "A* algorithm: key idea". Rounded box:

"The A* algorithm uses a heuristic to implement $Q.GetVertex()$:"

$$F(x) \triangleq C(x) + H(x)$$

Then "where", and two definitions:

- $C(x)$ : estimated cost-to-come from A to $x$
- $H(x)$ : estimated cost-to-go from $x$ to B

("estimated cost-to-come" and "estimated cost-to-go" are in blue.)

Below the box: "**Important:** $H(x)$ needs to be an underestimate (i.e., lower bound) on the optimal cost-to-go from $x$ to the goal", then two bullets:

- This is required for the algorithm to work correctly
- We can often get an underestimate $H(x)$ quite easily (e.g., Euclidean distance between $x$ and B for distance-optimal planning)

## Slide 65 — A* algorithm: key idea (Dijkstra's special case)

Title bar: "A* algorithm: key idea". The same box as slide 64, with $F(x) \triangleq C(x) + H(x)$ and the definitions of $C(x)$ and $H(x)$. Below it: "Special case: **Dijkstra's algorithm**" (bold, blue), then: Choose $H(x) = 0$ for all $x$.

## Slide 66 — Dijkstra's algorithm (article screenshot)

Title bar: "Dijkstra's algorithm". A screenshot of a web article. Headline (large bold): "The Simple, Elegant Algorithm That Makes Google Maps Possible". Subhead: "Edsger W. Dijkstra's short solution to a bottomless complexity." Byline: "By Michael Byrne"; date line "Mar 22 2015, 8:00am" with "Share" and "Tweet" buttons. Below, a photograph of an older man with a beard and glasses, in a grey cardigan, standing at a blackboard covered in chalk formulas (including "fib" expressions) and pointing at it with his right hand; a lectern is at the lower right. Credit under the photo: "IMAGE: ANDREAS F. BORCHERT/WIKI". Bottom link (underlined): https://www.vice.com/en_us/article/4x3pp9/the-simple-elegant-algorithm-that-makes-google-maps-possible

## Slide 67 — A* example

Section divider: the single text "A* example" in blue in a grey rounded box.

## Slide 68 — Setup

Title bar: "Setup". Left text:

- "Edge costs:  l(e) = 1 for every edge"
- "Cost-to-come  C(x):" with grey subtext "cost of the best path to x found so far"
- "Cost-to-go estimate  H(x) = |x₁ − 5| + |x₂ − 5|", i.e. $H(x) = |x_1 - 5| + |x_2 - 5|$, with grey subtext "Manhattan distance to B"
- "Priority:  F(x) = C(x) + H(x)" (blue)
- "Q is a priority queue: GetVertex() returns the vertex with the smallest F"

Right: the same 21-vertex 5-by-5 grid graph as slide 34 (obstacle cells (2,4), (3,4), (3,3), (3,2) in light blue; faint "A" at the (2,3) cell and "B" in the (5,5) cell), all vertices black, corner labels "(5,5)" at the top right and "(1,1)" at the bottom left.

## Slide 69 — Vertices: unvisited, alive, and dead

Title bar: "Vertices: unvisited, alive, and dead". Text: "For A*, it is helpful to think about three kinds of vertices:" then three bullets:

- "Unvisited": Vertices that we have not yet explored. ("Unvisited": in blue)
- "Alive": Vertices stored in $Q$. These are vertices we have encountered, but have not taken out from $Q$ yet.
- "Dead": Vertices removed from $Q$.

## Slide 70 — Initialization

Title bar: "Initialization". Left text:

- "C(A) = 0,   H(A) = 5,   F(A) = 5"
- "Q.Insert(A) with priority F(A) = 5"
- "Q = {(2,3)} = {A}" (blue)
- grey note, two lines: "Vertices in Q are marked in yellow" / "Expanded ("dead") vertices are marked in red"

Graph (same layout as slide 68, labels "(5,5)" and "(1,1)"): vertex A at (2,3) is yellow, with the small grey label "F=5" just above and to its right. All other vertices are black.

## Slide 71 — A* step: take A out of Q

No title in the title bar. Left text:

- "Q = {(2,3)} = {A}" (blue)
- "x <- Q.GetVertex()" (arrow as printed)
- "x = (2,3)      [smallest F in Q]"
- "x is not the goal, so mark x as "dead""

Graph: vertex (2,3) is red (dead) with a black ring drawn around it to show it is the current vertex x. All other vertices black. No F labels.

## Slide 72 — A* step: neighbours of A

![Slide 72 — A* step: neighbours of A](../images/02-discrete-motion-planning/slide-72.png)

No title in the title bar. Left text:

- "x = (2,3)"
- "Neighbors of x: {(1,3), (2,2)}"
- "C(1,3) = 0 + 1 = 1,   F = 1 + 6 = 7" and "C(2,2) = 0 + 1 = 1,   F = 1 + 6 = 7"
- "Insert both into Q with these priorities"
- "Q = {(1,3):7, (2,2):7}" (blue)

Graph: (2,3) red; (1,3) and (2,2) yellow, each with a grey "F=7" label ((1,3)'s label above and to its right, (2,2)'s label to its right). All others black. No ring.

## Slide 73 — A* step: neighbours of (1,3)

No title in the title bar. Left text:

- "Q = {(1,3):7, (2,2):7}" (blue)
- "x = (1,3)  [tie in F broken by smaller H]"
- "Neighbors of x: {(1,4), (1,2), (2,3)}"
- "C(1,4) = 2,   F = 2 + 5 = 7" and "C(1,2) = 2,   F = 2 + 7 = 9"
- grey: "(2,3) already "dead" — skip"
- "Q = {(1,4):7, (2,2):7, (1,2):9}" (blue)

Graph (corner labels "(5,5)" and "(1,1)", grey letters A and B): (1,3) red with a black ring (current x); (2,3) red; (1,4) yellow labelled "F=7" (above and right); (2,2) yellow labelled "F=7" (above and right); (1,2) yellow labelled "F=9" (above and right). All others black.

[Ed: under slide 68's heuristic, $H(1,3) = |1-5| + |3-5| = 6$ and $H(2,2) = |2-5| + |2-5| = 6$, so the printed tie-break "broken by smaller H" does not separate these two vertices. The slide takes (1,3).]

## Slide 74 — A* step: neighbours of (1,4)

![Slide 74 — A* step: neighbours of (1,4)](../images/02-discrete-motion-planning/slide-74.png)

No title in the title bar. Left text:

- "Q = {(1,4):7, (2,2):7, (1,2):9}" (blue)
- "x = (1,4)"
- "Neighbors of x: {(1,5), (1,3)}"
- "C(1,5) = 3,   F = 3 + 4 = 7"
- "Q = {(1,5):7, (2,2):7, (1,2):9}" (blue)

Graph: (1,4) red with a black ring (current x); (1,3) and (2,3) red; (1,5) yellow labelled "F=7"; (2,2) yellow labelled "F=7"; (1,2) yellow labelled "F=9". All others black.

## Slide 75 — A* example: and so on

No title in the title bar. Left text: "… and so on …" and "(until we reach B)". Graph unchanged from slide 74 (ring on (1,4); red (1,4), (1,3), (2,3); yellow (1,5) F=7, (2,2) F=7, (1,2) F=9).

## Slide 76 — Comparison

![Slide 76 — Comparison](../images/02-discrete-motion-planning/slide-76.png)

Title bar: "Comparison". Two side-by-side panels with grey rounded headings "BFS" (left) and "A*" (right). Each panel is a white square with a thin border containing the same light-blue upside-down "L" obstacle as slide 62, A with a black dot at the left of the stem, and B with a black star at the upper right. In the BFS panel the dot at A has a small yellow/orange cluster of cells around it; in the A* panel the dot at A has a yellow cluster with a short red-orange bar extending to its right. Under each panel the caption "expanded: 4" (both panels). The search marks are tiny and only the area around A is marked; no other cells are coloured, and no other numbers appear.

[Ed: in the lecture this is an animation of the two searches side by side (transcript ≈1:09:52–1:10:39); the PDF holds a single early frame, which is why both counters read 4.]

## Slide 77 — Learned searched heuristics

Title bar: "Learned searched heuristics". A video still from a talk: black background with centred white text "Finally, / Optimizing for a / Safe, Smooth & Fast Path / Inside the Corridor" on four lines; at the bottom left a small inset of a man in a dark T-shirt on a stage in front of a blue curtain, gesturing with both hands; at the bottom right the "TESLA LIVE" logo. Caption: "Tesla AI day, 2021".

## Slide 78 — A*: full algorithm

Section divider: the single text "A*: full algorithm" in blue in a grey rounded box.

## Slide 79 — A* algorithm

Title bar: "A* algorithm". Monospaced code listing on the whole slide; comments are in teal italics and keywords ("while", "for", "of", "continue", "if", "not", "in") in green bold. Reproduced line by line (indentation as shown):

```
// Initialize the queue and also initialize a set of “dead” states
Q := {start},
DeadSet = {}
// For vertex v, parent(v) is the vertex immediately preceding it on the cheapest path from start to v currently known.
parent := empty list
// For vertex x, C(x) is the cost of the cheapest path from start to x currently known.
Initialize C(x) to be infinity for all x
C(A) := 0 // Initialize C to be 0 for the start vertex A
// For vertex x, F(x) := C(x) + H(x).
Initialize F(x) to be infinity for all x
F(A) := H(A) // Initialize F(A) to be H(A) since C(A) = 0

while Q is not empty
    x := the vertex in Q having the lowest F value
    if x = goal
        Return SUCCESS

    Q.Remove(x)
    DeadSet.Add(x)
    for each neighbor x’ of x
        if x’ in DeadSet
            continue
        // l(x,x’) is the cost of the edge from x to x’
        // tentative_C is the cost from A to x’ through x
        tentative_C := C(x) + l(x, x’)
        if tentative_C < C(x’)
            // This path to neighbor is better than any previous one. Record it!
            parent(x’) := x
            C(x’) := tentative_C
            F(x’) := C(x’) + H(x’)
            if x’ not in Q
                Q.add(x’)

// Open set is empty but goal was never reached
return FAILURE
```
