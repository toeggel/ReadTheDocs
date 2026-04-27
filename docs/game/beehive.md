# Minimalist Beehive Logistics Game

A small minimalist strategy game where the player builds and organizes a growing beehive.

The hive expands as a **hexagonal grid**, and each cell serves a purpose such as:

- nectar storage
- pollen storage
- honey storage
- brood
- wax production
- defense

The player does not control individual bees directly.  
Instead, bees automatically move resources through the hive based on its layout.

---

## Core Gameplay

The player can:

- place new cells
- convert existing cells into different types
- reshape the hive to improve efficiency

Worker bees transport resources between cells:

- nectar → honey
- pollen → brood
- wax → new construction

A poor layout causes:

- slow transport
- congestion
- starvation
- colony collapse

The challenge is designing a hive that stays efficient as it grows.

---

## Organic Hive Growth

The colony partly grows on its own.

New edge cells can appear automatically using a **light WFC-inspired system**, where nearby cells influence what new cells become.

Example:
brood near brood is more likely to create more brood nearby.

This makes the hive feel alive while the player still guides its direction.

---

## Player Experience

The gameplay focuses on:

- spatial planning
- optimization
- adapting to growth
- balancing expansion vs efficiency

The goal is to create a healthy colony that can survive as long as possible.

---

## Replayability

Each game differs through:

- random growth patterns
- changing resource needs
- different hive layouts
- score improvement through better efficiency

Players replay to build better and longer-lasting colonies.

---

## Visual Style

Minimalist presentation:

- soft background
- warm honey colors
- simple icons
- tiny moving bees
- calm ambient sound

The hive gradually becomes a living animated structure.

---

## Core Appeal

The fun comes from watching a simple structure slowly turn into a functioning colony where:

**good design creates smooth flow.**

It combines:

- calm minimalism
- organic growth
- light strategy
- satisfying systems

---
# Minimalist Beehive Logistics Game — First Version (v1.0)

The first version should stay very small and focus on proving the core gameplay.

The goal of v1.0 is to answer one question:

**Is building and optimizing a living beehive fun?**

---

## Scope of v1.0

The first playable version contains only:

- a hexagonal hive grid
- a few cell types
- automatic bee movement
- simple resource flow
- organic hive growth
- one survival-based game loop

No advanced systems are needed yet.

---

## Core Player Actions

The player can only do three things:

### 1. Place a new cell
Expand the hive into an empty neighboring hex.

### 2. Convert a cell
Change one existing cell into another type.

### 3. Remove a cell
Delete a cell to reorganize the hive.

These actions create meaningful decisions without adding complexity.

---

## Cell Types in v1.0

Keep the first version limited to only 4 cell types.

### Nectar Cell
Stores raw nectar collected by workers.

### Honey Cell
Converts nectar into food reserves.

### Brood Cell
Consumes pollen/honey to create new bees.

### Wax Cell
Produces wax used for expansion.

This is enough for the first prototype.

---

## Bee Types in v1.0

Only two bee types are needed.

### Worker Bees
Move resources between cells.

### Guard Bees
Protect outer hive cells.

The queen remains automatic and does not need direct interaction.

---

## Resource System

Use only 4 simple resources.

- Nectar
- Honey
- Wax
- Population

Flow example:

Nectar → Honey → Brood → More Bees → More Collection

This creates a self-sustaining loop.

---

## Organic Growth System

At fixed intervals:

A new edge cell appears automatically.

Its type is influenced by neighboring cells.

Example:
- brood near brood increases brood chance
- honey near honey increases honey chance

The player then decides:

- keep it
- convert it
- remove it

This creates the "living hive" feeling.

---

## Core Challenge

The player must balance:

- enough food
- enough space
- enough wax
- efficient layout

Poor layouts create:

- long travel routes
- slow deliveries
- starvation
- overcrowding

The challenge comes from optimization.

---

## Win Condition

Simple for v1.0:

**Survive until the hive reaches 30 cells**

or

**Survive 10 in-game days**

---

## Lose Condition

The colony fails if:

- honey reaches zero
- brood cannot be fed
- population collapses

Simple and clear.

---

## Replayability in v1.0

Even the first version can feel replayable through:

- random starting cell layout
- random growth from WFC-lite system
- score based on survival time
- score based on efficiency

Each hive develops differently.

---

## Minimal Visual Style

To keep production realistic:

- simple hex tiles
- small animated bee dots
- soft honey colors
- clean UI
- no complex art

This keeps the project achievable for a solo developer.

---

## What v1.0 Should Feel Like

The first version should feel like:

- calm
- readable
- strategic
- organic

The player should feel:

**"I am shaping a living system."**

---

## Main Goal of v1.0

The first version does not need many features.

It only needs to prove that:

**building a self-organizing hive is satisfying.**
