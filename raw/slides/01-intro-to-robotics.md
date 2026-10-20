---
title: Lecture 1 — Introduction to Robotics (slide deck)
lecture: 1
slides: 57
source_pdf: https://www.dropbox.com/scl/fi/oltefsy9ihq4efgxvtyn9/Lecture1.pdf?rlkey=4kc7a1r2pja5z932phyakcq73&dl=0
numbering: PDF page 1 = Slide 1 (title, unnumbered); PDF pages 2–56 = Slides 3–57 (slide = page + 1; printed "2" does not exist); PDF page 57 = Slide 58 (unnumbered, inferred).
figure_audit: An independent reader checked six figure-heavy slides (6, 8, 15, 32, 33, 53) against the PDF. Four agreed; slide 8's gripper lettering, called illegible, reads "ROBOTIQ", and slide 15's Waymo/Lyft crossing and two Uber values were corrected. Renders of slides 15 and 32 were also checked against this file.
images: 24 slides are rendered and shown under their headings (6–8, 10, 11, 15, 20–22, 25–30, 32, 33, 36–41, 52). Not rendered — the title page and section dividers (1, 5, 34, 44); text-only slides; slide 9, an embedded video that does not render in the PDF; the news-article screenshots 12–14, 16 and 17, whose content is their headline text, transcribed below; slide 35, a road sign bearing the one word "Uncertainty"; slides 42 and 58, which repeat the images of slides 40 and 33; slides 45 and 46, photographs of course staff; and slide 53, a screenshot of text transcribed in full.
---

# Lecture 1 — Introduction to Robotics: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 1 deck (speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Diagrams, photographs and video stills are described in prose since the KB is read as text.

## Slide numbers vs PDF pages

The printed number "2" does not exist in the PDF (a slide hidden in the source deck). After the title page, every page's printed number is its PDF page number + 1: "slide N" is PDF page N−1 for N ≥ 3. Slide 1 is PDF page 1 (the title page prints no number; label inferred). Slides 6, 7, 8, 33 and 39 print no number, and their labels are inferred from position. Slide 5 prints its "5" inside the slide body rather than in the corner, so a text-layer scan misses it, but the number is printed. Slide 58 is PDF page 57 (prints no number; inferred). It shows the same topic map as slides 33 and 39 with the "Planning and control" card highlighted and "Geometric planning" in bold.

