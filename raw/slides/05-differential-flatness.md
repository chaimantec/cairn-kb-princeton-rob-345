---
title: Lecture 5 — Differential Flatness (slide deck)
lecture: 5
slides: 6
source_pdf: https://www.dropbox.com/scl/fi/e90rrmg0036wqix2xmv0f/Lecture5_slides.pdf?rlkey=qonzpbom400u3wozymjv3fga3&dl=0
numbering: PDF page N = Slide N for all 6 pages (1:1). Page 1 prints no number; its label (1) is inferred from position. Pages 2–6 print 2–6.
images: to be filled in by the parent
---

# Lecture 5 — Differential Flatness: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 5 deck (speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Photographs and diagrams are described in prose since the KB is read as text. The deck holds no definitions or derivations; the written material is in the separate lecture notes. Slides 3–6 are video slides: the PDF holds one frame of each video.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 6 pages, and the last printed number is 6. Slide 1 prints no number in the corner, so its label is inferred from position (it is the title page).

Companion pages: [wiki page for this lecture](../../wiki/05-differential-flatness.md) · [transcript](../transcripts/05-differential-flatness.md) · [lecture notes](../notes/05-differential-flatness.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Real-time planning using differential flatness: the Mellinger and Kumar paper (abstract, Fig. 1) |
| 3 | Video: indoor quadrotor flight (frame) |
| 4 | Video: drone racing gates in a hall (frame) |
| 5 | Video: not rendered (black frame) |
| 6 | Video: RRT* + differential flatness, title frame of a polynomial trajectory planning presentation |

---

## Slide 1 — Lecture 5: Differential Flatness

Title page. Title in blue in a rounded box: "Lecture 5: Differential Flatness". Below it, a faded wide photograph of a small quadrotor drone seen from the front (black propellers on the left and right arms, a circuit board in the centre with a small camera module on a vertical board, red and black wires). Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred).

## Slide 2 — Real-time planning using differential flatness

Title bar: "Real-time planning using differential flatness" (blue). Printed number 2. The slide is the first page of a paper, shown as an image under the title. Verbatim text of that page:

Title: "Minimum Snap Trajectory Generation and Control for Quadrotors"

Authors: "Daniel Mellinger and Vijay Kumar"

Abstract: "Abstract— We address the controller design and the trajectory generation for a quadrotor maneuvering in three dimensions in a tightly constrained setting typical of indoor environments. In such settings, it is necessary to allow for significant excursions of the attitude from the hover state and small angle approximations cannot be justified for the roll and pitch. We develop an algorithm that enables the real-time generation of optimal trajectories through a sequence of 3-D positions and yaw angles, while ensuring safe passage through specified corridors and satisfying constraints on velocities, accelerations and inputs. A nonlinear controller ensures the faithful tracking of these trajectories. Experimental results illustrate the application of the method to fast motion (5-10 body lengths/second) in three-dimensional slalom courses."

The page is cropped at the bottom: below the abstract, a sliver of the next heading and body text is cut through and unreadable.

Fig. 1, caption "Fig. 1. The flat outputs and the reference frames.", sits on the right of the abstract. It is a photograph of a four-rotor drone seen from slightly above, arms in an X layout, overlaid with coloured arrows and labels (not a line drawing):

- The rotors are numbered in black: "1" at the lower right (near the front right of the drone), "2" at the upper right, "3" at the top left of centre, "4" at the left.
- World frame, in grey, drawn from a point at the lower left of the figure that is not labelled: a vertical arrow pointing up labelled $z_W$; an arrow pointing right (slightly downward) labelled $y_W$; and a short arrow pointing down and slightly right labelled $x_W$ (the label overlaps the grey $x_W$ arrowhead and the lower $\psi$; the blue $x_C$ arrow ends to its right).
- Body frame, in purple, drawn from the drone's centre, labelled $O_B$: an arrow pointing up and slightly to the right labelled $z_B$; an arrow pointing to the right and slightly up labelled $y_B$; and an arrow pointing down and to the right labelled $x_B$.
- A dark red arrow labelled $\mathbf{r}$ (bold, printed as "r") runs from the world-frame origin at the lower left to the drone's centre $O_B$.
- Intermediate yaw frame, in blue: at the drone's centre, an arrow pointing straight up labelled $z_C$, an arrow pointing right labelled $y_C$ (beside the purple $y_B$ arrow, slightly lower), and an arrow pointing down and to the right labelled $x_C$ (close to $x_B$ but longer and steeper). A second, shorter set of blue arrows $y_C$ and $x_C$ is drawn from the world origin: $y_C$ pointing right (just above the grey $y_W$) and $x_C$ pointing down and to the right.
- Angle: two small blue arcs marked with the Greek letter $\psi$. One spans $y_W$ and $y_C$ about three-quarters of the way along them, towards their right-hand ends; the other spans $x_W$ and $x_C$ near the world origin. This shows the yaw angle $\psi$ as the rotation about the vertical from the world axes to the C axes.

