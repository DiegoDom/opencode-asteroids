# AGENTS.md

Asteroids clone: single-file HTML5 Canvas game. No frameworks, no bundler, no dependencies (verified: no `package.json`, no build config).

## Run / verify

- There is **no test, lint, build, or typecheck tooling**. Verification is manual: open `index.html` in a browser, or `npx serve .` then visit `http://localhost:3000`.
- After any change, sanity-check that the page loads and the game loop runs without console errors.

## Architecture (game.js)

- All game logic lives in one globals-based script, `game.js` (no modules, no classes split across files). `ctx`, `W` (800), `H` (600) are shared module-level globals. Keep this pattern — wrap-driven updates and `update(dt)`/`draw()` split apply to every entity.
- `W`/`H` in `game.js` must stay in sync with the `<canvas width height>` in `index.html`.
- Entity classes (`Ship`, `Asteroid`, `Bullet`, `Particle`) construct themselves and call `update(dt)`/`draw()`; shared state lives in top-level vars (`ship`, `bullets`, `asteroids`, `particles`).
- Game states: `'playing' | 'dead' | 'gameover'`, plus `level`, `lives`, `score`. `requestAnimationFrame` loop caps `dt` at `0.05`; `space` is toroidal via `wrap()`.
- Input uses `e.code` values (`'Space'`, `'ArrowLeft'`, etc.), tracked in `keys` with `justPressed`/`pressed()` for edge-triggered actions (shooting, restart).

## Conventions

- On-screen UI strings and README are in **Spanish** (`NIVEL`, `GAME OVER`, `PUNTAJE`, comments). Keep new UI text in Spanish.
- Asteroid sizes are constants indexed 1–3 (`RADII`, `SPEEDS`, `POINTS`); a comment notes "por tamaño 1, 2, 3". `size` 3 is largest, `split()` halves it.