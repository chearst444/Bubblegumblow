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
- **Space / W / Up arrow** (hold) — the bubble grows a stage roughly
  every quarter second while held, 4 stages total. Vertical speed eases
  toward a target rather than snapping to it, and the early stages barely
  lift at all, so pressing it doesn't yank you off the ground. Once fully
  inflated (stage 4) he doesn't stop climbing — he keeps floating upward
  at a gentle, steady speed for as long as you keep holding. Let go at
  any point and the bubble pops, handing control back to gravity —
  falling isn't fatal by itself, only missing every platform and hitting
  the bottom of the screen costs a heart.

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
- `assets/player/*.png` — 13 frames each from two character sheets,
  covering a 4-frame walk cycle, a 3-frame idle bob, a fall/jump pose,
  and 4 blow-up frames that map directly onto `player.bubbleStage`
  (1–4). Both directions are real art, not a mirrored flip, so
  `drawPlayer()` just picks whichever set matches `player.facing` and
  draws it as-is. The no-suffix files are the character facing/walking
  **right** and the `_r`-suffixed files face **left** (the suffix names
  which upload the frames came from, not which way they face - the
  second sheet was supplied as "him turning left" but turned out to be
  the visual mirror of the first, so the two ended up facing opposite
  to what their filenames suggest; confirmed by which side the backpack
  sits on - the back, always opposite the facing direction - in a
  screenshot of each). The single burst/pop frame (`blow_pop.png`) is
  shared by both directions - it's only shown for one instant, and no
  second version exists in the source sheets.

  The second sheet's two largest blow-up frames were packed close
  enough together in the source that a straight bounding-box crop
  pulled a stray red sliver in from the neighboring frame; both were
  re-cropped against the exact gap column between them to get clean,
  artifact-free frames.

The underwater background sheets that were also supplied aren't used —
this game is set over city rooftops, not underwater.
