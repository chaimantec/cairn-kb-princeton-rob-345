---
title: Lecture 9 — Optical Flow (slide deck)
lecture: 9
slides: 21
source_pdf: https://www.dropbox.com/scl/fi/yjkah2nhv83fdbnf6ea5a/Lecture9_slides.pdf?rlkey=d83o8wcmk8oczkogd2tpuogq3&dl=0
numbering: PDF page N = Slide N for all 21 pages (1:1). Pages 1 and 2 print no number; their labels (1, 2) are inferred from position. Pages 3–21 print their own number.
images: 9 slides are rendered and shown under their headings (3, 4, 5, 6, 7, 8, 15, 17, 18). Not rendered — the title page (1); the course outline (2); the text-only slides 9, 10 and 14; slide 11, which holds only a URL; slide 12, a black video frame; slide 13, a news-article screenshot whose text is transcribed; slide 16, the photograph that slides 17 and 18 mark up; slide 19, a second frame of the video on slide 5; slide 20, slide 6's picture again; and slide 21, that picture faded behind a line of text. The notes' four drawings are rendered in the notes file.
figure_audit: An independent reader checked slides 3, 5, 6, 7, 8, 15, 17, 18 and 19 against the PDF with crops at 300–600 dpi. Nothing described is absent from the page; slides 3, 7 and 15 agree. Fixed: on slides 5 and 19 the road recedes to the upper left, not the upper right, and slide 19's vehicle count; on slide 6 the arrows of the white column and the dark panel, and a summary of the whole field; on slide 8 the right frame's arrows trail behind the discs; the position of slide 17's box and a line in slide 18's inset. The render of slide 6 was also checked in the parent.
---

# Lecture 9 — Optical Flow: slide-by-slide

Text and figures of the Princeton ROB 345/549 "Introduction to Robotics" Lecture 9 deck (title "Lecture 9: Optical Flow", speaker: Anirudha Majumdar), transcribed from the PDF. Cite these as "slide N", the printed number. Figures are described in prose since the KB is read as text. The deck is short and mostly questions and images: slide 3 asks how the drone localized itself in the RRT lab, slides 4–10 introduce optical flow with pictures and questions, slides 11–13 show animal examples, slide 14 hands over to the blackboard, slides 15–18 show the aperture problem and ask when Lucas-Kanade optical flow has trouble, and slides 19–21 close with a video frame and the topic of imperfect sensing. The derivations are not on the slides; the written lecture notes carry them.

## Slide numbers vs PDF pages

The numbering is one-to-one: "slide N" is PDF page N for all 21 pages, and the last printed number is 21. Slides 1 and 2 print no number in the corner, so their labels are inferred from position (title page and outline page); slides 3–21 print their own numbers.

Companion pages: [wiki page for this lecture](../../wiki/09-optical-flow.md) · [transcript](../transcripts/09-optical-flow.md) · [lecture notes](../notes/09-optical-flow.md)

## Contents

| Slides | Section |
| ------ | ------- |
| 1 | Title |
| 2 | Course outline: where "Localization, mapping" sits |
| 3 | Motivating question: how did the drone localize itself in the RRT lab? |
| 4–8 | Optical flow: the flow-deck drone, a video frame of flow on a motorway, a flow field from a drone, estimating speed (homework), the pixel-motion problem |
| 9–10 | What optical flow is: apparent motion, and its possible causes |
| 11–13 | Examples from animals: bird flight, the waggle dance |
| 14 | Blackboard derivations |
| 15 | Aperture problem |
| 16–18 | Lucas-Kanade optical flow: when does it have trouble? |
| 19 | Optical flow (video frame, repeated) |
| 20–21 | Sensing is imperfect |

---

## Slide 1 — Lecture 9: Optical Flow

Title page. Title in blue in a rounded light-grey box: "Lecture 9: Optical Flow". Below it, a faded wide photograph of a small quadrotor seen from the front: black propellers on the left and right arms, a circuit board in the centre carrying a vertical board with a camera and lens, red and black wires. Below: "Anirudha Majumdar", "ROB 345/549", and the Princeton University shield logo with the wordmark "PRINCETON UNIVERSITY". No slide number is printed (label inferred from position).

## Slide 2 — Course outline (Localization, mapping)

No title bar and no number printed (label inferred from position). Three rounded cards side by side. The middle card is in full colour and slightly darker grey; the other two are faded.

