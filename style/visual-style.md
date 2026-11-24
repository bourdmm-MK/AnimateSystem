# Visual style — one look for every tool and repository

Every visual made for Marianna's physics teaching uses **this** style, whatever
draws it: Manim scenes and slides (PhysicsAid), Blender models and renders
(BlenderPhysics), the tutor's session whiteboards and diagrams (PhysicsLearn),
and any other generated image or animation.

**This file is the master copy** (AnimateSystem repository). It started from the
Manim course style in PhysicsAid `PhysicsAid_toolbox/PhAid_scene_toolbox.py`.
The same values as data: [`../tokens/style.json`](../tokens/style.json) and
[`../tokens/style.css`](../tokens/style.css). Code copies live in
`PhAid_scene_toolbox.py` (PhysicsAid) and `lib/physkit/style.py`
(BlenderPhysics); keep them in step with this file.

Break a rule only when the user asks for something different for that piece of work.

## Background and lettering

- **Background: black** (Manim's default, `#000000`).
- **Math and labels look like LaTeX** (Computer Modern, italic for symbols):
  `MathTex`/`Tex` in Manim; KaTeX/MathJax in HTML/SVG; real LaTeX in Blender
  (`physkit/latex.py`, Latin Modern for changing numbers). Serif italic
  (Times) only as a fallback when LaTeX is unavailable. Subscripts are real subscripts (`m_1`, `y_2`).
- **Arrows over vector symbols depend on the problem** (user rule, 2026-11-24, applies
  everywhere, magnetic force included). A **generic** problem (symbols only, no numbers)
  writes vectors with an arrow (`\vec v`, `\vec B`, `\vec F = q\,\vec v \times \vec B`).
  A problem whose parameters **have values** — the usual case — uses **no arrows** on labels,
  cards or equations (`T`, `m_1 g`, `v`, `B`, `F = qvB\sin\alpha`). Unit vectors get a hat
  (`\hat z`) in either case.
- **No shadows or glows** on bodies, labels or text unless they are specifically needed. (User rule, 2026-11-24.)
- **HTML whiteboards really load KaTeX** (CSS + JS + auto-render from a CDN) and typeset
  every symbol with it — card text, equations and the labels in the 3D scene
  (`katex.renderToString`). Listing a KaTeX font in CSS without loading KaTeX is not
  enough: it silently falls back to Times/Cambria. In right-to-left (Hebrew) text, keep
  each formula left-to-right and unbroken (`.katex{direction:ltr; unicode-bidi:isolate;
  white-space:nowrap}`), and put multi-step calculations on their own left-to-right lines.
- **No handwriting fonts** — not on whiteboards either — unless the user asks.
- Sizes (Manim, 1080p frame): headers `font_size = 40`, definitions and
  equations `def_font_size = 36`; labels inside small bodies scale to fit.

## Colours by meaning

Use the Manim colour constants by name; hex values are for HTML and Blender.

| Meaning | Manim | Hex |
|---|---|---|
| Position | `BLUE` | `#58C4DD` |
| Displacement | `ORANGE` | `#FF862F` |
| Distance | `PINK` | `#D147BD` |
| Velocity | `YELLOW` | `#F7D96F` |
| Acceleration | `TEAL` | `#5CD0B3` |
| Axes | `GREEN` | `#83C167` |
| Definitions, helper text, dashed guide lines | `GRAY_A` | `#DDDDDD` |
| Time annotations | `WHITE` | `#FFFFFF` |
| Gravity `g` / forces | `RED` | `#FC6255` |
| Structure: slopes, floor, walls, strings, springs | `GREY_B` | `#BBBBBB` |
| Bodies (blocks, carts): fill / outline / label inside | `#C8BD99` / `GREY_E` / `BLACK` | `#C8BD99` / `#222222` / `#000000` |

Kept from PhysicsLearn, they do not clash with the table: **positive charge red,
negative charge blue**; on whiteboard cards **knowns green, unknowns red**.

**Contrast between bodies (Marianna, 2026-11-23).** Sand is right for a single
body. When two or more bodies are compared (a light and a heavy block, m₁ and m₂…),
give each one its **own strong colour** (e.g. big `M` blue `#58C4DD`, small `m`
yellow `#F7D96F`) and colour **its symbol the same way everywhere** (in M/m, on axis
names, in equations). Labels inside the bodies stay black. All-sand scenes look
too bland.
**On whiteboards with equations** (user rule, 2026-11-24) the body colour is used only where it tells
which body something belongs to: the tag before each equation of motion ("m₁:" pink, "m₂:" blue) and
each body's axis name (x₁, x₂ — in the equations' axes line and at the axis tips; axis lines stay green).
Other m₁, m₂ in equations and text stay plain.

**One colour for the goal.** A target value the video is about (π, g, a final
answer) gets one colour used everywhere it appears: title, readout, graph
heading (collision_pi uses teal). The "distance from the goal" readout
(off by … %) is orange, like displacement.

## Shapes

- **Bodies** (blocks, carts, masses): rectangles or squares with fill
  `#C8BD99`, thin dark outline, label inside in black. Round masses (balls,
  pendulum bobs) are circles in the same colours.
- **Structure** (slopes, floor, walls, ceilings, pulleys, strings, springs):
  light grey `GREY_B` lines. Floors and walls are a line with short hatch marks
  on the outside; a spring is a zig-zag (not a sine curve); a string is a
  straight thin line; a pulley is a circle with a centre dot.
- **Vectors:** straight arrows with a solid triangular head, coloured by what
  they are (velocity yellow, acceleration teal, forces red…), starting on the
  body. Curved arrows only for real rotations, and always labelled.
