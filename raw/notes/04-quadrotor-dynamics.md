---
title: Lecture 4 — Quadrotor Dynamics (lecture notes)
lecture: 4
pages: 7
source_pdf: https://www.dropbox.com/scl/fi/onuvrtpb64sytgp78towu/Lecture4_notes.pdf?rlkey=yo9dpy9jxt7730f0ex3sjdcuw&dl=0
numbering: PDF page N = page N; page 1 prints no number. Equations keep the notes' own numbers (1)–(32).
images: Figures 1, 2 and 3 are rendered as crops of the page, each with its printed caption, and shown under their captions (`notes-figure-1.jpg` to `notes-figure-3.jpg` in this lecture's image folder). Figure 2 is credited in the notes to Bitcraze.io.
figure_audit: An independent reader checked Figures 1–3 against the PDF at 600 dpi, and eqs. (7), (8) and (28)–(31) against the page; every equation was also compared with the PDF's text layer. Fixed: Figure 1(b) missed the solid Y arrow from O, and its 'faint vertical line' is the edge of the pasted drawing's border (seen on the committed render, after the auditor called it invented); Figure 3(b)'s rotor spin directions, first reported illegible, are legible and are now given (checked again on a 600 dpi render); small corrections to the L arrow in Figure 1(a), the arrowhead in Figure 3(a) and the boxes in Figure 2.
---

# Lecture 4 — Quadrotor Dynamics: lecture notes

Full text of the course's written notes for Lecture 4 (A. Majumdar), transcribed from the PDF. Cite as "notes p. N", "notes §N" or "notes eq. (N)". The three figures are described in prose, since the descriptions are the only representation of them here.

[wiki page for this lecture](../../wiki/04-quadrotor-dynamics.md) · [slides](../slides/04-quadrotor-dynamics.md) · [transcript](../transcripts/04-quadrotor-dynamics.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| Introduction (unnumbered) | 1 | none |
| 1. Planar Quadrotor | 1–3 | (1)–(21) |
| 2. Motor Model | 4 | none |
| 3. 3D Quadrotor (3.1 Euler Angles) | 4–5 | none |
| 4. States of the 3D quadrotor | 5 | (22) |
| 5. Motor model for 3D quadrotor | 6 | (23)–(24) |
| 6. Full 3D quadrotor dynamics (sketch) | 6–7 | (25)–(32) |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 1 header: "Insturctor" is evidently "Instructor".
- Page 1, last paragraph: "see Figure 3(b)" is evidently Figure 1(b), the planar quadrotor constrained to move along the y-axis. Figure 3 is the rotor figure on page 6.
- Page 5, section 4: "time derivates" is evidently "time derivatives".
- Page 7, after eq. (28): the expression $\bar{R}(\phi, \theta), \psi)$ has a stray closing parenthesis; evidently $\bar{R}(\phi, \theta, \psi)$ as in eq. (28).
- Page 7, eq. (28): written with $\triangleq$ (defined-as), where it is an equation of motion from Newton's second law; evidently "=" is meant.
- Page 7, eq. (28): the subscript in $F_{tot}$ is typeset in math italics, while eq. (22) and the text on page 5 set it upright ($F_{\text{tot}}$). Same quantity.

---

## Page 1

Intro to Robotics — Lecture #4 — Insturctor: A. Majumdar

So far in the course, we have focused on *geometric* motion planning: computing a path from a starting configuration $A$ to a goal configuration $B$ that avoids obstacles in the environment. Over the next few lectures, we will address two challenges:

(1) **Dynamic feasibility.** Not all paths are feasible for a particular robot. For example, imagine a motion plan for an autonomous vehicle that makes it travel sideways. Unless the car has omni-directional wheels, this is not feasible.

(2) **Errors and disturbances.** Even if the plan is feasible, there may be errors (e.g., in modeling the robot) or external disturbances (e.g., wind gusts) that prevent the robot from following the planned path perfectly.

**Goal** for next 3 lectures: **motion planning with dynamic feasibility**. We will develop techniques that allow us to account for the dynamics of the robot when generating motion plans. After these 3 lectures, we will focus on correcting for errors and disturbances through feedback control.

**Today:** Understand dynamics of a quadrotor.

### 1. Planar Quadrotor

We will first consider a highly simplified model of a quadrotor; this system resides in the x-y plane and is referred to as the "planar quadrotor" (see Figure 1(a)).

**Figure 1.** (a) Planar Quadrotor. (b) Planar Quadrotor constrained to move along $y$-axis.

![Notes Figure 1 — (a) the planar quadrotor; (b) the planar quadrotor constrained to move along the y-axis](../images/04-quadrotor-dynamics/notes-figure-1.jpg)

Description of Figure 1(a): a side view of a quadrotor drawn as a black central body with a red dome on top and a grey arm on each side ending in a motor with a grey propeller disc. The whole vehicle is tilted: the left propeller is lower and the right propeller is higher, so the arm rises to the right. Two thin arrows labelled $F_1$ (left rotor) and $F_2$ (right rotor) start at the propeller hubs and point up and slightly to the left, along the direction perpendicular to the tilted arm (they are not vertical). A double-headed arrow labelled $L$ is drawn just below the arm, parallel to it, from under the centre of the body to the outer end of the right arm, slightly beyond the motor hub (the arm length). At the lower left of the drawing is a coordinate frame with origin $O$, a vertical axis labelled $Y$ pointing up and a horizontal axis labelled $X$ pointing right. This frame is the inertial frame and does not rotate with the vehicle. The tilt angle $\theta$ is not drawn or labelled in this figure.

Description of Figure 1(b): the same vehicle drawn level (arms horizontal). A thin arrow labelled $F_1$ rises vertically from the left propeller hub and a thin arrow labelled $F_2$ rises vertically from the right propeller hub; both point straight up. A solid vertical arrow rises from the origin $O$, below the vehicle, to just above the body, and a dashed vertical line continues it upward through the centre of the body; the label $Y$ sits at the top left of the dashed part. A horizontal axis labelled $X$ points right from $O$. A faint thin grey rectangle, the border of the pasted drawing, encloses the vehicle; its right edge is the faint vertical line at the right of the panel. A red dot marks the centre of the body, as in (a). There is no $L$ or $\theta$ label in this figure.

In fact, we will make things even simpler and begin by only considering the motion in the $y$ direction (i.e., up and down); see Figure 3(b). In this case, we can describe the configuration of the entire quadrotor at any point in time with a single number: the $y$ position of the center of mass (COM). This system thus has *one degree of freedom (DoF)*.

---

## Page 2

How do we describe the motion of this system (still considering only the motion in the $y$ direction)? We can derive the equations of motion (EoMs) for the system using Newton's second law:

$$
m\ddot{y} = F_1 + F_2 - mg,
\tag{1}
$$

where $m$ is the total mass of the quadrotor, and $F_1$ and $F_2$ are the thrust forces from the propeller (we will say more about how motors produce these forces later). Thus,

$$
\ddot{y} = \frac{F_1 + F_2}{m} - g.
\tag{2}
$$

Now, denote the total thrust force produced by the propellers as:

$$
u_1 \triangleq F_1 + F_2.
\tag{3}
$$

We then have:

$$
\ddot{y} = \frac{u_1}{m} - g.
\tag{4}
$$

Now, let's consider the planar quadrotor (no longer constrained to move only along the $y$-direction). How many DoFs does this system have? Answer: 3 DoFs corresponding to $x$-position, $y$-position, and orientation $\theta$.

How do we describe the system's motion? Again, we can use Newton's second law to derive the equations of motion:

$$
\ddot{x} = -\frac{u_1}{m}\sin\theta,
\tag{5}
$$

$$
\ddot{y} = \frac{u_1}{m}\cos\theta - g,
\tag{6}
$$

$$
\ddot{\theta} = \frac{(F_2 - F_1)L}{I}.
\tag{7}
$$

Here, $u_1$ is the same as above (total thrust force), $I$ corresponds to the moment of inertia of the system, and $L$ is the length of the quadrotor's arm (see Figure 1(a)). The moment of inertia is a physical property of the system that can be estimated from the geometry (and mass distribution) of the quadrotor or via physical experiments.

Next, denote the total moment due to the propeller forces as:

$$
u_2 \triangleq (F_2 - F_1)L.
\tag{8}
$$

Our equations of motion for the planar quadrotor can then be expressed as:

$$
\ddot{x} = -\frac{u_1}{m}\sin\theta,
\tag{9}
$$

$$
\ddot{y} = \frac{u_1}{m}\cos\theta - g,
\tag{10}
$$

$$
\ddot{\theta} = \frac{u_2}{I}.
\tag{11}
$$

As a sanity check, Equation (10) matches Equation (2) when $\theta = 0$.

---

## Page 3

**Note:** I will not expect you to derive equations of motion in this course (although students in the MAE department should be able to do this!). We will typically just assume that we are provided the EoMs. But, it is good to go through the exercise of deriving EoMs at least once (as we did with the planar quadrotor above).

The equations (9) – (11) are three *second-order* ordinary differential equations (ODEs). Recall from your ODE course that we can always take a system of second-order ODEs and convert them to a system of first-order ODEs by introducing new variables. Let us see how this works for the planar quadrotor's EoMs.

Define:

$$
v_x \triangleq \dot{x},
\tag{12}
$$

$$
v_y \triangleq \dot{y},
\tag{13}
$$

$$
\omega \triangleq \dot{\theta}.
\tag{14}
$$

We can then re-express the EoMs (9) – (11) as six *first-order* ODEs:

$$
\dot{x} = v_x,
\tag{15}
$$

$$
\dot{y} = v_y,
\tag{16}
$$

$$
\dot{\theta} = \omega,
\tag{17}
$$

$$
\dot{v}_ x = \ddot{x} = -\frac{u_1}{m}\sin\theta,
\tag{18}
$$

$$
\dot{v}_ y = \ddot{y} = \frac{u_1}{m}\cos\theta - g,
\tag{19}
$$

$$
\dot{\omega} = \ddot{\theta} = \frac{u_2}{I}.
\tag{20}
$$

We can then define the **state** of the system as: $\bar{x} = [x, y, \theta, \dot{x}, \dot{y}, \dot{\theta}]^T$. [Note: we will use bars to denote vectors.] The state defines everything we need to know in order to predict the motion of the system. If we specify the initial state of the system (i.e., the state at time $t = 0$), we can solve (either analytically or numerically) the EoMs and obtain the state of the system at any future time.

**Number of states:** The dimensionality of the state vector (i.e., the number of components of the state). The planar quadrotor thus has 6 states. The planar quadrotor constrained to move in the $y$-direction has 2 states (convince yourself of this).

**Configuration variables:** $[x, y, \theta]$. This is the portion of the state that describes the configuration of the system at any given time (this does not include the components of the state corresponding to time derivatives).

**Control input:** $\bar{u} = [u_1, u_2]^T$. These are things that we can directly control/command (the propeller thrusts for the planar quadrotor).

The equations of motion can then be written as:

$$
\dot{\bar{x}} = f(\bar{x}, \bar{u}).
\tag{21}
$$

We will always be able to write EoMs in this form.

---

## Page 4

### 2. Motor Model

So far, we have treated the propellers as thrusters. In reality, we do not directly control the thrust produced; we directly control the speed of the motor. It turns out that there is a nice relationship between the speed of the motor and the generated thrust.

Thrust (produced by propeller spinning): $F = k_f \times (\text{rotational speed of motor})^2$.

The constant $k_f$ is referred to as the *thrust coefficient*. How can we measure this quantity? Here is a simple method: place the drone on a scale and sweep through different values of motor speeds. Measure the readings of the scale (which you can convert from kilograms to Newtons).

We have performed this experiment for a Crazyflie quadrotor. In an upcoming assignment, you will use this data to estimate $k_f$.

The planar quadrotor thus has 3 physical parameters: $m, I, k_f$. In order to fully specify our dynamics model, we need to specify the value of these parameters.

### 3. 3D Quadrotor

**Figure 2.** Axes for (Crazyflie) quadrotor; source: Bitcraze.io.

![Notes Figure 2 — inertial axes and body axes on a Crazyflie quadrotor (source: Bitcraze.io)](../images/04-quadrotor-dynamics/notes-figure-2.jpg)

Description of Figure 2: a rendering of a small quadrotor (four propellers, grey body, white motor mounts) seen from a three-quarter view above. Two sets of three coloured axes are drawn. The large set starts at one common origin at the left of the picture: $\bar{e}_ z$ (blue) points straight up, $\bar{e}_ y$ (green) points up and to the right (away from the viewer, toward the drone), and $\bar{e}_ x$ (red) points down and to the right (toward the viewer, to the lower right). These are the inertial-frame axes. Three small empty rectangles with thin outlines sit near the axes (near the top of $\bar{e}_ z$ and part-way along $\bar{e}_ y$ and $\bar{e}_ x$); they carry no text. The small set starts at the center of the drone body: $\bar{b}_ z$ (blue) points straight up, $\bar{b}_ y$ (green) points up and to the right, and $\bar{b}_ x$ (red) points down and to the right, so each body axis is drawn parallel to the inertial axis of the same letter (the drone is shown unrotated). The labels $\bar{e}_ x, \bar{e}_ y, \bar{e}_ z$ and $\bar{b}_ x, \bar{b}_ y, \bar{b}_ z$ carry bars and subscripts as written here. Propeller spin directions are not marked.

How many degrees of freedom does a full three-dimensional quadrotor have (see Figure 2)?

Position: 3 numbers $x, y, z$;

Orientation: 3 numbers;

$\Longrightarrow$ 6 DoFs.

For the planar quadrotor, the orientation was easy to describe using $\theta$. For the 3D quadrotor, it is slightly more complicated. We will use *Euler angles* to describe the orientation of a 3D quadrotor (and 3D rigid bodies in general).

#### 3.1. Euler Angles

Euler angles allow us to describe orientations in 3D. Suppose we attach axes $\bar{b}_ x, \bar{b}_ y, \bar{b}_ z$ to the body of our quadrotor (see Figure 2).

$\bar{b}_ x$ : Points in the forward direction; $\bar{b}_ y$ : Points in the left direction; $\bar{b}_ z$ : Points up.

---

## Page 5

We will denote this frame by $B$ (corresponding to "body"). We also define $\bar{e}_ x, \bar{e}_ y, \bar{e}_ z$ associated with an *inertial reference frame* $I$.

One way to describe the orientation of $B$ relative to $I$ is the following:

(1) Rotate $B$ about $\bar{e}_ x$ by $\phi$ ("roll");

(2) Then rotate $B$ about $\bar{e}_ y$ by $\theta$ ("pitch");

(3) Then rotate $B$ about $\bar{e}_ z$ by $\psi$ ("yaw").

It turns out that *any* configuration of the quadrotor can be specified by specifying $(\phi, \theta, \psi)$.

The convention above is only one of many possibilities for defining Euler angles. This convention (which is the one we will use in this course) is referred to as the **space $1-2-3$ convention**, since we first rotate about $\bar{e}_ x$ (Axis 1), then about $\bar{e}_ y$ (Axis 2), and then $\bar{e}_ z$ (Axis 3).

There are other possibilities. For example, one could:

- Change the order of rotations, e.g., 2-3-1, or 3-2-1, etc.
- Perform the rotations about the intermediate axes, i.e., first rotate about $\bar{e}_ x$, then perform a rotation about the *new* $\bar{b}_ y$, and then perform a rotation about the *new* $\bar{b}_ z$. This is called the **body 1-2-3 convention**.

In practice, the fact that we have so many different conventions is a source of many headaches/errors. Be careful! Make sure you know which convention you're using (especially if you're working in a team, make sure everyone is using the same convention!). In this course, however, we won't worry too much about different conventions. **We will work with the space 1-2-3 convention in this course.**