- Left card (faded), heading "Planning and control", a faded image of a car on a road with a drawn lane path; lines "Geometric planning", "Robot dynamics", "Planning with dynamics", "**Feedback control**" (bold, faded).
- Middle card, heading in blue "Localization, mapping". Below it a colour image of a forest path with a coloured point-cloud or voxel overlay (a small person walking on the path in the middle distance). Below, four lines in black: "Bayes filtering", "Kalman filters", "Particle filters", "SLAM".
- Right card (faded), heading "Robot learning", a faded image of a humanoid robot and a person in a kitchen; lines "Imitation learning", "Generative architectures", "Reinforcement learning", "World models".

## Slide 3 — Motivating question: localization in the RRT lab

![Slide 3 — Motivating question: localization in the RRT lab](../images/09-optical-flow/slide-3.png)

Grey title bar with no title text. Printed number 3.

In a rounded grey box: "In the RRT lab, how did the drone localize itself? (For applying a feedback controller to follow the path you specified)" (the word "localize" in blue). Below the box is a path-planning picture: four dark-red filled circles (obstacles) at different positions, a black dot labelled "Start" in blue at the lower left, a black dot labelled "Goal" in blue at the right, and a black dotted curve from Start to Goal that passes above the lower-left obstacle and below the two upper obstacles. The curve has no arrowhead. The remaining obstacle sits below the curve, near the middle.

## Slide 4 — Optical flow

![Slide 4 — Optical flow](../images/09-optical-flow/slide-4.jpg)

Title bar: "Optical flow" (blue). Printed number 4.

A photograph of a small quadrotor held in a hand, seen from below or above at an angle. The hand holds the central circuit board between thumb and fingers. The four arms are white and translucent with black patterned markings, each ending in a black motor with a pair of black propellers; the board has the text "bitcraze.se" at its top edge and "Flow" printed along its left edge, a small square camera sensor in the middle of the board, and a battery with red and black wires and a white connector below the board. No caption is printed.

## Slide 5 — Optical flow (video frame)

![Slide 5 — Optical flow (video frame)](../images/09-optical-flow/slide-5.jpg)

Title bar: "Optical flow" (blue). Printed number 5. Below the image, an underlined URL: https://www.youtube.com/watch?v=5rR_9YIcg_s

This is a single frame of a video whose URL is printed on the slide. Two panels side by side. Left panel: a mostly white image with a small colour wheel (a circle shaded in pastel hues, black outline) in the upper left corner, and a soft-edged blob in the middle: yellow-green on its left part, green on its right part, with a fainter pale-blue-green smear above it and faint pale blue patches at the left edge and lower left. Right panel: a camera view of a motorway seen from above, the road receding from the bottom of the picture towards the upper left (its far end about 40% of the way across), with trucks and cars on it, a blue road sign in the distance and buildings along the horizon. A grid of small green arrows is overlaid on the whole picture. The arrows are tiny and mostly dot-like over the roadside vegetation and sky, and longer, pointing upward in the image, over the two trucks in the foreground (one white truck and one dark truck) and over their shadows on the road.

In the lecture: the video is played while the lecturer explains it (≈4:03–5:33). The left panel plots the magnitude of the apparent motion, more green meaning a larger magnitude; the arrows on the right give its direction at each pixel as the cars pass by.

## Slide 6 — Which way is the drone's motion?

