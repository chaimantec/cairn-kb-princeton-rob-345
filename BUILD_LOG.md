# Build log — Princeton ROB 345 knowledge base

The record of how this knowledge base was built and checked, one section per
finished run, in order: each deck's licence notices and lecture pointers, each
transcript's edit and checks, what each figure audit found, each deck's printed
slips, and which slides were rendered as images and why the others were not.
A run's section is its `TODO.md` checklist, moved here verbatim once the run
was committed and pushed. It holds no unchecked box: open work lives only in
`TODO.md`.

It is a build record, **not needed to answer questions**: every fact a learner
needs is on the wiki page, slide file or transcript it concerns. The rules
every build follows, and each lesson in general form, are in
[`AGENTS.md`](AGENTS.md).

## Index

| Lecture | Runs |
| --- | --- |
| 1 Intro to Robotics | Run 1 |
| 2 Discrete Motion Planning | Run 2 |
| 3 Rapidly Exploring Randomized Trees (RRTs) | Run 3 |
| 4 Quadrotor Dynamics | Run 4 |
| 5 Differential Flatness | Run 5 |
| 6 Trajectory Optimization | Run 6 |
| 7 Stability and PD Control | Run 7 |
| 8 The Linear Quadratic Regulator (LQR) | Run 8 |
| 9 Optical Flow | Run 9 |
| 10 Nondeterministic Filter | Run 10 |

## Runs

_Each finished run's section is appended below._

## Run 1 — Lecture 1 (Intro to Robotics), 2026-10-20

Scope: lecture 1 of 9 in the catalog manifest (the course site lists 24). Slide
images opted in; PDFs link-only. Commit as chaimantec <nantapon@chaimantec.com>.

### Transcripts
- [x] 01 Lecture 1: Intro to Robotics — video cMhFAq53v1c — verbatim captions in raw/transcripts/original/
- [x] 01 copy-edit (Sonnet): 74/74 timestamps identical, no number lost, no ratio outlier; 41 restorations, 10 [Ed: unclear]; proper nouns grepped against the slides

### Crawl
- [x] Fetch course site index: https://irom-lab.princeton.edu/intro-to-robotics/ (single page; all materials on Dropbox)
- [x] Download Lecture1.pdf (Dropbox, 75MB, 57 pages) into raw/pdfs/ (gitignored)
- [x] Write sources.md (hand-written by lecture; the generated table filed course decks under "papers")

### Slides
- [x] Slide number map: printed 2 absent (hidden slide), pages 2–56 print page+1; pages 1, 4–7, 32, 38, 57 print none
- [x] raw/slides/01-intro-to-robotics.md (Sonnet), --verify clean (57 headings)
- [x] Figure audit of six figure-heavy pages (Sonnet): 4 agree; fixed slide 8 (ROBOTIQ legible) and slide 15 (Waymo/Lyft crossing, two Uber values)

### Wiki
- [x] wiki/01-intro-to-robotics.md
- [x] Topic pages: course-map, course-logistics, crazyflie, sense-think-act, uncertainty
- [x] INDEX.md table of contents

### Images
- [x] raw/images/01-intro-to-robotics/ — 24 slides rendered (3.3MB), embedded in the slide file, the lecture page and four topic pages; 16 hand-written captions
- [x] INDEX.md — the chat's image rules; AGENTS.md — the Images conventions and table row; BUILD_LOG.md — what was rendered and why (below); LICENSE.md — attribution

### Publish
- [x] kb.json — coverage, materials.method, provenance caveats
- [x] BUILD_LOG.md — the lecture's record: notices, audit findings, printed slips, transcript edits (below)
- [x] verify_kb.py clean (all hard checks, 5 formulas in chat and on github.com), and its review section read
- [x] Commit and push — https://github.com/chaimantec/cairn-kb-princeton-rob-345
- [x] PATCH kbUrl onto the catalog entry (re-fetched: set)
- [x] Move this run's finished sections to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 1 record

- **Deck.** `Lecture1.pdf` from Dropbox, 57 pages, 75MB. No licence or copyright notice on any
  page, and none on the course site. Third-party images carry no credit lines; LICENSE.md
  attributes them from visible logos, captions and URLs.
- **Numbering.** Printed "2" is absent (a hidden slide), so pages 2–56 print page+1 and the last
  page, which prints nothing, is labelled 58. `slide_number_map.py` reported page 4 as unnumbered.
  The "5" is printed inside the slide body, not in the corner, which the text-layer scan misses.
  The label was right either way.
- **Transcription.** Sonnet, in about 2 minutes; `--verify` was clean first time. The agent flagged
  slides 15, 6, 8, 32, 33/39/58 and 53 for a second reader.
- **Figure audit.** Sonnet, on slides 6, 8, 15, 32, 33 and 53. Four agreed, with no invented
  elements. Slide 8's gripper lettering, called "illegible", reads "ROBOTIQ" at 600 dpi (the
  "illegible" claim was false again), and the file had also omitted a pipette and a bowl of caps.
  On slide 15, two Uber values were off by about 1 point, and the sentence "Waymo crosses above
  Lyft around 11-12/24" hid a double crossing. Checking the render of slide 15 in the parent
  caught that too. The render of slide 32 agreed.
- **Transcript edit.** Sonnet, 74/74 timestamps identical, no number lost, no word-ratio outlier
  (10,770 → 9,022 words). It made 41 restorations and left 10 `[Ed: unclear]` marks. All 3
  "gained" numbers are slide references inside `[Ed:]` notes. Parent adjudication: Sunnyvale
  confirmed by the slide 38 GPS stamp; the "skilled" startup at 3:14 left unclear (not printed on
  the slides); "x equals f of x" left spoken in the transcript and written as $\dot{x} = f(x)$ in
  the wiki with a note. The agent tagged student turns `*[Student answer]*`; the header says so.
- **Verbatim captions not committed.** The course has no licence, so the CS336 precedent applies.
  `raw/transcripts/original/` is gitignored; the first local commit was amended before any push
  so the captions never entered history.
- **Images rendered (24):** 6, 7, 8, 10, 11, 15, 20, 21, 22, 25–30, 32, 33, 36–41, 52. **Figure-bearing
  slides not rendered:** 1 (title), 9 (embedded video, black in the PDF), 12–14, 16 and 17 (news
  screenshots whose content is the headline, transcribed), 35 (road sign reading "Uncertainty"),
  42 and 58 (repeat the images of 40 and 33), 45 (TA photo grid), 46 (staff member in the lab),
  53 (chat screenshot, transcribed in full). The raster test flagged 39 pages, and its extra
  flags (3, 4, 23 and others) are logos and backgrounds.
- **sources.md** is hand-written. `inventory_to_sources.py` put the course's own Dropbox decks
  under "papers ... usually all-rights-reserved".
- **Wiki.** `$` in prose (20,000 dollars; 18 billion dollars) would open a math span, so amounts
  are written out in words. The case-study table on uncertainty.md became three paragraphs so
  that each image sits beside its case rather than stacked under the table.

## Run 2 — Lecture 2 (Discrete Motion Planning), 2026-10-20

Scope: lecture 2 only. Settings carried from run 1: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-20: still 9 lectures.

### Transcripts
- [x] 02 Lecture 2: Discrete Motion Planning — video LhLd8Kon1GY — verbatim captions in raw/transcripts/original/
- [x] 02 copy-edit (Sonnet): 97/97 timestamps identical; ratios all in band (lowest 0.74 at 15:39); number diffs all coordinate pairs restored from captions ("22 412" -> (2, 2), (1, 4), (1, 2)), "C3" -> C free, and false starts; 46 restorations, 15 unclear; proper nouns grepped (LaValle, AlphaFold, SE2 not in the deck: Lecture 1 slide 55, spoken aside, student answer)

### Slides
- [x] Download Lecture2.pdf (Dropbox dl=1, 14MB, 79 pages) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (79 pages); pages 1, 3, 4 print no number
- [x] raw/slides/02-discrete-motion-planning.md (Sonnet), --verify clean (79 headings)
- [x] Figure audit of seven figure-heavy pages (Sonnet): 24, 33, 45, 63 agree; 56 red set listed in full, 73 label position, 24 hedge dropped. Printed slip noted on 73 (tie-break by H with equal H)

### Wiki
- [x] wiki/02-discrete-motion-planning.md
- [x] Topic pages: configuration-space, graph-search; course-map row; cross-links from sense-think-act, uncertainty and the Lecture 1 page
- [x] INDEX.md table of contents and coverage paragraph

### Images
- [x] raw/images/02-discrete-motion-planning/ — 22 slides rendered (2.2MB), embedded in the slide file, the lecture page and both topic pages; 16 hand-written captions
- [x] INDEX.md image sentence; AGENTS.md table row and three general lessons; BUILD_LOG.md record (below); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, images, figureAudit, caveats
- [x] BUILD_LOG.md — lecture 2 record (below, moves with this section); index row added at the move
- [x] sources.md "In this KB" column
- [x] verify_kb.py clean (all hard checks; 284 formulas in chat and on github.com), and its review section read
- [x] Commit and push — 9262e3d; published pages re-checked: 284 formulas render on github.com
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 2 record

- **Deck.** `Lecture2.pdf` from Dropbox, 79 pages, 14MB. The text layer has no licence or copyright
  notice, and none is on the course site. Third-party material is credited only on slides 9 (Zoox)
  and 10 (Parasol Lab URL); slides 7, 11 and 19 give YouTube URLs. LICENSE.md lists what it can.
- **Numbering.** One-to-one. Pages 1, 3 and 4 (the title page and two topic maps) print no number.
  Slide 62's "62" is in the text layer but not visible on the page.
- **Transcription.** Sonnet, about 3 minutes; `--verify` clean first time (79 headings). PyMuPDF
  was not importable from the agent's shell, so it used `pdftotext` for text-layer checks. It
  flagged slides 24, 33, 44–46, 53–59, 73–74, 62 and 76 for a second reader.
- **Figure audit.** Sonnet, on slides 24, 33, 45, 56, 63, 73 and 76. All agreed in substance, with
  no invented content. Slide 24's path, which the file called "approximate by a cell at the
  turns", is exact at 600 dpi (the hedge was false again). Slide 56's red set was given as "as on
  slide 55 plus (3,5)" and is now listed in full. One label position on slide 73 was corrected.
  The agent viewed most pages at 200 dpi and cropped to 600 dpi only for 33 and 76. The renders of
  slides 46 and 74 were also checked in the parent, and both agree.
- **Printed slip.** Slide 73 says "tie in F broken by smaller H", but both tied vertices have H = 6.
  The lecturer notices this in class (≈1:06:01–1:06:47). The slide file has an `[Ed:]` note and the
  wiki says so.