### 4. States of the 3D quadrotor

Using Euler angles, the states of the 3D quadrotor are: $\bar{x} = [x, y, z, \phi, \theta, \psi, \dot{x}, \dot{y}, \dot{z}, p, q, r]^T$.

Here, $p, q, r$ correspond to *angular velocities*; these are directly related to $\dot{\phi}, \dot{\theta}, \dot{\psi}$. It is slightly more convenient to work with the angular velocities than with the time derivates of the Euler angles.

Control inputs: we can use the four propeller thrusts as our control inputs. However, as with the planar quadrotor, it will be slightly more convenient to work with the following control input vector:

$$
\bar{u} = [F_{\text{tot}}, M_1, M_2, M_3]^T,
\tag{22}
$$

where:

$F_{\text{tot}}$ : Total thrust (from 4 propellers);

$M_1$ : Moment about $x$-axis;

$M_2$ : Moment about $y$-axis;

$M_3$ : Moment about $z$-axis.

It is easy to go back and forth between $(F_1, F_2, F_3, F_4)$ and $(F_{\text{tot}}, M_1, M_2, M_3)$.

---

## Page 6

### 5. Motor model for 3D quadrotor

For the planar quadrotor, we discussed the relationship between thrust produced by a rotor and the rotor's angular speed:

