# Model Adapters

These are practical prompt-shaping defaults, not claims about undocumented internal weighting. Prefer the user's known workflow when they provide one.

## GPT Image

Use complete natural-language instructions.

Prioritize:

- what to generate
- subject pose and object relationships
- layout and viewpoint
- colors and materials
- background
- rendering/photographic language

Keep constraints in natural language. Avoid SD-style quality-tag dumps.

## Seedream

Use coherent natural language with explicit visual relationships.

Prioritize:

- subject
- action
- composition
- scene relationship
- style/medium
- lighting

For recreation, put the visual anchors in the first portion of the prompt.

## Qwen-Image

Use clear, structured natural language.

Make explicit:

- subject count and identity
- pose/action
- relative positions
- composition
- color
- environment

Avoid unnecessarily fragmented tags.

## FLUX

Keep the prompt semantically dense and visually concrete.

Strongly specify:

- subject and distinctive appearance
- framing and viewpoint
- action
- environment
- lighting
- material

Reduce redundant generic quality words.

## SDXL

A keyword-oriented format is acceptable when it matches the user's workflow.

Use:

- concise positive prompt containing subject, framing, pose, appearance, lighting, background, medium/style
- dedicated negative prompt when the workflow exposes one

Typical negative categories for people, when relevant:

`blurry, bad anatomy, deformed hands, extra fingers, extra limbs, distorted face, asymmetrical eyes, awkward pose, text artifacts, watermark`

For products, prefer categories such as:

`distorted product shape, incorrect proportions, warped packaging, broken geometry, fake reflections, cluttered background, blurry edges, text artifacts, watermark`

Do not copy a generic negative block when it is irrelevant.

## Gemini Image

Use complete visual description with explicit object relationships and layout.

Prioritize:

- overall intent
- hierarchy of subjects
- spatial relationships
- composition
- style consistency
- lighting and palette

## When the target model is unknown

Return a model-neutral natural-language prompt that should transfer reasonably well across instruction-oriented image generators.
