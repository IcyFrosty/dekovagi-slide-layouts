# DekoVägi slide style guide (v1.0, 06.11.2026)

For people and AI models that make DekoVägi slides. The numbers come from `style.json` (the machine-readable copy of
this guide). They were measured from 17 past decks (205 slides) and unified where the decks disagreed. When this guide
and `style.json` differ, `style.json` wins. Units are points (pt) on the 1215 × 810 pt slide; for HTML at 1620 × 1080 px,
multiply by 4/3.

## 1. Slide and grid

| | pt | px (×4/3) |
|---|---|---|
| Slide | 1215 × 810 (3:2, 16.875 × 11.25 in) | 1620 × 1080 |
| Side margin | 78 | 104 |
| Top margin | 72 | 96 |
| Content width | 1059 (x 78 to 1137) | 1412 |
| Safe bottom (nothing but the logo below) | 724 | 965 |
| Columns | 12 × 66.25, gutter 24 | 12 × 88.3, gutter 32 |
| 2-up / 3-up / 4-up / 6-up widths | 517.5 / 337 / 246.75 / 156.5 | 690 / 449.3 / 329 / 208.7 |

- Text starts at x 78 and ends by x 1137. Text inside a colour panel or card keeps 48 pt padding.
- Photos either bleed to a slide edge or sit on the grid. Nothing floats at a random spot.
- One exception: the photo-on-top layout (D17) starts its photo 18 pt from the top so the text band fits.

## 2. Colours

| Name | Hex | Use |
|---|---|---|
| cream | #F7F2EA | default background; text on dark |
| paper | #F1E8DB | tinted panel, empty image placeholder |
| sand | #E2D8C8 | 1 pt hairlines on light backgrounds |
| olive | #444C3B | dark background (concept, statement, numbers, closing) |
| wine | #5E1F28 | second dark background (the "burgundy" background) |
| ink | #2B2520 | titles on light |
| body | #6A6055 | body text, bullets, labels on light |
| accent | #8E2B39 | italic accent, kicker, meta values on light. **Text only, never a background.** Per project (template K08 used #A24E2C). |
| rose | #E4C3AE | italic accent, kicker and labels on dark |
| gold | #A98A5E | kicker mark, photo numbers, short rules, outlines |
| night | #14100C | photo scrim only, with transparency |

**Backgrounds allowed:** cream, olive, wine, or a photo. **Not allowed:** black #1C1917, the accent #8E2B39 as a
background, white, client or neon colours.

| Role | on light (cream) | on dark (olive, wine, photo) |
|---|---|---|
| title | ink | cream |
| italic accent | accent | rose |
| kicker label | accent | rose |
| body, bullets | body | cream |
| small labels | body | rose |
| hairline | sand | cream at 25 % |
| logo | dark | white |

## 3. Type

Fonts: **Cormorant Garamond** (titles, names) and **Hanken Grotesk** (body, labels, numbers). Only these two: no third font anywhere.
Always lining figures (`font-variant-numeric: lining-nums`): Cormorant's default figures read as letters.

| Style | Font | Size pt | Line | Tracking pt | Use |
|---|---|---|---|---|---|
| display | serif | 111 | 0.94 | −2.78 | cover title: line 1 client or event, line 2 italic accent |
| opener | serif | 104 | 0.90 | −2.0 | section opener title |
| statement | serif | 78 | 1.08 | −1.17 | one big sentence on colour |
| h1 | serif | 66 | 1.12 | −0.79 | slide title |
| h2 | serif | 55.5 | 1.2 | −0.83 | long 3-line heading, closing line, caption over a photo, title in a band or card |
| h3 | serif | 28 | 1.15 | 0 | name under a large image, quantities |
| name | serif | 22.5 | 1.18 | 0 | captions, item names, meta values (italic, accent), contacts |
| figure | serif | 111 | 1.0 | −2.78 | key numbers |
| kicker | sans bold, caps | 13.5 | | 4.05 | label above every title |
| body | sans | 20 | 1.6 | 0 | paragraphs and bullets, about 60 characters per line |
| small | sans | 14 | 1.4 | 0 | item details, captions, text in the D17 band |
| label | sans bold, caps | 9.75 | | 2.15 | meta labels, table headers, tags |
| number | sans bold | 10.5 | | 1.26 | gold photo/item numbers 01, 02, 03 |

No other sizes. A title that does not fit gets shorter words or the next smaller style. Never an in-between size.

**Title pattern:** plain words first, the last words or the second line in italic accent: "Detailid, mis /
*kannavad õhtut.*" Sentence case. No em dash in client copy.

## 4. Kicker block

`[leaf] [KICKER]` on one line at x 78, then the title 22 pt below, then body 30 pt below the title.
- **mark:** the leaf from the DekoVägi logo (`glyph.svg`), filled gold #A98A5E, 16.5 pt tall, 9 pt before the label,
  centred on the label and raised 2.25 pt. The same leaf on every kicker, cover and section opener included.
  Decided by Meelis on 06.11.2026 from 10 options (`marks.html`). Never a text mark such as "II".
- **kicker:** one or two words, typed normally (the style makes them uppercase).

## 5. Logo

One logo per slide, at one of four fixed boxes:

