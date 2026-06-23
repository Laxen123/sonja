# CLAUDE.md — sonjas projekt

Sonjas egna Roblox-inspirerade spel/avatarer. **Ren statisk HTML** (Three.js via CDN) — ingen
backend, ingen build. Egen subprojekt-historik (gitignorerad i umbrella `98 Hobby/`).

## Struktur
- `site/index.html` — **den deployade sajten**, en enda självständig fil (3D-spel: stjärnor, obby,
  husdjur, NPC:er, muskamera, 📋 kod-panel). Källan kom från `sonja-roblox-spel/` (parallell session).
- `sonja-roblox-spel/` — annan sessions arbetsmapp för spelet; rör inte utan koordinering.
- `output/` — **slängbart** (gitignorerat): stora preview-PNG:er + daterade källfiler. Kopiera aldrig
  irreplaceable data hit; det canonical är `site/`.
- `render.yaml` — Render Blueprint (static site, publish `./site`).

## Deploy (Render)
- Static Site kopplad till GitHub-repot `Laxen123/sonja` (publikt, default-branch `main`).
- **Auto-deploy på push till `main`** (till skillnad från vetapp som är manual deploy).
- Verifiera efter push, men polla inte deploy-API:t i loop (åter-billas som cache-read varje varv).

## Köra lokalt
`cd site && python -m http.server 3003` → http://localhost:3003. (Port 3003 — siblings använder
3000/3001/3002, se umbrella CLAUDE.md.)

## Innehållsregler
- Sidorna är barnvänliga (svenska, Comic Sans, ljusblå/gul). Behåll den glada tonen vid ändringar.
- Varje sida ska förbli självständig (CDN/inline-assets), så den funkar direkt på en statisk host.
