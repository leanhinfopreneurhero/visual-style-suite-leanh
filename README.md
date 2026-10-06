# Visual Style Suite

Visual Style Suite is an AI-assistant skill for analyzing visual references and turning them into reusable creative direction. It focuses on the underlying design language of a look—lighting, composition, camera language, rendering, texture, color relationships, mood, genre, and subject treatment—rather than merely copying subjects or palettes.

## What it does

The skill supports three workflows:

- **TRANSLATE** — Break down a reference image or Midjourney SREF look, separate its visual DNA from surface features, and rebuild it with a new palette.
- **EXTRACT** — Analyze a collection of images to identify recurring principles and package them as a reusable Style DNA guide.
- **MOODBOARD** — Turn inspiration images into a complete creative-direction package with a palette, moodboard plan, generation prompts, typography recommendations, and usage guidance.

Across all three modes, the skill distinguishes between color **logic**—such as contrast strategy or saturation hierarchy—and specific color **values**, which can be replaced without losing the character of the style.

## Key outputs

Depending on the selected mode, Visual Style Suite can produce:

- KEEP/DISCARD analysis of visual DNA versus surface features
- Named palettes with HEX values and usage ratios
- Midjourney and model-agnostic image-generation prompts
- Drift warnings for fragile stylistic traits
- Reusable Style DNA documents
- 3×3 moodboard concepts and cell-by-cell prompts
- Typography pairings and creative-direction notes

## Repository structure

```text
.
├── SKILL.md
└── references/
    ├── dna-framework.md
    ├── prompt-recipes.md
    └── style-guide-template.md
```

- `SKILL.md` defines the skill triggers, workflows, outputs, and global rules.
- `references/dna-framework.md` contains the nine-layer visual-analysis framework.
- `references/prompt-recipes.md` provides prompt structures and consistency guidance.
- `references/style-guide-template.md` defines the output format for extracted Style DNA documents.

## Usage

Install or import this repository using the skill workflow supported by your AI assistant, then provide reference images and describe the desired outcome.

Example requests:

```text
Run Style: analyze this reference and keep the lighting and composition,
but rebuild it with a muted olive and burgundy palette.
```

```text
Extract the visual DNA shared by these references and turn it into
a reusable style guide for future campaigns.
```

```text
Create a moodboard direction from these inspiration images, including
a HEX palette, typography pairings, and prompts for all nine cells.
```

If a request is ambiguous, the skill helps choose between TRANSLATE, EXTRACT, and MOODBOARD before proceeding.

## Design principles

- **Describe, never reproduce** — Analyze principles without claiming to replicate a living artist's style.
- **Separate DNA from surface** — Preserve structural relationships while allowing subjects, locations, and palette hues to change.
- **Make guidance actionable** — Use concrete, checkable language and explain why each recommendation works.
- **Encourage differentiation** — Turn references into a starting point for an original visual identity.

## License

No license has been specified for this repository.