| Box | x | y | w × h pt | When |
|---|---|---|---|---|
| standard | 78 | 742 | 84 × 26 | every slide, bottom left |
| standard right | 1053 | 742 | 84 × 26 | only when the bottom-left corner holds a photo or text |
| cover | 78 | 72 | 123 × 38 | cover, top left |
| closing | 78 | 703 | 113 × 35 | contact and thank-you slides |

Dark logo on light, white logo on dark backgrounds and photos. Never inside a collage cell. Centred only in one place: the cover D44, at the top of its title card (cover size, no kicker).

## 6. Bullets, hairlines, captions

- Bullets: a small round dot in the accent colour, 17 pt indent, 6 pt after each item, at most 6 items.
- Hairlines: 1 pt, sand on light (cream 25 % on dark). Full content width (1059) on covers; between list and table rows.
- Photo captions: `name` style, with a gold `number` (01, 02, 03) at the right end of the line.

## 7. Images

- **Ratios:** 3:2, 2:3, 1:1, 4:3, 3:4, 4:5, 16:9, 21:9. Each layout in the gallery states the ratio of every slot.
- **Rendered final vs separate objects:** a photo, render or collage cell fills its slot edge to edge (cover crop). A
  cut-out object sits on the background inside its box (contain), with no shadow added.
- No rounded corners, borders or shadows on photos, except where a layout defines it: a circle (D22, D43), an arch
  (D40), or a 9 pt background-colour edge on a photo that overlaps another (D20, D48, D62).
- Collage gaps: 6 pt in the background colour.
- Minimum source size: 1.5 × the slot (a full-bleed photo needs at least 1800 × 1200 px).
- Text over a photo only on a full-bleed photo with a soft fade: dark scrim on dark photos (D55), cream fade on light photos (D56, D66, D67). No boxes or bars under the text.
- No text behind an image or cut-out (no watermark numbers behind objects).

## 8. Copy

Estonian on client decks. No em dash. Neutral placeholders in templates: «Pealkiri», «aktsent.», [ Kliendi nimi ].
No real client names or logos except in the job's own deck; a client logo goes in a placeholder box.

## 9. Checking a slide

Run `python check_slides.py <slide folder>` (HTML) after any AI or person fills a layout. For each slide it checks:
- every text uses one of the styles above;
- every colour is in the palette;
- text stays inside the margins and above the safe bottom;
- no text overlaps other text, the logo or a photo (panels, cards and full-bleed photos excepted);
- there is exactly one logo, in a standard box;
- every photo uses an allowed ratio.

## 10. What the past decks got wrong (audit, 554 deviations on 161 of 205 slides)

| Mistake | Count | Unified to |
|---|---|---|
| Text size off the scale: near-duplicate titles 52.5 to 61.5 pt, Hanken 11, 11.5, 12.5, 15, 18, 22 pt | 178 | the 15 styles (h2 55.5, h1 66, label 9.75, small 14, body 20) |
| Kicker mark typed as text ("II", "III", "01", ...) | 142 | the gold logo leaf |
| Text starting at x 68 to 71 instead of 78 | 99 | 78 |
| Colour outside its role or the palette (terracotta outside its project, white and grey labels) | 62 | palette roles |
| Letter spacing off (labels 2.8 to 3.0 pt, titles −1.1 to −1.17 pt) | 55 | style tracking |
| Logo at x 1089/1090, y 749/750 or other one-off boxes | 42 | the four logo boxes |
| Black #1C1917 or ink backgrounds | 5 | olive or wine |

The full list is in `audit_decks.json` (deck, slide, what, found value).

## Decided

- Kicker mark: the gold logo leaf, raised a few px (Meelis, 06.11.2026).
- No text behind images; light photos get a cream fade, never a box (Meelis, 06.11.2026).
- Short side facts (room, guests, time) = a ruled label/value list (`facts()`), never a lone floating sentence (Meelis, 07.11.2026).
- Every client deck ends with D9 Lähenemine (standard text, includes "pildimaterjal on illustratiivne"), then D31 contact (Meelis, 07.11.2026).
- The order list (D27) is internal: it never goes into a client deck (Meelis, 07.11.2026).
- D39 is the items-with-quantities sheet for 7 to 12 items (BLRT lounge: 11).
- Key numbers (D26) are set in the accent colour (Meelis, 07.11.2026).
- Section opener: D82, the zone photo in a gold arch with its cut-out in front; D8 (cut-out alone) only when there is no photo (Meelis, 06.11.2026).
- Deck roles (Meelis, 09.11.2026): one cover first (D1, D40-D44, pick one), D9 second to last, D31 last; edge cases only when their condition applies: D8 (opener without a photo), D49 (one line), D54 (open questions, early drafts), D38 (only with an iso drawing), D32 (thank you after an event, never instead of D31); D27 internal only. Full list with a "use when" line per layout: gallery deck-rules.md and layouts.json.
- Two font families only: Cormorant Garamond and Hanken Grotesk; item numbers 01, 02, 03 in Hanken Grotesk Bold (Meelis, 07.11.2026).

## Open decisions (defaults used until Meelis decides)

1. Accent per project: burgundy #8E2B39 (default) or terracotta #A24E2C?
2. Page numbers ("02/ 10", bottom right; only the base deck has them): off by default; if used, Hanken Grotesk.
