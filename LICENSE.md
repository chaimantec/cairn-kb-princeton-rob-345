# Licence and copyright

This repository is a **study aid compiled from Princeton ROB 345/549 course material**. It is
not a work with a single owner, so it carries no single repository-wide licence. Three layers
of authorship sit here, with three different copyright positions. Read this before reusing
anything from it.

The short version: **the explanatory writing is yours to reuse with attribution; the course
material and the third-party images in the slides are not mine to give you.**

---

## Layer 1 — the compilation's own editorial work

Copyright (c) 2026 chaimantec.

Licensed under **Creative Commons Attribution 4.0 International** (`CC-BY-4.0`),
<https://creativecommons.org/licenses/by/4.0/>. You may share and adapt it, including
commercially, with attribution.

This covers only the material original to this compilation:

- `INDEX.md`, `AGENTS.md`, `BUILD_LOG.md`, `TODO.md`, `kb.json`, `sources.md`, this file;
- the original explanatory prose in `wiki/`: the explanations, the connective argument, the
  organisation of the material into pages, and the editorial judgements about what is worth
  recording.

It does **not** extend to the lecture content those pages describe, nor to any passage in
`wiki/` that quotes the lecturer or a slide. Those are quotations, marked as such, and belong to
Layer 2 or Layer 3.

### Not offered under CC BY 4.0, even though I wrote the words

`raw/transcripts/`, `raw/slides/` and `raw/notes/` are derivative works. The copy-editing, the
`[Ed:]` notes and the figure descriptions are mine; the lecture being transcribed and the slides
and notes being described are not. `raw/notes/` reproduces the full text of the course's written
notes. I cannot license the underlying expression, so these directories are not
offered under CC BY 4.0. Read them, cite them, and quote them as you would quote the lecture
itself, but do not treat them as freely relicensable text.

The verbatim auto-captions these transcripts were edited from are **deliberately not published
here**. They would be a complete reproduction of each lecture with no editorial contribution.
They are regenerable from the public video with the `cairn-kb` skill's `fetch_transcript.py`,
using the video id in each transcript's front matter, so anyone can re-derive them and audit an
edit.

---

## Layer 2 — Princeton ROB 345/549 course material

**No licence exists, and none is granted here.**

The lectures, slide decks and course notes are the work of Anirudha Majumdar and the ROB 345/549
course staff (Princeton University, Fall 2026). They are published through the course website,
<https://irom-lab.princeton.edu/intro-to-robotics/>, with the documents hosted on Dropbox and
the lecture videos on YouTube (recorded by the Princeton Broadcast Center).

As checked on 2026-10-20, no licence, copyright or reuse statement appears on the course
website, and none is printed on any page of the Lecture 1–9 decks or of the Lecture 4–9
notes (checked 2026-10-21). Publicly downloadable is not the
same as licensed. Absent an express grant the default applies: copyright arises automatically,
and no reuse rights pass to anyone.

The images in `raw/images/` and the material described in `raw/slides/` are reproduced here for
study and commentary, relying on fair use (17 U.S.C. § 107) rather than on any permission. Only
slides that carry a figure are rendered, and from the notes only their figures, cropped. Title slides, text slides, news-headline screenshots
and photographs of course staff are not. Every deck is linked at its canonical URL beside the
material drawn from it. **That reliance is mine and does not transfer to you.** Fair use is a
defence to infringement, not a licence. It can justify a particular use by a particular user for
a particular purpose, and gives me nothing to pass downstream. If you want to reuse Layer 2
material, make your own assessment or ask the course staff.

**Takedown.** If the instructor or any rights holder asks for an image or a transcription to be
removed, it will be deleted along with every link to it.

---

## Layer 3 — third-party images reproduced inside the decks

The decks reproduce many images that are not Princeton's: video frames, news
photographs and screenshots, product photos and historical images. **None carries a credit line
on the slide.** They belong to their respective owners, Princeton could not license them to
anyone, and nothing here does either. The attributions below are inferred from logos, captions
and URLs visible on the slides. Where nothing on the slide identifies the source, the entry says
so.

### Lecture 1 — Introduction to Robotics

Deck: [Lecture1.pdf](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0).
Rendered: 24 slides, in `raw/images/01-intro-to-robotics/`.

