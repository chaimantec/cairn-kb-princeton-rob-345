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
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

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

