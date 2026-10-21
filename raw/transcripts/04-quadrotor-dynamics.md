---
title: "Lecture 4: Quadrotor Dynamics"
lecture: 4
video: https://www.youtube.com/watch?v=upI4KaGawyE
source: copy-edited from the YouTube auto-captions
verbatim_original: not committed - regenerate from the video (see below)
material: ../slides/04-quadrotor-dynamics.md
notes: ../notes/04-quadrotor-dynamics.md
---

# Lecture 4: Quadrotor Dynamics — transcript

This is the edited transcript. The captions have been repunctuated, stripped of filler, had mis-heard terms restored, and had student turns marked `*[Student question]*` or `*[Student answer]*`; no content was added, removed or reordered, and every `[MM:SS]` marker is in its original position. The verbatim captions are not committed to this repo. They can be regenerated from the video id above with the `cairn-kb` skill's `fetch_transcript.py` piped through `transcript_to_md.py`. Terminology was cross-checked against [the lecture's slides](../slides/04-quadrotor-dynamics.md) and [the lecture notes](../notes/04-quadrotor-dynamics.md). Notation is kept as spoken: "x double dot", "u one" and "F one plus F two" are written x double dot, u1 and F1 plus F2, as in notes eqs. (1)-(11); the lecturer's "x bar" and "u bar" are the notes' state and control vectors. Where the captions mangle dictated notation, it is marked in the text and listed below. Student turns are run together with the lecturer's speech in the captions and are only partly captured; where a question was not captured, only the tag is kept.

## Restorations

| Caption | Restored | Confirmed by |
|---|---|---|
| AAR (1:00) | A* | context only (the list of Lecture 2 and 3 planners; Lecture 2 slide 61) |
| RT, RT algorithm | RRT, RRT algorithm | slides 9, 10; notes p. 1 context |
| planer, planer quadrotor, quadro order, quoter | planar, planar quadrotor, quadrotor | notes p. 1 ("planar quadrotor") |
| f_sub_1, f_sub_2, f_sub_3, f_sub_4, f_sub_i | F1, F2, F3, F4, F i | notes eqs. (1), (23) |
| cossine | cosine | context only |
| x dot, y dot, theta dot (7:14-12:40, where the lecturer means the second derivative) | x double dot, y double dot, theta double dot | notes eqs. (5)-(7), (9)-(11); the lecturer says "second time derivative of x" at 7:14 (see below) |
| x dot (15:43, "the time dative of x dot which is x dot") | x double dot | notes eqs. (18)-(20); see below |
| theta dot (21:10, "omega dot, which is the same as theta dot") | theta double dot | notes eq. (20) |
| MA 206, MA student | MAE 206, MAE student | notes p. 3 ("students in the MAE department"); the lecturer says "MAE friends" at 26:34 |
| difficq, diffic | diffeq, diffeqs | context only |
| mat lab | MATLAB | context only |
| f ofxq (25:48) | f of x, u | notes eq. (21) |
| oiler, our angles | Euler, Euler angles | notes p. 4 ("Euler angles") |
| quitterians | quaternions | context only |
| five (31:13), fi, pi, "fa side dot" | phi, phi, phi, phi dot, theta dot, psi dot | notes p. 5 (roll phi) |
| S, si, "5 theta s" | psi, psi, phi theta psi | notes p. 5 (yaw psi) |
| role | roll | notes p. 5 |
| "S. So this is going to be Y" (32:50) | psi. So this is going to be yaw | notes p. 5 |
| ex ey ez, bx by bzz | e x, e y, e z, b x, b y, b z | notes p. 4-5 (e-bar x etc.; b-bar x etc.) |
| coom m | COM, center of mass | notes p. 1 (COM) |
| PQ and R | p, q and r | notes p. 5 |
| KF | k f | notes p. 4 (thrust coefficient k_f) |
| omega I squared | omega i squared | notes eq. (23) |
| mi arrow | M i aero | notes eq. (24) (M_i^aero) |
| propw wash | prop wash | context only |
| wing scale, wing scale (several) | weighing scale | context only (the lecturer says "weighing scale" nearby, 52:20) |
| Equad | EQuad | slides 7, 8 |
| C's robotics lab | SEAS Robotics lab | slide 8 |
| weddness day | Wednesday | context only |
| at discussion | Ed Discussion | slide 12 (the "Drone issues" thread in Ed) |
| "600" with a leading dollar sign | 600 dollars | slide 13 |
| way points | waypoints | context only |
| dos (5:38) | DOFs | notes p. 1 (DoF) |
| John Po (1:04:48) | Jon Prevost | Lecture 1, slide 46 ("Jon Prevost (MAE)"); the same caption was restored the same way in Lecture 1's transcript |

## Places left unclear

- 7:14 to 12:40, 15:43, 21:10: the captions write "x dot", "y dot" and "theta dot" where the lecturer means the second derivatives (at 7:14 the lecturer says "the second time derivative of x"; at 15:43 "x double dot or sorry"). The captions seem to drop the word "double"; it is restored as "x double dot" and so on, from the lecturer's own wording and notes eqs. (5)-(7). The 15:43 sentence "the time derivative of vx is then x dot ... which is x dot" is garbled and was restored as "x double dot" in the same way.
- 7:14 to 8:02: the lecturer first writes F1 plus F2 cosine theta over m for the x equation, then corrects the sign and the trigonometric function aloud ("this should be negative ... and then sin theta"). Kept as said; the notes (eqs. (5), (9)) have the x equation as negative u1 over m times sine theta. The lecturer's spoken form of the x and y equations omits parentheses ("F1 plus F2 cosine theta"); the notes' eq. (6) has the total thrust times cosine theta.
- 4:04 and 24:17: the course number "MA 206" is read as MAE 206 (see notes p. 3); the number itself is not confirmed by the slides or notes.
- 25:48: "x dot equals f ofxq" is read as "f of x, u" (notes eq. (21)).
- 36:47: "sort of 31213" (a list of rotation orders) is not resolved.
- 43:47: the captions' run of "dot dot dot ..." after "phi do theta dot" is read as "phi dot, theta dot, psi dot"; the garbled stretch is not otherwise recoverable.
- 1:00:56: "the simplest possible mapping algorithm which is U" is not resolved (possibly "you", meaning the student measures the map by hand).
- 50:49: "Kian, who's sitting at the back" is kept as captioned; it is presumably the teaching assistant Kian Orr (Lecture 1, slide 45), but the lecture does not give the surname.
- 32:01 and 33:37: the lecturer says rotations follow the right hand rule and rotate "kind of clockwise", and that positive pitch by this convention "is kind of pitching down"; neither is in the notes and both are left as spoken.

