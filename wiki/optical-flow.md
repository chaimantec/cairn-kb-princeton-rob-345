# Optical flow

**Optical flow** is the apparent motion of things in a camera's view from one frame of video to the next:
a vector at every pixel giving the direction and magnitude of the motion perceived there. ROB 345 covers it
in [Lecture 9](09-optical-flow.md), the first lecture of the module on sensing, localization and mapping,
because it is how the course drone knows its own velocity. This page collects the idea, the derivation and
the Lucas-Kanade method in one place.

Notation follows the course. $I(x, y, t)$ is the grayscale image intensity at pixel $(x, y)$ and time
(frame) $t$; $(u, v)$ is the optical flow at a pixel; $I_x$, $I_y$ and $I_t$ are the partial derivatives
of the intensity along $x$, along $y$ and in time; $\nabla I = [I_x, I_y]$ is the image gradient.
Citations are to Lecture 9: "notes eq. (N)" and "notes p. N" for its written notes, "slide N" for its
deck, and (≈M:SS) for its video.

## Why a robot needs it

To follow a planned path with feedback, a drone has to know where it is. In the course's RRT lab there
were no external cameras or motion capture, only onboard sensors (slide 3, ≈0:57–1:46). Integrating the
accelerometer twice gives position, but needs the initial velocity and turns small measurement errors into
large position errors (≈1:46–3:17). The [Crazyflie](crazyflie.md) instead carries a small downward-facing
camera that measures optical flow (slide 4, ≈3:17–4:03). Given the flow and the drone's height, from a
height sensor such as a single-point lidar, a pinhole camera model gives the drone's velocity: its speed
and its direction relative to the surface beneath it. Working that out is a homework problem
(slide 7, ≈7:50–8:36).

## Apparent motion, not real motion

Flow is what the camera perceives, and it can differ from the real motion between the camera and its
surroundings in both directions (slides 9–10, ≈10:07–12:26). A drone moving over a perfectly
textureless carpet perceives no flow; a camera pointed at a still scene while the lights dim perceives
flow where nothing moves. Apparent motion can come from objects moving, from the camera moving, or from
changes in lighting.

