# Sonjas värld ✨

Sonjas egna Roblox-inspirerade 3D-spel — ren statisk HTML (Three.js från CDN).

## Sajten (`site/`)
Hela sajten är **en enda självständig fil**: `site/index.html` (inga lokala asset-beroenden).
Spelet innehåller: spring runt och samla 8 ⭐, obby/hoppbana med målflagga 🏁, husdjur 🐹🐱,
andra spelare (Max/Liv/Noah/Ella), muskamera, och en 📋 kod-panel med riktiga Roblox-koder.

> Tidigare fanns en meny + separata avatar-sidor; ersatt 2026-06-23 av den rikare enfilsversionen
> (operatörsbeslut). Se `docs/superpowers/specs/`.

## Köra lokalt
Det är bara statiska filer. Öppna `site/index.html` direkt i webbläsaren, eller servera mappen:

```bash
cd site && python -m http.server 3003   # http://localhost:3003
```

## Deploy
Hostas på **Render** som en *Static Site* (gratis, HTTPS, global CDN). Konfig i `render.yaml`
(`staticPublishPath: ./site`, ingen build). **Auto-deploy** vid varje push till `main`.

Repo: `Laxen123/sonja` (publikt). Live: se Render-tjänsten `sonjas-projekt`.

> `output/` är slängbart (gitignorerat): stora preview-PNG:er och de daterade källfilerna.
> Den riktiga sajten är `site/`.
