# Story and script

Sections are numbered to match the checklist IDs.

## 0. Principle: visual evidence, not decoration

0.1 **Every visual explains.** The picture shows the claim being spoken: the filing that signs the deal, the chart of the trend, the map of the place. A picture that only sets a mood (glowing screens, a generic stock building, a robot) is decoration and does not belong. Talk about what you can show.
- Check: pause on the midpoint of every VO sentence. The frame must contain the artifact, data or place that sentence is about. One sentence with only mood imagery fails.

0.2 **Anchor visuals.** Before scripting, name 2-3 anchor visuals: the recurring images that carry the story (for example one master map of the places involved, one master chart of the key trend, the key document). Each anchor appears at least twice: introduced, then revisited or built on. One anchor returns in the ending.
- Check: the script table (§2.6) lists the anchors; each appears in ≥2 non-adjacent shots.

0.3 **Real artifacts carry the frame.** Real documents, headlines, filings, regulator pages, datasets and licensed photos are the primary material. Generated imagery is limited to the uses in `sourcing-licences.md` §8.4.
- Check: ≥60% of shots contain at least one real, sourced artifact (document, headline, chart from a named dataset, map from real geodata, licensed photo or footage).

0.4 **One idea per beat, one beat per clause.** A new element lands on each spoken clause; nothing appears that the VO has not reached.
- Check: no element (label, number, highlight, chart series) appears more than 6 f before the word that names it.

## 2.1 Length and pace

- VO rate **160-190 words per minute** measured over speaking time. Vox's own vertical cut-downs run 168-193.
- Word budget: about 170-190 words for 60 s, 250-280 words for 90 s.
- Speech covers **≥85%** of the runtime.
- Check: compute WPM from `words.json` (words ÷ summed speaking time). Speech coverage = summed word durations plus intra-sentence gaps <0.35 s, divided by runtime.

## 2.2 Hook: the first 2 seconds

- **First spoken word at ≤0.3 s.** No silent lead-in, no logo sting, no title-only card.
- The first line is a **concrete, dated fact or event**, stated plainly, that is surprising on its face. It is never a question, never "In this video", never "Have you ever wondered".
- Frame 0 shows the anchor visual already in motion (a push or drift) with the **title box** (`captions-title.md` §6.3) over it.
- Within the first 60 f, three distinct motions land, each with strong ease-out and none popping on (for example: camera push, a label sliding into a matte, a highlighter or fill starting).
- Check: `words.json` first start ≤0.30 s. The 0-2 s contact sheet at 8 fps shows ≥3 separate eased motions and a real artifact on screen. Transcript line 1 contains no "?" and no "this video".

## 2.3 Beat structure

| Time (of a 75 s reel; scale proportionally) | Beat | Content |
|---|---|---|
| 0-3 s | Hook | The concrete fact, title box on screen |
| 3-12 s | Stakes | Why it matters, with one number that has a unit and a comparison, landed by 12 s |
| 12-55 s | Evidence | 4-6 beats. Each beat = one claim + one source artifact + one visual mode. Beat length 6-12 s |
| 55-68 s | Turn | The complication, sourced (cost, timeline, regulation, what is not built yet, who disagrees and on what evidence) |
| 68-75 s | Ending | The takeaway in plain words, a callback to an anchor visual, music resolves, designed end frame |

- Evidence beats must include at least: one **map** beat, one **chart** beat, two **document / headline** beats, one **2.5D collage** beat. The turn is a fact with a source, not opinion.
- If the topic has no geography, the map beat may be replaced by a second chart or a diagram beat; record the substitution in the script table.
- Check: the script table (§2.6) shows each beat type at least as many times as listed, and a stakes number with unit and comparison before 12.0 s.

## 2.4 Script rules

- Short lines, one idea per line, easy to say aloud. Sentences ≤20 words; median ≤13.
- Active voice, present or simple past. Named actors (the company, the agency, the regulator), never "experts say".
- Every number carries a unit and a comparison or context ("enough to power about X homes", "about Y% of the total"). Spell numbers for the voice the way a narrator says them.
- Dates are given when they matter ("In September 2024, …"). The story is current to the day of the build.
- No rhetorical questions except optionally the final line. No "Here's the thing", "But here's the catch", "Let's dive in", "game-changer", "revolutionary", "the future is".
- Every on-screen claim matches the VO in the same beat, word for word for numbers and names.
- Check: a transcript of the final video contains none of the banned phrases; every on-screen number appears in the VO within ±2 s.

## 2.5 Ending

- The last VO line restates the takeaway in plain words. It lands on an anchor visual (a callback), not on a new topic.
- After the last word: **1.0-3.0 s** designed end frame. This is a composed final image (the anchor visual, settled, with one final label or the completed build), held with a camera creep. The music resolves to a final chord or downbeat within 1-2 s of the last word.
- Forbidden: outro montage, "subscribe", "follow for more", a logo card, a fade to black that starts before the last word ends, music cut mid-phrase.
- Check: last word end to video end = 1.0-3.0 s. The music stem's RMS falls by ≥20 dB within the last 2 s and its final non-silent sample is ≥0.3 s before the end (it ends, it is not truncated).

## 2.6 Script table (required)

Write the script as a table before any animation:

`# | VO line | start/end time | visual mode | visual (what is shown) | source (outlet, title, date, URL) | anchor? | SFX`

Every row names its visual before it is animated. Re-time the start/end column from `words.json` once the VO exists.
- Check: the table exists in the project; every row with a factual claim has a source that also appears in `research/sources.md`.

## Worked example of a hook and stakes (illustrative only)

Topic "why tech companies are buying nuclear power":
- Hook line: a dated deal ("In September 2024, a tech company signed a deal to restart a shut-down nuclear plant.") over the deal document, title box up.
- Stakes number: data-centre electricity demand with a unit and a comparison to a familiar total, landed by 12 s.
- Anchors: one master map of plants and data-centre regions, one demand chart, the deal document.

Replace every element with the real, sourced equivalents for your topic.