| Slide | Third-party content (as identifiable from the slide) |
| --- | --- |
| 6 | Collage of the IRoM Lab's research; one panel shows a "1x" label and partly hidden "OPPO" text. Panel sources are not credited. |
| 7 | Frame from Google DeepMind's Gemini Robotics video (deepmind.google/models/gemini-robotics). |
| 8 | Demo frames under the π logo, the "GEN-1.5" caption and the "DYNA" label; a lab-bench panel with a ROBOTIQ gripper. Not credited. |
| 10 | Frame of a news video about the Beijing Humanoid Robot Games. The outlet is not shown. |
| 11 | Frame of a CNBC video (youtu.be/RQaW3iMue3M) showing a Waymo vehicle. |
| 15 | Waymo product photograph; market-share chart "per YipitData". |
| 20 | Historical images: an automaton sketch and an engraving of the Mechanical Turk. Not credited. |
| 21 | Federal Theatre (WPA) poster for *R.U.R.* (Rossum's Universal Robots). |
| 22 | Television-studio still of the Unimate robot. Not credited. |
| 25 | Photograph of Boston Dynamics' Atlas (captioned "Boston Dynamics: Atlas"). |
| 26 | Photograph of a small quadrotor with a camera. Not credited; apparently the course's own drone. |
| 27, 28 | Stock-style photographs of a dishwasher and an automatic door. Not credited. |
| 29 | Product photograph of a smart speaker. Not credited. |
| 30 | Photograph of the Intuitive Surgical da Vinci system (captioned "Intuitive Surgical, Da Vinci"). |
| 32 | Product photograph of a Crazyflie quadrotor (Bitcraze), with the deck's own labels and arrows. |
| 33 | Three thumbnails: a rendered driving scene, a voxel map over a forest, and a humanoid beside a person in a VR headset. Not credited. |
| 36 | Frame of an ABC7 news video ("Lindsey Austen via Storyful", Aug. 17, 2026). |
| 37 | Frame of a news.com.au video of a humanoid weightlifting robot. |
| 38 | Frame of an ABC7 news video of dashcam footage ("Anonymous via Storyful"). |
| 39 | The same thumbnails as slide 33. |
| 40 | Product photograph of the Crazyflie 2.1 brushless (Bitcraze). |
| 41 | Photograph of a netted drone-flight arena. Not credited; apparently the course's own lab. |
| 52 | No third-party content: the deck's own diagram. |

### Lecture 2 — Discrete Motion Planning

Deck: [Lecture2.pdf](https://www.dropbox.com/scl/fi/pnwucnirlwgviqwaj67hl/Lecture2.pdf?rlkey=6s2et2apw9rtnvr8x2ke243sp&dl=0).
Rendered: 22 slides, in `raw/images/02-discrete-motion-planning/`.

| Slide | Third-party content (as identifiable from the slide) |
| --- | --- |
| 2 | Frame of a video of a past final project in the course's flight arena. Not credited; apparently the course's own. |
| 5 | Street-level point-cloud image. Not credited. |
| 7 | Frame of a piano-mover animation (youtube.com/watch?v=cXm3WW-geD8). |
| 9 | Frames of a Zoox video ("Source: Zoox"). |
| 10 | Protein-folding renderings ("Source: parasollab.web.illinois.edu/research/protein-folding/"). |
| 11 | Frame of a robotic Rubik's cube solver video (youtube.com/watch?v=OZu9gjQJUQs). |
| 19 | Frame of a configuration-space obstacles video (youtube.com/watch?v=SBFwgR4K1Gk). |
| 76 | Frame of a BFS-versus-A\* animation. Not credited. |
| 15, 17, 18, 22, 24, 27, 31, 32, 34, 41, 46, 59, 72, 74 | No third-party content identified: the deck's own diagrams and worked-example grids. |

### Lecture 3 — Rapidly Exploring Randomized Trees (RRTs)

Deck: [Lecture3.pdf](https://www.dropbox.com/scl/fi/5uv2vt76nqj4b32vr4i37/Lecture3.pdf?rlkey=nx8jjqjlvmgcqqhb8r1p6okzp&dl=0).
Rendered: 17 slides, in `raw/images/03-rrts/`.

| Slide | Third-party content (as identifiable from the slide) |
| --- | --- |
| 19 | Frame of a configuration-space obstacles video (youtube.com/watch?v=SBFwgR4K1Gk). |
| 24 | Still from a GJK explainer video (youtube.com/watch?v=ajv46BSqcK4). |
| 50 | Frame of an RRT video (youtube.com/watch?v=FAFw8DoKvik). |
| 53 | Frame of a piano-moving RRT video from the Robotics Library channel (youtube.com/watch?v=HdfAzUXvmOQ). |
| 56 | Frame of a PR2 arm-planning video (youtube.com/watch?v=vW74bC-Ygb4). |
| 7, 9, 10, 13, 21, 25, 28, 32, 36, 43, 47, 51 | No third-party content identified: the deck's own diagrams and worked-example steps. |

### Lecture 4 — Quadrotor Dynamics

Deck: [Lecture4_slides.pdf](https://www.dropbox.com/scl/fi/v8bp2gyhpixill7c70u7q/Lecture4_slides.pdf?rlkey=h44i0kp1bpmxk3zdg65gvqu29&dl=0).
Notes: [Lecture4_notes.pdf](https://www.dropbox.com/scl/fi/onuvrtpb64sytgp78towu/Lecture4_notes.pdf?rlkey=yo9dpy9jxt7730f0ex3sjdcuw&dl=0).
Rendered: 4 slides and the notes' 3 figures (cropped with their captions), in
`raw/images/04-quadrotor-dynamics/`.

| Image | Third-party content (as identifiable from the page) |
| --- | --- |
| Slides 7, 8, 9 | Photographs of the course's lab spaces and flight arena. Not credited; apparently the course's own. No person is visible. |
| Slide 10 | Frame of a video of a small quadrotor among pipe obstacles. Not credited; apparently the course's own. |
| Notes Figure 1 | Drawings of the planar quadrotor. Not credited. |
| Notes Figure 2 | Rendering of a Crazyflie with its axes, credited in the notes' caption to Bitcraze.io. |
| Notes Figure 3 | Hand drawings of a rotor and of the rotors' spin directions. No third-party content identified. |

### Lecture 5 — Differential Flatness

Deck: [Lecture5_slides.pdf](https://www.dropbox.com/scl/fi/e90rrmg0036wqix2xmv0f/Lecture5_slides.pdf?rlkey=qonzpbom400u3wozymjv3fga3&dl=0).
Notes: [Lecture5_notes.pdf](https://www.dropbox.com/scl/fi/d0g09pk1opfkwdw7udmsi/Lecture5_notes.pdf?rlkey=l1sriwzrnb499bsbcyo3cylm9&dl=0).
Rendered: 3 slides and the notes' 4 drawings (cropped; the notes print no captions), in
`raw/images/05-differential-flatness/`.

| Image | Third-party content (as identifiable from the page) |
| --- | --- |
| Slide 2 | The first page of a research paper, "Minimum Snap Trajectory Generation and Control for Quadrotors" by Daniel Mellinger and Vijay Kumar, with its abstract and its Fig. 1, a photograph of a quadrotor overlaid with reference frames. The slide names no venue or publisher; the copyright is the paper's. |
| Slide 3 | Frame of a quadrotor video (youtube.com/watch?v=geqip_0Vjec), presented in the lecture as Mellinger and Kumar's. No person is visible. |
| Slide 4 | Frame of a drone-racing video (youtube.com/watch?v=XpuRpKHp_Bk); the gates are lettered "UZH", and the lecture attributes it to a group at the University of Zurich. No person is visible. |
| Notes drawings 1–4 | Drawings of an RRT, a car seen from above, the flatness pipeline, and the planar quadrotor. Not credited. |

### Lecture 6 — Trajectory Optimization

Deck: [Lecture6_slides.pdf](https://www.dropbox.com/scl/fi/9wnsc9wkmxmvwbugm7rps/Lecture6_slides.pdf?rlkey=9dsf9cbn7sjy9b5m6dieznycs&dl=0).
Notes: [Lecture6_notes.pdf](https://www.dropbox.com/scl/fi/ctybyh0a1gdrvaywbcylu/Lecture6_notes.pdf?rlkey=i9tmfyhkjiws7gboip2a8fkvl&dl=0)
(no figures). Rendered: 6 slides, in `raw/images/06-trajectory-optimization/`.

| Image | Third-party content (as identifiable from the page) |
| --- | --- |
| Slide 3 | A drawing of the planar quadrotor and an all-black video frame. Not credited; apparently the course's own. |
| Slide 6 | A plot of an RRT grown in state space that fails to reach a goal, credited on the slide to "Underactuated Robotics", Russ Tedrake. |
| Slide 8 | A diagram of the extension step (three points, a straight dotted line and a curve). Not credited; apparently the course's own. |
| Slide 12 | A contour plot of a two-variable quadratic program with its feasible region. Not credited. |
| Slide 14 | A screenshot of an interactive sequential-QP demo for the planar quadrotor; the lecture says it was made with Claude (≈1:01:02). Not credited on the slide. |
| Slide 16 | Frame of an acrobot video (youtube.com/watch?v=FeCwtvrD76I), which the lecture presents as from the lecturer's own PhD work. No person is visible. |

### Lecture 7 — Stability and PD Control

Deck: [Lecture7_slides.pdf](https://www.dropbox.com/scl/fi/6jzh0fey1mnfs8drq3905/Lecture7_slides.pdf?rlkey=nqo1qiqzhktzpy5klid7hyvgs&dl=0).
Notes: [Lecture7_notes.pdf](https://www.dropbox.com/scl/fi/70lppdz21xpgitd1ohhuo/Lecture7_notes.pdf?rlkey=bkk76zdh9ep0cvryzmpr34y7x&dl=0).
Rendered: 2 slides and the notes' 3 drawings (cropped; the notes print no captions), in
`raw/images/07-stability-and-pd-control/`.

| Image | Third-party content (as identifiable from the page) |
| --- | --- |
| Slide 3 | A screenshot of a planar quadrotor simulation (planned path, obstacles, legend), the trajectory-optimization demo of Lecture 6 replayed. Not credited; apparently the course's own. |
| Slide 6 | Five copies of a drawing of the planar quadrotor with thrust arrows. Not credited; apparently the course's own (the same drone drawing appears in Lecture 6's deck). |
| Notes drawings 1–3 | Two hand-drawn phase portraits, and a drawing of the planar quadrotor with thrusts F1, F2 and the X and Y axes. Not credited. |

### Lecture 8 — The Linear Quadratic Regulator

Deck: [Lecture8_slides.pdf](https://www.dropbox.com/scl/fi/vg2cumj4cs2kuqb3942fg/Lecture8_slides.pdf?rlkey=uthhn11zguqubxdgo0zrv5viv&dl=0).
Notes: [Lecture8_notes.pdf](https://www.dropbox.com/scl/fi/j89tx4kp1skacdhuz918r/Lecture8_notes.pdf?rlkey=4gyqm6qumqutg1lzx83uuac4d&dl=0).
Rendered: 4 slides and the notes' 2 drawings (cropped; the notes print no captions), in
`raw/images/08-lqr/`.

| Image | Third-party content (as identifiable from the page) |
| --- | --- |
| Slide 6 | A vector diagram of the sense–think–act loop. Not credited; apparently the course's own. |
| Slide 7 | A drawn phase portrait (a spiral into the origin). Not credited; apparently the course's own. |
| Slide 11 | A frame of a YouTube video (<https://www.youtube.com/watch?v=8OVsJNgNfa0>) of a quadrotor in a University of Zurich lab, whose sign is in the frame. Not credited on the slide beyond the link. |
| Slide 12 | A frame of a YouTube video (<https://www.youtube.com/watch?v=wBhS77cAJ0s>) of a fixed-wing airplane in a prop hang, work the lecturer was involved in during his PhD (≈1:12:49). Not credited on the slide beyond the link. |
| Notes drawings 1–2 | A hand-drawn quadrotor on a vertical line with the height marked, and a typeset sketch of a diagonal matrix Q. Not credited; apparently the course's own. |

### Lecture 9 — Optical Flow

Deck: [Lecture9_slides.pdf](https://www.dropbox.com/scl/fi/yjkah2nhv83fdbnf6ea5a/Lecture9_slides.pdf?rlkey=d83o8wcmk8oczkogd2tpuogq3&dl=0).
Notes: [Lecture9_notes.pdf](https://www.dropbox.com/scl/fi/az52bpcoly0ophkzc7sqj/Lecture9_notes.pdf?rlkey=ijs39xouvybcpqcv3cluaapvu&dl=0).
Rendered: 9 slides and the notes' 4 drawings (cropped; the notes print no captions), in
`raw/images/09-optical-flow/`.

| Image | Third-party content (as identifiable from the page) |
| --- | --- |
| Slide 3 | A drawn path among four obstacles from Start to Goal. Not credited; apparently the course's own. |
| Slide 4 | A photograph of a Crazyflie drone (a Bitcraze product; "bitcraze.se" is printed on its board) with the Flow deck, held in a hand. Not credited. |
| Slide 5 | A frame of a YouTube video (<https://www.youtube.com/watch?v=5rR_9YIcg_s>) showing an optical flow field over motorway traffic. Not credited on the slide beyond the link. |
| Slide 6 | An optical flow field plotted over a grayscale image of a corridor, with faint pink text at the top left, partly hidden, that may be a credit and is not legible in full. |
| Slide 7 | A diagram of a drone with a pinhole camera above the ground. Not credited; apparently the course's own. |
| Slide 8 | A diagram of four discs moving between two frames, printed "Credit: David Fouhey". |
| Slide 15 | A frame of the barber pole illusion, printed "Source: https://www.opticalillusion.net/optical-illusions/the-barber-pole-illusion/". |
| Slides 17–18 | A photograph of a stone building with a tower, among bare trees, marked up with boxes, arrows and magnified insets. Not credited. |
| Notes drawings 1–4 | Hand-drawn sketches: moving objects in a frame, a displaced point, the gradient and two flow vectors, an edge with its gradients. Not credited; apparently the course's own. |
