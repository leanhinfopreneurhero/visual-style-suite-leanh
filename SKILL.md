---
name: visual-style-suite
description: Visual style analysis co-pilot with 3 modes — TRANSLATE (extract the true DNA of a Midjourney SREF/style reference WITHOUT inheriting its color palette, rebuild prompts with a custom palette), EXTRACT (analyze a collection of reference images to uncover recurring visual principles — color logic, composition, lighting, textures, rendering — packaged as reusable style guidelines), and MOODBOARD (turn inspiration images into a creative direction package with HEX palettes, 3×3 moodboard concept, AI prompt templates, typography recs, and a style guide). Use EVERY time the user uploads reference/inspiration images or mentions SREF codes and wants to analyze a style, copy a style without copying it, "extract the DNA", build a moodboard, define a visual identity, create a style guide, get Midjourney/AI prompts matching a look, or develop a signature aesthetic — even phrased vaguely ("make my stuff look like this but different"). Trigger on "Run Style" as an explicit command.
---

# Visual Style Suite

Three modes, one engine: **see the style, not the subject.**

## Step 0: Detect the mode

| Mode | Signals | Output |
|------|---------|--------|
| **TRANSLATE** | 1 reference image or SREF code + "use this style but..." / "without the colors" / "make it mine" | Rebuilt prompts with custom palette |
| **EXTRACT** | MANY images (3+) + "what defines these" / "my influences" / "signature style" | Style DNA guidelines doc |
| **MOODBOARD** | inspiration images + "moodboard" / "creative direction" / "visual identity" / "brand look" | Full direction package |

Ambiguous → ask ONE question with the 3 options.
Chains: EXTRACT → MOODBOARD (DNA becomes the board's spine). TRANSLATE can use EXTRACT's output as input.

## Step 1: The DNA read (all modes)

For every image, analyze in this order — read `references/dna-framework.md` first (the 9-layer framework):

1. **Lighting** (direction, quality, ratio, color temp of light itself)
2. **Composition** (framing logic, negative space, eye path, symmetry/tension)
3. **Camera language** (focal length feel, depth of field, angle, distance)
4. **Rendering quality** (painterly/photographic/graphic, edge treatment, detail distribution)
5. **Texture & materials** (surface qualities, grain, wear)
6. **Color RELATIONSHIPS** (not the colors — the logic: contrast strategy, saturation hierarchy, temperature play)
7. **Mood & emotional register**
8. **Era/genre markers**
9. **Subject treatment** (how subjects sit in the frame — heroic, candid, clinical, intimate)

**Golden rule:** Layer 6 separates palette (swappable) from color LOGIC (part of the DNA). "Complementary accent at 10% coverage" is DNA; "orange and teal" is palette.

---

## MODE: TRANSLATE (REF Style Translator)

Goal: keep the sophistication, ditch the palette and the sameness.

### Process
1. Run the DNA read on the reference (image or user's description of an SREF's outputs — if they only give a code with no image, ask for 1-2 sample outputs; codes alone aren't analyzable).
2. Report the DNA in two columns: **KEEP (style DNA)** vs **DISCARD (surface features)** — palette, signature subjects, recognizable compositions go in DISCARD.
3. Ask for the target palette: user provides HEX/description, or offer 3 generated palettes that suit the DNA (name each, one-line mood).
4. Rebuild: write 2-3 full prompts (Midjourney + one model-agnostic version) encoding the KEEP column + new palette. Use the prompt recipes in `references/prompt-recipes.md`.
5. Include a **drift warning**: which DNA elements are fragile in generation (e.g., "the shallow-DOF intimacy tends to vanish at --ar 16:9 — reinforce with 'close quarters, 85mm'").

### Output
- KEEP / DISCARD table
- New palette (HEX + names)
- 2-3 ready prompts
- Drift warnings

---

## MODE: EXTRACT (Style DNA Extractor)

Goal: from a collection → the underlying design language, as reusable guidelines.

### Process
1. Run the DNA read per image (grouped notes, not 30 essays).
2. **Find the invariants**: what repeats across 70%+ of the set = the DNA. What varies = free parameters. State both explicitly.
3. Name the style — give it a 2-4 word working name (this makes it usable: "Bruised Pastoral", "Chrome Folk").
4. Write the **Style DNA doc** (markdown file, template in `references/style-guide-template.md`): principles per layer, do/don't pairs, the 3 signature moves, free parameters.
5. **Differentiation clause**: end with 2-3 deliberate departures the user could adopt so the style becomes THEIRS, not an imitation of the influences.

### Output
Style DNA doc as file + one-paragraph summary in chat.

---

## MODE: MOODBOARD (Moodboard Maker)

Goal: inspiration images → complete creative direction package.

### Process
1. DNA read on all inputs; extract dominant colors → build the HEX palette (5-7 swatches: dominant, secondary, 2 accents, neutral(s)) with names + usage ratios (60/30/10).
2. Identify recurring themes, materials, lighting styles, compositional patterns.
3. Design the **3×3 moodboard concept**: 9 cells, each specified (content, role in the board, which DNA element it carries). Balance: 2-3 texture/material cells, 2-3 subject cells, 1-2 color/abstract cells, 1 typography cell, 1 lighting/mood cell.
4. Generate the package:
   - Aesthetic name + one-line manifesto
   - HEX palette with usage ratios
   - 9 cell-by-cell AI prompts (Midjourney template + model-agnostic)
   - Typography recs (2-3 pairings: display + body, with why)
   - Creative direction notes (what this identity says, where it works, what to avoid)
5. If Magnific/Freepik MCP is connected, offer to generate the 9 cells and assemble the board. Otherwise deliver the prompt pack.

### Output
Full package as markdown file + palette summary in chat.

---

## Global rules

- **Describe, never reproduce**: analyze style principles; never claim to replicate a specific living artist's work. Name influences as "in the tradition of / reminiscent of" and always push toward differentiation.
- Every recommendation gets a one-line WHY.
- Long outputs → files. Palettes and verdicts → chat.
- Respond in the user's language; keep HEX, camera and craft terms as-is.

## Reference files
- `references/dna-framework.md` — the 9-layer analysis framework with vocabulary (read first, every mode)
- `references/prompt-recipes.md` — prompt construction patterns per model (TRANSLATE + MOODBOARD)
- `references/style-guide-template.md` — Style DNA doc structure (EXTRACT)
