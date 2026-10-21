# Princeton ROB 345/549 — Introduction to Robotics (Fall 2026)

An introduction to the theoretical and algorithmic principles behind modern robotic systems,
taught by **Anirudha Majumdar** (Mechanical & Aerospace Engineering, Princeton University), with
the public course site at <https://irom-lab.princeton.edu/intro-to-robotics/>. Its topics are
motion planning, feedback control, state estimation, localization and mapping, and machine
learning for robotics. It closes with the broader questions of jobs, ethics and law. Students
work hands-on with the Crazyflie quadrotor, and the final project trains a vision-based
navigation policy with imitation learning. ROB 345 is the undergraduate course; ROB 549 is the
graduate track.

> **Coverage: Lectures 1–7, of the 9 recorded lectures in the catalog.** The course site
> schedules 24 lectures, of which lectures 1–9 had videos and slides when this was built
> (2026-10-20). This knowledge base holds the introduction (Lecture 1), discrete motion planning
> (Lecture 2), randomized motion planning with RRTs (Lecture 3), quadrotor dynamics (Lecture 4),
> differential flatness (Lecture 5), trajectory optimization (Lecture 6) and stability and PD
> control (Lecture 7): their edited transcripts, their full slide decks as text, the written notes of
> Lectures 4–7 as text, 88 images (78 slides, the 3 figures of Lecture 4's notes and the drawings of
> Lecture 5's notes (4) and Lecture 7's (3)), and the course and concept pages they start. **It
> cannot answer questions about the technical content of lectures 8 onward** (LQR, optical flow and
> later). For those, point the
> learner to the lecture's slides and notes in [`sources.md`](sources.md). Build progress is in [TODO.md](TODO.md).

## Lecture pages

- [Lecture 1 — Introduction to Robotics](wiki/01-intro-to-robotics.md): a survey of robotics
  in 2026 (Gemini Robotics 2 and VLAs, the manipulation startups, humanoids, Waymo's market
  share in San Francisco, drone delivery, the 1X Neo home humanoid, and worries about jobs).
  The question "what is a robot?", with a pre-history from Talos to Unimate, four definitions,
  and the class debate over six edge cases (Atlas, the course drone, a dishwasher, an automatic
  door, a smart speaker, the da Vinci surgical robot). The sense–think–act anatomy. The three
  technical areas. Uncertainty as what makes robotics hard, with three failure case studies.
  The Crazyflie hardware, and the course logistics and generative-AI policy.
- [Lecture 2 — Discrete Motion Planning](wiki/02-discrete-motion-planning.md): geometric
  motion planning and its three assumptions; the piano mover's problem; degrees of freedom
  (point, pendulum, n-link snake, planar quadrotor); configuration space, free space and obstacle
  space; discretizing a grid into a graph; the forward search template; BFS and DFS worked step by
  step on a 5-by-5 grid; the cost of a plan; A\* with cost-to-come, an underestimating heuristic,
  alive and dead vertices, and a worked example; Dijkstra's algorithm; learned heuristics (Tesla
  AI Day); and the full A\* pseudocode.
- [Lecture 3 — Rapidly Exploring Randomized Trees (RRTs)](wiki/03-rrts.md): accounting for the
  robot's geometry (the circle approximation, inflating obstacles, the Minkowski sum, and why it
  fails in clutter); back to configuration space; the curse of dimensionality ($B^d$ cells) and
  why $C_{obs}$ cannot be built; the RRT's three key ideas, including collision checking with
  GJK; the RRT worked through six iterations, and its pseudocode; the goal threshold
  $\epsilon$ and path recovery; space-filling and Voronoi bias; step size and checking the whole
  segment; demos (a piano, a drone at MIT, a PR2 arm); RRT\* and rewiring; completeness and
  probabilistic completeness; and choosing what to optimize.
- [Lecture 4 — Quadrotor Dynamics](wiki/04-quadrotor-dynamics.md): the two challenges with
  geometric planning (dynamic feasibility, errors and disturbances) and why a level drone cannot
  slide sideways; the planar quadrotor's equations of motion from Newton's second law, with total
  thrust $u_1$ and moment $u_2$; converting second-order equations to first order; state,
  configuration variables, control input and $\dot{\bar{x}} = f(\bar{x}, \bar{u})$; the 3D
  quadrotor's body axes, Euler angles in the space 1-2-3 convention, 12 states and control input
  $[F_{\text{tot}}, M_1, M_2, M_3]$; the motor model ($F_i = k_f \omega_i^2$) and how the course
  measured the thrust coefficient; how a quadrotor yaws; and the lab spaces, lab rules and the
  first hardware lab (an RRT on the drone). The derivation follows the lecture notes, cited by
  equation number.
