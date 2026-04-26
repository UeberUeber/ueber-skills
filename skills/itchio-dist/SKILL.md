---
name: itchio-dist
description: Build, clean, validate, and zip existing browser/HTML5 games for itch.io upload. Use when the user asks to prepare a distribution folder, release artifact, upload ZIP, or final itch.io HTML5 build for Phaser, Pixi, Three.js, Canvas, WebGL, Vite, static HTML/CSS/JS, or similar web game projects.
---

# itchio-dist

## Goal

Create a clean itch.io upload artifact for an existing playable HTML5 game. Keep this as a release workflow, not a project scaffolding workflow. If the user is starting a new game or wants the initial folder skeleton, use `itchio-setting` instead.

Default output:

- Release folder: `dist/itch/<game-slug>/`
- Upload ZIP: `dist/itch/<game-slug>-itch.zip`
- ZIP root must contain `index.html` directly.

## Workflow

1. Detect the game root and entry point.
   - Find candidate `index.html` files with `rg --files -g 'index.html'`.
   - Prefer the folder the user names; otherwise prefer the smallest playable game folder over repo root.
   - Inspect script, stylesheet, asset, and fetch paths before copying.

2. Choose the source mode.
   - Static game: copy `index.html`, JS, CSS, assets, vendor files, and required metadata.
   - Bundled app: run the existing project build command if one exists (`npm run build`, `pnpm build`, etc.), then package that build output.
   - Do not invent a permanent project-local build script unless the user explicitly asks.

3. Create a clean release folder.
   - Remove and recreate only the release output folder, never the source game folder.
   - Preserve relative paths expected by `index.html`.
   - Exclude development/private files: `.git`, `.DS_Store`, `node_modules`, `recordings`, screenshots/raw captures, `palette-test.html`, test pages, logs, archives, source maps unless intentionally shipping them, and local-only tools.

4. Make the release self-contained when practical.
   - For external engine CDN scripts such as Phaser/Pixi/Three, download the exact pinned version into `vendor/` and rewrite the release `index.html` to local paths.
   - For Google Fonts, either leave an acceptable fallback or vendor fonts only if the license/source is clear.
   - Keep third-party license or credit files when shipping assets.

5. Disable development-only behavior in the release copy.
   - Remove dev recorder overlays, debug panels, localhost-only capture tools, and query-param debug bootstraps from the release HTML.
   - If recorder/debug flags live in JS, patch only the release copy so source development behavior remains intact.

6. Build the ZIP from inside the release folder.
   - Run `zip -qr ../<game-slug>-itch.zip .` from the release folder, or equivalent.
   - Verify `unzip -l` shows `index.html` at ZIP root, not nested under an extra directory.

7. Validate the artifact.
   - Serve the release folder with `python3 -m http.server <port> --directory <release-folder>`.
   - Check `/`, core JS/CSS, vendor scripts, and representative assets return HTTP 200.
   - Search the release folder for unwanted references: `rg -n "dev-recorder|localhost|cdn.jsdelivr|fonts.googleapis|recordings|palette-test|\\.git|\\.DS_Store" <release-folder>`.
   - If possible, open the served page and smoke-test: first input works, audio unlocks after user gesture, game over/restart works, and mobile scaling is acceptable.

## Report Back

Tell the user:

- Exact ZIP path to upload.
- Recommended viewport/embed size from the game config, commonly `800 x 800` for square Phaser games.
- Whether fullscreen should be enabled.
- Whether mobile friendly should be enabled.
- Any remaining external network dependencies or asset-license caveats.

## Boundaries

- Do not scaffold a new game here; use `itchio-setting`.
- Do not commit generated release folders unless the repository already tracks release artifacts.
- If the user wants this workflow repeated across future games, improve this skill rather than adding per-project scripts.
