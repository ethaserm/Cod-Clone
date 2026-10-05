# STEEL MERIDIAN

A browser FPS in the style of modern military multiplayer shooters, in **one self-contained `index.html`**: three.js (r186, via jsDelivr import map), no build step, no backend. Every texture, model and sound is generated in code.

**Play:** serve the folder with any static host (GitHub Pages works as-is) and open `index.html`. **Practice vs Bots** is a 3v3 Team Deathmatch. **Firing Range** is free practice with every weapon. Press Esc → **Loadout** to change weapons and attachments.

**Testing:** see [TESTING.md](TESTING.md) for the manual test checklist.

## Status — Phase 4 of 7

| Phase | Scope | State |
|---|---|---|
| 1 | Map, movement, collision, graphics pipeline, one rifle with full gun feel | done |
| 2 | All weapons + attachments, grenades, full HUD | done |
| 3 | Bots, TDM rules, practice mode | done |
| 4 | Create-a-Class, XP / levels / unlocks | **done** |
| 5 | Killstreaks | next |
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

## Practice vs Bots

Team Deathmatch, 3v3: you and two bot teammates against three bots. First to the score limit (20 / 30 / 50) wins, or the leader when time runs out (5 / 10 / 15 min). Respawns take 3 s and friendly fire is off.

Bots come in three skill levels: **Recruit**, **Regular** and **Veteran**. Each level changes reaction time, turn speed, aim error and how fast it settles, burst control, recoil control, how far they see and hear, how often they strafe, crouch and throw grenades, and when they retreat to heal.

Bots use the same movement controller, weapons table, hitboxes and damage rules as the player. Unsuppressed gunfire gives away your position, both to bots and as red dots on the minimap.

## Progression and Create-a-Class

- **XP** comes from Practice matches: 100 per kill (+25 for a headshot), 25 per assist, a 500 / 350 / 250 bonus for a win / draw / loss, and 40 per minute played. All of it is scaled by bot difficulty (Recruit ×0.8, Regular ×1, Veteran ×1.3). The Firing Range gives no XP.
- **Levels 1–30.** Levels unlock weapons and attachments (REFLEX 2, WASP 3, Create-a-Class 4, SUPPRESSOR 5, BRUTE 6, EXT MAG 7, MAULER 9, GRIP 10, LONGBOW 12, 3X 14), then weapon camos (Woodland 16, Desert 19, Urban 22, Night 26, Gold 30).
- **Create-a-Class:** 3 default classes are always available, and 5 custom slots unlock at level 4. You can rename a class and pick primary, secondary, attachments (max 2) and camo. Change class from the pause menu mid-match; it applies on your next spawn.
- **Barracks:** level, XP, unlock roadmap, career stats and kills per weapon.
- Settings → Gameplay → **Unlock All (testing)** lifts the level gates for testing.

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

`index.html` holds a single module script split into sections: **CONFIG** (every tuning value, including bot skill and match rules) · DATA (weapon table, attachments, grenades, surfaces, settings) · UTIL · SAVE · AUDIO · RENDER · TEXTURES · MATERIALS · COLLISION · MAP · FX · INPUT · PLAYER · VIEWMODEL · ACTORS · WEAPONS · GRENADES · NAV · BOTS · MATCH · NET (Phase 6) · UI · GAME.

- **Navigation:** at load, a 0.5 m grid is sampled straight from the collision world. Downward rays find every floor level, a capsule test checks headroom, and knee-height rays connect neighbours. The graph is flood-filled from the spawns (≈15k walkable nodes in ~0.4 s), and paths use A* on typed arrays (≈0.2 ms each).
- **Bots:** perception covers a sight cone with line of sight, hearing gunfire and explosions, and turning toward whoever shot them. A state machine drives them through roam, engage, search and retreat. Their aim model has a reaction delay, a capped turn rate, aim error that settles over time, and recoil. Soldier bodies are rigidly skinned, with two-bone arm IK to keep both hands on the rifle and procedural walk / strafe / sprint / crouch / death animation.
- **Weapons:** one data table drives everything: damage falloff, hitbox multipliers, fire rate, magazine, reload timings, ADS time, spread, movement speed and a per-shot recoil pattern. `buildWeaponDef(id, attachments)` folds attachment modifiers into a cached runtime definition.
- **Collision:** static triangles in three's `Octree`. Capsule, sphere and ray queries walk the Octree nodes without allocating. The player uses a `Capsule`, and grenades use a swept ray plus a sphere.
- **Rendering:** ACES + sRGB, a PMREM sky environment, a PCF soft sun shadow fitted to the map, and an EffectComposer chain (world → optional GTAO → viewmodel → bloom → output → grade/vignette/damage/flash → SMAA/FXAA). The viewmodel has its own scene, camera and reflection environment, so it never clips into walls.
- **Viewmodels:** six procedural guns built from merged primitives, with gloved hands posed from a basis (back-of-hand and finger direction). Reloads, pump/bolt cycling, melee and grenade throws are keyframe tracks.
- **Textures:** tileable PBR sets (albedo, normal and AO/roughness/metal) for concrete, asphalt, brick, plaster, corrugated and painted metal, steel, wood, fabric, dirt, tile, polymer, camo and glove.
- **Audio:** buffers are pre-rendered with `OfflineAudioContext` (layered gunshots per weapon plus suppressed variants, mechanical reload sounds, per-surface footsteps and impacts, explosions). Playback goes through a compressor bus with a synthetic urban reverb and a concussion low-pass.

A debug/test API is exposed as `window.__SM`. The headless test harness uses it.
