# Steel Meridian: manual test checklist

Tick these off in a real browser (Chrome or Edge; Firefox works too) with a mouse. Each item says what to do and what you should see. If something fails, note the number and what happened.

Tip: Settings → Video → **Show FPS** puts a frame counter in the top-left corner. Keep it on while testing.

---

## Phase 2: weapons, attachments, grenades, HUD (Firing Range)

Start from the main menu → **Firing Range**.

### A. Loadout screen
1. Press **Esc → Loadout**. The panel lists 5 primaries on the left; the Secondary tab lists the VIPER-P9.
2. Click each primary in turn. Name, class, RPM, magazine size and the six stat bars change.
3. Pick the BRUTE and add **Vantage 3x** and **Vertical Grip**. Both chips light up and the counter reads (2 / 2).
4. Try a third attachment. You get the "Two attachments maximum" note and it isn't added.
5. Pick a second optic while one is equipped. It replaces the first (one per slot).
6. Stat bars: green means better than the stock gun, red means worse, and the thin white tick is the stock value.
7. Press **Equip**. A toast confirms, and you're holding the new gun with the scope on it.
8. Quit to the menu and come back. The loadout is remembered.

### B. Each weapon (repeat for all six)
For each one: fire single shots and a full magazine at a target, aim down sights, then do a tactical reload (with rounds left) and an empty reload.

9. **KESTREL-556:** steady auto; recoil climbs and drifts a little; peep sight lines up when aiming.
10. **BRUTE-762:** slower, harder hitting, more kick; notched rear sight and post line up when aiming.
11. **WASP-9:** very fast fire, light recoil, quick aim.
12. **MAULER-12:** 8-pellet spread (a cluster of impacts on a wall). Pump after every shot; you can't fire again until the pump finishes. Reload loads one shell at a time with a pump at the end if it was empty. Firing during a reload cancels it.
13. **LONGBOW-338:** one shot to the body at most ranges. Bolt cycles after each shot and the viewmodel hand works the bolt.
14. **VIPER-P9:** semi-auto; the slide kicks back on each shot and **locks open** when empty.
15. Every gun: the magazine leaves the gun during the reload and the ammo count refills at the right moment, not at the start.
16. Every gun: firing sounds are distinct per weapon.

### C. Attachments
17. **Reflex sight:** red dot in a clear housing; it lines up when aiming and zoom is slightly stronger than irons.
18. **3x scope:** full scope overlay with an orange chevron reticle; the viewmodel hides while scoped.
19. **Suppressor:** quieter, duller shot; smaller muzzle flash; a can on the barrel.
20. **Extended mag:** longer magazine on the model, +50% rounds, slightly slower reload.
21. **Vertical grip:** grip under the handguard with the left hand on it; less recoil.

### D. Sniper scope
22. Aim with the LONGBOW: the view zooms 6x and the full black scope overlay appears with a mil-dot reticle.
23. The view sways gently while scoped.
24. Hold **Shift** while scoped: the sway nearly stops and the breath bar drains.
25. Hold until the bar empties: "OUT OF BREATH", sway gets worse for ~2 s, then the bar refills.
26. Mouse sensitivity while scoped feels about 6x slower than at the hip (it scales with zoom).

### E. Swapping and melee
27. **1 / 2 / mouse wheel** swap primary ↔ pistol; the old gun drops, the new one raises (about half a second).
28. **V** melee: the rifle bashes forward. A target within ~2 m goes down in one hit (150 damage).
29. Melee a wall: impact puff and a thud.

### F. Grenades
30. **G** (frag): pin-pull sound, the viewmodel shows a grenade in the left hand; release to throw.
31. Hold **G**: "COOKING 3.4… 3.3…" counts down; a cooked grenade explodes sooner after landing.
32. Hold **G** too long: it explodes in your hand → death screen "KILLED BY YOURSELF [FRAG]" → respawn after 3 s.
33. Explosions: fireball, sparks, a smoke column that lingers ~2 s, dust ring, a scorch mark on the ground, camera shake, ringing ears and muffled sound if you're close.
34. Throw a frag hard at a wall up close: it bounces back and never passes through.
35. Frags hurt targets near them (they go down in one if close).
36. **Q** (flashbang): throw it in front of you while looking at it. White-out with ringing that fades over 2–4 s. Looking away when it pops makes it much shorter.
37. In the range, grenade counts refill a few seconds after use (top right of the ammo panel shows G 1 / Q 2).