- [Lecture 5 — Differential Flatness](wiki/05-differential-flatness.md): why the RRT's
  straight-line extension fails for a robot with dynamics (a drone or a car cannot slide
  sideways); the planar quadrotor's equations in thrusts $F_1$, $F_2$ (with the sign of the moment
  equation corrected in class); the two-part claim that any smooth center of mass trajectory can
  be flown, and its proof via $\theta = \arctan(-\ddot{x}/(\ddot{y} + g))$ and two linear
  equations for the thrusts; why the fourth derivative is needed ($q = 4$); the general definition
  with flat outputs $\bar{z}$ and functions $\alpha$, $\beta$, $\gamma$; the theorem that there
  are as many flat outputs as control inputs; the 3D quadrotor's flat outputs $x$, $y$, $z$,
  $\psi$; running the RRT in the flat output space with polynomial segments; and the videos
  (Mellinger and Kumar's minimum snap work, drone racing, a tail-sitter, RRT\* with flatness).
  The derivation follows the lecture notes, cited by equation number.
- [Lecture 6 — Trajectory Optimization](wiki/06-trajectory-optimization.md): the two limits of
  differential flatness; the RRT grown in state space with random control inputs (probabilistically
  complete, useless in practice); keeping the RRT and solving each extension as a boundary value
  problem, i.e. trajectory optimization; linearizing the planar quadrotor about hover (nominal
  thrust $mg$, a first-order Taylor expansion) and computing $A$ and $B$ entry by entry; Euler
  discretization; trajectory optimization with linear dynamics as a convex quadratic program
  (minimum control effort, start, goal, dynamics and polytope constraints) and why it is fast;
  pictures of a QP; sequential quadratic programming for nonlinear systems, and minimum-time
  bang-bang control; trajectory optimization inside the RRT; and three videos (an acrobot swing-up,
  a knife-edge airplane, funnel libraries). The derivation follows the lecture notes, cited by
  equation number.
- [Lecture 7 — Stability and PD Control](wiki/07-stability-and-pd-control.md): why a plan executed
  open loop drifts (numerical integration error; 10% errors in inertia and mass) and the three kinds
  of uncertainty planning ignores; feedback control for hovering, the controller as a vector field
  $\bar{u}(\bar{x})$; receding horizon control (MPC) as replanning; fixed points and the planar
  quadrotor's hover point; closed-loop dynamics; global and local attractivity, stability in the
  sense of Lyapunov (the $\epsilon$ and $\delta$ game, invariance), global and local asymptotic
  stability and how they relate, including for linear systems; stabilizability, with the example
  $\dot{x}_ 1 = x_1$ that no controller can fix; and PD control of a quadrotor moving only up and
  down (proportional feedback oscillates like a spring-mass, adding damping with $k_p, k_d \lt 0$
  makes it asymptotically stable; gains and the gain matrix). The definitions follow the lecture
  notes, cited by equation number, with the board's naming where it differs.

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
- [Configuration space](wiki/configuration-space.md): degrees of freedom, the configuration
  space $C$ with a table of examples, free space $C_{free}$ and obstacle space $C_{obs}$, the
  geometric motion planning problem with its assumptions, why the robot's geometry calls for
  configuration space and what dimension costs, and the two ways the course solves it.
- [Graph search](wiki/graph-search.md): turning a grid into a graph, the forward search
  template, how BFS, DFS, Dijkstra's algorithm and A\* differ (only in which vertex they take out
  of the queue), edge costs and optimality, heuristics and why they must underestimate, A\*
  bookkeeping, and completeness and why graph search does not scale with dimension.
- [Rapidly exploring randomized trees (RRTs)](wiki/rrt.md): the problem the RRT solves, its three
  key ideas, the algorithm step by step, path recovery, practical details (segment checking, the
  goal threshold, goal bias), its properties (space-filling, feasible but not optimal,
  probabilistically complete), RRT\* and other variants, and a comparison with graph search.
- [The quadrotor model](wiki/quadrotor-model.md): the course's model of its drone in one place.
  The planar quadrotor's parameters and equations of motion, in second- and first-order form; the
  3D quadrotor's frames, Euler angles, 12-dimensional state, control input and sketched dynamics;
  the motor model with the thrust and moment coefficients; and why adjacent rotors spin opposite
  ways.
