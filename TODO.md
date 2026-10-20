# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 2 — Lecture 2 (Discrete Motion Planning), 2026-10-20

Scope: lecture 2 only. Settings carried from run 1: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-20: still 9 lectures.

### Transcripts
- [x] 02 Lecture 2: Discrete Motion Planning — video LhLd8Kon1GY — verbatim captions in raw/transcripts/original/
- [x] 02 copy-edit (Sonnet): 97/97 timestamps identical; ratios all in band (lowest 0.74 at 15:39); number diffs all coordinate pairs restored from captions ("22 412" -> (2, 2), (1, 4), (1, 2)), "C3" -> C free, and false starts; 46 restorations, 15 unclear; proper nouns grepped (LaValle, AlphaFold, SE2 not in the deck: Lecture 1 slide 55, spoken aside, student answer)

### Slides
- [x] Download Lecture2.pdf (Dropbox dl=1, 14MB, 79 pages) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (79 pages); pages 1, 3, 4 print no number
- [x] raw/slides/02-discrete-motion-planning.md (Sonnet), --verify clean (79 headings)
- [x] Figure audit of seven figure-heavy pages (Sonnet): 24, 33, 45, 63 agree; 56 red set listed in full, 73 label position, 24 hedge dropped. Printed slip noted on 73 (tie-break by H with equal H)

### Wiki
- [x] wiki/02-discrete-motion-planning.md
- [x] Topic pages: configuration-space, graph-search; course-map row; cross-links from sense-think-act, uncertainty and the Lecture 1 page
- [x] INDEX.md table of contents and coverage paragraph

### Images
- [x] raw/images/02-discrete-motion-planning/ — 22 slides rendered (2.2MB), embedded in the slide file, the lecture page and both topic pages; 16 hand-written captions
- [x] INDEX.md image sentence; AGENTS.md table row and three general lessons; BUILD_LOG.md record (below); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, images, figureAudit, caveats
- [x] BUILD_LOG.md — lecture 2 record (below, moves with this section); index row added at the move
- [x] sources.md "In this KB" column
- [x] verify_kb.py clean (all hard checks; 284 formulas in chat and on github.com), and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 2 record

- **Deck.** `Lecture2.pdf` from Dropbox, 79 pages, 14MB. The text layer has no licence or copyright
  notice, and none is on the course site. Third-party material is credited only on slides 9 (Zoox)
  and 10 (Parasol Lab URL); slides 7, 11 and 19 give YouTube URLs. LICENSE.md lists what it can.
- **Numbering.** One-to-one. Pages 1, 3 and 4 (the title page and two topic maps) print no number.
  Slide 62's "62" is in the text layer but not visible on the page.
- **Transcription.** Sonnet, about 3 minutes; `--verify` clean first time (79 headings). PyMuPDF
  was not importable from the agent's shell, so it used `pdftotext` for text-layer checks. It
  flagged slides 24, 33, 44–46, 53–59, 73–74, 62 and 76 for a second reader.
- **Figure audit.** Sonnet, on slides 24, 33, 45, 56, 63, 73 and 76. All agreed in substance, with
  no invented content. Slide 24's path, which the file called "approximate by a cell at the
  turns", is exact at 600 dpi (the hedge was false again). Slide 56's red set was given as "as on
  slide 55 plus (3,5)" and is now listed in full. One label position on slide 73 was corrected.
  The agent viewed most pages at 200 dpi and cropped to 600 dpi only for 33 and 76. The renders of
  slides 46 and 74 were also checked in the parent, and both agree.
- **Printed slip.** Slide 73 says "tie in F broken by smaller H", but both tied vertices have H = 6.
  The lecturer notices this in class (≈1:06:01–1:06:47). The slide file has an `[Ed:]` note and the
  wiki says so.
- **Spoken slips.** At ≈40:35 the start is given as (1, 1), corrected at ≈41:21 to (2, 3). At ≈44:25
  (2, 2) is said not to be in the queue yet, when it is. The wiki follows the slides.
- **Animations.** Slides 62 and 76 are animations in the lecture. The PDF holds one early frame,
  which is why both of slide 76's counters read "expanded: 4". Both slide entries say so.
- **Transcript edit.** Sonnet, 97/97 timestamps identical, every paragraph ratio in 0.72–1.10
  (lowest 0.74 at 15:39; 12,909 → 11,171 words). It made 46 restorations and left 15 unclear marks.
  The number diffs are all deliberate:
  - coordinate pairs restored from garbled captions ("22 412" → (2, 2), (1, 4), (1, 2), which the
    lecturer repeats at 46:43; "to one" → (2, 1), per slide 45);
  - "C3" → C free;
  - "for connectivity" → four-connectivity;
  - false starts removed.
  Every restored proper noun is in the deck except LaValle (Lecture 1 slide 55), AlphaFold (a
  spoken aside) and SE2 (a student's answer, which the lecturer repeats).
- **Images rendered (22):** 2, 5, 7, 9–11, 15, 17–19, 22, 24, 27, 31, 32, 34, 41, 46, 59, 72, 74
  and 76. The slide file's `images:` header gives the reason for every other slide. The worked
  examples are vector drawings, so the raster test does not see them (pages 68–75 have no raster
  at all), while it flags the photo-backed title and topic-map pages. The selection was made from
  the slide file.
- **Embedding.** The first pass stacked slides 9–11 after a bulleted list of examples. The list
  became three paragraphs and the embed was re-run. Ranges such as "slides 39–41" were kept out of
  any passage that should not carry those figures.
- **Math.** Three slide-file lines put inline math straight after a quotation mark (`"$`), which
  github.com shows as raw text. They were rewritten.
- **Wiki.** The DFS walk-through was left to the posted slides in the lecture (≈49:47), so the
  wiki's DFS table comes from slides 52–59 alone.

## Later runs — lectures 3–9

- [ ] Lectures 3–9, one per run: transcript, deck (Dropbox, `dl=1`), copy-edit, figure audit, wiki
      page, images. Lectures 4–9 also post notes PDFs; decide whether to transcribe them.
