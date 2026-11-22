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
  `MathTex`/`Tex` in Manim; KaTeX/MathJax or a serif italic in HTML/SVG; the
  closest serif italic font in Blender. Subscripts are real subscripts (`m_1`, `y_2`).
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
- **Guide lines** (projections, distances, dimensions): dashed, `GRAY_A`,
  behind the objects.
- **Charges:** circles marked + (red) or − (blue). Field into the page ×, out
  of the page ⊙.
- **Axes:** green, with arrow heads, behind everything, sized to contain the
  whole drawing.

## Layout

- **Mass labels go inside their body** (`m₁` inside block 1), sized to fit. Make
  the body big enough; put the label beside it only if it truly cannot fit.
- **Axes, dashed guide lines and helper arrows are drawn behind the objects**, so
  they never cover the system. Text sits in front.
- Never hide a given, label or angle mark; vectors start on their body (full rules in
  [`diagram-rules.md`](diagram-rules.md)).
- A "whiteboard" means building the picture step by step (drawing it in, then
  adding to it) — **in this same style**, not a white background or handwriting.

## Per tool

- **Manim:** import the palette and sizes from `PhAid_scene_toolbox`
  (`position_color`, `velocity_color`, `axes_color`, `def_color`, `font_size`…)
  instead of redefining them.
- **Blender (BlenderPhysics):** black world background, colours from the table,
  serif italic text objects, orthographic front camera when reproducing a 2D
  question figure.
- **HTML/SVG whiteboards (PhysicsLearn):** black canvas, colours from the table,
  KaTeX/MathJax (or serif italic) for every symbol.
