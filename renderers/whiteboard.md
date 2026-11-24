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
