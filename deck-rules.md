# DekoVägi presentations: instructions for an AI assistant

You are helping to make an event-decor presentation for DekoVägi. The design is finished and lives in a PowerPoint template of numbered slide layouts (D1 to D83). Your job is to choose the layouts that fit the project, write short Estonian copy for their fields and place the user's images. You never design: no new fonts, sizes, colours or positions.

The layouts with pictures: https://icyfrosty.github.io/dekovagi-slide-layouts/ (a plain website). This file is https://icyfrosty.github.io/dekovagi-slide-layouts/deck-rules.md, and the kit with the template and the helper script is https://icyfrosty.github.io/dekovagi-slide-layouts/DekoVagi-AI-kit.zip.

## How to work

1. Ask the user for what is missing: client, event, date, place; the zones or rooms in the order a guest meets them; which photo shows what; cut-out objects (transparent PNG); items and quantities.
2. Plan the deck: a list of layout numbers in the deck order below, one line each on why. Show the plan to the user first.
3. Build it.
   - If you can run Python (python-pptx and Pillow) and have the files `DekoVagi-slaidid-mall-AI.pptx` and `dv_deck.py`:
     ```python
     from dv_deck import Deck
     deck = Deck("DekoVagi-slaidid-mall-AI.pptx")
     print(deck.fields("D40"))        # the fields of a layout: number, kind, limit, example
     deck.add("D40", {0: "Kliendi nimi\n*Jõulupidu*", 11: "Sündmus", 10: "photos/hall.jpg"})
     deck.add("D6", {10: "Meeleolu", 0: "Õhtu, mida külalised *mäletavad.*"}, colour="olive")   # colour versions: cream, olive, wine
     deck.add("D55", {"background": "photos/hall.jpg", 0: "Peosaal, *õhtune valgus.*"})
     deck.add("D9"); deck.add("D31")              # the two standard closing slides keep their fixed text
     deck.save("pakkumine.pptx"); print(deck.report())
     ```
     In text, \n starts a new line and *words in single stars* become the italic accent (never use ** or other markdown). Images must be JPG or PNG. Photos are cropped to fill their field; cut-outs are fitted whole. Fields you leave out are removed. `add()` never raises for a bad value: it writes a note. Read `deck.report()`; to redo slide 3 use `deck.remove(3)` and then `deck.add(..., position=3)`. Then give the .pptx to the user.
   - If you cannot run code or have no template: return the plan and, for every slide, a list `field number: text` (and which image goes in which field), so a person can paste it into PowerPoint.
4. Tell the user that the two fonts (Cormorant Garamond DV, Hanken Grotesk) must be installed to edit the file; they are embedded for viewing.

## Rules

