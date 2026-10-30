# Prompt Templates

## Contents
- Assembly order
- B1 Archival collage template
- B2 Cinematic template
- B3 Still-life template
- B4 Abstract material collage template
- Palette snippets
- Layout snippets
- Seam snippets
- Through-element snippets
- Concept → object mapping
- Concept → texture (B4)
- Negative prompt
- Worked examples

## Assembly order

`[mode template] + [layout snippet] + [seam snippet, B1/B4] + [through-element snippet, B1/B4] + [subject objects or textures] + [palette snippet] + [texture line] + [text line] + [negative prompt]`

Keep the final prompt 80–160 words. Name concrete objects and materials; avoid abstract words like "innovation", "AI", "future" as visual subjects.

## B1 Archival collage template

```
Editorial paper collage illustration, archival research aesthetic. {LAYOUT}. {PANEL_1_CONTENT}. {PANEL_2_CONTENT}. {OPTIONAL_PANEL_3}. Visible paper materials: {paper types}. {SEAM}. {THROUGH_ELEMENT — if H2, use instead: "A loose hand-drawn {ink/charcoal} line crosses one panel"}. {PALETTE}. Fine film grain and subtle halftone dots unify all panels. Flat, printed, tactile, museum-catalogue mood, generous negative space, one clear focal point.
```

## B2 Cinematic template

```
Cinematic still, {SUBJECT} emerging from vast near-black space, raking warm light picks out fine surface detail, shallow depth of field, large empty dark field occupying most of the frame, subject low or off-center. {PALETTE}. Soft film grain, restrained, quiet, monumental scale for a small natural subject. No text, no labels.
```

## B3 Still-life template

```
Minimal editorial still life: a single {OBJECT} isolated on a flat {GROUND COLOR} paper background, photographed with soft even light, rich material detail. {OPTIONAL: a narrow side panel of {texture} paper}. Large negative space, object off-center, {PALETTE}. Subtle paper grain. Quiet, precise, archival.
```

## B4 Abstract material collage template

```
Abstract editorial paper collage, no photographs, no objects. {LAYOUT}. {PANEL_1_TEXTURE}. {PANEL_2_TEXTURE}. {OPTIONAL_PANEL_3_TEXTURE}. A {flat pale paper rectangle / small paper tile} overlaps the division. {SEAM}. {THROUGH_ELEMENT}. {PALETTE}. Flat printed surfaces, fine grain, tactile paper, generous negative space, calm and balanced. No photographs, no recognizable objects, no people.
```

Texture vocabulary for panels: `flat solid {color} paper`, `gray-purple marbled paper with fluid swirls`, `fine halftone dot field`, `faint ruled ledger lines`, `graph paper`, `cyanotype blue paper`, `coarse grain wash`.

## Palette snippets

- **C1:** `Palette: warm cream and buff paper, charcoal lines, a single coral (#d97757) accent field.`
- **C2:** `Palette: cream paper and pale sky blue, with one deep cyanotype blue panel as the accent.`
- **C3:** `Palette: pale yellow and tan paper, moss green (#788c5d) as the single accent.`
- **C4:** `Palette: pale pink and cream paper, charcoal black, one small saturated red disc as the only accent.`
- **C5:** `Palette: near-black, deep blue haze, a thin warm orange rim of light as the only color.`
- **C6:** `Palette: muted paper tones, charcoal, and a single desaturated {color} accent.`

## Layout snippets

- **E1:** `Two-panel composition split by an off-center vertical seam (about 60/40)`
- **E2:** `Three unequal vertical strips arranged side by side`
- **E3:** `Single subject placed off-center with large empty paper space`

## Seam snippets

Fill `{SEAM}` in the B1 or B4 template with exactly one of these. Never stack two seam types in one image.

- **G2 torn:** `Panels meet along a torn paper edge with irregular fibrous deckle, overlapping edges create depth without shadows`
- **G3 straight:** `Panels meet along a clean straight cut, crisp flat edge, no tearing, no shadow`
- **G4 strips:** `A narrow vertical strip of photographic film frames sits between the panels as the divider, clean straight edges`
- **G5 geometric:** `The photograph is cropped into a {circle / rectangular window / angular polygon} mask set into the paper ground, hard clean mask edges`
- **G6 overlap:** `Panels are separate paper sheets slightly overlapping, one sheet lying on top of the other with a thin visible paper edge, no tearing, no drop shadow`

**G1 auto** — pick by topic mood, then state the pick in the one-line summary:

| Topic mood | Pick |
|---|---|
| Precise, technical, data, security, policy | G3 straight or G5 geometric |
| Process, timeline, sequence, before/after | G4 strips or G3 straight |
| Human, emotional, history, craft, nature | G2 torn or G6 overlap |
| Exploration, vision, single focal object | G5 geometric (window / circle) |

Torn edge is one option among five, not the default. When `expect_count` is 2 under G1, use two different seam types so the user can compare.

For any seam other than G2, add `torn paper, ragged edges` to the Avoid list — "collage" alone pulls the generator toward torn edges (verified with gpt-image-2: G3 and G4 rendered cleanly with this line).

