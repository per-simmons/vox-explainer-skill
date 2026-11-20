# Final checklist

Run every row on the final render and record pass/fail with the measured value. Values are for the default 9:16 reel; apply the 16:9 substitutions in `format.md` for long-form.

| ID | Check | How to verify |
|---|---|---|
| F1 | 1080×1920, 30/1 CFR, H.264 High yuv420p, AAC 48 kHz stereo, 60-90 s, ≤95 MB | `ffprobe` |
| F2 | Frame 0 is the moving hook image, not black or a logo | Pull frame 0 and frame 10 |
| F3 | No Vox name, logo, wordmark or end card; no on-screen credits beyond source lines | 4 fps contact sheets + OCR |
| P1 | Every VO sentence's midpoint frame shows the evidence it describes | Script table vs frames at sentence midpoints |
| P2 | 2-3 anchor visuals, each in ≥2 non-adjacent shots; one returns at the end | Script table + sheets |
| P3 | ≥60% of shots contain a real sourced artifact | Shot list tally |
| S1 | First word ≤0.30 s; opening line is a concrete fact, no question | `words.json`, transcript |
| S2 | ≥3 eased motions and a real artifact in the first 2 s | 8 fps sheet of 0-2 s |
| S3 | Stakes number with unit and comparison before 12 s | Transcript + frames |
| S4 | Beat mix: ≥1 map, ≥1 chart, ≥2 document/headline, ≥1 collage beat; a sourced turn | Script table |
| S5 | 160-190 WPM over speaking time; speech coverage ≥85% | `words.json` |
| S6 | Last word to end 1.0-3.0 s; designed end frame on an anchor; music resolves, not truncated | `words.json`, music stem envelope, last frame |
| S7 | No banned phrases; every on-screen number spoken within ±2 s | Transcript + OCR |
| L1 | Accent `#FFF200` share 2-6% mean; ≤12% per frame (≤20% with title box) | Pixel script on 4 fps frames |
| L2 | Mean saturation of graphic frames ≤0.30; no glow, neon or gradient fields | Pixel script + review |
| L3 | No pure `#FFFFFF` / `#000000` in field patches or graphic type | Patch sampling |
| L4 | Exactly two type families, none banned; fonts and licences listed | README + sheets |
| L5 | Texture: patch std 3-8 levels; boil every 6-10 f; edge-only chromatic aberration ≤2 px; no visible vignette edge | Patch and frame-diff script |
| L6 | 4-11 visible elements per graphic shot; ≥25 distinct image assets | Sheet count + asset folder |
| L7 | Cut-outs: no fringe or spill at 200%, constant stroke ≤12 px, consistent shadow angle, no floating limbs | Zoomed crops |
| L8 | ≥3 parallax shots, FG/BG displacement ratio 1.5-3, no exposed plate edges | Feature tracking on frame pairs |
| M1 | Graphics ≥50% of moving seconds on twos/threes, ≤35% on ones; footage ≥90% on ones | Cadence classifier |
| M2 | No overshoot, bounce, scale-from-zero or spin in any entrance | 30 fps frame steps on 5+ builds |
| M3 | Elements staggered 4-8 f, each on its word ±3 f | Frames vs `words.json` |
| M4 | Static ≤15% of runtime, no static run >2.0 s; every graphic shot moves 3-10% | Frame-difference script |
| M5 | ≥1 zoom-through (speed peak on cut ±1 f), ≥1 map-continuity move, ≤1 whip per 30 s, no forbidden transitions | Cut list with types |
| M6 | Median shot 1.8-3.5 s; a new beat every ≤3 s; ≥4 modes, none >12 s | Scene detection + sheets |
| E1 | Every document shows masthead/outlet and date, wording identical to the linked source | README links vs frames |
| E2 | ≥2 highlighter swipes, Multiply, start and end within ±3 f of the words, ink ≤60 luminance | Frames vs `words.json`, pixel sample |
| E3 | Circles open and overshooting, ≤5 px, synced ±3 f; arrowheads after shafts | Frame steps |
| E4 | Chips square, consistent padding, no shadow; leaders touch targets | Sheets |
| E5 | Charts: no container, units, source line, line draw 60-75 f, values match sources | Frames + `research/sources.md` |
| E6 | Maps: real geodata, labelled places, no default clutter, no pixelation, pinned labels, route 90-105 f with labelled endpoints | Frames + sheets |
| E7 | Every third-party element has a source line for its full time on screen, 1.1-1.4% H | Sheets + OCR |
| E8 | 16:9 sources centred with blurred fill or inset; never stretched; footage on ones and credited | Frames |
| C1 | Captions verbatim to VO (0 word errors), 3-7 words per page, cap height 1.9-2.3% H | Transcript vs OCR |
| C2 | Active-word yellow box within ±2 f of each word start; no bounce or scale | 20 sampled words vs frames |
| C3 | No text in forbidden safe-area zones; captions, title box and source lines never overlap | Zone overlay on sheets |
| C4 | Title box `#FFF200`, 80% W, top edge 52-60% H, on by f 10, gone by 5.0 s | Frames 0-150 |
| A1 | VO dry, natural gaps (std ≥0.12 s), correct pronunciation of every name and acronym | `words.json`, transcript match |
| A2 | One instrumental bed, no vocals, 10-14 LU under VO during speech, rises 4-8 dB in gaps ≥0.7 s | Stem loudness |
| A3 | SFX on ≥90% of visual events within ±2 f; whooshes only on zoom/whip/push, ≤1 per 6 s; ≤1 riser; no braam or typewriter clatter | Onset vs event list |
| A4 | −16 LUFS ±1 integrated, ≤−1.0 dBTP, LRA ≤8 LU, no clipped samples, no silent holes | `ebur128`, `astats`, `silencedetect` |
| R1 | Every photo, clip, music and SFX credited with a reuse-permitting licence | README |
| R2 | Generated assets limited to anonymous subjects, generic objects and textures; none are documents, charts, maps, logos, real places or real people | README + frames |
| R3 | No item from the tells table (`tells.md`) appears | Full review of 4 fps sheets and audio checks |
