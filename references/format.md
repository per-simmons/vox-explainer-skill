# Format, conventions and delivery

## Conventions used in every reference file

- Technique names are the industry / After Effects terms. They name the *look*; build it with whatever tools you choose.
- Every frame count is at **30 fps**. "f" means frames. 1 f = 33.3 ms.
- Sizes are a percentage of the frame. For the default vertical frame (1080×1920): **W** = 1080 px, **H** = 1920 px, so "2% H" = 38 px. For 16:9 see the long-form profile below.
- Easing names map to CSS `cubic-bezier`:
  - **Strong ease-out**: `cubic-bezier(0.16, 1, 0.3, 1)`. Default for entrances.
  - **Easy Ease** (After Effects F9, 33% influence): `cubic-bezier(0.33, 0, 0.67, 1)`. Camera moves that start and land.
  - **Extreme ease-in-out**: `cubic-bezier(0.85, 0, 0.15, 1)`. Zoom-throughs.
  - **Linear**: only for slow creeps on stills and for texture drift.
- Every rule ends in a **Check**: a pass/fail test on frames pulled from the final video, on its audio with a meter, or on the stems and timing files listed in §1.4. "Fails" means the build fails that check.

## 1.1 Video (default: vertical reel)

| Parameter | Value |
|---|---|
| Resolution | 1080×1920, square pixels (SAR 1:1), no letterbox or pillarbox bars |
| Frame rate | 30/1 constant (not 29.97, not variable) |
| Duration | 60.0-90.0 s |
| Codec | H.264 High profile, `yuv420p`, BT.709 tagged, `+faststart` |
| Bitrate | 8-16 Mbps video; file ≤95 MB |
| Audio | AAC-LC, 48 kHz, stereo, 192-320 kbps |
| A/V sync | audio and video stream durations within 1 f of each other |

- Check: `ffprobe` reports 1080×1920, `r_frame_rate=30/1`, `avg_frame_rate=30/1`, h264 / High / yuv420p, aac 48000 Hz 2 channels, duration 60-90 s, file ≤95 MB.
- Check: frame 0 is not black and not a logo. The hook image is on screen and moving from frame 0.

## 1.2 Delivery

- The video file; a README / credits file with every source and asset credit; optionally a top-level `index.html` showing only the video centred on a plain background with play/pause.
- No credits on screen beyond source lines (see `evidence-graphics.md` §5.8). No end card with a channel name, no Vox wordmark, no Vox logo, no "Vox" text anywhere in the video.

## 1.3 Working resolution

- Render graphics at native resolution or higher. Any raster that the camera scales past 100% must be sourced at ≥1.5× its largest on-screen size, or be vector.
- Check: on the frame of maximum zoom in each shot, no element shows visible pixel stair-stepping or upscale softness at 100% view.

## 1.4 Verification artefacts (kept in the project, not shown on screen)

- `audio/vo.wav`, `audio/music.wav`, `audio/sfx.wav`: the three stems as mixed, same length as the video.
- `audio/words.json`: word-level VO timings (start, end, word).
- `qa/`: contact sheets at 4 fps of the final video, the loudness report, and the outputs of every scripted check.

## 16:9 long-form profile

Everything in the reference files applies, with these changes. Where a rule gives a size as % H or % W, apply it to the 16:9 frame's own W and H unless stated here.

| Item | Vertical reel (default) | 16:9 long-form |
|---|---|---|
| Resolution | 1080×1920 | 1920×1080 (3840×2160 if the sources hold up at 1.5× for every zoom) |
| Frame rate | 30/1 | 30/1 by default. At 24/1 (or 23.976), "on twos" = 12 poses/s and every frame count converts by ×0.8, rounded to an even number |
| Duration | 60-90 s | typically 4-15 min; the beat structure repeats per chapter (each chapter gets its own stakes, 4-6 evidence beats and a turn) |
| File size / bitrate | 8-16 Mbps, ≤95 MB | 16-40 Mbps at 1080p; no file cap |
| Type sizes | as given in % H of 1920 | use the vertical frame's **pixel** values (both frames share a 1080 px short side), then check legibility at 50% view; chart titles and big numbers may grow up to 1.5× |
| Captions | burned-in word-by-word captions required | optional. Long-form usually ships without burned captions (use a subtitle file). If burned in, keep the style and timing rules, block between 80% and 88% H |
| Safe areas | platform UI zones (see `captions-title.md` §6.2) | broadcast title-safe: text inside the central 90% of W and H; no text in the bottom-right 15% W × 15% H (player controls, end-screen elements) |
| Title box | on screen from frame 0, gone by 5.0 s | the same box may open the video, or a full-frame title card may follow a 10-30 s cold open; it never precedes the first spoken fact |
| Edit rhythm | median shot 1.8-3.5 s | median shot 2.5-5 s; a new beat at least every 4 s; no single mode >20 s |
| Parallax shots | ≥3 | ≥1 per minute |
| Type-only beats | ≤1 per 20 s | ≤1 per 30 s |
| Whips / whooshes | ≤1 whip per 30 s; whooshes ≤1 per 6 s | unchanged |
| Music | one continuous bed | one bed per chapter; changes happen at chapter turns, with a breath gap |
| Ending | 1.0-3.0 s designed end frame | 2-5 s designed end frame; still no subscribe card, montage or logo card inside the piece |
| Loudness | −16 LUFS ±1 | −14 to −16 LUFS integrated; true peak ≤−1.0 dBTP |
