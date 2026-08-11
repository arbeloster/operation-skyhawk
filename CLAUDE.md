# Operation Skyhawk — project guide for Claude

## Who you're working with
The lead developer on this project is a **9-year-old** building their own game (their dad is sometimes nearby for things like installing tools or paying for a domain). Please:
- Explain things **simply and encouragingly** — avoid unexplained jargon.
- When a terminal step is needed, give **copy-paste-ready** commands and say what each one does.
- Celebrate progress, be patient, and keep instructions clear and step-by-step.
- For anything that costs money, needs an account, or is outward-facing (deploying, buying a domain), explain it first and let them (or their dad) decide.

## What the project is
A browser **FPV drone game** built as a **single self-contained `index.html`** file. Three.js is loaded from a cdnjs CDN — there is **no build step and no npm**. Just open `index.html` in a browser to play; no server needed.

Features:
- Modes: **Race**, **Freestyle**, **Combat**
- 9 maps: flat, park, city, stadium, graveyard, snow, desert, village, space
- **Weapon Shop** with 7 guns that have special abilities (laser bounce, machine gun, rocket AoE, freeze, homing, lightning)
- Leveled **drone upgrades** (top speed, boost tank, armor, turbo motors)
- **Coins** (+15 per ring, +20 per kill) saved in `localStorage`
- Pilot **accounts** (name) and a local **friends** list
- Controls: `WASD` move, `Space`/`Shift` throttle up/down, arrow keys aim the (stabilized) camera, `Q` boost, `F` shoot, `V` camera, `R` restart

## How it's deployed (it's already live!)
- Hosted on **GitHub Pages** from repo **`arbeloster/operation-skyhawk`**, branch `main`, path `/`.
- Live at **https://operationskyhawk.com** (custom domain bought on GoDaddy, HTTPS enforced) and also https://arbeloster.github.io/operation-skyhawk/.
- **To publish an upgrade:** edit files, then run
  `git add -A && git commit -m "..." && git push` — the live site auto-updates in ~30 seconds.
- GitHub user is `arbeloster`. The first push from a new computer may need `gh auth login` (GitHub.com → HTTPS → login with a web browser).
- Keep the `CNAME` file (contains `operationskyhawk.com`) and the `.nojekyll` file in the repo — they make the custom domain and Pages work.

## How to make changes
- Everything lives in `index.html`. Prefer small, targeted edits.
- After a change, **verify it works** (open `index.html`, or use a local preview) before pushing — the site is public and real people play it.
- Player progress is stored per-device in `localStorage`. The friends list is local-only (`KNOWN_PILOTS` is a placeholder roster); real online multiplayer would require a separate backend server, which isn't built.
