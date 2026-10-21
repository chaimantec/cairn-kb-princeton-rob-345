# How this knowledge base is organized

This repo is the knowledge base for **Princeton ROB 345/549 — Introduction to Robotics (Fall
2026)**. It is read by Cairn's in-extension AI chat, which starts at `INDEX.md`, fetches files
over raw.githubusercontent.com and follows relative markdown links.

The chat never reads this file. It is for whoever builds the KB, and Claude Code
loads it into every step of every build agent, so keep it to the rules every
lecture's build follows. The per-lecture record (licence notices, audit findings,
printed slips, which slides were rendered and why) goes in
[`BUILD_LOG.md`](BUILD_LOG.md); anything the chat needs goes in `INDEX.md`;
attribution goes in [`LICENSE.md`](LICENSE.md).

## Layout

| Path                | Contents                                                      |
| ------------------- | ------------------------------------------------------------- |
| `INDEX.md`          | Entry point. Course summary + annotated table of contents.    |
| `wiki/`             | Durable pages: one per lecture, plus course and concept pages. |
| `raw/slides/`       | Full text of every slide, headed `## Slide N` with the **printed** number. |
| `raw/notes/`        | Full text of the written lecture notes, headed `## Page N`, equations under the notes' own numbers. |
| `raw/transcripts/`  | Copy-edited transcripts with `[MM:SS]` paragraph marks.       |
| `raw/transcripts/original/` | Verbatim auto-captions. **Gitignored**, local reference only. |
| `raw/pdfs/`         | Downloaded decks. **Gitignored**; cite the canonical URL.     |
| `raw/images/`       | Rendered figure slides, `NN-<slug>/slide-N.jpg`. Linked from the pages using them. |
| `sources.md`        | Every course document by lecture, with canonical URLs.        |
| `LICENSE.md`        | Three-layer licence and image attribution.                    |
| `kb.json`           | Machine-readable coverage and provenance.                     |
| `TODO.md`           | Open work only. Finished runs move to `BUILD_LOG.md`.         |
| `BUILD_LOG.md`      | Finished runs, one section each. Not needed to answer questions. |

## Conventions

- **INDEX.md is the front door.** The chat reads it first on every conversation.
  Every wiki page must appear there with a one-line description of what it holds.
  An unindexed page is effectively invisible. Keep its coverage paragraph true
  whenever a lecture is added.
- **Relative links only**, including images. Absolute GitHub URLs break when the
  repo is renamed or forked. Slide decks link to their canonical Dropbox URL,
  never to `raw/pdfs/`, which is gitignored.
- **Cite everything.** Written material as "slide N" (the printed number),
  spoken material as (≈M:SS). Claims trace back to one or the other.
- **Never invent course content.** If the transcript is unclear at some point,
  say so on the page. Do not fill the gap from outside knowledge — the chat
  presents these pages as authoritative material from this course.
- **Prose over fragments.** The chat quotes these pages to learners; bullet
  fragments quote badly.
- **Never rank lectures against each other** in prose; state the measurement for
  the lecture in hand.
- **Math in LaTeX**: `$...$` inline, `$$...$$` displayed, never inside a code
  fence. Define each symbol on first use, and follow the course's own notation.
  A literal dollar sign in prose opens a math span: write "20,000 dollars".
  Keep each inline formula on one line: one wrapped across a line break passes the offline
  check and renders as raw text on github.com. Run `check_math.mjs` (the `cairn-kb` skill),
  with `--github`, before pushing.

## Course materials

- The course site is a single page (GitHub Pages). **Every deck, set of notes and
  assignment is hosted on Dropbox**, so the crawler records them as external links
  and downloads nothing. Download a deck directly by changing the link's `dl=0` to
  `dl=1`. Cite the `dl=0` link. Assignment 2 is a notebook on GitHub
  (`Princeton-Introduction-to-Robotics/F2026`).
