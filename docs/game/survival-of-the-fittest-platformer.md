---
tags:
  - game
---

# Survival of the fittest Platformer

> Plantformer where in one round you have to reach the goal and in the next round you have to prevent your previous run from reaching the goal.

Alternative names:

- Your worst own enemy?
- Paradox Platformer
- Ruin your run
- Self-Sabotage

## 🎮 Core Game Loop

1. **Runner Phase (Platformer Dude):**

   * You start running automatically or semi-automatically.
   * You can jump (or eventually gain abilities).
   * Your entire run is recorded (position, timing, jumps, inputs).
   * Goal: Reach the finish line.

2. **Architect Phase (Saboteur You):**

   * Watch your previous run replay.
   * Place one or more obstacles to kill your past self (from a limited toolbox).
   * Can't edit terrain or goal position, just hinder progress.
   * Must be fair: obstacles must be avoidable by *some means*.

3. **Repeat:**

   * Your previous attempts become *ghosts* (or enemies).
   * New runner must survive past runs + new traps.
   * Over time, you have a mini ecosystem of ghosts and evolving skills.

## 🔄 Progression Design: "Survival of the Fittest"

### 🎲 Evolution Mechanics

* When a **ghost dies**, it may get:

  * A **counter-ability**: jump, armor, crawl, swim, etc.
  * A **limited-use upgrade** (e.g. one-time-use helmet).
* Abilities persist only **for the ghost that earned it**, or are randomly given.

> Each iteration, a new generation of runners must adapt to survive the increasing difficulty created by past failures.

## 🧱 Phase Expansions (Ausbaustufen)

You can scale development complexity gradually. Here’s a roadmap:

### 🌱 Phase 1 (MVP):

* Simple autoscroll runner.
* Jump only.
* One ghost run saved at a time.
* One obstacle: spike.
* Architect gets 1 spike per round.

### 🌿 Phase 2:

* Multiple ghosts active simultaneously.
* Multiple obstacle types.
* Random ability on death.
* Visual ghost indicators (color-code generations or skills).

### 🌳 Phase 3:

* Limited physics (falling spikes, swinging traps).
* Platform creation.
* Player can choose upgrades.
* Architect has resource points to spend.
* More complex AI on ghosts (simulate abilities better).

## 🧠 Game Design Principles

### 1. **Strategic Self-Sabotage**

* Make it about *efficiency vs sabotage*.
* You want to *just barely* stop yourself — overdoing it ruins the fun.

### 2. **Emergent Difficulty**

* The more ghosts you accumulate, the more chaotic it becomes.
* Like a puzzle with self-made traps.

### 3. **Visual and Sound Feedback**

* Every ghost should look visually distinct (different colors, hats, trails).
* Emphasize success/failure dramatically.

## 🧰 Technical Considerations (for a solo dev)

* **Game engine**: Unity, Godot, or PICO-8 (if you want ultra minimalist).
* **Ghost Recording**: Store key input timestamps or position frames.
* **Obstacle Placement UI**: Simple grid or free placement during architect phase.
* **Save System**: Loop rounds and persist ghosts and their upgrades.
* **Visual Style**: Stylized or minimal (e.g., VVVVVV or Celeste Pico-8 aesthetic).

## 🧪 Experimental Ideas

* **Online Ghost Sharing**: Compete against other players’ ghost runs.
* **Challenge Modes**: Only one attempt, high-score for most rounds survived.
* **Environmental Hazards**: Wind, water currents, lava rising.
* **Procedural Levels**: Seeded levels for replayability.

## 🏁 Victory / End Conditions

You can play with:

* **Endless Loop**: Try to get as far as possible before a generation finally cannot survive.
* **Score System**: Points per generation survived.
* **Level Unlocks**: Every X rounds unlock new obstacle/ability.

Let me know if you'd like mockups, level design sketches, or even help prototyping logic for Unity/Godot. This idea could really evolve into a tight little cult classic if done right.

## Notes:

The game starts as the most simple imaginable platformer. Running strait to reach the goal. On the next round your previous run gets simulated and you have to place an obsticle to prevent the previous you to reach the goal. On the next run after you play as the platformer dude again and have to reach the goal again. Loop continues.

- Platformer dude can only jump. Platformer architect can only place spikes.
- Platformer dude can only jump. Platformer architect gets some random object to choose from. 
  - e.g.:
    - spikes
    - hole
    - "Abrisskugel"
    - Falling spikes
    - vertical wall
    - water
    - ...
  - Maybe dude gets also new abilities or can place "platforms"
- "Survival of the fittest": Dude can do nothing exept running. 
  - Whenever dude dies they can choose (or get) an ability (protecting against the specific death):
    - Jump
    - Crawl
    - Armor
    - Helmet
    - Double Jump?
    - Swim?
    - ...
    - Such an ability might only last against one obstacle (e.g. armor lets you run through one spike)
  - Architect gets random obstacles.
