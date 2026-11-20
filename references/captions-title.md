# Captions, title and safe areas

Values are for the default 9:16 1080×1920 frame. For 16:9 changes see `format.md`.

## 6.1 Word-by-word captions

- **Style**: the video's sans, weight 600-700, sentence case, off-white `#F4F1EA`-`#FCFCFC`. Cap height 1.9-2.3% H (font size about 50-60 px). Leading 1.15-1.25.
- **Pages**: 3-7 words per page, 1-2 lines, max line width 80% W, centred. Pages break at phrase boundaries, never mid-name or mid-number.
- **Active word**: a solid `#FFF200` box behind the spoken word with near-black `#141413` text, padding 4-8 px horizontal, 2-4 px vertical, square corners. It jumps word to word on the word timings. No bounce, scale, colour fade or per-word animation beyond the box moving.
- **Readability**: on light or busy backgrounds a flat scrim of 20-30% black sits behind the caption block (no rounded pill, no blur glass). No outline, no drop shadow on caption text.
- **Text**: verbatim to the VO, including numbers. Outlet and publication names in the italic serif.
- **Timing**: each word's box appears within **±2 f** (±67 ms) of that word's start in `words.json`. A page appears with its first word and clears within 6 f after its last word, or is replaced by the next page.
- Forbidden: giant captions, one word per screen at 6%+ H, colour per word, emoji, stroke-outlined text, karaoke fill gradients.
- Check: transcribe the final video's audio and compare against caption OCR from frames: word error rate 0 for caption text vs VO. For 20 random words, the frame where the box arrives is within ±2 f of the word start.

## 6.2 Safe areas (9:16)

| Zone | Rule |
|---|---|
| Top 0-11% H (0-211 px) | no text and no key content |
| Bottom 80-100% H (1536-1920 px) | no text and no key content |
| Right 88-100% W (950-1080 px), between 45% and 80% H | no text |
| Left and right text margins | text stays inside 7.5%-92.5% W (81-999 px) |
| Caption block | between 72% and 79% H (1382-1517 px) |
| Title box | top edge 52-60% H, bottom edge ≤70% H |
| Source line (full-bleed) | baseline 68-70% H, left margin |
| Chart titles | top-left, starting at 12-20% H |

- Picture (photos, maps, fields) is full-bleed; only text and key evidence obey the zones.
- Captions, title box and source lines never overlap one another.
- Check: overlay the zone grid on the 4 fps sheets: zero text pixels in the forbidden zones; no overlaps.

## 6.3 Title box (first seconds)

- A solid `#FFF200` rectangle, no border, shadow or rounded corners, 80% W centred (10% side margins), top edge at 52-60% H.
- Text: near-black bold caps grotesque, 2-3 centred lines, cap height 2.3-3.0% H, leading ~1.1. It states the topic as a plain, question-free headline, for example "WHY CITIES ARE TEARING DOWN THEIR HIGHWAYS".
- On screen from frame 0; it enters by a 6-10 f width wipe or is already present; it leaves by a hard cut or 6-10 f wipe between 2.5 s and 5.0 s.
- Check: present at frame 0 (or fully on by f 10), gone by 5.0 s; colour sample within ΔE ≤6 of `#FFF200`; width 864 ± 11 px (80% of a 1080 px W).

## 6.4 Name and role card (only if a real person is quoted on camera)

- `#FFF200` card, 80% W, bold name over an italic serif role line, on the person's first appearance, held 2-3 s. People appear only through licensed real footage or photos.
