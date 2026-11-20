# vox-explainer skill

An agent skill for making animated explainer videos in the look of classic Vox explainers from the 2019-2022 stepped-collage era: paper textures, cut-out collage with 2.5D parallax, highlighter swipes on real documents, map and chart build-ons, motion on twos, a single yellow accent and word-synced captions.

It is a style guide plus a production workflow. Every technique is named with its parameters, and every rule ends in a pass/fail check you run on the finished video's frames and audio. It also lists the ranked "tells" that make an explainer look AI-made, all forbidden.

- Default output: a 9:16 1080x1920 reel, 60-90 s. A 16:9 long-form profile is included.
- Tool-agnostic: use any animation, compositing or code-based render stack that can hit the numbers.

> Independent style guide. Not affiliated with, endorsed by or connected to Vox Media.

## What's inside

```
SKILL.md                         workflow and when to use it
references/
  format.md                      conventions, delivery spec, 16:9 long-form profile
  story-script.md                principle, anchors, hook, beats, script rules, ending, script table
  look.md                        palette, typography, texture stack, cut-outs, parallax
  motion.md                      stepped animation, easing, entrances, camera, transitions, rhythm
  evidence-graphics.md           documents, highlighter, annotations, chips, charts, maps, source lines
  captions-title.md              word-by-word captions, safe areas, title box
  sound.md                       voiceover, music bed, sound design, master
  sourcing-licences.md           what real and generated material may be used
  tells.md                       ranked AI tells (all forbidden)
  checklist.md                   final pass/fail table
```

## The workflow

1. Research the style from real classic Vox explainers and write a breakdown.
2. Research the topic; every claim gets a source.
3. Write the script table, record the voiceover, get word timings.
4. Build every scene to the audio.
5. Render to the delivery spec.
6. QA on pulled frames and an audio meter against the checklist; fix and re-run.

## Install

**Claude Code:** copy the folder into your skills directory.

```bash
git clone https://github.com/per-simmons/vox-explainer-skill.git
cp -r vox-explainer-skill ~/.claude/skills/vox-explainer
```

Or put it in a project at `.claude/skills/vox-explainer/`. It triggers on requests like "Vox-style explainer", "animated explainer reel" or "collage explainer video".

**Any other agent:** point it at `SKILL.md` and tell it to read the files in `references/` as each step requires.

## Example prompt

> Make a Vox-style animated explainer reel, 9:16, about 75 seconds, on why cities are tearing down urban highways. Use real sourced documents, a map of the cities involved and one chart of traffic data. Follow the vox-explainer skill end to end and give me the final checklist with measured values.

## Licence

MIT. See [LICENSE](LICENSE).