- **Spoken slips.** At ≈40:35 the start is given as (1, 1), corrected at ≈41:21 to (2, 3). At ≈44:25
  (2, 2) is said not to be in the queue yet, when it is. The wiki follows the slides.
- **Animations.** Slides 62 and 76 are animations in the lecture. The PDF holds one early frame,
  which is why both of slide 76's counters read "expanded: 4". Both slide entries say so.
- **Transcript edit.** Sonnet, 97/97 timestamps identical, every paragraph ratio in 0.72–1.10
  (lowest 0.74 at 15:39; 12,909 → 11,171 words). It made 46 restorations and left 15 unclear marks.
  The number diffs are all deliberate:
  - coordinate pairs restored from garbled captions ("22 412" → (2, 2), (1, 4), (1, 2), which the
    lecturer repeats at 46:43; "to one" → (2, 1), per slide 45);
  - "C3" → C free;
  - "for connectivity" → four-connectivity;
  - false starts removed.
  Every restored proper noun is in the deck except LaValle (Lecture 1 slide 55), AlphaFold (a
  spoken aside) and SE2 (a student's answer, which the lecturer repeats).
- **Images rendered (22):** 2, 5, 7, 9–11, 15, 17–19, 22, 24, 27, 31, 32, 34, 41, 46, 59, 72, 74
  and 76. The slide file's `images:` header gives the reason for every other slide. The worked
  examples are vector drawings, so the raster test does not see them (pages 68–75 have no raster
  at all), while it flags the photo-backed title and topic-map pages. The selection was made from
  the slide file.
- **Embedding.** The first pass stacked slides 9–11 after a bulleted list of examples. The list
  became three paragraphs and the embed was re-run. Ranges such as "slides 39–41" were kept out of
  any passage that should not carry those figures.
- **Math.** Three slide-file lines put inline math straight after a quotation mark (`"$`), which
  github.com shows as raw text. They were rewritten.
- **Wiki.** The DFS walk-through was left to the posted slides in the lecture (≈49:47), so the
  wiki's DFS table comes from slides 52–59 alone.

## Run 3 — Lecture 3 (RRTs), 2026-10-21

Scope: lecture 3 only. Settings carried from runs 1–2: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures.

### Transcripts
- [x] 03 Lecture 3: Rapidly Exploring Randomized Trees (RRTs) — video KDIe1094FMo — verbatim captions in raw/transcripts/original/ (92 paragraphs, 12,152 words incl. header)
- [x] 03 copy-edit (Sonnet): 92/92 timestamps identical; ratios all in 0.72–1.10 (lowest 0.72 at 1:09:11; 12,019 → 9,719 words); number diffs C3 → C free and "00 0" → 0, 0, 0; 39 restorations, 2 inline unclear + 6 noted; proper nouns not in the deck all traced to captions (Keerthi from "Kery", Minkowski, Voronoi, Stata Center, LaValle, Hugging Face)

### Slides
- [x] Download Lecture3.pdf (Dropbox dl=1, 9.4MB, 62 pages) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (62 pages); pages 1 and 2 print no number
- [x] raw/slides/03-rrts.md (Sonnet), --verify clean (62 headings)
- [x] Figure audit (Sonnet), two passes, 34 slides incl. every step of the RRT walk-through: first pass 4 of 10 pages wrong (36 wrong point in collision, 41 node count, 44 wording, 50 tree extent); second pass 14 pages: 40/43 omitted the solid edge already drawn, 31 line clips the corner, small counts on 10/12/24. Renders of 36 and 50 checked in the parent

### Wiki
- [x] wiki/03-rrts.md
- [x] Topic pages: new wiki/rrt.md; configuration-space (robot geometry, curse of dimensionality) and graph-search (completeness, scaling) extended; course-map row; Lecture 2 forward link
- [x] INDEX.md table of contents and coverage paragraph

### Images
- [x] raw/images/03-rrts/ — 17 slides rendered (1.5MB), embedded in the slide file, the lecture page, rrt.md (3) and configuration-space.md (3); 17 hand-written captions
- [x] INDEX.md image sentence; AGENTS.md table row and three general lessons; BUILD_LOG.md record (below; index row added at the move); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, images (and the stale PNG count), figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] verify_kb.py clean (all hard checks; 553 formulas in chat and on github.com), and its review section read
- [x] Commit and push — ef6bb71; published pages re-checked: 553 formulas render on github.com
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 3 record

- **Deck.** `Lecture3.pdf` from Dropbox, 62 pages, 9.4MB. The text layer has no licence or copyright
  notice, and none is on the course site. No slide credits third-party material in words; slides
  19, 24, 49, 50, 53, 54, 56 and 58 give YouTube or Wikipedia URLs. LICENSE.md lists what it can.
- **Numbering.** One-to-one. Pages 1 and 2 (the title page and the topic map) print no number.
- **Repeats of earlier decks.** A low-resolution greyscale pixel diff against Lecture 2's deck
  found slides 2, 3, 4, 15, 17 and 18 identical (mean difference 0.00–0.01) to Lecture 2's 4, 5, 6,
  15, 17 and 18. Slide 19 is a different frame of the same video as Lecture 2's slide 19 (difference
  29.7), showing the configuration-space obstacle itself, so it was rendered. Slide 5 is one panel of
  Lecture 2's slide 76 animation.
- **Transcription.** Sonnet, about 2 minutes; `--verify` clean first time (62 headings). It flagged
  the worked-example steps (25–47), the pseudocode, and the video frames 49, 50 and 58 for a second
  reader. The agent's own note on slide 41 already contradicted itself ("five blue nodes",
  four listed).
- **Figure audit.** Sonnet, two passes. The first, on 13, 21, 36, 37, 41, 44, 46, 47, 50 and 58,
  found errors on four pages:
  - slide 36 put the nearest vertex inside the obstacle, when it is the extended point that is in
    collision, the very thing the step illustrates;
  - slide 41 counted five nodes for four;
  - slide 44 described the chain as running "along the bottom" of the obstacle;
  - slide 50 had the tree reaching the top of the tall obstacle.
  It also confirmed that slide 58's two panels are the same image as slide 50 (two pixels differ).
  This first agent viewed whole pages at 110 dpi and did not crop to 600 dpi, despite the prompt.
  Under the "dirty sample" rule, a second pass covered every remaining step of the walk-through
  (25–35, 38–40, 42, 43, 45) plus 7, 9, 10, 12, 19, 24 and 51, cropping where calls were close. It
  found:
  - slides 40 and 43 already draw the new edge, which the file omitted, so the deck has no
    "edge added" slide for iteration 4;
  - slide 31's dotted line clips the obstacle's corner;
  - small counts and wording on 10, 12 and 24.
  The renders of 36 and 50 were checked in the parent and agree. One more correction came from the
  render of 50: the up-left branch runs to about (−3.5, 5).
- **Transcript edit.** Sonnet, 92/92 timestamps identical, every paragraph ratio in 0.72–1.10
  (lowest 0.72 at 1:09:11; 12,019 → 9,719 words). Four paragraphs heavy with "uh" first came out at
  0.62–0.67. The agent raised them by keeping hedges that are in the captions ("kind of", "sort
  of"), not by adding anything. It made 39 restorations and left 2 inline unclear marks plus 6
  noted ones. The number diffs are both deliberate: C3 → C free, and the origin "00 0" → 0, 0, 0
  (the agent had written 0, 0, dropping a zero; corrected in the parent). Proper nouns not in the
  deck were all traced to the captions:
  - "Gilbert Johnson Kery" → Keerthi;
  - "Minkovski" → Minkowski;
  - "waroi" → Voronoi;
  - the lecturer's own "Stata Center", against an earlier "data center";
  - "Steve Laval" → LaValle (Lecture 1 slide 55);
  - "hugging face", capitalized.
  The header's claim that the lecturer spells out "Minkowski" was softened to "the captions spell
  it", matching its own unclear list.
- **Images rendered (17):** 7, 9, 10, 13, 19, 21, 24, 25, 28, 32, 36, 43, 47, 50, 51, 53 and 56. The
  slide file's `images:` header gives the reason for every other slide, and a script checked that
  the two lists cover slides 1–62 exactly once. Slides 54 (a title card) and 58–59 (repeated
  frames) were skipped although each is discussed.
- **Embedding.** The lecture page carries all 17 images. `rrt.md` carries 21, 47 and 51, and
  `configuration-space.md` carries 7, 13 and 21. A dry run on `configuration-space.md` would have
  stacked 7, 9 and 10 under one "slides 7–10" citation, so the citation was narrowed to slide 7. The
  Lecture 3 embed was not run on `graph-search.md`, whose Lecture 2 citations (24, 28, …) share
  numbers with Lecture 3's rendered slides. Lesson in AGENTS.md.
- **Math.** The slide file's `\bar{q}_s` put `_` straight after `}` 104 times (github.com italics
  pairing). It was rewritten as `\bar{q}_ s`, with `\lbrace`, `\Vert` and `\lt` in the pseudocode,
  and the wiki uses the same form.
- **kb.json.** `materials.images.format` said "one PNG" since run 2. Lectures 1–3 have six; fixed.

## Run 4 — Lecture 4 (Quadrotor Dynamics), 2026-10-21

Scope: lecture 4 only. Settings carried from runs 1–3: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures.

### Transcripts
- [x] 04 Lecture 4: Quadrotor Dynamics — video upI4KaGawyE — verbatim captions in raw/transcripts/original/ (88 paragraphs)
- [x] 04 copy-edit (Sonnet): 88/88 timestamps identical; ratios all in 0.72–1.10 (lowest 0.73 at 42:11, highest 1.06 at 41:23; 10,655 → 9,245 words); number diffs all deliberate ("5 theta s" → phi, theta, psi twice; 123 → 1-2-3; 111 → 1-1-1); 38 restorations, 2 inline unclear + 7 noted; "John Po" → Jon Prevost in the parent (Lecture 1 slide 46); proper nouns grepped against the slides, notes and Lecture 1's deck, the rest are spoken asides (quaternions, MATLAB, prop wash)

