---
title: Lecture 11 — Bayes Filter (lecture notes)
lecture: 11
pages: 4
source_pdf: https://www.dropbox.com/scl/fi/tfn61o04v3oxhxmnko2ui/Lecture11.pdf?rlkey=lidlhw6muo5zz4d2ifoxbny50&dl=0
numbering: PDF page N = page N; page 1 prints no page number (pages 2–4 print 2–4). Five displays are numbered (1) to (5) by the notes: (1) on page 1, (2) to (5) on page 2. The other displays are unnumbered and cited by page. The "(1)", "(2)" and "(3)" before the three steps of the recap on page 1 number list items, not equations. The two pasted drawings (pages 1 and 2) carry no printed figure numbers or captions; they are numbered notes-figure-1 and notes-figure-2 in order of appearance.
images: The two drawings are rendered as crops of the page and shown just above their descriptions (`notes-figure-1.jpg` and `notes-figure-2.jpg` in this lecture's image folder, numbered in order of appearance; the notes print no figure numbers or captions).
figure_audit: An independent reader checked the two drawings against the PDF at 500–1500 dpi. Everything described is on the page and nothing visible is missing. Corrected: the hatted labels of drawing 1 are a lowercase x (x̂₀), not a capital (settled in the parent from a crop, against the lowercase x̄ of the same drawing); the c of drawing 2's "corre" is lowercase; drawing 2's curve runs round the left end of the box.
---

# Lecture 11 — Bayes Filter: lecture notes

Full text of the course's written notes for Lecture 11 (A. Majumdar), transcribed from the PDF. The course posts no slide deck for this lecture, so these notes are the only written record. Cite as "notes p. N" and "notes eq. (N)". The notes number five equations: Bayes' rule (1) on page 1, its proof (2) and (3) on page 2, and the definition of the belief (4) with its Bayes expansion (5) on page 2. The "(1)", "(2)" and "(3)" in the recap on page 1 number list items. The two pasted drawings are hand-drawn images with no printed numbers or captions: they are numbered `notes-figure-1` and `notes-figure-2` in order of appearance and described in prose. Underlining in the notes is not reproduced; where a phrase is underlined for emphasis it is noted in brackets or left as plain text. Notation, as the PDF's fonts show it: random variables are italic capitals ($X_ t$ the state, $Z_ t$ the measurement, $U_ t$ the control input) and lowercase letters are their values; vectors carry an overbar ($\bar{x}_ t$, $\bar{z}_ t$, $\bar{u}$; on page 4 comment 3 also $\bar{X}_ t$, $\bar{Z}_ t$, $\bar{U}_ t$); the sets of possible states are italic capital $X$ with a hat ($\hat{X}_ t$); the belief is $\mathrm{bel}$ in upright roman type, and in four places the predicted belief (the belief before the measurement) is printed with a rule drawn over it, $\overline{\mathrm{bel}}$. The values of the door example are printed with an underscore between the words (is_open, is_closed, sense_open, sense_closed); in this file they are written with a space ($\text{is open}$, $\text{sense closed}$) so that the formulas render. The header line on page 1 reads "Lecture #12" although this is Lecture 11 (see Printed slips); pages 2–4 carry no header line, only the page number.

[wiki page for this lecture](../../wiki/11-bayes-filter.md) · [transcript](../transcripts/11-bayes-filter.md)

## Contents

| Section | Pages | Equations |
| --- | --- | --- |
| Opening recap (the non-deterministic filter's three steps, its three issues, the plan for today) | 1 | none numbered |
| 1. Probability Basics (random variables, joint, independence, conditional, total probability, Bayes' rule) | 1–2 | (1) on page 1; (2) and (3), the proof, on page 2; other displays unnumbered |
| 2. Example (a door sensor; prior; Bayes' rule at $t = 1$; remark) | 2–3 | (4) and (5) on page 2; other displays unnumbered |
| Example continued (dynamics with a push, Step 1 dynamics update, Step 2 measurement update) | 3–4 | unnumbered displays |
| The Bayes filter (boxed summary) and comments | 4 | unnumbered displays |

## Printed slips

These are in the PDF as printed; the body below keeps them as printed.

- Page 1, header line: "Lecture #12" for what is Lecture 11, and "Insturctor" for "Instructor". Pages 2–4 have no header line.
- Page 1, step (3) of the recap: the line reads "-=" (a hyphen followed by an equals sign, in roman text) before "Fuse information from 1. and 2.", where steps (1) and (2) use an en dash ("–").
- Page 1, the Independence line: "ff X and Y are independent" is printed with "ff" only, not "iff" (the page shows two f's and no i).
- Page 1: "out estimate" for "our estimate".
- Page 3: "ti the text time-step" for "to the next time-step"; "alao" for "also"; "as out $U_ {t-1}$" for "as our".
- Page 4: "the robot sense that the door is open" for "senses".
- Pages 1 and 2: the rule is called "Bayes' Rule" on page 1 and "Bayes's rule" on page 2.
- Page 3, the predicted belief: Step 1's left-hand side is printed with an overline, $\overline{\mathrm{bel}}(X_ 2 = \text{is open})$, but the sentence below it ("Intuitively, $\mathrm{bel}(X_ 2 = \text{is open})$ is the belief about the state at time $t = 2$ before making a sensor measurement") and the display $\mathrm{bel}(X_ 2 = \text{is closed}) = 1 - 0.95 = 0.05$, which are the same predicted belief, are printed without the overline.
- Page 4, Step 2: the denominator of the fraction in the definition of $\mathrm{bel}(X_ 2 = \text{is open})$ is printed with a capital $P$, as $P(Z_ 2 = \text{sense open})$, where every other probability is a lowercase $p$.
- Page 1, in drawing 1: the sets are labelled "x̂₀", "f(x̂₀)" and "f(x̂₀) ∩ h⁻¹(z̄₁)" with a lowercase x (two arcs, as this hand writes the lowercase x of "x̄ₜ₊₁" beside them), for the sets $\hat{X}_ 0$ and $f(\hat{X}_ 0)$ that the text writes with a capital.
- Page 2, in drawing 2: the handwritten caption writes "corre spods" for "corresponds", with a gap after "Corre" and no n between the o and the d.
- Page 4, the label under the underbrace beneath 0.95 is printed with a lowercase $x$, $\overline{\mathrm{bel}}(x_ 2 = \text{is open})$, where the state is a capital $X_ 2$ everywhere else.
- Page 4, comment 3, dynamics model: printed $p(\bar{X}_ t \mid \bar{X}_ {t-1}, \bar{U}_ t - 1)$, with the $-1$ full size on the baseline after $\bar{U}_ t$ rather than a subscript; the intended form is $\bar{U}_ {t-1}$, as in the boxed summary and on page 3.

The arithmetic was checked by substitution: $0.6 \times 0.5 / (0.6 \times 0.5 + 0.2 \times 0.5) = 0.75$; $1 \times 0.75 + 0.8 \times 0.25 = 0.95$; $0.6 \times 0.95 / (0.6 \times 0.95 + 0.2 \times 0.05) \approx 0.983$; the complements $0.25$, $0.05$ and $0.017$ follow. No equation slip was found.

---

## Page 1

Header: "Intro to Robotics", "Lecture #12", "Insturctor: A. Majumdar". No page number is printed on this page.

**Last lecture**: Started discussing methods for state estimation. Discussed the non-deterministic filter. ("state estimation" and "non-deterministic filter" are underlined as printed.)

![Notes drawing, p. 1 — a starting set, its image under the dynamics, the preimage of the measurement and their hatched overlap, with a bracketed recall of the dynamics and sensor equations](../images/11-bayes-filter/notes-figure-1.jpg)

**Notes drawing 1 (p. 1).** A hand-drawn picture in two parts, side by side. On the left are three blob-shaped sets. At the far left is a small oval blob with about four dots and short dashes inside it, labelled "x̂₀" (a lowercase x with a hat and a subscript zero) to its left. From the oval, three short dashed lines run to the right to a larger, pear-shaped blob (broad at the bottom, narrower at the top, about six dots and short dashes inside), which carries the label "f(x̂₀)" below it. To the upper right of the pear a second, round blob overlaps its top right edge; its label "h⁻¹(z̄₁)" (h with a superscript minus one, then z with an overbar and subscript 1) sits just above and to the right of it. The region where the pear and the round blob overlap is shaded in with diagonal hatching. A solid arrow comes from the right and points left at this hatched region, with the label "f(x̂₀) ∩ h⁻¹(z̄₁)" to the right of the arrow's tail; the arrowhead is at the left end, touching the hatched region. All blob outlines are solid; the only dashes are the three connectors. Every hatted x in the drawing is written as this hand writes a lowercase x (two arcs, the same height as the x of "x̄ₜ₊₁" in the bracket), although the text writes the sets with a capital, $\hat{X}_ t$; the z of "z̄₁" and "z̄ₜ" is drawn with a crossbar and read as lowercase. So the picture shows the old set $\hat{X}_ 0$, its image $f(\hat{X}_ 0)$ under the dynamics, the preimage $h^{-1}(\bar{z}_ 1)$ of the measurement, and their intersection as the new estimate. On the right, inside a large hand-drawn left square bracket "[" that closes with a "]" (a stray dot just before it) after the last line, is the handwritten text "Recall:" and below it two lines: "x̄ₜ₊₁ = f(x̄ₜ, ūₜ)" and "z̄ₜ = h(x̄ₜ)", each variable carrying an overbar; the second line ends with the closing bracket.

In general, at time-step $t$, we do:

(1) Compute $f(\hat{X}_ {t-1})$ – Dynamics/transition update

(2) Compute $h^{-1}(\bar{z}_ t)$ – Measurement update

(3) Compute $\hat{X}_ t = f(\hat{X}_ {t-1}) \cap h^{-1}(\bar{z}_ t)$ -= Fuse information from 1. and 2.

(The "(1)", "(2)" and "(3)" are list items; the last item prints "-=" before "Fuse", as noted in Printed slips.)

At every time-step $t$, $\hat{X}_ t$ is our estimate of where the state could be. Note that $\hat{X}_ t$ is a set.

In practice, the non-deterministic filter has many issues: (1) it is computationally challenging to implement; (2) it can be quite conservative; (3) it gives us a set as out estimate of the state. ("set" is underlined as printed.) What do we do with this set? Suppose we have a LQR controller: $\bar{u} = K\bar{x}$. How should we implement this based on $\hat{X}_ t$? Should we pick some representative element from $\hat{X}_ t$? Which one?

**Plan for today:** Probabilistic approach to state estimation. Instead of maintaining a set, we will keep track of a "belief" over the state: $\mathrm{bel}(\bar{x}_ t)$, probability distribution over state at time $t$. (The word "belief" is underlined as printed.)

**1. Probability Basics**

(See Ch.2.2, "Probabilistic Robotics")

We start off with some review of basic probability concepts. $p(X = x)$: probability of a random variable $X$ taking on value $x$, e.g., $p(X = \text{heads}) = p(X = \text{tails}) = 0.5$.

**Probabilities sum to one**: $\sum_x p(x) = 1$, and for a continuous random variable: $\int p(x) dx = 1$.

**Joint distribution**: $p(x, y) = p(X = x \text{ and } Y = y)$.

**Independence**: ff $X$ and $Y$ are independent, $p(x, y) = p(x)p(y)$.

**Conditional distribution**: $p(x \mid y) = p(X = x \mid Y = y)$. Definition: $p(x \mid y) = \frac{p(x, y)}{p(y)}$, as long as $p(y) \gt 0$. Sanity check: if $X$ and $Y$ are independent, $p(x \mid y) = \frac{p(x, y)}{p(y)} = \frac{p(x)p(y)}{p(y)} = p(x)$.

**Theorem of total probability**: following definitions above, $p(x) = \sum_y p(x \mid y)p(y)$ (discrete), and $p(x) = \int p(x \mid y)p(y) dy$ (continuous). We denote $p(x)$ the **marginal distribution**.

**Bayes' Rule (Very important!)**:

$$
p(x \mid y) = \frac{p(y \mid x)p(x)}{p(y)} = \frac{p(y \mid x)p(x)}{\sum_{x'} p(y \mid x')p(x')} \tag{1}
$$

---

## Page 2

Page number "2" at the top left.

Proof for the first equality:

$$
p(x \mid y)p(y) = p(x, y) = p(y \mid x)p(x) \tag{2}
$$

$$
p(x \mid y) = \frac{p(y \mid x)p(x)}{p(y)}. \tag{3}
$$

Bayes' rule allows us to "invert" conditional probabilities - figuring out $p(x \mid y)$ using $p(y \mid x)$.

**2. Example**

(Based on section 2.4.2., Prob Robotics)

Suppose we have a robot equipped with a sensor that allows it to detect if a door is open or closed. But the sensor is not perfect. ("not perfect" is underlined as printed.) It can be wrong sometimes.

$$
p(Z_ t = \text{sense open} \mid X_ t = \text{is open}) = 0.6
$$

$$
p(Z_ t = \text{sense closed} \mid X_ t = \text{is open}) = 0.4
$$

$$
p(Z_ t = \text{sense open} \mid X_ t = \text{is closed}) = 0.2
$$

$$
p(Z_ t = \text{sense closed} \mid X_ t = \text{is closed}) = 0.8
$$

![Notes drawing, p. 2 — a stick-figure robot, a box-shaped building with a small door, a curved arrow to the door, and the handwritten definition of the state](../images/11-bayes-filter/notes-figure-2.jpg)

**Notes drawing 2 (p. 2).** A hand-drawn picture with a handwritten caption. At the upper left, the word "Robot" is written and underlined; below it is a stick figure (a round head with a small dot or circle inside it, a vertical body, arms held straight out to the sides, and two legs spread in an inverted V). Two tiny dots sit to the left of the figure at about waist height (stray marks). At the upper right, the word "Door" is written and underlined. Below it is a long box drawn in perspective, a rectangular block with a flat top and a front face on the left, which carries a small rectangular door with a dot (a handle) on its right side. A curved line starts at the top, just left of the word "Door", sweeps down and to the left around the left end of the box, and ends in a small arrowhead pointing right at the foot of the small door; so the arrow points at the door. Below the picture, in handwritten capitals and lowercase over three lines: "State Xₜ : corre spods to" (the word is written "corre", with a lowercase c, then a gap, then "spods", a misspelling of "corresponds"; the "X" is capital with a subscript t), "whether or not the door", "is open at time t ." The final "t" is lowercase and italic-looking, followed by a period.

So when the door is closed, the robot's sensor is pretty reliable (0.2 probability of being wrong). But when the door is open, the robot's sensor is less reliable (0.4 probability of being wrong).

Suppose, before making any sensor measurements, the robot has a "prior belief" about whether or not the door is open. ("prior belief" is underlined as printed.)

$$
p(X_ 1 = \text{is open}) = 0.5,
$$

$$
p(X_ 1 = \text{is closed}) = 0.5.
$$

Now at time $t = 1$, the robot senses an open door. How should it update its belief about the state of the door? By Bayes's rule:

$$
\mathrm{bel}(X_ 1 = \text{is open}) \triangleq p(X_ 1 = \text{is open} \mid Z_ 1 = \text{sense open}) \tag{4}
$$

$$
\phantom{\mathrm{bel}(X_ 1 = \text{is open})} = \frac{p(Z_ 1 = \text{sense open} \mid X_ 1 = \text{is open})p(X_ 1 = \text{is open})}{p(Z_ 1 = \text{sense open})} \tag{5}
$$

(The symbol between the two sides of (4) is the "is defined as" triangle-over-equals, $\triangleq$.)

Numerator: (underlined as printed)

$$
\underbrace{p(Z_ 1 = \text{sense open} \mid X_ 1 = \text{is open})}_ {\text{sensor model}} \underbrace{p(X_ 1 = \text{is open})}_ {\text{prior}} = 0.6 \times 0.5
$$

---

## Page 3

Page number "3" at the top right.

Denominator: (underlined as printed)

$$
\begin{aligned}
p(Z_ 1 = \text{sense open}) &= p(Z_ 1 = \text{sense open} \mid X_ 1 = \text{is open})p(X_ 1 = \text{is open}) \cr
&\quad + p(Z_ 1 = \text{sense open} \mid X_ 1 = \text{is closed})p(X_ 1 = \text{is closed}) \cr
&= 0.6 \times 0.5 + 0.2 \times 0.5
\end{aligned}
$$

then,

$$
\mathrm{bel}(X_ 1 = \text{is open}) = \frac{0.6 \times 0.5}{0.6 \times 0.5 + 0.2 \times 0.5} = 0.75.
$$

Thus, given the sensor measurements, the robot has increased its belief that the door is open. Since the door can only be open or closed, we conclude:

$$
\mathrm{bel}(X_ 1 = \text{is closed}) = 1 - 0.75 = 0.25.
$$

Remark: (underlined as printed) think about the role that Bayes' rule played here. We had a "model" (a probabilistic one) of our sensor of the form $p(Z_ t \mid X_ t)$. What we really care about is $p(X_ t \mid Z_ t)$. Bayes' rule allowed us to do this "inversion". This is conceptually similar to how we computed $h^{-1}(\bar{z}_ t)$ in the non-deterministic filter.

So far, we haven't taken into account dynamics or control inputs. Let's do this. Suppose the robot has an action (control input) it can apply for pushing the door.

$$
p(X_ t = \text{is open} \mid X_ {t-1} = \text{is open}, U_ {t-1} = \text{push}) = 1
$$

$$
p(X_ t = \text{is closed} \mid X_ {t-1} = \text{is open}, U_ {t-1} = \text{push}) = 0
$$

$$
p(X_ t = \text{is open} \mid X_ {t-1} = \text{is closed}, U_ {t-1} = \text{push}) = 0.8
$$

$$
p(X_ t = \text{is closed} \mid X_ {t-1} = \text{is closed}, U_ {t-1} = \text{push}) = 0.2
$$

Note: (underlined as printed) the Probabilistic Robotics book uses a slightly different convention. Their dynamics models are of the form $p(X_ t \mid X_ {t-1}, U_ t)$ instead of $p(X_ t \mid X_ {t-1}, U_ {t-1})$. You can just think of their $U_ t$ as out $U_ {t-1}$.

Recall: (underlined as printed) using our previous calculation, the robot's belief at $t = 1$ is: $\mathrm{bel}(X_ 1 = \text{is open}) = 0.75, \mathrm{bel}(X_ 1 = \text{is closed}) = 0.25$.

We will apply a similar procedure to the non-deterministic filter and use two steps:

**Step 1**: "Dynamics / transition update"

$$
\begin{aligned}
\overline{\mathrm{bel}}(X_ 2 = \text{is open}) &\triangleq p(X_ 2 = \text{is open} \mid X_ 1 = \text{is open}, U_ 1 = \text{push})\mathrm{bel}(X_ 1 = \text{is open}) \cr
&\quad + p(X_ 2 = \text{is open} \mid X_ 1 = \text{is closed}, U_ 1 = \text{push})\mathrm{bel}(X_ 1 = \text{is closed}) \cr
&= 1 \times 0.75 + 0.8 \times 0.25 = 0.95
\end{aligned}
$$

Intuitively, $\mathrm{bel}(X_ 2 = \text{is open})$ is the belief about the state at time $t = 2$ before making a sensor measurement. ("before" is underlined as printed.) We are propagating our belief from $t = 1$ ti the text time-step based on the knowledge of the dynamics of our system.

Using the calculation above, we alao have:

$$
\mathrm{bel}(X_ 2 = \text{is closed}) = 1 - 0.95 = 0.05.
$$

**Step 2**: "Measurement update"

---

## Page 4

Page number "4" at the top left.

Suppose at time $t = 2$, the robot sense that the door is open. It can then update its belief.

$$
\mathrm{bel}(X_ 2 = \text{is open}) \triangleq p(X_ 2 = \text{is open} \mid Z_ 2 = \text{sense open})
$$

$$
\phantom{\mathrm{bel}(X_ 2 = \text{is open})} = \frac{p(Z_ 2 = \text{sense open} \mid X_ 2 = \text{is open})p(X_ 2 = \text{is open})}{P(Z_ 2 = \text{sense open})}
$$

Numerator: (underlined as printed)

$$
0.6 \times \underbrace{0.95}_ {\overline{\mathrm{bel}}(x_ 2 = \text{is open})}
$$

Denominator: (underlined as printed)

$$
\begin{aligned}
p(Z_ 2 = \text{sense open}) &= p(Z_ 2 = \text{sense open} \mid X_ 2 = \text{is open})p(X_ 2 = \text{is open}) \cr
&\quad + p(Z_ 2 = \text{sense open} \mid X_ 2 = \text{is closed})p(X_ 2 = \text{is closed}) \cr
&= 0.6 \times 0.95 + 0.2 \times 0.05
\end{aligned}
$$

then,

$$
\mathrm{bel}(X_ 2 = \text{is open}) = \frac{0.6 \times 0.95}{0.6 \times 0.95 + 0.2 \times 0.05} \approx 0.983,
$$

and

$$
\mathrm{bel}(X_ 2 = \text{is closed}) = 1 - 0.983 = 0.017.
$$

What we have described is the **Bayes filter**. You should think of it as a probabilistic version of the non-deterministic filter.

The notes then show a boxed summary (a rectangle spanning the text width, headed "At each time-step, we do (for all $X_ t$):"; the Bayes filter is not under a new numbered heading):

1.

$$
\overline{\mathrm{bel}}(X_ t) = \sum_{X_ {t-1}} p(X_ t \mid X_ {t-1}, U_ {t-1})\mathrm{bel}(X_ {t-1}) \quad \text{– "Dynamics update"}
$$

2.

$$
\mathrm{bel}(X_ t) = \frac{p(Z_ t \mid X_ t)\overline{\mathrm{bel}}(X_ t)}{p(Z_ t)} \quad \text{– "Measurement update"}
$$

(The two lines of the box are numbered "1." and "2." as list items, not as equations; each ends with its name in quotation marks after an en dash.)

Some comments: (underlined as printed)

1. See Section 2.4.3 of Probabilistic Robotics for a complete mathematical justification/details for the Bayes filter.

2. The Bayes filter can be computationally challenging to implement. For continuous state spaces, the sums in the Bayes filter get replaced by integrals. This makes it tricky to implement. There will be settings where we can implement the Bayes filter in a computationally efficient manner. ("can" is underlined as printed.) In other settings, we will have to make some approximations (we will discuss this in the next lecture).

3. We need two things to implement the Bayes filter:

$$
\text{Dynamics model:} \quad p(\bar{X}_ t \mid \bar{X}_ {t-1}, \bar{U}_ t - 1)
$$

$$
\text{Measurement model:} \quad p(\bar{Z}_ t \mid \bar{X}_ t)
$$

Think a little bit about how you might specify/obtain these.
