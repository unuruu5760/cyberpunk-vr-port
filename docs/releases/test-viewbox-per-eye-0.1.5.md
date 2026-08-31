# test-viewbox-per-eye-0.1.5

Test build from branch `feature/viewbox-per-eye-f10-ui`.  
Replace `CyberpunkVR_Stereo.dll` in your mod install. Delete `vrport.ini` to test defaults (center box **OFF**).

---

## What's included

### Center box on lens (opt-in, default OFF)

- F10 → **Tracking / Camera** → **Center box on lens**
- Aligns the picture with the headset **lens optical centre** (Quest 3 / canted optics).
- Rotates **render camera + OpenXR submit pose together** (no FOV number change).
- Use when lowering FOV for sharper PPD makes the view feel shifted (e.g. upward).

### Shared picture box sliders

- **Box vertical / horizontal** — move both eyes together (fine-tune on top of center box).

### Per-eye viewbox (stereo + VRCAM only)

- **Left / Right vertical & horizontal** — extra pitch/yaw **per eye** on top of the shared box.
- For asymmetric lens alignment or filling FOV margins (left eye slightly left, right slightly right).
- Requires **Stereo submit** + **VRCAM component** ON (F10 → Stereo tab). When off, sliders are parked and values restore when re-enabled.

### HUD fuse / Aim fuse

- When per-eye tuning splits the stereo views, 2D HUD and the aim dot can appear doubled.
- **HUD fuse** / **Aim fuse** reproject those overlays by angle (not a 2D pan) until they fuse.
- **0** = automatic from per-eye sliders; non-zero = manual trim.

### F10 UI improvements

- ReShade-style **reset** button on sliders (mod defaults).
- **Left/Right arrow** on focused slider: **0.1** step.
- **FOV runtime toggle**: unchecking restores your last **manual** FOV instead of snapping to 112°.

---

## Known limitations / bugs

| Issue | Cause | Workaround |
|-------|--------|------------|
| **Shadows misaligned** with per-eye sliders | Shadow cascades / atlas often shared or built for the base view; per-eye rotation is camera-only | Keep per-eye values **small**; use **shared Box** sliders first |
| **SSR / reflections drift** with per-eye sliders | SSR and temporal reprojection are view-dependent; extra rotation is not propagated into all history matrices | Same as above — minimal per-eye; prefer shared box |
| Per-eye sliders greyed out | Stereo submit or VRCAM off | Enable both in F10 → Stereo tab |
| HUD still doubled after per-eye tune | Fuse trim needed | Adjust **HUD fuse** / **Aim fuse** while looking at HUD / aim dot |
| Center box feels wrong on mono path | Per-eye + fuse paths target true stereo | On mono, use **shared box** only |

**Summary:** Per-eye tuning is a **visual alignment** tool, not a full lighting/reflection fix. For most users: **Center box ON + shared Box sliders** is enough; touch per-eye only if one lens is still off, and keep values low.

---

## Install

1. Download `CyberpunkVR_Stereo.dll` from this release.
2. Replace the DLL in your Cyberpunk VR Port plugin folder (same path as your current mod).
3. Optional: back up `vrport.ini` before testing.

## Feedback

Quest 3 / canted-lens testers welcome — comfort, judder, center alignment, HUD fuse, shadow/SSR at low per-eye values.
