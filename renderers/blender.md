# Blender (BlenderPhysics)

**Code lives in:** BlenderPhysics (`bourdmm-MK/BlenderPhysics`), locally
`../BlenderPhysics/`. Read its `AGENTS.md` first. Blender 5.3; every model is a
script `models/<name>/build.py` that builds the scene from empty.

## Two looks

- **Physics-question scenes** (a system from a question): the course style.
  Use `physkit.style` — `COURSE["velocity"]`, `COURSE["structure"]`… for
  colours, `label_font()` for serif italic labels, and finish with
  `physkit.finish(scene, name, args, style="question")` (flat colours on black).
  Use an orthographic front camera when reproducing a 2D figure.
- **3D object models** (a realistic pendulum, a cart): realistic materials from
  `physkit/materials.py`. Labels, vectors and axes added to them still follow
  the course colours.

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
