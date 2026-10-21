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
- [x] wiki/07-stability-and-pd-control.md (definitions cited to the notes, with the board's naming where it differs; 5 images, every caption hand-written)
- [x] Topic pages: new wiki/stability.md (with notes drawing 2) and wiki/feedback-control.md (with slide 6); quadrotor-model, linearization, state-and-dynamics, trajectory-optimization (MPC, the replayed demo), uncertainty, crazyflie Lectures entries; course-map row; Lecture 4, 5 and 6 forward links (Lecture 5's MPC sentences now say it comes up in Lecture 7)
- [x] INDEX.md table of contents (lecture page, two concept pages), coverage paragraph, raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/07-stability-and-pd-control/ — slides 3 and 6 and notes drawings 1–3 (0.4MB), embedded in the slide file (script), the notes file (by hand, above each description), the lecture page (all 5, by hand) and the two concept pages
- [x] INDEX.md image sentence; AGENTS.md table row and two lessons in general form (check a reported equation slip by substitution; audit arrow directions in drawn trajectories), and "how a definition is built up" added to the board-vs-notes rule; LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 2,084 formulas in the chat and on github.com after one fix, an inline matrix GitHub would not render in the notes file), and its review section read: no ranking claims, 88 images = 78 slides + 10 notes figures, 5 on disk and 5 in the wiki for Lecture 7
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 7 record

- **Deck and notes.** `Lecture7_slides.pdf` from Dropbox, 7 pages, 4.8MB, exported from Keynote on
  2026-09-24, titled "Lecture 7: Feedback Control", and `Lecture7_notes.pdf`, 5 pages, pdfTeX output of
  the same date. Neither text layer has a licence or copyright notice. The deck motivates feedback
  control (slides 3–6) and states the plan (slide 7); the definitions and the PD example were done on
  the blackboard, so the notes were transcribed and the wiki cites them. The lecture never speaks their
  numbers (1)–(19).
- **Numbering.** One-to-one. Pages 1 (title) and 2 (course outline) print no number.
- **Repeats of earlier decks.** The pixel diff at 64px matched only the title background (slide 1,
  0.50 against Lecture 4's page 1) and the course-outline layout (slide 2, 0.50–0.68). Slides 3 and 5–7
  are at 5.1 or more against every earlier page. Slide 3 is not Lecture 6's slide 14 (6.91), though it
  shows the same demo.
- **Slide transcription.** Sonnet, about 1.5 minutes for deck and notes together, `--verify` clean first
  time (7 headings), `check_math.mjs` clean. The parent added to slide 3 what the lecture shows (the run
  played in class, numerical integration error, the 10% inertia and mass runs).
- **Notes transcription.** Sonnet, in the same agent. Three pasted raster drawings (pp. 2, 3, 4), no
  printed figure numbers or captions, numbered `notes-figure-1` to `-3`; `MSAM10` is the ≜ of eqs. (4),
  (13) and the definition of $\tilde{y}$, and there is no `MSBM10`. The parent checked every equation
  against the text layer by span position: eq. (16)'s proportional term is printed $k_p/m$ (the $k$ above
  the $m$ at x = 295), a slip, since eq. (17) and the board (≈1:12:16) need $k_p$. The agent listed two
  further "slips", the $1/m$ of eqs. (14) and (17), which are correct (they come from $\ddot{y} = u_1/m - g$);
  the parent removed them. One inline matrix in a drawing description did not render on github.com and
  was reworded.
- **Figure audit.** Sonnet, one pass at 400–600 dpi over slides 3–6 and the notes' three drawings, also
  at the embedded images' native resolution. Nothing described is absent from the page. Findings:
  - notes figure 1: all three outer curves start at dots and run in to the origin (the file had two
    arrowheads pointing the wrong way); four to five loops, not four;
  - notes figure 2: the dashed circle runs all the way round (not "in pieces"); three to four loops with
    counter-clockwise arrowheads; the "short curve with a dot-like end" is a long line with an arrowhead
    that enters the ball, and the two curves on the right start at dots and leave it;
  - notes figure 3: the vertical axis is solid below the body, with an arrowhead above the dome and a
    dotted line above it;
  - slide 3: the planned path cuts through both obstacles' dashed margins (the file said it passed
    over and below them); the rest, including the printed m = 0.600 kg and J = 0.01500 kg·m², agrees;
  - slides 4, 5 and 6 agree; added the bottom drone's arrow lengths relative to the others.
  The parent viewed the renders of slides 3 and 6 and notes figure 2; they agree with the corrected files.
