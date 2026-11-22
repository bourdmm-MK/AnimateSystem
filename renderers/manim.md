# Manim (PhysicsAid)

**Code lives in:** PhysicsAid (`bourdmm-MK/PhysicsAid`), locally `../PhysicsAid/`.
Read its `AGENTS.md` first.

## Applying the style

- Import colours and sizes from the toolbox — do not retype them:

  ```python
  from PhysicsAid.PhysicsAid_toolbox.PhAid_scene_toolbox import (
      position_color, displacement_color, distance_color, velocity_color,
      acceleration_color, def_color, time_color, axes_color,
      font_size, def_font_size,
  )
  ```

- Background: Manim's default black. All symbols with `MathTex` / `Tex`.
- Bodies: `Rectangle(fill_color="#C8BD99", fill_opacity=1, stroke_color=GREY_E)`
  with a `MathTex(..., color=BLACK)` label placed at its centre and scaled to fit.
- Structure (slopes, floor, springs, strings): `GREY_B`. Forces and `g`: `RED`.
- Draw order: add axes and dashed guides **first** (or give them a lower
  `z_index`) so bodies and vectors sit on top.

## From a scene spec

One scene class per spec. Put the spec's `parameters` as constants at the top of
the file and compute motion with `ValueTracker` / updaters from the equations.

## Commands

Draft still: `manim -ql -s file.py SceneName`. Final: `manim -qh file.py SceneName`.
Use the PhysicsAid `.venv` (do not rebuild it with `uv sync`).

## Examples to copy from

`expermients/two_slopes_spring/`, `expermients/wedge_ramp_q2/`,
`expermients/two_mass_movable_pulley/`, `expermients/ball_between_two_springs/`.
