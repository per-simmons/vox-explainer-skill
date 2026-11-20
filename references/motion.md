# Motion

All frame counts at 30 fps (see `format.md` for 24 fps conversion).

## 4.1 Stepped animation ("on twos", Posterize Time)

- **Definition**: motion sampled below the frame rate so each pose holds for 2 frames (**on twos**, 15 poses/s at 30 fps) or 3 frames (**on threes**, 10 poses/s).
- **Where the era uses it**: all graphics, including the camera on graphic comps, labels, draw-ons, highlighter sweeps and collage drop-ins. In Vox's 2019-2020 collage pieces 48-71% of moving seconds are on twos.
- **Where it never goes**: real footage and archival video (posterizing real motion judders it), and the caption active-word box (it moves on word timings).
- Optional **alive-look jitter** on graphic comps: a stepped wiggle of position ≤2 px, rotation ≤0.3°, a new value every 4 f, with the layer at 101-102% scale so edges never show. Each element uses its own random seed; nothing jitters in lock-step.
- Check: classify every 1 s window that has motion (mean frame diff >0.4/255) as on ones, twos or threes by the pattern of identical consecutive frames. Graphic shots: **≥50% of moving windows on twos or threes, and ≤35% on ones.** Footage shots: ≥90% on ones. Jitter amplitude ≤2 px measured on a fixed feature.

## 4.2 Easing

- Entrances: strong ease-out. Camera starts and landings: Easy Ease. Zoom-throughs: extreme ease-in-out. Creeps on stills: linear.
- Forbidden curves: elastic, bounce, back / overshoot, spring with visible overshoot, linear entrances, uniform ease-in-out on every element.
- Check: step any entrance on the 30 fps frames: displacement per frame decreases monotonically to zero; no frame passes the final position and returns.

## 4.3 Entrances: one element at a time

Allowed entrance types:

| Entrance | Parameters |
|---|---|
| **Track matte / alpha matte reveal** (text rises into a mask) | travel 1.5-3% H, 10-15 f, strong ease-out; text never visible outside the matte |
| **Chip width wipe** (label grows from its left edge) | chip 12 f; text appears at f 9-10 (≈80% open); leader line 8-9 f after; ring or dot 8-9 f after that |
| **Stepped / jagged mask reveal** (eaten-on edge) | 8-12 f, uneven jumps held 2-4 f; text +4 f |
| **Trim Paths draw-on** (stroke writes on head-first) | see `evidence-graphics.md` for durations |
| **Paper drop-in** (collage piece lands) | 4-8 f on twos; enters from 3-6% offset with ≤3° rotation settling to rest; shadow distance shrinks as it lands; no overshoot |
| **Word-by-word build** (titles) | one word per spoken word; the second line sits at 50% opacity for 4-8 f before landing |
| **Write-on** (character reveal beside a portrait) | 25-30 characters/s, no blinking cursor |
| **Opacity fade** | ≤15 f, only for source lines, measurement labels and secondary text |

- **Stagger**: consecutive elements land 4-8 f apart (even numbers, so they stay on twos), each on its spoken word. Never more than one element starting on the same frame, except a chip and its own text.
- Forbidden: scale from 0, scale-pop, bounce, spin, flip, 3D card flip, letter-by-letter scale or rotate, everything appearing together.
- Check: on 30 fps frame steps through 5 random builds: no element's scale goes from <50% to 100%; no two unrelated elements start on the same frame; stagger 4-8 f.

## 4.4 Camera: never static on graphics

- Every graphic shot carries camera motion: a **push / creep** of 3-10% scale or a **drift** of 3-8% W over the shot. Moves into a new framing ease out on arrival.
- **Ken Burns / slow push** on stills, documents and scans: linear, 1-2% per second, never faster than 4% per second (faster reads as a zoom), never a push and a rotation together.
- No camera roll, except a slow globe orbit of 10-30° bearing over 4-8 s.
- Holds: after a build completes, hold 1-3 s (charts up to 5 s) with only the creep moving.
- Check: static seconds (1 s windows with mean absolute frame difference <0.4/255) total ≤15% of runtime and no static run is longer than 2.0 s. Measured scale change between first and last frame of every graphic shot is 3-10% (or the drift 3-8% W). No document push exceeds 4%/s.

## 4.5 Transitions

| Transition | Use | Parameters |
|---|---|---|
| **Hard cut** | default, and always between archival / footage and graphics | |
| **Zoom-through (push-through)** | the camera scales into an element until it becomes the next frame (chart thumbnail to full chart; map to site) | 15-21 f, extreme ease-in-out; speed peak on the cut frame ±1 f; **Fast Box Blur** spike 0 → 10-14 px → 0 over 5-7 f centred on the cut |
| **Map-continuity cut** | consecutive shots share one master map; zoom or layer change reads as a camera move | same projection, palette and label style across the cut |
| **Match cut** | shape or object carries across the cut | shared element's centre moves ≤5% of W/H across the cut |
| **Whip pan (swish pan)** | at most one per 30 s | 4-6 f, directional blur 30-80 px along the direction of travel |
| **Cross-dissolve** | only within the same scene (layers changing on one map or chart) | 6-12 f |
| **Rack focus (focus pull)** | on a zoom arrival only, at most 2 in a 60-90 s video | blur clears to 0 on the hero element before the VO names it |

- Requirements: ≥1 zoom-through and ≥1 map-continuity move.
- Forbidden: glitch, RGB-split transition, page curl, cube, star or iris wipe, film burn, light-leak transition, ink-bleed matte, morph cut, a dissolve between unrelated scenes, a blur or dissolve on every cut.
- Check: list every cut with its type from the 30 fps frames. Count ≥1 zoom-through, ≥1 map-continuity move, ≤1 whip per 30 s, 0 forbidden types. For each zoom-through, the frame of maximum displacement is within ±1 f of the cut.

## 4.6 Edit rhythm

- Median hard-cut shot length **1.8-3.5 s** (long-form: 2.5-5 s). No shot >12 s unless something in it is still building.
- A new visual beat (a cut or a new element) at least every **3 s** (long-form: 4 s).
- **Mode rotation**: map, chart, document / headline, collage / photo, footage, big-number type beat. No single mode runs longer than 12 s (long-form: 20 s); ≥4 distinct modes appear.
- A composition is used at most twice (an anchor revisit counts as a deliberate second use).
- Check: scene-detect cut list (threshold tuned so the cuts match a frame review); median in range. Sliding 3 s windows over the 4 fps sheet each contain a cut or a new element. Mode label per shot: max run within limit, ≥4 modes.
