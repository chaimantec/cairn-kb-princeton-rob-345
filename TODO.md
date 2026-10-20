# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lectures 3–9

- [ ] Lectures 3–9, one per run: transcript, deck (Dropbox, `dl=1`), copy-edit, figure audit, wiki
      page, images. Lectures 4–9 also post notes PDFs; decide whether to transcribe them.

## Run 3 — Lecture 3 (RRTs), 2026-10-21

Scope: lecture 3 only. Settings carried from runs 1–2: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures.

### Transcripts
- [x] 03 Lecture 3: Rapidly Exploring Randomized Trees (RRTs) — video KDIe1094FMo — verbatim captions in raw/transcripts/original/ (92 paragraphs, 12,152 words incl. header)
- [ ] 03 copy-edit (Sonnet), checked: timestamps, numbers, ratios, proper nouns

### Slides
- [x] Download Lecture3.pdf (Dropbox dl=1, 9.4MB, 62 pages) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (62 pages); pages 1 and 2 print no number
- [ ] raw/slides/03-rrts.md (Sonnet), --verify clean
- [ ] Figure audit of six figure-heavy pages (Sonnet)

### Wiki
- [ ] wiki/03-rrts.md
- [ ] Topic pages: new or extended (sampling-based planning?); course-map row; cross-links
- [ ] INDEX.md table of contents and coverage paragraph

### Images
- [ ] raw/images/03-rrts/ — pick from the slide file, render, embed, hand-written captions
- [ ] INDEX.md image sentence; AGENTS.md table row; BUILD_LOG.md record; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, images, figureAudit, caveats
- [ ] sources.md "In this KB" column
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work