- `inventory_to_sources.py` mislabels these Dropbox decks as third-party papers,
  so `sources.md` is maintained by hand as a per-lecture table. Update its "In this
  KB" column when a lecture lands.
- From Lecture 4 on, the site posts **notes** alongside slides. They are LaTeX prose documents,
  not decks. When a deck says "See notes", the notes are the written record of the derivation (the
  board is not in the video), so transcribe them to `raw/notes/NN-<slug>.md`: front matter,
  contents table (section, pages, equations), a "Printed slips" list, then `## Page N`, every
  displayed equation in its own `$$` block with one `\tag{N}` carrying the notes' number, and
  every figure described in prose. Delegate the reading to Sonnet like a deck. The prose may be
  copied from the text layer, which is clean for pdfTeX output; equations never. Check every
  equation number against the text layer in the parent, and read the font (`MSBM10` is
  blackboard bold) where a symbol's style matters. Cite as "notes eq. (N)", "notes p. N". Where the
  board and the notes differ (a symbol's name, a matrix's size, how a definition is built up), the wiki follows the notes and gives
  the board's version with its timestamp; the lecture never speaks the notes' equation numbers unless
  the transcript shows it.
  A printed slip the deck agent reports is a claim like any other: check an equation slip by substituting
  one equation into the next before listing it, since agents flag correctly derived factors as slips. A slip
  in a handwritten label is settled in the parent from a crop of that label (about 1k tokens), comparing the
  glyph with the same letter elsewhere in the drawing: audits misread handwriting in both directions.
- No licence is stated anywhere on the site or in the decks. See `LICENSE.md`.

## Transcripts

- `raw/transcripts/NN-<slug>.md` is the copy-edited transcript the chat reads. It is
  edited by a Sonnet subagent and checked in the parent with three checks: an
  identical `[MM:SS]` sequence, the number inventory, and per-paragraph word-count
  ratios in 0.72–1.10. Every restored proper noun is grepped against the slide file.
- The verbatim captions stay on disk in `raw/transcripts/original/` and are
  **not committed**. The course has no licence, and a full caption copy is the
  weakest thing to publish on every fair-use factor. Each edited file says how to
  regenerate them.
- Notation stays spoken in transcripts ("x equals f of x"). Reconstructing it, e.g.
  $\dot{x} = f(x)$, belongs in `wiki/`, with a note when the captions dropped a symbol.

## Slides

- Always run `slide_number_map.py` before transcribing. **Printed numbers are not
  PDF pages**: Lecture 1's deck hid slide 2, so every later page prints its page
  number + 1. Headings use the printed number; each slide file states its mapping.
- A number printed inside the slide body instead of the corner (Lecture 1, slide 5)
  is missed by the text-layer scan and reported as unnumbered. The labels still come
  out right, but confirm the "inferred" list by eye before writing it into a header.
- Transcription is delegated to a Sonnet subagent with the number map handed over.
  A Sonnet audit of six figure-heavy pages follows, returning discrepancies as text.
  Step-by-step worked examples (search grids, growing trees) are where errors concentrate:
  which point is in collision, how many nodes, which edge is drawn. Audit every step of one. In drawn phase portraits and trajectories, audit the direction of every arrow:
  whether a curve runs towards or away from the fixed point is the content, and it is where readings go wrong. When a drawing marks one entry of a matrix or list, have the audit count which entry it is.
- A slide that plays a video or animation, or a screenshot of a demo run live, holds a single frame in the PDF. The transcript
  shows it ("let me play it again"); say so in the slide entry, so that a counter or partial
  search state in that frame is not read as the result. The deck agent cannot see the lecture,
  so it describes only the frame; whether and how the video played comes from the transcript,
  written in by the parent.

## Images

- Notes figures are cropped from the page with their printed caption, 1400px wide, saved as
  `raw/images/NN-<slug>/notes-figure-N.jpg`, and placed by hand under the caption in `raw/notes/`
  and in the wiki: `embed_slide_images.py` handles only `slide-N` files. Count them in the table
  below as images, not as deck pages. Notes whose drawings have no printed number or caption are
  numbered `notes-figure-N` in order of appearance, and the notes file's header says so.