## Transcript

**[0:13]** So we're going to continue our discussion of motion planning. So maybe just as a quick reminder, in the past two lectures we focused on this problem of geometric motion planning. So how do you get your robot to plan some path from configuration A to configuration B without colliding with any obstacles that are in the environment? So the plan for the next couple of lectures is to start thinking about the dynamics of the robot, which so far is something that we've ignored. And I guess specifically there are two challenges with the kind of geometric motion planning techniques that we've discussed so far that we want to start addressing. The first one is what's known as dynamic feasibility. So basically not all motion plans that come

**[1:00]** out of A* or the RRT algorithm, which we looked at in the last lecture, are actually physically executable by whatever robot you happen to have. And maybe just as a sort of quick check to see if everyone understands what we mean by this, let's try to think about a motion plan, let's say that comes out of RRT or some other algorithm, that is not actually dynamically feasible, that's not physically executable by a drone. So let's say, yeah, I brought the drone that we're going to be using for this course along today. You'll have a chance to start using it in the upcoming assignment, which will go out tomorrow. But yeah, I

**[1:46]** guess for now, let's just think about some simple, let's say, motion plan that is not actually physically executable by the robot. Thoughts on this? Go ahead.

*[Student answer]* Maybe something that has a lot of really tight turns that the drone can't really achieve.

Yep. Yeah. So kind of very, very agile motions. There might be a certain minimum amount of, like, curvature. Yeah, I guess other thoughts. Yeah,

*[Student answer]* One frame, like fully to the right, max velocity, and then right, and one more time, fully to the left, max velocity.

That's right. Yeah. So something where it's actually a sharp curve may not be physically feasible. Go ahead.

*[Student answer]* Maybe like a crevice you have to go through where you have to orient sideways, but

**[2:33]** *[Student answer]* then it can't orient sideways because its thrust is pointing, like, into the wall.

Yep. Okay. Good. Yeah. There's actually a super simple example as well. I'm curious if anyone, yeah.

*[Student answer]* Translation.

Good. Yeah. So, just configuration A is horizontal, so just kind of flat, and then perfectly translating along the same Z height. So that's not physically feasible. And I guess the reason is that the propellers are producing thrust which is always perpendicular to the body of the drone. So there's no way to apply a force that is kind of purely horizontal if the drone is in this horizontal configuration. So there's no way to kind of have pure

**[3:18]** translation sideways. So yeah, I guess that's one challenge that we're going to start thinking about. How do we take into account dynamic feasibility when we're doing motion planning? And then the second challenge is that even if your plan happens to be feasible for the particular dynamics model that you have, that dynamics model may not be perfect. There's all sorts of aerodynamic effects that are pretty complicated to take into account that we're going to mostly ignore. Or there might be external disturbances. So, if you're flying outdoors, there might be a wind gust, and that is kind of unpredictable and it might take you off the planned motion that your drone is trying to follow. So, yeah, I guess how do we account for both of these factors? That's what

**[4:04]** we're going to focus on for the next few lectures. So, today's lecture and the next two lectures will focus on the first part of this, dynamic feasibility. And then beyond that we're going to start thinking about how we can use techniques from feedback control to address the errors and disturbances that your drone might encounter. Okay. So yeah, the goal for today actually is just to think about the dynamics, just how do we describe the dynamics of the drone. So there are entire courses devoted to dynamics. I know some of you took MAE 206, where we spend basically 23 lectures, and the 23rd lecture is a full derivation of equations of motion for the quadrotor. So obviously this is going to be a much quicker overview. The goal today is just to give you a sense for what the

**[4:51]** equations that describe the dynamics of a drone look like. So I'll do this on the blackboard and then I'll switch back. Yeah. So I'll start off with a simplified version of the quadrotor which we've already encountered. This is the planar quadrotor. And yeah, I guess just to remind you of the setup here, this is a version of the quadrotor that just lives in the plane. So just imagine that you're kind of looking at it from front on and all the motions are constrained to one plane. So the cartoon version of this system looks like this. So you have

**[5:38]** two propellers. So it's really a birotor rather than a quadrotor, but we're going to call it the planar quadrotor. And it's a three degree of freedom system. So there's an x and a y coordinate that describes, let's say, the center of mass of this planar quadrotor. And then there's also an orientation. So yeah, three DOFs, three independent ways that the system can move, three coordinates that we need to specify the configuration of the drone. And then there are also two control inputs, two things that the drone can directly impact. So these are the thrust forces. I'm going to call

**[6:24]** them F1 and F2. For now, just imagine that the drone has the ability to kind of directly control whatever thrust it wants to produce. I'll say a little bit more about exactly how that works. In practice, what's happening is that the thing that the drone directly controls is the propeller speed, and there's a nice relationship between the speed of the propeller and the thrust that gets produced. But I'll say more about that later in the lecture. So what I want to do is just kind of sketch out the dynamics of this system. So this three degree of freedom system, how do we describe its dynamics? How do we get its equations of motion?

