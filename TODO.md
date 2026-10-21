# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lectures 7–9

- [ ] Lectures 8–9, one per run (Lecture 7 in run 7): transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lectures 7–9 also post notes PDFs; transcribe them to raw/notes/ (AGENTS.md, Course materials).

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
- [ ] wiki/07-stability-and-pd-control.md
- [ ] Topic pages and cross-links
- [ ] INDEX.md table of contents, coverage paragraph, raw/ entries

### Images
- [ ] raw/images/07-stability-and-pd-control/ — figure slides and notes figures, embedded
- [ ] INDEX.md image sentence; AGENTS.md table row; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [ ] sources.md "In this KB" column
- [ ] BUILD_LOG.md — the lecture's record
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work