### Slides and notes
- [x] Download Lecture4_slides.pdf (13 pages, 30MB) and Lecture4_notes.pdf (7 pages, LaTeX) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (13 pages); pages 1–3 print no number
- [x] Pixel diff against Lectures 1–3: slides 2–3 are the topic map (0.32 and 0.88 against Lecture 3's slide 2); nothing else repeats
- [x] raw/slides/04-quadrotor-dynamics.md (Sonnet), --verify clean (13 headings); slide 13's dollar sign written out
- [x] raw/notes/04-quadrotor-dynamics.md (Sonnet): the notes carry the lecture's derivation (slide 5 says "See notes"), so they are transcribed; equations (1)–(32) checked against the text layer in the parent (the inertia matrix is blackboard-bold MSBM10, so $\mathbb{I}$ is right); thrust law on p.4 rewritten as a formula
- [x] Figure audit (Sonnet) of the deck's photographs and the notes' three figures, at 600 dpi: notes Figure 3(b) spin directions legible (re-checked in the parent), Figure 1(b) Y arrow, small fixes to 1(a), 2, 3(a); pole counts on slides 7 and 9, pipe lettering on 10; no person in any photograph; eqs. (7), (8), (28)–(31) agree

### Wiki
- [x] wiki/04-quadrotor-dynamics.md (derivation cited to the notes, since the board is not in the record; 7 images, all with hand-written captions)
- [x] Topic pages: new wiki/quadrotor-model.md and wiki/state-and-dynamics.md; configuration-space (configuration and state), crazyflie (model facts, the labs from Lecture 4, Ed thread), rrt (the RRT lab), course-map row, Lecture 2 and 3 forward links
- [x] INDEX.md table of contents, coverage paragraph, raw/notes/ entry, citation rule for notes

### Images
- [x] raw/images/04-quadrotor-dynamics/ — 4 slides (7–10) and 3 notes figures (1.5MB), embedded in the slide file, the notes file, the lecture page (7), quadrotor-model.md (3 notes figures) and crazyflie.md (slides 7, 8); every caption hand-written
- [x] INDEX.md image sentence; AGENTS.md table row, raw/notes/ layout row and notes conventions; BUILD_LOG.md record (at the move); LICENSE.md attribution and raw/notes/ in Layer 1

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] verify_kb.py clean (all hard checks; 1,027 formulas in the chat and on github.com), and its review section read: no ranking claims, every numeric claim checked against the image table
- [x] Commit and push — 02e7e72; published pages re-checked: 1,027 formulas render on github.com
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 4 record

- **Deck and notes.** `Lecture4_slides.pdf` from Dropbox, 13 pages, 30MB, and `Lecture4_notes.pdf`,
  7 pages, pdfTeX output dated 2026-09-15. Neither text layer has a licence or copyright notice.
  The only credit in either is the notes' Figure 2 caption, "source: Bitcraze.io". The deck has only
  title, topic-map, framing and lab-logistics slides. Slide 5 says "See notes", and the lecture says
  the derivation is done on the blackboard (≈4:51), which the video does not show. So the notes were
  transcribed, and the wiki cites the equations to them.
- **Numbering.** One-to-one. Pages 1–3 (title and the two topic maps) print no number.
- **Repeats of earlier decks.** The pixel diff against Lectures 1–3 put slides 2 and 3 at 0.32 and
  0.88 from Lecture 3's slide 2: the same topic map, with "Geometric planning" bold on 2 and "Robot
  dynamics" bold on 3. Nothing else came under 2. Slide 13's background is a faded copy of slide 7's
  photograph.
- **Slide transcription.** Sonnet, under a minute, `--verify` clean first time (13 headings). One
  fix in the parent: the dollar sign before slide 13's "600 / drone" would have opened a math span, so
  it is written out.
- **Notes transcription.** Sonnet, about 1.5 minutes, written to the new `raw/notes/` with
  `## Page N` headings and the notes' equation numbers as one `\tag{N}` per block. In the parent,
  every equation (1)–(32) was compared with the text layer, which agreed. The inertia matrix in
  eqs. (31)–(32) is set in `MSBM10`, so $\mathbb{I}$ is right, while the planar $I$ on p. 2 is
  italic `CMMI12`. The thrust law on p. 4, transcribed as "squared" in words, was rewritten as a
  formula. Printed slips: "Insturctor"; "Figure 3(b)" for Figure 1(b) on p. 1; "time derivates";
  $\triangleq$ in eq. (28); a stray parenthesis in "R(ϕ, θ), ψ)"; $F_{tot}$ italic in eq. (28).
  Eq. (30) prints only its first row, and the notes elide the other entries.
- **Figure audit.** Sonnet, one pass, rendering at 600 dpi and cropping each figure. It checked
  notes Figures 1–3, eqs. (7), (8) and (28)–(31), and slides 2, 3, 7–10 and 13. Findings:
  - notes Figure 3(b): the transcriber had called the rotor spin directions "not reliably
    legible", but they are legible. Top-left and bottom-right spin clockwise, the other two
    counter-clockwise. The parent viewed the 600 dpi crop and agrees;
  - notes Figure 1(b): the file missed the solid $Y$ arrow rising from $O$. The auditor called the
    file's "faint vertical line at the far right" invented. The committed render shows it is the
    right edge of a faint rectangle around the pasted drawing, so the description now says that;
  - small corrections to the $L$ arrow in Figure 1(a), the arrowhead of Figure 3(a), and the
    "right-angle guides" in Figure 2, which are three empty outlined boxes;
  - pole counts on slides 7 (about eight, not six) and 9 (four, not three), and slide 10's pipe
    lettering;
  - no person visible in any photograph. Equations agree.
  The parent also viewed the renders of notes Figure 1 and slide 9, which agree.