**[7:14]** And yeah, I guess typically the way you do this is through Newton's laws. So Newton's second law in particular. So we can analyze the forces that are being applied on the center of mass of the system, or the total forces that are being applied on the system, so equate that to mass times the acceleration. And if we do that we get some equations. So along the x-axis we have x double dot, so the second time derivative of x, equals F1 plus F2 cosine theta

**[8:02]** divided by m. Okay, let me get the signs correct here. Sorry, this should be negative, negative F1 plus F2 and then sine theta. And then y double dot is F1 plus F2 cosine theta divided by m minus g. So these are two equations that give you kind of dynamics for the center of mass of the drone. And again, just a quick sketch of where these come from. So we're equating the mass of

**[8:49]** the drone, little m, times the acceleration, let's say in the x direction. So that's m times x double dot, that equals the total forces that are being applied along the x direction on the drone. And I guess maybe a quick sanity check. Let's say F1 and F2 are both positive, so the drone is applying some positive thrust force. We would expect, in that sort of configuration where theta is positive, we would expect the force to be in the negative direction. Maybe just convince yourself, if the arrows are pointing that way, theta is positive, the component of the forces along the x direction is in the negative direction. So that checks out. So if

**[9:34]** theta is some small, let's say positive constant, sine of theta is positive and we have a negative sign over here. And then yeah, I guess we can do some kind of basic sanity checking here as well. Let's say if theta is zero, then cosine of theta is one. So in that configuration the drone is purely horizontal. In the vertical direction the total thrust force should be F1 plus F2, and then we have a negative gravitational constant. Yeah. I guess questions on this, where it comes from or what it means? Okay. And then the last equation describes dynamics for the third

**[10:19]** degree of freedom, which is the orientation. And this one basically relates the second derivative of theta, so theta double dot, to the moment that's being applied on the drone, and then also the moment of inertia. So this I term is the moment of inertia of the drone, which is a physical parameter of the drone. It basically captures how the mass of the drone is spread out in its body. It's something that you can either kind of physically measure using

**[11:05]** some experiments, or if you have a CAD model of the drone you can kind of estimate the moment of inertia from the CAD model. So yeah, I guess these are the equations for the planar quadrotor. And yeah, maybe I can just label these 1A, 1B, 1C. And I might, just to kind of simplify things, define some quantities. So I'm going to define u1 to be the total thrust force. So just

**[11:53]** F1 plus F2, and I'll define u2 to be the total moment, the torque, which is F2 minus F1 multiplied by L. And I should have said L here is also a physical parameter, which is the length of the moment arm. So it's the distance from the center of mass to one of the propellers. So that's this constant over here. So this is the force times the distance, which is the moment. Okay. So yeah, if I define these, then I can rewrite these equations as x double dot equals negative u1

**[12:40]** sine theta over m. And then y double dot is positive u1 cosine theta divided by m minus g. And then finally theta double dot is u2, which is F2 minus F1 times L, over I. So I've just rewritten in a slightly more compact form these equations. Yeah, I guess questions on this. Okay, so yeah, I guess one thing to notice here is that these are second

**[13:26]** order differential equations, and in general whenever you're applying Newton's second law you're going to end up with second order differential equations because of the acceleration term. So acceleration is the second derivative of position. So you always get second order differential equations. Second order meaning that you have double time derivatives, like double dots, for x, y and theta. And one thing that's going to be very useful for the next few lectures is taking these second order differential equations and converting them to a first order form. So first order

**[14:12]** differential equations. Maybe just a quick show of hands. How many people know how to do this? Like, just taking these equations which are second order and converting them to a system of first order diffeqs? Okay, I guess everyone who's taken 206 should be familiar with this. But I'll go through the process as a reminder. Also, in principle you've seen it in some diffeq or calculus course, but I think it's useful to go through it and either kind of remind yourself of how it works or just kind of learn how to do it. It's relatively simple once you get the hang of it. It's something that we're going to do a few times in the course and it's just kind of useful to see it kind of worked out.

**[14:57]** So yeah, I guess the trick here, going from second to first order, is to introduce some auxiliary variables, just to define some new variables. So I'm going to define vx, so v subscript x. I'm going to define that to be x dot. And the equal sign with a little triangle on top is the definition. So I'm just giving this a new name, x dot. I'm just calling it vx. And then similarly vy is going to be y dot, and omega is going to be theta dot.

**[15:43]** So these are just definitions. But what I can do with this is I can write x double dot, or sorry, I can write vx dot, so the time derivative of vx, is then x double dot. So it's the time derivative of x dot, which is x double dot, which from that equation up there is negative u1 sine theta divided by m. And then similarly vy dot is, by this definition, the time

**[16:31]** derivative of y dot, which is y double dot, which from this equation is u1 cosine theta divided by m minus g. And then finally omega dot is theta double dot, which is just u2 over I. And yeah, basically what this allows us to do is think of these second order differential equations in first order form. So we now have

**[17:16]** six first order differential equations. So we have x dot is vx, y dot is vy, theta dot is omega, and then vx dot is this, vy dot is this, and omega dot is this. So it's six first order differential equations, like, combining these. And that's sort of a general thing. So if you start off with n second order differential equations, you go

**[18:01]** through this conversion process, you're always going to end up with 2n first order differential equations. And yeah, I guess maybe just to pause here, the trick was to just define these new variables. So giving the time derivatives x dot, y dot, theta dot, we just give them new names, like new variables associated with them. I call them vx, vy and omega. So that gives you three first order differential equations. You take the derivatives of those, and then from these equations which we got from Newton's second law you get the other three first order equations. Maybe I can just kind of write this down in a compact form. We can define

**[18:50]** the state of the system. The planar quadrotor over here, I'm going to call that x with a bar. And the bar notation here we're going to use to denote vectors in the course. So anything with a bar is going to be a vector quantity. So this state vector, which I'm going to call x bar, is the concatenation of six things. So it's x, y, theta, and then x dot, y dot, and theta dot.

