# Frogger 🐸 

*August 8, 2021*

<div class="tag-list">
  <span class="tag">TypeScript</span>
  <span class="tag">Angular</span>
  <span class="tag">HTML5 Canvas</span>
  <span class="tag">WebGame</span>
  <span class="tag">Arcade</span>
</div>

---

## Overview

This is a TypeScript remake of the classic Frogger arcade game, rebuilt and integrated into an Angular project for improved structure and type safety.

Your objective: **reach the key without getting hit by bugs**.  
Each time you succeed, the game restarts with more enemies.  
Collide with a bug, and you're sent back to the start.

---

## Tech Stack

- **HTML** — Canvas structure and layout  
- **CSS** — Visual styling and sprite design  
- **JavaScript** — Original game logic and engine loop  
- **TypeScript** — Refactored logic with type safety and Angular integration  

---

## How It Works

The game is structured into three main layers:

### 🎮 Engine
- Controls the core game loop  
- Handles canvas rendering and frame updates  

### 🧰 Resources
- Preloads and caches image assets  
- Ensures all sprites are loaded before rendering  

### 🧍 Application Layer
- Defines core entities: player, enemies, key  
- Manages state, movement, and collision logic  
- Listens for keyboard input  

---

## Demo  
<a href="./demo/frogger" style="text-decoration: none; color: #007acc; font-weight: bold;">▶️ Play Frogger</a>

## Source  
<a href="https://github.com/JLSeto/jimmyset0/tree/master/src/app/frogger" target="__blank" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 View Source on GitHub</a>