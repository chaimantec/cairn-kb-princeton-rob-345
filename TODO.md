# KB build — Princeton ROB 345

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Later runs — lectures 4–9

- [ ] Lectures 4–9, one per run: transcript, deck (Dropbox, `dl=1`), copy-edit, figure audit, wiki
      page, images. Lectures 4–9 also post notes PDFs; decide whether to transcribe them.

## Run 3 — Lecture 3 (RRTs), 2026-10-21

Scope: lecture 3 only. Settings carried from runs 1–2: images on, PDFs link-only, commit as
chaimantec <nantapon@chaimantec.com>. Catalog re-fetched 2026-10-21: still 9 lectures.

### Transcripts
- [x] 03 Lecture 3: Rapidly Exploring Randomized Trees (RRTs) — video KDIe1094FMo — verbatim captions in raw/transcripts/original/ (92 paragraphs, 12,152 words incl. header)
- [x] 03 copy-edit (Sonnet): 92/92 timestamps identical; ratios all in 0.72–1.10 (lowest 0.72 at 1:09:11; 12,019 → 9,719 words); number diffs C3 → C free and "00 0" → 0, 0, 0; 39 restorations, 2 inline unclear + 6 noted; proper nouns not in the deck all traced to captions (Keerthi from "Kery", Minkowski, Voronoi, Stata Center, LaValle, Hugging Face)

### Slides
- [x] Download Lecture3.pdf (Dropbox dl=1, 9.4MB, 62 pages) into raw/pdfs/ (gitignored)
- [x] Slide number map: 1:1 (62 pages); pages 1 and 2 print no number
- [x] raw/slides/03-rrts.md (Sonnet), --verify clean (62 headings)
- [x] Figure audit (Sonnet), two passes, 34 slides incl. every step of the RRT walk-through: first pass 4 of 10 pages wrong (36 wrong point in collision, 41 node count, 44 wording, 50 tree extent); second pass 14 pages: 40/43 omitted the solid edge already drawn, 31 line clips the corner, small counts on 10/12/24. Renders of 36 and 50 checked in the parent

### Wiki
- [x] wiki/03-rrts.md
- [x] Topic pages: new wiki/rrt.md; configuration-space (robot geometry, curse of dimensionality) and graph-search (completeness, scaling) extended; course-map row; Lecture 2 forward link
- [x] INDEX.md table of contents and coverage paragraph

### Images
- [x] raw/images/03-rrts/ — 17 slides rendered (1.5MB), embedded in the slide file, the lecture page, rrt.md (3) and configuration-space.md (3); 17 hand-written captions
- [x] INDEX.md image sentence; AGENTS.md table row and three general lessons; BUILD_LOG.md record (below); LICENSE.md attribution

### Publish
- [x] kb.json — coverage, byLecture, images (and the stale PNG count), figureAudit, caveats
- [x] sources.md "In this KB" column
- [x] verify_kb.py clean (all hard checks; 553 formulas in chat and on github.com), and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Lecture 3 record

- **Deck.** `Lecture3.pdf` from Dropbox, 62 pages, 9.4MB. The text layer has no licence or copyright
  notice, and none is on the course site. No slide credits third-party material in words; slides
  19, 24, 49, 50, 53, 54, 56 and 58 give YouTube or Wikipedia URLs. LICENSE.md lists what it can.
- **Numbering.** One-to-one. Pages 1 and 2 (the title page and the topic map) print no number.
- **Repeats of earlier decks.** A low-resolution greyscale pixel diff against Lecture 2's deck
  found slides 2, 3, 4, 15, 17 and 18 identical (mean difference 0.00–0.01) to Lecture 2's 4, 5, 6,
  15, 17 and 18. Slide 19 is a different frame of the same video as Lecture 2's slide 19 (difference
  29.7), showing the configuration-space obstacle itself, so it was rendered. Slide 5 is one panel of
  Lecture 2's slide 76 animation.