**[19:38]** And then we can also define the control inputs over here. So the control input vector, I'll call that u bar, is going to be u1 and u2, where u1 again is the total thrust, which we defined up there, and u2 is the total moment. And yeah, basically what this notation allows us to do is we can write down equations like all of these equations over here, which are in first order form. We can kind of combine them. So x dot, the time

**[20:24]** derivative of the state vector, which is d by dt of x, is equal to... so x dot is vx, y dot is vy, theta dot is omega. So that's these three equations that I'm kind of writing over here. And then x dot, y dot, theta dot... actually I should have, maybe I'll just stick with my notation, I'll write this as vx, vy and omega

**[21:10]** and then vx dot we got from over here, so negative u1 sine theta divided by m. vy dot is u1 cosine theta over m minus g. And then omega dot, which is the same as theta double dot, is u2 over I. And yeah, I guess this is our system of first order differential equations. So first order because on the left hand side we have a single dot, not a double dot. And yeah, I guess on the right hand side we just have things that involve our state variables, our control inputs, and some physical constants like

**[21:58]** the inertia and the mass of the system. Yeah, I guess questions on this process of conversion. Does that ring a bell? Maybe raise your hand again if you've seen this before. Okay, most of you, good. Yeah, questions on the process? I'm happy to walk through it, because it is something that's just generally useful, not just in this course, but if you take control theory or other courses, it's good to be comfortable with this. Yeah, I'll pause for a minute. See if there are questions. Okay. So I guess the upshot of this is that we have our final equations of motion

**[22:44]** which end up looking like this. So if you look at these equations, on the left hand side we have the time derivative of the state. So that's x dot. On the right hand side we have some function of the state variables and the control input variables. And this form of equations is sort of a general form that any equations of motion will take. So the derivative of the state is some function of the state and control inputs. And basically what this allows us to do is we can

**[23:32]** predict what the system will do. So if at some initial time I tell you what the state of the system is, so I give you, for the planar quadrotor, I give you the configuration, which is the x, y and theta, I give you the initial speeds vx, vy and omega, and let's say I tell you what control inputs the drone is going to apply over some time horizon, then this differential equation, or the system of differential equations, allows you to predict exactly what the state will be at any given future point in time. And that's basically the starting point for doing motion planning in a way that accounts for the dynamics of the system, or to do feedback control to

**[24:17]** correct for errors. I haven't really given a thorough justification for why we're going from second order to first order. Again, if you've taken MAE 206 or some dynamics class, then you've gone through this process many times. You've plugged in these first order equations into MATLAB or Python to predict what your system will do. We'll have a more thorough justification for why this is useful in future lectures. For now just take it as given. It's something that will be useful when we think more about dynamics and control. Okay. Maybe just one more piece of terminology. So I said this is a state. This is

**[25:03]** the control input. These three variables are known as configuration variables. So we encountered this in the context of geometric motion planning when we were thinking about configuration space. For the planar quadrotor these three variables correspond to the three degrees of freedom of the planar quadrotor. And if I tell you these numbers, if I give you these scalars, then that perfectly defines the configuration that the planar quadrotor is in. So that's why we call these configuration variables. Okay. So yeah, I guess that's a quick kind of sketch of equations of motion

**[25:48]** for the planar quadrotor. I also want to sketch the equations for the full 3D quadrotor. I'm not going to go into detail here and write down the full equations. In the notes, which I posted on Canvas, I have a pointer to a reference that has the full equations written out. I guess the goal for this course is just to understand the general structure of equations of motion, like the fact that they're always going to have this form, x dot equals f of x, u. And then once you're given those equations, making use of them. I don't expect you to be able to derive equations of motion in this course. Again, if you're an MAE student you should be able to do it, but there's no

**[26:34]** expectation that you can in this course. So for this course we're just going to assume that maybe one of your MAE friends has derived equations of motion for you, we write them down in this general kind of first order form, and then we're just going to use them for motion planning or feedback control. Okay. So, yeah, let's start thinking a bit about the 3D quadrotor. So yeah, I guess the first question, as usual, is just how many degrees of freedom does this system have? So we discussed this in a previous lecture. So there's six degrees of freedom. So three degrees of freedom

**[27:19]** corresponding to the translation of the drone. So three coordinates that you need to specify the center of mass location. And then three degrees of freedom for the orientation of the drone. So yeah, what I want to do next is just give you a quick description of how we describe the orientation of the drone, which in this class we're going to do using Euler angles. Maybe another quick show of hands. How many of you have seen Euler angles before? Okay, a number of you. Okay, so yeah, hopefully this will be a recap for most people. Yeah, I guess the way Euler angles work is you

**[28:06]** attach some frame, so some directions, we'll write it like this. So we have three directions, let's say e x, e y and e z. These are our inertial directions. So some reference frame, let's say, attached to the room that you're working in. And then you have some frame that's attached to the body of the drone. So its origin is at the center of mass of the drone. So I'll call it O prime. And we have three directions

**[28:52]** here. So b x, which is sort of the forward direction, b y, which is the left direction, and then b z, which is up. And yeah, these axes are attached to the body of the drone. So for our drone, if you look carefully, there's a little kind of nub which denotes the forward direction. So that direction is going to be positive x. So forward is

**[29:39]** positive x. Left is positive y and then z is up. So that forms a right-handed coordinate system. That's the convention that we're going to use throughout for the course, so in particular for the lab that goes out tomorrow. That's the coordinate system that we're going to be using. So you'll have a chance to implement the RRT algorithm. For the RRT algorithm, x is going to be forward, y is going to be left, and then yeah, I guess z is just going to be up. Yeah, that's the convention that we'll follow. So yeah, let's say we've defined these axes that are attached to the body of the drone. These axes will move around as the drone moves and tilts. So the way Euler angles

