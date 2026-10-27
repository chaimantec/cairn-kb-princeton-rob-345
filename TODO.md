# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 10 — Lecture 10 (Nondeterministic Filter), 2026-10-28

Scope: lecture 10 only. Settings carried from runs 1–9: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-28: 11 lectures (10 "Nondeterministic
filter", 11 "Bayes filter"); creator check passed. The course site posts a video and notes for
Lecture 10 and no slide deck: the lecture was given at the board.

### Transcripts
- [x] 10 Lecture 10: Nondeterministic filter — video T7Uf2u3VVZ8 — verbatim captions in raw/transcripts/original/ (84 paragraphs)
- [x] 10 copy-edit (Sonnet), checked in the parent: 84/84 timestamps identical; numbers identical paragraph by paragraph; every ratio in 0.72–1.10 with [Ed:] notes and tags excluded (9,092 → 8,190 words; lowest 0.803 at 1:00:06) except 1:04:47, which is only the closing music mark; 6 restoration rows, 3 [Ed: unclear], 1 notation note; header fixed in the parent (no LaTeX, the names sentence, a continuation tag at 42:16, "Bayes filter" confirmed by the site's schedule)

### Notes
- [x] Download Lecture10_notes.pdf (6 pages, pdfTeX, 2026-10-06, nine pasted drawings) into raw/pdfs/ (gitignored); no deck posted
- [x] raw/notes/10-nondeterministic-filter.md (Sonnet); every display checked against the text layer in the parent (fonts of X and Z, the braces of the p. 3 dynamics display and its two arrows, the lowercase x-hat of p. 4); underline tags removed; check_math --github clean
- [x] Figure audit of the nine drawings (Sonnet), 400–1500 dpi crops: drawings 3 and 8 agree; corrections to 1, 2, 4, 5, 6, 9; drawing 7's arrow left as "most plausibly points at the state"; drawing 5's label and drawing 9's handwriting settled in the parent from the renders

### Wiki
- [x] wiki/10-nondeterministic-filter.md (follows the notes, cited by page; board differences with timestamps; 9 images, every caption hand-written)
- [x] Topic pages: new wiki/state-estimation.md (with notes drawing 5); uncertainty, sense-think-act, state-and-dynamics, stability, optical-flow Lectures entries; course-map rows 10 and 11 and its intro; Lecture 1 and 9 forward links
- [x] INDEX.md table of contents (lecture page, concept page), coverage paragraph (10 of 11 recorded lectures), raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/10-nondeterministic-filter/ — the notes' nine drawings (0.4MB), cropped at 1400px, placed by the transcription above each description and by hand in the wiki (all nine) and state-estimation.md (one)
- [x] INDEX.md image sentence; AGENTS.md table row and one lesson in general form (a lecture with notes and no deck; a "(1)" in notes prose may number a list); LICENSE.md attribution and its licence-check sentence brought up to the Lecture 10 notes

### Publish
- [x] kb.json — coverage (10 of 11), byLecture, notes 7/7, images 116 in 10 lectures, figureAudit note, a Lecture 10 caveat, the coverage caveat rewritten
- [x] sources.md rows 10 and 11, inventory sentence
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 3,010 formulas in the chat and on github.com, after one `>` became `\gt`), and its review section read: no ranking claims, 116 images = 91 slides + 25 notes figures, 9 on disk and 9 in the wiki for Lecture 10
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Older lines this run completes
- [x] Lectures 10 onward. Blocked: on 2026-10-21 the catalog holds 9 recorded lectures and the course
      site had posted materials only for lectures 1–9. When the catalog re-syncs, diff its lectures
      against raw/transcripts/ and add one line per new lecture here.

### Lecture 10 record

- **Material.** No deck: the course site's Lecture 10 row links a video and `Lecture10_notes.pdf` only.
  The notes are 6 pages of pdfTeX output (2026-10-06) with nine pasted raster drawings; no licence or
  copyright notice. The lecture was given entirely at the board. The notes print no equation numbers;
  the "(1)" and "(2)" of page 1 number two goals. Fonts: the state and measurement spaces are CMSY10
  (calligraphic), the set estimates CMMI12 X with a hat, ℝ MSBM10, ≜ MSAM10.
- **Notes transcription.** Sonnet, about 3 minutes, `check_math.mjs --github` clean. The agent wrote
  underlining as `<u>` tags, which no other notes file uses; removed in the parent. The p. 3 dynamics
  display: the text layer shows a CMEX `\bigg\{` opening and a `\Big\}` closing, and two small arrows
  rising from "[We will ignore control inputs for now]" to $\bar{u}_ t$ and to the second form; the
  description was corrected to say so. Slips: "Lecture #11" (p. 1 header); "our new estimate x̂₁"
  with a lowercase x (CMMI12 in the text layer, p. 4); drawing 5's label "f(x̂₀)"; drawing 9's
  "accont". No equation slip (step 3 at t = 1 reproduces the p. 4 display for X̂₁).
- **Figure audit.** Sonnet, crops at 400–1500 dpi. Nothing described was absent. Drawings 3 and 8 agree.
  Fixed: tick marks on the axes of drawings 1 and 2; the position of "s" in drawing 2 (up and left of
  its arrow); drawing 4's label (subscript loop, not a tail to the blob) and each arrow's ending (open
  arrowheads; heads and dots inside or just outside the right blob); drawing 5's connector (faint,
  dotted); drawing 6's dots (three, inside the narrow blob) and outlines (all solid). Drawing 7's thick
  stroke is "most plausibly" a "<" at the state (about 65%), against the text's meaning (the state
  leads to the set); the notes file and the wiki's Gaps say so and the caption gives the text's
  meaning. The audit read drawing 5's x as lowercase at about 75%; the parent's view of the render
  agrees (two arcs, as this hand writes a lowercase x; the capital X̂₀ beside it is a bold straight
  cross). Drawing 9: "have" is handwriting (the h closed into a loop), not listed; "accont" is listed,
  the missing letter not settled. Renders of drawings 5, 7 and 9 viewed in the parent.
