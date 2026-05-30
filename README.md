# isitjaimesbirthday.com

A single-serving birthday-gift microsite for Jaime. It boots up like deadpan internet
infrastructure to answer one question — *is it Jaime's birthday?* — and over six acts
loses its composure and becomes a love letter. Built in her studio's brand system (jkk.studio).

**The thesis:** the interface falls in love in real time — motion goes from *mechanical*
to *alive*. Full creative direction, brand tokens, voice, storyboard, and motion law live
in **[CLAUDE.md](CLAUDE.md)** (the single source of truth). Read that first.

## Project layout
```
index.html                  token-wired scaffold (BOOT scene wired; other scenes stubbed)
CLAUDE.md                   source of truth — brand, voice, flow, motion, open questions
assets/
  cursors/                  crab-open.svg, crab-pinch.svg  (the signature cursor)
  img/                      dog-placeholder.svg            (swap for real photo)
  vendor/anime.umd.min.js   anime.js v4 (global `anime`)
  ASSETS.md                 what's in place + what's still needed from you
docs/                       (storyboards / notes)
reference/                  (prior reference build, if restored)
```

## Run locally
Static site — serve the folder and open it:
```
cd isitjaimesbirthday
python3 -m http.server 8000   # then visit http://localhost:8000
```
(Open via a server, not file://, so the fonts/cursors/anime load cleanly.)

## Status
Scaffold stage. BOOT renders with correct tokens, fonts, crab cursor, grain, and anime.js
loaded. Scenes 01–06 are stubbed with build TODOs.

### Still needed from you (see assets/ASSETS.md)
- **Faffin Medium .ttf** — the display face, to base64-embed (prior copy was lost). Until then it falls back to Old Standard TT.

### Done
- Dog cutout baked into the dog-rain (`assets/img/dog.png`); favicon built from Jaime's photo.
- Notification wired to **melissa.donohue@icloud.com** via `CONFIG.yourEmail`.

## Deploy
Static. Rename nothing — `index.html` is the entry. Drag the folder onto Netlify Drop for a
free URL, then point `isitjaimesbirthday.com` at it from your registrar. (Public hosting of
Faffin needs a webfont license, or swap a free display fallback — noted in CLAUDE.md.)