- One image per rendered slide at `raw/images/NN-<slug>/slide-N.jpg` (or `.png`),
  1400px wide, rendered by `extract_slide_images.py` and placed by
  `embed_slide_images.py`. The script puts each image under `## Slide N` in the slide file
  and after the first block that cites slide N in a wiki page. Run it once per wiki page.
  Give each figure its own citing paragraph: a block citing several slides stacks their
  images under it. A range such as "slides 39–49" cites every slide in it, so cite a range
  only where no rendered slide falls inside, and cite one slide where its figure should sit.
- Choose figure slides from the slide file's descriptions. The raster test misses
  vector-drawn figures such as graphs and worked-example grids.
- Decks repeat slides from earlier lectures. Find them by a low-resolution greyscale pixel
  diff against the earlier deck (a mean difference near 0 is the same slide), not by opening
  pages, and do not render them again. Two blank (black) video frames also diff at 0, so check a
  match's brightness before calling it a repeat. A repeated video under a new title bar escapes
  the diff: compare the video URLs printed on video slides with the earlier slide files too.
- `embed_slide_images.py` matches "slide N" whatever lecture it belongs to. On a topic page that
  cites several lectures' slides, cite the other lecture's slides by section link or run
  `--dry-run` first, or one lecture's image lands on another lecture's citation.
- Render every figure-bearing slide except title and divider slides, text-only
  slides, unrendered video frames, screenshots whose content is headline text
  already transcribed, decorative stock photos, repeats and build steps of a
  rendered slide, and **photographs of course staff or students**.
- Hand-write captions that say what to look at for the figures that carry the
  argument (architecture-like diagrams, charts, the examples discussed at length).
- `grep -o 'raw/images/[^)]*' wiki/NN-*.md` lists a lecture's wiki images. The
  slide file's `images:` header lists every rendered slide and why the rest were not.
- When a lecture adds images, update `INDEX.md`'s "Only Lecture … has images"
  sentence, the table below, `kb.json` `materials.images`, and `LICENSE.md`.

| Lecture | Images | Notes |
| --- | --- | --- |
| 1 Intro to Robotics | 24 of 57 pages | photos, video stills, one chart, two diagrams |
| 2 Discrete Motion Planning | 22 of 79 pages | video stills, C-space diagrams, worked-example grids |
| 3 RRTs | 17 of 62 pages | geometry diagrams, video stills, steps of the RRT worked example |
| 4 Quadrotor Dynamics | 7 | 4 of the deck's 13 slides (lab photographs) and the notes' 3 figures |
| 5 Differential Flatness | 7 | 3 of the deck's 6 slides (a paper's first page, two video frames) and the notes' 4 drawings |
| 6 Trajectory Optimization | 6 of 18 pages | a plot, two diagrams, a QP contour plot, a demo frame, a video still; the notes have no drawings |
| 7 Stability and PD Control | 5 | 2 of the deck's 7 slides (a simulation frame, the hover vector field) and the notes' 3 drawings |
| 8 LQR | 6 | 4 of the deck's 13 slides (the control loop, a phase portrait, two video frames) and the notes' 2 drawings |
| 9 Optical Flow | 13 | 9 of the deck's 21 slides (a path diagram, a drone photograph, two flow fields, two diagrams, an illusion frame, two marked-up photographs) and the notes' 4 drawings |

## Rebuilding

Built and updated by the `cairn-kb` skill. To add newly released lectures,
append entries to `TODO.md` and re-run the skill — it only does unchecked work.
When a run is committed and pushed, move its `TODO.md` section verbatim to
`BUILD_LOG.md`, so `TODO.md` keeps only open work. Add here only a lesson
that applies to every lecture, stated in general form.