- **Transcription.** Sonnet, about 2 minutes; `--verify` clean first time (62 headings). It flagged
  the worked-example steps (25–47), the pseudocode, and the video frames 49, 50 and 58 for a second
  reader. The agent's own note on slide 41 already contradicted itself ("five blue nodes",
  four listed).
- **Figure audit.** Sonnet, two passes. The first, on 13, 21, 36, 37, 41, 44, 46, 47, 50 and 58,
  found errors on four pages:
  - slide 36 put the nearest vertex inside the obstacle, when it is the extended point that is in
    collision, the very thing the step illustrates;
  - slide 41 counted five nodes for four;
  - slide 44 described the chain as running "along the bottom" of the obstacle;
  - slide 50 had the tree reaching the top of the tall obstacle.
  It also confirmed that slide 58's two panels are the same image as slide 50 (two pixels differ).
  This first agent viewed whole pages at 110 dpi and did not crop to 600 dpi, despite the prompt.
  Under the "dirty sample" rule, a second pass covered every remaining step of the walk-through
  (25–35, 38–40, 42, 43, 45) plus 7, 9, 10, 12, 19, 24 and 51, cropping where calls were close. It
  found:
  - slides 40 and 43 already draw the new edge, which the file omitted, so the deck has no
    "edge added" slide for iteration 4;
  - slide 31's dotted line clips the obstacle's corner;
  - small counts and wording on 10, 12 and 24.
  The renders of 36 and 50 were checked in the parent and agree. One more correction came from the
  render of 50: the up-left branch runs to about (−3.5, 5).
- **Transcript edit.** Sonnet, 92/92 timestamps identical, every paragraph ratio in 0.72–1.10
  (lowest 0.72 at 1:09:11; 12,019 → 9,719 words). Four paragraphs heavy with "uh" first came out at
  0.62–0.67. The agent raised them by keeping hedges that are in the captions ("kind of", "sort
  of"), not by adding anything. It made 39 restorations and left 2 inline unclear marks plus 6
  noted ones. The number diffs are both deliberate: C3 → C free, and the origin "00 0" → 0, 0, 0
  (the agent had written 0, 0, dropping a zero; corrected in the parent). Proper nouns not in the
  deck were all traced to the captions:
  - "Gilbert Johnson Kery" → Keerthi;
  - "Minkovski" → Minkowski;
  - "waroi" → Voronoi;
  - the lecturer's own "Stata Center", against an earlier "data center";
  - "Steve Laval" → LaValle (Lecture 1 slide 55);
  - "hugging face", capitalized.
  The header's claim that the lecturer spells out "Minkowski" was softened to "the captions spell
  it", matching its own unclear list.
- **Images rendered (17):** 7, 9, 10, 13, 19, 21, 24, 25, 28, 32, 36, 43, 47, 50, 51, 53 and 56. The
  slide file's `images:` header gives the reason for every other slide, and a script checked that
  the two lists cover slides 1–62 exactly once. Slides 54 (a title card) and 58–59 (repeated
  frames) were skipped although each is discussed.
- **Embedding.** The lecture page carries all 17 images. `rrt.md` carries 21, 47 and 51, and
  `configuration-space.md` carries 7, 13 and 21. A dry run on `configuration-space.md` would have
  stacked 7, 9 and 10 under one "slides 7–10" citation, so the citation was narrowed to slide 7. The
  Lecture 3 embed was not run on `graph-search.md`, whose Lecture 2 citations (24, 28, …) share
  numbers with Lecture 3's rendered slides. Lesson in AGENTS.md.
- **Math.** The slide file's `\bar{q}_s` put `_` straight after `}` 104 times (github.com italics
  pairing). It was rewritten as `\bar{q}_ s`, with `\lbrace`, `\Vert` and `\lt` in the pseudocode,
  and the wiki uses the same form.
- **kb.json.** `materials.images.format` said "one PNG" since run 2. Lectures 1–3 have six; fixed.
