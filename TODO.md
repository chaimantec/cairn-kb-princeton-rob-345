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
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work
