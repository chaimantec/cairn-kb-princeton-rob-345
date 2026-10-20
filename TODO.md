# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 1 — Lecture 1 (Intro to Robotics), 2026-10-20

Scope: lecture 1 of 9 in the catalog manifest (the course site lists 24). Slide
images opted in; PDFs link-only. Commit as chaimantec <nantapon@chaimantec.com>.

### Transcripts
- [x] 01 Lecture 1: Intro to Robotics — video cMhFAq53v1c — verbatim captions in raw/transcripts/original/
- [x] 01 copy-edit (Sonnet): 74/74 timestamps identical, no number lost, no ratio outlier; 41 restorations, 10 [Ed: unclear]; proper nouns grepped against the slides

### Crawl
- [x] Fetch course site index: https://irom-lab.princeton.edu/intro-to-robotics/ (single page; all materials on Dropbox)
- [x] Download Lecture1.pdf (Dropbox, 75MB, 57 pages) into raw/pdfs/ (gitignored)
- [x] Write sources.md (hand-written by lecture; the generated table filed course decks under "papers")

### Slides
- [x] Slide number map: printed 2 absent (hidden slide), pages 2–56 print page+1; pages 1, 4–7, 32, 38, 57 print none
- [x] raw/slides/01-intro-to-robotics.md (Sonnet), --verify clean (57 headings)
- [x] Figure audit of six figure-heavy pages (Sonnet): 4 agree; fixed slide 8 (ROBOTIQ legible) and slide 15 (Waymo/Lyft crossing, two Uber values)

### Wiki
- [ ] wiki/01-intro-to-robotics.md
- [ ] Topic pages (cross-lecture concepts the lecture introduces)
- [ ] INDEX.md table of contents

### Images
- [ ] raw/images/01-intro-to-robotics/ — pick from slide file + raster test, render, embed in the wiki and slide files
- [ ] INDEX.md — the chat's image rules; AGENTS.md — the Images conventions and table row; BUILD_LOG.md — what was rendered and why; LICENSE.md — attribution

### Publish
- [ ] kb.json — coverage, materials.method, provenance caveats
- [ ] BUILD_LOG.md — the lecture's record: notices, audit findings, printed slips, transcript edits
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] PATCH kbUrl onto the catalog entry
- [ ] Move this run's finished sections to BUILD_LOG.md; TODO.md keeps only open work
