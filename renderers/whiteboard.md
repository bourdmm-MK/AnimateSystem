# Whiteboards (PhysicsLearn)

**Code lives in:** PhysicsLearn (`bourdmm-MK/PhysticsLearn`), locally
`../PhysicsLearn/`. The tutor rules for when and how to build a board (state
object, givens/unknowns cards, step-by-step updates, teach mode not running
ahead) are in its `knowledge-base/visualization-guide.md`. Reusable pieces
(the 3D hand kit) are in `tools/whiteboard/`.

"Whiteboard" means **an HTML board** (SVG or three.js, KaTeX for maths) that
builds the picture step by step — in this same style, not a white background,
not handwriting, and not a Manim scene that "draws in". When Marianna asks for a
whiteboard, build the HTML board.

## Applying the style

- Paste the contents of [`../tokens/style.css`](../tokens/style.css) into the
  board's `<style>` (boards are self-contained HTML files, so inline it rather
  than linking), and colour SVG elements with `var(--velocity)`, `var(--force)`…
- Every symbol in KaTeX or MathJax; if neither is available, serif italic.
- Black canvas; givens cards green (`--known`), unknowns red (`--unknown`).
- In SVG, draw axes and guides **first** in the markup so they sit behind.
- 3D boards (three.js): black scene background, the same hex colours,
  orthographic front camera at the start when copying a 2D figure.

## Cards and readouts

- Cards in the question's language (English question → English board, Hebrew → Hebrew): givens in green; unknowns in red, turning green with ✓ once
  found; a "current step" card; live readouts of changing quantities
  (for example `p_x`, `E`).

- **Roomy line spacing:** ≈0.26em above and below each equation line (≈0.34em on a phone); frames never touch the next line. (User review, 2026-11-25.)
- **General formulas in a red frame:** a symbols-only equation used before numbers are put into it (e.g. v² = v₀² + 2aΔx) is framed in red (#FC6255); the final answer is framed in green. (User rule, 2026-11-25.)
- **The solution comes after the animation:** each step's equations fade in only once its animation has finished. (User rule, 2026-11-25.)
- **Mass label inside each body:** KaTeX `m_1`, `m_2` (true subscript), black, sized from the box — at most ¾ of its width and 80% of its height, never touching the edges; recomputed on resize and in the phone view. (User review, 2026-11-25.)
- **Each body is filled with its own colour** (m₁ pink, m₂ blue; label inside black), and **the drawing copies the question's figure** (which body on which side, what holds the pulleys, where the floor is). (User review, 2026-11-25.)
- **Body colours, only where they tell which body:** the "m₁:" / "m₂:" tag before each equation of motion
  and the axis names x₁, x₂ (equations' axes line + axis tips in the drawing). Nothing else coloured.
- **One line per equation:** never split an equation unless the whole line would make the equation text
  smaller than 15 px. (User rule, 2026-11-24.)
- **Equation size fixed per board:** chosen once from the fullest step; it never changes between steps.
- **Phone or computer, the viewer chooses:** a chooser on opening (remembered, switchable); the phone view
  stacks drawing over equations; the equations panel is a plain scrolling list (no CSS columns) that jumps to
  the newest lines; phone drawing: bodies 20% smaller, arrows and labels larger. (User rule, 2026-11-24.)
- **No key/legend card** — everything is labelled on the board. (User rule, 2026-11-24.)
- **One screen, no scrolling:** header + drawing + a compact cards row (≈26vh) fill the window; the
  drawing (its own shape) and an equations panel share the rest of the width edge to edge, the
  equations auto-sized as large as fits (one or two columns); card text `clamp(15px,1.15vw,24px)`, drawing text scales with
  the drawing. (User rule, 2026-11-24.)

## Known quirks

- **KaTeX inside Hebrew (RTL) cards comes out mirrored** unless you add
  `.katex { direction: ltr; unicode-bidi: isolate; }` (already in
  [`../tokens/style.css`](../tokens/style.css)).
- **SVG text cannot show a vector arrow** made with the combining character
  (v + U+20D7). Draw a small → above the letter as its own SVG element instead,
  or use KaTeX in an HTML overlay.

## From a scene spec

The spec's `steps` list maps directly onto the board's state: each step reveals
the listed objects.

## Examples

PhysicsAid `expermients/wedge_ramp_q2/`: `whiteboard.html` + `whiteboard.js`
(the board for Question 2), and `compare.html`, which plays the Blender video,
the Manim video and the live board side by side, in sync.
