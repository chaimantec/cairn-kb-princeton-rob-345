# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lectures 6–9

- [ ] Lectures 6–9, one per run: transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lectures 6–9 also post notes PDFs; transcribe them to raw/notes/ (AGENTS.md, Course materials).

## Run 5 — Lecture 5 (Differential Flatness), 2026-10-21

Scope: lecture 5 only. Settings carried from runs 1–4: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.

### Transcripts
- [x] 05 Lecture 5: Differential Flatness — video 64Rfzm359Xg — verbatim captions in raw/transcripts/original/ (86 paragraphs, 9,968 words)
- [ ] 05 copy-edit (Sonnet), then the timestamp, number and ratio checks in the parent

### Slides and notes
- [x] Download Lecture5_slides.pdf (6 pages, 3MB, Keynote) and Lecture5_notes.pdf (4 pages, pdfTeX) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (6 pages); page 1 prints no number
- [x] Pixel diff against Lectures 1–4: no repeats (slide 5 matches Lecture 1's slide 9 only because both are black video frames; slide 1 is the shared title background)
- [x] raw/slides/05-differential-flatness.md (Sonnet), --verify clean (6 headings)
- [x] raw/notes/05-differential-flatness.md (Sonnet); the definition on p. 2 and eqs. (1)–(4) agree with the text layer (checked in the parent); four drawings described
- [ ] Figure audit (Sonnet) at 600 dpi: slide 2's paper figure, the video poster frames, the notes' four drawings, eqs. (1)–(4)

### Wiki
- [ ] wiki/05-differential-flatness.md
- [ ] Topic pages: new wiki/differential-flatness.md; rrt (extension under dynamics), quadrotor-model, state-and-dynamics, course-map row, Lecture 4 forward link
- [ ] INDEX.md table of contents, coverage paragraph

### Images
- [ ] raw/images/05-differential-flatness/ — figure slides and notes figures, embedded
- [ ] INDEX.md image sentence; AGENTS.md table row; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [ ] sources.md "In this KB" column
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work
