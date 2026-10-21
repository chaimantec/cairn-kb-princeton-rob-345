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
- [ ] 09 copy-edit (Sonnet), checked in the parent: timestamps, numbers, ratios, proper nouns

### Slides and notes
- [x] Download Lecture9_slides.pdf (21 pages, 32MB, Keynote, 2026-10-01) and Lecture9_notes.pdf (5 pages, pdfTeX, four pasted drawings) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (21 pages); pages 1 and 2 print no number. Pixel diff: nothing repeats an earlier deck (slide 1 matches the title background only, 0.60); within the deck slide 20 is slide 6 again (0.75)
- [x] raw/slides/09-optical-flow.md (Sonnet), --verify clean (21 headings); check_math --github clean
- [x] raw/notes/09-optical-flow.md (Sonnet); (1)–(5) and every display agree with the text layer in the parent; slips: "Lecture #18" (page 1 header only, corrected from the agent's "every page"), "determininat", "(x+u, x+v)" in drawing 2 (seen in the render)
- [x] Figure audit (Sonnet), slides 3, 5–8, 15, 17–19, the four notes drawings and the p. 4 matrix display, crops at 300–600 dpi: nothing described is absent; slides 3, 7, 15, drawings 1 and 4 and the matrix agree; fixed the road direction on slides 5 and 19 (upper left, not right) and slide 19's vehicles, slide 6's column and panel arrows plus a whole-field summary, slide 8's right-frame arrows (trailing), slide 17's box position, slide 18's inset line, drawing 3's angles. The audit's "(u, x)" for drawing 2's displacement label overruled by a crop in the parent ("(u, v)"); renders of slide 6 and drawing 2 viewed in the parent

### Wiki
- [ ] wiki/09-optical-flow.md
- [ ] Topic pages and cross-links
- [ ] INDEX.md table of contents, coverage paragraph

### Images
- [ ] raw/images/09-optical-flow/ — render, embed in the slide file, notes file and wiki
- [ ] INDEX.md image sentence; AGENTS.md table row; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, notes, images, figureAudit, caveats
- [ ] sources.md "In this KB" column
- [ ] BUILD_LOG.md — the lecture's record
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Older lines this run completes
- [ ] Lecture 9 (Optical Flow), one run: transcript, deck (Dropbox, `dl=1`), notes, copy-edit, figure audit,
      wiki page, images. Lecture 9 also posts a notes PDF; transcribe it to raw/notes/ (AGENTS.md, Course materials).
