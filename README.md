# STEEL MERIDIAN

A browser FPS in the style of modern military multiplayer shooters, in **one self-contained `index.html`**: three.js (r186, via jsDelivr import map), no build step, no backend. Every texture, model and sound is generated in code.

**Play:** serve the folder with any static host (GitHub Pages works as-is), open `index.html`, then click **Firing Range**. Press Esc → **Loadout** to change weapons and attachments.

## Status — Phase 2 of 7

| Phase | Scope | State |
|---|---|---|
| 1 | Map, movement, collision, graphics pipeline, one rifle with full gun feel | done |
| 2 | All weapons + attachments, grenades, full HUD | **done** |
| 3 | Bots, TDM rules, practice mode | next |
| 4 | Create-a-Class, XP / levels / unlocks | |
| 5 | Killstreaks | |
| 6 | P2P multiplayer (Trystero), lobby, room browser | |
| 7 | Polish: performance, balance, menus | |

## Arsenal

| Weapon | Class | Fire | Damage (near → far) | RPM | Mag |
|---|---|---|---|---|---|
| KESTREL-556 | Assault rifle | Auto | 30 → 21 | 750 | 30 |
| BRUTE-762 | Assault rifle | Auto | 36 → 26 | 610 | 25 |
| WASP-9 | SMG | Auto | 26 → 17 | 920 | 32 |
| MAULER-12 | Shotgun | Pump, 8 pellets | 22 → 5 per pellet | 70 | 6 (shell by shell) |
| LONGBOW-338 | Sniper | Bolt | 110 → 96 | 46 | 5 |
| VIPER-P9 | Pistol | Semi | 28 → 18 | 420 | 15 |

Attachments (max two, one per slot): R7 Reflex sight, Vantage 3x scope, suppressor (keeps you off the enemy minimap), extended magazine, vertical grip. Lethal: cookable frag (G). Tactical: flashbang (Q).

## Controls

| Action | Key |
|---|---|
| Move / look | WASD / mouse (pointer lock) |
| Fire / aim down sights | Left / right mouse |
| Sprint | Shift (hold; toggle in settings) |
| Hold breath (scoped) | Shift |
| Crouch (slide while sprinting) | C or Ctrl |
| Jump | Space |
| Reload | R |
| Melee | V |
| Swap weapon | 1 / 2 / mouse wheel |
| Frag (hold to cook) / flashbang | G / Q |
| Scoreboard | Tab |
| Pause, loadout, settings | Esc |

## Code layout

`index.html` holds a single module script split into sections: **CONFIG** (every tuning value) · DATA (weapon table, attachments, grenades, surfaces, settings) · UTIL · SAVE · AUDIO · RENDER · TEXTURES · MATERIALS · COLLISION · MAP · FX · INPUT · PLAYER · VIEWMODEL · ACTORS · WEAPONS · GRENADES · BOTS/NET (later phases) · UI · GAME.

- **Weapons:** one data table drives everything: damage falloff, hitbox multipliers, fire rate, magazine, reload timings, ADS time, spread, movement speed and a per-shot recoil pattern. `buildWeaponDef(id, attachments)` folds attachment modifiers into a cached runtime definition.
- **Collision:** static triangles in three's `Octree`. Capsule, sphere and ray queries walk the Octree nodes without allocating. The player uses a `Capsule`, and grenades use a swept ray plus a sphere.
- **Rendering:** ACES + sRGB, a PMREM sky environment, a PCF soft sun shadow fitted to the map, and an EffectComposer chain (world → optional GTAO → viewmodel → bloom → output → grade/vignette/damage/flash → SMAA/FXAA). The viewmodel has its own scene, camera and reflection environment, so it never clips into walls.
- **Viewmodels:** six procedural guns built from merged primitives, with gloved hands posed from a basis (back-of-hand and finger direction). Reloads, pump/bolt cycling, melee and grenade throws are keyframe tracks.
- **Textures:** tileable PBR sets (albedo, normal and AO/roughness/metal) for concrete, asphalt, brick, plaster, corrugated and painted metal, steel, wood, fabric, dirt, tile, polymer, camo and glove.
- **Audio:** buffers are pre-rendered with `OfflineAudioContext` (layered gunshots per weapon plus suppressed variants, mechanical reload sounds, per-surface footsteps and impacts, explosions). Playback goes through a compressor bus with a synthetic urban reverb and a concussion low-pass.

A debug/test API is exposed as `window.__SM`. The headless test harness uses it.