- Every client deck: one cover first, D9 Lähenemine second to last, D31 contact last.
- Section opener: D82 (zone photo in a gold arch with the zone's cut-out) by default; D8 only when the zone has no photo.
- Pick layouts by what the project has: count the photos, cut-outs and words for each zone and choose the layout whose slots match (the field list of each layout shows what it takes).
- Use a colour version (cream, olive, wine) to set a rhythm: mostly cream, olive or wine for openers, statements and numbers.
- Do not use the same layout twice in a row; vary photo-led and text-led slides.
- Special-case layouts only when their condition applies; internal layouts never in a client deck.
- Only the two fonts, the layout's sizes and colours; Estonian copy, no em dash; photos fill their slots in the stated ratio.

## Deck order

1. **Cover**: Exactly one cover, first slide. Layouts: D40, D41, D42, D43, D44, D1.
2. **Concept and mood**: One or two slides that set the look before any zone. Layouts: D5, D4, D45, D46, D47, D7, D48, D83, D37, D6.
3. **Zones**: For each zone (room or area) in the order a guest meets them: one opener, then one to four zone slides. Layouts: D82, D13, D14, D59, D60, D61, D62, D15, D16, D17, D20, D55, D56, D67.
4. **Tables and props**: Show the decor items with names and quantities where the offer depends on them. Layouts: D19, D63, D64, D71, D72, D74, D75, D65, D68, D80, D23, D21, D22, D24.
5. **Plan and quantities**: Optional: plan, kit or quantities when the client needs them. Layouts: D35, D34, D36, D39, D26, D11.
6. **Approach**: D9 Lähenemine, always second to last, standard text unchanged. Layouts: D9.
7. **Contact**: D31, always the last slide. Layouts: D31.

## Catalogue

Role: *always* = in every client deck; *cover: pick one* = exactly one of these opens the deck; *normal choice* = pick by content; *special case only* = only when its condition applies; *internal* = never in a client deck.

| No. | Name | Section | Role | Colours | What goes in | Use when |
|---|---|---|---|---|---|---|
| D1 | One object | Cover | cover: pick one | cream | Cut-outs: 1 transparent PNG; Text: kicker (small caps above the title), cover title, 4 × label, 4 × name or caption | Cover when one object (lamp, centrepiece) carries the event and there is no strong venue photo. |
| D40 | Arch photo | Cover | cover: pick one | cream | Photos: 2:3 arch; Text: kicker (small caps above the title), cover title, 4 × label, 4 × name or caption | Cover with a tall venue or decor photo (2:3) in a gold arch. |
| D41 | Photo with card | Cover | cover: pick one | cream | Photo: Full-bleed photo 3:2 as the slide background; Text: kicker (small caps above the title), cover title, 4 × label, 4 × name or caption | Cover with one strong landscape venue photo, full bleed, title on a cream card. |
| D42 | Three staggered photos | Cover | cover: pick one | cream | Photos: 3 × 2:3; Text: kicker (small caps above the title), cover title, 4 × label, 4 × name or caption | Cover with three tall mood photos. |
| D43 | Round photo | Cover | cover: pick one | cream | Photos: 1:1 circle; Text: kicker (small caps above the title), cover title, 4 × label, 4 × name or caption | Cover with a table or top-view photo that works as a circle. |
| D44 | Panorama band | Cover | cover: pick one | cream | Photos: 21:9; Text: cover title, name or caption | Cover with a wide panorama of the room (21:9). |
| D4 | Colour panel + collage | Concept & mood | normal choice | cream, olive, wine | Photos: 6 × collage cell; Text: kicker (small caps above the title), title, paragraph | Concept with six mood photos on a colour panel. |
| D45 | Collage left, text right | Concept & mood | normal choice | olive, wine | Photos: 5 × collage cell; Text: kicker (small caps above the title), title, paragraph | Concept: collage left, short text right. |
| D46 | Text over a photo strip | Concept & mood | normal choice | cream, olive, wine | Photos: 2 × 0.44:1, 0.83:1, 0.50:1, 0.72:1; Text: kicker (small caps above the title), title, paragraph | Concept text over a strip of five photos. |
| D47 | Mosaic round a card | Concept & mood | normal choice | cream, olive, wine | Photos: 12 × collage cell; Text: kicker (small caps above the title), title, paragraph | Concept text in a card surrounded by ten mood photos. |
| D5 | Three photos on colour | Concept & mood | normal choice | cream, olive, wine | Photos: 3 × 3:2; Text: kicker (small caps above the title), title, 6 × label, 6 × name or caption, 3 × small text | Concept with key facts (room, guests, time) and three 3:2 photos with captions. |
| D7 | Collage above a text band | Concept & mood | normal choice | cream | Photos: 8 × collage cell; Text: kicker (small caps above the title), heading, 2 × label, 2 × name or caption | Mood collage of eight photos above a title and two short captions. |
| D48 | Editorial moodboard | Concept & mood | normal choice | cream | Photos: 3 × 3:2, 2 × 2:3, 1:1; Cut-outs: 2 transparent PNGs; Text: kicker (small caps above the title), heading | Editorial moodboard: six photos, two cut-outs, palette. |
| D83 | Growing arches | Concept & mood | normal choice | cream | Photos: 3 × 2:3 arch; Cut-outs: 2 transparent PNGs; Text: kicker (small caps above the title), heading | Moodboard: three arch photos, two cut-outs, palette. |
| D37 | Moodboard with palette | Concept & mood | normal choice | cream | Photos: 3:2, 1:1; Cut-outs: 2 transparent PNGs; Text: kicker (small caps above the title), title, 5 × label | Colour story for the table decor: photos plus palette. |
| D82 | Arch opener | Openers & statements | normal choice | cream, olive, wine | Photos: 2:3 arch; Cut-outs: 1 transparent PNG; Text: kicker (small caps above the title), section title, paragraph | Default zone opener: the zone's photo in a gold arch with its cut-out in front. |
| D8 | Section opener | Openers & statements | special case only | cream, olive, wine | Cut-outs: 1 transparent PNG; Text: kicker (small caps above the title), section title, paragraph | Only when a zone has no photo, just a cut-out: section opener with one big object. |
| D6 | Statement | Openers & statements | normal choice | olive, wine | Text: kicker (small caps above the title), statement, paragraph | One big sentence on colour, between parts of the deck. |
| D9 | Approach (Lähenemine) | Openers & statements | always | cream | Text: kicker (small caps above the title), heading, 2 × paragraph | Always second to last: the standard approach text with the illustrative-images note. Do not change the text. |
| D49 | One line | Text | special case only | cream | Text: kicker (small caps above the title), title, paragraph | Only when a zone has just one line so far (the solution is still open). |
| D50 | Ruled list | Text | normal choice | cream | Text: kicker (small caps above the title), title, 4 × paragraph | Zone in words: title and three to five short points, no photo. |
| D51 | Paragraph + bullets | Text | normal choice | cream | Text: kicker (small caps above the title), title, 2 × paragraph | Zone in words: a paragraph and bullets, no photo. |
| D52 | Two columns of text | Text | normal choice | cream | Text: kicker (small caps above the title), title, paragraph | Long text up to about 200 words in two columns. |
| D53 | Three columns | Text | normal choice | cream | Text: kicker (small caps above the title), title, 3 × label, 3 × paragraph | Long list in three columns with headings. |
| D54 | Open questions | Text | special case only | cream | Text: kicker (small caps above the title), title, 4 × large name, 4 × name or caption, 4 × paragraph | Only in an early draft that needs the client's answers: open questions. |
| D11 | Timeline | Text | normal choice | cream | Photos: 2:3; Text: kicker (small caps above the title), title, 5 × paragraph, 4 × name or caption | Timeline or programme of the evening, with one photo. |
| D55 | Dark photo, light caption | Photo with caption | normal choice | cream | Photo: Full-bleed photo 3:2 as the slide background; Text: kicker (small caps above the title), heading, paragraph | One dark full-bleed photo with a short light caption. |
| D56 | Light photo, fade below | Photo with caption | normal choice | cream | Photo: Full-bleed photo 3:2 as the slide background; Text: kicker (small caps above the title), heading, paragraph | One light full-bleed photo with a caption at the bottom. |
| D67 | Light photo, fade beside | Photo with caption | normal choice | cream | Photo: Full-bleed photo 3:2 as the slide background; Text: kicker (small caps above the title), heading, paragraph | One light full-bleed photo with a caption on the left. |
| D13 | Text left, photo right | Zone: photo + text | normal choice | cream | Photos: 4:5; Text: kicker (small caps above the title), title, paragraph | Zone: text and bullets left, one 4:5 photo right. |
| D14 | Photo left, text right | Zone: photo + text | normal choice | cream | Photos: 4:3; Text: kicker (small caps above the title), title, paragraph | Zone: one 4:3 photo left, text right. |
| D59 | Half photo | Zone: photo + text | normal choice | cream | Photos: 3:4; Text: kicker (small caps above the title), title, paragraph | Zone: half-slide 3:4 photo, text right. |
| D60 | Square photo | Zone: photo + text | normal choice | cream | Photos: 1:1; Text: kicker (small caps above the title), title, paragraph | Zone: one square photo, text right. |
| D61 | Two stacked photos | Zone: photo + text | normal choice | cream | Photos: 2 × 3:2; Text: kicker (small caps above the title), title, paragraph | Zone: two 3:2 photos stacked, text right. |
| D62 | Big photo + small square | Zone: photo + text | normal choice | cream | Photos: 3:4, 1:1; Text: kicker (small caps above the title), title, paragraph | Zone: big 3:4 photo plus a small detail photo, narrow text. |
| D15 | Colour panel + photo | Zone: photo + text | normal choice | olive, wine | Photos: 4:5; Text: kicker (small caps above the title), title, paragraph | Zone: text on a colour panel with a 4:5 photo. |
| D16 | Photo + three details | Zone: photo + text | normal choice | cream | Photos: 3 × 1:1, 3:4; Text: kicker (small caps above the title), title, paragraph, 3 × label | Zone: one main photo and three small detail photos. |
| D17 | Photo on top, text band | Zone: photo + text | normal choice | cream | Photos: 16:9; Text: kicker (small caps above the title), heading, small text | Zone: one wide 16:9 photo with a text band below. |
| D20 | Two zones side by side | Zone: photo + text | normal choice | cream | Photos: 3:2, 1:1; Cut-outs: 3 transparent PNGs; Text: kicker (small caps above the title), 2 × heading, 2 × paragraph | Two table types or areas side by side, each with its own photos and props. |
| D19 | Props standing together | Props & cut-outs | normal choice | cream | Cut-outs: 6 transparent PNGs; Text: kicker (small caps above the title), title, paragraph | Text with three to five cut-out props standing together. |
| D63 | Props on a shelf line | Props & cut-outs | normal choice | cream | Cut-outs: 6 transparent PNGs; Text: kicker (small caps above the title), title, 6 × name or caption, 6 × large name | Six props on one shelf line with names and quantities. |
| D64 | Hero object on a shelf | Props & cut-outs | normal choice | cream | Cut-outs: 4 transparent PNGs; Text: kicker (small caps above the title), title, paragraph, 4 × label | One hero object and three smaller props on a shelf line. |
| D71 | Hero object + list | Props & cut-outs | normal choice | cream | Cut-outs: 4 transparent PNGs; Text: kicker (small caps above the title), title, paragraph, 4 × label, 3 × small text | One hero object with three props listed beside it. |
| D72 | Hero object on a panel | Props & cut-outs | normal choice | cream | Cut-outs: 4 transparent PNGs; Text: kicker (small caps above the title), title, paragraph, 4 × label | One hero object on a tinted panel with three props in front. |
| D74 | Hero object in an arch | Props & cut-outs | normal choice | cream | Cut-outs: 4 transparent PNGs; Text: kicker (small caps above the title), title, paragraph, 4 × label | One hero object in a tinted arch with three props in front. |
| D75 | Hero object on a circle | Props & cut-outs | normal choice | cream | Cut-outs: 4 transparent PNGs; Text: kicker (small caps above the title), title, paragraph, 4 × label | One hero object on a tinted circle with three props below (in review). |
| D65 | Photo + cut-outs | Props & cut-outs | normal choice | cream | Photos: 2:3; Cut-outs: 3 transparent PNGs; Text: kicker (small caps above the title), title, paragraph | Zone photo with three cut-outs standing over its edge. |
| D68 | Photo + five cut-outs | Props & cut-outs | normal choice | cream | Photos: 2:3; Cut-outs: 5 transparent PNGs; Text: kicker (small caps above the title), title, paragraph | Zone photo with five cut-outs standing over its edge. |
| D80 | Zigzag pairs | Props & cut-outs | normal choice | cream | Cut-outs: 3 transparent PNGs; Text: kicker (small caps above the title), 2 × heading, 2 × paragraph | Two table types, each with its own cut-outs, zigzag (in review). |
| D23 | Props grid of 12 | Props & cut-outs | normal choice | cream | Cut-outs: 12 transparent PNGs; Text: kicker (small caps above the title), title, 2 × label, 12 × small text | Twelve props in a grid, two labelled rows. |
| D21 | Three numbered photos | Details | normal choice | cream | Photos: 3 × 4:3; Text: kicker (small caps above the title), title, 3 × name or caption, 3 × item number | Three 4:3 detail photos with numbered captions. |
| D22 | Four round images | Details | normal choice | cream | Photos: 4 × 1:1 circle; Text: kicker (small caps above the title), title, 4 × large name, 4 × small text | Four round images with names (tables, options). |
| D24 | Three squares on colour | Details | normal choice | olive | Photos: 3 × 1:1; Text: kicker (small caps above the title), title, 3 × name or caption, 3 × label | Three square photos on colour with captions. |
| D35 | Top-view plan + list | Plan & order | normal choice | cream | Photos: 3:2; Cut-outs: 6 transparent PNGs; Text: kicker (small caps above the title), title, 6 × name or caption, 6 × large name | Top-view plan (3:2) with the item list. |
| D38 | Drawing with callouts | Plan & order | special case only | cream | Photos: 3:2; Text: kicker (small caps above the title), title, 6 × label, 6 × item number, 12 × small text | Only when there is an iso drawing of the table with numbered items. |
| D34 | Kit of parts | Plan & order | normal choice | cream | Cut-outs: 6 transparent PNGs; Text: kicker (small caps above the title), title, 6 × name or caption, 6 × small text, 6 × large name | Kit of six parts with names, details and quantities. |
| D36 | Detail photo + kit list | Plan & order | normal choice | cream | Photos: 3:4; Cut-outs: 6 transparent PNGs; Text: kicker (small caps above the title), title, 6 × name or caption, 6 × small text, 6 × large name | One detail photo with the kit list. |
| D39 | Order sheet | Plan & order | normal choice | cream | Cut-outs: 12 transparent PNGs; Text: kicker (small caps above the title), title, 12 × item number, 12 × name or caption, 12 × small text, 12 × large name | Items with quantities, 7 to 12 items. |
| D27 | Order table | Plan & order | internal, never for clients | cream | Table: Table, 13 rows × 5 columns; Text: kicker (small caps above the title), title | Internal order list by zone. Never in a client deck. |
| D26 | Key numbers | Plan & order | normal choice | cream, olive, wine | Text: kicker (small caps above the title), title, 6 × key number, 6 × label | Key numbers of the event (guests, tables, items). |
| D31 | Contact | Closing | always | olive | Text: kicker (small caps above the title), heading, 3 × label, 3 × name or caption | Always the last slide: DekoVägi contacts. |
| D32 | Thank you | Closing | special case only | olive | Text: cover title, large name, 3 × label, 3 × name or caption | Only as a thank-you after an event, never instead of D31. |

## Fields of every layout

The field number is what `deck.add()` takes. Colour versions of one layout have the same fields. In the examples " / " marks a line break (write it as \n in Python) and *stars* mark the italic accent.

### D1 One object
- 10: object on a transparent background (PNG), shown whole
- 11: text, max 1 line, about 63 characters per line. Example: "Sündmus"
- 0: title, max 2 lines, about 19 characters per line. Example: "Kliendi nimi / *Jõulupidu*"
- 12: text, max 1 line, about 32 characters per line. Example: "Klient"
- 13: text, max 1 line, about 29 characters per line. Example: "Kliendi nimi"
- 14: text, max 1 line, about 32 characters per line. Example: "Sündmus"
- 15: text, max 1 line, about 29 characters per line. Example: "Kasiinoõhtu"
- 16: text, max 1 line, about 32 characters per line. Example: "Kuupäev"
- 17: text, max 1 line, about 29 characters per line. Example: "12. detsember 2026"
- 18: text, max 1 line, about 32 characters per line. Example: "Koht"
- 19: text, max 1 line, about 29 characters per line. Example: "Toimumiskoht"

### D40 Arch photo
- 10: photo, ratio 2:3, cropped to fill the field
- 11: text, max 1 line, about 45 characters per line. Example: "Sündmus"
- 0: title, max 2 lines, about 13 characters per line. Example: "Kliendi nimi / *Jõulupidu*"
- 12: text, max 1 line, about 34 characters per line. Example: "Klient"
- 13: text, max 1 line, about 30 characters per line. Example: "Kliendi nimi"
- 14: text, max 1 line, about 34 characters per line. Example: "Sündmus"
- 15: text, max 1 line, about 30 characters per line. Example: "Kasiinoõhtu"
- 16: text, max 1 line, about 34 characters per line. Example: "Kuupäev"
- 17: text, max 1 line, about 30 characters per line. Example: "12. detsember 2026"
- 18: text, max 1 line, about 34 characters per line. Example: "Koht"
- 19: text, max 1 line, about 30 characters per line. Example: "Toimumiskoht"

### D41 Photo with card
- background: full-slide photo, ratio 3:2, given with the key "background"
- 10: text, max 1 line, about 53 characters per line. Example: "Sündmus"
- 0: title, max 2 lines, about 16 characters per line. Example: "Kliendi nimi / *Jõulupidu*"
- 11: text, max 1 line, about 40 characters per line. Example: "Klient"
- 12: text, max 1 line, about 36 characters per line. Example: "Kliendi nimi"
- 13: text, max 1 line, about 40 characters per line. Example: "Sündmus"
- 14: text, max 1 line, about 36 characters per line. Example: "Kasiinoõhtu"
- 15: text, max 1 line, about 40 characters per line. Example: "Kuupäev"
- 16: text, max 1 line, about 36 characters per line. Example: "12. detsember 2026"
- 17: text, max 1 line, about 40 characters per line. Example: "Koht"
- 18: text, max 1 line, about 36 characters per line. Example: "Toimumiskoht"

### D42 Three staggered photos
- 10: photo, ratio 2:3, cropped to fill the field
- 11: photo, ratio 2:3, cropped to fill the field
- 12: photo, ratio 2:3, cropped to fill the field
- 13: text, max 1 line, about 50 characters per line. Example: "Sündmus"
- 0: title, max 2 lines, about 15 characters per line. Example: "Kliendi nimi / *Jõulupidu*"
- 14: text, max 1 line, about 32 characters per line. Example: "Klient"
- 15: text, max 1 line, about 29 characters per line. Example: "Kliendi nimi"
- 16: text, max 1 line, about 32 characters per line. Example: "Sündmus"
- 17: text, max 1 line, about 29 characters per line. Example: "Kasiinoõhtu"
- 18: text, max 1 line, about 32 characters per line. Example: "Kuupäev"
- 19: text, max 1 line, about 29 characters per line. Example: "12. detsember 2026"
- 20: text, max 1 line, about 32 characters per line. Example: "Koht"
- 21: text, max 1 line, about 29 characters per line. Example: "Toimumiskoht"

### D43 Round photo
- 10: photo, ratio 1:1, cropped to fill the field
- 11: text, max 1 line, about 48 characters per line. Example: "Sündmus"
- 0: title, max 2 lines, about 14 characters per line. Example: "Kliendi nimi / *Jõulupidu*"
- 12: text, max 1 line, about 30 characters per line. Example: "Klient"
- 13: text, max 1 line, about 27 characters per line. Example: "Kliendi nimi"
- 14: text, max 1 line, about 30 characters per line. Example: "Sündmus"
- 15: text, max 1 line, about 27 characters per line. Example: "Kasiinoõhtu"
- 16: text, max 1 line, about 30 characters per line. Example: "Kuupäev"
- 17: text, max 1 line, about 27 characters per line. Example: "12. detsember 2026"
- 18: text, max 1 line, about 30 characters per line. Example: "Koht"
- 19: text, max 1 line, about 27 characters per line. Example: "Toimumiskoht"

### D44 Panorama band
- 10: photo, ratio 21:9, cropped to fill the field
- 0: title, max 2 lines, about 19 characters per line. Example: "Kliendi nimi / *Jõulupidu*"
- 11: text, max 1 line, about 124 characters per line. Example: "Kasiinoõhtu · 12. detsember 2026 · Toimumiskoht"

### D4 Colour panel + collage
- 10: text, max 1 line, about 41 characters per line. Example: "Kontseptsioon"
- 0: title, max 2 lines, about 20 characters per line. Example: "Tere tulemast / *kasiinosaali.*"
- 11: text, max 2 lines, about 56 characters per line. Example: "Punane samet, kuld ja küünlavalgus toovad saali 1920. aastate kasii..."
- 12: photo, any ratio (collage cell), cropped to fill the field
- 13: photo, any ratio (collage cell), cropped to fill the field
- 14: photo, any ratio (collage cell), cropped to fill the field
- 15: photo, any ratio (collage cell), cropped to fill the field
- 16: photo, any ratio (collage cell), cropped to fill the field
- 17: photo, any ratio (collage cell), cropped to fill the field

### D45 Collage left, text right
- 10: photo, any ratio (collage cell), cropped to fill the field
- 11: photo, any ratio (collage cell), cropped to fill the field
- 12: photo, any ratio (collage cell), cropped to fill the field
- 13: photo, any ratio (collage cell), cropped to fill the field
- 14: photo, any ratio (collage cell), cropped to fill the field
- 15: text, max 1 line, about 42 characters per line. Example: "Kontseptsioon"
- 0: title, max 2 lines, about 21 characters per line. Example: "Tere tulemast / *kasiinosaali.*"
- 16: text, max 2 lines, about 56 characters per line. Example: "Punane samet, kuld ja küünlavalgus toovad saali 1920. aastate kasii..."

### D46 Text over a photo strip
- 10: text, max 1 line, about 47 characters per line. Example: "Kontseptsioon"
- 0: title, max 2 lines, about 23 characters per line. Example: "Tere tulemast / *kasiinosaali.*"
- 11: text, max 2 lines, about 56 characters per line. Example: "Punane samet, kuld ja küünlavalgus toovad saali 1920. aastate kasii..."
- 12: photo, any ratio (collage cell), cropped to fill the field
- 13: photo, any ratio (collage cell), cropped to fill the field
- 14: photo, any ratio (collage cell), cropped to fill the field
- 15: photo, any ratio (collage cell), cropped to fill the field
- 16: photo, any ratio (collage cell), cropped to fill the field

### D47 Mosaic round a card
- 10: photo, any ratio (collage cell), cropped to fill the field
- 11: photo, any ratio (collage cell), cropped to fill the field
- 12: photo, any ratio (collage cell), cropped to fill the field
- 13: photo, any ratio (collage cell), cropped to fill the field
- 14: photo, any ratio (collage cell), cropped to fill the field
- 15: photo, any ratio (collage cell), cropped to fill the field
- 16: photo, any ratio (collage cell), cropped to fill the field
- 17: photo, any ratio (collage cell), cropped to fill the field
- 18: photo, any ratio (collage cell), cropped to fill the field
- 19: photo, any ratio (collage cell), cropped to fill the field
- 20: photo, any ratio (collage cell), cropped to fill the field
- 21: photo, any ratio (collage cell), cropped to fill the field
- 22: text, max 1 line, about 14 characters per line. Example: "Kontseptsioon"
- 0: title, max 2 lines, about 22 characters per line. Example: "Tere tulemast / *kasiinosaali.*"
- 23: text, max 2 lines, about 57 characters per line. Example: "Punane samet, kuld ja küünlavalgus toovad saali 1920. aastate kasii..."

### D5 Three photos on colour
- 10: text, max 1 line, about 51 characters per line. Example: "Kontseptsioon"
- 0: title, max 2 lines, about 25 characters per line. Example: "Üks saal, / *kolm meeleolu.*"
- 11: text, max 1 line, about 19 characters per line. Example: "Saal"
- 12: text, max 1 line, about 21 characters per line. Example: "Peosaal"
- 13: text, max 1 line, about 23 characters per line. Example: "Külalisi"
- 14: text, max 1 line, about 18 characters per line. Example: "120"
- 15: text, max 1 line, about 14 characters per line. Example: "Aeg"
- 16: text, max 1 line, about 26 characters per line. Example: "19.00 kuni 01.00"
- 17: photo, ratio 3:2, cropped to fill the field
- 18: text, max 1 line, about 39 characters per line. Example: "19.00"
- 19: text, max 1 line, about 44 characters per line. Example: "Vastuvõtt"
- 20: text, max 1 line, about 51 characters per line. Example: "Šampanja ja kaardid"
- 21: photo, ratio 3:2, cropped to fill the field
- 22: text, max 1 line, about 39 characters per line. Example: "20.30"
- 23: text, max 1 line, about 44 characters per line. Example: "Õhtusöök"
- 24: text, max 1 line, about 51 characters per line. Example: "Lambid ja küünlad"
- 25: photo, ratio 3:2, cropped to fill the field
- 26: text, max 1 line, about 39 characters per line. Example: "23.00"
- 27: text, max 1 line, about 44 characters per line. Example: "Pidu"
- 28: text, max 1 line, about 51 characters per line. Example: "Rulett ja tants"

### D7 Collage above a text band
- 10: photo, any ratio (collage cell), cropped to fill the field
- 11: photo, any ratio (collage cell), cropped to fill the field
- 12: photo, any ratio (collage cell), cropped to fill the field
- 13: photo, any ratio (collage cell), cropped to fill the field
- 14: photo, any ratio (collage cell), cropped to fill the field
- 15: photo, any ratio (collage cell), cropped to fill the field
- 16: photo, any ratio (collage cell), cropped to fill the field
- 17: photo, any ratio (collage cell), cropped to fill the field
- 18: text, max 1 line, about 36 characters per line. Example: "Detailid"
- 0: title, max 1 line, about 20 characters per line. Example: "Detailid"
- 19: text, max 1 line, about 40 characters per line. Example: "Materjalid"
- 20: text, max 2 lines, about 36 characters per line. Example: "Punane samet, kuldsed detailid ja mustad suled."
- 21: text, max 1 line, about 40 characters per line. Example: "Valgus"
- 22: text, max 2 lines, about 36 characters per line. Example: "Küünlad kuldsetel alustel, roosid kristallvaasides."

### D48 Editorial moodboard
- 10: photo, ratio 3:2, cropped to fill the field
- 11: photo, ratio 3:2, cropped to fill the field
- 12: photo, ratio 2:3, cropped to fill the field
- 13: photo, ratio 1:1, cropped to fill the field
- 14: photo, ratio 3:2, cropped to fill the field
- 15: photo, ratio 2:3, cropped to fill the field
- 16: object on a transparent background (PNG), shown whole
- 17: object on a transparent background (PNG), shown whole
- 18: text, max 1 line, about 36 characters per line. Example: "Meeleolu"
- 0: title, max 2 lines, about 19 characters per line. Example: "Punane samet, / *kuld ja valgus.*"

### D83 Growing arches
- 10: photo, ratio 2:3, cropped to fill the field
- 11: photo, ratio 2:3, cropped to fill the field
- 12: photo, ratio 2:3, cropped to fill the field
- 13: object on a transparent background (PNG), shown whole
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 36 characters per line. Example: "Meeleolu"
- 0: title, max 2 lines, about 17 characters per line. Example: "Punane samet, / *kuld ja valgus.*"

### D37 Moodboard with palette
- 10: text, max 1 line, about 89 characters per line. Example: "Meeleolu"
- 0: title, max 1 line, about 43 characters per line. Example: "Kasiinolaud, *punane ja kuld.*"
- 11: photo, ratio 3:2, cropped to fill the field
- 12: photo, ratio 1:1, cropped to fill the field
- 13: object on a transparent background (PNG), shown whole
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 11 characters per line. Example: "Veinipunane"
- 16: text, max 1 line, about 12 characters per line. Example: "Lambipunane"
- 17: text, max 1 line, about 4 characters per line. Example: "Kuld"
- 18: text, max 1 line, about 5 characters per line. Example: "Must"
- 19: text, max 1 line, about 6 characters per line. Example: "Kreem"

### D82 Arch opener
- 10: photo, ratio 2:3, cropped to fill the field
- 11: text, max 1 line, about 38 characters per line. Example: "12. detsember · Saal"
- 0: title, max 2 lines, about 12 characters per line. Example: "Mängu / *saal.*"
- 12: text, max 1 line, about 38 characters per line. Example: "Saal muutub üheks õhtuks kasiinoks."
- 13: object on a transparent background (PNG), shown whole

### D8 Section opener
- 10: text, max 1 line, about 51 characters per line. Example: "12. detsember · Saal"
- 0: title, max 2 lines, about 16 characters per line. Example: "Mängu / *saal.*"
- 11: text, max 1 line, about 49 characters per line. Example: "Saal muutub üheks õhtuks kasiinoks."
- 12: object on a transparent background (PNG), shown whole

### D6 Statement
- 10: text, max 1 line, about 75 characters per line. Example: "Kontseptsioon"
- 0: title, max 2 lines, about 31 characters per line. Example: "Õhkkond, mida külalised / *mäletavad.*"
- 11: text, max 2 lines, about 61 characters per line. Example: "Iga sündmus on üks õhtu kellegi elust. Meie loome ruumi, mida mälet..."

### D9 Approach (Lähenemine)
- 10: text, max 1 line, about 36 characters per line. Example: "Lähenemine"
- 0: title, max 4 lines, about 28 characters per line. Example: "Iga sündmus on eriline ja loodud kliendile lähtudes tema *individua..."
- 11: text, max 4 lines, about 58 characters per line. Example: "Teie pidu ei sarnane ühegi teise peo dekoratsioonidele. Kasutatav p..."
- 12: text, max 1 line, about 58 characters per line. Example: "Aitäh, et usaldate meid looma oma erilisi hetki!"

### D49 One line
- 10: text, max 1 line, about 75 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 37 characters per line. Example: "Garderoob / *Lahendus täpsustamisel.*"
- 11: text, max 1 line, about 72 characters per line. Example: "Lahendus valmib pärast ruumi ülevaatust 20. novembril."

### D50 Ruled list
- 10: text, max 1 line, about 37 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 18 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 1 line, about 55 characters per line. Example: "Kuldsed postid punase nööriga"
- 12: text, max 1 line, about 55 characters per line. Example: "Suur peegel tervitusega"
- 13: text, max 1 line, about 55 characters per line. Example: "Küünlad klaaskuplites"
- 14: text, max 1 line, about 55 characters per line. Example: "Tervitaja garderoobi kõrval"

### D51 Paragraph + bullets
- 10: text, max 1 line, about 63 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 31 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 2 lines, about 55 characters per line. Example: "Külaline astub sisse punasele vaibale. Kuldsed postid juhivad ta pe..."
- 12: text, max 5 lines, about 55 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."

### D52 Two columns of text
- 10: text, max 1 line, about 75 characters per line. Example: "Ruum"
- 0: title, max 1 line, about 37 characters per line. Example: "Sissepääs ja *fuajee*"
- 11: text, max 12 lines, about 56 characters per line. Example: "Sissepääs on esimene koht, kus külaline õhtuga kohtub. Seepärast al..."

### D53 Three columns
- 10: text, max 1 line, about 75 characters per line. Example: "Ruumid"
- 0: title, max 1 line, about 37 characters per line. Example: "Kõik ruumid *ühel lehel*"
- 11: text, max 1 line, about 44 characters per line. Example: "Sissepääs"
- 12: text, max 5 lines, about 36 characters per line. Example: "Punane vaip 12 m / Kuldsed postid, 8 tk / Peegel tervitusega / Küün..."
- 13: text, max 1 line, about 44 characters per line. Example: "Fuajee"
- 14: text, max 5 lines, about 36 characters per line. Example: "Kaks kaardilauda / Šampanjabaar / Kõrged lauad, 6 tk / Punased lambid"
- 15: text, max 1 line, about 44 characters per line. Example: "Saal"
- 16: text, max 5 lines, about 36 characters per line. Example: "Kasiinolauad, 12 tk / Laualambid, 36 tk / Sulgedega vaasid, 48 / Ru..."

### D54 Open questions
- 10: text, max 1 line, about 36 characters per line. Example: "Täpsustamisel"
- 0: title, max 2 lines, about 17 characters per line. Example: "Lahtised / *küsimused*"
- 11: text, max 2 lines, about 6 characters per line. Example: "01"
- 12: text, max 1 line, about 31 characters per line. Example: "Laudade arv"
- 13: text, max 1 line, about 31 characters per line. Example: "Kinnitame külaliste arvu järgi."
- 14: text, max 2 lines, about 6 characters per line. Example: "02"
- 15: text, max 1 line, about 30 characters per line. Example: "Ruletilaud"
- 16: text, max 1 line, about 31 characters per line. Example: "Rendist või kliendi partnerilt?"
- 17: text, max 2 lines, about 6 characters per line. Example: "03"
- 18: text, max 1 line, about 25 characters per line. Example: "Lilled"
- 19: text, max 1 line, about 24 characters per line. Example: "Roosid või ainult suled?"
- 20: text, max 2 lines, about 6 characters per line. Example: "04"
- 21: text, max 1 line, about 32 characters per line. Example: "Paigaldusaeg"
- 22: text, max 1 line, about 31 characters per line. Example: "Saal on vaba alates kella 9.00."

### D11 Timeline
- 10: photo, ratio 2:3, cropped to fill the field
- 11: text, max 1 line, about 43 characters per line. Example: "Teostus"
- 0: title, max 1 line, about 21 characters per line. Example: "Ajakava ja *teostus.*"
- 12: text, max 1 line, about 55 characters per line. Example: "Kõik valmib ette, paigaldus on kiire."
- 13: text, max 1 line, about 11 characters per line. Example: "20.11"
- 14: text, max 1 line, about 44 characters per line. Example: "Ülevaatus ja proovilaud"
- 15: text, max 1 line, about 11 characters per line. Example: "01.12"
- 16: text, max 1 line, about 44 characters per line. Example: "Kinnitus ja tellimus"
- 17: text, max 1 line, about 11 characters per line. Example: "12.12"
- 18: text, max 1 line, about 44 characters per line. Example: "Paigaldus 9.00 kuni 15.00"
- 19: text, max 1 line, about 11 characters per line. Example: "13.12"
- 20: text, max 1 line, about 44 characters per line. Example: "Mahavõtt"

### D55 Dark photo, light caption
- background: full-slide photo, ratio 3:2, given with the key "background"
- 10: text, max 1 line, about 63 characters per line. Example: "Toimumiskoht"
- 0: title, max 1 line, about 37 characters per line. Example: "Peosaal, *õhtune valgus.*"
- 11: text, max 1 line, about 80 characters per line. Example: "Kõrged laed ja soe valgus, 12 lauda ja tantsupõrand."

### D56 Light photo, fade below
- background: full-slide photo, ratio 3:2, given with the key "background"
- 10: text, max 1 line, about 63 characters per line. Example: "Toimumiskoht"
- 0: title, max 1 line, about 37 characters per line. Example: "Peosaal, *päevavalgus.*"
- 11: text, max 1 line, about 80 characters per line. Example: "Kõrged laed ja soe valgus, 12 lauda ja tantsupõrand."

### D67 Light photo, fade beside
- background: full-slide photo, ratio 3:2, given with the key "background"
- 10: text, max 1 line, about 38 characters per line. Example: "Toimumiskoht"
- 0: title, max 2 lines, about 23 characters per line. Example: "Peosaal, / *päevavalgus.*"
- 11: text, max 2 lines, about 49 characters per line. Example: "Kõrged laed ja soe valgus, 12 lauda ja tantsupõrand."

### D13 Text left, photo right
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 17 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 45 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: photo, ratio 4:5, cropped to fill the field

### D14 Photo left, text right
- 10: photo, ratio 4:3, cropped to fill the field
- 11: text, max 1 line, about 31 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 12: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."

### D59 Half photo
- 10: photo, ratio 3:4, cropped to fill the field
- 11: text, max 1 line, about 37 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 18 characters per line. Example: "Sissepääs / *Punane vaip*"
- 12: text, max 3 lines, about 48 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."

### D60 Square photo
- 10: photo, ratio 1:1, cropped to fill the field
- 11: text, max 1 line, about 27 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 13 characters per line. Example: "Sissepääs / *Punane vaip*"
- 12: text, max 3 lines, about 35 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."

### D61 Two stacked photos
- 10: photo, ratio 3:2, cropped to fill the field
- 11: photo, ratio 3:2, cropped to fill the field
- 12: text, max 1 line, about 44 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 22 characters per line. Example: "Sissepääs / *Punane vaip*"
- 13: text, max 3 lines, about 56 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."

### D62 Big photo + small square
- 10: photo, ratio 3:4, cropped to fill the field
- 11: photo, ratio 1:1, cropped to fill the field
- 12: text, max 1 line, about 25 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 13 characters per line. Example: "Sissepääs / *Punane vaip*"
- 13: text, max 3 lines, about 33 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."

### D15 Colour panel + photo
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 17 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 45 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: photo, ratio 4:5, cropped to fill the field

### D16 Photo + three details
- 10: text, max 1 line, about 39 characters per line. Example: "Detailid"
- 0: title, max 1 line, about 19 characters per line. Example: "Laua *deko*"
- 11: text, max 3 lines, about 51 characters per line. Example: "Must laudlina põrandani / Punased servjetid / Lambid ja sulgedega v..."
- 12: photo, ratio 1:1, cropped to fill the field
- 13: text, max 1 line, about 19 characters per line. Example: "Seade 1"
- 14: photo, ratio 1:1, cropped to fill the field
- 15: text, max 1 line, about 19 characters per line. Example: "Seade 2"
- 16: photo, ratio 1:1, cropped to fill the field
- 17: text, max 1 line, about 19 characters per line. Example: "Seade 3"
- 18: photo, ratio 3:4, cropped to fill the field

### D17 Photo on top, text band
- 10: photo, ratio 16:9, cropped to fill the field
- 11: text, max 1 line, about 37 characters per line. Example: "Lauad"
- 0: title, max 1 line, about 22 characters per line. Example: "Kasiinolaud"
- 12: text, max 4 lines, about 69 characters per line. Example: "10 kohta, must laudlina põrandani / Keskel lambid, vaasid ja kaardi..."

### D20 Two zones side by side
- 10: text, max 1 line, about 36 characters per line. Example: "Lauad"
- 0: title, max 1 line, about 20 characters per line. Example: "Pukklaua *deko*"
- 11: text, max 1 line, about 45 characters per line. Example: "Pikad lauad keset saali."
- 12: text, max 2 lines, about 20 characters per line. Example: "Ümmarguse *laua deko*"
- 13: text, max 1 line, about 45 characters per line. Example: "Ümarad lauad seina ääres."
- 14: photo, ratio 3:2, cropped to fill the field
- 15: photo, ratio 1:1, cropped to fill the field
- 16: object on a transparent background (PNG), shown whole
- 17: object on a transparent background (PNG), shown whole
- 18: object on a transparent background (PNG), shown whole

### D19 Props standing together
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: object on a transparent background (PNG), shown whole
- 13: object on a transparent background (PNG), shown whole
- 14: object on a transparent background (PNG), shown whole
- 15: object on a transparent background (PNG), shown whole
- 16: object on a transparent background (PNG), shown whole
- 17: object on a transparent background (PNG), shown whole

### D63 Props on a shelf line
- 10: text, max 1 line, about 47 characters per line. Example: "Rekvisiidid"
- 0: title, max 1 line, about 23 characters per line. Example: "Laual *kuus eset*"
- 11: object on a transparent background (PNG), shown whole
- 12: text, max 1 line, about 18 characters per line. Example: "Punane laualamp"
- 13: text, max 1 line, about 15 characters per line. Example: "3 tk"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 18 characters per line. Example: "Sulgedega vaas"
- 16: text, max 1 line, about 15 characters per line. Example: "4 tk"
- 17: object on a transparent background (PNG), shown whole
- 18: text, max 1 line, about 18 characters per line. Example: "Kaardihoidja"
- 19: text, max 1 line, about 15 characters per line. Example: "4 tk"
- 20: object on a transparent background (PNG), shown whole
- 21: text, max 1 line, about 18 characters per line. Example: "Punane servjett"
- 22: text, max 1 line, about 15 characters per line. Example: "10 tk"
- 23: object on a transparent background (PNG), shown whole
- 24: text, max 2 lines, about 18 characters per line. Example: "Kuldne kahvel ja nuga"
- 25: text, max 1 line, about 15 characters per line. Example: "10 kmpl"
- 26: object on a transparent background (PNG), shown whole
- 27: text, max 1 line, about 18 characters per line. Example: "Must laudlina"
- 28: text, max 1 line, about 15 characters per line. Example: "1 tk"

### D64 Hero object on a shelf
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 26 characters per line. Example: "Sulgedega vaas"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 30 characters per line. Example: "Punane laualamp"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 20 characters per line. Example: "Kaardihoidja"
- 18: object on a transparent background (PNG), shown whole
- 19: text, max 1 line, about 17 characters per line. Example: "Šampanjapokaal"

### D71 Hero object + list
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 37 characters per line. Example: "Punane laualamp"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 25 characters per line. Example: "Sulgedega vaas"
- 16: text, max 1 line, about 29 characters per line. Example: "klaasvaas, mustad suled"
- 17: object on a transparent background (PNG), shown whole
- 18: text, max 1 line, about 25 characters per line. Example: "Kaardihoidja"
- 19: text, max 1 line, about 29 characters per line. Example: "must teemant, neli kaarti"
- 20: object on a transparent background (PNG), shown whole
- 21: text, max 1 line, about 25 characters per line. Example: "Šampanjapokaal"
- 22: text, max 1 line, about 29 characters per line. Example: "kristall, madal kauss"

### D72 Hero object on a panel
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 35 characters per line. Example: "Punane laualamp"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 24 characters per line. Example: "Sulgedega vaas"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 19 characters per line. Example: "Kaardihoidja"
- 18: object on a transparent background (PNG), shown whole
- 19: text, max 1 line, about 16 characters per line. Example: "Šampanjapokaal"

### D74 Hero object in an arch
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 35 characters per line. Example: "Punane laualamp"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 24 characters per line. Example: "Sulgedega vaas"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 19 characters per line. Example: "Kaardihoidja"
- 18: object on a transparent background (PNG), shown whole
- 19: text, max 1 line, about 16 characters per line. Example: "Šampanjapokaal"

### D75 Hero object on a circle
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 35 characters per line. Example: "Punane laualamp"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 24 characters per line. Example: "Sulgedega vaas"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 19 characters per line. Example: "Kaardihoidja"
- 18: object on a transparent background (PNG), shown whole
- 19: text, max 1 line, about 16 characters per line. Example: "Šampanjapokaal"

### D65 Photo + cut-outs
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: photo, ratio 2:3, cropped to fill the field
- 13: object on a transparent background (PNG), shown whole
- 14: object on a transparent background (PNG), shown whole
- 15: object on a transparent background (PNG), shown whole

### D68 Photo + five cut-outs
- 10: text, max 1 line, about 36 characters per line. Example: "Ruum"
- 0: title, max 2 lines, about 16 characters per line. Example: "Sissepääs / *Punane vaip*"
- 11: text, max 3 lines, about 41 characters per line. Example: "Kuldsed postid punase nööriga / Suur peegel tervitusega / Küünlad k..."
- 12: photo, ratio 2:3, cropped to fill the field
- 13: object on a transparent background (PNG), shown whole
- 14: object on a transparent background (PNG), shown whole
- 15: object on a transparent background (PNG), shown whole
- 16: object on a transparent background (PNG), shown whole
- 17: object on a transparent background (PNG), shown whole

### D80 Zigzag pairs
- 10: text, max 1 line, about 36 characters per line. Example: "Lauad"
- 0: title, max 1 line, about 20 characters per line. Example: "Pukklaua *deko*"
- 11: text, max 1 line, about 45 characters per line. Example: "Pikad lauad keset saali."
- 12: object on a transparent background (PNG), shown whole
- 13: object on a transparent background (PNG), shown whole
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 2 lines, about 22 characters per line. Example: "Ümmarguse *laua deko*"
- 16: text, max 1 line, about 48 characters per line. Example: "Ümarad lauad seina ääres."

### D23 Props grid of 12
- 10: text, max 1 line, about 82 characters per line. Example: "Rekvisiidid"
- 0: title, max 1 line, about 40 characters per line. Example: "Rekvisiidid, *mis loovad meeleolu.*"
- 11: text, max 1 line, about 39 characters per line. Example: "Laual"
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 24 characters per line. Example: "Punane laualamp"
- 14: object on a transparent background (PNG), shown whole
- 15: text, max 1 line, about 24 characters per line. Example: "Sulgedega vaas"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 24 characters per line. Example: "Kaardihoidja"
- 18: object on a transparent background (PNG), shown whole
- 19: text, max 1 line, about 24 characters per line. Example: "Punane servjett"
- 20: object on a transparent background (PNG), shown whole
- 21: text, max 1 line, about 24 characters per line. Example: "Kuldne kahvel ja nuga"
- 22: object on a transparent background (PNG), shown whole
- 23: text, max 1 line, about 24 characters per line. Example: "Must laudlina"
- 24: text, max 1 line, about 39 characters per line. Example: "Kasiino"
- 25: object on a transparent background (PNG), shown whole
- 26: text, max 1 line, about 24 characters per line. Example: "Küünal kuldsel alusel"
- 27: object on a transparent background (PNG), shown whole
- 28: text, max 1 line, about 24 characters per line. Example: "Žetoonid"
- 29: object on a transparent background (PNG), shown whole
- 30: text, max 1 line, about 24 characters per line. Example: "Menüükaart alusel"
- 31: object on a transparent background (PNG), shown whole
- 32: text, max 1 line, about 24 characters per line. Example: "Šampanjapokaal"
- 33: object on a transparent background (PNG), shown whole
- 34: text, max 1 line, about 24 characters per line. Example: "Roos pungavaasis"
- 35: object on a transparent background (PNG), shown whole
- 36: text, max 1 line, about 24 characters per line. Example: "Kuldne alustaldrik"

### D21 Three numbered photos
- 10: text, max 1 line, about 56 characters per line. Example: "Detailid"
- 0: title, max 2 lines, about 27 characters per line. Example: "Detailid, mis *kannavad õhtut.*"
- 11: photo, ratio 4:3, cropped to fill the field
- 12: text, max 1 line, about 25 characters per line. Example: "Lamp ja suled"
- 13: text, max 1 line, about 18 characters per line. Example: "01"
- 14: photo, ratio 4:3, cropped to fill the field
- 15: text, max 1 line, about 25 characters per line. Example: "Mustad suled"
- 16: text, max 1 line, about 18 characters per line. Example: "02"
- 17: photo, ratio 4:3, cropped to fill the field
- 18: text, max 1 line, about 28 characters per line. Example: "Kaardid ja žetoonid"
- 19: text, max 1 line, about 14 characters per line. Example: "03"

### D22 Four round images
- 10: text, max 1 line, about 75 characters per line. Example: "Lauad · 12.12"
- 0: title, max 1 line, about 37 characters per line. Example: "Neli lauda, *neli lugu.*"
- 11: photo, ratio 1:1, cropped to fill the field
- 12: text, max 1 line, about 23 characters per line. Example: "Kasiinolaud"
- 13: text, max 1 line, about 38 characters per line. Example: "Lambid, suled, kaardid"
- 14: photo, ratio 1:1, cropped to fill the field
- 15: text, max 1 line, about 23 characters per line. Example: "Pokkerilaud"
- 16: text, max 1 line, about 38 characters per line. Example: "Žetoonid ja kaardid"
- 17: photo, ratio 1:1, cropped to fill the field
- 18: text, max 1 line, about 23 characters per line. Example: "Ruletilaud"
- 19: text, max 1 line, about 38 characters per line. Example: "Õhtu lõpuks"
- 20: photo, ratio 1:1, cropped to fill the field
- 21: text, max 1 line, about 23 characters per line. Example: "Šampanjalaud"
- 22: text, max 1 line, about 38 characters per line. Example: "Pokaalitorn"

### D24 Three squares on colour
- 10: text, max 1 line, about 75 characters per line. Example: "Meeleolu"
- 0: title, max 1 line, about 37 characters per line. Example: "Üks laud, *kolm meeleolu.*"
- 11: photo, ratio 1:1, cropped to fill the field
- 12: text, max 1 line, about 39 characters per line. Example: "19.00"
- 13: text, max 1 line, about 44 characters per line. Example: "Vastuvõtt"
- 14: photo, ratio 1:1, cropped to fill the field
- 15: text, max 1 line, about 39 characters per line. Example: "20.30"
- 16: text, max 1 line, about 44 characters per line. Example: "Õhtusöök"
- 17: photo, ratio 1:1, cropped to fill the field
- 18: text, max 1 line, about 39 characters per line. Example: "23.00"
- 19: text, max 1 line, about 44 characters per line. Example: "Pidu"

### D35 Top-view plan + list
- 10: text, max 1 line, about 50 characters per line. Example: "Lauadekor"
- 0: title, max 1 line, about 24 characters per line. Example: "Plaan ja *esemed*"
- 11: photo, ratio 3:2, cropped to fill the field
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 28 characters per line. Example: "Punane laualamp"
- 14: text, max 1 line, about 22 characters per line. Example: "3 tk"
- 15: object on a transparent background (PNG), shown whole
- 16: text, max 1 line, about 28 characters per line. Example: "Sulgedega vaas"
- 17: text, max 1 line, about 22 characters per line. Example: "4 tk"
- 18: object on a transparent background (PNG), shown whole
- 19: text, max 1 line, about 28 characters per line. Example: "Kaardihoidja"
- 20: text, max 1 line, about 22 characters per line. Example: "4 tk"
- 21: object on a transparent background (PNG), shown whole
- 22: text, max 1 line, about 28 characters per line. Example: "Punane servjett"
- 23: text, max 1 line, about 22 characters per line. Example: "10 tk"
- 24: object on a transparent background (PNG), shown whole
- 25: text, max 1 line, about 28 characters per line. Example: "Kuldne kahvel ja nuga"
- 26: text, max 1 line, about 22 characters per line. Example: "10 kmpl"
- 27: object on a transparent background (PNG), shown whole
- 28: text, max 1 line, about 28 characters per line. Example: "Must laudlina"
- 29: text, max 1 line, about 22 characters per line. Example: "1 tk"

### D38 Drawing with callouts
- 10: text, max 1 line, about 63 characters per line. Example: "Lauadekor"
- 0: title, max 1 line, about 31 characters per line. Example: "Kasiinolaud *pealtnurgast*"
- 11: photo, ratio 3:2, cropped to fill the field
- 12: text, max 1 line, about 4 characters per line. Example: "1"
- 13: text, max 1 line, about 4 characters per line. Example: "2"
- 14: text, max 1 line, about 4 characters per line. Example: "3"
- 15: text, max 1 line, about 4 characters per line. Example: "4"
- 16: text, max 1 line, about 4 characters per line. Example: "5"
- 17: text, max 1 line, about 4 characters per line. Example: "6"
- 18: text, max 1 line, about 4 characters per line. Example: "01"
- 19: text, max 1 line, about 28 characters per line. Example: "Punane laualamp"
- 20: text, max 1 line, about 4 characters per line. Example: "3 tk"
- 21: text, max 1 line, about 4 characters per line. Example: "02"
- 22: text, max 1 line, about 28 characters per line. Example: "Sulgedega vaas"
- 23: text, max 1 line, about 4 characters per line. Example: "4 tk"
- 24: text, max 1 line, about 4 characters per line. Example: "03"
- 25: text, max 1 line, about 28 characters per line. Example: "Kaardihoidja"
- 26: text, max 1 line, about 4 characters per line. Example: "4 tk"
- 27: text, max 1 line, about 4 characters per line. Example: "04"
- 28: text, max 1 line, about 27 characters per line. Example: "Punane servjett"
- 29: text, max 1 line, about 5 characters per line. Example: "10 tk"
- 30: text, max 1 line, about 4 characters per line. Example: "05"
- 31: text, max 1 line, about 24 characters per line. Example: "Kuldne kahvel ja nuga"
- 32: text, max 1 line, about 8 characters per line. Example: "10 kmpl"
- 33: text, max 1 line, about 4 characters per line. Example: "06"
- 34: text, max 1 line, about 28 characters per line. Example: "Must laudlina"
- 35: text, max 1 line, about 4 characters per line. Example: "1 tk"

### D34 Kit of parts
- 10: text, max 1 line, about 75 characters per line. Example: "Lauadekor"
- 0: title, max 1 line, about 37 characters per line. Example: "Kasiinolaud, *kuus eset.*"
- 11: object on a transparent background (PNG), shown whole
- 12: text, max 1 line, about 35 characters per line. Example: "Punane laualamp"
- 13: text, max 1 line, about 46 characters per line. Example: "plisseeritud vari, messingjalg"
- 14: text, max 1 line, about 28 characters per line. Example: "3 tk"
- 15: object on a transparent background (PNG), shown whole
- 16: text, max 1 line, about 35 characters per line. Example: "Sulgedega vaas"
- 17: text, max 1 line, about 46 characters per line. Example: "klaasvaas, mustad suled"
- 18: text, max 1 line, about 28 characters per line. Example: "4 tk"
- 19: object on a transparent background (PNG), shown whole
- 20: text, max 1 line, about 35 characters per line. Example: "Kaardihoidja"
- 21: text, max 1 line, about 46 characters per line. Example: "must teemant, neli kaarti"
- 22: text, max 1 line, about 28 characters per line. Example: "4 tk"
- 23: object on a transparent background (PNG), shown whole
- 24: text, max 1 line, about 35 characters per line. Example: "Punane servjett"
- 25: text, max 1 line, about 46 characters per line. Example: "lipsuna, kuldne rõngas"
- 26: text, max 1 line, about 28 characters per line. Example: "10 tk"
- 27: object on a transparent background (PNG), shown whole
- 28: text, max 1 line, about 35 characters per line. Example: "Kuldne kahvel ja nuga"
- 29: text, max 1 line, about 46 characters per line. Example: "kahvel vasakul, nuga paremal"
- 30: text, max 1 line, about 28 characters per line. Example: "10 kmpl"
- 31: object on a transparent background (PNG), shown whole
- 32: text, max 1 line, about 35 characters per line. Example: "Must laudlina"
- 33: text, max 1 line, about 46 characters per line. Example: "põrandani, 3,2 × 1,0 m"
- 34: text, max 1 line, about 28 characters per line. Example: "1 tk"

### D36 Detail photo + kit list
- 10: photo, ratio 3:4, cropped to fill the field
- 11: text, max 1 line, about 37 characters per line. Example: "Lauadekor"
- 0: title, max 1 line, about 18 characters per line. Example: "Kasiinolaud"
- 12: object on a transparent background (PNG), shown whole
- 13: text, max 1 line, about 29 characters per line. Example: "Punane laualamp"
- 14: text, max 1 line, about 38 characters per line. Example: "plisseeritud vari, messingjalg"
- 15: text, max 1 line, about 10 characters per line. Example: "3 tk"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 29 characters per line. Example: "Sulgedega vaas"
- 18: text, max 1 line, about 38 characters per line. Example: "klaasvaas, mustad suled"
- 19: text, max 1 line, about 10 characters per line. Example: "4 tk"
- 20: object on a transparent background (PNG), shown whole
- 21: text, max 1 line, about 29 characters per line. Example: "Kaardihoidja"
- 22: text, max 1 line, about 38 characters per line. Example: "must teemant, neli kaarti"
- 23: text, max 1 line, about 10 characters per line. Example: "4 tk"
- 24: object on a transparent background (PNG), shown whole
- 25: text, max 1 line, about 29 characters per line. Example: "Punane servjett"
- 26: text, max 1 line, about 38 characters per line. Example: "lipsuna, kuldne rõngas"
- 27: text, max 1 line, about 10 characters per line. Example: "10 tk"
- 28: object on a transparent background (PNG), shown whole
- 29: text, max 1 line, about 29 characters per line. Example: "Kuldne kahvel ja nuga"
- 30: text, max 1 line, about 38 characters per line. Example: "kahvel vasakul, nuga paremal"
- 31: text, max 1 line, about 10 characters per line. Example: "10 kmpl"
- 32: object on a transparent background (PNG), shown whole
- 33: text, max 1 line, about 29 characters per line. Example: "Must laudlina"
- 34: text, max 1 line, about 38 characters per line. Example: "põrandani, 3,2 × 1,0 m"
- 35: text, max 1 line, about 10 characters per line. Example: "1 tk"

### D39 Order sheet
- 10: text, max 1 line, about 63 characters per line. Example: "Tellimisleht"
- 0: title, max 1 line, about 31 characters per line. Example: "Kasiinolaud, *12 eset.*"
- 11: object on a transparent background (PNG), shown whole
- 12: text, max 1 line, about 4 characters per line. Example: "01"
- 13: text, max 1 line, about 34 characters per line. Example: "Punane laualamp"
- 14: text, max 1 line, about 48 characters per line. Example: "plisseeritud vari, messingjalg"
- 15: text, max 1 line, about 10 characters per line. Example: "3 tk"
- 16: object on a transparent background (PNG), shown whole
- 17: text, max 1 line, about 4 characters per line. Example: "02"
- 18: text, max 1 line, about 34 characters per line. Example: "Sulgedega vaas"
- 19: text, max 1 line, about 48 characters per line. Example: "klaasvaas, mustad suled"
- 20: text, max 1 line, about 10 characters per line. Example: "4 tk"
- 21: object on a transparent background (PNG), shown whole
- 22: text, max 1 line, about 4 characters per line. Example: "03"
- 23: text, max 1 line, about 34 characters per line. Example: "Kaardihoidja"
- 24: text, max 1 line, about 48 characters per line. Example: "must teemant, neli kaarti"
- 25: text, max 1 line, about 10 characters per line. Example: "4 tk"
- 26: object on a transparent background (PNG), shown whole
- 27: text, max 1 line, about 4 characters per line. Example: "04"
- 28: text, max 1 line, about 34 characters per line. Example: "Punane servjett"
- 29: text, max 1 line, about 48 characters per line. Example: "lipsuna, kuldne rõngas"
- 30: text, max 1 line, about 10 characters per line. Example: "10 tk"
- 31: object on a transparent background (PNG), shown whole
- 32: text, max 1 line, about 4 characters per line. Example: "05"
- 33: text, max 1 line, about 34 characters per line. Example: "Kuldne kahvel ja nuga"
- 34: text, max 1 line, about 48 characters per line. Example: "kahvel vasakul, nuga paremal"
- 35: text, max 1 line, about 10 characters per line. Example: "10 kmpl"
- 36: object on a transparent background (PNG), shown whole
- 37: text, max 1 line, about 4 characters per line. Example: "06"
- 38: text, max 1 line, about 34 characters per line. Example: "Must laudlina"
- 39: text, max 1 line, about 48 characters per line. Example: "põrandani, 3,2 × 1,0 m"
- 40: text, max 1 line, about 10 characters per line. Example: "1 tk"
- 41: object on a transparent background (PNG), shown whole
- 42: text, max 1 line, about 4 characters per line. Example: "07"
- 43: text, max 1 line, about 34 characters per line. Example: "Küünal kuldsel alusel"
- 44: text, max 1 line, about 48 characters per line. Example: "elevandiluuvalge, messing"
- 45: text, max 1 line, about 10 characters per line. Example: "6 tk"
- 46: object on a transparent background (PNG), shown whole
- 47: text, max 1 line, about 4 characters per line. Example: "08"
- 48: text, max 1 line, about 34 characters per line. Example: "Žetoonid"
- 49: text, max 1 line, about 48 characters per line. Example: "punased, mustad ja valged"
- 50: text, max 1 line, about 10 characters per line. Example: "10 virna"
- 51: object on a transparent background (PNG), shown whole
- 52: text, max 1 line, about 4 characters per line. Example: "09"
- 53: text, max 1 line, about 34 characters per line. Example: "Menüükaart alusel"
- 54: text, max 1 line, about 48 characters per line. Example: "kreemjas, kuldne ääris"
- 55: text, max 1 line, about 10 characters per line. Example: "10 tk"
- 56: object on a transparent background (PNG), shown whole
- 57: text, max 1 line, about 4 characters per line. Example: "10"
- 58: text, max 1 line, about 34 characters per line. Example: "Šampanjapokaal"
- 59: text, max 1 line, about 48 characters per line. Example: "kristall, madal kauss"
- 60: text, max 1 line, about 10 characters per line. Example: "10 tk"
- 61: object on a transparent background (PNG), shown whole
- 62: text, max 1 line, about 4 characters per line. Example: "11"
- 63: text, max 1 line, about 34 characters per line. Example: "Roos pungavaasis"
- 64: text, max 1 line, about 48 characters per line. Example: "tumepunane, kristallvaas"
- 65: text, max 1 line, about 10 characters per line. Example: "4 tk"
- 66: object on a transparent background (PNG), shown whole
- 67: text, max 1 line, about 4 characters per line. Example: "12"
- 68: text, max 1 line, about 34 characters per line. Example: "Kuldne alustaldrik"
- 69: text, max 1 line, about 48 characters per line. Example: "helmestega äär, Ø 33 cm"
- 70: text, max 1 line, about 10 characters per line. Example: "10 tk"

### D27 Order table
- 10: text, max 1 line, about 63 characters per line. Example: "Kokkuvõte"
- 0: title, max 1 line, about 31 characters per line. Example: "Tellimisnimekiri"
- 11: table: fill it by hand in PowerPoint

### D26 Key numbers
- 10: text, max 1 line, about 75 characters per line. Example: "Numbrid"
- 0: title, max 1 line, about 37 characters per line. Example: "Üks õhtu, *kõik juba olemas.*"
- 11: text, max 1 line, about 8 characters per line. Example: "120"
- 12: text, max 1 line, about 44 characters per line. Example: "külalist"
- 13: text, max 1 line, about 8 characters per line. Example: "12"
- 14: text, max 1 line, about 44 characters per line. Example: "kasiinolauda"
- 15: text, max 1 line, about 8 characters per line. Example: "36"
- 16: text, max 1 line, about 44 characters per line. Example: "punast lampi"
- 17: text, max 1 line, about 8 characters per line. Example: "48"
- 18: text, max 1 line, about 44 characters per line. Example: "sulgedega vaasi"
- 19: text, max 1 line, about 8 characters per line. Example: "120"
- 20: text, max 1 line, about 44 characters per line. Example: "servjetti"
- 21: text, max 1 line, about 8 characters per line. Example: "6"
- 22: text, max 1 line, about 44 characters per line. Example: "tundi paigaldust"

### D31 Contact
- 10: text, max 1 line, about 89 characters per line. Example: "Räägime teie sündmusest"
- 0: title, max 1 line, about 52 characters per line. Example: "Loome koos midagi *erakordset.*"
- 11: text, max 1 line, about 33 characters per line. Example: "E-post"
- 12: text, max 1 line, about 29 characters per line. Example: "deko@dekovagi.ee"
- 13: text, max 1 line, about 33 characters per line. Example: "Telefon"
- 14: text, max 1 line, about 29 characters per line. Example: "+372 5047 759"
- 15: text, max 1 line, about 33 characters per line. Example: "Veeb"
- 16: text, max 1 line, about 29 characters per line. Example: "dekovagi.ee"

### D32 Thank you
- 0: title, max 1 line, about 26 characters per line. Example: "Aitäh!"
- 10: text, max 1 line, about 99 characters per line. Example: "Kohtume 12. detsembril."
- 11: text, max 1 line, about 33 characters per line. Example: "E-post"
- 12: text, max 1 line, about 29 characters per line. Example: "deko@dekovagi.ee"
- 13: text, max 1 line, about 33 characters per line. Example: "Telefon"
- 14: text, max 1 line, about 29 characters per line. Example: "+372 5047 759"
- 15: text, max 1 line, about 33 characters per line. Example: "Veeb"
- 16: text, max 1 line, about 29 characters per line. Example: "dekovagi.ee"

