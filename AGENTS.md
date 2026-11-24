# AnimateSystem — agent instructions

Read [README.md](README.md) first. This repository is the **source of truth for
the visual style** of every physics visual made for Marianna (Manim, Blender,
whiteboards, any image), and for the **workflow** from a text or picture to an
animation.

## Rules

- **The user is a teacher, not a developer.** Explain in plain words; make the
  technical choices yourself and ask only about content (what to show, how it
  should look).
- **Before drawing anything**, read [`style/visual-style.md`](style/visual-style.md)
  and [`style/diagram-rules.md`](style/diagram-rules.md), then follow
  [`workflow/text-or-picture-to-animation.md`](workflow/text-or-picture-to-animation.md).
- **Whiteboards:** before showing one, go through PhysicsLearn `knowledge-base/whiteboard-checklist.md`
  (required; it collects every board rule from Marianna's reviews).
- **Give a time estimate before rendering** (speeds are in the workflow file).
- **Keep the copies in step.** The style exists in three places:
  1. here — `style/visual-style.md` and `tokens/style.json` (the master),
  2. PhysicsAid — `PhysicsAid_toolbox/PhAid_scene_toolbox.py` (Manim constants),
  3. BlenderPhysics — `lib/physkit/style.py` (`COURSE` dictionary).
  When a colour, font or size changes, change 1 first, then 2 and 3 in the same
  session, and say so. If a code copy disagrees with this repository, this
  repository wins unless the user says the code is right.
- **No big media in git.** Text, JSON, CSS and small scripts only. Example
  images for the style guide must be small PNGs (< 300 KB) and only if the user
  wants them.
- The actual drawing code lives in the other projects (see `renderers/`). Do not
  copy Manim or Blender scenes into this repository — link to them.

## Workspace context

This repository sits in the local `PhysicsWork` folder next to PhysicsLearn
(the tutor brain), PhysicsAid (Manim studio) and BlenderPhysics (3D workshop).
The workspace `../README.md` maps where all data lives.
