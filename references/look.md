# Look

## 3.1 Palette

One muted base field family for the whole piece, plus at most one secondary field for a mood shift, plus 1-2 desaturated data colours, plus **one hot accent: yellow `#FFF200`**.

| Role | Values |
|---|---|
| Base field (pick one family) | near-black `#141713` / `#101010`; desaturated navy `#202F40` / `#2A446C`; sage grey `#6C6C66`; paper off-white `#E5E5E6`-`#F3F2F3` |
| 2020-era inset fields (optional) | soft pastel pink `#E8C9CF`-ish, dusty blue `#8FA3B8`-ish, low-contrast blooms only |
| Map | land `#121212` (highlighted land `#2A2A2A`), sea `#2A446C`, borders at ~20% contrast; or black land on paper off-white |
| Data colours | blue `#7EBAC6`, pink `#EA9696`, neutral `#B4BAAE`, muted green `#5E7F5A` |
| Type on dark | off-white `#F4F1EA`-`#FCFCFC` |
| Type on light | near-black `#141413` |
| Hand annotation | desaturated red `#C8453C` |
| Accent | `#FFF200` only: highlighter, title box, active caption word, route lines, one hero fill |

Rules:
- **Accent coverage.** Accent pixels (within ΔE2000 ≤12 of `#FFF200`, or of its Multiply result on paper, about `#F5D90A`) average **2-6%** of pixels over the whole video. Any single frame: ≤12%, except frames where the title box is up, ≤20%.
- **Saturation.** Mean HSV saturation of graphic frames ≤0.30. No saturated colour other than the accent.
- **No pure white or black in fields and type.** Fields and graphic type never use `#FFFFFF` or `#000000`. (Real photos and scans keep their own values.)
- **No gradients, neon or glow.** Fields are flat (plus texture, §3.3). Pastel blooms, if used, vary by ≤15 levels across the frame.
- Check: run a per-frame script on 4 fps frames: accent share per frame and mean; mean saturation over graphic shots; count of pure `#FFFFFF` / `#000000` pixels inside field regions (must be 0 in sampled 40×40 px field patches). Visual check: no element has an outer glow or a gradient fill.

## 3.2 Typography

**Exactly two type families**, by class:
1. **Bold American-gothic grotesque sans.** Caps for labels, chips and map labels; sentence case for titles and captions. Weights 600-800. A condensed width of the same family is allowed for map labels.
2. **High-contrast transitional / modern serif**, used in **italic** for names, roles, subtitles, outlet names and year numerals; roman for occasional title words.

Acceptable open-licence fonts:

| Class | Use one of |
|---|---|
| Grotesque sans | Libre Franklin, Public Sans, Archivo (with Archivo Narrow / Condensed for map labels), Franklin-class equivalents under OFL |
| Italic serif | Libre Caslon Text / Display, Libre Baskerville, Source Serif 4, Newsreader |

Forbidden as the video's own type: Inter, Roboto, Open Sans, Montserrat, Poppins, Lato, Nunito, Raleway, Playfair Display, Merriweather, Arial, Helvetica, system-ui / browser default, any monospace except inside a real screenshot, any script or handwriting font.

Sizes (cap height unless stated; % H of the 1920 px vertical frame, see `format.md` for 16:9):

| Element | Size | Notes |
|---|---|---|
| Title box text | 2.3-3.0% H (44-58 px) | bold caps, leading 1.05-1.15 |
| Chart / section title | 3.0-4.0% H | bold sentence case, top-left aligned |
| Label chip text | 1.6-2.2% H | bold caps, tracking +2 to +5% |
| Italic serif subtitle / role | 70-85% of the label size above it | |
| Map hero label | 4-6% H | condensed bold caps, on the land mass, no box |
| Map secondary label | 2-3% H | |
| Big number | 5-8% H | sans, inside a circle chip or on the field |
| Caption | see `captions-title.md` §6.1 | |
| Source line | 1.1-1.4% H | see `evidence-graphics.md` §5.8 |

- Real documents and headlines keep their own typefaces; they are artifacts, not the video's type.
- No outline strokes, drop shadows or glows on graphic type. The one exception: place labels over busy satellite photos get a soft shadow ≤30% opacity, ≤4 px blur.
- Check: list every font file loaded by the build in the README with its licence. Visual check on the 4 fps contact sheets: ≤2 families in the video's own type; no banned font; no outlined or glowing type.

## 3.3 Texture stack (2019-2022 collage era)

