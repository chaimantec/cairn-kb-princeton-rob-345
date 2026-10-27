# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 11 — Lecture 11 (Bayes Filter), 2026-10-28

Scope: lecture 11 only. Settings carried from runs 1–10: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-28: 11 lectures (11 "Lecture 11: Bayes
filter", video mno8-hG7tJc, 4,596 s); creator check passed. The course site's Lecture 11 row links a video
and `Lecture11.pdf` (as "Notes"); no slide deck. Lecture 12 (Kalman filtering and particle filtering) and
later rows have no links yet.

### Transcripts
- [x] 11 Lecture 11: Bayes filter — video mno8-hG7tJc — verbatim captions in raw/transcripts/original/ (98 paragraphs, 10,932 words with header)
- [x] 11 copy-edit (Sonnet), checked in the parent: 98/98 timestamps identical; every ratio in 0.72–1.10 with [Ed:] notes and tags excluded (10,799 → 9,922 words; lowest 0.814, highest 1.00); numbers differ only by restored decimal points (23 paragraphs, e.g. "6" → 0.6, "75.25" → 0.75, 0.25), each checked against the notes; 13 restoration rows, 3 [Ed: unclear], 1 [Ed: slip]; restored names: Bayes in the notes, Kalman, Gaussian and Monte Carlo spoken only; 54:32 re-tagged in the parent as an inaudible student answer

### Notes
- [x] Download Lecture11.pdf (4 pages, pdfTeX, 2021-10-10, two pasted drawings) into raw/pdfs/ (gitignored); no deck posted
- [x] raw/notes/11-bayes-filter.md (Sonnet); every display checked against the text layer in the parent (the four overlined beliefs found as drawn rules; the underscores of is_open as 3.5pt rules; "-=" and "ff" as printed glyphs; the full-size "−1" of the p. 4 dynamics model); `\\` → `\cr`, `>` → `\gt`, box items and one "and" fixed; check_math --github clean
- [x] Figure audit of the two drawings (Sonnet), 500–1500 dpi crops: nothing absent or missing; fixed the case of drawing 1's hatted x (lowercase, settled in the parent from a crop against the bracket's x̄), drawing 2's lowercase "corre", the curve round the box's left end, dot counts. Equations were checked against the text layer in the parent instead

### Wiki
- [x] wiki/11-bayes-filter.md (follows the notes, cited by eq. and page; board differences with timestamps; 2 images, both captions hand-written)
- [x] Topic pages: new wiki/probability.md; state-estimation.md (intro, a Bayes filter section, the LQR-with-a-set point, Lectures list); uncertainty, sense-think-act, state-and-dynamics, stability, lqr Lectures entries; course-map row 11; Lecture 1, 9 and 10 forward links; course-logistics probability line
- [x] INDEX.md table of contents (lecture page, probability page, state-estimation line), coverage paragraph (all 11 recorded lectures), raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/11-bayes-filter/ — the notes' two drawings, cropped at the image rectangles plus 6pt, 1400px (0.1MB)
- [x] Placed in raw/notes/ (by the transcription, above each description) and by hand in the wiki
- [x] INDEX.md image sentence; AGENTS.md table row and two lessons in general form (overlines and underscores are drawn rules the text layer drops; captions drop decimal points); LICENSE.md attribution and its licence-check sentence brought up to the Lecture 11 notes

### Publish
- [x] kb.json — coverage (11 of 11), byLecture, notes 8/8, images 118 in 11 lectures, figureAudit note, a Lecture 11 caveat, the coverage caveat rewritten
- [x] sources.md row 11
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 3,368 formulas in the chat and on github.com), and its review section read: no ranking claims, 118 images = 91 slides + 27 notes figures, 2 on disk and 2 in the wiki for Lecture 11
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 11 record

- **Material.** No deck: the course site's Lecture 11 row links a video and `Lecture11.pdf` ("Notes")
  only. The notes are 4 pages of pdfTeX output dated 2021-10-10 (older than the other notes, which are
  2026), with two pasted raster drawings and no licence or copyright notice. They number five equations:
  (1) Bayes' rule on p. 1, (2)–(3) its proof and (4)–(5) the door example's belief on p. 2. The "(1)",
  "(2)", "(3)" of the p. 1 recap and the "1.", "2." of the p. 4 box are list items. Fonts: bel is CMR12
  (upright), the random variables CMMI12 capitals, ≜ MSAM10.