- **Angles:** a thin arc in `GRAY_A`, the label inside the angle.
- **Measured lengths show their starting point:** a dashed reference line at the level a height
  or distance is measured from (e.g. the bottom of the body at its start), plus the dimension line.
  No unexplained marks (a lone "0" at an axis origin). (User rule, 2026-11-24.)
- **Guide lines** (projections, distances, dimensions): dashed, `GRAY_A`,
  behind the objects.
- **Charges:** circles marked + (red) or − (blue). Field into the page ×, out
  of the page ⊙. When a direction symbol (⊗/⊙, e.g. the force into the page) or another
  vector is drawn on top of a charge or body at the same spot, make the body **faint**
  (opacity ≈0.1, its +/− mark hidden) while the symbol is shown, so the symbol reads clearly; fully transparent
  only when absolutely necessary. (User rule, 2026-11-24.)
- **Axes:** green, with arrow heads, behind everything, sized to contain the
  whole drawing.

## Layout

- **An object's values sit next to the object** (live readouts, its labels), moving with it — best as the label of its
  own arrow; never in a far corner. (User rule, 2026-11-24.)
- **Mass labels go inside their body** (`m₁` inside block 1), sized to fit. Make
  the body big enough; put the label beside it only if it truly cannot fit.
- **Axes, dashed guide lines and helper arrows are drawn behind the objects**, so
  they never cover the system. Text sits in front.
- Never hide a given, label or angle mark; vectors start on their body (full rules in
  [`diagram-rules.md`](diagram-rules.md)).
- **3D views are seen from above and in front** (user review, 2026-11-24). A picture without perspective can be read
  two ways — from above or from below — and the eye always assumes "from above". Flat things (vectors in the board's
  plane) look the same either way, but anything that sticks out of the plane (the z axis, a force out of the page)
  looks flipped if the camera is below. So: camera above (y > 0) and in front (z > 0), e.g. (5, 6, 10) with y up;
  then look at the 3D view and check x × y = z by the right hand and that each out-of-plane arrow matches its ⊙/⊗.
  Applies to Manim 3D scenes, Blender cameras and whiteboards alike. The maths being right is not enough — the
  picture must read right.
- A "whiteboard" means building the picture step by step (drawing it in, then
  adding to it) — **in this same style**, not a white background or handwriting.

Marianna's preferences from review rounds (2026-11-23, collision_pi reel):

- **Text big enough to read on a phone.** When in doubt, larger. Keep bodies
  (blocks) large in the frame too; small boxes read as "too small".
- **Related things are aligned.** A number sits on the **same baseline** as its
  label ("Collisions: 181"), only slightly larger than the label for emphasis — not
  much larger. Rows that belong together are centred together or share a left
  edge; values meant to be compared are lined up digit under digit.
- **Even spacing.** A line between two groups sits exactly halfway between them
  (measure the real text edges, don't guess).
- **Centre the key result** (e.g. "off by 0.019 %") and put the main reference line
  (e.g. π = 3.14159…) centred under the title.
- **Fewer lines beat more lines.** Drop readouts that repeat what another shows
  (the reel dropped "estimate =" once "off by %" was there).
- **Show intuitive measures, not raw values.** When values converge (3, 3.1,
  3.14…), plot the **distance from the goal in percent on a log scale**, labelled
  "(lower = closer)", and write the percentage next to each point. Points sitting on
  top of a line show nothing.
- **Leave space** between text blocks and graphs; never let labels touch lines,
  points or other labels.

## Motion and timing

- **One change at a time.** When a run ends, the result appears first (a
  noticeable pop), **holds about 1 s**, then disappears as the next setting (e.g. a
  new M/m) appears. Never change the result and the setting in the same moment.
- When something happens too fast to see, use **labelled slow motion**
  ("slow motion ×11,000"), never unlabelled time tricks.

## Sound

- Sound is **gentle background**: no loud bangs or bells. Dense bursts (many
  events per second), bells and closing chords must not be louder than single
  events — they were "too loud" three rounds in a row.
- Set **fixed levels** for each sound; do **not** normalise the track up to full
  volume at the end (that undoes every reduction). Single event peak ≈ −12 dB,
  continuous parts ≈ −33 dB average; measure before delivering.

## Reels (vertical social videos)

- **1080×1920 (9:16), about 30 s.** Shorten pauses and speed up motion rather than
  cutting content.
- Short **title on top** with the goal symbol in its goal colour, then the key
  readouts, then the graph, then the 3D/system view at the bottom.
- Keep everything out of the app overlays: top ≈ 220 px, bottom ≈ 380 px
  (caption), right ≈ 140 px in the lower half (buttons). Check a still with these
  zones drawn before rendering the video.
- Finished reels go to Dropbox `PhysicaAid\Social\reels\` — only after Marianna
  says so; replace an older copy only when she asks.

## Per tool

- **Manim:** import the palette and sizes from `PhAid_scene_toolbox`
  (`position_color`, `velocity_color`, `axes_color`, `def_color`, `font_size`…)
  instead of redefining them.
- **Blender (BlenderPhysics):** black world background, colours from the table,
  LaTeX labels from `physkit/latex.py` sized with `manim_em()` to match Manim
  (details: [`../renderers/blender.md`](../renderers/blender.md)), orthographic front camera when reproducing a 2D
  question figure.
- **HTML/SVG whiteboards (PhysicsLearn):** black canvas, colours from the table,
  KaTeX/MathJax (or serif italic) for every symbol.
