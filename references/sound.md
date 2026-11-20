# Sound

## 7.1 Voiceover

- One narrator, human or synthetic, conversational documentary register: close-miked, dry, no reverb tail, no music-bed bleed in the VO stem.
- Rate and coverage per `story-script.md` §2.1. First word ≤0.3 s.
- **Natural pacing**: pauses vary with meaning. Inter-sentence gaps 0.15-1.0 s, with standard deviation ≥0.12 s across the video; 2-4 breath gaps of 0.7-1.0 s at section turns so the bed can rise. No gap >1.2 s before the last line.
- **Pronunciation**: every company name, acronym, place and number is spoken correctly; acronyms read as a narrator would (spelled letter by letter where that is the convention, units spoken in full: "gigawatts", not "G-W").
- Processing: high-pass ~80 Hz, gentle compression (2-3:1), de-essing; no audible artefacts, clicks or cut-off word endings.
- Check: from `words.json`: WPM, coverage, gap distribution and its standard deviation. A listen-free check: the VO stem's spectrogram shows no reverb decay tails >150 ms after phrase ends. A transcript of the final video matches the script word for word (pronunciation errors show as transcription mismatches).

## 7.2 Music bed

- One continuous instrumental bed (documentary score: pulsing synth, plucked strings, light percussion). No vocals. Licensed or generated with clear rights (credit in the README).
- Edited to the story: a change of texture or a drop on the turn (`story-script.md` §2.3); resolves to a final chord within 1-2 s of the last word.
- **Level**: during speech, the music stem's short-term loudness sits **10-14 LU below** the VO stem's. In VO gaps ≥0.7 s the bed rises **4-8 dB**, staying ≥4 LU below the speech level.
- **Ducking** (sidechain): duck depth 9-13 dB, attack 50-150 ms, release 300-600 ms.
- The bed never stops mid-piece without a story reason.
- Check: short-term loudness (3 s) of the music stem vs the VO stem over speech windows: median difference 10-14 LU. Over each gap ≥0.7 s the music stem rises 4-8 dB relative to its ducked level. Music stem present (above −50 dBFS RMS) from ≤0.3 s to the resolve.

## 7.3 Sound design: a sound on every move

- Every move gets a synced sound: transitions, element entrances, draw-ons, highlights, drop-ins. Each SFX transient lands within **±2 f** of its visual event.
- Vocabulary, literal to the action:

| Event | Sound |
|---|---|
| Paper drop-in, collage piece landing | paper slide / paper tap, short |
| Label chip, number, dot landing | soft click, tick or pop, no bass |
| Highlighter swipe | soft marker drag, length matched to the sweep |
| Circle, underline, arrow draw-on | pen or marker scratch, length matched to the stroke |
| Zoom-through, push-through, whip | whoosh with its peak on the cut or speed peak ±1 f |
| Map route draw | a soft continuous tone or pen line under the draw, not a whoosh |
| Chart bars building | a short run of soft ticks, one per bar or group |

- **Levels**: each SFX peak 10-18 dB below the concurrent VO peak; whooshes peak at −20 to −26 dBFS in a −16 LUFS mix; nothing masks a consonant.
- Limits: whooshes only on zoom-throughs, whips and push-through transitions, ≤1 per 6 s. Risers ≤1 in a 60-90 s video. No cinematic "braam", sub-bass booms, typewriter clatter (a write-on gets at most one soft tick per word), stinger hits on every cut, or a constant paper-rustle bed.
- Check: cross-correlate the onsets in `audio/sfx.wav` with the visual event list (cuts plus element start frames): ≥90% of visual events have an SFX onset within ±2 f; every whoosh aligns with a zoom-through / whip / push frame. Count whooshes ≤ runtime ÷ 6 s.

## 7.4 Master

- Integrated loudness **−16 LUFS ±1** (EBU R128 / ITU-R BS.1770) for side-by-side playback. True peak **≤−1.0 dBTP**. Loudness range ≤8 LU.
- No clipping: no samples at or above −0.1 dBFS, no inter-sample overs beyond the true-peak limit.
- No digital-silence holes inside the video (no run of samples below −70 dBFS longer than 100 ms before the music resolve).
- Check: `ffmpeg -af ebur128=peak=true` on the final file: I = −17 to −15 LUFS, TP ≤ −1.0 dBTP, LRA ≤8 LU. `astats`: peak level ≤ −0.1 dBFS, zero clipped samples. Silence detection (−70 dB, 0.1 s) finds nothing before the final resolve.
