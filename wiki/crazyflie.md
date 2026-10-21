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

## Its model

[Lecture 4](04-quadrotor-dynamics.md) writes down how the drone moves; the equations are on
[the quadrotor model](quadrotor-model.md). A few facts there are about this particular drone:

- **Its axes.** A small nub on the Crazyflie marks the forward direction. The body axes are $x$
  forward, $y$ left and $z$ up, a right-handed frame, and the labs use the same convention
  (Lecture 4, ≈28:52–29:39). The Lecture 4 notes draw the axes on a Crazyflie, crediting Bitcraze.
- **Its propellers.** Adjacent propellers spin in opposite directions, which is what lets the drone
  yaw in place, and the blades of opposite-spinning propellers are pitched the other way so that
  every propeller pushes up (Lecture 4, ≈55:31–58:37).
- **Its thrust coefficient.** The thrust of each propeller is $k_f \omega_i^2$, where $\omega_i$ is
  its rotational speed. The course staff measured $k_f$ again for the new brushless drones by
  flipping one onto a raised digital scale and sweeping the motor speed, and an assignment asks
  students to estimate $k_f$ from that data (Lecture 4, ≈50:49–53:52; Lecture 4 notes, p. 4).

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

Lecture 4 shows both spaces and gives the details (≈58:37–1:07:51). G109
is in the G-wing of the EQuad and has two netted flying spaces separated by a middle net (Lecture 4,
slide 7, ≈59:25).

![Slide 7 — EQuad, G109](../raw/images/04-quadrotor-dynamics/slide-7.jpg)

*Lecture 4, slide 7 — G109 in the EQuad: the netted flying area with green turf and blue foam-pole obstacles, desks outside the net. [Deck](https://www.dropbox.com/scl/fi/v8bp2gyhpixill7c70u7q/Lecture4_slides.pdf?rlkey=h44i0kp1bpmxk3zdg65gvqu29&dl=0)*

The SEAS Robotics lab, in the F-wing, is slightly smaller. It is the large robotics lab on the
left as you enter the EQuad, by the EQuad café (Lecture 4, slide 8, ≈1:00:11).

![Slide 8 — SEAS Robotics lab (F-wing, EQuad)](../raw/images/04-quadrotor-dynamics/slide-8.jpg)

*Lecture 4, slide 8 — the smaller netted space in the SEAS Robotics lab, seen through the netting. [Deck](https://www.dropbox.com/scl/fi/v8bp2gyhpixill7c70u7q/Lecture4_slides.pdf?rlkey=h44i0kp1bpmxk3zdg65gvqu29&dl=0)*

Lecture 4 counts **four drones in G109 and three in the SEAS Robotics lab**, together with spare
propellers, motors and prop guards, a measuring tape for mapping the obstacles, and safety glasses
(slide 11, ≈1:02:28). The spaces are open at any time, weekdays and weekends, to anyone who has
completed the online safety training. There is no sign-up sheet: teams take turns, and debug
outside the net while another team flies (slide 12, ≈1:03:14–1:04:48). Wear safety glasses, stand
outside the netted area while a drone is flying, and treat the drones with care. All the teams share
seven or eight drones, each about 600 dollars with its parts, and last year two teams stepped on
drones and crushed them (slide 13, ≈1:05:33–1:07:51).

**When a drone breaks**, email the course staff and copy Jon Prevost. The plan is to fix drones
quickly with replacement parts rather than build new ones (≈38:12–38:58). By Lecture 4 the channel
was a "Drone issues" thread on Ed Discussion: post the drone's number there and use another drone
(Lecture 4, slide 12, ≈1:04:48). Majumdar asks
students to report problems early and to be patient with the new fleet (≈34:21).

## Lectures

- [Lecture 1 — Introduction to Robotics](01-intro-to-robotics.md#hardware-the-crazyflie-drone):
  the platform, the hardware goal, teams and labs.
- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): the drone's dynamics model, its
  axes and motor model, the two lab spaces in detail, and the first hardware lab (an RRT on the
  drone).
- [Lecture 7 — Stability and PD Control](07-stability-and-pd-control.md): the lab announced for the
  following week, implementing an LQR controller that makes the real drone stabilize itself
  (≈10:06), and the sources of model error on the real drone (unmodeled aerodynamics, inertia
  estimated with a pendulum setup, thrust that changes with the battery level; ≈5:34).
- Lecture 9 (Optical flow) covers the drone's optical flow sensing. It is not yet in this
  knowledge base; see the [course map](course-map.md).