$$
F_i = k_f \omega_i^2, \quad i = 1, 2, 3, 4,
\tag{23}
$$

i.e., the thrust $F_i$ produced by rotor $i$ is equal to the thrust coefficient $k_f$ times the rotational speed of rotor $i$ squared.

For the 3D setting, the spinning of the propellers (rotors) results in both a thrust *and* a moment. The moment is due to **aerodynamic drag**, and acts about the $\bar{b}_ z$ direction. This is actually what allows the quadrotor to turn in the yaw direction.

**Figure 3.** (a) Directions of thrust force and aerodynamic drag moment. (b) Top view: Adjacent rotors spin in *opposite* directions. Thus, the moments they produce are in opposite directions.

![Notes Figure 3 — (a) a rotor's thrust and aerodynamic drag moment; (b) top view of the four rotors' spin directions](../images/04-quadrotor-dynamics/notes-figure-3.jpg)

Description of Figure 3(a): a hand-drawn side view of a single propeller blade, an elongated figure-eight (two lobes) lying horizontally. A straight arrow labelled $F_i$ starts at the center of the blade and points straight up. Below the blade a curved arrow starts under the left lobe, curves down and to the right, and ends below the middle-right of the blade with its head pointing right, nearly horizontal; the label $M_i^{\text{aero}}$ (printed as M with subscript i and the word aero as a superscript) sits just right of the head. The curved arrow indicates the aerodynamic drag moment about the vertical axis. Because this is a side view, the drawing alone does not settle whether the moment is clockwise or counter-clockwise seen from above.

