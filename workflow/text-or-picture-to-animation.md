# From text or picture to animation — the unified way

The same six steps, whether the result is a Manim clip, a Blender render or a
whiteboard.

## 1. Read the input

- **Text** (a question, a description): list the bodies, the connections
  (strings, springs, contact), the givens with units, and what is asked.
- **Picture** (scan, photo, screenshot of a question figure): describe what is
  drawn — shapes, their order left to right, angles, labels, arrows. Measure
  proportions from the picture (for example "slope is about twice as long as
  the block is wide"). If something is unreadable or ambiguous, **ask** rather
  than guess.

## 2. Write the scene spec

Write a short spec in the format of [`../spec/scene-spec.md`](../spec/scene-spec.md):
objects, sizes, positions, colours by meaning, labels, and — if it moves — the
equations of motion and parameters. This spec is tool-neutral: the same spec
can feed Manim, Blender or a whiteboard.

## 3. Choose the tool

| If you need… | Use |
|---|---|
| A 2D course animation or slide, equations appearing step by step | **Manim** → [`../renderers/manim.md`](../renderers/manim.md) |
| A 3D object, a camera move around the system, or a 3D model for reuse | **Blender** → [`../renderers/blender.md`](../renderers/blender.md) |
| An interactive picture a student can change or rotate during tutoring | **Whiteboard** (HTML/SVG/three.js) → [`../renderers/whiteboard.md`](../renderers/whiteboard.md) |

When unsure, a 2D question figure goes to Manim.

## 4. Draft still first

Render **one still frame** in draft quality and check it against
[`../style/diagram-rules.md`](../style/diagram-rules.md) (physics → nothing
hidden → bounds → looks). For a picture input, put the original next to the
draft and compare.

## 5. Show it, then animate

Show the draft to the user. Only after the picture is right, render the motion
— first a quick preview, then the final quality.

Time estimates on this computer (Intel Iris Xe, no separate graphics card):

| Tool | Draft | Final |
|---|---|---|
| Manim | `-ql` (480p) ≈ seconds per scene | `-qh` (1080p) ≈ a few minutes per minute of video |
| Blender | Workbench ≈ 0.1 s/frame (16 s clip ≈ 40 s) | Eevee 720p ≈ 2–3 s/frame (≈ 1 min per second of video) |
| Whiteboard | instant | instant |

Measure the real speed on the first frames and update the estimate.

## 6. Keep it

- Code goes in the project that owns the tool (PhysicsAid, BlenderPhysics,
  PhysicsLearn), with a note naming the spec it came from.
- Renders go to that project's `output/` folder; finished videos to Dropbox
  (ask first). Never into git.
- If the work taught something new about the style, add it to
  [`../style/visual-style.md`](../style/visual-style.md).
