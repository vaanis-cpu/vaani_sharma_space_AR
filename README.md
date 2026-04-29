# 🌌 Vaani Sharma · Space AR

> **Advanced Hand Tracking Augmented Reality Experience — Space Edition**

A cinematic, browser-based AR experience that combines real-time hand tracking with immersive space visuals. No app install required — just open in a browser, allow camera access, and interact with the cosmos using your bare hands.

---

## ✨ Features

### 🪐 Space Entrance Screen
- Animated star field with twinkling, parallax-depth stars
- Orbiting planet avatar with multi-ring CSS animation
- Shooting stars at random intervals
- Nebula cloud drifts in the background
- HUD corner brackets and watermark labels
- Smooth fade transition into the AR experience

### 🤚 Real-Time Hand Tracking (MediaPipe)
- Detects up to **2 hands simultaneously**
- 21 landmark points tracked per hand at up to **60 FPS**
- Mirrored camera feed for natural interaction
- Hand skeleton rendered with glowing neon connectors

### ✦ Visual Effects
| Effect | Trigger |
|---|---|
| Fingertip spark particles | Always active on all 5 tips |
| Lightning arc | Both hands close together |
| Gradient beam | Between matching fingertips of both hands |
| Mandala connector | Both hands detected simultaneously |
| Shockwave ripple | Pinch gesture |
| Space matrix rain | Background — accelerates with hand motion |

### 🎵 Spatial Audio
- **Ambient hum** activates when both hands are visible — pitch and volume modulate based on the distance between index fingers
- **Zap sound** fires on every pinch gesture
- Powered by the Web Audio API — no external libraries

### 🎨 5 Visual Themes
| Theme | Palette |
|---|---|
| **Galaxy** | Shifting purples and violet hues |
| **Rainbow** | Full HSL spectrum cycling over time |
| **Cyberpunk** | Electric red `#ff003c` and cyan `#00f0ff` |
| **Lava** | Deep oranges and amber tones |
| **Ocean** | Cool teals and aqua blues |

### 🖐 Gesture Recognition
| Gesture | Detection Method | Action |
|---|---|---|
| Pinch | Thumb tip (4) + Index tip (8) distance < 5% | Shockwave + zap sound |
| Open Hand | Palm spread > 50% | Label: "Open Hand" |
| Fist | Palm spread ≤ 50% | Label: "Fist" |

---

## 🚀 Getting Started

### Requirements
- A modern browser (**Chrome** or **Edge** recommended)
- A webcam or front-facing camera
- Internet connection (MediaPipe loads from CDN)

### Run It
1. Download `vaani_sharma_space_AR.html`
2. Open it directly in **Chrome** or **Edge**
3. Click **"Enter Space AR"**
4. Allow camera permissions when prompted
5. Hold your hands in front of the camera and explore

> ⚠️ **Firefox** has limited support for some MediaPipe camera APIs. Use Chrome/Edge for the best experience.

---

## 🛠 Tech Stack

| Technology | Purpose |
|---|---|
| **MediaPipe Hands** | Real-time hand landmark detection |
| **Canvas API (2D)** | AR rendering, particle system, effects |
| **Web Audio API** | Procedural sound synthesis |
| **CSS Animations** | Entrance screen, orbits, shimmer effects |
| **Vanilla JavaScript** | All logic — zero frameworks, zero dependencies |

---

## 📁 File Structure

```
vaani_sharma_space_AR.html   ← Single self-contained file
README.md                    ← This file
```

Everything — HTML, CSS, JS, animations, audio engine — lives in **one file**. No build step, no npm, no server needed.

---

## 🎮 Controls & Interaction

| Action | Result |
|---|---|
| Show one hand | Skeleton + fingertip sparks appear |
| Show both hands | Lightning arcs + mandala connector |
| Bring fingertips of both hands close | Electric lightning between tips |
| Pinch (thumb + index) | Shockwave explosion + zap audio |
| Move hands fast | Matrix rain accelerates |
| Click a theme button | Switches color palette instantly |
| Click **✕ Exit** | Returns to the space entrance screen |

---

## 📐 Architecture Overview

```
Entrance Screen
│
├── Canvas starfield (requestAnimationFrame loop)
├── CSS nebula + orbit animations
└── "Enter Space AR" button
        │
        ▼
AR Screen
│
├── <video> — live camera feed (mirrored)
├── bgCanvas — space matrix rain / background effects
├── mainCanvas — hand skeleton, particles, ripples, lightning
│       │
│       ├── MediaPipe Hands → onResults callback
│       │       └── updates currentHands[]
│       │
│       └── renderLoop()
│               ├── drawBackground()
│               ├── updatePhysics()   ← particles + ripples
│               ├── drawConnectors()  ← MediaPipe skeleton
│               ├── fingertip effects
│               ├── two-hand interactions
│               └── detectGestures()
│
├── Web Audio Engine
│       ├── humOscillator  ← continuous tone (two-hand)
│       └── triggerZap()   ← one-shot on pinch
│
└── HUD overlay (hands count, FPS, gesture, spread %)
```

---

## ⚙️ Configuration

You can tweak these constants at the top of the `<script>` block:

```js
// Hand tracking
maxNumHands: 2              // Max simultaneous hands (1 or 2)
minDetectionConfidence: 0.7 // Lower = more sensitive, less stable
minTrackingConfidence: 0.7  // Lower = tracks faster movement

// Effects
FINGER_TIPS = [4,8,12,16,20]  // Which landmarks emit particles
lightning threshold: dist < 150  // px distance to trigger lightning
pinch threshold: dist < 0.05     // normalized distance for pinch
```

---

## 🌠 Credits

**Project:** Vaani Sharma · Space AR  
**Hand Tracking:** [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) by Google  
**Audio:** Web Audio API (native browser)  
**Rendering:** HTML5 Canvas API (native browser)  

---

## 📄 License

This project is created for personal/portfolio use.  
MediaPipe is licensed under the [Apache 2.0 License](https://github.com/google/mediapipe/blob/master/LICENSE).

---

<div align="center">

**Made with 🌌 by Vaani Sharma**

*Point your hands at the camera. The universe responds.*

</div>
