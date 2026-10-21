# The quadrotor model

The course's robot is a quadrotor, the [Crazyflie](crazyflie.md), and from Lecture 4 on its
planning and control lectures work with a mathematical model of how it moves. This page collects
that model in one place: the planar quadrotor and its equations of motion, the 3D quadrotor's
frames, Euler-angle convention, state and control input, and the motor model that links propeller
speed to thrust and to the moment that makes the drone yaw. The derivation and its classroom
discussion are on the [Lecture 4 page](04-quadrotor-dynamics.md). Equation numbers are those of
the Lecture 4 notes ([PDF](https://www.dropbox.com/scl/fi/onuvrtpb64sytgp78towu/Lecture4_notes.pdf?rlkey=yo9dpy9jxt7730f0ex3sjdcuw&dl=0),
[as text](../raw/notes/04-quadrotor-dynamics.md)), and timestamps refer to Lecture 4. The
general form the model takes, $\dot{\bar{x}} = f(\bar{x}, \bar{u})$, has its own page,
[state and dynamics](state-and-dynamics.md).

You will not be asked to derive these equations: "I will not expect you to derive equations of
motion in this course (although students in the MAE department should be able to do this!)"
(notes p. 3). What the course expects is that you know their structure and can use them.

## Why the course needs a dynamics model

Geometric motion planning, as in [Lectures 2](02-discrete-motion-planning.md) and
[3](03-rrts.md), treats the robot as something that can move along any collision-free path. A
quadrotor cannot. Its propellers push only perpendicular to its body, so a level quadrotor cannot
slide sideways at constant height (Lecture 4, ≈2:33–3:18). A plan that ignores this is not
**dynamically feasible**. Lectures 4–6 develop planning that respects the dynamics, and later
lectures use the same model for feedback control (Lecture 4, ≈4:04; see the
[course map](course-map.md)).

## The planar quadrotor

The planar quadrotor is a quadrotor confined to a vertical plane, a two-propeller "birotor"
that the course still calls a quadrotor (Lecture 4, ≈5:38). The course used it earlier as a
configuration-space example, with three degrees of freedom (see
[configuration space](configuration-space.md)).

![Notes Figure 1 — (a) the planar quadrotor; (b) the planar quadrotor constrained to move along the y-axis](../raw/images/04-quadrotor-dynamics/notes-figure-1.jpg)

*Notes Figure 1 — (a) the planar quadrotor with thrusts F1 and F2 perpendicular to its tilted arm and arm length L; (b) the version constrained to move along Y. [Notes](https://www.dropbox.com/scl/fi/onuvrtpb64sytgp78towu/Lecture4_notes.pdf?rlkey=yo9dpy9jxt7730f0ex3sjdcuw&dl=0)*

| Quantity | Symbol | Meaning |
| --- | --- | --- |
| configuration | $x$, $y$, $\theta$ | position of the centre of mass, and the tilt angle |
| thrusts | $F_1$, $F_2$ | thrust force of each propeller, perpendicular to the arm |
| mass | $m$ | total mass |
| arm length | $L$ | distance from the centre of mass to a propeller |
| moment of inertia | $I$ | how the mass is spread out in the body; measured, or estimated from a CAD model |
| gravity | $g$ | gravitational acceleration |
| total thrust | $u_1 \triangleq F_1 + F_2$ | eq. (3) |
| total moment | $u_2 \triangleq (F_2 - F_1)L$ | eq. (8) |

Newton's second law gives the **equations of motion** (notes eqs. (9)–(11)):

$$\ddot{x} = -\frac{u_1}{m}\sin\theta \tag{9}$$

$$\ddot{y} = \frac{u_1}{m}\cos\theta - g \tag{10}$$

$$\ddot{\theta} = \frac{u_2}{I} \tag{11}$$

The total thrust, tilted by $\theta$, accelerates the centre of mass. Its horizontal component is
$-u_1 \sin\theta$, so a positive tilt pushes the drone in the negative $x$ direction, and its
vertical component $u_1 \cos\theta$ fights gravity. The difference between the two thrusts,
times the arm length, turns the drone. At $\theta = 0$ eq. (10) reduces to the one-dimensional
model of a drone that only moves up and down, $\ddot{y} = u_1/m - g$ (notes eqs. (2) and (4)).

In first-order form, with $v_x \triangleq \dot{x}$, $v_y \triangleq \dot{y}$ and
$\omega \triangleq \dot{\theta}$ (notes eqs. (12)–(20)):

| | |
| --- | --- |
| state | $\bar{x} = [x, y, \theta, \dot{x}, \dot{y}, \dot{\theta}]^T$, 6 states |
| configuration variables | $[x, y, \theta]$ |
| control input | $\bar{u} = [u_1, u_2]^T$ |
| dynamics | $\dot{x} = v_x$, $\dot{y} = v_y$, $\dot{\theta} = \omega$, $\dot{v}_ x = -\frac{u_1}{m}\sin\theta$, $\dot{v}_ y = \frac{u_1}{m}\cos\theta - g$, $\dot{\omega} = \frac{u_2}{I}$ |

The version constrained to move along $y$ has one degree of freedom and 2 states, $y$ and
$\dot{y}$ (notes p. 3).

## The 3D quadrotor

**Six degrees of freedom**: the position $x$, $y$, $z$ of the centre of mass and three angles of
orientation (notes p. 4, Lecture 4 ≈26:34–27:19).

**Frames.** The inertial frame $I$, with directions $\bar{e}_ x$, $\bar{e}_ y$, $\bar{e}_ z$, is
fixed to the room. The body frame $B$, with directions $\bar{b}_ x$, $\bar{b}_ y$, $\bar{b}_ z$,
is attached to the drone at its centre of mass: $\bar{b}_ x$ points **forward**, $\bar{b}_ y$
**left**, $\bar{b}_ z$ **up** (notes pp. 4–5). On the Crazyflie a small nub marks the forward
direction. The same right-handed convention, $x$ forward, $y$ left, $z$ up, is used in the labs
(Lecture 4, ≈28:52–29:39).

![Notes Figure 2 — inertial axes and body axes on a Crazyflie quadrotor (source: Bitcraze.io)](../raw/images/04-quadrotor-dynamics/notes-figure-2.jpg)

*Notes Figure 2 — inertial axes (left) and body axes (at the drone's centre), x red, y green, z blue. The notes credit the drawing to Bitcraze.io. [Notes](https://www.dropbox.com/scl/fi/onuvrtpb64sytgp78towu/Lecture4_notes.pdf?rlkey=yo9dpy9jxt7730f0ex3sjdcuw&dl=0)*

**Orientation: Euler angles, space 1-2-3.** Start with the body frame aligned with the inertial
frame, then rotate it about $\bar{e}_ x$ by the **roll** $\phi$, about $\bar{e}_ y$ by the
**pitch** $\theta$, and about $\bar{e}_ z$ by the **yaw** $\psi$, each by the right-hand rule
(notes p. 5). Any orientation can be reached this way, though not always by a unique triple
(Lecture 4, ≈34:24–35:10). "Space" means the rotations are about the fixed inertial axes; "1-2-3"
gives their order. Body conventions instead rotate about the new intermediate body axes. The course
uses **space 1-2-3** throughout, and the notes warn that mixing conventions "is a source of many
headaches/errors" (notes p. 5). The [Lecture 4 page](04-quadrotor-dynamics.md#euler-angles) has the
details and the classroom discussion.

**State: 12 dimensions** (notes p. 5):

$$\bar{x} = [x, y, z, \phi, \theta, \psi, \dot{x}, \dot{y}, \dot{z}, p, q, r]^T$$

Here $p$, $q$, $r$ are the components of the angular velocity $\bar{\omega}_ {BW}$. They are
related to the Euler-angle rates $\dot{\phi}$, $\dot{\theta}$, $\dot{\psi}$ (eq. (30)), and using
them makes the equations more compact (Lecture 4, ≈42:59–43:47).

**Control input** (notes eq. (22)):

$$\bar{u} = [F_{\text{tot}}, M_1, M_2, M_3]^T \tag{22}$$

$F_{\text{tot}}$ is the total thrust of the four propellers, and $M_1$, $M_2$, $M_3$ are the
moments about the $x$, $y$ and $z$ axes. They are computed from the four propeller thrusts
$F_1, \dots, F_4$ and the drone's geometry, and back.

**Dynamics** (notes §6, sketched; the full equations are in C. Powers, D. Mellinger and V. Kumar,
"Quadrotor Kinematics and Dynamics", *Handbook of Unmanned Aerial Vehicles*). The translational
part is

$$\ddot{\bar{r}} = \begin{bmatrix} 0 \cr 0 \cr -g \end{bmatrix} + \bar{R}(\phi, \theta, \psi) \begin{bmatrix} 0 \cr 0 \cr F_{\text{tot}}/m \end{bmatrix} \tag{28}$$

with $\bar{r} = [x, y, z]^T$ and $\bar{R}$ the rotation matrix from the body frame to the inertial
frame: thrust acts along the body's $z$ axis, gravity along the room's. The rotational part is

$$\dot{\bar{\omega}}_ {BW} = \mathbb{I}^{-1} \left[ -\bar{\omega}_ {BW} \times (\mathbb{I}\bar{\omega}_ {BW}) + \begin{bmatrix} M_1 \cr M_2 \cr M_3 \end{bmatrix} \right] \tag{31}$$

with the diagonal inertia matrix $\mathbb{I}$, whose entries are $I_{xx}$, $I_{yy}$, $I_{zz}$
(eq. (32)). The notes print eq. (28) with $\triangleq$, a printed slip, and elide most of
eq. (30). All of this has the form $\dot{\bar{x}} = f(\bar{x}, \bar{u})$.

**Flat outputs.** [Lecture 5](05-differential-flatness.md#the-3d-quadrotors-flat-outputs) states,
without proof, that the 3D quadrotor is [differentially flat](differential-flatness.md) with flat
outputs $x$, $y$, $z$ and the yaw $\psi$. Any sufficiently smooth trajectory of those four can be
flown, and the control inputs, the roll and the pitch follow from it. The planar quadrotor is flat
with flat outputs $x$ and $y$, and Lecture 5 proves it from eqs. (9)–(11), written there in $F_1$
and $F_2$ (Lecture 5 notes eqs. (1)–(4)).

## The motor model

What the drone really controls is the current to each motor, which sets the rotational speed
$\omega_i$ of propeller $i$ (Lecture 4, ≈48:30). Thrust and drag moment both grow with the square
of that speed (notes eqs. (23) and (24)):

$$F_i = k_f \omega_i^2, \quad i = 1, 2, 3, 4 \tag{23}$$

$$M_i^{\text{aero}} = k_m \omega_i^2, \quad i = 1, 2, 3, 4 \tag{24}$$

- $k_f$, the **thrust coefficient**, depends on the propeller's size and blade pitch. It is
  measured rather than computed. The course flips the drone onto a digital weighing scale, raised
  on a stand so that prop wash does not distort the reading, sweeps the motor speed, and takes the
  slope of thrust against $\omega_i^2$, allowing for the four motors (Lecture 4, ≈50:03–53:52).
  An assignment asks students to estimate $k_f$ from this data (notes p. 4).
- $k_m$, the **drag/moment coefficient**, scales the aerodynamic drag moment about $\bar{b}_ z$.
  It is the reaction of the air to the spinning propeller, by Newton's third law (≈56:16).

The model assumes identical motors and is an aggregate aerodynamics model, imperfect but good
enough for much of what a drone needs (≈53:52). With it, the planar quadrotor's physical
parameters are $m$, $I$ and $k_f$ (notes p. 4).

## Yaw: why adjacent rotors spin opposite ways

Seen from above, adjacent rotors spin in opposite directions: in notes Figure 3(b) the top-left
and bottom-right rotors spin clockwise and the other two counter-clockwise. Their drag moments
therefore point in opposite directions (notes p. 6). Speeding up one pair and slowing the other
makes the drone **yaw in place** one way, and the reverse yaws it the other way, something it can
do although it cannot translate sideways while level (Lecture 4, ≈53:52–57:04).
Every propeller still pushes up, because the blades of the opposite-spinning propellers are angled
the other way (≈57:51–58:37).

![Notes Figure 3 — (a) a rotor's thrust and aerodynamic drag moment; (b) top view of the four rotors' spin directions](../raw/images/04-quadrotor-dynamics/notes-figure-3.jpg)

*Notes Figure 3 — (a) one rotor's upward thrust and its drag moment about the vertical axis; (b) top view: diagonal rotors spin the same way, adjacent rotors opposite ways. [Notes](https://www.dropbox.com/scl/fi/onuvrtpb64sytgp78towu/Lecture4_notes.pdf?rlkey=yo9dpy9jxt7730f0ex3sjdcuw&dl=0)*

## Lectures

- [Lecture 4 — Quadrotor Dynamics](04-quadrotor-dynamics.md): the whole model, derived for the
  planar quadrotor and sketched for the 3D quadrotor, with the motor model and the lab.
- [Lecture 2](02-discrete-motion-planning.md) and [Lecture 3](03-rrts.md) use the planar
  quadrotor as a configuration-space example, without its dynamics.
- [Lecture 5 — Differential Flatness](05-differential-flatness.md) plans with this model: it proves
  the planar quadrotor flat and states the 3D quadrotor's flat outputs.
- Lecture 6 (trajectory optimization) also plans with this model, and Lectures 7 and 8 (stability
  and PD control, LQR) turn to feedback control. They are not yet in this knowledge base; see the
  [course map](course-map.md).
