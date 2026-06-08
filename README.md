# ✈️ Flappy Airplane

A browser-based Flappy Bird-style game where you pilot an airplane through city buildings. Built with vanilla HTML, CSS, and Canvas — no dependencies, no frameworks, just one file.

**🔴 Live Demo → [https://911-the-twin-towers.pages.dev/](https://911-the-twin-towers.pages.dev/)**

---

## Gameplay

Guide your airplane through the gaps between buildings without crashing. Each building pair you clear scores you a point. Hit a building or the ground and it's over — complete with an explosion, fire, structural cracks, and smoke damage on the building.

**Controls:**
- `Space` — flap / start / restart
- `Click / Tap` — flap / start / restart

---

## Features

### ⚙️ Settings Panel
Click the gear icon (top-right) at any time — before, during, or after a game — to adjust:

#### Game Speed
A 5-level slider that sets the base scroll speed of the entire game:

| Level | Name | Multiplier |
|-------|------|------------|
| 1 | Slow | ×0.55 |
| 2 | Easy | ×0.75 |
| 3 | Normal | ×1.0 (default) |
| 4 | Fast | ×1.4 |
| 5 | Insane | ×1.9 |

Building spawn rate adjusts proportionally so gap density stays consistent at all speeds.

#### Progressive Difficulty Toggle
- **Off (default):** speed stays exactly at your chosen level for the entire run
- **On:** every 5 points scored, speed increases by 5% on top of your base speed, capping at +200% (3× base)

---

### 📊 Live Speed HUD
A badge in the bottom-right corner shows your current speed multiplier during play.

When **Progressive Difficulty is on**, the badge reacts to how fast things are actually moving:

| Boost above base | Color | What it means |
|---|---|---|
| 0% (no boost yet) | White | At base speed |
| +5% → +50% | 🟢 Green | Warming up |
| +50% → +100% | 🟠 Orange | Getting spicy |
| +100% → cap | 🔴 Red | Danger zone |

A pulsing `↑` arrow appears the moment progressive speed kicks in and stays visible until the run ends. When progressive mode is off, the badge stays plain white with no arrow.

---

### 💥 Crash Effects
- Particle explosion burst on impact
- Structural damage on the building — scorch mark, irregular hole, radiating cracks
- Broken and glowing windows near the impact point
- Animated fire and flame tongues (direction follows which building face was hit)
- Lingering smoke particles after the crash

---

## File Structure

```
flappy-airplane.html    # Entire game — single self-contained file
README.md
```

No build step. No dependencies. Open `flappy-airplane.html` in any modern browser and play.

---

## Technical Notes

- Rendering: HTML5 Canvas 2D API
- All particles (explosion, smoke, debris) are class-based with per-frame lifecycle management
- Building damage is clipped to the exact building rectangle so nothing renders outside the structure
- Speed HUD colors are computed via linear interpolation between hex/rgba values each frame
- Progressive speed formula: `base × (1 + min(floor(score / 5) × 0.05, 2.0))`

---

## Browser Support

Any modern browser with Canvas 2D support — Chrome, Firefox, Safari, Edge.
