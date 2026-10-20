# The Crazyflie drone: the course's robot

Every hardware assignment and the final project in ROB 345/549 run on the **Crazyflie**, a
small open-source quadrotor from Bitcraze. "I think this would not be a robotics course without
actual physical robots that we get to play with" ([Lecture 1](01-intro-to-robotics.md#hardware-the-crazyflie-drone),
≈32:48). The reason for building the course around hardware is Majumdar's view that the best way
to appreciate the technical challenges of robotics is to try things yourself: "Nothing like
seeing things work (or not) in practice!" (slide 40).

![Slide 40 — Course plan: hardware implementation](../raw/images/01-intro-to-robotics/slide-40.jpg)

*Slide 40 — the Crazyflie 2.1 brushless drone used for every hardware assignment, new for Fall 2026. [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

## The platform

The Fall 2026 course uses the **Crazyflie 2.1 brushless**, described on the slide as an "open
source platform, small, light-weight, ideal for testing" (Lecture 1, slide 40, ≈32:48–34:21).
These drones are new that year. Earlier offerings used a non-brushless Crazyflie, and the
previous year's course evaluations held "lots of well-founded complaints" about it. The
department paid to replace the whole fleet. Majumdar expects better motors, flight time and
battery life, and the analog cameras give way to digital FPV cameras (≈33:34–34:21).

The course website's parts list for the motion-planning and feedback-control assignments is the
Crazyflie 2.1 (brushless), the **Flow deck v2** and the **Crazyradio PA**. The final project adds
a digital FPV camera and long pins (see [`sources.md`](../sources.md)).

## Its sensors and actuators

Lecture 1 uses the drone to illustrate the [sense–think–act](sense-think-act.md) anatomy of a
robot (slide 32, ≈18:40–20:56):

![Slide 32 — Anatomy of a robotic system](../raw/images/01-intro-to-robotics/slide-32.jpg)

*Slide 32 — the sense–think–act loop on the course's Crazyflie: sensors (IMU, optical flow camera) feed computation, which commands the actuators (motors and propellers), clockwise and repeating. [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

- **Actuators**: the propellers and motors.
- **Sensors**: an **inertial measurement unit (IMU)** for orientation and acceleration; a
  downward-facing **optical flow camera** that detects the ground's apparent motion beneath the
  drone; and a **height sensor**. Together, optical flow and height give a fairly accurate
  estimate of the drone's velocity relative to the ground.
- **Computation**: processes the measurements and decides the motor commands.

For the final project the drone also carries a camera that streams images in real time to a
laptop. Jon Prevost of MAE designed and built a custom PCB to power the cameras (≈37:25–38:12).

## Is it a robot?

In the class's "Is this a robot?" exercise, a Crazyflie with a camera on top is the second
example (slide 26, ≈13:15–14:48). It is clearly an embodied agent, and clearly programmable:
"that's what you'll do in your assignments". The only arguable test is the physical task.
Students suggested taking pictures, flying, navigation and collision avoidance.

![Slide 26 — What is a robot? (Is this a robot? small drone)](../raw/images/01-intro-to-robotics/slide-26.jpg)

*Slide 26 — What is a robot? (Is this a robot? small drone). [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

## What the course does with it

**The goal** of the hardware component is to **make the drone navigate autonomously** through an
obstacle environment set up in the lab (slide 41, ≈34:21–35:54). The previous year's final
project shows the end state. On demo day, teams find obstacles in a semi-random configuration
they have not seen. The drone's camera sends images to a laptop, where a **visual navigation
policy trained with imitation learning**, a neural network, does the navigation. The
assignments build up to this.

![Slide 41 — Course plan: hardware implementation (goal)](../raw/images/01-intro-to-robotics/slide-41.jpg)

*Slide 41 — the hardware goal, autonomous navigation, and one of the netted flight arenas with its foam-padded pole obstacles. [Deck](https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0)*

**Teams of four** do the hardware parts of the assignments and the final project. Theory and
coding parts are individual (slide 42, ≈35:54, ≈42:04).

**Generative AI** is unrestricted for the hardware assignments and the final project. Majumdar
sees this as the place to learn what coding agents can and cannot do, because there is "some
loop with the physical system itself" (slide 54, ≈52:07–52:53). See
[course logistics](course-logistics.md#generative-ai-policy).

## The lab

Two lab spaces have netted flying arenas (slide 43, ≈55:56–56:42). One is in **G109 of the
E-Quad** (the G wing), with two netted arenas. The other is a room in the **SEAS Robotics Lab**
in the F-wing, part of a robotics research facility near the E-Quad café entrance. About four or
five drones are kept set up in each space. A team picks up any available drone, works, and
leaves it there (≈38:12). Access requires Princeton's general lab-safety training through EHS,
which has online and in-person parts (<https://ehs.princeton.edu/training>).

**When a drone breaks**, email the course staff and copy Jon Prevost. The plan is to fix drones
quickly with replacement parts rather than build new ones (≈38:12–38:58). Majumdar asks
students to report problems early and to be patient with the new fleet (≈34:21).

## Lectures

- [Lecture 1 — Introduction to Robotics](01-intro-to-robotics.md#hardware-the-crazyflie-drone):
  the platform, the hardware goal, teams and labs.
- Lecture 4 (Quadrotor dynamics) and Lecture 9 (Optical flow) model and sense this vehicle.
  They are not yet in this knowledge base; see the [course map](course-map.md).