**[30:24]** work, like the way we define orientations, is a basically three-step process. So the first step is you rotate... actually there's a zero step, which is like, align the body frame with the inertial frame.

**[31:13]** So just start off with the drone kind of aligned with the inertial axes. So b x is e x, b y is e y, b z is e z. And then the first step is to rotate the body frame, which I'm going to call B. So yeah, the body frame is B. So rotate B about e x with some angle, which I'm going to call phi. So this angle is called the roll angle. So maybe just going back to the drone over here. So again, forward

**[32:01]** is the positive x direction. So when we apply rotations we always apply them with the right hand rule. So you point the thumb along that direction and then you rotate, kind of, clockwise. So the first step here is to do the rotation about the positive x direction. So that's this angle over here. So that's step one. And then step two is to rotate about e y by an angle which I'm going to call theta. And this will be the pitch.

**[32:50]** And then the third step is to rotate B about e z, the z inertial direction, by another angle which I'm going to call psi. So this is going to be yaw. And yeah, maybe I can just visualize this again. So again, if you want to describe some arbitrary orientation that the drone is in, you first start off with the drone being aligned to the inertial axes, you then rotate about the positive x direction. So that's roll. Then you rotate about the positive y direction. So that's sort of

**[33:37]** the left inertial direction. If we again apply the right hand rule, positive pitch by this convention is kind of pitching down. And then the last step is rotate about the e z direction, again right hand rule, so we go this way. Yeah, I guess does that make sense? Questions on the steps? Yeah, question.

*[Student question]*

Yeah, of course. Yeah, so forward is positive x. So that's this direction over here. So the first step is rotate about that axis by some angle phi. So that's this rotation. And then the second one is rotate, again using the right hand rule, about e y. e y is

**[34:24]** the left sort of inertial axis, which is this way. So again, right hand rule means you go this way. So that's positive theta. And then the third direction is you rotate about positive e z, which is the vertical axis in the room. So that's going to be this way. And yeah, I guess the key result behind Euler angles is that any arbitrary orientation of the drone, like, no matter what sort of random configuration your drone is in, you can always describe that orientation using these three numbers. So whatever configuration of the drone, or orientation of the drone, you give me, I can give you three numbers, phi, theta, psi, such that if I go through this sequence of rotations, then I

**[35:10]** will get to the arbitrary orientation that you specified, and we can do this for any rotation. These numbers are not necessarily unique. So there might be two sets of phi, theta, psi that describe the same physical orientation. That's not something we're going to bother with in this course. There are more sophisticated ways of describing orientations using quaternions, for example. Yeah, I guess for this course we'll just keep it simple, use Euler angles. And yeah, this is the process by which we're going to describe orientations for the drone. Maybe just one quick note. What I've described over here is what's known as the space 1-2-3, or maybe x-y-z,

**[36:02]** convention. It turns out that there are many, many conventions that you could use. The name here comes from the fact that we're doing the rotations about the inertial axes, so e x, e y, e z. So that's the space part. There's a whole different set of conventions which are body conventions, meaning that you always rotate about the new, sort of, intermediate axes that the body frame is in. So when you do the first rotation you get some new b x, b y, b z, and then you rotate about one of those directions,

**[36:47]** you get another new frame, and then you rotate about one of those new directions. So those are called, like, body something-something-something conventions. We're not going to use them in this class, just to keep things simple. We're going to stick to the space 1-2-3 convention. Even within the space conventions or the body conventions, there's multiple choices that you have. Here we're choosing to do e x followed by e y followed by e z. You could do the opposite. You could do e z followed by e y followed by e x. Or you could do sort of *[Ed: unclear — "31213"]*. There's many permutations. Some of them are not valid. Like if I of course do 1-1-1, that's a sort of useless convention. But there's a

**[37:34]** bunch of non-trivial conventions that are all kind of equally valid. And depending on the particular domain that you happen to be working in, whether it's aerospace or something else, people like different conventions just for purely historical and maybe convenience reasons. But again, as I mentioned, we're going to just kind of forget about all the different conventions. For the purpose of this course, we're just going to stick to this particular Euler angle convention, of space, meaning that we do the rotations about the inertial axes, 1-2-3, meaning that we first do the rotation about x, then the rotation about y, and then the rotation about z. Okay, yeah, questions? Let me pause here and see if there are questions. I guess if you haven't seen Euler angles, or if you have. Yeah, go ahead.

**[38:20]** *[Student question]* Are there advantages to using body fixed frames, in the sense that it enables you to define it relative to your controller inputs, because your forces are also, like, your engines are defined...

So there are some benefits, particularly on the sensing side. It might be sort of easier to make some measurements in the body frame. But yeah, you can go back and forth. If I give you one convention and you want to do the conversion to another convention, you can do that conversion. But yeah, I guess in practice using multiple conventions causes a lot of headache and confusion. Yeah, I remember in grad school I was trying to get a model for a fixed wing airplane, and I wasted about, like, three months one summer because I was using some particular convention

**[39:06]** that I thought the motion capture system was giving me. It turned out the motion capture system was giving me some other convention and I didn't realize it, and yeah, I knew to look for it and I still made the mistake. And yeah, it's just like a super common error, thinking that you're using one convention and then somehow ending up using equations for the other convention. Just for convenience purposes here, we're just going to use this one particular convention. In some sense the simplest one, doing the rotations about the inertial frame, and just 1-2-3. Yep. But there are good reasons, and also bad reasons I guess, to use other conventions. Yeah. Other questions? Okay, cool. So, yeah, I guess that's how we describe orientations for our 3D

**[39:52]** drone. So that gives us a reason for why we have six degrees of freedom. So three coordinates to specify the translational location of the drone, so the center of mass of the drone, and then these three coordinates, the Euler angles, to describe the orientation of the drone. All right. So with that we can write down the state of the 3D

**[40:38]** quadrotor. Maybe just a quick check: how many dimensions will the state vector for the 3D quadrotor have? So we defined the state for the planar quadrotor up there. Go ahead, in the front.

