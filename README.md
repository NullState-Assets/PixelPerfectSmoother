# PixelPerfectSmoother — Lite

> **Stop fighting your engine. Ship faster.**

---

## The Problem

Camera2D smoothing is jittery with pixel art.

Godot's built-in position smoothing rounds to whole pixels *after* interpolating, discarding the sub-pixel remainder every frame. The result: the camera snaps instead of glides, and sprite edges crawl during movement. There is no clean built-in fix.

---

## The Solution

Drop `script.gd` onto your Camera2D node. It replaces the engine's smoothing with a high-precision float position that is tracked separately, smoothed independently, and only snapped to the pixel grid at the final render step.

No plugins. No autoloads. One file.

---

## What's in the Lite Version

- Sub-pixel accurate position tracking and smoothing
- Configurable follow speed and pixel size via Inspector
- Pixel grid snapping (toggle on/off)
- Static world-space offset (`base_offset`)
- World boundary clamping
- `snap_to_target()` and `set_follow_target()` public API

## What's in the Full Version

The full version adds **velocity-based lookahead**: the camera reads your CharacterBody2D's `velocity` and shifts ahead of movement direction, giving a cinematic anticipation feel. Two exports control strength and smoothing independently so you can dial in the exact camera personality your game needs.

**Full version on itch.io:** https://nullstateassets.itch.io

---

## Quick Start

1. Copy `script.gd` into your Godot project.
2. Attach it to your Camera2D node (replaces it — Camera2D is the base class).
3. Set `follow_target` to your player node in the Inspector.
4. Hit **Play**.

---

## Compatibility

| Engine    | Language  | Tested On    |
|-----------|-----------|--------------|
| Godot 4.x | GDScript  | 4.2, 4.3     |

---

## License

MIT License. Free for personal and commercial use. Attribution appreciated but not required.
