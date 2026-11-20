---
name: vox-explainer
description: Make a Vox-style animated explainer video in the classic 2019-2022 stepped-collage look (paper textures, cut-out collage with 2.5D parallax, highlighter swipes on real documents, map and chart build-ons, motion on twos, yellow accent, word-synced captions). Default output is a 9:16 1080x1920 reel of 60-90 s; 16:9 long-form is supported. Use when asked for a "Vox-style explainer", an "animated explainer reel", a "collage explainer video", or an explainer that should look like classic Vox. The workflow is style research, topic research with sourced claims, script and voiceover with word timings, scenes built to the audio, render, then QA on pulled frames and an audio meter against a pass/fail checklist.
---

# Vox-style animated explainer

A style guide and production workflow for explainer videos in the look of classic Vox animated explainers from the 2019-2022 stepped-collage era. Every technique is named with its parameters and ends in a pass/fail **Check** run on the finished file.

> Independent style guide. Not affiliated with, endorsed by or connected to Vox Media. Vox is named only as the style reference. Never put the Vox name, logo or wordmark in the output.

The principle behind everything: **visual evidence, not decoration.** Each picture shows the thing being said, and real, sourced artifacts carry the frame. Most of what makes these videos read as AI-made comes from breaking that rule or from motion that is too smooth (see `references/tells.md`).

The skill is tool-agnostic. Build it with any animation, compositing or code-based render stack that can hit the numbers. Frame and audio checks assume a command-line media tool such as `ffmpeg`/`ffprobe` and a small image-analysis script, but any equivalent works.

## Reference files

Read the ones a step names before doing it. Numbers in them are requirements, not suggestions.

| File | Covers |
|---|---|
| `references/format.md` | Conventions (frames, sizes, easing), resolution, codec, delivery, verification artefacts, 16:9 long-form profile |
| `references/story-script.md` | Principle rules, anchor visuals, pace, hook, beat structure, script rules, ending, script table |
| `references/look.md` | Palette, typography, texture stack, layer counts, cut-outs, 2.5D parallax |
| `references/motion.md` | Stepped animation, easing, entrances, camera, transitions, edit rhythm |
| `references/evidence-graphics.md` | Document callouts, highlighter, circles, arrows, chips, charts, maps, source lines, big numbers, footage |
| `references/captions-title.md` | Word-by-word captions, safe areas, title box, name cards |
| `references/sound.md` | Voiceover, music bed, sound design, master |
| `references/sourcing-licences.md` | What real and generated material may be used, and how it is logged |
| `references/tells.md` | The ranked AI tells, all forbidden |
| `references/checklist.md` | The final pass/fail table |

## Workflow

Work in this order. Do not animate anything before step 3 is done; the audio is the clock for every scene.

### 1. Research the style first and write a breakdown

Before touching the topic, study real classic Vox animated explainers from 2019-2022 (the collage-heavy explainers and music-explainer episodes of that period). Pick 3-5 and, for each:
- Pull frames at 4 fps for the whole piece and at 30 fps for 3-4 short stretches (an entrance, a highlighter swipe, a zoom-through, a parallax shot).
- Measure what you can: palette samples, accent coverage, type classes, how many frames each pose holds (on ones, twos or threes), shot lengths, element counts per frame, caption placement, how the open and the end are built.
- Note the sound: VO pace, how the bed ducks and rises, which moves get an effect.

Write `research/style-breakdown.md`: what you observed, with timestamps, set against the reference files. Where your observations disagree with a reference number, note it and keep the reference number unless the evidence is strong. This step calibrates your eye; it is not a source of footage. Never reuse frames, graphics or audio from those videos.

### 2. Research the topic with sourced claims

- Find the real artifacts the story will show: headlines, filings, press releases, regulator pages, datasets, licensed photos and footage, public-domain geodata. Capture documents from their live URL or a dated archive copy.
- Write `research/sources.md`: every claim, number and plotted series with outlet, title, date and URL. A claim with no source does not go in the script.
- Name 2-3 **anchor visuals** (recurring images that carry the story) before scripting. See `references/story-script.md` §0.2.
- Check the licence of every photo, clip, music track and effect now, not at the end. See `references/sourcing-licences.md`.

### 3. Script, then voiceover with word timings

- Write the **script table** first (`references/story-script.md` §2.6): every row names its VO line, visual mode, what is shown, its source, whether it is an anchor, and its sound effect.
- Hit the hook, beat structure, word budget and script rules in `references/story-script.md`.
- Record or synthesise the voiceover (`references/sound.md` §7.1). Fix pronunciation of every name, acronym and number before moving on.
- Produce `audio/words.json` with word-level start and end times (forced alignment or a word-timestamped transcription). Re-time the script table from it.
- Measure WPM, speech coverage and gap distribution now. If they fail, re-record; do not fix pace in the edit.

### 4. Build scenes to the audio

- Lay out every scene against `words.json`. Each element lands on the word that names it (no more than 6 f early), staggered 4-8 f.
- Follow `references/look.md` for the field, type, texture stack and cut-outs; `references/motion.md` for cadence, easing, camera and transitions; `references/evidence-graphics.md` for each evidence device; `references/captions-title.md` for captions, title box and safe areas.
- Graphics move on twos or threes; real footage stays on ones. Every graphic shot has camera motion.
- Mix music and sound design against the VO stem (`references/sound.md`). Keep the three stems separate: `audio/vo.wav`, `audio/music.wav`, `audio/sfx.wav`.

### 5. Render

- Render to the delivery spec in `references/format.md` §1.1 (default 1080x1920, 30/1 CFR, H.264 High yuv420p, AAC 48 kHz stereo, −16 LUFS).
- Write the credits file: every source, asset, font, music and effect with its licence.

### 6. QA on pulled frames and an audio meter

Never sign off from watching it once. Measure.
- Pull 4 fps contact sheets of the whole render, an 8 fps sheet of 0-2 s, and 30 fps frame steps of at least 5 builds, every zoom-through and every highlighter swipe. Save them under `qa/`.
- Run the scripted checks: `ffprobe` format, per-frame accent share and saturation, field-patch sampling, frame-difference cadence and static detection, scene-detect cut list, caption timing against `words.json`.
- Run the audio meter on the final file and the stems: integrated loudness, true peak, loudness range, clipping, silence holes, music-under-VO difference, SFX onset alignment.
- Go through `references/checklist.md` row by row and record pass/fail with the measured value. Then review every row of `references/tells.md` against the sheets.
- Fix every failure and re-run the affected checks on a fresh render. Report the final table.

## Output

- The video file (`reel.mp4` for vertical).
- A credits/README file with every source and asset credit and licence.
- Optional: a minimal `index.html` that shows only the video centred on a plain background with play/pause.
- Kept in the project, not shown: the three stems, `audio/words.json`, `research/style-breakdown.md`, `research/sources.md`, the script table, and `qa/` with contact sheets, the loudness report and every check's output.
