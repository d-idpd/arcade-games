# 🕹️ Arcade Games

Two-player browser games — desktop, mobile, and RetroPie-ready.  
Each game is a self-contained folder with a single `index.html`. No build step, no server required.

## Folder structure

```
arcade-games/
├── index.html                    ← Hub / landing page
├── README.md
│
├── 2048-twoplayer/
│   ├── index.html                ← Game (fully self-contained)
│   └── 2048-config.json          ← Optional config overrides
│
├── snake-twoplayer/
│   └── index.html                ← Placeholder (coming soon)
│
├── tetris-battle/
│   └── index.html
│
├── breakout-twoplayer/
│   └── index.html
│
└── pong-classic/
    └── index.html
```

## Playing locally

Just open `index.html` in any modern browser — double-click the file or drag it in.  
No internet connection required after download.

## GitHub Pages

1. Push this folder to a GitHub repo
2. Settings → Pages → Source: `main`, folder `/` (root)
3. Access at `https://yourusername.github.io/arcade-games/`

Each game will be live at its subfolder URL, e.g.:
```
https://yourusername.github.io/arcade-games/2048-twoplayer/
```

## RetroPie / Ports

```bash
# Install dependency
sudo apt install python3-pygame chromium-browser

# Copy game folder to Ports
cp -r 2048-twoplayer/ ~/RetroPie/roms/ports/

# Create launcher script
cat > ~/RetroPie/roms/ports/2048-twoplayer.sh << 'EOF'
#!/bin/bash
chromium-browser --kiosk --app=file:///home/pi/RetroPie/roms/ports/2048-twoplayer/index.html
EOF
chmod +x ~/RetroPie/roms/ports/2048-twoplayer.sh

# Restart EmulationStation — game appears under Ports
```

## Config (2048)

Drop a `2048-config.json` next to `index.html` to override defaults:

```json
{
  "playerNames": ["Dean", "Player 2"],
  "sfxOn": true,
  "musicOn": true,
  "darkMode": false,
  "demoSpeed": 2,
  "aiDepth": 3,
  "attractDelay": 60
}
```

If no config file is found, all defaults apply. Settings changed in-game are saved to `localStorage`.

## Controls — 2048

| Control | Player 1 | Player 2 |
|---------|----------|----------|
| Keyboard | Arrow keys | W A S D |
| Gamepad | Gamepad 1 (analog/d-pad) | Gamepad 2 |
| Mobile | Swipe left half of screen | Swipe right half |
| Start/Select | Restart both boards | — |
| R | Restart | — |
