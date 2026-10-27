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
- [ ] Topic pages: state-estimation, uncertainty, course-map and the other pages that point forward to Lecture 11
- [ ] INDEX.md table of contents, coverage paragraph, raw/notes and raw/images entries

### Images
- [x] raw/images/11-bayes-filter/ — the notes' two drawings, cropped at the image rectangles plus 6pt, 1400px (0.1MB)
- [x] Placed in raw/notes/ (by the transcription, above each description) and by hand in the wiki
- [ ] INDEX.md image sentence; AGENTS.md table row; LICENSE.md attribution

### Publish
- [ ] kb.json — coverage, byLecture, notes, images, caveats
- [ ] sources.md row 11
- [ ] BUILD_LOG.md — the lecture's record
- [ ] verify_kb.py clean, and its review section read
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Older lines this run completes
- [ ] Lecture 11 (Bayes filter), video mno8-hG7tJc: transcript, notes (`Lecture11.pdf` on Dropbox,
      linked as "Notes"; no deck posted on 2026-10-28), copy-edit, figure audit, wiki page, images.

## Later runs

- [ ] Lectures 12 onward. On 2026-10-28 the catalog holds 11 recorded lectures. When it re-syncs, diff
      its lectures against raw/transcripts/ and add one line per new lecture here.
