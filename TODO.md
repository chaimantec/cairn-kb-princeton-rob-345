# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lecture 9

- [ ] Lecture 9 (Optical Flow), one run: transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lecture 9 also posts a notes PDF; transcribe it to raw/notes/ (AGENTS.md, Course materials).

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
- [ ] wiki/08-lqr.md
- [ ] Topic pages and cross-links
- [ ] INDEX.md table of contents, coverage paragraph

### Images
- [ ] raw/images/08-lqr/ — render, embed in the slide file, notes file and wiki
- [ ] INDEX.md image sentence; AGENTS.md table row; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [ ] sources.md "In this KB" column
- [ ] BUILD_LOG.md — the lecture's record
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work
