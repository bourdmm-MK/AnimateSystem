# Whiteboards (PhysicsLearn)

**Code lives in:** PhysicsLearn (`bourdmm-MK/PhysticsLearn`), locally
`../PhysicsLearn/`. The tutor rules for when and how to build a board (state
object, givens/unknowns cards, step-by-step updates, teach mode not running
ahead) are in its `knowledge-base/visualization-guide.md`. Reusable pieces
(the 3D hand kit) are in `tools/whiteboard/`.

"Whiteboard" means **building the picture step by step** — in this same style,
not a white background and not handwriting.

## Applying the style

- Paste the contents of [`../tokens/style.css`](../tokens/style.css) into the
  board's `<style>` (boards are self-contained HTML files, so inline it rather
  than linking), and colour SVG elements with `var(--velocity)`, `var(--force)`…
- Every symbol in KaTeX or MathJax; if neither is available, serif italic.
- Black canvas; givens cards green (`--known`), unknowns red (`--unknown`).
- In SVG, draw axes and guides **first** in the markup so they sit behind.
- 3D boards (three.js): black scene background, the same hex colours,
  orthographic front camera at the start when copying a 2D figure.

## From a scene spec

The spec's `steps` list maps directly onto the board's state: each step reveals
the listed objects.

## Examples

PhysicsAid `expermients/wedge_ramp_q2/whiteboard.html` (a board for the same
question that also has Manim and Blender versions).