## Through-element snippets

Fill `{THROUGH_ELEMENT}` (B1 and B4). Leave it empty for H2. In B1, it replaces the template's default "A loose hand-drawn line crosses one panel" sentence — don't add both.

- **H3 discs:** `A loose row of repeated solid circular paper discs of varying sizes drifts across all panels, crossing every division; the discs are white/cream on the paper panels and turn {ACCENT} where they pass over the {photograph / accent panel}`
- **H4 tiles:** `A sequence of small rectangular paper tiles steps across all panels, overlapping each division, cream tiles with one {ACCENT} tile at the end`
- **H5 line:** `One continuous loose hand-drawn black ink line loops and wanders across the full width, passing over every panel and division`

The accent color stays the only saturated hue; repeated white/cream shapes count as neutral.

## Concept → object mapping

Use these to turn a topic into things the generator can draw:

| Concept | Objects / imagery |
|---|---|
| Security, protection | brass padlock, old key, clasp, wire mesh cage |
| Data, analysis, research | graph paper, plotted curves, specimen sheet, microscope photo |
| Growth, learning | climbing stem, seedling, ginkgo leaf, pressed flower |
| Collaboration, people | hands at work, office desk, repeating balconies |
| Balance, decisions, policy | brass balance scale, ballot box, compass rose |
| Work, tools, productivity | wrench, scissors, calculator, mallet |
| Exploration, vision | ocean horizon, sky through a rectangular window, earth curve |
| History, infrastructure | classical columns, locomotive, archival control room |
| Mind, thinking | anatomical brain engraving, sheet music, tree rings |
| Speed, motion | bird crossing panels, film strip, field of arrows |

## Concept → texture (B4)

| Concept | Textures / shapes |
|---|---|
| Conversation, listening, guidance | flat warm color block + marbled paper, one wandering line connecting them |
| Trust, care, companionship | soft pink/peach paper, overlapping pale rectangle, gentle looping line |
| Values, judgment, balance | two equal-weight panels of contrasting texture, one centered tile bridging them |
| Uncertainty, complexity | dense marbling or halftone beside a calm flat field |
| Change, transformation | texture shifts panel to panel (ruled → halftone → marbled) with a through-element tying them |

## Negative prompt

Append (or pass as negative prompt if supported):

```
Avoid: gradients, 3D render, glossy plastic, glow, neon, glassmorphism, drop shadows, UI screenshots, robots, circuit brains, glowing networks, people looking at camera, logos, watermarks, signature, corner stamp, garbled text.
```

If F1 (no text), add `No text, no letters, no numbers, no labels.`

Tested gotchas (seedream-4-5):
- Drafting diagrams, scales, and charts tend to sprout numerals — write them as `unlabeled circular drafting diagram, no numbers`.
- A small stamp/logo may appear in a corner — keep `no watermark, no signature, no corner stamp` in every prompt.

If F2, add `One short title in a small elegant serif typeface reading "{TEXT}", placed in empty space.` and switch to `google.nanobanana-pro`.

## Worked examples

**Topic: 团队协作提升效率 — A1 B1 C1 D2+D6 E1 F1 G6**

```
Editorial paper collage illustration, archival research aesthetic. Two-panel composition split by an off-center vertical seam (about 60/40). Left panel: a black-and-white archival photograph of two pairs of hands assembling a brass mechanism on a workbench. Right panel: cream graph paper with an unlabeled circular drafting diagram with no numbers and a solid coral disc. Visible paper materials: graph paper, buff card. Panels are separate paper sheets slightly overlapping, one sheet lying on top of the other with a thin visible paper edge, no tearing, no drop shadow. A loose hand-drawn charcoal line crosses the right panel. Palette: warm cream and buff paper, charcoal lines, a single coral (#d97757) accent field. Fine film grain and subtle halftone dots unify all panels. Flat, printed, tactile, museum-catalogue mood, generous negative space, one clear focal point. No text, no letters, no numbers, no labels. Avoid: torn paper, ragged edges, gradients, 3D render, glow, neon, drop shadows, logos, watermark, corner stamp.
```

**Topic: 新品发布 — A1 B2 C5 D3 F1**

```
Cinematic still, the thin curved horizon of a planet emerging from vast near-black space, raking warm light picks out fine atmospheric detail, large empty dark field occupying most of the frame, horizon low in the frame. Palette: near-black, deep blue haze, a thin warm orange rim of light as the only color. Soft film grain, restrained, quiet, monumental scale. No text, no labels. Avoid: gradients, 3D render, glow, neon, logos.
```

**Topic: 数据安全 — A2 B3 C2 D2 E3 F1**

```
Minimal editorial still life: a single tarnished brass padlock isolated on a flat cream paper background, soft even light, rich material detail, a narrow side panel of deep cyanotype blue paper with a white botanical print. Large negative space, object off-center. Palette: cream paper and pale sky blue, with one deep cyanotype blue panel as the accent. Subtle paper grain. Quiet, precise, archival. No text. Avoid: gradients, 3D render, glow, drop shadows, logos.
```
