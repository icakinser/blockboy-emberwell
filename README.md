# Emberwell

*A jetpack cave explorer made with [BlockBoy Game Foundry](https://github.com/icakinser/Blockboy-Game-Foundry), a block-based game engine.* This repo holds the playable game, its cartridge, and a step-by-step tutorial that rebuilds it from an empty cartridge.

<p align="center"><img src="screenshots/player.png" width="420" alt="Emberwell running in the BlockBoy player"></p>

**Emberwell** is a jetpack cave explorer. Four Ember hearts fell from Kettlemoor's furnace into the Underflue caves. Tam the sweep goes down with a steam puffer pack to bring them back to the Furnace lift. The cave is one open scene of 4 × 4 screens, and the hearts can be fetched in any order:

1. **Chimney top:** ride the updraft in the chimney; it lifts harder than the pack can.
2. **Cistern alcove:** carry the heavy anvil stone off its ledge; it sinks onto a weight plate under the water and holds the sluice gate open.
3. **Rubble gallery:** cut the rubble with the cutter (F) from the old toolbox in the mite warren.
4. **Brass vault:** swim down the siphon to the fungus grotto, throw a glowcap to the Gnasher so it eats and dozes, then roll a pebble through the mousehole to ring the old bell, which opens the brass gate. A geyser lifts you back out.

## Play it

- **In your browser:** download [`index.html`](index.html) and open it. The whole game is in that one file and needs no install or internet connection.
- **On the web:** turn on GitHub Pages for this repo (Settings > Pages > Deploy from branch `main`, folder `/`) and the game plays at `https://icakinser.github.io/blockboy-emberwell/`.
- **In BlockBoy:** open [`emberwell-cartridge.json`](emberwell-cartridge.json) with the editor's **Import** button to see and edit every object, block and rule. The game also ships with BlockBoy itself under **NEW > EMBERWELL**.

The controls are listed in [Controls in the finished game](#controls-in-the-finished-game) below.

## Screenshots

| | |
|---|---|
| <img src="screenshots/01-furnace-lift.png" width="400" alt="The Furnace lift, where Tam starts"><br>The Furnace lift, where Tam starts | <img src="screenshots/02-puffer-pack.png" width="400" alt="Flying with the steam puffer pack"><br>Flying with the steam puffer pack |
| <img src="screenshots/03-mite-warren.png" width="400" alt="The mite warren"><br>The mite warren | <img src="screenshots/04-cistern.png" width="400" alt="The cistern"><br>The cistern |
| <img src="screenshots/05-rubble-gallery.png" width="400" alt="The rubble gallery"><br>The rubble gallery | <img src="screenshots/06-fungus-grotto.png" width="400" alt="The fungus grotto"><br>The fungus grotto |
| <img src="screenshots/07-old-bell.png" width="400" alt="The old bell and the brass vault"><br>The old bell and the brass vault | |

## What's in this repo

| File | What it is |
| --- | --- |
| `index.html` | The standalone game, exported from BlockBoy |
| `emberwell-cartridge.json` | The game's cartridge, for loading into the BlockBoy editor |
| `screenshots/` | The pictures in this README |

## Tutorial: build Emberwell step by step

**Emberwell** is a jetpack cave explorer. Four Ember hearts fell from Kettlemoor's furnace into the Underflue caves. Tam the sweep goes down with a steam puffer pack to bring them back to the Furnace lift. The cave is one open scene of 4 × 4 screens, and the hearts can be fetched in any order:

1. **Chimney top:** ride the updraft in the chimney; it lifts harder than the pack can.
2. **Cistern alcove:** carry the heavy anvil stone off its ledge; it sinks onto a weight plate under the water and holds the sluice gate open.
3. **Rubble gallery:** cut the rubble with the cutter (F) from the old toolbox in the mite warren.
4. **Brass vault:** swim down the siphon to the fungus grotto, throw a glowcap to the Gnasher so it eats and dozes, then roll a pebble through the mousehole to ring the old bell, which opens the brass gate. A geyser lifts you back out.

This tutorial rebuilds the whole game from an empty cartridge, with every block setting and every rule. Every block it uses is described in [the block reference](https://github.com/icakinser/Blockboy-Game-Foundry/blob/main/docs/BLOCK-REFERENCE.md).

**What you will learn:** a jetpack hero with fuel and momentum, fuel vents and pickups, carry and throw, physics objects that float, sink, bounce and press plates, water with a current, wind zones and updrafts, an ecosystem of creatures that hunt and flee each other, bait, an impact switch rung by a thrown object, an item found in a chest, and building a big cave map with the Brush.

**Time:** about 3 hours. The cave rock is the slow part; Part 3 shows how to paint it quickly.

---

### Before you start

- **Keep the finished game open for comparison.** In BUILD mode click **NEW** (bottom of the editor) and choose **EMBERWELL**. Play it once, then save your own work to a separate file.
- **Coordinates.** Every object gives `x, y, w × h` in pixels; type them into the X, Y, W, H boxes in the Object Inspector. The cave is drawn on a **16 px tile grid**, so most positions are multiples of 16. Set the editor **SNAP** to 16 while you build rock and 8 for props.
- **Kinds.** "Place a Spikes" means pick **Spikes** in the Toolbox and click the map. Each kind comes with starter blocks; the steps say which to keep. Remove a block with the **×** on its card.
- **Settings** are written as `Setting = value` using the inspector's names; anything not mentioned stays at its default.
- **Rules:** select an object, click **ADVANCED**, then **ADD LOGIC RULE**.
- **Playtest often** with Ctrl/⌘+Enter; **E** returns to the editor.

#### Controls in the finished game

| Key                | Does                                                          |
| ------------------ | ------------------------------------------------------------- |
| Left / Right       | Walk, or push sideways in the air                             |
| Space / Z / Up (A) | Fire the puffer pack (hold)                                   |
| X (B)              | Pick up the thing in front of you; press again to throw it    |
| Down + X           | Roll the carried thing along the floor instead of throwing it |
| F                  | Cutter (after the toolbox)                                    |

---

### Part 1: Set up the scene

1. Click **NEW**, then **EMPTY GAME**.
2. Rename the scene **THE UNDERFLUE**. Set **W = 1280**, **H = 960** (80 × 60 tiles, 4 × 4 screens).
3. **CAMERA = Follow player.** The camera glides with Tam instead of snapping rooms.
4. Make the palette: click the palette button (top right), **COPY** a built-in palette, name it **Emberwell** and set Ink `#1a1420`, Dark `#3b3046`, Light `#c8743a`, Paper `#f2d9a6`. Click **USE FOR THIS LEVEL**.
5. **SKY = clear**, **HORIZON = none**, **WEATHER = embers**, **INTRO = BRING 4 EMBER HEARTS BACK TO THE FURNACE LIFT**.
6. Optional: open **SCENE STUDIO** (or **BACKGROUND & GRAPHICS**) and paint a dark cave mural on the background with a parallax of about 20 so it drifts slowly behind the rock.
7. Delete the ground strip the empty game started with.

The cave layout, one screen per box:

|                  | x 0 to 320                                | x 320 to 640         | x 640 to 960 | x 960 to 1280  |
| ---------------- | ----------------------------------------- | -------------------- | ------------ | -------------- |
| **y 0 to 240**   | Lamp gallery                              | Furnace hall (start) | Draught hall | Chimney top    |
| **y 240 to 480** | Mite warren                               | Central shaft        | Hollow       | Windpipe       |
| **y 480 to 720** | Cistern (flooded; the current flows east) | Cistern              | Cistern      | Rubble gallery |
| **y 720 to 960** | Fungus grotto                             | Gnasher's gullet     | Bell chamber | Brass vault    |

---

### Part 2: Tam, the hero

1. Select the hero, rename it **Tam**, set `416, 176, 12 × 16`.
2. Keep **Gravity** and set `Force = 720`, `Max fall speed = 420`.
3. Keep **Run**: `Top speed = 84`, `Acceleration × = 1`.
4. Remove **Jump, Double jump, Dash, Stomp attack, Dash attack**. Tam does not jump; the pack does the lifting.
5. Add **Jetpack** (Actions):

   | Setting          | Value | Why                                              |
   | ---------------- | ----- | ------------------------------------------------ |
   | Thrust           | 1180  | Stronger than gravity (720), so holding A climbs |
   | Fuel tank        | 3     | Three seconds of thrust from full                |
   | Refill on ground | 0.8   | Slow refill while standing, so vents matter      |
   | Air push         | 420   | Sideways control in the air                      |
   | Top speed        | 190   | Momentum cap                                     |
   | Air drag         | 0.6   | How fast momentum fades                          |
   | Crash speed      | 400   | Hitting a wall faster than this hurts            |

6. Add **Carry + throw**: `Throw X speed = 170`, `Throw Y arc = 150`. Anything you carry moves with Tam and its weight slows the climb.
7. Add **Key input**: `Key = F key`, `Trigger mode = On press`, `Cooldown = 0.3`. Under **RUN THESE BLOCKS** add **Hero shot**: `Cooldown = 0.3`, `Projectile speed = 260`, `Aim range = 48`, `Projectile count = 1`, `Lifetime = 0.9` (rest 0). Switch the Hero shot **off** with its toggle. That is the cutter; the toolbox will switch it on.
8. Keep **Damage + respawn** (`Max hearts = 5`, `Invulnerable after hit = 1.2`, `Knockback = 140`), **Heart collector**, **Core collector**, **Exit reader**, **Checkpoint reader**.
9. Sprite (**SPRITE**, 16 × 16): `idle`, `move` (2 frames, 0.14 s), `jump` (one frame, used while falling) and `jet` (2 frames of the pack firing). Jetpack plays `jet` automatically while it thrusts.

#### World settings marker

Place a **Checkpoint** at `592, 48, 8 × 8` called **World settings**, remove Checkpoint flag, add **Environment settings** with `Pixel sprites = Flip to face movement` (everything else default), and a rule `WHEN onStart · TARGET self · DO Show / hide (hide)`.

---

### Part 3: The rock

The whole cave is **Brick** objects with **Solid body**. The map below is the template's exact layout: each character is one 16 px tile, `#` is rock and `.` is open cave. Column numbers run across the top (tens, then units); row numbers down the side. A tile at column `c`, row `r` sits at `x = 16 × c`, `y = 16 × r`.

```text
          1111111111222222222233333333334444444444555555555566666666667777777777
01234567890123456789012345678901234567890123456789012345678901234567890123456789
################################################################################  0
################################################################################  1
#########################.#........############.......#....#####################  2
##.###.....#...#######.##............#.######.#.......#....#####.............###  3
##..#..........######......................................#####.............###  4
##..............#####......................................#####.............###  5
##....####......#####............................#####.....#####....############  6
##.....#........#####.............................##.#.....#####....############  7
##.....................................######.#............#####....############  8
##.....................................#########...........#####....############  9
##.....................................#########...........#####....############ 10
##....................................##########...........#####....############ 11
##....#######################...################...........#####....############ 12
##....#######################...##################...###########....############ 13
##....#######################...##################...###########....############ 14
##....#######################...##################...###########....############ 15
##......####..#....##########...##################...###########....############ 16
##.......#.#.......##########...#########.#...##.......#.......#....############ 17
##.................##########.................##.......#.......#....############ 18
##.................##########..................................#....############ 19
##........#........##########..........................................###.##.## 20
##.......######....##########...#########.....#..#......................##.##.## 21
##.........#.......##########...#########.....#####...........................## 22
####...............##########...#########......#..#...........................## 23
######..........................#########......#..............................## 24
##..............................#########.....................................## 25
##..............................#########.....................................## 26
##....#......#..................#########...........##................##......## 27
#############################...################################################ 28
#############################...################################################ 29
#############################...################################################ 30
##........#....#.............................##.#....#.###........##.##.......## 31
##...........................................#.......#.###........##..........## 32
##..................####...............................###....................## 33
##..................####............###.......................................## 34
#########...........####............###.......................................## 35
##..................####............###.......................................## 36
##..................####............###.......................................## 37
##..................####............###................###....................## 38
##..................####............###................###....................## 39
##..................####............###................###....................## 40
##..................####............###................###....................## 41
##..................####............###................###...#.##.#.......#...## 42
##..................####............###..............#.######################### 43
##...####################################...#################################### 44
##...####################################...#################################### 45
##...####################################.....................................## 46
##....###..#.#.#..#######################.....................................## 47
##.....#..........#######################.....................................## 48
##................#######################.....................................## 49
##................#######################.....................................## 50
##........#.......#######################.....................................## 51
##......#####.....#######################..................#######............## 52
##.......#.#...........##################..................#######............## 53
##.....................##################..................#..####............## 54
##.........................................................#..####............## 55
##............................................................####............## 56
###...#...#.#..#..############################################################## 57
################################################################################ 58
################################################################################ 59
```

The fastest way to build it:

1. Click **Brush** in the bottom toolbar, pick **Brick** in the Toolbox, set **SNAP = 16**.
2. Drag a rectangle over each block of `#`. Make the rectangles as big as you can: the outer frame, the thick bands at rows 0 to 1, 12 to 15, 28 to 30, 44 to 45 and 57 to 59, then the pillars, ledges and lumps. The template uses 138 rectangles; you can use fewer by ignoring single-tile bumps.
3. An object can be at most one screen (320 × 240, 20 × 15 tiles), so split long bands into screen-sized pieces.
4. Give the rock a sprite: select one rock piece, **SPRITE**, draw a 16 × 16 rock texture, set **ON BIG OBJECTS = Repeat as tiles**, then save it as an entity and use that entity for every piece (or copy and paste the first piece and resize it).

Leave these gaps open, the puzzles depend on them:

- **The central shaft** (columns 29 to 31, rows 12 to 30): the main way down from the Furnace hall to the cistern.
- **The chimney** (columns 64 to 67, rows 3 to 27): the updraft column.
- **The siphon** (columns 2 to 4, rows 44 to 46): the underwater passage from the cistern down to the fungus grotto.
- **The gullet** (columns 41 to 43, rows 44 to 45): the way from the bell chamber up into the cistern, where the geyser goes.
- **The mousehole** at column 59, row 56: you add a thin lip over it in Part 9.

---

### Part 4: The Furnace hall (start)

- **Furnace lift** (the goal): **Exit** at `352, 160, 32 × 32`. Keep **Locked exit**: it opens once every Collectible core (the four Ember hearts) is collected. Draw a brass lift cage.
- **Hall lamp:** **Checkpoint** `400, 168, 12 × 24`, keep **Checkpoint flag**. Draw a lamp. Every lamp in the cave is a checkpoint.
- **Hall vent:** **Spikes** `560, 168, 24 × 24`. Remove Hazard, add **Fuel cell**: `Fuel = 2.5`, `Bigger tank = 0`, `Kind = Vent (refills per second while touching)`. Draw a steam vent with two `idle` frames so it puffs.
- **Keeper's note:** Checkpoint `512, 176, 16 × 16`, remove Checkpoint flag, **Dialogue box** (`Pause while open = Live gameplay`, `Show for = 4`). Text, then **+ LINE** for each extra line:
  - `HOLD SPACE TO FIRE THE PUFFER PACK. IT RUNS ON STEAM: VENTS AND CELLS REFILL IT.`
  - `X PICKS THINGS UP AND THROWS THEM. YOUR SPEED GOES WITH THEM.`
  - `BRING ALL FOUR EMBER HEARTS BACK TO THE FURNACE LIFT.`

> **Check:** play. Tam should walk, hold Space to rise, drift with momentum, and refuel standing in the vent.

---

### Part 5: The creatures

Emberwell's creatures use **Creature instincts**: each belongs to a numbered group and can hunt one group and fear another. The template's groups:

| Group | Who                                 | Hunts        | Fears    |
| ----- | ----------------------------------- | ------------ | -------- |
| 1     | Mites                               | nothing      | owls (2) |
| 2     | Duskowls                            | mites (1)    | nothing  |
| 3     | Glowcaps (bait, via Creature scent) |              |          |
| 4     | Gnasher                             | glowcaps (3) | nothing  |
| 5     | Glimmerbats                         | the hero     | owls (2) |
| 6     | Eels                                | the hero     | nothing  |

Build one of each, save it as an entity (**SAVE ENTITY**), then place copies.

**Glimmerbat** (Gloom bat, 16 × 10): remove Hover, Chase and Stompable. Add **Creature instincts**: `Group = Group 5`, `Hunts = The hero`, `Fears = Group 2`, `Senses within = 104`, `Speed = 48`, `Bite damage = 0`, `Moves by = Flying (any direction)`. Add **Health pool** `1`; keep **Touch damage** `1`. Sprite with `idle` and `move` (wing flap, 0.12 s).

**Duskowl** (Gloom bat, 16 × 14): remove all starter blocks, add **Creature instincts**: `Group = Group 2`, `Hunts = Group 1`, `Fears = Nothing`, `Senses within = 200`, `Speed = 70`, `Bite damage = 1`, `Moves by = Flying`, `Calm after eating = 4`. No Touch damage: owls ignore Tam.

**Mite** (Muck, 12 × 10): keep **Gravity**, remove Patrol, Stompable and Touch damage. Add **Creature instincts**: `Group = Group 1`, `Fears = Group 2`, `Senses within = 88`, `Speed = 34`, `Bite damage = 0`, `Moves by = Walking (left/right)`, `Roams within = 96`. **Health pool** `1`. **Respawn**: `Comes back after = 9`, `Times = 0` (forever), so owls never run out of food.

**Eel** (Gloom bat, 20 × 10): remove starters, add **Creature instincts**: `Group = Group 6`, `Hunts = The hero`, `Senses within = 96`, `Speed = 44`, `Moves by = Swimming (any direction in water)`. **Health pool** `2`, **Touch damage** `1`.

---

### Part 6: West: the Lamp gallery and the Mite warren

- **Gallery bats:** glimmerbats at `144, 64` and `208, 128`.
- **Gallery heart:** **Heart** `112, 84, 12 × 12`, Healing heart `1`.
- **Gallery cell:** **Core** `48, 178, 10 × 14`. Remove Collectible core, add **Fuel cell**: `Fuel = 3`, `Bigger tank = 0`, `Kind = Pickup (disappears)`. Draw a brass cell.
- **Warren owl:** duskowl at `160, 272`.
- **Mites A to D:** at `64, 416`, `128, 416`, `208, 416`, `256, 416`.
- **Warren sign:** Checkpoint `48, 352`, Dialogue box (`Live gameplay`, `4 s`): `MITES. DUSKOWLS EAT THEM AND LEAVE SWEEPS ALONE. GLIMMERBATS FEAR OWLS.`

**The old toolbox (the cutter):**

1. **Brick** at `192, 320, 16 × 16`, name **Old toolbox**. Keep Solid body, add **Treasure chest** `Contents = Nothing (rules only)`, `Points = 0`.
2. Sprite with `idle` (closed) and `open` frames.
3. Rule: `WHEN onState · TARGET named → Tam · IF State equals open · DO Turn block on / off (Hero shot, on)`.
4. **Toolbox sign:** Checkpoint `240, 320`, Dialogue box (`Live gameplay`, `4 s`): `A SWEEP'S OLD TOOLBOX. THE CUTTER INSIDE FIRES ON F AND CUTS RUBBLE.`

> **Check:** watch the owl swoop on the mites and the mites scatter. Open the toolbox and press F: Tam fires short cutter shots.

---

### Part 7: East: the Draught hall, the Hollow and the Chimney (heart 1)

- **Draught:** **Spikes** `624, 64, 96 × 64`. Remove Hazard, add **Wind zone**: `Push X = -35`, `Push Y = 0`, `Lift = 0`. A steady breeze west. Sprite: a few faint streaks with 4 `idle` frames, **ON BIG OBJECTS = Repeat as tiles**.
- **Big tank:** Core `816, 82, 12 × 14`, Fuel cell: `Fuel = 6`, `Bigger tank = 2`, `Kind = Pickup`. It raises the tank from 3 to 5 seconds for good.
- **Hollow bats:** glimmerbats at `704, 304` and `912, 384`.
- **Hollow heart:** Heart `768, 340`.
- **Windpipe vent:** a vent (like the hall vent) at `1152, 424, 24 × 24`.
- **Chimney draughts** (two pieces, since one object can be at most one screen tall): Spikes at `1024, 256, 64 × 192` (**Chimney draught low**) and `1024, 48, 64 × 208` (**Chimney draught high**). Remove Hazard, add **Wind zone**: `Push X = 0`, `Push Y = 0`, `Lift = 1000`. Lift above the hero's gravity makes an updraft that carries Tam up without fuel.
- **Puffball** (a toy): Core `1056, 438, 10 × 10`, remove Collectible core, add **Physics object**: `Weight = 1`, `Bounce = 0.5`, `Buoyancy = 1.5`, `Hit damage = 0`. It floats up the chimney on its own, showing players the draught.
- **Ember heart: chimney:** Core `1184, 84, 12 × 12`, keep **Collectible core** (`Points = 250`). Draw a glowing heart with 2 `idle` frames.

---

### Part 8: The Cistern (heart 2)

#### Water

Water zones are **Spikes** with Hazard removed and **Water zone** added. The cistern spans x 32 to 880, y 560 to 704, split into screen-wide pieces:

| Name      | x   | y   | w × h     | Current X |
| --------- | --- | --- | --------- | --------- |
| Cistern 1 | 32  | 560 | 320 × 144 | 40        |
| Cistern 2 | 352 | 560 | 320 × 144 | 40        |
| Cistern 3 | 672 | 560 | 208 × 144 | 40        |
| Siphon 1  | 32  | 704 | 48 × 48   | 0         |

All four: `Gravity × = 0.35`, `Water drag = 0.55`, `Swim stroke = 150`, `Current Y = 0`. The current pushes everything in the water east at 40 px/s. Give them a water sprite with 2 frames (0.5 s), **Repeat as tiles**.

#### The sluice puzzle

The heart sits in an alcove at the far west behind a sluice gate. A weight plate on the cistern floor opens it, but only something heavy can hold it down, and the only heavy thing is the anvil stone on a ledge above the water.

- **Anvil stone:** **Brick** `336, 514, 14 × 14`. Remove Solid body, add **Physics object**:

  | Setting                | Value               | Why                                                    |
  | ---------------------- | ------------------- | ------------------------------------------------------ |
  | Weight                 | 9                   | Counts as 3 on a weight plate (weight ÷ 3, rounded up) |
  | Bounce                 | 0.1                 |                                                        |
  | Ground friction        | 0.9                 |                                                        |
  | Buoyancy (1 = neutral) | 0.15                | Sinks fast                                             |
  | Hit damage             | 2                   |                                                        |
  | Carry + throw          | Hero can pick it up |                                                        |

  It is so heavy that Tam cannot fly while carrying it: it only goes down.

- **Sluice plate:** **Platform** `384, 698, 64 × 6` on the cistern floor. Remove One-way top, add **Weight plate**: `Channel = 1`, `Required weight = 3`.
- **Sluice gate:** **Cracked wall** `128, 496, 16 × 64`. Remove Dash breakable, keep Solid body, add **Switch door** `Channel = 1`. Brass bars sprite, Repeat as tiles.
- **Ember heart: cistern:** Core `64, 548, 12 × 12` (Collectible core).
- **Cistern lamp:** Checkpoint `368, 504, 12 × 24`.
- **Island vent:** vent at `576, 520, 24 × 24`.
- **Cork raft:** **Brick** `192, 544, 32 × 10`, keep Solid body, add **Physics object**: `Weight = 3`, `Bounce = 0`, `Ground friction = 0.9`, `Buoyancy = 1.7`, `Hit damage = 0`, `Carry + throw = Too big to carry`. It floats and drifts east with the current; Tam can ride it.
- **Eels:** at `224, 640` and `704, 656`.
- **Cistern sign:** Checkpoint `400, 512`, Dialogue box (`Live gameplay`, `4 s`): `THE SLUICE OPENS WHEN SOMETHING HEAVY SITS ON THE PLATE BELOW.` + `THE ANVIL STONE IS TOO HEAVY TO FLY WITH. IT ONLY GOES DOWN.`

> **Check:** pick up the anvil stone (X), walk off the ledge into the water above the plate and drop it (X again). It sinks onto the plate and the gate opens. Swim west for the heart.

---

### Part 9: The Rubble gallery (heart 3)

- **Gallery lamp:** Checkpoint `960, 664, 12 × 24`.
- **Rubble:** **Cracked wall** `1056, 496, 32 × 192`. Keep Solid body, set **Dash breakable**: `Points = 100`, `Hero shots = Shots break it`. Rubble sprite, Repeat as tiles. Only the cutter (hero shots) breaks it.
- **Ember heart: rubble:** Core `1152, 676, 12 × 12`.

---

### Part 10: The deep caves (heart 4)

#### Fungus grotto: bait

**Glowcap** (bait): **Heart** `10 × 10`. Remove Healing heart. Add:

- **Physics object**: `Weight = 1`, `Bounce = 0.25`, `Ground friction = 0.7`, `Buoyancy = 1.3`, `Hit damage = 0`, `Carry + throw = Hero can pick it up`. It floats, so it survives the swim back up.
- **Creature scent**: `Group = Group 3`, `Bitten = Eaten (bait)`.
- **Respawn**: `Comes back after = 6`, `Times = 0`, so the player can always fetch another.

Place glowcaps at `80, 918`, `160, 822`, `240, 918`. Also:

- **Grotto tank:** Core `48, 914, 12 × 14`, Fuel cell `Fuel = 6`, `Bigger tank = 1.5`, `Pickup`.
- **Grotto sign:** Checkpoint `208, 912`, Dialogue box: `GLOWCAPS. SOMETHING IN THE GULLET CAN SMELL THEM FROM HERE.`

#### Gnasher's gullet: the guardian

**Gnasher:** **Prowler** `528, 888, 26 × 24`. Keep **Gravity**; remove Chase and Stompable. Add:

| Block              | Settings                                                                                                                                   |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Creature instincts | Group 4, Hunts Group 3, Fears Nothing, Senses within 150, Speed 36, Bite damage 0, Moves by Walking, Calm after eating 25, Roams within 48 |
| Touch damage       | 1                                                                                                                                          |
| Knockback          | Pushes hero 240, Lifts hero 120, Pushed back when hit 0                                                                                    |
| Invulnerable       | (no settings)                                                                                                                              |

It cannot be beaten. Throw it a glowcap: it eats, turns calm for 25 seconds and stops hurting. Give its sprite `idle`, `move` and a sleepy `calm` animation; Creature instincts plays `calm` on its own.

#### Bell chamber: the impact switch

- **Bell lamp:** Checkpoint `688, 888, 12 × 24`. **Bell vent:** vent at `800, 888`.
- **Pebbles** at `720, 906`, `768, 906`, `864, 906`, each a **Core** `6 × 6` with Collectible core removed and **Physics object**: `Weight = 1`, `Bounce = 0.45`, `Ground friction = 0.25`, `Buoyancy = 0.6`, `Hit damage = 1`, `Hero can pick it up`.
- **Mousehole lip:** **Brick** `944, 896, 16 × 5`. It leaves an 11 px gap above the floor: too low for Tam, wide open for a rolling pebble.
- **Old bell:** **Brick** `976, 864, 16 × 48`, keep Solid body, add **Impact switch**: `Channel = 2`, `Min speed = 50`, `Each hit = Turns the channel on`. Sprite with `idle` and `rung` (2 frames); it plays `rung` when struck. Tam touching it does nothing.
- **Brass gate:** **Cracked wall** `1040, 736, 16 × 96`, Solid body + **Switch door** `Channel = 2`.
- **Ember heart: vault:** Core `1184, 900, 12 × 12`.
- **Bell sign:** Checkpoint `896, 896`, Dialogue box: `THE OLD BELL OPENS THE BRASS GATE. ONLY A PEBBLE FITS THE HOLE.` + `HOLD DOWN AS YOU THROW TO ROLL IT. THE GEYSER IN THE WEST CORNER TAKES YOU BACK UP.`

#### The way back up

- **Geyser:** **Spikes** `656, 720, 48 × 160`, Hazard removed, **Wind zone** `Lift = 1100`.
- **Geyser lid:** **Platform** `656, 704, 48 × 6`, keep **One-way top** with `Drop through = Always solid on top`. Tam rises through it into the cistern and cannot fall back down.

> **Check:** carry a glowcap through the gullet and throw it near the Gnasher. Pick up a pebble, hold Down and press X beside the mousehole. The bell rings and the brass gate opens.

---

### Part 11: Playtest the whole game

1. From the Furnace hall go west, open the toolbox (cutter on F).
2. East: ride the chimney draught to the first heart.
3. Down the central shaft to the cistern. Anvil stone onto the plate, heart 2.
4. Through the windpipe and rubble gallery: cut the rubble (F), heart 3.
5. Swim down the siphon to the grotto. Glowcap to the Gnasher, pebble through the mousehole, heart 4.
6. Geyser up, back to the Furnace lift.

#### Troubleshooting

| Problem                          | Fix                                                                                                        |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Tam cannot climb                 | Jetpack Thrust must be well above Gravity Force (1180 vs 720)                                              |
| Tam falls through floors         | Rock pieces need Solid body; check for gaps between brushed rectangles                                     |
| The stone floats                 | Buoyancy 0.15 and Weight 9 on the anvil stone                                                              |
| The plate does not open the gate | Plate Required weight 3, same channel (1) as the gate's Switch door                                        |
| The Gnasher ignores glowcaps     | Glowcaps need Creature scent Group 3 and Bitten = Eaten; the Gnasher must hunt Group 3                     |
| The bell never rings             | The pebble must hit faster than Min speed 50; throw harder or roll it with Down + X                        |
| The lift never opens             | Every Core with Collectible core counts; pebbles and the puffball must have their Collectible core removed |

---

### Ideas to take it further

- Add a **Time limit** for a speedrun mode.
- Put a **Swoop** on a new cave flyer that dives at Tam from the ceiling.
- Hide a second **Bigger tank** behind a **Blink** wall.
- Add a **Follower** lantern-moth that trails Tam and carries **Healing aura**.