*[Student answer]* 12.

Yeah. Maybe just give a quick explanation.

*[Student answer]* Because there's six degrees of freedom, we're going to put the velocity.

Perfect. Yeah. So when you apply Newton's second law, you're going to end up with six second order differential equations, corresponding to each of the degrees of

**[41:23]** freedom, six degrees of freedom. When we go through this conversion from second order to first order, you're always going to double the number of equations you end up with. So six second order differential equations is going to mean 12 first order differential equations. So that's the state of the quadrotor, or that's the dimensionality of the state. And yeah, I guess the state vector itself, you have some flexibility in the way you define it. The typical definition is x, y, z, so the center of mass location, say COM, center of mass, and then phi, theta, psi, which are the Euler angles, according to whatever convention you picked, which again will be the space 1-2-3 convention for this course.

**[42:11]** And then you can have the sort of speed terms, like the time derivative terms. So x dot, maybe I'll, I'll, I'll stick to that same notation. So v x, v y, v z. So these are x dot, y dot, and z dot. And then something to do with the time derivatives of the Euler angles. So we could, we could choose these last three

**[42:59]** variables in the state to be phi dot, theta dot, psi dot. That's a perfectly valid definition of the state. In practice it turns out that it's a little bit more convenient to work with p, q and r, which define the angular velocity of the drone. Yeah, they sort of have to do with how quickly the drone's orientation is changing along these different axes, e x and so on, or the body axes. Using this definition

**[43:47]** instead of phi dot, theta dot, psi dot just makes the equations a little bit more compact and easier to work with. But you can go back and forth. So if I give you phi dot, theta dot, psi dot, so the time derivatives of the angles, and I give you the angles, then you can compute p, q and r, and then similarly you can basically go from p, q and r and the other angles to phi dot, theta dot, psi dot. So in theory you can switch back and forth between, maybe I'll just write it over here, you can switch back and forth between the Euler angle rates, so phi dot, theta dot, psi dot, and p, q and r, which is the angular velocity vector.

**[44:37]** Okay. So yeah, this is the state. So 12 dimensions, as expected. And then we also have the control input vector. So the control inputs, the things that the drone directly controls, are the thrust forces for each of the propellers. So these are F1,

**[45:22]** F2, F3, F4. So each of these is a scalar, just the amount of thrust that each of the four propellers is producing. It turns out again, just for some sort of convenience reasons, it's useful to define the control input in a slightly different way. So u is usually defined as F total, the total thrust, and then three moments, M1, M2, M3. So that F total is just the summation of the four thrust forces,

**[46:12]** F1 plus F2 plus F3 plus F4. And then M1, M2, M3, these are the moments, so the torques produced about each axis. So the moment about the b x direction, the moment about the b y direction, and then the moment about the b z direction, which you can compute from F1, F2, F3, F4 and also the geometry of the drone. Yeah, I'm sort of just going through things at a relatively high level here. My main goal is to just emphasize that at the end, once you derive the equations of motion,

**[46:57]** you go through this process of converting from second order to first order, you're again going to end up with equations that have this general form that we saw for the planar quadrotor, which I'll just write here. So you'll get equations of motion which are x dot equals some function of x and u. And again, I'm not going through writing down the full explicit equations for the 3D

**[47:43]** quadrotor. They're a little bit messy. They're kind of long. But what I want to just convey for the purpose of this course is you go through the derivation with Newton's second law and you're just going to get equations that have this general form. Right, so the time derivative of your state, defined in this way, in that way, is some function of the state and the control input. And this differential equation, or the system of first order differential equations, allows you to predict exactly what the state of the drone will be at any future time, given the initial state and the control inputs that your drone is going to apply. Yeah, I guess questions on any of this? Go ahead.

*[Student question]* Is M3 a function of the forces, or is

**[48:30]** it more of a function of, like, drag on the...

Good. Okay, so that was actually going to be the very next thing I wanted to talk about. So I mentioned right at the beginning that there's some relationship between forces, like these thrust forces, and what the drone actually controls. So what's actually being controlled is not directly the force. You're applying some current on the motor, and that controls the rotational speed of each propeller. It turns out there's a nice relationship between the rotational speed and the thrust, and also the moment that you're referring to. So I'm going to just quickly sketch that out. So this is often referred to as a motor model

**[49:16]** in the context of drone dynamics. And the nice relationship is that the thrust force on any motor, so i here is indexing the four motors, the thrust force is equal to some constant times omega i squared. So i here is 1, 2, 3, 4, so four propellers. F i is the thrust from propeller i,

**[50:03]** and then omega i is the rotational speed, squared rotational speed, of the propeller. And then this thing is called the thrust coefficient. So this thrust coefficient k f has to do basically with the geometry of the propeller. So you could imagine if you have a large propeller, the thrust coefficient might be larger, or depending on exactly what the pitch

**[50:49]** of the blades looks like, that determines what this constant is. But this is something that we have to typically measure empirically. You could have some kind of computational fluid dynamics model of the propeller and its geometry and try to figure out what this is, but in practice it's much more convenient to just empirically measure what this is for your particular drone. Maybe thoughts on how you would measure it. So let's say I gave you this drone and we want to measure this thrust coefficient. That's something that, actually, Kian, who's sitting at the back, we had to redo this because we had new drones this year. So we had to do this experiment to figure out what's the thrust coefficient, which is something that we'll use in later assignments.

**[51:35]** Yeah, I guess thoughts on how you might measure this thrust coefficient for a particular drone?

*[Student answer]* Like some experiments we could do.

Yep. Go ahead.

*[Student answer]* Yeah. I guess how would you record the thrust from the propeller? You could compare that to, like, gravity and see how fast the drone moves.

You could do that. So that's reasonable. I guess you would need some motion capture system or some way to estimate the position of the drone, which might get noisy, but that's a perfectly reasonable idea. I guess other thoughts.

