# Steel Meridian: manual test checklist

Tick these off in a real browser (Chrome or Edge; Firefox works too) with a mouse. Each item says what to do and what you should see. If something fails, note the number and what happened.

Tip: Settings → Video → **Show FPS** puts a frame counter in the top-left corner. Keep it on while testing.

> **Still to test (reminder):** Phase 4 (sections Q–U, items 91–112), Online (V–Z, 113–140) and Phase 5 killstreaks (AA–EE, 141–159). Phases 2–3 were reported working, apart from the flashbang fix (U, 110–112).

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

## Online play (built before killstreaks)

**How to test it.** You need two copies of the game running:

- **Two computers** (best): open the GitHub Pages link on both.
- **One computer**: two **separate browser windows** side by side. Don't use two tabs in one window, because a hidden tab stops drawing. Both windows share your saved data, so add `?name=TWO` to the end of the second window's address to give it a different callsign.
- **No internet / quick check**: add `?net=local` to both windows' addresses (for example `…/index.html?net=local&name=TWO`). They then talk through a test network inside the browser with about 40 ms of simulated lag, without WebRTC or any relays.

### V. Room browser
113. Main menu → **Play Online**. After a moment the status reads "SEARCHING FOR ROOMS". If the networking library can't load, you get an error message instead.
114. Type a callsign. It's remembered next time.
115. **Create Room**: set a name (optional), score limit, time limit, bot fill on/off and bot difficulty. **Create** puts you in the room lobby as HOST on Team A.
116. In the other window, Play Online lists the room within a few seconds: name, host, players 1 / 6, "TDM · 30 · SALT MARKET", IN LOBBY. Close the host window and the room drops off the list within about 6 s.
117. **Join**: you land on Team B (auto-balance) as NOT READY, and the host gets a "… joined the room" toast.

### W. Room lobby
118. The joiner presses **Ready** and the host sees READY. **Start Match** stays greyed out until everyone is ready. A host on their own can start straight away with bots.
119. The host can change the settings in the lobby, and the joiner sees them update (read-only for them).
120. **Switch Team** works if teams stay even (at most one apart, at most 3 per team). Otherwise you get "Teams would be uneven."
121. Empty slots show BOT (bot fill on) or OPEN SLOT (off).
122. **Choose Class** opens Create-a-Class and brings you back to the lobby. The CLASS line updates.
123. After a couple of seconds, each other player's ping shows next to their name.
124. **Leave Room** goes back to the room browser.

### X. Match
125. Start: both windows load into the match: "MATCH BEGINS IN 4…", then FIGHT. The joiner may need to click once ("CLICK TO CONTINUE"), because browsers only lock the mouse after a click.
126. The other player is a soldier in their team's colour. They move smoothly (drawn about 0.1 s in the past) and crouch, sprint, aim up and down, reload and switch weapons. Their footsteps and gunshots come from where they are.
127. A teammate has a blue name tag and a blue minimap dot. An enemy gets a red name tag only while under your crosshair, and their unsuppressed shots flash red on your minimap.
128. Shoot the other player: you get the hitmarker straight away. They get damage arrows and the red screen edge. Kills show in both killfeeds with the right names, and the right team's score goes up.
129. The host runs the bots. They're in the same places and get the same kills in both windows.
130. Frags and flashbangs thrown by either player appear for both. Frag damage counts (you get a hitmarker when yours hits), and a flashbang blinds whoever is looking at it.
131. When you die you get the death screen, then respawn at your base after about 3 s. The host decides the spawn.
132. **Tab** scoreboard: both players are listed by callsign, the host's row reads HOST, bots read BOT, and everyone else shows their ping in ms.
133. **Esc** opens a MENU, not PAUSED: the match keeps running and you can be shot while it's open. Change Class and Settings work. **Leave Match** leaves.
134. XP: kills, assists and the match bonus count online too, with no difficulty multiplier. Career stats in the Barracks include online matches.

### Y. Joining in progress, leaving, the host leaving
135. With a match running, open a third window (or leave and rejoin from the second). The browser shows the room as IN MATCH. **Join** drops you straight into the live match, replacing a bot on the team with fewer people.
136. A player who leaves mid-match is replaced by a bot, with a "… left the room" toast.
137. **Host migration**: the host leaves mid-match (Leave Match or closes the window). Everyone else gets a toast ("… left. X is taking over as host" or "You are now the host"). The match carries on with the same score and clock, and the old host's slot becomes a bot. If it can't carry on, the match ends with "HOST LEFT".
138. End of match: the results line reads "… · ONLINE · room name". **Back to Lobby** returns you to the room, where you can ready up and start again.