![Slide 6 — Which way is the drone's motion?](../images/09-optical-flow/slide-6.jpg)

Title bar: "Which way is the drone's motion?" (blue). Printed number 6.

A grayscale camera image of an indoor corridor shown as a plot with axes: the horizontal axis is labelled with ticks 0, 50, 100, 150, 200, 250, and the vertical axis with ticks 0, 50, 100, 150, 200, 250 running from 0 at the top to 250 at the bottom (image coordinates). Faint pink text in the top-left corner, partly hidden behind the "0" tick label and the plot border, begins "Sa…" and is not legible in full. The image shows a white wall on the left with a framed dark poster and a tall dark door-like panel in the lower middle, a tall white vertical column in the middle, and a corridor receding to the right with equipment in the distance. Large black letters on the floor of the corridor read downward "O", "X", "F", "O", "R" (the last letters partly visible) lying on the floor in the right half of the picture. Red arrows are drawn on a regular grid over the whole image. Their direction and length vary across the image:

- Left wall (x from about 0 to 100): arrows are short at mid-height (y about 90 to 130) and point right; lower down (y about 130 to 170) they point right and downward; in the lower left (y about 170 to 235) they are long, nearly horizontal and point right, some reaching about 70 pixels in length, with short up-and-right arrows between them at x about 25 to 50. Above y about 75, in the top left, the arrows point up and to the right and are long.
- Dark panel in the lower middle (x about 78 to 103, y about 160 to 250): a bundle of long arrows whose heads meet in a chevron near (88, 185), those from below pointing up and slightly right, and others from the upper left pointing down and to the right.
- White column (x about 105 to 125): arrows point down and to the right at y about 110 to 150, and up and to the right lower down, at y about 150 to 195.
- Right half (x about 130 to 240): arrows are mostly short. In the upper part (y about 30 to 70) they point right, slightly downward at the far right, and are longest near y about 30 at x about 180 to 230, where they point right and slightly up. At mid-height they point right, with longer ones pointing right and slightly up near the right edge (y about 130 to 150). A column of short arrows near x about 155 to 160, y about 100 to 150, points down. Around the floor letters (y about 160 to 230) they are very short or dot-like, with a few short ones pointing left near x about 130 to 150, and a few short ones at the far right (x about 225 to 235) pointing down or down and to the right.

Overall, most arrows point right or up and to the right. They are longest on the near wall at the left (the upper left, the lower left and the dark panel) and shortest down the corridor in the right half, many of them dot-like. There is no single point they radiate from; they converge on the region around x 95 to 135, y 160 to 195, at the dark panel and the foot of the white column, while the upper-left arrows point away from it.

The exact length and direction of individual arrows are only approximate in this description.

No answer to the question is printed on the slide.

In the lecture: the flow field is from a drone's forward-facing camera. After several guesses from the class, the answer given is that the drone is "mostly turning to the left": the apparent motion at these points is to the right, which is what turning towards the left produces (≈4:48–7:50).

## Slide 7 — Estimating speed (homework)

![Slide 7 — Estimating speed (homework)](../images/09-optical-flow/slide-7.png)

Title bar: "Estimating speed (homework)" (blue). Printed number 7.

A side-view diagram of a quadrotor above a ground plane. At the top, a grey horizontal bar (the body) with a short vertical post at each end, each post carrying a black horizontal propeller blade pair; a short grey stem drops from the middle of the bar to a white rectangle labelled "Pin-hole camera". To the left of the rectangle, a double-headed vertical arrow spanning the height of the rectangle is labelled "Focal length: f". To the right of the rectangle, a short black horizontal arrow pointing right is labelled "Speed: v". Below the rectangle, a double-headed vertical arrow runs from the bottom of the camera rectangle down to a long blue horizontal bar (the ground), labelled "Height: h".

In the lecture: this is the next homework, estimating the drone's velocity from a downward-facing pinhole camera's optical flow and the drone's height (≈7:50–8:36).

## Slide 8 — Optical flow

![Slide 8 — Optical flow](../images/09-optical-flow/slide-8.jpg)

Title bar: "Optical flow" (blue). Printed number 8.

Two white rectangular frames side by side, the left captioned "I(x,y,t)" and the right "I(x,y,t+1)". Each contains four coloured discs with a black arrow attached to each disc. Left frame: a blue disc at the upper left with an arrow pointing up and to the right; a red disc at the upper right with an arrow pointing down and to the right; a purple disc at the lower left with an arrow pointing right; a green disc at the lower middle with an arrow pointing straight up. Right frame: the same four discs in new positions relative to the frame, each with an arrow of the same direction that now trails behind the disc, its head ending at the disc (in the left frame each arrow starts at the disc and its head is beyond it). The blue disc is higher and further right than in the left frame, with its arrow pointing up and to the right. The red disc has moved down and to the right, with its arrow pointing down and to the right. The purple disc has moved to the right, with its arrow pointing right. The green disc has moved up, to about the same horizontal position, with its arrow pointing straight up. Below the frames, in large text: "Want to estimate pixel motion from image I(x,y,t) to image I(x,y,t+1)". At the lower left, in small grey text: "Credit: David Fouhey".

## Slide 9 — Optical flow

Title bar: "Optical flow" (blue). Printed number 9.

In a small rounded grey box: "Optical flow: *Apparent* motion of objects" ("Optical flow:" in blue, "Apparent" in italic blue, the rest black). Below: "Can you think of examples where:" followed by two numbered items: "1. There is no optical flow, but there is relative motion (between camera and environment)" and "2. There is no relative motion, but there is optical flow".

## Slide 10 — Apparent motion could be due to different factors

Grey title bar with no title text. Printed number 10.

In a rounded grey box: "Apparent motion could be due to different factors:" ("different factors" in blue), then three bullets: "Motion of object in camera's view", "Motion of camera itself", "Lighting changes".

## Slide 11 — Optical flow: bird flight (video link)

Title bar: "Optical flow: bird flight" (blue). Printed number 11. The slide body is empty white apart from one underlined URL in the middle: https://video.wyomingpbs.org/video/nova-mysteries-optic-flow/

The slide shows no video frame in the PDF: the area where a video would sit is blank white. The URL is the only content.

In the lecture: the bird-flight video is played in class (≈12:26–15:32); its narration is in the transcript.

## Slide 12 — The waggle dance (video frame)

Title bar: "The waggle dance" (blue). Printed number 12. Below the picture, an underlined URL: https://www.youtube.com/watch?v=LU_KD1enR3Q

This is a single frame of a video whose URL is printed on the slide. The frame is a black rectangle filling the picture area, with the "Smithsonian CHANNEL" logo (white text and a yellow sun-burst symbol) in the lower right corner. No other content is visible in the frame.

In the lecture: the waggle-dance video is played in class (≈15:32–18:46); its narration is in the transcript. The PDF holds only a black frame, not what was shown.

## Slide 13 — The waggle dance (news article)

Title bar: "The waggle dance" (blue). Printed number 13. Below the picture, an underlined URL: https://www.nature.com/news/2001/010531/full/

A screenshot of a Nature news web page. At the top is the dark-red "nature" banner ("International weekly journal of science", a "Login" link, and tabs "nature news home", "news archive", "specials", "opinion", "features", "news blog", "nature journal"). The article reads: "Published online 31 May 2001 | Nature | doi:10.1038/news010531-9", a red "News" tag, the headline "Bees go with the flow", the standfirst "Honeybees tell their hivemates how much scenery they should fly past, not how far they should fly." and the byline "John Whitfield". Body text, as legible on the slide:

"A bee measures how far it has travelled by how much scenery it has flown past. By jamming this navigation system, researchers have shown that bees incorporate this measurement into the dances that alert their nestmates to food."

"Harald Esch, of the University of Notre Dame, Indiana, and colleagues deceived bees into thinking they had flown a greater distance to reach a food source than they actually had. These bees then communicated their false impressions to their hivemates, who took off in search of nectar, only to overshoot the mark." (with a superscript footnote mark 1)

"Bees measure distance using optic flow. This is the amount that an image appears to move as the position of the observer moves. Nearby things produce more optic flow than distant objects. This is why the scenery close to a moving train seems to zip by more quickly than the distant landscape, and why driving a ground-hugging vehicle such as a go-kart gives such an impression of speed."

A photograph embedded in the article shows a red flower with a bee on it against a blue sky, with other red flowers on stems behind; its caption reads "Bees' dances tell their hivemates how much scenery to fly past on the way to food." The left sidebar lists "comments on this story", "Stories by subject" ("Cell and molecular biology"), "This article elsewhere" ("Blogs linking to this article", "Add to Digg", "Add to Facebook", "Add to Newsvine", "Add to Del.icio.us", "Add to Twitter"); the right sidebar holds "Naturejobs" (two identical job listings "Deputy Director of Nanoscopy Center in SLST, ShanghaiTech", "More science jobs", "Post a job") and "Resources" ("Send to a Friend", "Reprints & Permissions", "RSS Feeds").

## Slide 14 — Switch to blackboard for derivations

Grey title bar with no title text. Printed number 14. In the middle of the slide, in black: "Switch to blackboard for derivations". Nothing else is on the slide; the derivations are not in the deck.

## Slide 15 — Aperture Problem

![Slide 15 — Aperture Problem](../images/09-optical-flow/slide-15.jpg)

Title bar: "Aperture Problem" (blue). Printed number 15. Below the picture: "Source: https://www.opticalillusion.net/optical-illusions/the-barber-pole-illusion/" (the URL underlined).

A dark-red rectangular picture containing two illustrations, a single frame of an animation from the source page. On the left is a barber pole: a white sphere on top of a cylinder wrapped in diagonal blue, white and red stripes, with grey octagonal bands at its top and base. The stripes run from the lower left to the upper right (rising to the right). No arrows are drawn on the barber pole. On the right are two pale-green shapes with black diagonal stripes, all running from the lower left up to the upper right at the same slope as the barber pole's stripes: an ellipse (lower left of the pair), and a large "L"-shaped band (a horizontal bar along the top whose right end turns down into a vertical bar along the right side, the elbow at the upper right). The L shape is open to the lower left, with the ellipse sitting inside the open corner. No arrows are drawn on any shape. No caption besides the source line is printed.

In the lecture: this is a video, played in class (≈42:21–45:26). The class watched the stripes in the top bar of the L-shaped band (seen moving left), its vertical bar (seen moving up) and the ellipse; once the whole picture was in view, most saw the stripes in the top bar moving to the top left.

## Slide 16 — Lucas-Kanade optical flow

Title bar: "Lucas-Kanade optical flow" (blue). Printed number 16. Text below the title bar: "When does Lucas-Kanade optical flow have trouble?"

A colour photograph of a large stone building with a central tower topped by a cupola, ivy on its walls and many windows, seen across a lawn from the end of a paved path that runs towards the building's door; two other paths cross in the foreground, with a round plaque set in the pavement at the bottom. Bare winter trees stand in front of the building and fill the sky. No box, arrow or other mark is drawn on the picture.

## Slide 17 — Lucas-Kanade optical flow: low texture

![Slide 17 — Lucas-Kanade optical flow: low texture](../images/09-optical-flow/slide-17.jpg)

Title bar: "Lucas-Kanade optical flow" (blue). Printed number 17. Text: "When does Lucas-Kanade optical flow have trouble?" followed in blue by "Low texture".

The same photograph as slide 16. A small red-outlined square (hollow) is drawn on the sky region between the bare trees, to the upper right of the building's roof and right of the tower (about four-fifths of the way across the photo and a third of the way down). A large blue arrow points from lower right to upper left, its head ending beside the red square. At the arrow's tail, at the right of the slide, is a black-outlined white square: a magnified view of the red square's content, which is almost uniformly white with one or two very faint grey specks and no visible texture.

## Slide 18 — Lucas-Kanade optical flow: edge

![Slide 18 — Lucas-Kanade optical flow: edge](../images/09-optical-flow/slide-18.jpg)

Title bar: "Lucas-Kanade optical flow" (blue). Printed number 18. Text: "When does Lucas-Kanade optical flow have trouble?" followed in blue "Edge".

The same photograph as slide 16. A small red-outlined square (hollow) is drawn at the top of the photo, just to the right of the tower's finial, on a bare tree trunk against the white sky. A large blue arrow points from the lower right to the upper left, its head ending beside the red square. At the arrow's tail, at the right of the slide, is a magnified, blurry crop with no border: it is mostly white, with a dark blue-grey diagonal band in its lower left that forms a straight edge running from the upper left to the lower right (the tree trunk's edge against the white sky) and a faint grey line above it, left of centre, slanting from upper right to lower left.

## Slide 19 — Optical flow (video frame, repeated)

Title bar: "Optical flow" (blue). Printed number 19. Below the image, an underlined URL: https://www.youtube.com/watch?v=5rR_9YIcg_s

This is a single frame of the video whose URL is also printed on slide 5, at a different moment from the frame on slide 5. Two panels side by side, as on slide 5. Left panel: a mostly white image with the small colour wheel (pastel hues, black outline) in the upper left corner and a soft-edged coloured smear: pale green and pale blue-green above, yellow-green in the middle and green in the lower middle, extending to the bottom edge of the panel; a faint pale blue patch at the left edge and a faint pink patch in the lower left. Right panel: the same motorway camera view, the road again receding towards the upper left, now with more vehicles: two white trucks or vans in the upper middle, one white van lower down, one white van cut off by the bottom edge, and a few small cars farther up the road. A grid of small green arrows covers the picture; over the road and the foreground vehicles the arrows are long and point upward in the image, and over roadside vegetation and sky they are tiny.

In the lecture: shown again near the end, with the remark that the estimates jitter and that one big arrow is inconsistent with its neighbours (≈1:06:04).

## Slide 20 — Sensing is imperfect

Title bar: "Sensing is imperfect" (blue). Printed number 20.

The same picture as slide 6: the grayscale corridor image with axis ticks 0 to 250 on both axes and red arrows on a grid, arrows identical to those on slide 6 (see that slide's description). No other text.

## Slide 21 — Sensing is imperfect: next lecture

Title bar: "Sensing is imperfect" (blue). Printed number 21.

The same corridor picture as slide 20, faded to a pale wash, with a rounded grey box across its middle reading "Next lecture: how can we account for imperfect sensing?" ("Next lecture:" in blue, the rest black).
