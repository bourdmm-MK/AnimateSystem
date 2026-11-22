# AnimateSystem — one way to draw and animate a physics system

This repository is the **single home of the visual style** and the **single
recipe** for turning a physics system — given as **text** (a question, a
description) or a **picture** (a scanned figure, a photo of the board) — into a
drawing or animation. It does not matter which tool draws it:

- **Manim** (2D course animations and slides — code in PhysicsAid),
- **Blender** (3D models and scenes — code in BlenderPhysics),
- **Whiteboards** (HTML/SVG/three.js boards the tutor builds step by step — code in PhysicsLearn).

All three follow the same look: black background, LaTeX-style lettering, colours
by meaning, mass labels inside bodies, axes behind objects.

## What is here

| Folder / file | What it holds |
|---|---|
| [`style/visual-style.md`](style/visual-style.md) | **The style** — background, fonts, colours, shapes, layout. The master copy. |
| [`style/diagram-rules.md`](style/diagram-rules.md) | Rules that keep a drawing *physically* right and readable (vectors on the body, nothing hidden, axes contain everything, how to check a render). |
| [`tokens/style.json`](tokens/style.json) | The same colours, fonts and sizes as data, so code reads them instead of retyping them. |
| [`tokens/style.css`](tokens/style.css) | The colours as CSS variables, for HTML/SVG whiteboards. |
| [`workflow/text-or-picture-to-animation.md`](workflow/text-or-picture-to-animation.md) | **The unified way**: the steps from a question or figure to a finished visual. |
| [`spec/scene-spec.md`](spec/scene-spec.md) | The short tool-neutral description of a system (bodies, slopes, springs, vectors, motion) written before any drawing. |
| [`spec/examples/`](spec/examples/) | Filled-in examples. |
| [`renderers/`](renderers/) | How each tool applies the style: [Manim](renderers/manim.md), [Blender](renderers/blender.md), [whiteboard](renderers/whiteboard.md). |

## How to use it (in one paragraph)

Give the AI the question text or the picture. It first writes a **scene spec**
(what objects exist, their sizes, what moves and by which equation), shows you a
**quick draft** still, and only after the picture is physically right does it
render the final animation in the tool you chose. Every step uses the colours
and fonts from this repository.

## Rules

- This repository holds **text and small code only** — no videos, renders or
  recordings. Renders stay in each project's `output/` folder or in Dropbox.
- When the style changes, change it **here first**, then the code copies
  (`PhAid_scene_toolbox.py` in PhysicsAid, `physkit/style.py` in
  BlenderPhysics) — see [`AGENTS.md`](AGENTS.md).
