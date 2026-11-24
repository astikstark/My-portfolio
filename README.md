# 🛡️ ASTIK.OS — J.A.R.V.I.S. Interface v4.2

> *A cinematic, Iron Man–inspired personal portfolio & HUD built as a single-file HTML application.*

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-00f0ff)

---

## ✨ Overview

**J.A.R.V.I.S. Interface** is Astik Mishra's developer portfolio, designed as a full-screen tactical heads-up display inspired by Tony Stark's J.A.R.V.I.S. system. It's a **zero-dependency, single HTML file** — no build tools, no frameworks, no npm installs. Just open it in a browser.

```
NEURAL_CORE: ONLINE
RTX_TELEMETRY: NOMINAL
ASTIK.OS: READY
```

---

## 🎬 Features

### 🔄 Boot Sequence
An animated startup sequence with expanding concentric rings and a typed system log that initializes subsystems one by one — skippable via `[ SKIP BOOT ]`.

### 🎯 Custom Reticle Cursor
On desktop (pointer devices), the default cursor is replaced with a crosshair reticle SVG that tracks the mouse, with a press-to-shrink interaction.

### ⚛️ Arc Reactor Hero
A fully animated, 3D-tiltable arc reactor SVG with three independently rotating rings (outer, mid, inner), tick marks, and a pulsing core glow — responds to mouse movement with perspective transforms.

### 📊 HUD Corner Telemetry
Four fixed-position readouts displaying:
| Corner | Data |
|---|---|
| **Top-Left** | Live clock (ms precision), session status |
| **Top-Right** | Simulated latency, memory usage, node location |
| **Bottom-Left** | Mouse X/Y coordinates |
| **Bottom-Right** | Scroll depth %, audio toggle |

### 🗂️ Project Schematics
Interactive project cards for four featured builds, each with:
- Status badge (`DEPLOYED` / `ACTIVE_DEV` / `OPEN_SOURCE`)
- Corner bracket hover animation
- Click-to-expand modal with architecture overview, engineering highlights, tech stack, and GitHub link

#### Featured Projects
| Project | Status | Stack |
|---|---|---|
| **J.A.R.V.I.S. Local Voice Assistant** | Deployed | Python, Ollama, faster-whisper, Piper TTS, CUDA |
| **CamCraft** | Active Dev | Kotlin, Jetpack Compose, CameraX, MediaStore |
| **Retail Inventory & Sales Analytics** | Open Source | Python, SQL, Analytics |
| **Smart Campus Reservation System** | Deployed | Python, SQLite3, Full-Stack |

### 📡 Skills Radar & Capability Matrix
- **Category tabs** for filtering: Core Languages, AI & Local Inference, Mobile & UI, Systems & DevOps
- **SVG radar chart** drawn dynamically with polygon data shapes
- **Animated meter bars** with per-skill proficiency percentages that dim/highlight on category selection

### 💬 Transmission Uplink (Contact)
- One-click copy buttons for GitHub, LinkedIn, and email
- A styled contact form ("Dispatch Transmission") with an animated fill-bar submit effect
- Resume archive placeholder with status feedback

### 💻 Interactive Terminal
A dockable slide-up terminal emulator (`astik@jarvis:~$`) with command history (↑/↓) and built-in directives:

```
$ help
AVAILABLE DIRECTIVES:
  help      - list directives
  whoami    - identity readout
  projects  - list active deployments
  skills    - subsystem diagnostic summary
  github    - open uplink coordinates
  status    - full system status
  overdrive - toggle alert theme
  clear     - flush terminal buffer
```

### 🔥 Overdrive Mode
Toggle the entire interface from cyan to amber/red alert palette — ring rotation speed increases, all accent colors shift, and the terminal logs the mode change.

### 🔊 Audio Engine
Optional Web Audio API–powered sound effects:
- **Hover** → high sine blip
- **Click** → square wave tap
- **Confirm** → dual-tone chime
- **Alert** → sawtooth growl (overdrive engage)