Description of Figure 3(b): a hand-drawn top view. Two straight lines cross in an X, representing the two diagonals of the quadrotor with a rotor at each of the four ends. A small curved arrow is drawn just outside each end, showing that rotor's spin direction as seen from above. Top-left: the arc runs over the top from left to right, so **clockwise**. Top-right: the arc runs over the top from right to left, so **counter-clockwise**. Bottom-left: the arc runs underneath from left to right, so **counter-clockwise**. Bottom-right: the arc runs underneath from right to left, so **clockwise**. So rotors on the same diagonal spin the same way and adjacent rotors spin opposite ways, as the caption says. The arms carry no labels or rotor numbers.

The aerodynamic moment produced by propeller $i$ is given by:

$$
M_i^{\text{aero}} = k_m \omega_i^2, \quad i = 1, 2, 3, 4,
\tag{24}
$$

where $k_m$ is the drag/moment coefficient.

### 6. Full 3D quadrotor dynamics (sketch)

Remember that dynamics will be of the form:

$$
\dot{\bar{x}} = f(\bar{x}, \bar{u}).
\tag{25}
$$

I'll just sketch the equations here. If you are interested in a more thorough treatment of quadrotor dynamics, you can look at this reference: C. Powers, D. Mellinger, and V. Kumar, "Quadrotor Kinematics and Dynamics", Handbook of Unmanned Aerial Vehicles.

