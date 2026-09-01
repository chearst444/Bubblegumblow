# Bubblegum Blow

A tiny browser platformer: blow a bubblegum bubble to float up over the
rooftops of a city skyline, collect stars, and reach the gold star at the
end of each level.

Open `index.html` in a browser to play — no build step, no dependencies.

## Controls

You start standing on the ground, facing into the level. Blow a bubble
with four taps to float up to the platforms above. On touch devices,
on screen left, TAP TO BLOW, and right buttons appear below the game and
work the same as the keys. The canvas also scales to fit the screen. On
desktop:

- **A / D** or **Left / Right arrows**: move
- **Space / W / Up arrow**: tap to pump the bubble.
  - Tap 1: tiny bubble. He starts floating the moment you see it.
  - Tap 2: a little bit bigger. Still floating after you let go.
  - Tap 3: all the way blown up.
  - Tap 4: keep holding this press and navigate him through the platforms.
  - Let go of that hold to drop down onto a platform.
  - Tap 5: the bubble pops. Same hard fall if you float into the underside
    of a platform.
  - Landing on a platform while a bubble is still up deflates it safely
    with no fall damage.

### Health

A health bar (starts full, 10 points) replaces a simple life count.
A pop (a 5th tap, or bonking a platform from below) or a drop from
letting go at full size costs health scaled to how far he fell from the
highest point of that flight to where he landed: a little fall costs 1, a
bigger one 2, and a fall from the highest platform costs 3. That's
measured by distance rather than tied to any specific platform, so it
scales to whatever a level's tallest platform happens to be, and a trivial drop (a few
pixels) costs nothing. Flying into a landing instead of popping first
is always free, however far up he was. Missing every platform and
hitting the bottom of the screen is the one fall with nothing to
measure, so it costs the worst tier outright. Health hits 0 → game over.

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
  the visual mirror of the first). The mapping in `drawPlayer()` is the
  single place that decides which set is shown for which travel
  direction - confirmed correct by which side the backpack sits on (the
  back, always opposite the facing direction) in a screenshot of him
  walking each way. The single burst/pop frame (`blow_pop.png`) is
  shared by both directions - it's only shown for one instant, and no
  second version exists in the source sheets.

  Both sheets' two largest blow-up frames were packed close enough
  together in the source that a straight bounding-box crop pulled a
  stray sliver in from the neighboring frame in each case (a fix
  applied to the second sheet's frames initially missed the same issue
  in the first sheet's `blow_4.png`/`blow_pop.png` - both are now
  re-cropped against the exact gap column between the two frames).

The underwater background sheets that were also supplied aren't used —
this game is set over city rooftops, not underwater.

**Missing asset:** a health-meter image was mentioned but never actually
came through as an attachment, so the health bar in the UI panel right
now is a plain CSS gradient bar rather than themed art. Send it over and
it'll get sliced in to replace that placeholder.