*[Student answer]* You just set it at steady state with, like, weights.

You could put different weights

**[52:20]** underneath. Then you have to get a bunch of weights and kind of tie it and get it to steady state. Also reasonable, but just a bunch of work. We want to be as lazy as possible. Go ahead. Yeah.

*[Student answer]* Could you just tie it to a scale and...

Yeah, you could tie it to a scale and just measure the forces. Yeah, I guess what we did for this course is just use a weighing scale and flip the drone so that it's pressing down on the weighing scale, and you can directly measure the thrust just from a digital scale. There's one complication here, which is that if you flip it and you place it on the weighing scale, there's a prop wash effect. So the propellers are blowing air onto the weighing scale, that air is coming back and kind

**[53:06]** of creating lift for the drone. So you'll actually get incorrect measurements if you just directly place it on the weighing scale. So what you need to do is raise it up high, like on one of those chemistry stand things, and that way there's no prop wash, propeller wash effect. So yeah, that's an experiment you can do. So just flip it, put it on a weighing scale. On the x-axis, measure omega i squared. On the y-axis, measure the thrust. Yeah, I guess take into account the fact that there are four motors, so there's four times the thrust that's being produced total. And then just sweep through a bunch of values on the x-axis. You'll get a nice neat curve, or neat line, and the slope of that line is the thrust

**[53:52]** coefficient. Okay, so going back to, yeah, I guess the question that was asked about the moment, yeah, maybe I'll pose this as another question. So far we've only talked about the thrust force that the propellers are... Oh, sorry. Question. Go ahead. I'm sorry.

*[Student question]* This requires us to assume that all the motors are basically identical, right?

Yes, which is not going to be perfect. And this model, by the way, itself is not perfect. It's just an aggregate kind of aerodynamics model, but it's good enough for a lot of the basic things that you might want to do with a drone. Yep. Okay. So I guess a question for you to think about is, how does the drone... so we said that the drone cannot translate horizontally, there's no way for the drone to apply a force in the kind of

**[54:38]** purely horizontal direction. But it is possible for the drone to yaw in place, just change the orientation about the z-axis. I guess any thoughts on how this is possible? Like, how is it possible for the drone to just kind of go like this? Go ahead. Yeah.

*[Student answer]* You can have the rotors spinning in opposite directions.

Yeah.

*[Student answer]* And if you slow down the rotors that are spinning in a specific direction, then you have higher drag force. That's...

Yeah, that's exactly right. So I think it's easiest to visualize this with a kind of top view of the drone.

**[55:31]** So if you look at the drone from the top, it has this shape. These are the propellers. So adjacent motors or propellers actually spin in opposite directions. So this one spins clockwise, this one spins counterclockwise, CCW, this one will spin clockwise, and then this one will spin counterclockwise. So any adjacent pair of propellers, if you look at the drone spinning, these will be spinning in opposite

**[56:16]** directions. And basically what happens is that there's an aerodynamic drag. So this comes from Newton's third law. So the drone is applying some moment on the air, the air is applying a moment in the opposite direction. So there's an aerodynamic drag due to the spinning of the propeller. So each of these propellers is producing some aerodynamic drag. And then if you basically control the speeds of the propellers, you can create a drag. Let's say you want the drone to spin clockwise. Then you increase these two motors, you decrease these ones, and then that's going to cause your drone to go in one direction.

**[57:04]** And if you do the opposite then it's going to yaw in the opposite direction. And there's a similar relationship here. So the aerodynamic drag, I'll call it M i aero, is equal to some other coefficient, this is called the moment coefficient, times again omega i squared, where omega i is the same as before, it's the rotational speed of a propeller. So maybe your hand... okay, so there's a question about, yeah, if you haven't thought about this before, it's a little bit counterintuitive. Like, if one of my

**[57:51]** propellers is spinning clockwise, the other spinning counterclockwise, why isn't one of them producing negative thrust? That's what you might expect. Go ahead. Yeah.

*[Student answer]* You could change the pitch.

Yeah, exactly. So if you look at the drones, I guess you'll have a chance in the next assignment, the pitch, so the way the blades are oriented, is flipped. So if your propellers are spinning this way or that way, you make sure that the pitch, like the way the rotors are angled, the blades are angled, flips accordingly. So you're always producing positive thrust. So you're not doing some kind of weird thing by producing negative thrust. Okay, questions on this.

**[58:37]** All right, so yeah, I think that's mostly what I had in terms of the dynamics of the drone. So, understanding the motor model, understanding the state, the control input, the fact that you get equations like this. If you want to see the equations written out, again, I have a pointer to a reference in the notes, and there's a bit more discussion about how to get these equations in the notes as well. What I want to do, I think we have about 15 minutes or so, I want to say a little bit about the next lab and some of the logistics. So it's going to go out tomorrow. It'll be due the Wednesday after. Okay. So I mentioned this in the very first lecture, we have two lab spaces that we were able to get this year. So I

**[59:25]** always cap the course based on how much lab space we're able to acquire in any given year. This year 72 students total, like 60 in the 345 version, 12 in the grad version. One of the spaces is G109. This is in the G-wing, I mean, both are in the EQuad. This is in the G-wing of the EQuad, and this is what it looks like. There's two netted spaces, yeah, each space is sort of separated by this kind of middle netting, and there's a bunch of drones and other stuff in the space. So this is G109. And then we have a slightly smaller space in the F-wing. This is the SEAS Robotics lab. I guess a quick show of hands if you don't know where it is. Okay. It's like basically if you enter

**[1:00:11]** the EQuad, it's just on the left, there's a large robotics lab. Part of that space we're using for teaching this here. It's basically right by the EQuad cafe. Another kind of net zone, some space for seating for students. So the very first lab, which is going to be the one that goes out tomorrow, is to implement the RRT algorithm, which we discussed in the previous lecture, to plan a collision free trajectory for the drone. And we're going to make sort of all the assumptions that we've made so far for the RRT algorithm. We're going to assume that there's a map of the environment that's provided to the algorithm. Here we're going to use the sort of simplest possible