Define:

$$
\bar{r} \triangleq \begin{bmatrix} x \cr y \cr z \end{bmatrix} \quad \text{(Position vector)}
\tag{26}
$$

---

## Page 7

Then,

$$
\dot{\bar{r}} \triangleq \begin{bmatrix} \dot{x} \cr \dot{y} \cr \dot{z} \end{bmatrix} \quad \text{(Velocity vector)}
\tag{27}
$$

From Newton's 2nd law:

$$
\ddot{\bar{r}} \triangleq \begin{bmatrix} 0 \cr 0 \cr -g \end{bmatrix} + \bar{R}(\phi, \theta, \psi) \begin{bmatrix} 0 \cr 0 \cr F_{tot}/m \end{bmatrix},
\tag{28}
$$

where $\bar{R}(\phi, \theta), \psi)$ is a rotation matrix that takes vectors in the body frame and rotates them to the inertial frame.

Define:

$$
\bar{\omega}_ {BW} \triangleq \begin{bmatrix} p \cr q \cr r \end{bmatrix} \quad \text{(Angular velocity vector)}
\tag{29}
$$

Then,

$$
\begin{bmatrix} \dot{\phi} \cr \dot{\theta} \cr \dot{\psi} \end{bmatrix} = \begin{bmatrix} 1 & \sin(\phi)\tan(\theta) & \cos(\phi)\tan(\theta) \cr \cdots & \cdots & \cdots \cr \cdots & \cdots & \cdots \end{bmatrix} \begin{bmatrix} p \cr q \cr r \end{bmatrix}
\tag{30}
$$

The notes print only the first row of the matrix in eq. (30); the other six entries are printed as dots and are elided in the notes, not filled in here.

$$
\dot{\bar{\omega}}_ {BW} = \mathbb{I}^{-1} \left[ -\bar{\omega}_ {BW} \times (\mathbb{I}\bar{\omega}_ {BW}) + \begin{bmatrix} M_1 \cr M_2 \cr M_3 \end{bmatrix} \right],
\tag{31}
$$

where $\times$ is the cross product and $\mathbb{I}$ is known as the *inertia matrix*:

$$
\mathbb{I} \triangleq \begin{bmatrix} I_{xx} & 0 & 0 \cr 0 & I_{yy} & 0 \cr 0 & 0 & I_{zz} \end{bmatrix}
\tag{32}
$$

**Note:** Again, I don't expect you to derive these equations. I just want you to understand that the equations have the form $\dot{\bar{x}} = f(\bar{x}, \bar{u})$.
