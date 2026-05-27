# 🌌 NEON SNAKE 198X 🌌

**NEON SNAKE 198X** is a premium, fully self-contained retro 80s Synthwave Progressive Snake Game. Designed with rich aesthetics, dynamic gameplay loops, custom procedural sound synthesis, and advanced NPC artificial intelligence, it takes the classic 1970s game concept and warps it into an immersive, progressive arcade adventure.

## 🕹️ [CLICK HERE TO PLAY NOW](https://andefors.com/octopus/)

---

## 🎮 Game Basics & Controls

### 💻 Desktop Controls
- **Steering**: Use **Arrow Keys** or **W, A, S, D** to steer the snake.
- **Start / Restart**: Press the **Enter** key to instantly start or restart when game over.
- **Mute / Unmute**: Toggle the cabinet's retro volume via the audio toggle button.

### 📱 Mobile Touchscreen Controls
- **Touch Detection**: The game automatically detects touch-capable browsers and activates mobile mode, adapting the layout dynamically.
- **Virtual D-Pad**: Tap the glowing neon on-screen buttons below the cabinet screen (vertical keys are styled in pink, horizontal in cyan) for low-latency steering.
- **Swipe Gestures**: Swipe anywhere on the game canvas (Up, Down, Left, or Right) to steer intuitively.
- **Start / Restart / Mute**: Tap overlay buttons (`START GAME`, `PLAY AGAIN`, `MUSIC: ON/OFF`) directly for instant activation (bypassing the standard mobile 300ms tap-delay).


### 🍎 Food Tier System
As you navigate the grid, three distinct tiers of glowing data packets spawn, accompanied by custom synthesized eat sound effects:
1. **CYBER-PULSE (Common - Cyan)**: Adds **100 points**, grows the snake by **1 segment**.
2. **GOLD-GLITCH (Rare - Yellow)**: Adds **250 points**, grows the snake by **2 segments**, flashes a golden alert.
3. **PLASMA-CORE (Exclusive - Glowing Pink)**: Adds **500 points**, grows the snake by **3 segments**, flashes a plasma warning and triggers rich explosion particles.
4. **OCTO-GLITCH (Special - Spinning Cyan-White Galaxy Portal)**: Worth a massive **1000 points**! Upgraded from standard food by the Cyber-Octopus.

---

## 🎹 Progressive Stage Composition

The cabinet features a dynamic, multi-voice Web Audio API synthesizer sequencer that speeds up and morphs across **8 progressive stages**:

### 🟢 Stage 1: Neon Grid (Loop 0)
* Driving syncopated kick/snare drums, closed hi-hat shuffles, warm plucky chord pads, and a retro lead synth hook. An atmospheric soaring counter-melody enters starting at Loop 2.

### 🟡 Stage 2: Speed Glide (Loop 4)
* Hi-hat ticks constant on 8th notes, opening the lowpass bass filter for a resonant growling bass sweep.

### 🟠 Stage 3: Apex Chase (Loop 6)
* Hi-hats double to a relentless sixteenth-note closed-hat roll, while the lead melody is octave-doubled with an extremely bright resonant cutoff filter.

### 🔴 Stage 4: Headbanger Overdrive (Loop 8)
* Massive overdrive waveshaper distortion, warmer chorused saw/triangle bass chugs, arena snare claps, screen shakes, and beat-synced visual grid slices. The standard single food item expands to **3 simultaneous food glitches** on the grid.

### 🔵 Stage 5: Sub-Aquatic Chasm (Loop 10)
* **High-Impact Submersion Transition**: Gameplay freezes for 1.5 seconds as a translucent deep blue wave rises with 45 sinusoidal bubble particles. A dual swoosh and pitch-dive sweep runs as audio filters drop to a muffled `900Hz` (submerged).
* **Caribbean Dub Riddim**: Plays a deep low-passed reggae bassline, offbeat chord skanks with tape delay feedback, rimshot One-Drop drum beats, hi-hat bubble swings, and steel-drum chime fills. Maintains the **3 simultaneous food glitches** from Stage 4, while a few **subtle, highly translucent ambient bubbles** float slowly from the bottom to the top in the background of the play area.

### 🦈 Stage 6: Deep Cyber Sharks (Loop 12)
* **Atmospheric Suspense**: Plays a stripped-down, suspenseful reggae/dub groove (no flute lead) to build deep underwater tension before launch.
* **Cyber Shark Incursion**: Glowing 2x2 red Cyber Sharks start spawning on the board (lethal footprint) accompanied by a speed-rolling, alternating-semitone Jaws bass alarm.

### 🌌 Stage 7: Cosmic Nebula Horizon (Loop 14)
* **Space Warp Hyper-Jump Transition**: A dramatic 1.5-second visual and acoustic Space Warp transition (rising white-noise sweeps, square-wave chimes, expanding cyan/purple concentric warp tunnel, and high-frequency camera vibration) freezes physics as the snake leaps into the cosmos.
* **Distinct Ethereal Space Soundtrack**: Audio tracks transition to a highly distinct, spacey Dorian pad progression (Am9 - D9 - Fmaj7 - G6/9) and a brand new soaring celestial melody hook with gliding arpeggios, perfect-fifth delays, a **fat detuned 3-oscillator analog synth voice** (two detuned saws + one sub-octave fundamental square), and a lush **procedural stereo convolution reverb tail**.
* **Neon Projectiles**: Cyber Sharks shoot fast neon lasers (2 cells per tick) in cardinal directions. Bullets destroy head hits (Game Over) or shoot other sharks (red self-destruct explosion).

### 🐙 Stage 8: Deep Sector Octopus (Loop 16)
* **Cyber-Octopus NPC Spawns**: Renders an animated Cyber-Octopus with 8 waving tentacles and eyes tracking the nearest food, walking at 75% the speed of the snake (taking 3 steps every 4 ticks).
* **BFS AI Pathfinding**: The octopus runs a Breadth-First Search (BFS) pathfinder to navigate to the closest unenhanced food, treating snake body segments and active 2x2 sharks as impassable walls.
* **Food Portals**: When the octopus eats a food, it chimes a major arpeggio, upgrading it to a portal worth **1000 points** with custom gold explosion particles.
* **Intelligent Bounce**: If the snake head bumps into the octopus, the snake plays a springy bounce sound, bursts cyan particles, and **instantly steers** into a safe corridor.

---

## 🛠️ Technical Implementation Details

- **Web Audio API Synthesis**: Generates all background loops, chords, leads, sub-basses, noise-based snare/hi-hat drums, and sound effects programmatically. No external `.mp3` or `.wav` dependencies!
- **Separated Loop Engines**: Decouples 60FPS visual requestAnimationFrame (for particles, star scrolls, CRT ripples, and camera shakes) from delta-based grid physics ticks, guaranteeing silky-smooth rendering.
- **Safe Steering Vector Queue**: Inputs are queued up to 2 frames ahead to guarantee rapid key entries aren't lost in-between slow physics intervals.
- **Optimal BFS Pathfinder**: Breadth-First Search parses neighbors UP/DOWN/LEFT/RIGHT in sub-milliseconds on a 30x30 coordinate grid, making AI pathing extremely robust.
