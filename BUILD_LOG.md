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
