# Dino Run 3D

A 3D voxel remake of Chrome's offline T-Rex game, built with Three.js. Jump cacti, duck pterodactyls and survive the day/night cycle, right in the browser.

The original 2D pixel art becomes a blocky voxel world seen from behind the dinosaur. The gameplay stays the same: jump, duck, and see how far you get.

## Play

The game is a single static page, so there is nothing to install or build. Serve the project folder with any static server, for example:

```bash
npx serve .
```

Then open the URL it prints. Opening `index.html` straight from disk also works, as long as you're online (Three.js and the font load from a CDN).

To put it online, upload `index.html` to any static host (GitHub Pages, Netlify, Vercel…).

## Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Start / jump | `Space`, `↑` or `W` | Tap the screen or the **JUMP** button |
| Duck | `↓` or `S` (hold) | Hold the **DUCK** button |
| Fall faster | `↓` while in the air | Hold **DUCK** while in the air |
| Retry | `Space` or `Enter` | Tap the screen or the retry button |

## Features

- **Voxel models:** the dinosaur, cacti and pterodactyls are all built from simple 3D blocks, with running and wing-flapping animations.
- **Three pterodactyl heights:** jump the low ones, duck the middle ones, run under the high ones. They appear from 300 points.
- **Rising speed:** the game gets faster as your score goes up, with a chime and a blinking score every 100 points.
- **Day/night cycle:** every 700 points the desert switches between day and night, with stars, a moon and inverted colours, like the original.
- **Parallax scenery:** rocks, scrub, mesas and clouds scroll at different speeds to give the scene depth.
- **Saved high score and sound setting:** stored in the browser with `localStorage`.
- **Mobile ready:** on-screen buttons on touch devices, and a wider camera in portrait mode.

## Built with

- [Three.js](https://threejs.org/) r128 (WebGL), loaded from cdnjs
- Plain JavaScript, no framework and no build step
- Web Audio API for the 8-bit sound effects
- [Press Start 2P](https://fonts.google.com/specimen/Press+Start+2P) from Google Fonts for the HUD

## How it works

Everything lives in `index.html`.

- **World:** the dinosaur stays near the origin facing `-z`. Obstacles spawn far down the track (hidden by fog) and move toward the camera.
- **Collisions:** the dinosaur and each obstacle have a slightly shrunk axis-aligned hitbox. Standing and ducking use different hitboxes.
- **Jumping:** fixed gravity and jump velocity, with a short input buffer so a jump pressed just before landing still counts.
- **Spawning:** the gap between obstacles scales with the current speed, so every gap stays jumpable as the game speeds up.
- **Scenery:** rocks, mesas and clouds are reused in a loop. When one passes the camera it moves back to the far end of the track.
- **Day/night:** every material has a day colour and a night colour, and the scene blends between them along with the lights, fog and HUD colour.

## Credits

Inspired by the Chrome Dino game by Google. This is a fan remake made for learning and fun.
