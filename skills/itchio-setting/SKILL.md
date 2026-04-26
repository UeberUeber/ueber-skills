---
name: itchio-setting
description: Scaffold new itch.io-ready HTML5 game projects and folder structures. Use when the user asks to start a new browser game, create an HTML5 game skeleton, set up an itch.io-friendly project layout, choose baseline web game files, or prepare an initial Phaser/Pixi/Canvas/WebGL static game foundation before gameplay implementation.
---

# itchio-setting

## Goal

Create the initial structure for a new HTML5 game so it is easy to develop locally and later package with `itchio-dist`. Keep this as a scaffolding workflow, not a release packaging workflow. If the user already has a playable game and wants an upload ZIP, use `itchio-dist`.

## Defaults

When the user does not specify details, use these defaults and state them briefly:

- Game folder slug: lowercase hyphen-case from the title, e.g. `my-game`.
- Engine: static Phaser 3 via local `vendor/phaser.min.js` if Phaser is appropriate; otherwise plain Canvas if the requested game is tiny.
- Viewport: `800 x 800` for square arcade games, `960 x 540` for landscape games, or match the user's target.
- Output style: source game folder only; do not create `dist/` or upload ZIP during setup.

## Recommended Structure

For a static HTML5 game:

```text
<game-slug>/
  index.html
  css/
    main.css
  js/
    game.js
    scenes/
      PlayScene.js
  resources/
    art/
    sound/
    fonts/
  vendor/
  recordings/
    .gitkeep
```

For bundled apps, use the framework's normal source layout, but still keep itch-facing constraints visible:

- Ensure the eventual build output has root `index.html`.
- Keep asset paths relative.
- Avoid requiring server-side routes.
- Keep a clear `dist/itch/` target for later packaging.

## Scaffold Workflow

1. Choose or derive the game slug.
   - Use the user's requested name if given.
   - Normalize folder names to lowercase hyphen-case.
   - Avoid spaces in shipped file and folder names.

2. Create the game root and baseline folders.
   - Put `index.html` at the game root.
   - Separate source JS, styles, vendor libraries, and game assets.
   - Include `recordings/.gitkeep` only if the project will use local capture tools.

3. Create a playable placeholder, not an empty shell.
   - The first run should show a canvas, title, basic input response, and a visible update loop.
   - For Phaser, define a minimal config in `js/game.js` and a `PlayScene` with preload/create/update.
   - For Canvas, define a minimal animation loop with pointer/keyboard input.

4. Make it itch.io-friendly from day one.
   - Use relative paths only.
   - Include `<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">`.
   - Use `overflow: hidden`, centered canvas, and a predictable background color.
   - Prefer local vendor files over unpinned CDNs when feasible.
   - Leave room for fullscreen and mobile scaling.

5. Add development guardrails.
   - Add `.gitignore` entries for `dist/`, `node_modules/`, `.DS_Store`, recordings, generated archives, and large raw exports.
   - Keep experimental pages clearly named and exclude them later with `itchio-dist`.
   - Do not mix raw asset archives with the playable game folder unless the user explicitly wants that.

6. Add a short launch note only when useful.
   - If the project has no README, add a compact README with local run command and itch target.
   - Avoid long planning docs unless the user asks.

7. Verify the skeleton.
   - Serve locally with `python3 -m http.server <port> --directory <game-folder>`.
   - Check `/`, JS, CSS, and any vendor file return HTTP 200.
   - If possible, open the page and confirm the placeholder responds to input.

## Handoff

Tell the user:

- The created game folder.
- The local run command.
- The default viewport chosen.
- The next skill to use for upload packaging: `itchio-dist`.

## Boundaries

- Do not create an itch upload ZIP here; use `itchio-dist`.
- Do not over-engineer with npm/Vite unless the user wants a bundled workflow or the game needs it.
- Do not add analytics, ads, monetization SDKs, or platform-specific APIs during initial setup unless explicitly requested.
