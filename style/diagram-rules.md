# Diagram rules — physically right first, pretty second

These rules apply to every drawing and animation, in every tool. They come from
the PhysicsLearn tutor's visualization guide, which keeps the tutor-specific
parts (session whiteboards, teach/solve modes).

## Physics

- **Vector tails stay on the body.** Components start at the body and lie on
  their true lines of action. Never shift a vector sideways to avoid overlap;
  when a component lies on an axis, tell them apart by styling (thin light
  axis, bold coloured vector).
- **Straight quantities get straight arrows.** Forces, fields and velocities
  are straight arrows. Curved arrows only for real rotations, and labelled.
- **Motion comes from the equations.** Animated motion is computed from the
  equations of motion (or a physics engine with stated parameters), never from
  hand-placed positions that only look right. Physical parameters are named
  constants in SI units at the top of the script.
- **Show only what the model includes.** No implied friction, air resistance
  or precision the model does not have.

## Readability

- **Never hide information.** Nothing may cover a given, label or angle mark.
  Move labels into clear space; an angle label goes inside its angle.
- **Axes contain the drawing** — the whole trajectory and every arrow.
- **Draw only what the step needs.** One vector per quantity at the object of
  interest; no decorative field-line forests unless the spatial picture is
  what is being taught.
- **Multi-stage problems:** dim what belongs to other stages, remove what is
  used up, keep the quantity that links two stages fully visible.

## Reproducing a given figure (from a picture)

- First match the original figure: same layout, same proportions, same view.
  For a 3D situation drawn in 2D, start from an exact **orthographic front
  view**, then let the camera move.
- **Do not add axes or objects that the figure did not have**; add them only
  when the solution needs them.
- × and ⊙ are real vectors: in 3D, model each as an arrow along −z / +z.

## Hebrew text

Hebrew (right-to-left) labels must not be mixed into monospace text sketches —
the letters get reordered. Use Latin letters or symbols as anchors in the
drawing and explain them in a Hebrew legend, or place every label at an
explicit coordinate (SVG, Manim, Blender).

## Checking a render — in this order

1. **Physical correctness** — tails on bodies, directions true, geometry
   matches the question.
2. **Nothing hidden** — every given, label and angle mark readable.
3. **Bounds** — the frame and axes contain everything.
4. Only then **looks** — colours, fonts and shapes from
   [`visual-style.md`](visual-style.md).

A tidy but physically wrong drawing is a worse failure than an overlap.
