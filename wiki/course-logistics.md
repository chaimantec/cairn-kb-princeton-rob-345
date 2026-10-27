# Course logistics — ROB 345/549, Fall 2026

How the course runs, as Majumdar laid it out at the end of
[Lecture 1](01-intro-to-robotics.md#course-logistics) (≈36:40 to the end). Enrolled students
should treat the syllabus and Canvas as authoritative. This page records what the lecture and
its slides said, and some details (exam date, office-hour times) were not yet final.

## Staff

- **Instructor**: Anirudha Majumdar ("Ani"), faculty in MAE and associated faculty in COS,
  co-director of the Princeton Robotics Initiative, and 20% research scientist at Google DeepMind
  (Lecture 1, slide 4).
- **TAs**: Asher Hancock (MAE PhD student in Majumdar's group), Jutang Gao (architecture PhD
  student), Kian Orr (MAE PhD student) and Yanbo Xu (computer science PhD student, also in
  Majumdar's group). Their emails are in the syllabus (slide 45, ≈36:40–37:25).
- **Hardware support**: Jon Prevost (MAE) sets up the lab spaces, netting and hardware. He built
  the custom PCB that powers the drone cameras, and wants to be copied whenever a drone breaks
  (slide 46, ≈37:25–38:58). See [the Crazyflie page](crazyflie.md).

## Prerequisites

The listed prerequisites are multivariable calculus (e.g. MAT 201 or 203), linear algebra
(e.g. MAT 202 or 204), basic probability (e.g. ORF 309), basic differential equations
(e.g. MAE 305), and some programming experience (e.g. COS 126) (slide 47, ≈38:58–42:04).
Majumdar calls the list "overly conservative", and says which parts matter:

- **Multivariable calculus** and **linear algebra** are the critical ones. Linear algebra
  matters especially for feedback control.
- **Probability**: backgrounds vary widely, so he will cover the basics the course needs.
  About 70–80% of the room said they could write down Bayes' rule. The refresher opens
  [Lecture 11](11-bayes-filter.md#probability-basics); see [probability](probability.md).
- **Differential equations**: you will not solve any analytically, since apart from linear
  ones none in the course can be solved that way. You need to know what one means, say
  $\dot{x} = f(x)$ for a state $x$. You also need the idea that, from an initial state, it
  predicts the state at any future time, and that it can be integrated numerically. (The
  captions read "x equals f of x"; the dot is implied by the context.)
- **Programming**: Python only, throughout. Nearly everyone in the room had used it.

## Grading

| Component | Weight | Notes |
| --- | --- | --- |
| Problem sets | 40% | Weekly: assigned Wednesday, due Wednesday midnight. A mix of theory, coding and hardware. Theory and coding are individual; hardware is in teams of four. |
| Term exam | 30% | In person, planned for roughly November (date to be confirmed with the registrar). Theory and coding, no hardware. Covers the fundamentals up to that point. |
| Final project | 30% | In teams, on the drones: vision-based navigation using imitation learning and the course's other robot-learning techniques. |

(Slide 48, ≈42:04–43:37.) The slide calls it a midterm; in the lecture Majumdar says it is now
called a term exam.

## Teams

Teams of four for the hardware portions, formed by Wednesday, September 9, and emailed to the
course staff. Undergraduates team with undergraduates. The 12 graduate students form three
teams. Ed Discussion has a thread for finding teammates. Majumdar suggests mixing majors
(slide 42, ≈35:54–36:40, ≈42:04).

## Office hours

Five hours a week: one from each of the four TAs and one from Majumdar, held in one of the
drone lab spaces. Times were to be announced on Canvas within a day or two of Lecture 1
(slide 49, ≈43:37–44:23).

## Policies

From slide 50 (≈44:23–45:56):

- **Collaboration** on problem sets is permitted and encouraged, including study groups. You
  turn in your own write-up and code reflecting your own understanding. The hardware portions
  are the exception: one team member submits for the team.
- **Late work** loses 10% for every day late. Work more than a week late is not accepted.
  Emergencies such as illness or family emergencies get exceptions if you email Majumdar.
  Being busy with other midterms or assignments does not.
- **The exam** is in person.
- **Attendance** is not tracked but is strongly encouraged. He wants lectures to be interactive.

## Generative AI policy

Four uses are **permitted**, and no others (slide 54, ≈51:22–52:53):

1. **Analysing past assignments**: ones you have already submitted, including working out
   what you got wrong or other ways to solve a problem.
2. **Explaining technical concepts.**
3. **Asking about Python syntax.**
4. **Any use whatsoever for the hardware-based assignments and the final project**, with any
   coding agent or LLM. This is deliberate. Because the work closes a loop with a physical
   system, it is a good place to learn the strengths and limits of these tools.

If you think another use would be valuable, he asks you to tell him.

The reasoning behind the policy is on the
[Lecture 1 page](01-intro-to-robotics.md#generative-ai-the-courses-position-and-policy). In
brief: the tension between proficiency with AI and the discipline to learn fundamentals; the
spectrum from Luddism ("Never use AI for anything!") to nihilism ("AGI is inevitable. No need to
learn anything!"); and a case study of a Claude model that reversed a confident conclusion when
challenged with a paper. The tools are "imperfect in very, very subtle ways."

## Textbooks and references

There is no required textbook (slide 55, ≈52:53–54:24). Slides and course notes are posted per
lecture (see [`sources.md`](../sources.md)). Three references are named, which Majumdar will
point to as the course goes:

- D. Gammelli, J. Lorenzetti, K. Luo, G. Zardini, M. Pavone, *Principles of Robot Autonomy*.
  A recent book, free on arXiv: <https://arxiv.org/pdf/2608.03496>.
- S. M. LaValle, *Planning Algorithms*. A classic for motion planning, free online at
  <http://planning.cs.uiuc.edu/>.
- S. Thrun, W. Burgard, D. Fox, *Probabilistic Robotics*. For localization, mapping and SLAM;
  parts are available online.

## Tools

Gradescope for submissions and Ed Discussion for questions, both through Canvas (slide 56,
≈54:24–55:09). Majumdar prefers questions on Ed to email, unless they are confidential, so
everyone benefits from the discussion. That includes drone setup problems.

## ROB 345 vs. ROB 549

ROB 345 is the undergraduate course, with 60 students. ROB 549 is the graduate track: 12
students, "12/12" enrolled per the slide, aimed at first-year PhD students per the course
website. Lectures are shared, as are most assignments. ROB 549 gets extra or different problems,
clearly marked, and possibly a slightly different exam (slide 57, ≈55:09–55:56).