Bottom to top:
1. **Field colour** (flat).
2. **Paper texture overlay** or **grid background**: scanned paper in Multiply at 10-40% on light fields, Overlay / Soft Light at 10-30% on dark fields. A grid, if used, sits at 5-15% opacity with its lines slightly roughened.
3. **Content**, with **Roughen Edges** (border ≈2-3 px) on vector lines, chips, arrows and frames so they read as printed or cut, not as CAD.
4. **Halftone** (optional) only on cut-out photos: dot pitch 4-8 px, never across type or the whole frame.
5. **Boil / looping texture**: 3-5 texture states, one of them rotated 90°, each held **6-10 f** (3-5 Hz), Screen or Overlay at ≤50%.
6. **Stepped animation** on graphics (`motion.md` §4.1).
7. **Edge-masked chromatic aberration** (≤2 px at the frame edges, 0 px in the centre 60% of the frame) plus a **vignette** (corners −5 to −15% luminance, no visible oval).

Limits:
- Paper and grain amplitude on flat fields: standard deviation 3-8 levels of 255 in a 40×40 px patch. Visible at 100%, invisible at thumbnail size.
- Texture is screen-locked or boils; it never slides with the camera like a sticker.
- Check: patch standard deviation on 10 field samples within 3-8. Frame-difference on a held field patch shows texture changes every 6-10 f, not every frame and not never. Chromatic aberration: R and B channel edges in the centre 60% align within 0.5 px; at the corners offset ≤2 px. No visible vignette edge.

## 3.4 Layer counts

- A typical graphic frame shows **4-8 visible elements** (field, texture, 1-3 content objects, 1-2 labels, source line). ≤2 reads as a slide; ≥12 reads as clutter.
- Collage shots are built from **3-5 depth planes**.
- A 60-90 s video uses **≥25 distinct image assets** (photos, documents, cut-outs, map layers, textures). Collage pieces of this era run 30-60 for a short.
- Check: count visible elements on one frame per shot from the contact sheet: every graphic shot in 4-11. Asset folder holds ≥25 distinct images, each logged in the README.

## 3.5 Cut-out rules

- **Cut-out**: a subject masked from its background and placed as its own layer. Real photographs for real people and real places; generated images only for anonymous subjects and generic objects (`sourcing-licences.md` §8.4).
- **Edges**: clean, ≤1 px fringe, no halo of the old background, no chroma spill. Or a deliberate **offset stroke** (die-cut sticker border): Outside stroke 4-10 px, off-white `#F4F1EA` or the paper colour, constant width ±1 px, never coloured, never >12 px.
- **Drop shadow** (paper lift): three stacked soft shadows: 30% / distance 3 px / softness 10 px; 20% / 6 / 50; 10% / 10 / 50; all at the same angle (≈135°) across every layer in the shot, colour black or the darkened field. Never a hard 100% shadow, never offset >15 px.
- **Anatomy**: no floating limbs, no hands detached from arms, no missing or extra fingers, no objects held with no grip. Every person stands on, sits on or is cropped by something.
- **Photo treatment**: cut-out photos are converted to the piece's palette: B/W, **Tritone** (highlights = paper, midtones = field colour, shadows = near-black) or B/W with one flat-filled region in the accent or a data colour. No full-colour stock photos dropped on a muted field.
- Check: zoom 200% on every cut-out edge in the contact sheets: no halo, no green or white fringe, stroke width constant. Sample 20 edge pixels per cut-out: none with hue 90-150° and saturation >0.35 (green spill). Shadow angles agree within 10° per shot.

## 3.6 2.5D parallax (multiplane camera)

- **Definition**: flat layers at different Z depths filmed by a moving camera, so nearer layers cross the frame faster. A uniform scale of a flat image is a Ken Burns move, not parallax.
- Planes: background, mid (subject), foreground, then type and texture on top (type and texture screen-locked or on their own plane).
- Camera dolly or truck: **5-15% of W** over a 3-6 s shot. Foreground-to-background speed ratio **1.5-3×**.
- **Depth-of-field**: background plane defocused 6-12 px; the hero plane sharp by the time the VO names it.
- Plates overscan ≥110% of the frame area they can reach, so no layer edge or empty canvas is ever exposed.
- Layers never interpenetrate; labels stay pinned to the point they mark.
- At least **3 parallax shots** in a 60-90 s video (≥1 per minute in long-form).
- Check: on two frames 1 s apart in each parallax shot, measure the displacement of a foreground feature and a background feature: ratio 1.5-3. No frame shows a plate edge, empty canvas or interpenetration.
