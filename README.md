# Horse-Run
Replica of Chrome Dinosaur game with my own elements.

# 🐎 Horse Run

A Chrome-dino-style endless runner in the browser. You play a galloping horse and jump over puddles, hay stacks and high-jump bars. It's a single HTML file with no dependencies, no build step and no assets.

**[▶ Play it live](https://claude.ai/artifact/WvbpQS9JVLTec78P8f9Xkf)**

## Features

- **Obstacles:** water puddles, hay stacks (single, double, pyramid) and striped high-jump bars
- **Scoring:** live score plus a high score for the current session
- **Difficulty:** the game speeds up over time
- **Day/night cycle:** the scenery switches every 500 points
- **Variable jump height:** hold the button for a high jump, tap for a short hop
- **Sound effects:** jump, milestone chime and crash, generated with the Web Audio API
- **Controls:** pause, mute, and auto-pause when the tab loses focus
- **Responsive:** scales from phones to desktops and stays sharp on high-DPI screens
- **Dark mode:** follows the system light or dark theme
- **Touch support:** tap to jump, with vibration on crash

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Jump (hold for higher) | `Space` / `↑` / `W` | Tap the game |
| Fast fall | `↓` / `S` | n/a |
| Pause / resume | `P` / `Esc` | Pause button |
| Mute / unmute | `M` | Sound button |
| Start / retry | `Space` / `Enter` | Tap |

## Run locally

No install needed. Open the file in a browser:

```bash
git clone https://github.com/<your-username>/horse-run.git
cd horse-run
open index.html        # macOS; on Linux use xdg-open, on Windows use start
```

Or serve it locally:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deploy

It's a static site, so any static host works. Rename `horse-run.html` to `index.html` first.

**GitHub Pages**
1. Push the repo to GitHub.
2. Go to **Settings → Pages**.
3. Set the source to your `main` branch, root folder, and save.
4. Your game will be live at `https://<your-username>.github.io/horse-run/`.

**Netlify / Vercel / Cloudflare Pages**
Drag and drop the folder, or connect the repo. There is no build command, and the publish directory is the repo root.

## Tweaking the game

Constants are at the top of the `<script>` block in `index.html`:

| Constant | What it does |
|---|---|
| `G` | Gravity (higher means a snappier jump) |
| `JV` | Jump velocity (higher means a taller jump) |
| `GY` | Ground height on the canvas |
| `speed` start / max | Initial and top running speed (in `reset()` and `update()`) |
| `D` / `N` | Day and night colour palettes |

Obstacle shapes and sizes live in `spawn()` and `drawObs()`.

## How it works

- Rendered on a single `<canvas>` with a fixed logical height and a width that adapts to the screen.
- A `requestAnimationFrame` loop uses delta time, so speed stays consistent across refresh rates.
- Collisions use slightly shrunk bounding boxes, so near-misses feel fair.
- The session high score is kept in `sessionStorage`, so it resets when the tab closes.

## Browser support

Any modern browser (Chrome, Edge, Firefox, Safari, iOS and Android).

## License

MIT. Use it, remix it, ship it.
