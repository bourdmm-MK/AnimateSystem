# Scene spec — describe the system before drawing it

A scene spec is a short YAML file (or block in a chat) that says **what** is in
the picture, independent of **which tool** draws it. Units are SI (metres,
seconds, kilograms, degrees for angles). Colours are named by meaning
(`velocity`, `force`, `structure`…) from [`../tokens/style.json`](../tokens/style.json),
never as raw hex.

## Fields

```yaml
title: short name
source: text | picture (+ file name or question number)
view: 2d-front | 3d               # 2d-front = orthographic front view
frame: { width: 14, height: 8 }   # visible area in metres (or Manim units)

objects:                          # everything that is drawn
  - id: m1
    kind: block | ball | slope | floor | wall | spring | string | pulley | charge | axes
    size: ...                     # depends on kind (width/height, radius, length/angle)
    at: [x, y]                    # position of its centre (or start point)
    label: "m_1"                  # LaTeX; goes inside bodies
    color: body                   # meaning name; bodies default to body colours

vectors:                          # arrows attached to objects
  - on: m1
    quantity: velocity | acceleration | force | displacement | position
    direction: [dx, dy] | along: slope1 | angle: 30
    label: "\\vec v"

motion:                           # leave out for a still picture
  equations: "x'' = g sin(theta) - mu g cos(theta)"
  parameters: { g: 9.8, theta: 60, mu: 0 }
  duration: 4                     # seconds of animation
  events: ["t=1.2: m1 hits m3, they stick"]

steps:                            # optional: order things appear (whiteboard / lesson build-up)
  - draw: [floor, slope1]
  - draw: [m1]
  - draw: [vectors of m1]
```

Leave out what you do not need. A still picture needs only `objects` (and
maybe `vectors`).

## Examples

- [`examples/two_slopes_spring.yaml`](examples/two_slopes_spring.yaml) — the
  exam question with two slopes and a spring; it exists as a Manim scene
  (PhysicsAid `expermients/two_slopes_spring/`) and a Blender scene
  (BlenderPhysics `models/two_slopes_spring/`) drawn from the same description.
