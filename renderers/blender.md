# Blender (BlenderPhysics)

**Code lives in:** BlenderPhysics (`bourdmm-MK/BlenderPhysics`), locally
`../BlenderPhysics/`. Read its `AGENTS.md` first. Blender 5.3; every model is a
script `models/<name>/build.py` that builds the scene from empty.

## Two looks

- **Physics-question scenes** (a system from a question): the course style.
  Use `physkit.style` — `COURSE["velocity"]`, `COURSE["structure"]`… for
  colours — and finish with
  `physkit.finish(scene, name, args, style="question")` (flat colours on black).
  Use an orthographic front camera when reproducing a 2D figure.
- **Question scenes shown in 3D:** `style="question3d"` — the same colours with
  shaded faces. Lessons from `models/collision_pi` (Marianna liked the result):
  - Render the **text/graph as a separate flat layer** over the shaded 3D layer
    (ffmpeg overlay); one shared lighting makes the text grey and dim. 1080p with
    32-sample anti-aliasing; brighten only the 3D layer (exposure ≈ +0.7).
  - **Keep the camera level** (no tilt) so walls stand upright on the floor; frame
    with the lens shift (`shift_y`), and move the text layer by
    `shift_y × frame width` to keep it in place.
  - Reels: `.\tools\run.ps1 <name> -mode preview -reel -resolution 1920`.
- **3D object models** (a realistic pendulum, a cart): realistic materials from
  `physkit/materials.py`. Labels, vectors and axes added to them still follow
  the course colours.

## Lettering — the same font as Manim

Use `physkit/latex.py`, so labels look exactly like the Manim ones:

- `tex(body, em, color, loc)` — runs real LaTeX (MiKTeX + dvisvgm) and imports
  the result as a flat curve facing the camera (−y). Cached in `output/_tex`.
  Use it for every symbol and equation (`m_1`, `\vec v`, `\theta`…).
- `manim_em(font_size, frame_width_m)` — the letter size that matches a Manim
  `font_size` for a camera of that width (measured: 1 em = 0.4979 Manim units
  at `font_size` 48).
- `number(text, em, color, loc)` — a changing readout (like Manim's
  `DecimalNumber`) in Latin Modern, `C:\Windows\Fonts\lmroman10-regular.otf`;
  update it through `obj.data.body`.

Known quirks:
- LaTeX's `\times` imports badly — use the font's × character instead.
- Latin Modern text has no Greek letters, so θ, ω… must come from `tex()`.
- `label_font()` (Times italic) is only a **fallback** when LaTeX is missing.

Example: `models/wedge_ramp_q2/build.py`.

## From a scene spec

Spec parameters become named SI constants at the top of `build.py`; motion is
integrated from the equations in the script (1 Blender unit = 1 metre).

## Commands

Draft still: `.\tools\run.ps1 <name> -mode preview -still` (≈ seconds).
Preview video: `-mode preview` (≈ 0.1 s/frame). Final: `-mode final`
(Eevee ≈ 2–3 s/frame at 720p). Renders go to `output/`, never git.

## Examples

`models/two_slopes_spring/`, `models/wedge_ramp_q2/` (question style),
`models/pendulum/` (object model).
