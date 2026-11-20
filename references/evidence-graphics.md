# Evidence graphics

The devices that put real evidence on screen. All frame counts at 30 fps.

## 5.1 Document / headline callout ("screenshot journalism")

- **Definition**: a real article, filing, press release, regulator page or dataset page composited into the frame and read on camera.
- The real page, captured from its real URL: masthead or logo, headline, date and byline visible. Wording never changed.
- Placed at ~90% opacity over a related photo tinted to the field colour, or on the field with a paper-lift shadow. Width 80-92% of W (16:9: 50-70% of W).
- Irrelevant body text is defocused 6-12 px or replaced with greyed placeholder bars; only the read phrase is legible. Nothing is invented to fill it.
- Optional **screen treatment** for web pages: fine scanlines (Venetian Blinds at ~5% completion, finer than the type stroke), chromatic aberration ≤1.2 at the edges, slight exposure flicker ≤±3%. Text stays legible.
- Linear push 1-2%/s. No rotation.
- Check: every document shot shows a masthead, logo or outlet name, and a date; the headline text matches the live or archived source word for word (the README links it).

## 5.2 Highlighter swipe (marker highlight)

- **Definition**: a solid `#FFF200` rectangle in **Multiply** blend mode (or matted behind the type) that wipes across words as they are spoken.
- Height: from 15% below the baseline to the cap height plus 10%. Hard top and bottom edges; slightly ragged vertical ends (2-4 px roughness). Skew ≤1°.
- Sweep: **12-36 f** (0.4-1.2 s), pacing word by word with the VO, on twos.
- **Sync tolerance**: the sweep starts within **±3 f** of the VO start of the first highlighted word and reaches the end of the phrase within ±3 f of the end of the last highlighted word.
- The ink stays black: text pixels under the highlight stay ≤60/255 luminance.
- One highlighted phrase per document at a time. At least **2 highlighter swipes** in the video.
- Check: for each sweep, compare the first frame where the highlight is visible and the frame where it completes against `words.json`: both within ±3 f. Sample text pixels under the highlight: luminance ≤60. A highlight in Normal mode that greys the text fails.

## 5.3 Circle annotation (marker ellipse)

- A loose hand-drawn ellipse that writes on around a word or feature: open or overlapping, total sweep 370-400° (it overshoots its start), slightly irregular (Roughen Edges or Turbulent Displace ≤2 px).
- Stroke 3-5 px, `#C8453C` (or the accent on dark fields). Draws on in **13-18 f**, synced to the word ±3 f.
- Does not cross the circled text.
- Check: the ellipse is not a closed geometric circle; stroke ≤5 px; no glow; it starts within ±3 f of its word.

## 5.4 Underline and arrow

- **Underline**: hand-drawn stroke 4-6 px, draws left to right in 8-12 f, synced to the word.
- **Arrow**: two strokes with staggered **Trim Paths**: shaft first (8-10 f), head after the shaft completes (4-6 f). Roughened edge. Never clip-art or 3D.
- Check: the arrowhead's first visible frame is after the shaft's last growing frame.

## 5.5 Label chip and callout with leader line

- **Label chip**: a solid rectangle tight behind a word. Padding 0.3 em vertical, 0.5 em horizontal, square corners, one chip colour for the piece (near-black, or `#A60000` red, or the navy field colour). Text caps sans; sub-chip in italic serif.
- **Callout with leader line**: chip, then a 2-3 px hairline leader, then a ring or dot on the target. Timing as `motion.md` §4.3. The leader touches its target. The label then holds ≥2 s with no further motion of its own.
- Check: chip padding is consistent (±2 px) across all chips; corners are square; no chip has a shadow, gradient or rounded "app" shape; every leader ends on its target.

## 5.6 Charts (chart build-on)