**[1:00:56]** mapping algorithm, which is *[Ed: unclear — "U"]*. So you're going to just measure where the obstacles are. There's a tape measure in the room. Just measure out where the obstacles are, measure the radius of the obstacles. That's going to be the map. Obviously we're going to have more sophisticated ways of mapping later on in the course, but for the purpose of this lab, just measure where they are. That defines what the environment looks like. Apply the RRT algorithm. That will give you some collision free path from the starting location, which is marked with an X, to the end box. Like, the goal is just to land anywhere in that final box. We're going to assume that the drone can follow whatever path the RRT algorithm came up with. So for this lab we're not going to think

**[1:01:42]** about the dynamics. We're just going to assume that the drone has a good enough built-in controller to follow whatever trajectory RRT came up with. And yeah, I guess this is what it should, oops, look like in practice. All right, I guess you can imagine what it looks like. Sorry. It takes off, avoids the obstacles, gets to the landing zone. And because we're using the RRT algorithm, it's not going to be optimal. So there's a bunch of kind of wacky stuff that it does in the middle. We're not going to try to optimize it. The goal is just to see it in practice and to just get some kind of familiarity working with the drone. Yeah, just kind of figuring out how to connect to it, how to control it, give it waypoints, and just see the RRT algorithm work in practice. Okay. So I guess when you show up at one of

**[1:02:28]** the lab spaces, there's four drones in G109 that are in the space. There's three drones in the SEAS Robotics lab. So yeah, you show up, you pick up one of them that's available. We've kept a bunch of spare parts, so propellers, extra motors, these prop guards, like propeller guards as well, which are new on this brushless drone, and then measuring tape in each space for creating this map of the environment, and then safety glasses as well. And yeah, I guess some logistics for using the different lab spaces. Because of the size of the course, it doesn't really make sense to have a lab hour. Like, we would not all, 72 of us, fit at

**[1:03:14]** any given time. So you can use the lab spaces anytime you want, so weekdays, weekends. Anyone who's completed at least the online safety training, which hopefully should be everyone at this point, can access the space. Ideally you've completed the in-person version as well, but sometimes there's just issues with scheduling. Maybe a quick show of hands if you've completed both the online and the in-person training. Okay, most of you. Okay, actually not as many as I would have thought. Maybe show of hands if you haven't completed the online portion. Okay. All right. I guess I see some people who haven't. So by tomorrow, please complete the online portion of the EHS training. That's required for using basically any lab space in the EQuad. So

**[1:04:02]** occupancy suggestions or guidelines. In the past, the very first time that I taught this course, this was back in 2019, we had a signup sheet. So each team would sign up before they showed up. We gave up on it within, like, two weeks, because what would happen is people would sign up, like, 5 minutes before showing up to the space and it was basically as good as not having a signup sheet. What we found to work well throughout the years is a much more organic way of organizing yourself. So you come to the space, there's going to be some other teams maybe that are in the space. Just take turns, test something out. Most likely it's not going to work well. Kind of go back out of the netted area, debug with your

**[1:04:48]** teammates, and then just take turns. Yeah, that turns out to work much better than some kind of signup sheet or something more organized. People are busy at different times, so it just kind of naturally works out. There's going to be some times where it's busy, but overall I think it's pretty good. We also have a thread that I created this morning on Ed Discussion. If there are issues with any particular drone, the drones are going to be numbered, just post on the thread and then use whatever other available drones there are in the space. That way you're not wasting any time. We'll look at the thread. Jon Prevost, who helps out with the course, is going to try to fix the drones. We have a bunch of replacement parts. Yeah, so let

**[1:05:33]** let's try to do this. Just be proactive. If there is an issue, just post on that thread so we know to fix it. The situation I want to avoid is there's a bunch of broken drones and then people show up to the lab and they're all broken and we don't know that they're broken, so we have no way to fix it. Yeah. Questions on any of these logistics? Okay. Yeah, last couple of things. So safety is obviously super important. The drones are pretty lightweight and the propellers are small and there are prop guards, so the chances of a severe injury are low, but it's still possible. I think the thing I worry about the most is, like, the propeller either breaks off, or somehow you're in the net, netted

**[1:06:19]** area, and the drone comes and hits your eye. That's the main thing. It's not, the propellers are not strong enough that they're going to physically injure you otherwise. It's mostly the eyes that I'm concerned about. We'll have a bunch of safety glasses in the space. If you feel like you need more, just let me know. We'll try to have enough, but if that's an issue, let me know. And then obviously stand outside the netted area. That's why we have the nets. When the drone is operating, don't stand inside with the drone. Just put the drone in, run your code, see it fly or crash, and then pick it up. And then also, yeah, I guess please treat the drones with care. So we're using it as a shared resource.

**[1:07:05]** So all the teams will be using the same seven or eight drones. There's a non-trivial operating cost for the course. These drones in particular, the new ones with the brushless motors, if you combine all the parts, like the drone itself, there's an optical flow camera, the propellers, the motors, there's an extra camera that we're going to add towards the end of the course, all of it per drone is about, like, 600 dollars. So if they break, it just takes some cost to try to replace these. And we bought entirely new drones, like a whole new fleet of drones, this year. In the past we've had some teams not be super careful with the drone. So last year we had two different teams

**[1:07:51]** who stepped on the drones and just crushed them. Please do not step on the drones. Yeah, just treat them with care, as if they're your own. It's going to make things much, much smoother in terms of just making sure that they're reliable throughout the semester and usable by everyone. Yeah, questions on the logistics? All right. Yeah, it should be fun. So I'll post an announcement tomorrow and I'll see you next time. Thanks.
