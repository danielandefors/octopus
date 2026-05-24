# 🌌 NEON SNAKE 198X 🌌

**NEON SNAKE 198X** is a premium, fully self-contained retro 80s Synthwave Progressive Snake Game. Designed with rich aesthetics, dynamic gameplay loops, custom procedural sound synthesis, and advanced NPC artificial intelligence, it takes the classic 1970s game concept and warps it into an immersive, progressive arcade adventure.

## 🕹️ [CLICK HERE TO PLAY NOW](https://andefors.com/octopus/)

---

## 🎮 Game Basics & Controls

- **Steering**: Use **Arrow Keys** or **W, A, S, D** to steer the snake.
- **Start / Restart**: Press the **Enter** key to instantly start or restart when game over.
- **Mute / Unmute**: Toggle the cabinet's retro volume via the audio switch on the cabinet.

### 🍎 Food Tier System
As you navigate the grid, three distinct tiers of glowing data packets spawn, accompanied by custom synthesized eat sound effects:
1. **CYBER-PULSE (Common - Cyan)**: Adds **100 points**, grows the snake by **1 segment**.
2. **GOLD-GLITCH (Rare - Yellow)**: Adds **250 points**, grows the snake by **2 segments**, flashes a golden alert.
3. **PLASMA-CORE (Exclusive - Glowing Pink)**: Adds **500 points**, grows the snake by **3 segments**, flashes a plasma warning and triggers rich explosion particles.
4. **OCTO-GLITCH (Special - Spinning Cyan-White Galaxy Portal)**: Worth a massive **1000 points**! Upgraded from standard food by the Cyber-Octopus.

---

## 🎹 Progressive Stage Composition

The cabinet features a dynamic, multi-voice Web Audio API synthesizer sequencer that speeds up and morphs across **10 progressive loops**:

### 🟢 Stage 1: Standard Mode (Loop 0)
* Syncopated driving bass kick, off-beat hi-hat ticks, soft synth chords, and a catch-phrase melody hook. An atmospheric soaring counter-melody kicks in starting at loop 2.

### 🟡 Stage 2: High Intensity (Loop 4)
* Continuous, fast 8th-note clicks. Lowpass bass filter opens wide for a buzzing growl.

### 🟠 Stage 3: Apex Intensity (Loop 6)
* Hi-hats double to a relentless sixteenth-note closed-hat chug roll. Lead hook is octave-doubled. Bass filter opens completely to `2700Hz` with a roaring boost.

### 🔴 Stage 4: "Headbanger Mode" (Loop 8)
* Flashing red alert toast. lead melody is driven through overdriven waveshaping curves, detuned flat supersaw bass, 80s arena snare claps, and clicking thump kicks. Grid lines and glowing segments pulse in sync. Camera translation shakes coordinates in sync with kicks/claps.

### ⚡ Stage 5: "Core Disintegration" (Loop 10)
* Cabinet tempo sweep reaches a fast **`130 BPM`**. High-tension, cybernetic staccato soaring pads, E5 note chug lead power-chords, glitching screen slices, and a tight `0.85s` ambient chord envelope limit prevent notes holding too long. Standard 1 food item expands to **3 simultaneous food glitches** on the grid.

### 🌀 Stage 6: "Underwater Submersion" (Loop 11)
* **2-Second Powerdown Freeze**: Game freezes for 2.0s as keyboard controls lock. A massive descending pitch-dive brown note powerdown SFX sweeps oscillators to silence.
* **Aquatic Lowpass**: Cutoff sweeps to a muffled `360Hz`, drowning the entire audio track.
* **Aquatic Slowdown**: Resumes at a sluggish `64 BPM` and slow `270ms` game ticks. Eating food slowly ramps speed back up, cap-flooring at `120ms`.
* Separates 60FPS canvas draw loop from slow physics ticks, rendering blue water filter and horizontal wave ripples.

