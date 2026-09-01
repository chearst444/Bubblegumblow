# Bubblegum Blow

A tiny browser platformer: blow a bubblegum bubble to float up over the
rooftops of a city skyline, collect stars, and reach the gold star at the
end of each level.

Open `index.html` in a browser to play — no build step, no dependencies.

## Controls

- **A / D** or **Left / Right arrows** — move
- **Space / W / Up arrow** (hold) — blow up a bubble in 4 stages; each
  stage lifts you faster than the last (balloon-style progressive lift —
  bigger bubble, faster float). Keep holding past the max stage and it
  over-inflates and pops on its own. Release early to pop it voluntarily.
  Either way, gravity takes back over and you glide down to the ground or
  the nearest platform below — falling isn't fatal by itself, only
  missing every platform and hitting the bottom of the screen costs a
  heart.

## Assets

- `assets/star_blue.png`, `assets/star_gold.png` — sliced from a shared
  star/sparkle sheet; used for the collectible coins and the level-goal
  marker.
- `assets/bg_city.png` — a city skyline backdrop composited from pieces
  of the houses/buildings/trees/mountains tileset (distant mountains,
  an apartment row, a hospital tower, a house, and trees) standing on a
  continuous green ground plane, layered behind a sky gradient. Mountains
  and buildings are placed so every peak/base stays fully on-canvas and
  flush with the ground — no clipped peaks, no gap of bare sky showing
  above the ground line.
- `assets/world_badge.png` — small decorative icon next to the level
  counter in the UI panel.
- `assets/platform_tile.png` — a frost-topped candy tile strip sliced
  from the "world 1 CAKES" sheet (the same sheet `world_badge.png` comes
  from); tiled via `ctx.createPattern(..., 'repeat')` to texture every
  floating platform instead of a flat gray rectangle.
- `assets/player/*.png` — 13 frames sliced from the bubblegum-blowing boy
  character sheet: a 4-frame walk cycle, a 3-frame idle bob, a fall/jump
  pose, and 4 blow-up frames + a pop frame that map directly onto
  `player.bubbleStage` (1–4) so the character visibly blows and pops the
  bubble instead of just growing a plain circle. The sheet faces left by
  default; walking right is drawn mirrored.

The underwater background sheets that were also supplied aren't used —
this game is set over city rooftops, not underwater.