- **Transcript edit.** Sonnet, about 3 minutes. 88/88 timestamps identical. Every paragraph ratio
  is in 0.72–1.10 (lowest 0.73 at 42:11, highest 1.06 at 41:23; 10,655 → 9,245 words). The 42:11
  paragraph first came out at 0.66 and was raised by keeping the captions' own repetitions. The
  number diffs are all deliberate: "5 theta s" → phi, theta, psi (twice), "space 123" → 1-2-3,
  "111" → 1-1-1. The captions write "x dot" where the lecturer means the second derivative ("x dot.
  So the second time derivative of x", 7:14). The agent restored "double dot" from that wording
  and the notes, and the header says so. In the parent, "John Po" → Jon Prevost (Lecture 1 slide
  46, restored the same way in Lecture 1's transcript). "Kian" is kept as captioned, noted as
  presumably the TA Kian Orr. Proper nouns not in any deck are spoken asides: quaternions, MATLAB,
  prop wash.
- **Images rendered (7):** slides 7, 8, 9 and 10 (the two lab spaces, the RRT lab arena, and the
  one still of the lab video, which did not play in the lecture), and the notes' Figures 1, 2 and 3
  as `notes-figure-N.jpg`. The notes figures are cropped with their captions to 1400px. JPEG
  beat PNG on all three: 47, 79 and 85 KB, against 88, 112 and 100 KB. Not rendered: slide 1
  (title), slides 2–3 (topic maps that repeat Lecture 3's slide 2 apart from the bold line), slides
  4, 5, 6, 11 and 12 (text), and slide 13 (a faded repeat of 7 under transcribed text). 1.5MB in
  all.
- **Embedding.** The lecture page carries all 7 images. `quadrotor-model.md` carries the three
  notes figures, and `crazyflie.md` slides 7 and 8. The notes figures were placed by hand, because
  `embed_slide_images.py` handles only `slide-N` files. Both the lecture page and `crazyflie.md`
  first cited "slides 6–13" for the lab section. Embedding would have stacked slides 7–10 under
  that one citation (`crazyflie.md` dry run: +2 for 9 and 10), so both citations were narrowed.
- **Math.** Two inline formulas wrapped across a line break, `$[x, y,` / `\theta]$` and an
  Euler-rate vector. Both passed the offline check and rendered as raw text on github.com, which
  `verify_kb.py --github` caught. They were rewrapped, and the lesson is in AGENTS.md. Formulas
  inside the italic image captions were rewritten as plain text.

## Run 5 — Lecture 5 (Differential Flatness), 2026-10-21

Scope: lecture 5 only. Settings carried from runs 1–4: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.

### Transcripts
- [x] 05 Lecture 5: Differential Flatness — video 64Rfzm359Xg — verbatim captions in raw/transcripts/original/ (86 paragraphs, 9,968 words)
- [x] 05 copy-edit (Sonnet): 86/86 timestamps identical; ratios all in 0.72–1.10 (lowest 0.79 at 20:26, highest 1.05 at 30:34; 9,847 → 8,685 words); numbers identical paragraph by paragraph; ~20 restorations; in the parent, two more garbles marked unclear (21:13, 57:22), "word" → board (28:13), and the spoken names UPenn, GRASP Lab, AeroAstro (slide 6), Davide Scaramuzza and Sertac Karaman restored with the captions' form noted (not printed in the course materials)

### Slides and notes
- [x] Download Lecture5_slides.pdf (6 pages, 3MB, Keynote) and Lecture5_notes.pdf (4 pages, pdfTeX) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (6 pages); page 1 prints no number
- [x] Pixel diff against Lectures 1–4: no repeats (slide 5 matches Lecture 1's slide 9 only because both are black video frames; slide 1 is the shared title background)
- [x] raw/slides/05-differential-flatness.md (Sonnet), --verify clean (6 headings)
- [x] raw/notes/05-differential-flatness.md (Sonnet); the definition on p. 2 and eqs. (1)–(4) agree with the text layer (checked in the parent); four drawings described
- [x] Figure audit (Sonnet) at 600 dpi: slide 2's paper figure (a photograph with arrows, not a drawing; $x_W$ and $y_W$ directions and the $\psi$ arc fixed), slide 4 (five gates, not four), notes p. 2 pipeline (three plots, not four); slides 1, 3, 5, 6, the other notes drawings and the definition and eqs. (1)–(4) agree. Renders of notes figures 3 and 4 viewed in the parent: agree (arm colour fixed)

### Wiki
- [x] wiki/05-differential-flatness.md (derivation cited to the notes; 7 images, all with hand-written captions)
- [x] Topic pages: new wiki/differential-flatness.md; rrt (extension under dynamics, Where it appears), quadrotor-model (flat outputs, Lectures), state-and-dynamics, course-map row, Lecture 3 and 4 forward links
- [x] INDEX.md table of contents, coverage paragraph, raw/slides and raw/notes entries, citation rule for notes

### Images
- [x] raw/images/05-differential-flatness/ — slides 2, 3, 4 and the notes' 4 drawings (0.5MB), embedded in the slide file, the notes file, the lecture page (7) and differential-flatness.md (notes drawing 3); every caption hand-written
- [x] INDEX.md image sentence; AGENTS.md table row and three lessons (video slides, uncaptioned notes drawings, black-frame and retitled-video repeats); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] verify_kb.py clean (all hard checks; 1,380 formulas in the chat and on github.com after fixing 11 GitHub-only breaks: `$p$th`, `_` after `}`, `$` after a quote, a display block inside a list), and its review section read: no ranking claims, every numeric claim checked against the image table
- [x] Commit and push — b357a1c, then 34249fa (the slide file's front matter, which GitHub renders as a table, had math in it); published pages re-checked: 1,376 formulas render on github.com
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 5 record

- **Deck and notes.** `Lecture5_slides.pdf` from Dropbox, 6 pages, 3MB, exported from Keynote on
  2026-09-17, and `Lecture5_notes.pdf`, 4 pages, pdfTeX output of the same date. Neither text layer
  has a licence or copyright notice. The deck is a title page, the first page of Mellinger and
  Kumar's "Minimum Snap Trajectory Generation and Control for Quadrotors" (slide 2, its bottom edge
  cut off), and four video slides (3–6) captioned with YouTube URLs. The derivation was done on the
  blackboard, so the notes were transcribed and the wiki cites the equations to them. Their numbers
  (1)–(4) match the ones the lecture speaks (≈8:41, ≈33:46).
- **Numbering.** One-to-one. Page 1 (title) prints no number.
- **Repeats of earlier decks.** The pixel diff flagged slide 5 against Lecture 1's slide 9 at 0.0.
  It is not a repeat: both are all-black video frames. Slide 1 shares the title background of
  Lectures 1 and 4. The diff missed one real repeat. Slide 6 is the same video, with the same
  title-card frame, as Lecture 3's slide 54, under a new title bar ("RRT\* + Differential
  Flatness"). The lecture says so (≈1:06:07), and the URL ul7YboQA5OY is printed on both.
- **Slide transcription.** Sonnet, about a minute, `--verify` clean first time (6 headings). The
  agent wrote "the video does not play" on each video slide, which it could not know. The parent
  replaced it with what the lecture shows: each video was played, slide 3's with its audio.
- **Notes transcription.** Sonnet, in the same agent. The definition on p. 2 (unnumbered) and eqs.
  (1)–(4) on p. 3 were compared with the text layer in the parent and agree. $\mathbb{R}$ is `MSBM10`.
  Printed slips: "it turns out the at the system" (p. 3); $t \in [0, t]$ for $[0, T]$ (p. 3);
  "control inputs require to execute" (p. 3). The four drawings have no printed number or caption.
  They are numbered `notes-figure-1` to `-4` in order of appearance. The agent reported "a fifth
  drawing" on p. 3, but the page has four rasters, and the one it meant is the fourth.
- **Figure audit.** Sonnet, one pass at 600 dpi with crops, over all 6 slides, the four drawings,
  the definition and eqs. (1)–(4). Findings:
  - slide 2's Fig. 1 is a photograph of a quadrotor with overlaid frames; the file had called it
    a drawing and a photograph in one sentence. Grey $x_W$ points down and slightly *right*, and
    $y_W$ right and slightly *down*. One $\psi$ arc spans $y_W$ and $y_C$ three-quarters of the way
    along them, not at the origin;
  - slide 4 shows five gates, not four (two "UZH" checkered gates and three further back);
  - the notes' p. 2 pipeline has three plots, not four, and the state curve dips below the $t$ axis;
  - slides 1, 3, 5 (all black) and 6, the other drawings and every equation agree. No person is
    visible in any frame.
  The parent viewed the renders of notes drawings 3 and 4. They agree, apart from the arm colour
  in drawing 4 (light grey, not black), which was fixed.
- **Transcript edit.** Sonnet, about 2.5 minutes. 86/86 timestamps identical. Every paragraph ratio
  is in 0.72–1.10 (lowest 0.79 at 20:26, highest 1.05 at 30:34; 9,847 → 8,685 words). The numbers
  are identical paragraph by paragraph. About 20 restorations, among them "x dot" → "x double dot"
  where the lecturer means the second derivative, and "XYZ and Y" → "x, y, z and yaw". The parent
  made these changes:
  - marked two more garbles unclear: "expand t oft" (21:13), whose answer shows it asked about
    specifying theta, and "excess data" (57:22);
  - restored "use this word" → board (28:13);
  - restored spoken names the agent had kept as captioned: "UPEN … grass lab" → UPenn's GRASP
    Lab; "aerastro" → AeroAstro (the logo on slide 6); "David Scaruda" → Davide Scaramuzza;
    "Sach Carman" → Sertac Karaman. The last two are printed nowhere in the course material,
    so each keeps the captions' form in an inline `[Ed:]` note, and the wiki and kb.json say so.
  The moment equation is spoken with "F1 plus F2" (8:41) and corrected by a student (37:46); the
  transcript keeps both as spoken.
- **Images rendered (7):** slide 2 (the paper page with Fig. 1), slides 3 and 4 (video frames:
  Mellinger and Kumar's video and the Zurich drone racing), and the notes' four drawings, cropped
  from the page at 1400px. They weigh 0.5MB in all: 180, 193 and 132 KB for the slides, 21–49 KB
  for the drawings. Drawing 4's crop was redone with no bottom margin, because the first one
  caught the top of the "States" line. Not rendered: slide 1 (title), slide 5 (black frame) and
  slide 6 (a title card whose text is transcribed, repeating Lecture 3's slide 54).
- **Embedding.** The lecture page carries all 7 images, placed by hand with hand-written captions
  (`embed_slide_images.py --dry-run` then added nothing to it). The script put slides 2–4 into the
  slide file. The notes drawings were placed by hand above their descriptions in `raw/notes/`.
  `differential-flatness.md` carries drawing 3.
- **Math.** The offline check passed, and `--github` found 11 GitHub-only breaks:
  - `$p$th` and `$q$th`, where an inline `$` before a letter does not close; now
    `$p\text{th}$`;
  - `\bar{q}_{\text{rand}}` and `\underbrace{…}_{…}`, with `_` after `}`;
  - `$` straight after a quotation mark;
  - a `$$` block inside a list item, which GitHub renders inline (the list became paragraphs).
  After the push, `--github-published` found 4 more, all in the slide file's front matter, which
  GitHub renders as a table, where math does not render. It was rewritten in plain words.

## Run 6 — Lecture 6 (Trajectory Optimization), 2026-10-21

Scope: lecture 6 only. Settings carried from runs 1–5: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.

### Transcripts
- [x] 06 Lecture 6: Trajectory Optimization — video ETOwJ-aPWe8 — verbatim captions in raw/transcripts/original/ (92 paragraphs, 10,312 words)
- [x] 06 copy-edit (Sonnet): 92/92 timestamps identical; ratios all in 0.72–1.10 (lowest 0.81 at 22:00, highest 1.00 at 29:54; 10,185 → 9,177 words); numbers identical except two deliberate removals (a stuttered "1" at 24:24, a false start "u1 … or vx" at 39:13); 18 restoration rows; 4 [Ed: unclear]; Mosek, Gurobi, ORF 363 confirmed in the notes; in the parent, "Claude" (1:01:02, printed nowhere) given the captions' form in an inline [Ed:] note, "put MIT with PVC pipes" (1:10:41) marked as captioned, and the Names section corrected

### Slides and notes
- [x] Download Lecture6_slides.pdf (18 pages, 6MB, Keynote) and Lecture6_notes.pdf (3 pages, pdfTeX, no drawings) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (18 pages); pages 1 and 2 print no number
- [x] Pixel diff against Lectures 1–5: no repeat of a figure slide (title background, topic map and section-divider layout only); the three video URLs (slides 16–18) appear in no earlier slide file
- [x] raw/slides/06-trajectory-optimization.md (Sonnet), --verify clean (18 headings)
- [x] raw/notes/06-trajectory-optimization.md (Sonnet); eqs. (1)–(10) agree with the text layer in the parent (tag positions by span y-coordinate; every entry of the evaluated A and B in eqs. (7)–(8)); no drawings, no MSBM10, no printed slips found
- [x] Figure audit (Sonnet), crops at 300–500 dpi, slides 2, 3, 6, 8, 11, 12, 14, 16, 17, 18: nothing described that is not on the page; fixed slide 14 (10 brackets, not about 13; dot counts confirmed at 23 by pixel components; one visible thrust line, u1 hidden under u2; teal arrows on Start only) and slide 12 (the arrow is perpendicular to the edge, not aimed at (4, 3); the x1 + x2 ≤ 4 label's position); slide 16 detail added; the other seven agree

### Wiki
- [x] wiki/06-trajectory-optimization.md (derivation cited to the notes; 6 slide images, every caption hand-written)
- [x] Topic pages: new wiki/trajectory-optimization.md (with slide 12) and wiki/linearization.md; rrt (RRTs with dynamics, Where it appears), differential-flatness, state-and-dynamics, quadrotor-model Lectures entries; course-map row; Lecture 3, 4 and 5 forward links (Lecture 5's "model predictive control is to be touched on there" now says Lecture 6 does not mention it)
- [x] INDEX.md table of contents (lecture page, two concept pages), coverage paragraph, raw/slides and raw/notes entries, citation rule

### Images
- [x] raw/images/06-trajectory-optimization/ — slides 3, 6, 8, 12, 14, 16 (0.5MB), embedded in the slide file (script), the lecture page (6, by hand, captions hand-written) and trajectory-optimization.md (slide 12); the notes have no figures
- [x] INDEX.md image sentence; AGENTS.md table row and two lessons in general form (board vs notes differences; a live demo's screenshot is a single frame); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 1,721 formulas in the chat and on github.com, first time), and its review section read: no ranking claims, 83 images = 76 slides + 7 notes figures, 6 on disk and 6 in the wiki for Lecture 6
- [x] Commit and push — 7b573db, a47588d, 22e2aba; published pages re-checked: 1,731 formulas render on github.com
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 6 record

- **Deck and notes.** `Lecture6_slides.pdf` from Dropbox, 18 pages, 6MB, exported from Keynote on
  2026-09-22, titled "Lecture 6: Planning with dynamics", and `Lecture6_notes.pdf`, 3 pages, pdfTeX
  output of the same date. Neither text layer has a licence or copyright notice. The deck states the
  RRT ideas (slides 4–9), sends the linear case to the notes (slide 10, "See lecture notes"), pictures a
  quadratic program (11–12), shows a sequential-QP demo (13–14) and three videos (15–18). The
  linearization and the QP were done on the blackboard (≈13:19), so the notes were transcribed and the
  wiki cites the equations to them. The lecture never speaks their numbers (1)–(10).
- **Numbering.** One-to-one. Pages 1 (title) and 2 (course outline) print no number.
- **Repeats of earlier decks.** The pixel diff at 64px matched only the title background (slide 1),
  the course-outline layout (slide 2, 0.60 against Lecture 4's page 3) and the divider layout (slide 4,
  0.28). No figure slide repeats. The three video URLs on slides 16–18 appear in no earlier slide file.
  Slide 3's video frame is all black, like Lecture 5's slide 5, but nothing identifies it.
- **Slide transcription.** Sonnet, about 2 minutes, `--verify` clean first time (18 headings), and
  `check_math.mjs --github` clean on both files. The agent kept slide 5's $u_ {\text{rand}}$ without
  its bar, as printed. The parent added what the lecture shows on slides 3, 14 and 16–18.
- **Notes transcription.** Sonnet, in the same agent. No drawings (the vector paths are the header
  rule, an underbrace and fraction bars), no `MSBM10`, no printed slips found. The parent checked every
  equation against the text layer: the y-coordinate of each tag puts (6) on the Jacobian of partials
  and (7) on the evaluated $A$, and every entry of eqs. (7) and (8) agrees. The notes give $C$ as
  $n \times n$; the board had $k \times n$ (≈51:43, captions "K by N").
- **Figure audit.** Sonnet, one pass with crops at 300–500 dpi over slides 2, 3, 6, 8, 11, 12, 14,
  16, 17, 18, counting slide 14's dots by pixel-colour components. Nothing described is absent from
  the page. Findings:
  - slide 14: 10 constraint brackets, not "about 13"; the 23 orange dots (11 and 12) confirmed; only
    one thrust line is visible (teal, about 2.96), the blue $u_1$ line hidden under it; the teal
    arrows are on the Start drone only;
  - slide 12: the $-\nabla f$ arrow is perpendicular to the edge $x_1 + x_2 = 4$, ending near
    (2.5, 2.5), not aimed at (4, 3); the $x_1 + x_2 \le 4$ label sits below the thick ellipse with
    no leader line;
  - slide 16: rails and planks against the wall, a yellowish frame atop the rod (added);
  - slides 2, 3, 6, 8, 11, 17, 18 agree, including both video title cards' author lists. No person is
    visible in any frame.
  The parent viewed the renders of slides 12 and 14; they agree with the corrected file.
- **Transcript edit.** Sonnet, about 4 minutes. 92/92 timestamps identical. Every paragraph ratio is
  in 0.72–1.10 (lowest 0.81 at 22:00, highest 1.00 at 29:54; 10,185 → 9,177 words). Numbers identical
  paragraph by paragraph except two deliberate removals: a stuttered "1" ("u1 1 just needs to be mg",
  24:24) and a false start ("u1 uh or or vx", 39:13). 18 restoration rows, among them "f ofxq" →
  f of x, u; "xs/access/excess" → x s; "or 363" → ORF 363 and "MOS, Groi" → Mosek, Gurobi (notes p.
  3); "4a 3" → 4, 3 (slide 11); "compass gate walker" → compass gait walker. Four `[Ed: unclear]`:
  18:09 ("so it's x dot"), 38:27 ("u1 1 vy u2"), 47:46 (no "2 delta t"), 1:00:17 ("Clex", a third
  solver). The parent made these changes:
  - "wipe coded with cloud" → vibe coded with Claude (1:01:02), printed nowhere in the course
    material, so it keeps the captions' form in an inline `[Ed:]` note, and the Names section, which
    said every spoken name was printed, was corrected;
  - "I put MIT with PVC pipes" (1:10:41) marked `[Ed: as captioned]`.
  No video audio is in the captions; each video was narrated by the lecturer.
- **Images rendered (6):** slides 3 (the recap drawing and black video frame), 6 (Tedrake's RRT plot),
  8 (the extension diagram), 12 (the QP contour plot), 14 (iteration 0 of the sequential-QP demo) and
  16 (the acrobot video still). 0.5MB in all; slides 3 and 8 came out PNG. Not rendered: the title
  (1), the course outline (2), the dividers (4, 10, 13, 15), the text slides (5, 7, 9), slide 11 (the
  build step before 12) and slides 17 and 18 (video title cards whose text is transcribed).
- **Embedding.** The script put all six into the slide file. The lecture page carries all six, placed
  by hand with hand-written captions; `trajectory-optimization.md` carries slide 12. Captions carry no
  `$` math, which GitHub does not render inside italics.
- **Wiki.** Two new concept pages, `trajectory-optimization.md` and `linearization.md`. Two
  explanations of mine were taken out of the drafts before the check (a physical reading of the $-g$
  entry; why sequential QP re-linearizes), since the course does not give them. Lecture 5's page said
  model predictive control "is to be touched on" in Lecture 6; Lecture 6 does not mention it, and the
  page now says so.

## Run 7 — Lecture 7 (Stability and PD Control), 2026-10-21

Scope: lecture 7 only. Settings carried from runs 1–6: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.

### Transcripts
- [x] 07 Lecture 7: Stability and PD Control — video nn022Copybg — verbatim captions in raw/transcripts/original/ (98 paragraphs, 11,198 words)
- [x] 07 copy-edit (Sonnet): 98/98 timestamps identical; ratios all in 0.72–1.10 with [Ed:] notes excluded (11,100 → 10,007 words); numbers identical except two deliberate changes ("y z" → y0 at 1:09:54, a stuttered "x1" at 1:11:29); 24 restoration rows; 2 [Ed: unclear] (29:55 "N9 the speed of light", 1:02:07 a student question) and 7 notation notes; Lyapunov confirmed in the notes, Taylor in Lecture 6's; in the parent, the Names section corrected (Newton's second law is spoken)

### Slides and notes
- [x] Download Lecture7_slides.pdf (7 pages, 4.8MB, Keynote) and Lecture7_notes.pdf (5 pages, pdfTeX, three pasted drawings) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (7 pages); pages 1 and 2 print no number
- [x] Pixel diff against Lectures 1–6: only the title background (slide 1) and the course-outline layout (slide 2) match; no figure slide repeats
- [x] raw/slides/07-stability-and-pd-control.md (Sonnet), --verify clean (7 headings); check_math clean
- [x] raw/notes/07-stability-and-pd-control.md (Sonnet); eqs. (1)–(19) agree with the text layer in the parent (tag positions by span y-coordinate); slips: header "Lecture #4", eq. (16) prints k_p/m (the agent's two other equation "slips" were the correct 1/m of eqs. (14) and (17), removed), "describe", ".;"
- [x] Figure audit (Sonnet), slides 3–6 and notes drawings 1–3 at 400–600 dpi: nothing described is absent; slides 4–6 agree; fixed slide 3 (path cuts both dashed margins), notes figures 1–2 (direction of every outer curve, loop counts, full dashed circle), figure 3 (axis solid below the body, dotted above); renders of slides 3 and 6 and notes figure 2 viewed in the parent

### Wiki
- [x] wiki/07-stability-and-pd-control.md (definitions cited to the notes, with the board's naming where it differs; 5 images, every caption hand-written)
- [x] Topic pages: new wiki/stability.md (with notes drawing 2) and wiki/feedback-control.md (with slide 6); quadrotor-model, linearization, state-and-dynamics, trajectory-optimization (MPC, the replayed demo), uncertainty, crazyflie Lectures entries; course-map row; Lecture 4, 5 and 6 forward links (Lecture 5's MPC sentences now say it comes up in Lecture 7)
- [x] INDEX.md table of contents (lecture page, two concept pages), coverage paragraph, raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/07-stability-and-pd-control/ — slides 3 and 6 and notes drawings 1–3 (0.4MB), embedded in the slide file (script), the notes file (by hand, above each description), the lecture page (all 5, by hand) and the two concept pages
- [x] INDEX.md image sentence; AGENTS.md table row and two lessons in general form (check a reported equation slip by substitution; audit arrow directions in drawn trajectories), and "how a definition is built up" added to the board-vs-notes rule; LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 2,084 formulas in the chat and on github.com after one fix, an inline matrix GitHub would not render in the notes file), and its review section read: no ranking claims, 88 images = 78 slides + 10 notes figures, 5 on disk and 5 in the wiki for Lecture 7
- [x] Commit and push — 047a88a, 3bbfb18, 140768f; published pages re-checked: 2,096 formulas render on github.com
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 7 record

- **Deck and notes.** `Lecture7_slides.pdf` from Dropbox, 7 pages, 4.8MB, exported from Keynote on
  2026-09-24, titled "Lecture 7: Feedback Control", and `Lecture7_notes.pdf`, 5 pages, pdfTeX output of
  the same date. Neither text layer has a licence or copyright notice. The deck motivates feedback
  control (slides 3–6) and states the plan (slide 7); the definitions and the PD example were done on
  the blackboard, so the notes were transcribed and the wiki cites them. The lecture never speaks their
  numbers (1)–(19).
- **Numbering.** One-to-one. Pages 1 (title) and 2 (course outline) print no number.
- **Repeats of earlier decks.** The pixel diff at 64px matched only the title background (slide 1,
  0.50 against Lecture 4's page 1) and the course-outline layout (slide 2, 0.50–0.68). Slides 3 and 5–7
  are at 5.1 or more against every earlier page. Slide 3 is not Lecture 6's slide 14 (6.91), though it
  shows the same demo.
- **Slide transcription.** Sonnet, about 1.5 minutes for deck and notes together, `--verify` clean first
  time (7 headings), `check_math.mjs` clean. The parent added to slide 3 what the lecture shows (the run
  played in class, numerical integration error, the 10% inertia and mass runs).
- **Notes transcription.** Sonnet, in the same agent. Three pasted raster drawings (pp. 2, 3, 4), no
  printed figure numbers or captions, numbered `notes-figure-1` to `-3`; `MSAM10` is the ≜ of eqs. (4),
  (13) and the definition of $\tilde{y}$, and there is no `MSBM10`. The parent checked every equation
  against the text layer by span position: eq. (16)'s proportional term is printed $k_p/m$ (the $k$ above
  the $m$ at x = 295), a slip, since eq. (17) and the board (≈1:12:16) need $k_p$. The agent listed two
  further "slips", the $1/m$ of eqs. (14) and (17), which are correct (they come from $\ddot{y} = u_1/m - g$);
  the parent removed them. One inline matrix in a drawing description did not render on github.com and
  was reworded.
- **Figure audit.** Sonnet, one pass at 400–600 dpi over slides 3–6 and the notes' three drawings, also
  at the embedded images' native resolution. Nothing described is absent from the page. Findings:
  - notes figure 1: all three outer curves start at dots and run in to the origin (the file had two
    arrowheads pointing the wrong way); four to five loops, not four;
  - notes figure 2: the dashed circle runs all the way round (not "in pieces"); three to four loops with
    counter-clockwise arrowheads; the "short curve with a dot-like end" is a long line with an arrowhead
    that enters the ball, and the two curves on the right start at dots and leave it;
  - notes figure 3: the vertical axis is solid below the body, with an arrowhead above the dome and a
    dotted line above it;
  - slide 3: the planned path cuts through both obstacles' dashed margins (the file said it passed
    over and below them); the rest, including the printed m = 0.600 kg and J = 0.01500 kg·m², agrees;
  - slides 4, 5 and 6 agree; added the bottom drone's arrow lengths relative to the others.
  The parent viewed the renders of slides 3 and 6 and notes figure 2; they agree with the corrected files.
- **Transcript edit.** Sonnet, about 5 minutes. 98/98 timestamps identical. Every paragraph ratio is in
  0.72–1.10 once `[Ed:]` notes are excluded (11,100 → 10,007 words). Numbers identical paragraph by
  paragraph except two deliberate changes: "y z" → y0 (1:09:54) and a stuttered "x1" (1:11:29). 24
  restoration rows, among them the eight garbles of Lyapunov ("leapono", "the open", "sensibly up andov",
  "the upon" …), "asmtotically" → asymptotically, "the mouse" → the mass (4:02), "next wetness day" →
  next Wednesday, and "u = 2 x2" → negative 2 x2 (1:00:34, on the lecturer's "it doesn't have to be
  negative 2"). Two `[Ed: unclear]`: 29:55 ("N9 the speed of light"; the notes and 34:38 say 0.99) and
  1:02:07 (a garbled student question). Seven notation notes where the captions drop a symbol the notes
  show (21:53 "x = f of x" without the dot; 25:51 no norm; "y dot" for y double dot at 1:05:58, 1:09:07,
  1:10:40 and 1:12:16; "y and y" at 1:09:54). In the parent, the Names section, which said no other name
  was spoken, now names Newton's second law (1:05:58). Lyapunov is printed in the notes; Taylor in
  Lecture 6's.
- **Board versus notes.** The board defines global and local attractivity and then global and local
  asymptotic stability as attractivity plus stability in the sense of Lyapunov (≈20:21–48:46); the notes
  never say "attractivity". The board's local condition was spoken as a strict inequality, "less than r"
  (≈33:52); the notes have $\leq R$. The board's stabilizability needs a feedback controller making the
  system globally asymptotically stable (≈59:47); the notes' eq. (9) only that every state can be driven
  to the fixed point. The board's example first had $x_1 + u$, corrected to $x_2 + u$ (≈54:13), and its
  sign-flipped variant $\dot{x}_ 1 = -x_1$ is on the board only. The wiki follows the notes and gives these.
- **Images rendered (5):** slides 3 (the simulation frame before execution) and 6 (the hover vector field
  with "feedback control law"), and the notes' three drawings (two phase portraits and the planar
  quadrotor). 0.4MB in all; slide 6 came out PNG. Not rendered: the title (1), the course outline (2),
  slide 4 (a stock photograph of an "Uncertainty" road sign beside text), slide 5 (the same figure as 6
  under a different caption) and slide 7 (text in a box).
- **Embedding.** The script put the two slide images into the slide file; the notes drawings were placed
  by hand above their descriptions. The lecture page carries all five, placed by hand with hand-written
  captions; `stability.md` carries notes drawing 2 and `feedback-control.md` slide 6. Captions carry no
  `$` math. Questions in the Lyapunov section were first written as italic lead-ins containing math,
  which GitHub does not render; they are bold or plain now.
- **Wiki.** Two new concept pages, `stability.md` and `feedback-control.md`. Lecture 5's page said model
  predictive control would be touched on in the next lecture and Lecture 6's did not; it comes up in
  Lecture 7's Q&A as receding horizon control (≈10:06–11:40), and Lecture 5's page and the
  trajectory-optimization page now say so. Phrases of mine taken out of the drafts before the check: that
  a student had asked about using trajectory optimization for feedback (the captions do not show a
  question), a lower-case $r$ on the board (captions cannot show case), and that linear feedback design
  starts from the linearization (the course has not said so).

## Run 8 — Lecture 8 (The Linear Quadratic Regulator), 2026-10-21

Scope: lecture 8 only. Settings carried from runs 1–7: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.
Ticks the "Lectures 8–9" line for Lecture 8 (split above, Lecture 9 stays open).

### Transcripts
- [x] 08 Lecture 8: The Linear Quadratic Regulator (LQR) — video zqi9QhUio8s — verbatim captions in raw/transcripts/original/ (99 paragraphs, 11,635 words)
- [x] 08 copy-edit (Sonnet), checked in the parent: 99/99 timestamps identical; numbers identical paragraph by paragraph; every ratio in 0.72–1.10 with [Ed:] notes and student tags excluded (11,495 → 9,886 words); 38 restoration rows, 7 [Ed: unclear], 8 notation notes; Riccati, Lyapunov, Zurich, MATLAB printed in the material; in the parent, Kian confirmed as Kian Orr (Lecture 1, slide 45) and "Jang" left unclear (no TA of that name)

### Slides and notes
- [x] Download Lecture8_slides.pdf (13 pages, 7.6MB, Keynote, 2026-09-29) and Lecture8_notes.pdf (4 pages, pdfTeX, two pasted drawings) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (13 pages); pages 1, 2 and 9 print no number. Pixel diff: slides 2–5 are Lecture 7's slides 2, 4, 5, 6 (0.00); slide 1 matches the title background only; nothing else under 1.7
- [x] raw/slides/08-lqr.md (Sonnet), --verify clean (13 headings); check_math clean
- [x] raw/notes/08-lqr.md (Sonnet); the one printed number, (1), and every display agree with the text layer in the parent; slips confirmed by font and text layer: the italic o subscript (CMMI8 'o', not CMR8 '0') in the fixed-point line, "Riccatti" (pp. 2, 3), "derivations", "(e.g.; hover)"
- [x] Figure audit (Sonnet), slides 6–9 and 11–13, both notes drawings, the p. 1 pipeline and the p. 2 equations: nothing described is absent; slides 6, 7, 9, 13 and the equations agree; fixed notes figure 2 (the circled entry is the third diagonal entry, z, and the arrow points from it to "Crank this up"), notes figure 1 (dashed line above, through and below the drone), slide 8's axis, slide 11's inset and second drone, slide 12's mount; renders of slide 7 and both notes drawings viewed in the parent

### Wiki
- [x] wiki/08-lqr.md (formulation cited to the notes, board differences with timestamps; 6 images, every caption hand-written)
- [x] Topic pages: new wiki/lqr.md (with notes drawing 2); feedback-control (the loop, an LQR section), stability, linearization, quadrotor-model, state-and-dynamics, crazyflie, sense-think-act, trajectory-optimization, uncertainty Lectures entries; course-map row; Lecture 4, 6 and 7 forward links
- [x] INDEX.md table of contents (lecture page, concept page, feedback-control line), coverage paragraph, raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/08-lqr/ — slides 6, 7, 11, 12 and notes drawings 1–2 (0.6MB), embedded in the slide file (script), the notes file (by hand, above each description), the lecture page (all 6, by hand) and lqr.md
- [x] INDEX.md image sentence; AGENTS.md table row and one lesson in general form (have the audit count which entry a drawing marks); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 2,567 formulas in the chat and on github.com after two fixes, an inline formula in INDEX.md and a display inside a list in lqr.md), and its review section read: no ranking claims, 94 images = 82 slides + 12 notes figures, 6 on disk and 6 in the wiki for Lecture 8
- [x] Commit and push — 38208aa, 486d4be, 1d137d7; published pages re-checked: one formula in the notes file's front matter did not render on github.com and was reworded, pushed with the move below
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 8 record

- **Deck and notes.** `Lecture8_slides.pdf` from Dropbox, 13 pages, 7.6MB, exported from Keynote on
  2026-09-29, titled "Lecture 8: Linear Quadratic Regulator", and `Lecture8_notes.pdf`, 4 pages, pdfTeX
  output of the same date. Neither text layer has a licence or copyright notice. The deck recaps
  Lecture 7 (slides 2–9), introduces LQR (slide 10) and shows three videos (slides 11–13, YouTube links
  printed); the formulation was done on the blackboard, so the notes were transcribed and the wiki cites
  them. The notes number one equation, (1); the lecture never speaks it.
- **Numbering.** One-to-one. Pages 1 (title), 2 (course outline) and 9 print no number.
- **Repeats of earlier decks.** The pixel diff at 64px matched slides 2–5 to Lecture 7's slides 2, 4, 5
  and 6 at 0.00, and slide 1 to the title background only (0.70–2.69). Slide 6 (sense–think–act) is not
  Lecture 1's slide (5.88). Slides 7–9 paste Lecture 7 material: slide 7's spiral is a new vector drawing,
  and slides 8–9 carry the Lecture 7 notes' quadrotor drawing (notes-figure-3 there). The three video URLs
  appear in no earlier slide file.
- **Slide transcription.** Sonnet, deck and notes in one agent, about 3 minutes, `--verify` clean first
  time (13 headings), `check_math.mjs --github` clean. The parent added to slides 6 and 11–13 what the
  lecture says about them (the 500 Hz loop; the three videos as played).
- **Notes transcription.** Sonnet, in the same agent. Two pasted raster drawings (pp. 1, 3), no printed
  numbers or captions, numbered `notes-figure-1` and `-2`; `MSBM10` is the $\mathbb{R}$ of p. 1 and
  `MSAM10` the ≜ of p. 2. Every display agrees with the text layer, and the single tag (1) sits at the
  first cost function (span y = 246). Slips confirmed in the parent: the fixed-point line's second
  subscript is `CMMI8` "o", not `CMR8` "0"; "Riccatti" (pp. 2, 3) and "derivations" are in the text
  layer; "(e.g.; hover)". The parent added a fifth: the positive-definite condition printed "for all
  $\bar{x}$", which the lecture itself corrects to non-zero vectors (≈29:09).
- **Figure audit.** Sonnet, one pass with crops (150 dpi for slides, 300 dpi for notes, below the 600 asked
  for) over slides 6–9 and 11–13, both notes drawings, the p. 1 pipeline and annotations and the p. 2
  equations. Nothing described is absent from the page. Findings:
  - notes figure 2: the circled dot is the third of twelve diagonal entries (the $z$ entry, answering the
    notes' question about height), not the first, and the arrow runs from it to "Crank this up"; the parent
    had seen the same in the render before the audit returned;
  - notes figure 1: the dashed vertical line runs above, through and below the drone; the horizontal
    dashed line extends both ways;
  - slide 8: the axis is solid from O through the body to an arrowhead above the dome, dotted above it
    (worded as Lecture 7's audit of the same drawing found it; a further "short dotted stretch" below the
    body, reported at 150 dpi, was not added);
  - slide 11: the inset's layout, a second quadrotor in the inset, "UZH" on the sign; slide 12: the
    airplane is mounted on top of the pole;
  - slides 6, 7, 9 and 13, the pipeline and the equations agree, including every arrow on slides 6 and 7
    (the spiral runs clockwise into the origin, arrowhead at the inner end).
  The parent viewed the renders of slide 7 and both notes drawings; they agree with the corrected files.
- **Transcript edit.** Sonnet, about 5 minutes. 99/99 timestamps identical. Every paragraph ratio is in
  0.72–1.10 with `[Ed:]` notes and student tags excluded (11,495 → 9,886 words; lowest 0.724 at
  1:14:21). Numbers identical paragraph by paragraph. 38 restoration rows, among them the six garbles of
  Riccati ("ricotti", "regard", "Ricard" …), "sar" → S star, "branspose" → B transpose, "Z not equal to Z"
  → z not equal to zero (29:09, 29:56), "math lab" → MATLAB, "aons" → ailerons and "fixing airplane" →
  fixed-wing airplane. Seven `[Ed: unclear]`: the integrand at 17:27, three student questions (36:02,
  two at 50:18), a student's words at 58:11, the dimension check at 59:42, and the name "Jang" (1:05:54).
  Eight notation notes. In the parent: "Kian" confirmed as Kian Orr from Lecture 1's slide 45; "Jang"
  left unclear, since no TA has that name (Jutang Gao is nearest, unconfirmed).
- **Board versus notes.** The board named the optimal controller $u^\ast$ (≈40:08); it first wrote the optimal
  cost at time $t$ and corrected it to the initial state (≈58:56), with a transpose on the second factor
  in the captions that the notes do not have. Spoken only: the scalar $\lambda$ weighting the control term
  (≈25:15), the quadrotor's diagonal $R$ (≈31:26), $Q$ needing only to be positive semidefinite (≈34:31),
  and trajectory-tracking LQR (≈51:05), which Majumdar said he might sketch in the notes; they do not.
  The recap's spoken PD controller has $k_p(y - y_0)$ (≈7:12), against slide 8's printed $k_p/m$, which
  supports run 7's reading of Lecture 7's eq. (16) as a slip.
- **Images rendered (6):** slides 6 (the sense–think–act loop, vector), 7 (the phase portrait), 11 (the
  Zurich quadrotor video) and 12 (the prop-hang video), and the notes' two drawings. 0.6MB in all;
  slides 6 and 7 came out PNG. Not rendered: the title (1), slides 2–5 (Lecture 7 repeats), slides 8–9
  (the Lecture 7 notes' drawing, already rendered there, beside equations transcribed exactly), the
  divider (10) and slide 13 (a video title card whose text is transcribed).
- **Embedding.** The script put the four slide images into the slide file; the notes drawings were
  placed by hand above their descriptions. The lecture page carries all six, by hand, with hand-written
  captions and no `$` math in them; `lqr.md` carries notes drawing 2.
- **Wiki.** One new concept page, `lqr.md`. Removed from the drafts before the checks: a caption calling
  the Zurich quadrotor "holding position" (the frame shows only a drone in the air); a pipeline formula in
  INDEX.md that GitHub would not render; a displayed equation inside a numbered list in `lqr.md`.

## Run 9 — Lecture 9 (Optical Flow), 2026-10-21

Scope: lecture 9 only. Settings carried from runs 1–8: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.
Ticks the "Later runs — lecture 9" line.

### Transcripts
- [x] 09 Lecture 9: Optical Flow — video wvuVX9L7v4Y — verbatim captions in raw/transcripts/original/ (89 paragraphs, 9,954 words)
- [x] 09 copy-edit (Sonnet), checked in the parent: 89/89 timestamps identical; numbers identical paragraph by paragraph except two "2"s spoken as "squared" at 1:01:28 (listed); every ratio in 0.72–1.10 with [Ed:] notes and student tags excluded (9,830 → 8,601 words; lowest 0.727 at 1:06:04); 24 restoration rows, 7 [Ed: unclear], 8 notation notes; Lucas-Kanade, Taylor, RRT printed in the material; Queensland Brain Institute, Australian National University and "Partha" confirmed in the raw captions (the bird video's narration), the surname left unclear

### Slides and notes
- [x] Download Lecture9_slides.pdf (21 pages, 32MB, Keynote, 2026-10-01) and Lecture9_notes.pdf (5 pages, pdfTeX, four pasted drawings) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (21 pages); pages 1 and 2 print no number. Pixel diff: nothing repeats an earlier deck (slide 1 matches the title background only, 0.60); within the deck slide 20 is slide 6 again (0.75)
- [x] raw/slides/09-optical-flow.md (Sonnet), --verify clean (21 headings); check_math --github clean
- [x] raw/notes/09-optical-flow.md (Sonnet); (1)–(5) and every display agree with the text layer in the parent; slips: "Lecture #18" (page 1 header only, corrected from the agent's "every page"), "determininat", "(x+u, x+v)" in drawing 2 (seen in the render)
- [x] Figure audit (Sonnet), slides 3, 5–8, 15, 17–19, the four notes drawings and the p. 4 matrix display, crops at 300–600 dpi: nothing described is absent; slides 3, 7, 15, drawings 1 and 4 and the matrix agree; fixed the road direction on slides 5 and 19 (upper left, not right) and slide 19's vehicles, slide 6's column and panel arrows plus a whole-field summary, slide 8's right-frame arrows (trailing), slide 17's box position, slide 18's inset line, drawing 3's angles. The audit's "(u, x)" for drawing 2's displacement label overruled by a crop in the parent ("(u, v)"); renders of slide 6 and drawing 2 viewed in the parent

### Wiki
- [x] wiki/09-optical-flow.md (derivation cited to the notes, board differences with timestamps; 13 images, every caption hand-written)
- [x] Topic pages: new wiki/optical-flow.md (with slide 6 and notes drawing 3); crazyflie, sense-think-act, uncertainty, feedback-control Lectures entries; course-map row; Lecture 1 and 8 forward links
- [x] INDEX.md table of contents (lecture page, concept page), coverage paragraph (all 9 recorded lectures), raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/09-optical-flow/ — slides 3–8, 15, 17, 18 and notes drawings 1–4 (1.5MB), embedded in the slide file (script), the notes file (by hand, above each description), the lecture page (all 13, by hand) and optical-flow.md (two)
- [x] INDEX.md image sentence; AGENTS.md table row and one lesson in general form (settle a handwritten-label slip from a crop in the parent); LICENSE.md attribution, and its licence-check sentence brought up to Lectures 1–9

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats; the PNG count corrected to thirteen (it read "nine", stale before this run)
- [x] sources.md "In this KB" column
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 2,640 formulas in the chat and on github.com), and its review section read: no ranking claims, 107 images = 91 slides + 16 notes figures, 13 on disk and 13 in the wiki for Lecture 9
- [x] Commit and push
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Older lines this run completes
- [x] Lecture 9 (Optical Flow), one run: transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lecture 9 also posts a notes PDF; transcribe it to raw/notes/ (AGENTS.md, Course materials).

### Lecture 9 record

- **Deck and notes.** `Lecture9_slides.pdf` from Dropbox, 21 pages, 32MB, exported from Keynote on
  2026-10-01, titled "Lecture 9: Optical Flow", and `Lecture9_notes.pdf`, 5 pages, pdfTeX output of the
  same date. Neither text layer has a licence or copyright notice. The deck opens the second module
  (slide 2), asks how the drone localized itself in the RRT lab (slide 3), motivates optical flow with
  pictures, questions and three videos (slides 4–13), hands over to the blackboard (14), shows the barber
  pole illusion (15) and the Lucas-Kanade failure cases (16–18), and closes on imperfect sensing
  (19–21). The derivation was done on the blackboard, so the notes were transcribed and the wiki cites
  them. The notes number (1)–(5); the lecture speaks "equation one", "two" and "three" (≈25:15,
  ≈27:36, ≈39:16), matching, and never numbers (4) or (5).
- **Numbering.** One-to-one. Pages 1 (title) and 2 (course outline) print no number.
- **Repeats.** The pixel diff at 64px matched no page to an earlier deck: slide 1 matches only the
  shared title background (0.60), slide 2's outline is a new layout (14.2), slide 12's black frame is
  closest to Lecture 6's slide 18 (7.9, both dark video frames). Within the deck, slide 20 is slide 6
  again (0.75 at 128px) and slide 21 that picture faded; slide 19 is a second frame of slide 5's video
  (8.2). The three video URLs appear in no earlier slide file.
- **Slide transcription.** Sonnet, deck and notes in one agent, about 3 minutes, `--verify` clean first
  time (21 headings), `check_math.mjs --github` clean. The parent added to slides 5–7, 11, 12, 15 and
  19 what the lecture says about them (the videos as played; the answer to slide 6's question).
- **Notes transcription.** Sonnet, in the same agent. Four pasted raster drawings (pp. 1, 2, 3, 5), no
  printed numbers or captions, numbered `notes-figure-1` to `-4`; `MSAM10` is the ≜ of p. 4. Every
  display agrees with the text layer, including (1)–(5). The agent wrote that every page header reads
  "Lecture #18"; the text layer has the header line on page 1 only, and the file was corrected. Slips:
  "Lecture #18" (p. 1), "determininat" (p. 5), and drawing 2's label "(x+u, x+v)" for (x+u, y+v). No
  equation slip; the agent's substitution of (2) into (1) gives (3), checked.
- **Figure audit.** Sonnet, one pass with crops at 300–600 dpi over slides 3, 5–8, 15 and 17–19, the
  four drawings and the p. 4 matrix display. Nothing described is absent from the page. Findings:
  - slides 5 and 19: the road recedes to the upper left, not the upper right; slide 19 has one van at
    the bottom edge, not two;
  - slide 6: the white column's arrows point down-right only at y 110–150 and up-right below; the dark
    panel spans y 160–250 with a chevron of arrowheads near (88, 185); a whole-field summary added (most
    arrows right or up-right, longest on the near wall, converging near the panel); the faint pink text
    begins "Sa…" and is not legible in full;
  - slide 8: in the right frame each arrow trails behind its disc, head at the disc;
  - slide 17's box is about four-fifths across, not three-fifths; slide 18's inset line repositioned;
  - drawing 3's arrow angles tightened;
  - slides 3, 7 and 15, drawings 1 and 4 and the matrix display agree, including every arrow's
    direction in drawings 1 and 2 and on slide 8.
  The audit read drawing 2's displacement label as "(u, x)". The parent's 300 dpi crop shows "(u, v)", its
  v drawn with the same crossed stroke as the v of "x+v", while the x's of the drawing are two arcs;
  only "(x+u, x+v)" is listed. The parent also viewed the renders of slide 6 and drawing 2.
- **Transcript edit.** Sonnet, about 4.5 minutes. 89/89 timestamps identical. Every paragraph ratio is in
  0.72–1.10 with `[Ed:]` notes and student tags excluded (9,830 → 8,601 words; lowest 0.727 at
  1:06:04). Numbers identical paragraph by paragraph except two "2"s spoken as "squared" at 1:01:28,
  listed. 24 restoration rows, among them "Lucas Canad", "locus can" → Lucas-Kanade, "tailor" → Taylor,
  "RT" → RRT, "barberhop" → barber pole and "single point lighter" → single-point lidar. Seven
  `[Ed: unclear]`: the researcher's surname in the bird video (13:13, "Buckavatula"), a student's answer
  (29:58), two student questions (35:20, 45:26), "the map" (41:35), the last word of the window-size
  question (55:05) and the student's answer naming the edge case (1:02:59). Eight notation notes. The
  two videos' narration is untagged, as the header says. In the parent, Queensland Brain Institute,
  Australian National University and "Partha" were confirmed in the raw captions.
- **Board versus notes.** The lecture calls the first assumption intensity constancy (≈22:43); the notes
  say "Color and Intensity constancy" (p. 1) and "Brightness constancy assumption" (p. 2). The board
  moved $I_t$ to the right of eq. (3) (≈33:46, ≈40:04). The notes' "dates from ~1981" and the numpy /
  Assignment 1 margin note are not spoken. The spoken least-squares solution is garbled (≈57:26) and the
  determinant loses its sums (≈1:01:28). At ≈1:05:18 the lecture calls the edge failure motion "aligned
  with all the image gradients"; by the notes' p. 3 derivation it is motion perpendicular to them, and
  the wiki's Gaps section says so.
- **Images rendered (13):** slides 3 (the RRT-lab path, PNG), 4 (the Flow deck photograph), 5 and 6 (the
  two flow fields), 7 (the homework diagram, PNG), 8 (the pixel-motion diagram), 15 (the barber pole
  frame), 17 and 18 (low texture and edge), and the notes' four drawings. 1.5MB in all. Not rendered: the
  title (1), the outline (2), text-only slides 9, 10 and 14, slide 11 (only a link), slide 12 (a black
  video frame), slide 13 (a news-article screenshot whose text is transcribed), slide 16 (the photograph
  17 and 18 mark up), slide 19 (a second frame of slide 5's video), slide 20 (slide 6 again) and slide 21
  (slide 6 faded behind text).
- **Embedding.** The script put the nine slide images into the slide file; the notes drawings were placed
  by hand above their descriptions. The lecture page carries all thirteen, by hand, with hand-written
  captions and no `$` math in them; `optical-flow.md` carries slide 6 and notes drawing 3.
- **Wiki.** One new concept page, `optical-flow.md`. Removed from the drafts before the checks: a caption
  calling the drone on slide 4 "the course drone" (the slide shows a Crazyflie, not necessarily one of the
  course's); "the rest greys out" for the lecture's "once it grays out"; a sentence attributing the
  jitter of the flow video to Lucas-Kanade (the lecture does not say which method made it).

## Run 10 — Lecture 10 (Nondeterministic Filter), 2026-10-28

Scope: lecture 10 only. Settings carried from runs 1–9: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-28: 11 lectures (10 "Nondeterministic
filter", 11 "Bayes filter"); creator check passed. The course site posts a video and notes for
Lecture 10 and no slide deck: the lecture was given at the board.

### Transcripts
- [x] 10 Lecture 10: Nondeterministic filter — video T7Uf2u3VVZ8 — verbatim captions in raw/transcripts/original/ (84 paragraphs)
- [x] 10 copy-edit (Sonnet), checked in the parent: 84/84 timestamps identical; numbers identical paragraph by paragraph; every ratio in 0.72–1.10 with [Ed:] notes and tags excluded (9,092 → 8,190 words; lowest 0.803 at 1:00:06) except 1:04:47, which is only the closing music mark; 6 restoration rows, 3 [Ed: unclear], 1 notation note; header fixed in the parent (no LaTeX, the names sentence, a continuation tag at 42:16, "Bayes filter" confirmed by the site's schedule)

### Notes
- [x] Download Lecture10_notes.pdf (6 pages, pdfTeX, 2026-10-06, nine pasted drawings) into raw/pdfs/ (gitignored); no deck posted
- [x] raw/notes/10-nondeterministic-filter.md (Sonnet); every display checked against the text layer in the parent (fonts of X and Z, the braces of the p. 3 dynamics display and its two arrows, the lowercase x-hat of p. 4); underline tags removed; check_math --github clean
- [x] Figure audit of the nine drawings (Sonnet), 400–1500 dpi crops: drawings 3 and 8 agree; corrections to 1, 2, 4, 5, 6, 9; drawing 7's arrow left as "most plausibly points at the state"; drawing 5's label and drawing 9's handwriting settled in the parent from the renders

### Wiki
- [x] wiki/10-nondeterministic-filter.md (follows the notes, cited by page; board differences with timestamps; 9 images, every caption hand-written)
- [x] Topic pages: new wiki/state-estimation.md (with notes drawing 5); uncertainty, sense-think-act, state-and-dynamics, stability, optical-flow Lectures entries; course-map rows 10 and 11 and its intro; Lecture 1 and 9 forward links
- [x] INDEX.md table of contents (lecture page, concept page), coverage paragraph (10 of 11 recorded lectures), raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/10-nondeterministic-filter/ — the notes' nine drawings (0.4MB), cropped at 1400px, placed by the transcription above each description and by hand in the wiki (all nine) and state-estimation.md (one)
- [x] INDEX.md image sentence; AGENTS.md table row and one lesson in general form (a lecture with notes and no deck; a "(1)" in notes prose may number a list); LICENSE.md attribution and its licence-check sentence brought up to the Lecture 10 notes

### Publish
- [x] kb.json — coverage (10 of 11), byLecture, notes 7/7, images 116 in 10 lectures, figureAudit note, a Lecture 10 caveat, the coverage caveat rewritten
- [x] sources.md rows 10 and 11, inventory sentence
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 3,010 formulas in the chat and on github.com, after one `>` became `\gt`), and its review section read: no ranking claims, 116 images = 91 slides + 25 notes figures, 9 on disk and 9 in the wiki for Lecture 10
- [x] Commit and push
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Older lines this run completes
- [x] Lectures 10 onward. Blocked: on 2026-10-21 the catalog holds 9 recorded lectures and the course
      site had posted materials only for lectures 1–9. When the catalog re-syncs, diff its lectures
      against raw/transcripts/ and add one line per new lecture here.

### Lecture 10 record

- **Material.** No deck: the course site's Lecture 10 row links a video and `Lecture10_notes.pdf` only.
  The notes are 6 pages of pdfTeX output (2026-10-06) with nine pasted raster drawings; no licence or
  copyright notice. The lecture was given entirely at the board. The notes print no equation numbers;
  the "(1)" and "(2)" of page 1 number two goals. Fonts: the state and measurement spaces are CMSY10
  (calligraphic), the set estimates CMMI12 X with a hat, ℝ MSBM10, ≜ MSAM10.
- **Notes transcription.** Sonnet, about 3 minutes, `check_math.mjs --github` clean. The agent wrote
  underlining as `<u>` tags, which no other notes file uses; removed in the parent. The p. 3 dynamics
  display: the text layer shows a CMEX `\bigg\{` opening and a `\Big\}` closing, and two small arrows
  rising from "[We will ignore control inputs for now]" to $\bar{u}_ t$ and to the second form; the
  description was corrected to say so. Slips: "Lecture #11" (p. 1 header); "our new estimate x̂₁"
  with a lowercase x (CMMI12 in the text layer, p. 4); drawing 5's label "f(x̂₀)"; drawing 9's
  "accont". No equation slip (step 3 at t = 1 reproduces the p. 4 display for X̂₁).
- **Figure audit.** Sonnet, crops at 400–1500 dpi. Nothing described was absent. Drawings 3 and 8 agree.
  Fixed: tick marks on the axes of drawings 1 and 2; the position of "s" in drawing 2 (up and left of
  its arrow); drawing 4's label (subscript loop, not a tail to the blob) and each arrow's ending (open
  arrowheads; heads and dots inside or just outside the right blob); drawing 5's connector (faint,
  dotted); drawing 6's dots (three, inside the narrow blob) and outlines (all solid). Drawing 7's thick
  stroke is "most plausibly" a "<" at the state (about 65%), against the text's meaning (the state
  leads to the set); the notes file and the wiki's Gaps say so and the caption gives the text's
  meaning. The audit read drawing 5's x as lowercase at about 75%; the parent's view of the render
  agrees (two arcs, as this hand writes a lowercase x; the capital X̂₀ beside it is a bold straight
  cross). Drawing 9: "have" is handwriting (the h closed into a loop), not listed; "accont" is listed,
  the missing letter not settled. Renders of drawings 5, 7 and 9 viewed in the parent.
- **Transcript edit.** Sonnet, about 3.5 minutes. 84/84 timestamps identical, numbers identical
  paragraph by paragraph. Ratios in band except 1:04:47 (only `>> [music]`); lowest real ratio 0.803
  (1:00:06). Restorations: "pre-image" → preimage, "base filter" → Bayes filter (confirmed by the course
  site's "Lecture 11: Bayes filtering"), "base rule" → Bayes rule, a stray "X" before "F of X0 hat",
  "access" dropped as a mis-hearing. Three `[Ed: unclear]`: the end of a student question (30:26), a
  student's answer (32:55), what "it" is in "let's say it's larger than 1" (48:30). One notation note:
  the third sensor's distance formula without squares (15:47). The parent removed LaTeX from the
  header, corrected "No person's name is spoken" (Bayes, Euler and Gaussian are), and added
  `*[Student answer, continued]*` at 42:16, which the header described but the text lacked.
- **Board versus notes.** The board names the distances R1, R2 (R3) and the measurement space R^D; the
  notes use r and s and only R³. The board calls steps 2 and 3 together the measurement update (≈39:10);
  the notes call step 3 "Fuse information from 1. and 2.". Spoken only: "triangulation", the 1D unstable
  example x_{t+1} = λx_t with the interval [−ε, ε], the no-sensor sensor, the polytope and
  discretization answers, and the Bayes filter preview. The notes use x̄₀ both for the sensor point
  (1, 1) and for a state in X̂₀.
- **Images rendered (9):** all nine notes drawings, 0.4MB, cropped at the image rectangles plus 6pt
  and scaled to 1400px. Drawing 7 is a 98-point-wide raster, so its crop is upscaled about 5×.
- **Wiki.** One new concept page, `state-estimation.md`, a hub for the module's filters. Removed from
  the draft before the checks: a gendered pronoun for the lecturer (now "Majumdar may spend some time on
  them"); `$\lambda > 1$` written `\gt` for github.com.