### G. Health and damage
38. Get hurt by your own frag at a distance: health drops, the screen edges go red, a red arrow points to where it came from.
39. Wait 4 s without taking damage: health regenerates and the red fades.
40. The death screen shows the killer and weapon, and counts down "RESPAWNING IN 3 / 2 / 1".

### H. HUD
41. **Minimap** (top left): rotates with you; your arrow always points up, with a view cone. The N marker moves around the rim as you turn. Buildings, walls and streets are recognisable.
42. **Score/clock** (top centre) counts up in the range.
43. **Killfeed** (top right): "YOU [WEAPON] TARGET", with HEADSHOT tags on head kills. Entries fade after ~5 s.
44. **Killstreak icons** (bottom left): UAV 3 / AIRSTRIKE 5 / HELO 7 fill as you down targets without dying; they reset on death.
45. **Hitmarkers:** white on hit, red and larger on kills, with a tick sound.
46. **Damage numbers** float off targets in the range (Settings → Gameplay can turn them off).
47. **Tab** shows the scoreboard; release to hide.
48. Crosshair spreads when moving or firing from the hip and hides when aiming down sights.

### I. Regression (from Phase 1)
49. Movement: walk, sprint, crouch (C), slide (sprint + C), jump, the stairs in both buildings, landing dip.
50. Recoil: spray, release, and the aim settles almost all the way back down within a second.
51. Brightness looks the same as after the Phase 1 fix; the Brightness slider still works.
52. Low / Medium / High presets switch without errors.

---

## Phase 3: bots, Team Deathmatch, Practice vs Bots

Main menu → **Practice vs Bots**.

### J. Setup screen
53. The panel shows Bot Difficulty (RECRUIT / REGULAR / VETERAN), Score Limit (20 / 30 / 50) and Time Limit (5 / 10 / 15 min). Your choices are remembered next time.
54. The **Loadout** button opens the loadout screen; **Equip** brings you back to the setup screen with the new loadout listed.
55. **Back** (or Esc) returns to the main menu.