### Z. Real-world network check
139. If you can, play a few minutes with someone on a different internet connection. Note the ping on the scoreboard, whether movement looks smooth or jumpy, and whether hits register when they should.
140. If Play Online never finds rooms, or Join says "Could not reach the host", note which browsers and networks were involved. Some work or school networks block peer-to-peer connections.

---

## Phase 5: killstreaks

Practice vs Bots on **Recruit** is the easiest place to string kills together. Settings → Gameplay → Unlock All has no effect on killstreaks: you have to earn them.

### AA. Earning
141. Get 3 kills without dying. The UAV icon (bottom left) turns gold and pulses, its label reads PRESS 3, and "UAV READY · PRESS 3" appears under the score panel with a chime.
142. At 5 kills, AIRSTRIKE reads PRESS 4. At 7, HELO reads PRESS 5. The STREAK counter shows your current run.
143. Dying resets the streak, but rewards you've earned stay until you use them. Earn the same one twice and its label shows ×2.
144. Kills by your airstrike or helicopter count for score and XP, but don't add to your streak.
145. Press 3 / 4 / 5 for a reward you haven't earned: a red note tells you how many kills it needs.

### BB. UAV (3 kills)
146. Press 3: "FRIENDLY UAV ONLINE" with a radio beep, and a drone circles high above the map. For 30 s, every 2 s, every enemy flashes as a red dot on your minimap with a soft ping.
147. When the enemy calls one in, you get "ENEMY UAV ONLINE" in red with a warning beep, and enemy bots home in on you more directly.

### CC. Precision Airstrike (5 kills)
148. Press 4: your gun drops and a red designator frame appears. A red circle, two lines and an arrow on the ground show where the bombs will land. The arrow points the way the jets will fly, which is the way you're facing.
149. Aim at a wall or the sky and the frame turns grey ("AIM AT OPEN GROUND INSIDE THE MAP"). Roofs and streets are fine.
150. Click: "FRIENDLY AIRSTRIKE INBOUND", and an orange marker appears on your minimap. About 2.5 s later two jets scream overhead (the engine pitch drops as they pass) and lay two lines of 4 big explosions along the mark.
151. Your own airstrike can't hurt you or your teammates. Enemies caught in it die ([AIRSTRIKE] in the killfeed). Anyone under a solid roof is protected.
152. Right click, or 4 again, cancels without using it up.

### DD. Attack Helicopter (7 kills)
153. Press 5: "FRIENDLY ATTACK HELICOPTER INBOUND". A helicopter with a team-coloured stripe flies in from your side, rotor thumping, patrols over the map for 40 s and then flies off.
154. It hunts the enemies it can see: a short wind-up, then bursts from its nose gun with tracers and impacts. Kills show as [HELICOPTER] and are credited to you.
155. Helicopters show on everyone's minimap: blue for your team's, red for the enemy's.
156. An enemy helicopter can be shot down. It's armoured (bullets do about a third of their damage, so roughly three rifle magazines). It smokes once it's badly damaged, then spins down trailing smoke and crashes in a big explosion. Whoever downs it gets "+150 HELICOPTER DOWN", and the killfeed shows "[weapon] ATTACK HELICOPTER".
157. Bots shoot at enemy helicopters when there's no soldier in view.

### EE. Bots and online
158. Bots earn and use killstreaks too: UAVs are the most common, airstrikes and helicopters come when a bot gets on a run. Enemy ones are announced in red and can kill you.
159. Online, all three work for every player. The host checks that you really earned it, and everyone sees the same jets, bombs and helicopter. Shooting an enemy helicopter online damages it and gives you hitmarkers.

---

## Coming next: Phase 7 tests (polish)

Likely topics. The final list depends on your feedback from the tests above:

160. Settings → Keys lets you rebind every action.
161. Steadier frame rate in big fights (target: 60 FPS on Medium on a mid-range laptop).
162. A balance pass on weapons, bots and killstreaks, based on what you report.
163. Menu polish: transitions, hover sounds, results-screen detail.
