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
