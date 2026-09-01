# Bubblegum Blow

A tiny browser platformer: blow a bubblegum bubble to float up over the
rooftops of a city skyline, collect stars, and reach the gold star at the
end of each level.

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
- `assets/bg_city.png` — a city skyline backdrop composited from pieces
  of the houses/buildings/trees/mountains tileset (distant mountains,
  an apartment row, a hospital tower, a house, and trees), layered behind
  a sky gradient.
- `assets/world_badge.png` — small decorative icon next to the level
  counter in the UI panel.
- `assets/player/*.png` — 13 frames sliced from the bubblegum-blowing boy
  character sheet: a 4-frame walk cycle, a 3-frame idle bob, a fall/jump
  pose, and 4 blow-up frames + a pop frame that map directly onto
  `player.bubbleStage` (1–4) so the character visibly blows and pops the
  bubble instead of just growing a plain circle. The sheet faces left by
  default; walking right is drawn mirrored.

The underwater background sheets that were also supplied aren't used —
this game is set over city rooftops, not underwater.
