# Spec: Deploya "Sonjas värld" på Render

**Datum:** 2026-06-23
**Status:** Levererad 2026-06-23. **Exekveringsnotis:** sajten gick först live som startsida +
3 separata sidor; samma dag ersatt (operatörsbeslut) av en rikare **enfilsversion** av spelet
(från en parallell sessions `sonja-roblox-spel/`) som nu utgör hela sajten (`site/index.html`).

## Mål
Få Sonjas tre HTML-artefakter (spel + 2D-avatar + 3D-avatar) live på webben via Render, bakom
en enkel barnvänlig startsida. Klart = en publik HTTPS-URL där startsidan länkar alla tre och
de fungerar.

## Bakgrund
Projektet bestod av tre fristående, självständiga HTML-filer i `output/` (date-stämplade):
`roblox-game` (samla 8 stjärnor, Three.js), `roblox-avatar` (2D SVG), `roblox-avatar-3d` (styrbar
3D). Inga lokala asset-beroenden — allt är CDN + inline. `output/` är slängbart per umbrella-regel,
så den canonical sajten måste bli committad källkod.

## Beslut
- **Hosting:** Render **Static Site** (gratis, HTTPS, global CDN, auto-deploy). Valt över Web
  Service (onödig server/kostnad) och GitHub Pages/Netlify (användaren bad om Render).
- **Scope:** Startsida + alla tre sidorna (användarval).
- **Repo:** publikt GitHub-repo `Laxen123/sonja` (default-branch `main`). Subprojektet är eget
  git-repo, gitignorerat i umbrella `98 Hobby/`.
- **Adress:** gratis `*.onrender.com`-subdomän nu; egen domän kan läggas till senare.
- **Auto-deploy:** på, vid push till `main`.

## Struktur
```
sonjas projekt/
  site/
    index.html       NY startsida (meny: 🎮 Spel · 🕹️ 3D-avatar · 🧍 Avatar)
    spel.html        = roblox-game (oförändrat innehåll)
    avatar-3d.html   = roblox-avatar-3d
    avatar.html      = roblox-avatar (2D)
  render.yaml        Blueprint: runtime static, staticPublishPath ./site, ingen build
  README.md
  CLAUDE.md
  .gitignore         (ignorerar output/)
  docs/superpowers/specs/2026-06-23-render-deploy-design.md
```

## Startsidan (enda nya artefakten)
Matchar spelets stil: ljusblå→gul gradient, Comic Sans, svävande stjärnor, tre stora tappbara
kort med emoji + etikett, responsiv (kort staplas på mobil). Touch-vänlig (barn på surfplatta).

## Steg
1. Scaffold + kopiera de tre filerna till `site/` med rena namn, skriv `index.html`. ✅
2. `git init`, lägg `sonjas projekt/` i umbrella `.gitignore`, initial commit.
3. Push till befintligt repo `Laxen123/sonja` (`GH_TOKEN`), branch `main`.
4. Skapa Render Static Site kopplad till repot (Render-API / dashboard, `RENDER_API_KEY`).
5. Verifiera live-URL (startsida + alla tre laddar och funkar), lämna länk.

## Risker / noter
- Render Static Site kräver Git-koppling (ingen drag-and-drop) → GitHub-repo behövs.
- `gh` CLI saknas på maskinen → GitHub-repo skapas via REST-API med `GH_TOKEN` (fine-grained PAT;
  faller tillbaka till browser om repo-create nekas av scope).
- Verifiera deploy men polla inte i loop (umbrella render-deploy-regel).
