# Lighthouse Logic – Game Concept

## Overview
A minimalist puzzle game where players place and rotate lighthouses to guide ships safely through hazardous waters. The game focuses on spatial reasoning, line-of-sight, and simple systemic interactions.

---

## Core Gameplay
- Ships spawn from map edges and must reach designated harbors
- Players control lighthouses placed at fixed positions
- Lighthouses emit directional light beams that influence ship movement
- Terrain (islands) blocks light, creating natural puzzles

---

## Core Mechanics
- **Rotate Lighthouses:** Snap to fixed angles (e.g. 45°)
- **Beam Types:**
  - White = ships are attracted / guided
  - Red = ships avoid / repel
- **Line of Sight:** Beams are blocked by terrain
- **Ship Movement:** Constant speed, influenced by beams + weak pull toward goal

---

## Player Goal
- Guide all ships safely to their harbor
- Avoid collisions with terrain
- Optional: solve within constraints (limited rotations, minimal moves)

---

## Core Loop
1. Adjust lighthouse directions  
2. Press play  
3. Observe ship paths  
4. Iterate until solved  

---

## Level Design Progression
1. Single ship, single lighthouse  
2. Introduce obstacles (beam blocking)  
3. Multiple ships  
4. Multiple lighthouses  
5. Introduce red (repel) beams  
6. Crossing paths  
7. Precision angles / narrow passages  
8. Limited moves  
9. Multiple harbors  
10. Combined challenges  

---

## Optional Mechanics (expand later)
- Color-coded ships and beams
- Rotating or pulsing beams (timing puzzles)
- Ocean currents (passive influence)
- Fog (visibility limited to light cones)
- Mirror towers (reflect beams)

---

## Technical Approach (Simple)
- 2D map (no grid required)
- Ships use vector-based steering:
  - Combine attraction (white), repulsion (red), and goal direction
- Beam check:
  - Angle check (dot product)
  - Optional distance limit
  - Raycast for terrain blocking
- Collision:
  - Ship vs terrain = fail

---

## Minimal Viable Scope
- Predefined lighthouse positions (no free placement)
- 1–2 beam types
- Static ship speed
- ~20 handcrafted levels
- Simple UI (rotate, play, reset)

---

## Visual Style
- Soft shaded terrain (topographic look)
- Muted color palette
- Clean typography and minimal UI
- Calm, readable presentation

---

## Key Design Principles
- Easy to understand, hard to master
- Deterministic and readable systems
- Small changes create meaningful differences
- Focus on handcrafted puzzles

---

## Notes for Solo Development
- Keep systems simple and predictable
- Build a level editor early
- Avoid feature creep (especially physics and complex simulation)
- Prioritize clarity over realism