- **Text layer.** The four overlined beliefs (p. 3 Step 1's left side; on p. 4 the underbrace label and
  both lines of the box) are drawn rules over "bel", absent from the text; found with `get_drawings()` and
  handed to the agent. The door's values (is_open, sense_closed) carry a 3.5pt drawn underscore. Item (3)
  of the recap prints "-=" (CMR12 hyphen and equals); the independence line prints the ligature "ff" with
  no i; the p. 4 dynamics model prints "−1" in CMSY10/CMR12 at full size after Ū_t.
- **Notes transcription.** Sonnet, about 1 minute. Fixed in the parent: three `aligned` blocks' `\\` →
  `\cr`, one `>` → `\gt`, three inline formulas after a quote mark, the p. 4 box's invented "Dynamics
  update:" labels, an "and" moved out of a display. Slips (all listed in the file): "Lecture #12",
  "Insturctor", "-=", "ff", "out estimate", "ti the text", "alao", "as out", "the robot sense", "Bayes's"
  beside "Bayes'", the unbarred predicted belief in two p. 3 sentences, the capital P of one p. 4
  denominator, the lowercase x₂ under the p. 4 underbrace, "Ū_t − 1", drawing 1's lowercase x̂₀, drawing
  2's "corre spods". No arithmetic slip: 0.75, 0.95, 0.983 and their complements checked by substitution.
- **Figure audit.** Sonnet, crops at 500–1500 dpi. Nothing described was absent, nothing visible missing.
  Fixed: drawing 1's three hatted labels are a lowercase x (the parent's crop compared them with the
  bracket's x̄ₜ₊₁ and x̄ₜ: the same two-arc letter at the same height), dot counts, the arrowhead's end;
  drawing 2's lowercase c of "corre", the curve round the box's left end. "spods" (no n, a gap after
  "corre") was read the same way in the parent's crop and by the audit. The z of z̄ is drawn with a
  crossbar and read as lowercase, with low confidence.
- **Transcript edit.** Sonnet, about 3.5 minutes. 98/98 timestamps identical; ratios 0.814–1.00. The number
  diff showed 23 paragraphs, every difference a restored decimal ("6" → 0.6, "04" → 0.4, "75.25" → 0.75,
  0.25, "0 983" → 0.983, the board's coin 0.7 and 0.3). Restorations: Bayes filter and Bayes rule (with
  "Bayes's" at 3:06 and 30:22), Kalman, probabilistic, *Probabilistic Robotics*, a priori, state of the
  world, preimage, "I erased it" (33:31), "Should it be" (1:11:51). `[Ed: unclear]` at 25:37 (a student's
  answer), 53:44 (a third "25"), 1:11:05; `[Ed: slip, see 17:56]` at 16:23 ("times P of X" for "divided
  by"). Six inaudible-student markers inserted; the one at 54:32 was a `*[Student answer]*` on "Yeah. More
  confident." and was changed in the parent, since that reads as the lecturer repeating the answer.
  Kalman, Gaussian and Monte Carlo are spoken only.
- **Board versus notes.** The board's coin is biased (0.7, 0.3), the notes' fair; the board writes Bayes
  rule as p(y|x) = p(x|y)p(y)/p(x); the board drops "is" (≈31:56) and says "Z1 equals is open" (≈28:51); the
  general filter is in lowercase on the board. Two board slips corrected in class: p(x_{t−1}) for
  bel(x_{t−1}) in the dynamics update (≈1:08:46) and P(X_t|Z_t) for the sensor term, caught by a student
  (≈1:11:51). Notes only: the three issues of the nondeterministic filter and the LQR question, the
  textbook's dynamics convention, Section 2.4.3.
- **Images rendered (2):** both notes drawings, 0.1MB, cropped at the image rectangles plus 6pt and scaled
  to 1400px. Both in the wiki with hand-written captions; drawing captions avoid inline math (github.com
  does not render math inside italics).
- **Wiki.** One new concept page, `probability.md`, since the refresher is the course's probability
  reference for the filtering lectures ahead. A summary table of the door example's four beliefs was added
  to the lecture page.

### Older lines this run completes
- [ ] Lecture 11 (Bayes filter), video mno8-hG7tJc: transcript, notes (`Lecture11.pdf` on Dropbox,
      linked as "Notes"; no deck posted on 2026-10-28), copy-edit, figure audit, wiki page, images.

## Later runs

- [ ] Lectures 12 onward. On 2026-10-28 the catalog holds 11 recorded lectures. When it re-syncs, diff
      its lectures against raw/transcripts/ and add one line per new lecture here.