- Sit on the field with **no card, box or panel**.
- Build order in VO order: title word by word → gridlines (≈15% opacity, 1-2 px) and axis labels → series → end-value label after the series arrives → source line.
- **Line**: draws left to right in **60-75 f**, round caps, 1-1.2% W stroke. End label appears 4-8 f after the line arrives. A second series follows after a beat of ≥12 f.
- **Bars**: build in ~30 f total with a 2 f stagger; values inside or at the end of bars. The highlighted bar or row is outlined or takes the accent.
- Every chart: axis units, a source line, values that match the source and the VO.
- Forbidden: 3D bars, drop-shadowed bars, pie charts with >5 slices, rainbow palettes, unlabelled axes, animated counters that tick through every value faster than they can be read.
- Check: each chart frame at completion shows a title, units, a source line and no container. Line draw duration counted in frames: 60-75. Values spot-checked against `research/sources.md`.

## 5.7 Maps

- **Base**: flat two-tone (land `#121212`, sea `#2A446C`) or black land on paper off-white. Borders hairline at ~20% contrast. Real geodata (for example Natural Earth, public domain). No default web-map tiles, road networks or label clutter.
- **Map-continuity system**: one master vector map per video, every map shot taken from it by camera move; vector or high-resolution so it never pixelates on zoom.
- **Labels**: condensed bold caps placed on the land mass, no box; italic serif for localities. Labels pinned to their geographic point (Z-depth layering: lifted a few px above the map plane so they parallax slightly).
- **Country / region highlight fill**: the region filled in the accent or a data colour and revealed by opacity or a left-to-right mask wipe of 12-20 f; the fill edge matches the border at every zoom.
- **Spatial-data dots**: one dot per real item (facility, site, campus, event) from a dataset you can name; dot 0.8-1.5% W; they build on in groups, 2 f stagger.
- **Route / connection line**: dashed `#FFF200` (dash ≈2% W, gap ≈1.3% W, stroke ≈1% W), draws on head-first over **90-105 f** while the camera follows its head. Endpoints: filled dot plus a dashed arrival ring; both endpoints labelled.
- **Measurement callout** (dimension line): dashed span with end ticks and a label that carries a unit and a conversion or context; label fades in 15 f, holds 2-3 s, fades before the line.
- Check: every map shot has labelled places and a source line for its data; no frame shows default map labels or roads; zoomed frames show no pixelation; labels do not slide relative to their points during camera moves; route draw counted at 90-105 f with labelled endpoints.

## 5.8 Source line (citation super)

- Every third-party image, document, chart, map dataset and clip carries a visible source line for its full time on screen.
- Format: caps with tracking +5-8% in the sans, or small caps; `OUTLET | TITLE OR DATASET, YEAR` or `SOURCE: …`; 1.1-1.4% H; off-white at ~60% opacity on dark, near-black at ~60% on light. Data credits inside graphics may sit in brackets above a number: `[AGENCY DATASET, 2025]`.
- Position: anchored to the lower-left edge of the artifact it credits, 8-16 px below it; for full-bleed images, at the left text margin (7.5% W) with its baseline at 68-70% H (16:9: baseline at 88-90% H).
- Never a fabricated or approximate source name.
- Check: on the 4 fps sheets, every frame showing third-party material shows a source line; every source line text maps to an entry in `research/sources.md` or the README.

## 5.9 Big-number beat (kinetic typography, restrained)

- A single number with its unit, set in the sans at 5-8% H, centred in a flat circle chip (near-black or the field's darker tone) with a bracketed source above it; it builds by matte reveal, not by a counter.
- At most one type-only beat per 20 s (long-form: per 30 s).
- Check: count type-only shots; within the limit; each carries a unit and source.

## 5.10 Footage and photos

- In the vertical frame, 16:9 footage or photos sit centred at full width with an enlarged, heavily blurred (Gaussian σ 40-60 px), darkened (−30 to −50%) copy of themselves filling above and below; or they are placed as an **inset frame** on the field (78-92% W, soft paper-lift shadow). Never stretched; never center-cropped so the subject is lost. In 16:9, footage runs full frame or as an inset (60-80% W).
- Real footage clips run 1-3 s, cut on action, on ones, credited. Archival is left as found (no AI upscaling, restoration or colourising); a shared light treatment (soft edge blur, grain, ≤2 px edge chromatic aberration) is allowed to make mismatched sources sit together.
- Check: aspect of the main image in each footage shot matches its source; no footage shot has held-frame (twos) cadence; each is credited.
