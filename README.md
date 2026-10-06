# STEEL MERIDIAN

A browser FPS in the style of modern military multiplayer shooters, in **one self-contained `index.html`**: three.js (r186, via jsDelivr import map), no build step, no backend. Every texture, model and sound is generated in code.

**Play:** serve the folder with any static host (GitHub Pages works as-is) and open `index.html`. **Play Online** hosts or joins a 3v3 Team Deathmatch room with other people. **Practice vs Bots** is the same match offline. **Firing Range** is free practice with every weapon. Press Esc → **Loadout** to change weapons and attachments.

**Testing:** see [TESTING.md](TESTING.md) for the manual test checklist.

## Status — Phases 1–4 and 6 of 7

| Phase | Scope | State |
|---|---|---|
| 1 | Map, movement, collision, graphics pipeline, one rifle with full gun feel | done |
| 2 | All weapons + attachments, grenades, full HUD | done |
| 3 | Bots, TDM rules, practice mode | done |
| 4 | Create-a-Class, XP / levels / unlocks | done |
| 6 | P2P multiplayer (Trystero), lobby, room browser | **done** (built before Phase 5, on request) |
| 5 | Killstreaks | next |
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

## Play Online

Peer to peer over WebRTC with [Trystero](https://github.com/dmotz/trystero) (loaded from jsDelivr only when you open Play Online). Players find each other through public Nostr relays, then game traffic goes directly between browsers. There is no game server.

- **Room browser:** hosts announce their room every 2 s in a shared lobby channel, and a room drops off the list after 6 s of silence. The list shows name, host, players, mode / score limit / map, and whether a match is running.
- **Room lobby:** teams (auto-balanced, Switch Team if it keeps them even), ready-up, host-only settings (score limit, time limit, bot fill and bot difficulty), Choose Class. The host starts once everyone is ready. Up to 6 players (3 v 3). Bots fill the empty slots unless bot fill is off.
- **Host-authoritative:** the host runs the match: rules, clock, spawns, kills, assists and the bots. The host sends a 20 Hz snapshot (bots, clock, scores, health), plus events (kill, spawn, hit, roster, end) and a scoreboard sync once a second. Every player sends their own movement at 20 Hz to everyone. Remote soldiers are drawn 100 ms in the past, interpolated between samples, with a per-peer clock-offset estimate.
- **Hits:** you simulate your own movement and shots, so there's no input delay. Bullets that hit someone send a *claim* to the host. The host checks that claim against about a second of position history: the shooter really was there, and the target was at that distance with line of sight within the shooter's ping + 100 ms. It also checks fire rate and recomputes the damage from its own weapon table, then applies the hit. You see your hitmarker straight away (shooter-favoured). Grenade damage is worked out on the host.
- **Joining in progress:** you join a running match straight away and take a bot's slot on the team with fewer people. A player who leaves is replaced by a bot.
- **Host leaves → host migration:** the remaining player with the lowest id rebuilds the authoritative match from their mirror (scores, clock, stats, bot positions), takes over the bots, and carries on. The old host's slot becomes a bot. If no one can take over, the match ends cleanly ("HOST LEFT") with results and XP.
- **Esc** opens a menu without pausing (the match keeps running). XP and career stats count online matches, with no difficulty multiplier.
- **Testing without a second machine:** two browser windows side by side (not tabs; a hidden tab stops drawing). `?name=TWO` sets a different callsign, and `?net=local` swaps WebRTC for an in-browser test network (BroadcastChannel with simulated lag).
- **Soldier model:** remote players use the same procedural soldier as the bots, in team colours. I didn't use three.js's `Soldier.glb` example model because I couldn't confirm a CC0 licence for it (it appears to be a Mixamo-based asset).

## Progression and Create-a-Class

- **XP** comes from Practice and online matches: 100 per kill (+25 for a headshot), 25 per assist, a 500 / 350 / 250 bonus for a win / draw / loss, and 40 per minute played. Practice XP is scaled by bot difficulty (Recruit ×0.8, Regular ×1, Veteran ×1.3). The Firing Range gives no XP.
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
| Pause, loadout, settings (online: menu, no pause) | Esc |

## Code layout

`index.html` holds a single module script split into sections: **CONFIG** (every tuning value, including bot skill and match rules) · DATA (weapon table, attachments, grenades, surfaces, settings) · UTIL · SAVE · AUDIO · RENDER · TEXTURES · MATERIALS · COLLISION · MAP · FX · INPUT · PLAYER · VIEWMODEL · ACTORS · WEAPONS · GRENADES · NAV · BOTS · MATCH · NET · UI · GAME.

- **Match:** one Team Deathmatch rule set for every mode. `TDMMatch` is authoritative: offline practice, or the online host. Everything that happens is an event (kill / spawn / hit / roster / end). `Game.applyMatchEvent` applies an event on every machine and handles the local player's side: killfeed, XP, streak, death screen and respawn. Online clients run `ClientMatch`, a mirror fed by snapshots and events. Remote soldiers are `Puppet`s, interpolated from network samples.
- **Net:** `NetTransport` (Trystero, or the `?net=local` BroadcastChannel test transport) · `Lobby` (room announcements) · `Net` (one room: lobby state, match start, 20 Hz state and snapshots, events, hit claims with `LagComp` validation, shot and grenade replication, pings, join in progress, host migration). All rates and windows are in `CONFIG.NET`.

- **Navigation:** at load, a 0.5 m grid is sampled straight from the collision world. Downward rays find every floor level, a capsule test checks headroom, and knee-height rays connect neighbours. The graph is flood-filled from the spawns (≈15k walkable nodes in ~0.4 s), and paths use A* on typed arrays (≈0.2 ms each).
- **Bots:** perception covers a sight cone with line of sight, hearing gunfire and explosions, and turning toward whoever shot them. A state machine drives them through roam, engage, search and retreat. Their aim model has a reaction delay, a capped turn rate, aim error that settles over time, and recoil. Soldier bodies are rigidly skinned, with two-bone arm IK to keep both hands on the rifle and procedural walk / strafe / sprint / crouch / death animation.
- **Weapons:** one data table drives everything: damage falloff, hitbox multipliers, fire rate, magazine, reload timings, ADS time, spread, movement speed and a per-shot recoil pattern. `buildWeaponDef(id, attachments)` folds attachment modifiers into a cached runtime definition.
- **Collision:** static triangles in three's `Octree`. Capsule, sphere and ray queries walk the Octree nodes without allocating. The player uses a `Capsule`, and grenades use a swept ray plus a sphere.
- **Rendering:** ACES + sRGB, a PMREM sky environment, a PCF soft sun shadow fitted to the map, and an EffectComposer chain (world → optional GTAO → viewmodel → bloom → output → grade/vignette/damage/flash → SMAA/FXAA). The viewmodel has its own scene, camera and reflection environment, so it never clips into walls.
- **Viewmodels:** six procedural guns built from merged primitives, with gloved hands posed from a basis (back-of-hand and finger direction). Reloads, pump/bolt cycling, melee and grenade throws are keyframe tracks.
- **Textures:** tileable PBR sets (albedo, normal and AO/roughness/metal) for concrete, asphalt, brick, plaster, corrugated and painted metal, steel, wood, fabric, dirt, tile, polymer, camo and glove.
- **Audio:** buffers are pre-rendered with `OfflineAudioContext` (layered gunshots per weapon plus suppressed variants, mechanical reload sounds, per-surface footsteps and impacts, explosions). Playback goes through a compressor bus with a synthetic urban reverb and a concussion low-pass.

A debug/test API is exposed as `window.__SM`. The headless test harness uses it.