### 🦈 Stage 7: "Deep Cyber Sharks" (Loop 13)
* Spawns a glowing yellow-cyan warning banner.
* A glowing red **2x2 Cyber Shark** swims onto the board, remaining for 3-5 seconds with a 2-6s gap.
* Alternates a menacing low-bass alternating-semitone **Jaws-reminiscent alarm** (E2 and F2) speed-rolling faster. Bumping into the 2x2 footprint is lethal!

### 💥 Stage 8: "Cyber Shark Swarm" (Loop 15)
* Glowing red toast warning. Swarms of **up to 3 active sharks** patrol the screen, remaining 5-8 seconds.
* Alternates twice as loud, detuned **analog dual-supersaw sub-growl Jaws alarms** opening filters to `260Hz` with a high resonance sweep.

### 🌌 Stage 9: "Cosmic Horizon" (Loop 17)
* Blue subaquatic filters and horizontal wave ripples **fade away smoothly to 0** over 1.5 seconds.
* Replaced by floating **cyan/purple radial gradient nebulas** and scrolling **parallax space stars**.
* Master lowpass filter sweeps open back to a crisp **`20000Hz`** over 2 seconds.
* Ambient pads play slow-attack (`0.9s`) space drones, hats sound like soft sweeping solar wind, and soaring melodies trigger **ascending perfect-fifth double-space echoes** (`frequency * 1.5`).
* Physics speed returns to a fast, responsive cosmic speed of **115ms per tick** (accelerates faster by `6.5ms` per 100 points, cap-floored at `65ms`).
* **Shark Lasers**: Cyber-sharks shoot glowing yellow lasers at random 2-7s intervals with synthesized arcade pew/zap pitch sweeps. Lasers travel fast (**2 cells per tick** with 2-step collision checks), passing through tail segments safely, but triggering Game Over on head hits. Bullets destroy other sharks on impact! Enforces at least one shark visible at all times.

### 🐙 Stage 10: "Deep Sector Octopus" (Loop 20)
* Flashes glowing cyan-green alerts. A friendly but erratic **Cyber-Octopus NPC** spawns, walking slowly once every 3 ticks.
* **BFS Pathfinding**: Runs a real-time Breadth-First Search (BFS) pathfinder to navigate to the closest unenhanced food, treating snake body segments and 2x2 active sharks as impassable solid walls (waiting in place if blocked).
* **Expressive Animations**: Renders **8 waving tentacles** animated with sinusoidal wave offsets. Features target cyber-eyes that **automatically track and follow** the closest food item!
* **Food Upgrades**: If the octopus eats a food, it triggers a synthesized **C5-E5-G5-B5 major arpeggio chime** and golden particles, upgrading the food to a Type 3 **`OCTO-GLITCH`** worth **1000 points**!
* **Intelligent Bounce**: If the snake runs into the octopus, the snake plays a springy bounce sound, bursts cyan particles, and **instantly redirects left or right** into a safe lane without hitting a wall or its own tail.
* **Laser Immunity**: The octopus is bulletproof and damage-resistant.

---

## 🛠️ Technical Implementation Details

- **Web Audio API Synthesis**: Generates all background loops, chords, leads, sub-basses, noise-based snare/hi-hat drums, and sound effects programmatically. No external `.mp3` or `.wav` dependencies!
- **Separated Loop Engines**: Decouples 60FPS visual requestAnimationFrame (for particles, star scrolls, CRT ripples, and camera shakes) from delta-based grid physics ticks, guaranteeing silky-smooth rendering.
- **Safe Steering Vector Queue**: Inputs are queued up to 2 frames ahead to guarantee rapid key entries aren't lost in-between slow physics intervals.
- **Optimal BFS Pathfinder**: Breadth-First Search parses neighbors UP/DOWN/LEFT/RIGHT in sub-milliseconds on a 30x30 coordinate grid, making AI pathing extremely robust.
