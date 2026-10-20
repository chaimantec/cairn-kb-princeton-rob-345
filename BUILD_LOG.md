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