Every label above is legible. The arrow directions are as read from the picture; the figure carries no further text.

## Slide 3 — Real-time planning using differential flatness (video)

Title bar: "Real-time planning using differential flatness" (blue). Printed number 3. Video slide: the PDF holds a single frame. In the lecture this is the video released with Mellinger and Kumar's work, played with its audio (≈1:01:16–1:04:36). Below the frame, a link: "https://www.youtube.com/watch?v=geqip_0Vjec".

The frame is a full-width still from an indoor flight video, tinted pink-red. A single quadrotor with a dark X-shaped frame and red parts is in the lower right of the picture, close to the floor with blurred spinning propellers (hovering or just above the floor). The floor is dark tiled. The room is a cluttered lab: black netting hangs in front of the walls, a white board covered in illegible handwriting on the back wall, cardboard boxes, a round white table and a fan, a vacuum cleaner and coiled orange and green cables on the left, a desk with equipment at the right edge, and small white tape markers on the floor. No people are visible. The frame shows no trajectory or overlay text.

## Slide 4 — Video (drone racing)

Plain grey header bar with no title text. Printed number 4. Video slide: the PDF holds a single frame. In the lecture this is drone racing from a group at the University of Zurich (≈1:04:36–1:05:22). Below the frame, a link: "https://www.youtube.com/watch?v=XpuRpKHp_Bk".

The frame is a high-angle view of a large indoor hall with a pale grey floor and corrugated metal walls. Five racing gates stand on the floor. Two are black-and-white checkered square frames marked with the letters "UZH": one at the left, with blue side panels, and one at the bottom centre. Three more stand further back: a thin white gate seen edge-on at centre-left, a gate at centre-right, and one at the far right. Two black foam mats lie in the middle of the floor. A very small drone is visible near the bottom centre (just right of the lower gate) and its shadow can be seen at the bottom right. White subtitle text overlaid at the bottom reads: "We also further improve both methods to track a racing trajectory at up to 20m/s with centimeter-level tracking accuracy." No people are visible.

## Slide 5 — Video (not rendered)

Plain grey header bar with no title text. Printed number 5. Video slide: the PDF holds a single frame, and here the frame is entirely black, so the video did not render and nothing of its content is known from the deck. Below it, a link: "https://www.youtube.com/watch?v=PLjN2UNz8Mg". In the lecture this is a tail-sitter drone from a group in MIT's AeroAstro department (≈1:05:22–1:06:07); read what the video shows from the transcript, not from the slide.

## Slide 6 — RRT* + Differential Flatness (video)

Title bar: "RRT* + Differential Flatness" (blue). Printed number 6. Video slide: the PDF holds a single frame. It is the same video, and the same title-card frame, as Lecture 3's slide 54 ("RRT"); here the lecture adds that the RRT was built in the flat output space (≈1:06:07–1:06:53). Below the frame, a link: "https://www.youtube.com/watch?v=ul7YboQA5OY".

The frame is the title card of a recorded presentation: a white 4:3 panel with black bars at left and right. Text: "Polynomial Trajectory Planning for Quadrotor Flight" (two lines, large), then "Charles Richter, Adam Bry, Nicholas Roy" and "Robust Robotics Group". At the bottom are three logos: the "MIT" logo in black and red on the left, a blue circular logo with the text "AEROASTRO" and a small "MIT" on the centre, and an outline logo with the word "CSAIL" on the right. This frame shows no drone or trajectory.
