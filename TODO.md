# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lectures 6–9

- [ ] Lectures 7–9, one per run (Lecture 6 done in run 6): transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lectures 7–9 also post notes PDFs; transcribe them to raw/notes/ (AGENTS.md, Course materials).

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
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

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