Companion pages: [wiki page for this lecture](../../wiki/01-intro-to-robotics.md) · [transcript](../transcripts/01-intro-to-robotics.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 3–4 | Agenda; about the instructor |
| 5–11 | A snapshot of robotics today: IRoM Lab, Gemini Robotics, manipulation demos, humanoids, Waymo |
| 12–17 | From labs to the real world: news on robotaxis, drone delivery, home humanoids, warehouse automation |
| 18 | Course goal |
| 19–31 | What is a robot? Pre-history of robotics, definitions, "Is this a robot?" examples |
| 32 | Anatomy of a robotic system (sense-think-act) |
| 33 | Topic map: planning and control, localization and mapping, robot learning |
| 34–39 | What makes robotics hard? Uncertainty |
| 40–43 | Course plan: hardware implementation (Crazyflie drones, teams, lab safety) |
| 44–57 | Course logistics: TAs, hardware support, prerequisites, grading, office hours, policies, generative AI, references, Gradescope/Ed, ROB 345 vs 549 |
| 58 | Topic map repeated with "Planning and control" highlighted |

---

## Slide 1 — Lecture 1: Introduction to Robotics

Title page. Title in blue in a rounded box: "Lecture 1: Introduction to Robotics". Below it, a faded (washed-out) wide photograph of a small quadrotor drone seen from the front: two black propellers on left and right arms, a circuit board in the centre with a small camera module on a vertical board, red and black wires. Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed.

## Slide 3 — Agenda for today

Three lines in a rounded box (blue words are highlighted):

- Motivation and introduction to course content
- Overview of technical topics
- Course logistics

## Slide 4 — A little bit about me

- Faculty in MAE and Associated Faculty in COS
- Co-Director, Princeton Robotics Initiative
- 20% Research Scientist at Google DeepMind (Princeton & NYC)
- My first name is difficult to pronounce!
  - I usually go by "Ani"

Right side: the "Princeton Robotics" logo (Princeton shield, orange "ROBOTICS" wordmark, a pink/orange/yellow linked-chain emblem) and the "Google DeepMind" logo.

## Slide 5 — A snapshot of robotics today

Section divider: the single text "A snapshot of robotics today" in blue in a grey rounded box. (The printed number "5" is visible at the bottom right of this page.)

## Slide 6 — IRoM Lab: generalist robots that are helpful, safe, and trustworthy

![Slide 6 — IRoM Lab: generalist robots that are helpful, safe, and trustworthy](../images/01-intro-to-robotics/slide-6.jpg)

No printed title and no printed number (label inferred). A collage of five panels around a centre white box. In the centre box: the "IRoM Lab" logo (a small drone icon over the "M", text "IRoM Lab") and "Intelligent Robot Motion Lab". A white banner across the middle reads "Generalist robots that are helpful, safe, and trustworthy" (the last three words in dark red).

- Top left: a chat-bubble panel with a small user avatar and the text "Hey robot, could you put the bowl on the small counter in the microwave?"; the rest of the panel is empty white.
- Top middle: a still of a kitchen/cafe area with grey drawers, a tiled green-and-white wall with posted papers, a microwave and a coffee machine; a white mobile robot with a round head is at the right. A speaker icon is at the bottom left of the panel. Appears to be a frame from an embedded video.
- Top right: a white robot arm with a gripper over a small wooden tray holding a cylinder, beside a second white arm and cameras on orange cables, on a grey table; a "1x" label at top left; partly cut-off text "OPPO" at bottom left of the panel (first letters hidden behind the centre box). Appears to be a video frame.
- Bottom left: an indoor flight arena with netting and white walls, with tall coloured cylinders (blue, green, red, yellow); a small black winged drone is flying between the columns.
- Bottom right: a white robot arm above a grey fabric storage drawer box on a tiled wooden floor, with a computer mouse on the floor in front of the box.

## Slide 7 — Google DeepMind: Gemini Robotics

![Slide 7 — Google DeepMind: Gemini Robotics](../images/01-intro-to-robotics/slide-7.jpg)

No printed title and no printed number (label inferred). Google DeepMind logo at the top. A full-width still of a robotic hand with silver and gold-coloured finger joints (a glowing ring light on the back of the hand at left) touching a green-grey desk lamp with brass fittings and a small brass toggle switch. A pill-shaped label at top right reads "Autonomous 1x". Caption at the bottom: "https://deepmind.google/models/gemini-robotics/". Appears to be a frame from an embedded video.

## Slide 8 — Four robot-manipulation demos (GEN-1.5 and others)

![Slide 8 — Four robot-manipulation demos (GEN-1.5 and others)](../images/01-intro-to-robotics/slide-8.jpg)

No printed title and no printed number (label inferred). Four equal panels in a 2×2 grid under a grey header bar.

- Top left: a white domestic kitchen with a black robot on a stand with two arms holding black grippers and cameras; a "π" logo is in the top right corner of the panel.
- Top right: close-up of a robot arm with a green status light and orange/black gripper fingers bending a white book or box lid on a dark carpet; large white text overlaid: "GEN-1.5".
- Bottom left: a lab bench with a black mat holding test tubes in a rack, a blue tube rack, a syringe, a pipette, an orange container, a blue bowl of caps and small cups; black robot grippers reach over it, one gripper body printed "ROBOTIQ" with a logo mark.
- Bottom right: a white robot with the text "DYNA" on its base, arm cutting celery on a wooden board, with a tray of chopped celery and several similar robots and people blurred in the background.

## Slide 9 — Video slide (black frame)

No printed title. A large black rectangle (an embedded video that did not render; nothing visible in it). Caption: "www.youtube.com/watch?v=EtRXay2kqtc". Printed number 9.

## Slide 10 — Beijing Humanoid Robot Games

![Slide 10 — Beijing Humanoid Robot Games](../images/01-intro-to-robotics/slide-10.jpg)

No printed title. A still of a blue running track with lanes and numbered start blocks "4", "3", "2", "1"; four humanoid biped robots stand on the line: two white ones with blue head lights and chest numbers (left) and two red ones (right). Spectators' hands holding phones are in the foreground. Overlaid caption text: "Beijing's Humanoid Robot Games have come to a close, where the robots showed how capable they are at running - but not at stopping...". Appears to be a news video frame. Printed number 10.

## Slide 11 — Waymo self-driving car (CNBC video)

![Slide 11 — Waymo self-driving car (CNBC video)](../images/01-intro-to-robotics/slide-11.jpg)

No printed title. A still of a white Waymo robotaxi (the word "WAYMO" on the roof sensor housing, a roof lidar dome, California-style licence plate) driving down a sunny residential street lined with palm trees, parked cars and buildings on a hillside. "CNBC" logo at top right. Caption: "https://youtu.be/RQaW3iMue3M?si=bV-8qWo015mLgFhT". Appears to be a frame from an embedded video. Printed number 11.

## Slide 12 — From labs to the real world

Screenshot of a CNBC web article page. Top bar: CNBC logo, search box "Search quotes, news & videos", "WATCHLIST"; menu: "MARKETS, BUSINESS, INVESTING, TECH, POLITICS & POLICY, VIDEO, INVESTING CLUB, PRO, LIVESTREAM". Headline: "Waymo to launch driverless rides in Germany in 2027, entering third market outside U.S." Dateline: "PUBLISHED TUE, AUG 25 2026·1:07 PM EDT | UPDATED TUE, AUG 25 2026·5:47 PM EDT". Byline: "Samantha Subin @SAMANTHA_SUBIN" with a small author avatar and share icons (Facebook, X, LinkedIn, email).

## Slide 13 — From labs to the real world (build: adds Amazon article)

Same slide as 12, with the CNBC screenshot faded to a ghost, and a new article overlaid: headline "Amazon's Prime Air autonomous drones to reach 500 US cities", byline "Ryan Daws, August 20, 2026". Below it, a photo (cropped at the bottom) of a white-bodied drone tilted on its side with a blue wing/tail and the Amazon smile logo, on a dark background.

Adds: the Amazon Prime Air article.

## Slide 14 — From labs to the real world (build: adds Wall Street Journal article)

Same as 13, with the earlier two articles faded and overlapping. New article overlaid: "THE WALL STREET JOURNAL." masthead; "TECHNOLOGY • PERSONAL TECHNOLOGY • JOANNA STERN"; headline "I Tried the Robot That's Coming to Live With You. It's Still Part Human."; subhead "1X's Neo wants to be your housekeeper. First, it needs to be controlled by a human in your home. Cool with you?"

Adds: the WSJ article about the 1X Neo humanoid.

## Slide 15 — From labs to the real world (Waymo market share chart)

![Slide 15 — From labs to the real world (Waymo market share chart)](../images/01-intro-to-robotics/slide-15.jpg)

Left: a product-style side-view photo of a white Waymo robotaxi SUV (roof sensor pod with a "W" logo, "WAYMO" on the door) on a white background.

Right: line chart titled "Estimated Market Share (Gross Bookings) – 8/23-4/25, San Francisco Operating Zone, per YipitData". Y axis: "% of San Francisco Gross Bookings", ticks 0%, 25%, 50%, 75%. X axis ticks: 8/23, 12/23, 4/24, 8/24, 12/24, 4/25. Legend: Waymo (blue), Uber (black), Lyft (magenta). Three series (values approximate, read from the plot):

- Waymo (blue): rises steadily from 0% at 8/23; about 7% at 12/23; about 9% at 4/24; about 14-15% at 8/24; about 22% around 11/24 then a dip to about 20% at 12/24; about 27% at 4/25.
- Uber (black): about 66% at 8/23 falling to about 61% shortly after; about 63% at 12/23; peak of about 66% near 3/24; about 57% at 8/24; about 55–56% at 12/24; about 54.5% at 4/25.
- Lyft (magenta): about 34% at 8/23 (peak about 35%); about 30% at 12/23; about 27% at 4/24; about 28% at 8/24; about 24% at 12/24; about 18.5% at 4/25. The Waymo and Lyft lines first meet at about 22% around 11/24; Lyft is back above at 12/24 (about 24% against 20%), and Waymo crosses above for good around 2/25.

## Slide 16 — From labs to the real world (Futurism article)

Screenshot of a web article: headline "Uber Drivers Say Waymo Robotaxis Are Driving Down Their Pay"; subhead "And their union is fighting back."; byline "By Frank Landymore / Published Aug 30, 2026 3:02 PM EDT / Add Futurism" (with a Google "G" icon). Below: a wide banner photo, tinted red, of a row of about nine white robotaxi cars parked nose-in, seen from above.

## Slide 17 — From labs to the real world (New York Times article)

Screenshot of a New York Times page (masthead "The New York Times", menu and search icons, "Account"). Background photo: a warehouse robotics cell with a large yellow industrial robot arm with a grey corrugated hose, blue plastic bins on a conveyor, and a blue panel in the background. Overlaid white italic headline: "Amazon Plans to Replace More Than Half a Million Jobs With Robots"; subhead: "Internal documents show the company that changed how people shop has a far-reaching plan to automate 75 percent of its operations."

## Slide 18 — Course goal

No printed title. Boxed: "**Course goal:** understand technical underpinnings of modern robotic systems"

- Explore connections: machine learning, control, optimization, vision, …
- Broader impacts: privacy, ethics, alignment with human values, …

## Slide 19 — What is a robot?

Boxed question: "What is a robot?"
Below: "Side note: asking this question is a good way to start a fight at a robotics conference"

## Slide 20 — A brief (pre-)history of robotics

![Slide 20 — A brief (pre-)history of robotics](../images/01-intro-to-robotics/slide-20.jpg)

List (dates in grey); the first eight items sit in a grey rounded box:

- Greek mythology (Talos): ~1000BC
- Early automata: ~300BC - 100AD
- Banu Musa brothers: ~800AD
- Ismail al Jazari: ~1100s
- Leonardo da Vinci: ~1500s
- Descartes: ~1600s
- More complex automata: ~1700s
- Charles Babbage: ~1800s
- Karel Capek: 1920
- Unimate (George Devol, Joe Engelberger): ~1950s

Right: two images. Top: a sepia sketch of a mechanical device with jointed arms, pulleys, a cylinder and gears (an old automaton-like machine; no caption). Bottom: an old coloured engraving of a seated figure in a turban and fur-trimmed robe over a cabinet with a chessboard, with the cabinet open to show a person and gears inside (looks like the Mechanical Turk chess automaton; no caption printed).

## Slide 21 — A brief (pre-)history of robotics (build: highlights Karel Capek)

![Slide 21 — A brief (pre-)history of robotics (build: highlights Karel Capek)](../images/01-intro-to-robotics/slide-21.jpg)

Same list as slide 20; the box highlight moves to "Karel Capek: 1920" (blue text, grey rounded box). Right: a yellow, black and red theatre poster showing a stylised black-and-red robot figure with a gear/blade form; text on the poster: "FEDERAL THEATRE", "USA WORK WPA", "MARIONETTE THEATRE PRESENTS", "RUR", "REMO BUFANO DIRECTOR". Caption (blue): "Rossum's Universal Robots"; then "This is where the word "robot" comes from. In Czech: "work", "labor"".

Adds: the RUR poster and the caption; removes the two images of slide 20.

## Slide 22 — A brief (pre-)history of robotics (build: highlights Unimate)

![Slide 22 — A brief (pre-)history of robotics (build: highlights Unimate)](../images/01-intro-to-robotics/slide-22.jpg)

Same list as slide 20 (the grey box now surrounds only "Unimate (George Devol, Joe Engelberger): ~1950s", in blue). Right: a black-and-white television-style still of two men in dark suits standing on a studio stage (one holds a microphone) next to a large industrial robot arm on a base whose long thin arm points toward them. No caption printed.

Adds: the Unimate still; removes the RUR poster.

## Slide 23 — What is a robot? (definition)

Boxed sentence: "An embodied agent that can be programmed to perform physical tasks" (blue highlights on "embodied agent", "programmed", "physical tasks").

## Slide 24 — What is a robot? (other definitions)

"Other reasonable definitions:"

- A machine — especially one programmable by a computer — capable of carrying out a complex series of actions *automatically* [Wikipedia/dictionary definition]
- A reprogrammable, multifunctional manipulator designed to move material, parts, tools or specialized devices through variable programmed motions for the performance of a variety of tasks [Robotics Industries Association]
- An *autonomous* machine capable of sensing its environment, carrying out computations to make decisions, and performing actions in the real world [https://robots.ieee.org/learn/]

## Slide 25 — What is a robot? (Is this a robot? Atlas)

![Slide 25 — What is a robot? (Is this a robot? Atlas)](../images/01-intro-to-robotics/slide-25.jpg)

"Ultimately, all proposed definitions have some issues" / "Is this a robot?"

Photo: a silver-grey humanoid robot with a round head and a dark face visor walking in a lab/warehouse-like space, carrying a dark moulded plastic part toward a tall metal cart with numbered fabric slots (numbers 01–30 visible). Caption: "Boston Dynamics: Atlas".

## Slide 26 — What is a robot? (Is this a robot? small drone)

![Slide 26 — What is a robot? (Is this a robot? small drone)](../images/01-intro-to-robotics/slide-26.jpg)

Same two lines. Photo: a small four-propeller quadrotor on a grey table, with a camera module on a vertical board, an upright black antenna and an orange-brown circuit board (same vehicle as in the title-page image). No caption.

## Slide 27 — What is a robot? (Is this a robot? dishwasher)

![Slide 27 — What is a robot? (Is this a robot? dishwasher)](../images/01-intro-to-robotics/slide-27.jpg)

Same two lines. Photo: an open dishwasher in a kitchen with wooden cabinets, both racks loaded with plates, cups and dishes. No caption.

## Slide 28 — What is a robot? (Is this a robot? automatic door)

![Slide 28 — What is a robot? (Is this a robot? automatic door)](../images/01-intro-to-robotics/slide-28.jpg)

Same two lines. Photo: a glass automatic sliding door at a building entrance, with a sensor housing above the door and small stickers on the glass. No caption.

## Slide 29 — What is a robot? (Is this a robot? smart speaker)

![Slide 29 — What is a robot? (Is this a robot? smart speaker)](../images/01-intro-to-robotics/slide-29.jpg)

Same two lines. Product photo: a white cylindrical smart speaker with a slanted top showing four small coloured lights and a grey fabric base, on a white background (resembles a Google Home speaker; no caption printed).

## Slide 30 — What is a robot? (Is this a robot? Da Vinci)

![Slide 30 — What is a robot? (Is this a robot? Da Vinci)](../images/01-intro-to-robotics/slide-30.jpg)

Same two lines. Photo: a surgical robot system: a surgeon in blue scrubs seated at a console with head against the viewer, a standing person in a gown and cap touching a monitor showing a surgical view (a yellow circle on the screen), and a multi-arm patient-side cart over a blue-draped operating table. Caption: "Intuitive Surgical, Da Vinci".

## Slide 31 — What is a robot? (references)

- Ultimately, all proposed definitions have some issues
- See these articles for a discussion of issues with definitions:
  - https://robotsguide.com/learn/what-is-a-robot

## Slide 32 — Anatomy of a robotic system

![Slide 32 — Anatomy of a robotic system](../images/01-intro-to-robotics/slide-32.jpg)

Diagram: a photo of a small four-propeller quadrotor (Crazyflie-style, with a battery and stacked boards on top) at the centre, surrounded by three thick black curved arrows forming a clockwise loop. Three labels with grey arrows pointing at the drone: "Actuators" (top, arrow pointing at a propeller/motor), "Sensors (Inertial Measurement Unit, Optical Flow camera)" (bottom right, arrow pointing at the underside of the board), and "Computation" (bottom left, arrow pointing at the central board). The loop arrows run Actuators → (right side, down) → Sensors → (bottom, leftwards) → Computation → (left side, up) → Actuators. Bold blue caption at the bottom: ""Sense-Think-Act"".

## Slide 33 — Planning and control / Localization, mapping / Robot learning (topic map)

![Slide 33 — Planning and control / Localization, mapping / Robot learning (topic map)](../images/01-intro-to-robotics/slide-33.jpg)

No printed title and no printed number (label inferred). Three side-by-side rounded cards, each with a blue heading, a thumbnail and a list:

- **Planning and control**. Thumbnail: a blue wireframe-style rendering of two cars on a road with a light-blue curved planned path ahead of the near car, with bollards at the right. List: Geometric planning; Robot dynamics; Feedback control; Planning with dynamics.
- **Localization, mapping**. Thumbnail: a forest scene with a path and a person walking, overlaid with a colourful (green/purple/yellow) voxel-grid mesh covering the ground and trees (a 3D map). List: Bayes filtering; Kalman filters; Particle filters; SLAM.
- **Robot learning**. Thumbnail: a humanoid robot with a dark visor head and metal arms standing in a kitchen with a toaster in front of it, next to a man wearing a VR headset making hand gestures. List: Imitation learning; Generative architectures; Reinforcement learning; World models.

## Slide 34 — What makes robotics hard?

Section divider: "What makes robotics hard?" in blue in a grey rounded box.

## Slide 35 — What makes robotics hard? (Uncertainty)

Photo of a green road sign against a blue sky with clouds, with the single word "Uncertainty" in white letters on the sign, mounted on two wooden posts.

## Slide 36 — What makes robotics hard? (drone delivery news clip)

![Slide 36 — What makes robotics hard? (drone delivery news clip)](../images/01-intro-to-robotics/slide-36.jpg)

A tall portrait-format still of a news clip on a white slide: mostly blue sky with the corner of a roof or dark object at top left, hedges and a backyard with an outdoor seating area and a small swimming pool at the bottom. Overlaid text: "Lindsey Austen via Storyful"; the "abc7" logo with "Aug. 17, 2026"; caption "Amazon drone delivery drops woman's package into swimming pool". Appears to be a frame from an embedded video.

## Slide 37 — What makes robotics hard? (humanoid weightlifting)

![Slide 37 — What makes robotics hard? (humanoid weightlifting)](../images/01-intro-to-robotics/slide-37.jpg)

A still of a large indoor arena with spectators in tiered stands and a blue floor, with officials and robot handlers in black and white shirts standing around a blue square platform. On the platform, a white humanoid robot with black patches bends over a loaded barbell mid-lift. Two seated people in black clothes in the foreground at right; judges' tables at left; other humanoid robots with handlers standing at right. Logo "news.com.au" at top right; sponsor banners (partly legible, Chinese text) around the arena. Appears to be a video frame; no caption.

## Slide 38 — What makes robotics hard? (dashcam clip)

![Slide 38 — What makes robotics hard? (dashcam clip)](../images/01-intro-to-robotics/slide-38.jpg)

A tall portrait-format dashcam still looking forward over a car bonnet at a two-lane road with double yellow centre lines; a black sedan ahead at right, a truck with a "COSTCO" sign further ahead, utility poles and trees. Overlays: the "abc7" logo, faint text "Anonymous via Storyful" (a date beneath it is illegible), and at the bottom a GPS/speed stamp reading approximately "48:17 N37.37321 W121.99599 000mph" (the beginning of the timestamp is cut off). Appears to be a frame from an embedded news video; no caption states what the clip shows.

## Slide 39 — Uncertainty in each topic area (topic map)

![Slide 39 — Uncertainty in each topic area (topic map)](../images/01-intro-to-robotics/slide-39.jpg)

No printed title and no printed number (label inferred). Same three cards and thumbnails as slide 33, each now with a blue "Uncertainty in:" list in place of the topic list:

- **Planning and control** — Uncertainty in: Dynamics of robot; Dynamics of world; Initial state of robot; …
- **Localization, mapping** — Uncertainty in: State of robot; Geometry of world; Semantics of environment; …
- **Robot learning** — Uncertainty in: Data quality; Human intent; Rewards from world; …

Adds relative to slide 33: the "Uncertainty in:" lists replace the topic lists.

## Slide 40 — Course plan: hardware implementation

![Slide 40 — Course plan: hardware implementation](../images/01-intro-to-robotics/slide-40.jpg)

Hardware implementation:

- Best way to appreciate challenges
- Nothing like seeing things work (or not) in practice!

Crazyflie 2.1 brushless drone

- Open source platform, small, light-weight, ideal for testing

Photo: a small quadrotor with green propellers, black propeller guards around each rotor, and stacked circuit boards and a battery at the centre, on a white background. Callout box in the lower right: "**New drones** this year!" (the words "New drones" in green bold, "this year!" in light green).

## Slide 41 — Course plan: hardware implementation (goal)

![Slide 41 — Course plan: hardware implementation (goal)](../images/01-intro-to-robotics/slide-41.jpg)

Boxed text: "Goal: make the drone navigate autonomously" (blue highlights on "Goal:" and "navigate autonomously").

Photo: a small indoor drone-flight arena corner with a net on the walls, artificial-grass floor marked with white tape lines (a grid with an X mark), tall blue foam-padded poles (obstacles) on bases and several orange poles stacked in the back corner.

## Slide 42 — Course plan: hardware implementation (teams)

"Teams for hardware implementation portions of assignments"

- Please form teams of **4** by next Wed **[Sept. 9th] and email course staff**
  - Can use Ed Discussion to facilitate team formation
  - Might be a good idea to have students from multiple majors in a team

Photo: the green-propeller quadrotor with black propeller guards, on a white background (same as slide 40).

## Slide 43 — Course plan: hardware implementation (logistics)

"Logistics for hardware implementation"

- Netted spaces in G109 (EQuad) and SEAS Robotics Lab
- General lab-safety training (if you haven't completed this)
  - https://ehs.princeton.edu/training
  - Online and in-person components (through EHS)
  - Needed to access lab

## Slide 44 — Other logistics

Section divider: "Other logistics" in blue in a grey rounded box.

## Slide 45 — Course logistics: TAs

"TAs for the course"

- Asher Hancock
- Jutang Gao
- Kian Orr
- Yanbo Xu

"Emails are listed in the syllabus"

Right: a 2×2 grid of four portrait photographs, one per TA. The photos carry no printed name labels, so the names are not matched to individual photos here. Layout: top left a colour headshot against green foliage; top right a black-and-white full-torso portrait against a plain light background; bottom left a colour portrait in front of trees; bottom right a colour candid photo of a person indoors holding an electric guitar and a bundle of blue wrapping or flowers.

## Slide 46 — Course logistics: hardware

Photo: a workshop/lab with tool cabinets, a stepladder, a small CNC mill (printed text on it includes a web address, partly legible) and a white machine on a shelf, with a large black multirotor (octocopter-style) drone on a workbench at right; a person in a light-blue shirt stands at the left beside the bench. Caption: "Jon Prevost (MAE)".

## Slide 47 — Course prerequisites

Boxed list:

- Multivariable calculus (e.g., MAT 201 or 203)
- Linear algebra (e.g., MAT 202 or 204)
- Basic probability (e.g., ORF 309)
- Basic differential equations (e.g., MAE 305)
- Some programming experience (e.g., COS 126)
  - We will be using Python

## Slide 48 — Course logistics: grading

Boxed list:

- Problem Sets: 40% (assigned: Wed, due: Wed midnight)
  - Mixture of theory, coding, and hardware implementation
- Midterm Exam (in-person): 30%
  - See syllabus for tentative date
- Final Project: 30%

## Slide 49 — Course logistics: OHs

Boxed text: "Office hours: 5 hours / week (finalized in the next 1-2 days)"

## Slide 50 — Course logistics: policies

Boxed text:

- Collaboration is permitted (encouraged) on problem sets. But, you must turn in your own write-up, code, etc. (except for hardware portions).
- Late policy: 10% deduction for every day of lateness (won't accept if more than week late).
- In-person midterm exam.
- Regular attendance is strongly encouraged!

## Slide 51 — Course logistics: Generative AI

- Generative AI has huge potential for education
- Main tension: be proficient with AI while also having the discipline to learn fundamentals deeply
- Individual response to AI: two extremes

(Text only; the next slide continues the point.)

## Slide 52 — Course logistics: Generative AI (build: adds spectrum)

![Slide 52 — Course logistics: Generative AI (build: adds spectrum)](../images/01-intro-to-robotics/slide-52.png)

Same three lines as slide 51, plus a grey box with a double-headed horizontal arrow. Above the left end: "Luddism"; above the right end: "Nihilism"; a large "?" above the middle of the arrow. Below the left end: ""Never use AI for anything!""; below the right end: ""AGI is inevitable. No need to learn anything!"".

Adds: the Luddism-to-Nihilism spectrum.

## Slide 53 — A personal case study

Screenshot of a chat with Claude (the "Claude" logo with an orange starburst at top left). Three message blocks, transcribed:

1. Assistant reply, heading **"Why M1-as-teacher is specifically wrong for this case"**: "M1-as-teacher earns its keep when the teacher's training corpus is unavailable. Here it's the opposite: the robotics dataset is precisely the data you have. Distilling action competence out of M1 means round-tripping labeled demonstrations through a lossy model copy, when you could just train on the demonstrations. You'd be paying distillation's bandwidth penalty to recover something you already hold in supervised form."
2. User message (grey bubble at right): "Hmm, the intuition I have is coming from this line of work: https://arxiv.org/abs/2510.18874 / OPD should lead to knowledge preservation (while fine-tuning for some target capabilities)."
3. Assistant reply, heading **"Why this makes your proposal the strong version"**: "Given that finding, the question for the VLA becomes: how do I train action generation on-policy? Two options."

## Slide 54 — Course logistics: Generative AI (permitted uses)

Boxed text: "The following 4 uses are *permitted* (see syllabus):"

- Analyze past assignments
- Explain technical concepts
- Ask about Python syntax
- Any use you want for hardware-based assignments and final project

"No other uses"

## Slide 55 — Course logistics: references

"No required textbooks"; "References:"

- D. Gammelli, J. Lorenzetti, K. Luo, G. Zardini, M. Pavone, *Principles of Robot Autonomy* — https://arxiv.org/pdf/2608.03496
- S. Lavalle, *Planning Algorithms* — http://planning.cs.uiuc.edu/
- S. Thrun, W. Burgard, and D. Fox, *Probabilistic Robotics* — https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf

## Slide 56 — Other logistics

- Gradescope (through Canvas)
- Ed Discussion (through Canvas)

## Slide 57 — ROB 345 vs. ROB 549

Boxed text:

- ROB 549 is the "grad track"
- There are 12/12 students enrolled
- ROB 549 students will have some extra problems on assignments (these will be clearly marked)

## Slide 58 — Planning and control (topic map, first topic highlighted)

No printed title and no printed number (label inferred). Same three-card topic map as slides 33 and 39, with the "Planning and control" card highlighted (full colour) and the other two cards ("Localization, mapping" and "Robot learning") faded to a light ghost. Within the first card the list is Geometric planning (bold), Robot dynamics, Feedback control, Planning with dynamics. The other cards' lists (Bayes filtering, Kalman filters, Particle filters, SLAM; Imitation learning, Generative architectures, Reinforcement learning, World models) are faded. The thumbnails are the same as on slide 33.

Relative to slide 33: highlights the first topic area and its first item, "Geometric planning" (apparently marking where the course starts).
