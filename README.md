# Sonjas värld ✨

Sonjas egna Roblox-inspirerade spel och avatarer — ren statisk HTML (Three.js från CDN).

## Sidor (`site/`)
| Fil             | Vad                                                    |
| --------------- | ------------------------------------------------------ |
| `index.html`    | Startsida / meny som länkar de tre sidorna nedan       |
| `spel.html`     | Plattformsspel — spring runt och samla 8 stjärnor (3D) |
| `avatar-3d.html`| 3D-avatar du styr själv                                |
| `avatar.html`   | 2D-avatar (SVG)                                         |

Alla sidor är självständiga (inga lokala asset-beroenden).

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
