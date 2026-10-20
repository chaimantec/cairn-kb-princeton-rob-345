# Princeton ROB 345/549 — Introduction to Robotics (Fall 2026)

An introduction to the theoretical and algorithmic principles behind modern robotic systems,
taught by **Anirudha Majumdar** (Mechanical & Aerospace Engineering, Princeton University), with
the public course site at <https://irom-lab.princeton.edu/intro-to-robotics/>. Its topics are
motion planning, feedback control, state estimation, localization and mapping, and machine
learning for robotics. It closes with the broader questions of jobs, ethics and law. Students
work hands-on with the Crazyflie quadrotor, and the final project trains a vision-based
navigation policy with imitation learning. ROB 345 is the undergraduate course; ROB 549 is the
graduate track.

> **Coverage: Lecture 1 only, of the 9 recorded lectures in the catalog.** The course site
> schedules 24 lectures, of which lectures 1–9 had videos and slides when this was built
> (2026-10-20). This knowledge base holds the first lecture, the introduction: its edited
> transcript, its full slide deck as text, 24 of its slides as images, and the concept pages
> it starts. **It cannot answer questions about the technical content of lectures 2 onward**
> (graph search, RRTs, quadrotor dynamics, differential flatness, trajectory optimization, PD
> control, LQR, optical flow and later). For those, point the learner to the lecture's slides
> and notes in [`sources.md`](sources.md). Build progress is in [TODO.md](TODO.md).

## Lecture pages

- [Lecture 1 — Introduction to Robotics](wiki/01-intro-to-robotics.md): a survey of robotics
  in 2026 (Gemini Robotics 2 and VLAs, the manipulation startups, humanoids, Waymo's market
  share in San Francisco, drone delivery, the 1X Neo home humanoid, and worries about jobs).
  The question "what is a robot?", with a pre-history from Talos to Unimate, four definitions,
  and the class debate over six edge cases (Atlas, the course drone, a dishwasher, an automatic
  door, a smart speaker, the da Vinci surgical robot). The sense–think–act anatomy. The three
  technical areas. Uncertainty as what makes robotics hard, with three failure case studies.
  The Crazyflie hardware, and the course logistics and generative-AI policy.

## Course pages

- [Course map](wiki/course-map.md): the three technical areas and the full 24-lecture
  schedule from the course website, marking which lectures this KB covers.
- [Course logistics](wiki/course-logistics.md): staff and TAs, prerequisites and how much
  of each matters, grading (40/30/30), teams, office hours, the late and collaboration
  policies, the four permitted uses of generative AI, reference textbooks, Gradescope and Ed,
  and ROB 345 versus ROB 549.
- [The Crazyflie drone](wiki/crazyflie.md): the course's robot. The Crazyflie 2.1
  brushless, its sensors (IMU, optical flow, height) and actuators, the parts list, the
  autonomous-navigation goal and final project, teams, the two lab spaces, and what to do when
  a drone breaks.

## Concept pages

- [Sense–think–act](wiki/sense-think-act.md): the anatomy every robotic system shares
  (actuators, sensors, computation in a closed feedback loop), illustrated on the course drone,
  and how the course's three areas fit the loop.
- [Uncertainty](wiki/uncertainty.md): the course's central theme. Why robotics is hard
  (Moravec's paradox), the sources of uncertainty in planning and control, localization and
  mapping, and robot learning, the three failure case studies, and sim-to-real with domain
  randomization.

## Raw materials

- [`raw/transcripts/`](raw/transcripts/): lecture transcripts in ~45-second paragraphs, each
  opening with an `[MM:SS]` timestamp into the video. **Read the files directly in this
  folder.** They are copy-edited from YouTube's auto-captions, which garble names and terms
  (e.g. "Whimo" for Waymo, "crazy fly" for Crazyflie). The edits are listed in each file's
  header, and passages too garbled to restore are marked `[Ed: unclear]`. The verbatim captions
  are not committed; each file says how to regenerate them.
- [`raw/slides/`](raw/slides/): every slide of each deck as text, headed `## Slide N` with
  the number printed on the slide, and every figure described in prose. **Lecture 1's deck has
  no slide 2**: a slide was hidden before export, so slide *N* is PDF page *N*−1 from slide 3
  on. Each file's header says how its numbers map to PDF pages.
- [`raw/images/`](raw/images/): whole-slide images of figure slides, embedded under the
  matching `## Slide N` heading and in the wiki passage that cites that slide. **Only Lecture 1
  has images**, and only some of its slides (24 of 57). Title and divider slides, text-only
  slides, news-headline screenshots, repeats, and photographs of course staff were deliberately
  not rendered. The slide file's header lists which slides have images.
- [`sources.md`](sources.md): every lecture video, slide deck, set of notes and assignment
  the course website links to, with canonical URLs. The PDFs are not committed; cite those
  URLs.
- [`LICENSE.md`](LICENSE.md): what you may reuse. The editorial writing is CC BY 4.0. The
  course material and the third-party images in the slides are not licensed here.

## Showing images

- **Use an image path you have actually read in a page. Never construct one from the
  pattern**, and never assume a slide has an image because a neighbouring slide does. Most
  slides have none.
- Read the relative path (e.g. `raw/images/01-intro-to-robotics/slide-32.jpg`) to get a URL you
  can show.
- Prefer the slide file's text for numbers, names and quotations, since it is searchable and
  exact. Show one image, not a gallery, and keep the slide citation with it.

## How to cite

Cite slides as "Lecture 1, slide N" using the printed number, and spoken material by
timestamp, e.g. "Lecture 1, ≈24:01". Prefer a slide citation for anything written down, and a
timestamp for what was said aloud.