- [State and dynamics](wiki/state-and-dynamics.md): why dynamics enter the course; state,
  configuration variables, control input and physical parameters; converting $n$ second-order
  equations of motion into $2n$ first-order ones; and the general form
  $\dot{\bar{x}} = f(\bar{x}, \bar{u})$ and what it is used for (prediction).
- [Differential flatness](wiki/differential-flatness.md): the problem it answers (planning that
  respects the dynamics), the definition with flat outputs and the functions $\alpha$, $\beta$,
  $\gamma$, what it does and does not give (smoothness, only the flat outputs are chosen, no
  general test), the planar quadrotor worked through, the 3D quadrotor's flat outputs, and
  planning an RRT in the flat output space.
- [Trajectory optimization](wiki/trajectory-optimization.md): the boundary value problem of
  driving a robot from one state to another under its dynamics; the linear case as a convex
  quadratic program (linearize, discretize, minimize control effort subject to linear constraints)
  and why it is fast; other objectives and bang-bang control; sequential quadratic programming for
  nonlinear systems, without guarantees; and its use for the RRT's extension step.
- [Linearization](wiki/linearization.md): approximating nonlinear dynamics near a nominal state and
  control input by a first-order Taylor expansion, $\dot{\bar{x}} \approx A(\bar{x} - \bar{x}_ 0) + B(\bar{u} - \bar{u}_ 0)$;
  the hover point of the planar quadrotor; its matrices $A$ and $B$ worked out entry by entry; and
  how good the approximation is.
- [Stability](wiki/stability.md): what a feedback controller should achieve. Fixed (equilibrium)
  points, closed-loop dynamics $f_{\text{cl}}$, global and local attractivity, stability in the sense
  of Lyapunov, global and local asymptotic stability and how they relate (equivalent for linear
  systems), and stabilizability, with an example of a system no controller can stabilize.
- [Feedback control](wiki/feedback-control.md): why a planned trajectory needs feedback, the
  controller as a vector field $\bar{u}(\bar{x})$, model predictive control as repeated replanning,
  PD control with proportional and derivative gains and the gain matrix $K$, and what LQR (Lecture 8,
  not yet covered) adds.

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
  on. The decks of Lectures 2–7 are numbered one-to-one: slide *N* is PDF page *N*. Each
  file's header says how its numbers map to PDF pages. Lecture 4's deck has only 13 slides and
  Lecture 5's only 6 (a paper's first page and four videos); their technical content is in the
  notes. Lecture 6's 18 slides carry the ideas and pictures, and its derivation is in the notes.
  Lecture 7's 7 slides motivate feedback control; its definitions and PD control are in the notes.
- [`raw/notes/`](raw/notes/): the full text of the course's written lecture notes, headed
  `## Page N`, with every equation in LaTeX under the notes' own number and every figure
  described in prose. **Only Lectures 4–7 have notes here** so far. Each file lists the printed
  slips in its notes.
- [`raw/images/`](raw/images/): whole-slide images of figure slides, embedded under the
  matching `## Slide N` heading and in the wiki passage that cites that slide. **Only Lectures
  1–7 have images**, and only some of their slides: 24 of Lecture 1's 57, 22 of Lecture 2's 79,
  17 of Lecture 3's 62, 4 of Lecture 4's 13, 3 of Lecture 5's 6, 6 of Lecture 6's 18 and 2 of
  Lecture 7's 7. Lecture 4 also has the three figures of its notes, cropped with their captions,
  and Lectures 5 and 7 the drawings of their notes (four and three), which have no captions; they
  are shown in `raw/notes/` and in the wiki. Lecture 6's notes have no figures.
  Title and divider slides, text-only slides, pseudocode, news-headline screenshots, decorative stock photographs, blank video frames, video title cards whose text is transcribed, repeats
  (including slides repeated from an earlier lecture's deck) and build steps, and photographs of
  course staff were deliberately not rendered. Each slide or notes file's header lists which of
  its slides or figures have images.
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
timestamp, e.g. "Lecture 1, ≈24:01". Cite the written notes as "Lecture 4 notes, eq. (N)" or
"notes p. N"; each lecture's notes number their equations from (1). Prefer a slide or notes
citation for anything written down, and a timestamp for what was said aloud. The derivations of
Lectures 4–7 were done on a blackboard that is not in the record, so their equations are
cited to the notes.
