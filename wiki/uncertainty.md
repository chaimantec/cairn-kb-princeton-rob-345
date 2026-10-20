# Uncertainty: why robotics is hard

"The main thing that makes anything in robotics hard is uncertainty." This is the theme
Majumdar sets for the whole course in [Lecture 1](01-intro-to-robotics.md#what-makes-robotics-hard-uncertainty)
(≈24:01). He asks students to keep it in mind through every technical topic: "I think it's
absolutely fundamental to everything in robotics" (≈32:01). He goes further and argues that
"basically every algorithmic contribution or theoretical contribution in robotics in some way or
the other tries to address some particular form of uncertainty" (≈32:48).

## Why it is not obvious: Moravec's paradox

From a human point of view it is hard to see what is hard about robotics. Manipulating objects,
running and driving come naturally to us, yet they are extremely difficult to program a robot
to do autonomously. This observation is **Moravec's paradox** (Lecture 1, ≈23:14). Lecture 1's
way into it is to look at concrete failures and ask what the robot was uncertain about.

## Where uncertainty enters, by area

Lecture 1 lists the forms each of the course's three areas has to deal with (slide 39,
≈32:01–32:48). Each list ends in "…", so these are examples, not a closed list.

![Slide 39 — Uncertainty in each topic area (topic map)](../raw/images/01-intro-to-robotics/slide-39.jpg)

*Slide 39 — the same three areas, each with the uncertainty it has to handle: dynamics and initial state; robot and world state, geometry, semantics; data quality, human intent, rewards. [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

| Area | Uncertainty in |
| --- | --- |
| Planning and control | the dynamics of the robot; the dynamics of the world; the robot's initial state |
| Localization and mapping | the state of the robot; the state and geometry of the world; the semantics of the environment |
| Robot learning | the quality of the data (e.g. demonstrations in imitation learning); human intent; the rewards from the world, or estimated in reinforcement learning |

## Three case studies from Lecture 1

Each is a real failure from the month or two before the lecture. The class proposed sources of
uncertainty, and Majumdar stressed that there is no single right answer and that the true causes
were not public. These are hypotheses, not findings.

**A delivery drone drops a package into a backyard swimming pool** (slide 36, ≈24:47–26:18).
The proposed sources were **localization** (the drone thought it was at the drop point and was
not); **perception out of distribution** (a vision check mistook the pool for ordinary ground);
and **user error** in marking the drop point, which the system should ideally be robust to.

![Slide 36 — What makes robotics hard? (drone delivery news clip)](../raw/images/01-intro-to-robotics/slide-36.jpg)

*Slide 36 — uncertainty case 1: an Amazon delivery drone dropped a package into a backyard swimming pool (ABC7, Aug. 17, 2026). [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

**A humanoid robot fails mid-lift at a weightlifting event** (slide 37, ≈26:18–29:40). The
proposed sources were a **switching error** (the robot believed a subtask was done when it was
not); uncertainty in **its own state** (wrong inferences about its body and what it held);
uncertainty in **its own abilities** ("knowing when it doesn't know"); and Majumdar's own
hypothesis, **the sim-to-real gap** (below).

![Slide 37 — What makes robotics hard? (humanoid weightlifting)](../raw/images/01-intro-to-robotics/slide-37.jpg)

*Slide 37 — uncertainty case 2: a frame from the video of the humanoid weightlifting failure the class analysed, with the robot bent over a loaded barbell. [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

**A Waymo collides with a human-driven car** (slide 38, ≈29:40–31:13). The proposed sources
were **partial observability** (from the Waymo's viewpoint the other car was hidden) and
**human intent** (the Waymo assumed the human would yield and behave rationally). It may also
be a hard-to-attribute error inside the large neural networks that run the system.

![Slide 38 — What makes robotics hard? (dashcam clip)](../raw/images/01-intro-to-robotics/slide-38.jpg)

*Slide 38 — uncertainty case 3: a dashcam frame from the video of the Waymo collision the class analysed; the GPS stamp places it near Sunnyvale. [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

## Sim-to-real and domain randomization

The weightlifting case introduces an idea that recurs whenever learning meets hardware. Many
state-of-the-art legged-locomotion controllers are trained with **reinforcement learning in a
simulator**: a trial-and-error process learns a neural-network controller against a nominal
dynamics model programmed into the simulator. To make the controller survive the real world,
training uses **domain randomization**. Physical parameters such as friction, masses and
inertias are randomized "in the hope that the real world lies somewhere in the combination of
things that you've randomized in your simulator" (Lecture 1, ≈28:53).

There are two ways this can fail. The learning can fixate on peculiarities of the simulator, or
the real system can simply lie outside what was simulated. Majumdar calls the mismatch between
simulation and reality **the sim-to-real gap** (≈29:40). Reinforcement learning is scheduled
for Lectures 21–22 (see the [course map](course-map.md)).

## Hardware as the teacher

Majumdar's other answer to "what makes robotics hard" is to experience it. The best way to
understand the technical challenges is "to try things out yourself on hardware" (≈32:48), which
is why the course's assignments run on [the Crazyflie drone](crazyflie.md). Even the hardware
upgrade comes with a caveat: "There's always some uncertainty anytime you upgrade hardware"
(≈33:34).

## Lectures

- [Lecture 1 — Introduction to Robotics](01-intro-to-robotics.md#what-makes-robotics-hard-uncertainty):
  the theme, Moravec's paradox, the three case studies, and the uncertainty in each area.
- The state-estimation lectures (10–12: nondeterministic filter, Bayes filtering, Kalman and
  particle filtering) are scheduled next in this thread. They are not yet in this knowledge base.
