# Bubblegum Blow

A tiny browser platformer: blow a bubblegum bubble to float up over the
rooftops of a city skyline, collect stars, and reach the gold star at the
end of each level.

Open `index.html` in a browser to play — no build step, no dependencies.

## Controls

You start standing on the ground; blow a bubble to float up to the
platforms above rather than starting mid-air. On touch devices, on-screen
◀ / ▶ / HOLD TO BLOW buttons appear below the game and work identically
to the keys below (the canvas also scales to fit the screen). On desktop:

- **A / D** or **Left / Right arrows** — move
- **Space / W / Up arrow** (hold) — blow up a bubble in 4 stages. Lift
  eases toward a target speed rather than snapping to it, and the early
  stages barely lift at all, so pressing the button doesn't yank you off
  the ground — it's a slow float that only really picks up once the
  bubble is nearly/fully inflated (balloon-style progressive lift —
  bigger bubble, faster float, gradually). Keep holding past the max
  stage and it over-inflates and pops on its own. Release early to pop
  it voluntarily. Either way, gravity takes back over and you glide down
  to the ground or the nearest platform below — falling isn't fatal by
  itself, only missing every platform and hitting the bottom of the screen costs a
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
  above the ground line. The orange tree is kept away from the player's
  starting corner (a green one sits there instead) since its color read
  as another bubble when blown up nearby.
- `assets/world_badge.png` — small decorative icon next to the level
  counter in the UI panel.
- `assets/platform_tile.png` — a small procedurally-generated candy-stripe
  tile (24×20px, in the same purple/teal/gold palette sampled from the
  "world 1 CAKES" sheet). An early version sliced straight from that sheet
  actually captured several adjacent platform segments joined together,
  so tiling it produced visible periodic gaps; every stripe/scallop period
  in this version divides the tile size evenly, so `ctx.createPattern(...,
  'repeat')` tiles it with zero seams at any platform width.
- `assets/player/*.png` — 13 frames sliced from the bubblegum-blowing boy
  character sheet: a 4-frame walk cycle, a 3-frame idle bob, a fall/jump
  pose, and 4 blow-up frames + a pop frame that map directly onto
  `player.bubbleStage` (1–4) so the character visibly blows and pops the
  bubble instead of just growing a plain circle. The sheet faces left by
  default; walking right is drawn mirrored.

The underwater background sheets that were also supplied aren't used —
this game is set over city rooftops, not underwater.
