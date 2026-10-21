# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 9 — Lecture 9 (Optical Flow), 2026-10-21

Scope: lecture 9 only. Settings carried from runs 1–8: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures; creator check passed.
Ticks the "Later runs — lecture 9" line.

### Transcripts
- [x] 09 Lecture 9: Optical Flow — video wvuVX9L7v4Y — verbatim captions in raw/transcripts/original/ (89 paragraphs, 9,954 words)
- [x] 09 copy-edit (Sonnet), checked in the parent: 89/89 timestamps identical; numbers identical paragraph by paragraph except two "2"s spoken as "squared" at 1:01:28 (listed); every ratio in 0.72–1.10 with [Ed:] notes and student tags excluded (9,830 → 8,601 words; lowest 0.727 at 1:06:04); 24 restoration rows, 7 [Ed: unclear], 8 notation notes; Lucas-Kanade, Taylor, RRT printed in the material; Queensland Brain Institute, Australian National University and "Partha" confirmed in the raw captions (the bird video's narration), the surname left unclear

### Slides and notes
- [x] Download Lecture9_slides.pdf (21 pages, 32MB, Keynote, 2026-10-01) and Lecture9_notes.pdf (5 pages, pdfTeX, four pasted drawings) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (21 pages); pages 1 and 2 print no number. Pixel diff: nothing repeats an earlier deck (slide 1 matches the title background only, 0.60); within the deck slide 20 is slide 6 again (0.75)
- [x] raw/slides/09-optical-flow.md (Sonnet), --verify clean (21 headings); check_math --github clean
- [x] raw/notes/09-optical-flow.md (Sonnet); (1)–(5) and every display agree with the text layer in the parent; slips: "Lecture #18" (page 1 header only, corrected from the agent's "every page"), "determininat", "(x+u, x+v)" in drawing 2 (seen in the render)
- [x] Figure audit (Sonnet), slides 3, 5–8, 15, 17–19, the four notes drawings and the p. 4 matrix display, crops at 300–600 dpi: nothing described is absent; slides 3, 7, 15, drawings 1 and 4 and the matrix agree; fixed the road direction on slides 5 and 19 (upper left, not right) and slide 19's vehicles, slide 6's column and panel arrows plus a whole-field summary, slide 8's right-frame arrows (trailing), slide 17's box position, slide 18's inset line, drawing 3's angles. The audit's "(u, x)" for drawing 2's displacement label overruled by a crop in the parent ("(u, v)"); renders of slide 6 and drawing 2 viewed in the parent

### Wiki
- [x] wiki/09-optical-flow.md (derivation cited to the notes, board differences with timestamps; 13 images, every caption hand-written)
- [x] Topic pages: new wiki/optical-flow.md (with slide 6 and notes drawing 3); crazyflie, sense-think-act, uncertainty, feedback-control Lectures entries; course-map row; Lecture 1 and 8 forward links
- [x] INDEX.md table of contents (lecture page, concept page), coverage paragraph (all 9 recorded lectures), raw/slides, raw/notes and raw/images entries, citation rule

### Images
- [x] raw/images/09-optical-flow/ — slides 3–8, 15, 17, 18 and notes drawings 1–4 (1.5MB), embedded in the slide file (script), the notes file (by hand, above each description), the lecture page (all 13, by hand) and optical-flow.md (two)
- [x] INDEX.md image sentence; AGENTS.md table row and one lesson in general form (settle a handwritten-label slip from a crop in the parent); LICENSE.md attribution, and its licence-check sentence brought up to Lectures 1–9

### Publish
- [x] kb.json — coverage, byLecture, notes, images, figureAudit, caveats; the PNG count corrected to thirteen (it read "nine", stale before this run)
- [x] sources.md "In this KB" column
- [x] BUILD_LOG.md — the lecture's record (below, moved with this section)
- [x] verify_kb.py clean (all hard checks; 2,640 formulas in the chat and on github.com), and its review section read: no ranking claims, 107 images = 91 slides + 16 notes figures, 13 on disk and 13 in the wiki for Lecture 9
- [x] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Older lines this run completes
- [x] Lecture 9 (Optical Flow), one run: transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lecture 9 also posts a notes PDF; transcribe it to raw/notes/ (AGENTS.md, Course materials).

### Lecture 9 record

- **Deck and notes.** `Lecture9_slides.pdf` from Dropbox, 21 pages, 32MB, exported from Keynote on
  2026-10-01, titled "Lecture 9: Optical Flow", and `Lecture9_notes.pdf`, 5 pages, pdfTeX output of the
  same date. Neither text layer has a licence or copyright notice. The deck opens the second module
  (slide 2), asks how the drone localized itself in the RRT lab (slide 3), motivates optical flow with
  pictures, questions and three videos (slides 4–13), hands over to the blackboard (14), shows the barber
  pole illusion (15) and the Lucas-Kanade failure cases (16–18), and closes on imperfect sensing
  (19–21). The derivation was done on the blackboard, so the notes were transcribed and the wiki cites
  them. The notes number (1)–(5); the lecture speaks "equation one", "two" and "three" (≈25:15,
  ≈27:36, ≈39:16), matching, and never numbers (4) or (5).
- **Numbering.** One-to-one. Pages 1 (title) and 2 (course outline) print no number.
- **Repeats.** The pixel diff at 64px matched no page to an earlier deck: slide 1 matches only the
  shared title background (0.60), slide 2's outline is a new layout (14.2), slide 12's black frame is
  closest to Lecture 6's slide 18 (7.9, both dark video frames). Within the deck, slide 20 is slide 6
  again (0.75 at 128px) and slide 21 that picture faded; slide 19 is a second frame of slide 5's video
  (8.2). The three video URLs appear in no earlier slide file.
- **Slide transcription.** Sonnet, deck and notes in one agent, about 3 minutes, `--verify` clean first
  time (21 headings), `check_math.mjs --github` clean. The parent added to slides 5–7, 11, 12, 15 and
  19 what the lecture says about them (the videos as played; the answer to slide 6's question).
- **Notes transcription.** Sonnet, in the same agent. Four pasted raster drawings (pp. 1, 2, 3, 5), no
  printed numbers or captions, numbered `notes-figure-1` to `-4`; `MSAM10` is the ≜ of p. 4. Every
  display agrees with the text layer, including (1)–(5). The agent wrote that every page header reads
  "Lecture #18"; the text layer has the header line on page 1 only, and the file was corrected. Slips:
  "Lecture #18" (p. 1), "determininat" (p. 5), and drawing 2's label "(x+u, x+v)" for (x+u, y+v). No
  equation slip; the agent's substitution of (2) into (1) gives (3), checked.
- **Figure audit.** Sonnet, one pass with crops at 300–600 dpi over slides 3, 5–8, 15 and 17–19, the
  four drawings and the p. 4 matrix display. Nothing described is absent from the page. Findings:
  - slides 5 and 19: the road recedes to the upper left, not the upper right; slide 19 has one van at
    the bottom edge, not two;
  - slide 6: the white column's arrows point down-right only at y 110–150 and up-right below; the dark
    panel spans y 160–250 with a chevron of arrowheads near (88, 185); a whole-field summary added (most
    arrows right or up-right, longest on the near wall, converging near the panel); the faint pink text
    begins "Sa…" and is not legible in full;
  - slide 8: in the right frame each arrow trails behind its disc, head at the disc;
  - slide 17's box is about four-fifths across, not three-fifths; slide 18's inset line repositioned;
  - drawing 3's arrow angles tightened;
  - slides 3, 7 and 15, drawings 1 and 4 and the matrix display agree, including every arrow's
    direction in drawings 1 and 2 and on slide 8.
  The audit read drawing 2's displacement label as "(u, x)". The parent's 300 dpi crop shows "(u, v)", its
  v drawn with the same crossed stroke as the v of "x+v", while the x's of the drawing are two arcs;
  only "(x+u, x+v)" is listed. The parent also viewed the renders of slide 6 and drawing 2.
- **Transcript edit.** Sonnet, about 4.5 minutes. 89/89 timestamps identical. Every paragraph ratio is in
  0.72–1.10 with `[Ed:]` notes and student tags excluded (9,830 → 8,601 words; lowest 0.727 at
  1:06:04). Numbers identical paragraph by paragraph except two "2"s spoken as "squared" at 1:01:28,
  listed. 24 restoration rows, among them "Lucas Canad", "locus can" → Lucas-Kanade, "tailor" → Taylor,
  "RT" → RRT, "barberhop" → barber pole and "single point lighter" → single-point lidar. Seven
  `[Ed: unclear]`: the researcher's surname in the bird video (13:13, "Buckavatula"), a student's answer
  (29:58), two student questions (35:20, 45:26), "the map" (41:35), the last word of the window-size
  question (55:05) and the student's answer naming the edge case (1:02:59). Eight notation notes. The
  two videos' narration is untagged, as the header says. In the parent, Queensland Brain Institute,
  Australian National University and "Partha" were confirmed in the raw captions.
- **Board versus notes.** The lecture calls the first assumption intensity constancy (≈22:43); the notes
  say "Color and Intensity constancy" (p. 1) and "Brightness constancy assumption" (p. 2). The board
  moved $I_t$ to the right of eq. (3) (≈33:46, ≈40:04). The notes' "dates from ~1981" and the numpy /
  Assignment 1 margin note are not spoken. The spoken least-squares solution is garbled (≈57:26) and the
  determinant loses its sums (≈1:01:28). At ≈1:05:18 the lecture calls the edge failure motion "aligned
  with all the image gradients"; by the notes' p. 3 derivation it is motion perpendicular to them, and
  the wiki's Gaps section says so.
- **Images rendered (13):** slides 3 (the RRT-lab path, PNG), 4 (the Flow deck photograph), 5 and 6 (the
  two flow fields), 7 (the homework diagram, PNG), 8 (the pixel-motion diagram), 15 (the barber pole
  frame), 17 and 18 (low texture and edge), and the notes' four drawings. 1.5MB in all. Not rendered: the
  title (1), the outline (2), text-only slides 9, 10 and 14, slide 11 (only a link), slide 12 (a black
  video frame), slide 13 (a news-article screenshot whose text is transcribed), slide 16 (the photograph
  17 and 18 mark up), slide 19 (a second frame of slide 5's video), slide 20 (slide 6 again) and slide 21
  (slide 6 faded behind text).
- **Embedding.** The script put the nine slide images into the slide file; the notes drawings were placed
  by hand above their descriptions. The lecture page carries all thirteen, by hand, with hand-written
  captions and no `$` math in them; `optical-flow.md` carries slide 6 and notes drawing 3.
- **Wiki.** One new concept page, `optical-flow.md`. Removed from the drafts before the checks: a caption
  calling the drone on slide 4 "the course drone" (the slide shows a Crazyflie, not necessarily one of the
  course's); "the rest greys out" for the lecture's "once it grays out"; a sentence attributing the
  jitter of the flow video to Lucas-Kanade (the lecture does not say which method made it).

