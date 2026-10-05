# STEEL MERIDIAN

A browser FPS in the style of modern military multiplayer shooters, in **one self-contained `index.html`**: three.js (r186, via jsDelivr import map), no build step, no backend. Every texture, model and sound is generated in code.

**Play:** serve the folder with any static host (GitHub Pages works as-is), open `index.html`, then click **Firing Range**.

## Status — Phase 1 of 7

| Phase | Scope | State |
|---|---|---|
| 1 | Map, movement, collision, graphics pipeline, one rifle with full gun feel | **done** |
| 2 | All weapons + attachments, grenades, full HUD | next |
| 3 | Bots, TDM rules, practice mode | |
| 4 | Create-a-Class, XP / levels / unlocks | |
| 5 | Killstreaks | |
| 6 | P2P multiplayer (Trystero), lobby, room browser | |
| 7 | Polish: performance, balance, menus | |

## Controls

| Action | Key |
|---|---|
| Move / look | WASD / mouse (pointer lock) |
| Fire / aim down sights | Left / right mouse |
| Sprint | Shift (hold; toggle in settings) |
| Crouch (slide while sprinting) | C or Ctrl |
| Jump | Space |
| Reload | R |
| Pause / settings | Esc |

## Code layout

`index.html` holds a single module script split into sections: **CONFIG** (every tuning value) · DATA (weapon table, surfaces, settings) · UTIL · SAVE · AUDIO · RENDER · TEXTURES · MATERIALS · COLLISION · MAP · FX · INPUT · PLAYER · VIEWMODEL · ACTORS · WEAPONS · BOTS/NET (later phases) · UI · GAME.

- **Collision:** static triangles in three's `Octree`. Capsule, sphere and ray queries walk the Octree nodes without allocating. The player uses a `Capsule`.
- **Rendering:** ACES + sRGB, a PMREM sky environment, a PCF soft sun shadow fitted to the map, and an EffectComposer chain (world → optional GTAO → viewmodel → bloom → output → grade/vignette → SMAA/FXAA). The viewmodel has its own scene and camera, so it never clips into walls.
- **Textures:** tileable PBR sets (albedo, normal and AO/roughness/metal) for concrete, asphalt, brick, plaster, corrugated and painted metal, steel, wood, fabric, dirt, tile, polymer, camo and glove.
- **Audio:** buffers are pre-rendered with `OfflineAudioContext` (layered gunshots, mechanical reload sounds, per-surface footsteps and impacts). Playback goes through a compressor bus with a synthetic urban reverb.

A debug/test API is exposed as `window.__SM`. The headless test harness uses it.
