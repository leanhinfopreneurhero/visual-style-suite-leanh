# Prompt Recipes

How to encode extracted DNA into generation prompts. Two formats always: Midjourney + model-agnostic.

## The encoding order (both formats)

`[subject] + [subject treatment] + [environment] + [lighting DNA] + [camera language] + [rendering + texture] + [color logic + NEW palette] + [mood register] + [params]`

Front-load what matters most: models weight early tokens heavier.

## Midjourney template

```
[subject with treatment stance], [environment], [lighting: direction + quality + temperature],
[camera: focal feel + DOF + angle], [rendering mode + edge/finish], [texture/grain],
color palette of [HEX or named swatches] with [color logic: e.g. muted field with single saturated accent],
[two-word mood], [era/genre markers if load-bearing]
--ar [ratio] --stylize [see below]
```

- **--stylize**: 50-150 to keep YOUR DNA in control; 400+ lets MJ's aesthetics override — use only if the DNA is close to MJ's defaults
- **--no**: use for DISCARD items that MJ will otherwise inject (e.g. `--no teal, lens flare` when escaping the orange-teal gravity well)
- Never include the SREF code in rebuilt prompts — the whole point is independence from it
- Palette in prompt: name hues in words AND give 2-3 HEX values; MJ reads both

## Model-agnostic template (Nano Banana / GPT-Image / Flux / SDXL)

Natural-language paragraph, same order, fuller sentences:

```
A [rendering mode] image of [subject], [treatment stance]. Set in [environment].
Lit by [direction] [quality] light with [temperature behavior]. Shot as if on a [focal]mm lens,
[DOF], from [angle]. [Texture/finish sentence]. The palette is strictly [swatches + ratios],
following [color logic]. Overall mood: [register]. Avoid: [DISCARD list].
```

The explicit "Avoid:" line replaces --no and works across models.

## Drift warnings — the fragile DNA list

Warn the user when the KEEP column includes these (they degrade in generation):
- **Thin DOF at wide aspect ratios** → reinforce: "85mm, close quarters, background dissolved"
- **Restricted palettes** → models drift to full color; repeat the palette twice + Avoid line
- **Broken/painterly edges** → often smoothed out; add "visible brushwork, no digital smoothness"
- **Underexposure / low-key** → models auto-brighten; say "deep shadows retain no detail, exposed for highlights"
- **Specific grain/print artifacts** → add process words ("scanned 35mm negative, halation on highlights")
- **Negative space** → models fill space; say "vast empty [color] field occupying 70% of frame"

## Palette generation (when user says "surprise me")

Offer 3 named palettes that fit the DNA's color LOGIC but change all hues:
- Each: name + 5-7 HEX + one-line mood + usage ratio
- Make them genuinely distinct (one warm-led, one cool-led, one unexpected)
- Check contrast strategy survives: if DNA = "muted + one saturated accent", every offered palette needs exactly that structure

## Consistency across a series

When the user will generate MANY images in the style:
- Lock a reusable **style suffix** (everything after the subject) — same words every prompt
- Vary ONLY subject + environment tokens
- Keep --stylize and --ar constant across the series
- Log the suffix in the deliverable so it's copy-pasteable