- **Transcript edit.** Sonnet, about 5 minutes. 98/98 timestamps identical. Every paragraph ratio is in
  0.72–1.10 once `[Ed:]` notes are excluded (11,100 → 10,007 words). Numbers identical paragraph by
  paragraph except two deliberate changes: "y z" → y0 (1:09:54) and a stuttered "x1" (1:11:29). 24
  restoration rows, among them the eight garbles of Lyapunov ("leapono", "the open", "sensibly up andov",
  "the upon" …), "asmtotically" → asymptotically, "the mouse" → the mass (4:02), "next wetness day" →
  next Wednesday, and "u = 2 x2" → negative 2 x2 (1:00:34, on the lecturer's "it doesn't have to be
  negative 2"). Two `[Ed: unclear]`: 29:55 ("N9 the speed of light"; the notes and 34:38 say 0.99) and
  1:02:07 (a garbled student question). Seven notation notes where the captions drop a symbol the notes
  show (21:53 "x = f of x" without the dot; 25:51 no norm; "y dot" for y double dot at 1:05:58, 1:09:07,
  1:10:40 and 1:12:16; "y and y" at 1:09:54). In the parent, the Names section, which said no other name
  was spoken, now names Newton's second law (1:05:58). Lyapunov is printed in the notes; Taylor in
  Lecture 6's.
- **Board versus notes.** The board defines global and local attractivity and then global and local
  asymptotic stability as attractivity plus stability in the sense of Lyapunov (≈20:21–48:46); the notes
  never say "attractivity". The board's local condition was spoken as a strict inequality, "less than r"
  (≈33:52); the notes have $\leq R$. The board's stabilizability needs a feedback controller making the
  system globally asymptotically stable (≈59:47); the notes' eq. (9) only that every state can be driven
  to the fixed point. The board's example first had $x_1 + u$, corrected to $x_2 + u$ (≈54:13), and its
  sign-flipped variant $\dot{x}_ 1 = -x_1$ is on the board only. The wiki follows the notes and gives these.
- **Images rendered (5):** slides 3 (the simulation frame before execution) and 6 (the hover vector field
  with "feedback control law"), and the notes' three drawings (two phase portraits and the planar
  quadrotor). 0.4MB in all; slide 6 came out PNG. Not rendered: the title (1), the course outline (2),
  slide 4 (a stock photograph of an "Uncertainty" road sign beside text), slide 5 (the same figure as 6
  under a different caption) and slide 7 (text in a box).
- **Embedding.** The script put the two slide images into the slide file; the notes drawings were placed
  by hand above their descriptions. The lecture page carries all five, placed by hand with hand-written
  captions; `stability.md` carries notes drawing 2 and `feedback-control.md` slide 6. Captions carry no
  `$` math. Questions in the Lyapunov section were first written as italic lead-ins containing math,
  which GitHub does not render; they are bold or plain now.
- **Wiki.** Two new concept pages, `stability.md` and `feedback-control.md`. Lecture 5's page said model
  predictive control would be touched on in the next lecture and Lecture 6's did not; it comes up in
  Lecture 7's Q&A as receding horizon control (≈10:06–11:40), and Lecture 5's page and the
  trajectory-optimization page now say so. Phrases of mine taken out of the drafts before the check: that
  a student had asked about using trajectory optimization for feedback (the captions do not show a
  question), a lower-case $r$ on the board (captions cannot show case), and that linear feedback design
  starts from the linearization (the course has not said so).