### 🎨 Visual Effects Layer
- **Canvas particle field** — floating particles with parallax mouse tracking
- **CSS grid overlay** — faint perspective grid with radial mask
- **Scanlines** — CRT-style repeating lines
- **Vignette** — edge darkening for depth
- **Noise pulse** — flash layer for feedback events

---

## 🚀 Getting Started

```bash
# It's a single file. Just open it.
open Astik____J.A.R.V.I.S._Interface.html

# Or serve it locally
python -m http.server 8000
# Then visit http://localhost:8000
```

> [!NOTE]
> No build step, bundler, or package manager required. The entire application — HTML, CSS, and JavaScript — lives in one self-contained file.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────┐
│                 Single HTML File                 │
├──────────┬──────────────────┬────────────────────┤
│  <style> │     <body>       │     <script>       │
│          │                  │                    │
│ CSS vars │ Boot overlay     │ Boot sequence      │
│ HUD      │ HUD corners (4) │ Canvas particles   │
│ Panels   │ Hero + Reactor   │ Custom cursor      │
│ Terminal │ Project grid     │ HUD telemetry      │
│ Modal    │ Skills layout    │ Arc reactor tilt   │
│ Radar    │ Contact form     │ Project cards/modal│
│ Animate  │ Terminal dock    │ Radar chart (SVG)  │
│ Respond  │ Modal backdrop   │ Terminal emulator  │
│          │                  │ Audio engine       │
│          │                  │ Overdrive toggle   │
└──────────┴──────────────────┴────────────────────┘
```

**Key design decisions:**
- **Zero dependencies** — Google Fonts loaded via CDN (Orbitron, Rajdhani, JetBrains Mono) are the only external resources
- **CSS custom properties** — the entire color system is theme-switchable via `--accent`, `--panel-edge`, etc.
- **Vanilla JS (ES5-compatible)** — no transpilation needed; runs in any modern browser
- **`prefers-reduced-motion`** — all ring/core animations are disabled for accessibility
- **Safe-area insets** — full support for notched/island devices via `env()` padding

---

## 📱 Responsive Design

| Breakpoint | Adaptations |
|---|---|
| **> 860px** | Full two-column layouts for skills and contact |
| **520–860px** | Single-column skills; simplified HUD readouts |
| **< 520px** | Single-column meters; truncated HUD labels; bottom-left HUD hidden |

---

## 🎨 Customization

### Change the color scheme
Edit the CSS custom properties in `:root`:

```css
:root {
  --cyan: #00f0ff;     /* Primary accent */
  --blue: #0077ff;     /* Secondary accent */
  --amber: #ffb000;    /* Overdrive primary */
  --red: #ff3b30;      /* Overdrive secondary */
  --bg: #02060f;       /* Background */
  --ink: #d7f6ff;      /* Text color */
}
```

### Add a project
Push a new object to the `PROJECTS` array in the `<script>` section:

```js
{
  id: "my-project",
  name: "Project Name",
  status: "DEPLOYED",          // DEPLOYED | ACTIVE_DEV | OPEN_SOURCE
  statusClass: "deployed",     // deployed | active | open
  short: "One-line description.",
  architecture: "Detailed architecture paragraph.",
  highlights: ["Bullet 1", "Bullet 2"],
  tags: ["Tech1", "Tech2"],
  github: "https://github.com/..."
}
```

### Add a skill category or update proficiency
Edit the `SKILLS` object — the radar chart and meter bars regenerate automatically:

```js
var SKILLS = {
  "Category Name": {
    key: "cat",
    items: [["Skill", 85], ["Another", 72]]
  }
};
```

---

## 📄 License

© Astik Mishra. All rights reserved.

---

<p align="center">
  <code>ASTIK.OS v4.2 // ALL SYSTEMS NOMINAL</code>
</p>
