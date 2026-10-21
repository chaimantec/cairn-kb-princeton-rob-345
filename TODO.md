# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lectures 4–9

- [ ] Lectures 5–9, one per run: transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lectures 5–9 also post notes PDFs; decide whether to transcribe them.

## Run 4 — Lecture 4 (Quadrotor Dynamics), 2026-10-21

Scope: lecture 4 only. Settings carried from runs 1–3: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures.

### Transcripts
- [x] 04 Lecture 4: Quadrotor Dynamics — video upI4KaGawyE — verbatim captions in raw/transcripts/original/ (88 paragraphs)
- [ ] 04 copy-edit (Sonnet), three checks, proper nouns grepped

### Slides and notes
- [x] Download Lecture4_slides.pdf (13 pages, 30MB) and Lecture4_notes.pdf (7 pages, LaTeX) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (13 pages); pages 1–3 print no number
- [x] Pixel diff against Lectures 1–3: slides 2–3 are the topic map (0.32 and 0.88 against Lecture 3's slide 2); nothing else repeats
- [ ] raw/slides/04-quadrotor-dynamics.md (Sonnet), --verify clean
- [ ] raw/notes/04-quadrotor-dynamics.md (Sonnet): the notes carry the lecture's derivation (slide 5 says "See notes"), so they are transcribed; equations checked against the text layer in the parent
- [ ] Figure audit (Sonnet) of the deck's photographs and the notes' three figures

### Wiki
- [ ] wiki/04-quadrotor-dynamics.md
- [ ] Topic pages (new: dynamics / quadrotor model; extend course-map, crazyflie)
- [ ] INDEX.md table of contents and coverage paragraph

### Images
- [ ] raw/images/04-quadrotor-dynamics/ — figure slides and notes figures, embedded
- [ ] INDEX.md image sentence; AGENTS.md table row (and notes conventions); BUILD_LOG.md record; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [ ] sources.md "In this KB" column
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work
