# Bubblegum Blow

A tiny browser platformer: blow a bubblegum bubble to float up through a
reef, collect stars, and reach the gold star at the end of each level.

Open `index.html` in a browser to play — no build step, no dependencies.

## Controls

- **A / D** or **Left / Right arrows** — move
- **Space / W / Up arrow** (hold) — blow up a bubble; the bubble grows in
  stages while held and lifts you upward once fully inflated. Release to
  pop it and fall back under gravity.

## Assets

- `assets/star_blue.png`, `assets/star_gold.png` — sliced from a shared
  star/sparkle sheet; used for the collectible coins and the level-goal
  marker.
- `assets/bg_underwater.jpg`, `assets/bg_underwater_overlay.png` — a
  two-layer reef backdrop (base gradient + translucent depth layer) drawn
  behind each level.
- `assets/world_badge.png` — small decorative icon next to the level
  counter in the UI panel.

An additional overworld/city tileset (houses, trees, mountains) was
supplied alongside these but isn't used here — it doesn't fit the
underwater bubble theme this game ended up with, so it was left out
rather than forced in.