- **Transcript edit.** Sonnet, about 3.5 minutes. 84/84 timestamps identical, numbers identical
  paragraph by paragraph. Ratios in band except 1:04:47 (only `>> [music]`); lowest real ratio 0.803
  (1:00:06). Restorations: "pre-image" → preimage, "base filter" → Bayes filter (confirmed by the course
  site's "Lecture 11: Bayes filtering"), "base rule" → Bayes rule, a stray "X" before "F of X0 hat",
  "access" dropped as a mis-hearing. Three `[Ed: unclear]`: the end of a student question (30:26), a
  student's answer (32:55), what "it" is in "let's say it's larger than 1" (48:30). One notation note:
  the third sensor's distance formula without squares (15:47). The parent removed LaTeX from the
  header, corrected "No person's name is spoken" (Bayes, Euler and Gaussian are), and added
  `*[Student answer, continued]*` at 42:16, which the header described but the text lacked.
- **Board versus notes.** The board names the distances R1, R2 (R3) and the measurement space R^D; the
  notes use r and s and only R³. The board calls steps 2 and 3 together the measurement update (≈39:10);
  the notes call step 3 "Fuse information from 1. and 2.". Spoken only: "triangulation", the 1D unstable
  example x_{t+1} = λx_t with the interval [−ε, ε], the no-sensor sensor, the polytope and
  discretization answers, and the Bayes filter preview. The notes use x̄₀ both for the sensor point
  (1, 1) and for a state in X̂₀.
- **Images rendered (9):** all nine notes drawings, 0.4MB, cropped at the image rectangles plus 6pt
  and scaled to 1400px. Drawing 7 is a 98-point-wide raster, so its crop is upscaled about 5×.
- **Wiki.** One new concept page, `state-estimation.md`, a hub for the module's filters. Removed from
  the draft before the checks: a gendered pronoun for the lecturer (now "Majumdar may spend some time on
  them"); `$\lambda > 1$` written `\gt` for github.com.

## Later runs

- [ ] Lecture 11 (Bayes filter), video mno8-hG7tJc: transcript, notes (`Lecture11.pdf` on Dropbox,
      linked as "Notes"; no deck posted on 2026-10-28), copy-edit, figure audit, wiki page, images.
- [ ] Lectures 12 onward. On 2026-10-28 the catalog holds 11 recorded lectures. When it re-syncs, diff
      its lectures against raw/transcripts/ and add one line per new lecture here.
