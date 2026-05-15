# hello-globe

An interactive 3D globe built entirely on a **Samsung S25 Ultra**, powered by **Claude Code running in Termux**. No laptop. No desktop. Just a phone, a terminal, and an AI pair programmer.

## The Setup

- **Device:** Samsung Galaxy S25 Ultra (Snapdragon 8 Elite)
- **Environment:** [Termux](https://termux.dev/) — a native Linux terminal for Android
- **Editor:** Claude Code (CLI) paired with touch-optimized Vim
- **Browser:** Chrome for Android, rendering WebGL live during dev
- **Version control:** Git + GitHub, all from the command line

The entire project — from `git init` to `git push` — was done through a terminal session on a 6.9" screen. Claude Code handled code generation, Three.js boilerplate, shader authoring, and debugging, all within the same Termux session.

## Why This Matters

This isn't a toy demo. It's proof that modern AI-assisted development has outgrown the workstation:

- **Claude Code in Termux** is a fully capable development environment — shell access, file I/O, git, package management, and GPU-accelerated WebGL preview all work out of the box
- **Touch + pinch-zoom + inertia** are first-class interactions in the globe itself, because the entire project was tested on the same glass screen that coded it
- **Zero cloud reliance** for the dev loop — everything runs locally on the device

## The Globe

- **Three.js** WebGL rendering with a 2048px Earth texture
- Custom GLSL **atmosphere glow** shader with Fresnel rim lighting
- **1500 procedural stars** in the background
- Full **drag-to-rotate** with momentum/inertia decay
- **Pinch-to-zoom** for mobile, scroll-wheel zoom for desktop
- **Auto-rotation** when idle, blending into user interaction
- Responsive canvas that fills the viewport

## Run It

```bash
git clone git@github.com:shamshuipo/hello-globe.git
cd hello-globe
python3 -m http.server 8080
# Open http://localhost:8080 in a browser
```

Or serve it with any static file server — it's a single `index.html` with zero build step.

## Phone as a Dev Machine

| Capability | Works on S25 Ultra? |
|---|---|
| Git (clone, commit, push) | Yes |
| Claude Code (full CLI agent) | Yes |
| WebGL preview (Chrome) | Yes |
| Multi-window (Termux + browser split) | Yes, via One UI split-screen |
| External keyboard (USB-C / Bluetooth) | Optional, but Claude handles the heavy typing |

Built with [Claude Code](https://claude.ai/code) in [Termux](https://termux.dev/).
