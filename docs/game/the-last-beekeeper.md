# The Last Beekeeper — Small Prototype Plan

## Prototype Goal

Validate these 3 core ideas:

1. Moving with the hive feels good  
2. Bee commands feel interesting  
3. Protecting the hive feels fun  

If those work, the concept is worth expanding.

---

# Prototype Scope

Keep the prototype extremely small.

## One small map only

Include:
- 1 meadow area
- 1 flower patch
- 1 danger zone
- 1 enemy type

Do not build procedural generation yet.

---

# Core Player Actions

## Movement
Player can move:
- up
- down
- left
- right

The player moves together with the hive wagon.

---

## Bee Commands

Only two commands:

### Gather
Bees fly to nearby flowers and collect nectar.

### Defend
Bees attack the nearest enemy threatening the hive.

That is enough for the first prototype.

---

# Core Systems

## Hive

The hive is one object with:

- Health
- Nectar storage
- Bee count

Example values:
- Health: 100
- Nectar: 0–50
- Bees: 20

---

## Bee Swarm

Do not simulate individual bees.

Use:
- one swarm cloud
- one state machine

States:
- Idle
- Gather
- Defend

This keeps complexity low.

---

## Flowers

One flower patch on the map.

When using **Gather**:
- bees fly to flowers
- timer runs
- nectar increases
- bees return

Example:
- +5 nectar every 3 seconds

---

## Enemy

Only one enemy for the prototype.

### Wasp

Behavior:
- slowly approaches hive
- damages hive
- can be attacked by bees

Example stats:
- Health: 3 hits
- Damage: 5 per second

---

# Gameplay Loop

Simple loop:

Move → Gather → Defend → Survive

That is enough to test the game.

---

# Win / Lose Conditions

## Win
Collect:
50 nectar

## Lose
Hive health reaches:
0

Session length target:
2–5 minutes

---

# Minimal UI

Display only:

- Hive health
- Nectar amount
- Bee mode

Example:

HP: 72  
NECTAR: 24 / 50  
MODE: DEFEND  

---

# Minimal Art Needed

Use placeholders if needed.

Required:
- player sprite
- hive wagon
- swarm cloud
- flower patch
- wasp
- grass tile

No complex animation required.

---

# Controls

## Keyboard

WASD → Move  
1 → Gather  
2 → Defend  

---

# Basic Scripts

Recommended systems:

## Player
Handles movement

## Hive
Stores:
- health
- nectar
- current mode

## Swarm
Moves based on command state

## Enemy
Moves toward hive

---

# Build Order

## Step 1
Create player movement

Goal:
Movement feels good

---

## Step 2
Add hive following player

Goal:
Hive movement feels natural

---

## Step 3
Add bee swarm

Goal:
Swarm visually responds

---

## Step 4
Add flowers + gather command

Goal:
Resource collection works

---

## Step 5
Add enemy

Goal:
Defense feels functional

---

## Step 6
Add win/lose states

Goal:
Prototype becomes playable

---

# Things NOT to Build Yet

Do not add:

- mutations
- multiple biomes
- seasons
- story
- upgrades
- multiple enemy types
- advanced AI

Keep the scope very small.

---

# Success Criteria

Prototype succeeds if:

- bees feel alive
- gathering feels satisfying
- defending feels tense
- player wants another run

If yes, continue expanding.

---

# Estimated Time

Solo dev estimate:

1–3 weekends

depending on engine familiarity.

---

# Core Fantasy

The strongest emotional hook:

**Protect the last surviving hive.**