### K. Match flow
56. **Start Match:** you spawn at the south end with two blue teammates; "MATCH BEGINS IN 4…1" counts down and you can look around but not move or shoot.
57. "FIGHT" appears and everyone starts moving.
58. The top panel shows your team's score (blue, left), the enemy's (red, right) and a clock counting down from the time limit.
59. The first team to the score limit wins; otherwise the higher score wins when time runs out (equal = DRAW).
60. The results screen shows VICTORY / DEFEAT / DRAW, the final score, why it ended, your score / kills / deaths / K/D / assists / accuracy, and the full scoreboard.
61. **Play Again** starts a new match with the same settings; **Main Menu** returns to the menu.
62. **Esc** during a match pauses everything (it's offline); Resume carries on where you were.
63. Changing your loadout mid-match (Esc → Loadout) applies on your next spawn.

### L. Bots: what to watch for
64. Bots walk the lanes, go up the stairs into both buildings, and use the upper floors and windows.
65. They sprint when nothing is around and slow down / strafe / sometimes crouch in a firefight.
66. They don't shoot instantly: there's a short reaction delay, and their first shots are a bit off before they settle (much tighter on VETERAN).
67. They react to being shot from behind by turning toward you.
68. Unsuppressed shots draw them toward the noise; a suppressed weapon lets you flank more quietly.
69. They reload after a fight, and sometimes mid-fight when empty (a good window to push).
70. Badly hurt bots sometimes break off to cover, then come back after healing.
71. They occasionally throw frags at where you were hiding.
72. Bots blinded by your flashbang stop shooting accurately for a few seconds (you get a hitmarker when it catches an enemy).
73. Bots don't shoot through their own teammates, and friendly fire is off (your shots don't hurt blue bots, and theirs don't hurt you).
74. Bots don't get stuck on corners for long (they jump or re-route). Note anywhere one gets stuck repeatedly.
75. Compare difficulties: RECRUIT should feel beatable while learning the guns; VETERAN should punish standing still in the open.

### M. Bodies and animation
76. Soldiers hold their rifle at the shoulder with both hands on it, aim up/down with their torso, walk / strafe / sprint (rifle lowered) / crouch (kneeling).
77. Their rifle has a muzzle flash and you see tracers; gunshots come from the right direction and get quieter with distance.
78. On death they buckle and fall (backwards if shot from the front), stay down briefly, then respawn at their base about 3 s later.
79. Hitboxes: headshots on bots do more damage (HEADSHOT in the killfeed); shooting arms and legs does less.

### N. Team HUD
80. Blue name tags float over your teammates (through walls, when on screen).
81. Point your crosshair at an enemy: a red name tag appears over them.
82. Minimap: teammates are blue dots with a facing line; enemies who fire **unsuppressed** weapons flash as red dots for ~2 s.
83. Killfeed colours: you in gold, teammates blue, enemies red; assists give "+25 ASSIST", kills "+100" (+125 HEADSHOT) under the crosshair.
84. Bullets that miss you closely make a whiz/crack; damage arrows point at the shooter.
85. **Tab** scoreboard: both teams with score / kills / deaths / assists, sorted by score; dead players dimmed.
86. Your killstreak counter goes up with kills and resets when you die.

### O. Spawns
87. You and bots always spawn in your own base, away from enemies and out of their sight when possible.
88. Spawns don't stack two soldiers on the same spot.

### P. Performance
89. With Show FPS on, a full 3v3 match on Medium should hold close to your Phase 1 frame rate. Report the FPS you see in a big firefight with explosions.
90. Play two or three matches back to back: no slowdown, no stuck sounds, no leftover bodies from the previous match.

---

## Phase 4: Create-a-Class, XP, levels, unlocks, Barracks

Tip: Settings → Gameplay → **Unlock All (testing)** makes everything available straight away, so you can try camos and every class option without levelling. XP still counts. Do items 91–100 with it **off** first.

### Q. Levelling
91. The main menu shows **Create-a-Class** and **Barracks (Level 1)**.
92. Kills in a Practice match pop "+100" (+125 for a headshot). That's XP: ×0.8 on Recruit, ×1.3 on Veteran. A thin XP bar with your level sits at the bottom of the screen and fills as you go.
93. Levelling up mid-match plays a chime with a "LEVEL UP · n" banner and an "UNLOCKED: …" toast.
94. The results screen shows the XP breakdown (kills, headshots, assists, win / draw / loss bonus, time played, difficulty multiplier, total), the bar filling, and "LEVEL UP → n · UNLOCKED: …" when you level.
95. The Firing Range gives no XP and doesn't count toward career stats.

### R. Create-a-Class
96. At level 1: three default classes (ASSAULT, CLOSE QUARTERS, MARKSMAN) are usable. The five CUSTOM slots show "LEVEL 4" and can't be edited.
97. Default classes are read-only: clicking a weapon shows a note telling you to use a custom slot.
98. From level 4: click a custom class's name to rename it, then pick primary, secondary, attachments (max 2) and camo. Changes save as you make them.
99. Locked weapons, attachments and camos are dimmed with "UNLOCKS AT LEVEL n" / "LEVEL n" and can't be picked.
100. **Use Class** marks it ACTIVE. Practice setup shows "CLASS: name · weapons", and you spawn with it.
101. Mid-match: Esc → **Change Class** → Use Class says "takes effect on your next spawn", and your next life uses it. During the countdown it equips immediately.
102. Camos (Woodland 16, Desert 19, Urban 22, Night 26, Gold 30) recolour the primary weapon's body. The pistol keeps its finish.
103. The Firing Range keeps its own free Loadout (Esc → Loadout, everything unlocked), separate from your classes.

### S. Barracks
104. **Progress** tab: level badge, XP into the level, total XP, next unlock, and the full unlock list (green = unlocked, gold = next).
105. **Stats** tab: matches, wins, losses, W/L, kills, deaths, K/D, assists, headshots, accuracy, best streak, time played.
106. **Weapons** tab: kills per weapon with bars, and your favourite.

### T. Saving
107. Reload the page: level, XP, classes, the active class and stats are all still there.
108. Settings → **Reset All Data** returns you to level 1, default custom classes, zero stats and Unlock All off.
109. **Unlock All** on/off switches the gating instantly (check Create-a-Class before and after).

### U. Flashbang re-test (fixed after your report)
110. Throw a flashbang and turn fully away before it pops: no white-out, just ringing and muffled sound.
111. Side-on: a brief faint haze.
112. Looking at it: a full white-out that fades over 2–4 s.

---

## Coming next: Phase 5 tests (killstreaks)

What you'll be testing after the next update:

113. The streak icons light up at 3 / 5 / 7 kills without dying, and a key calls in the reward.
114. **UAV** (3): enemies show as red dots on your minimap for a while, refreshed by sweeps.
115. **Precision Airstrike** (5): you mark a spot and jets fly over and carpet it.
116. **Attack Helicopter** (7): a helicopter circles the map for a while, hunting enemies, and it can be shot down.
117. Bots earn and use killstreaks too; enemy ones are announced and can kill you.
118. Streaks reset on death, and kills from killstreaks don't build the next streak.
