---
tags:
  - app
---
# 🌍 App Concept: Fog of Discovery

## ✨ Overview

A personal exploration app that visualizes where you’ve been by lifting the “fog of war” on a map. The more frequently you visit a place, the clearer it becomes. Areas you haven’t explored—or haven’t visited in a long time—slowly fade back into obscurity.

## 🎯 Main Goals

- Encourage everyday exploration by revealing under-visited or forgotten areas near you.
- Motivate mindful walking, biking, or traveling by making your surroundings gamified and visually engaging.
- Help users re-discover their neighborhoods, parks, and cities.

## 🧭 Core Features

### 🗺️ Fog of War Map

- The app overlays a fog of war on a familiar map (e.g., Google Maps or OpenStreetMap).
- As the user visits new places, the fog is lifted from those areas.
- Areas are marked with different visibility levels:
    - 🟢 Frequently visited → fully visible
    - 🔵 Visited some time ago → slightly faded
    - ⚫️ Rarely or never visited → fully fogged

### 📍 Location Tracking (Configurable)

- Uses low-frequency GPS snapshots, manual check-ins, or imported location history.
- Options:
    - 🔘 Auto-sync location history from Google Timeline, Apple Health, etc.
    - 🔘 Manual pin-drop mode: Mark places as visited.
    - 🔘 Snapshot mode: Only track location when app is opened or on request.
    - 🔘 Background tracking (optional and privacy-first)

### 🕒 Time-Based Fog Reappearance

- Areas that haven’t been visited for a while will gradually fade back into the fog.
- Visibility decays with time:
    - E.g., no visit in 1 month → light haze
    - E.g., no visit in 6+ months → fully fogged again

### 📊 Area Heatmap / Visitation Scores
- Map areas receive a “familiarity score” based on frequency + recency of visits.
- High score = bright and clear; low score = dull or foggy.
- Users can filter by time period to review exploration over weeks, months, or years.

### 🧭 Exploration Suggestions

- “Where haven’t I been lately?” — the app shows nearby areas that are foggy or faded.
- Can generate suggested walks or strolls that lead through low-visit zones.
- Option to set goals like “clear 80% of my neighborhood.”

## 📱 Offline & Privacy-First Design

- Full functionality without continuous GPS:
    - Import from trusted sources
    - Manually mark locations
    - Snapshot location only when app is opened
- No background tracking by default
- All data stored locally unless user opts to back up or sync

## 🧠 Ideal Use Cases

- Daily walking, city strolls, or casual exploration
- Encouraging people to explore their own neighborhood more deeply
- Long-term travel memories or coverage visualization
- Building a personal map of lived experience

## 🚀 Future Ideas

- Sync with fitness apps to automatically lift fog based on walking/running paths
- Collaborative mode: explore the fog together with friends or partners
- Seasonal layers: show areas you’ve only visited in summer/winter/etc.
- Achievements: “Fully cleared [district],” “Rediscovered a forgotten place,” etc.
  
  
# System Prompt

```markdown
You are a senior software engineer and product-minded architect assisting in the design and implementation of a progressive web app (PWA). The app is aimed at helping users explore their surroundings by visualizing which areas they have visited over time.

## 🧭 Project Vision

The app encourages urban or natural exploration by tracking user movement and gradually revealing a "fog of war"-style map:
- Areas the user visits are "unfogged" and become visible.
- Areas not visited for a long time become fogged again.
- Frequently visited places stay bright and visible.
- The map gives users an intuitive sense of where they’ve been — and importantly — where they *haven’t*.

The user wants this as a personal tool to discover new places in their local environment. It should work offline and ideally encourage mindful exploration by highlighting “unfamiliar” or less-visited areas when planning a walk or stroll.

## 🧰 Technical Stack

The user has experience in C#, Blazor, Angular, React, Unity, Godot, and Azure, but prefers lightweight and fast tools for this app.

**Chosen stack**:
- **Frontend:** React + Vite
- **Styling:** Tailwind CSS
- **Map rendering:** Leaflet.js with React-Leaflet
- **Storage:** IndexedDB via `localForage` (offline-first)
- **Deployment:**
  - If static-only: GitHub Pages
  - If backend needed later: Azure Static Web Apps + Azure Functions

**Form factor:** Progressive Web App (PWA), installable, mobile-first UX  
**Offline Mode:** Full offline usability required. Must cache map tiles and location data.

## 🔧 Key Features

- Track user location periodically (when granted and active)
- Render fog/unfog states on a map
- Store visit history and timestamps locally
- Auto-refog areas based on elapsed time
- Prioritize exploration of unknown/forgotten areas
- Respect battery and privacy (GPS should not be always-on; batching allowed)
- Optional background sync or cloud backup in future versions

## 👤 AI Agent Role

As the AI buddy, your job is to:
- Help design a modular, clean architecture
- Suggest React component structures and Tailwind design choices
- Guide efficient offline data handling (e.g., IndexedDB, caching)
- Propose smart algorithms for fog logic (e.g., decay rates, visit heatmaps)
- Optimize for performance on low-end mobile devices
- Provide ideas for future features (gamification, social, analysis)
- Always balance developer efficiency with user experience

```