![Slide 6 — Which way is the drone's motion?](../raw/images/09-optical-flow/slide-6.jpg)

*Lecture 9, slide 6 — a flow field from a forward-facing drone camera in a corridor. Most arrows point right or up and to the right, longest on the near wall at the left. The drone is mostly turning to the left. [Deck](https://www.dropbox.com/scl/fi/yjkah2nhv83fdbnf6ea5a/Lecture9_slides.pdf?rlkey=d83o8wcmk8oczkogd2tpuogq3&dl=0)*

Reading a flow field takes practice: in the corridor on Lecture 9's slide 6, objects move to the right in
the image because the drone is turning to the left (≈7:04–7:50). Animals rely on flow too. Birds flying
down a striped corridor slow down when the stripes give more flow, and keep the flow equal in both eyes;
bees signal the distance to nectar as the optical flow integrated along the way, not in kilometres
(slides 11–13, ≈12:26–20:18).

## The constraint equation

The derivation rests on two assumptions (notes p. 1): **color and intensity constancy**, that a point
looks the same at time $t + 1$ as at time $t$, and **small motion**, that points do not move far between
frames, relative to the frame rate. Brightness constancy says (notes eq. (1))

$$I(x, y, t) = I(x + u, y + v, t + 1) \tag{1}$$

A first-order Taylor expansion of the right-hand side, good when the motion is small, gives (notes eq. (2))

$$I(x + u, y + v, t + 1) \approx I(x, y, t) + I_x u + I_y v + I_t \tag{2}$$

and together they give one linear equation per pixel (notes eq. (3)):

$$(\nabla_{x,y} I) \cdot [u, v]^T + I_t = 0 \tag{3}$$

Everything but $(u, v)$ comes from the video by finite differences: $I_t$ as the change in a pixel's
intensity from one frame to the next, $I_x$ and $I_y$ as differences between neighbouring pixels
(≈29:58–31:29, ≈36:08).

## The aperture problem

Eq. (3) is one equation in two unknowns. Only the component of the flow along the gradient is
determined: if $[u, v]^T$ solves it and $[u', v']^T$ is perpendicular to $\nabla I$, so that
$\nabla I \cdot [u', v']^T = 0$ (notes eq. (4)), then $[u + u', v + v']^T$ solves it too (notes p. 3). Motion
perpendicular to the image gradient is invisible to this equation. This is the **aperture problem**: seen
through a small window, the motion of a stripe is ambiguous, and resolving it takes an extra assumption
about the world. The barber pole illusion of Lecture 9's slide 15 shows the brain making one (≈41:35–47:45).

![Notes drawing, p. 3 — the gradient, a flow vector and a second flow vector perpendicular to the gradient](../raw/images/09-optical-flow/notes-figure-3.jpg)

*Lecture 9 notes, p. 3 — the gradient ∇I, a solution [u, v], and a vector [u′, v′] at right angles to the gradient. Adding [u′, v′] gives another solution.*

## Lucas-Kanade

The Lucas-Kanade method (about 1981, notes p. 4) adds **spatial coherence**: a pixel's neighbours move
together, with the same $[u, v]$. It holds inside objects and fails at their boundaries (≈47:45–50:51). In
a 5-by-5 window around a pixel, the 25 copies of eq. (3) form an overdetermined system
$A \bar{d} = \bar{b}$, where the rows of the 25-by-2 matrix $A$ are the gradients $[I_x(p_i), I_y(p_i)]$
at the window's pixels $p_1, \dots, p_{25}$, $\bar{d} = [u, v]^T$, and $\bar{b}$ stacks the values
$-I_t(p_i)$ (notes p. 4). Its least-squares solution is (notes eq. (5))

$$\bar{d}^\ast = (A^T A)^{-1} A^T \bar{b} \tag{5}$$

Repeating this at every pixel gives the flow field. Window sizes of 5 by 5 or 7 by 7 are common; it depends
on the image resolution (≈55:05–55:51).

## When it fails

Eq. (5) needs the 2-by-2 matrix $A^T A$, whose entries are the sums $\Sigma I_x I_x$, $\Sigma I_x I_y$
and $\Sigma I_y I_y$ over the window, to be invertible, that is (notes p. 5)

$$\det(A^T A) = (\Sigma I_x I_x)(\Sigma I_y I_y) - (\Sigma I_x I_y)^2 \neq 0$$

It is zero in two cases (notes p. 5, slides 16–18, ≈1:02:14–1:05:18):

- **Low texture**: the gradients are nearly zero across the window, as on a blank wall or a patch of
  sky. Moving a little shows the same featureless patch.
- **An edge**: every pixel in the window has the same gradient. Moving along the edge shows the same image
  at every step.

It also breaks down when its assumptions do: intensity constancy (lighting changes), small motion, or
spatial coherence (notes p. 5). The notes ask what this implies for the environments a robot should fly in.

## Beyond Lucas-Kanade

Lucas-Kanade is a model-based method, and flow estimates in practice have imperfections and artifacts:
the flow video shown in class jitters and has arrows inconsistent with their neighbours. Today's better methods train a neural network to predict flow, often from simulated
data where the true flow is known, sometimes combined with Lucas-Kanade (≈21:10, ≈1:06:04–1:06:49).
Whatever the method, the velocity estimated from flow is imperfect, and integrating it to get position
amplifies the errors. How to account for imperfect sensing, by combining measurements from several sensors
or over time, is where the course goes next (≈1:08:22; see [uncertainty](uncertainty.md)).

## Lectures

- [Lecture 9 — Optical Flow](09-optical-flow.md): the localization question, the flow camera, apparent
  motion, birds and bees, the derivation, the aperture problem, Lucas-Kanade and its failure cases, and
  imperfect sensing.
- [Lecture 1 — Introduction to Robotics](01-intro-to-robotics.md#anatomy-of-a-robotic-system-sensethinkact):
  the drone's optical flow camera among its sensors, combined with a height sensor to estimate velocity.
- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md#the-labs-and-the-first-hardware-assignment):
  the RRT lab whose localization Lecture 9 asks about.
