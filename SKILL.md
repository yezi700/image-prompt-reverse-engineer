---
name: image-prompt-reverse-engineer
description: Reverse-engineer reference images into high-fidelity AI image prompts by identifying the subject, composition, pose, camera/viewpoint, lighting, color, materials, spatial relationships, and the few visual anchors that most strongly determine similarity. Use when a user provides or refers to an image and asks for its prompt, reverse prompt, image recreation prompt, prompt extraction, visual deconstruction, or model-specific prompts for GPT Image, Seedream, Qwen-Image, FLUX, SDXL, or Gemini Image.
---

# Image Prompt Reverse Engineer

Turn a reference image into a prompt that helps an image model reproduce its important visual properties. Do not merely caption the image or dump generic style tags.

## Core objective

Optimize for **visual fidelity**, especially:

1. subject identity and count
2. pose/action and object relationships
3. composition and viewpoint
4. distinctive appearance or product structure
5. lighting and dominant color relationships
6. background and depth structure
7. medium/rendering language

Prefer a small number of concrete, high-impact observations over many weak adjectives.

## Workflow

### 1. Classify the image

Determine only what is useful for prompt construction:

- likely use: portrait, fashion, product ad, illustration, character design, food, architecture, interior, landscape, vehicle, animal, 3D/CG, poster, other
- medium: photo, photoreal AI, 3D/CG, cel-shaded illustration, digital painting, watercolor, vector, pixel art, mixed media, other
- primary subject and any secondary subjects

### 2. Build the visual skeleton

Describe:

- subject count
- shot size / framing
- viewpoint and camera height
- front / side / three-quarter / back / over-the-shoulder orientation
- subject placement
- composition pattern
- perspective strength
- foreground / midground / background relationships

Spatial relationships matter more than decorative adjectives.

### 3. Load only the relevant subject rules

Read `references/visual-analysis.md` when detailed subject-specific analysis is needed.

Do not run every category mechanically. For example, hair and facial structure are relevant to people but not to product photography.

### 4. Separate observation from inference

State directly observable visual facts as facts.

Do not invent exact camera models, focal lengths, apertures, ISO values, render engines, software, lighting hardware, or production metadata unless visibly established.

When useful, describe the visual effect instead:

- "shallow depth of field with portrait-lens compression"
- not "shot on an 85mm f/1.4 lens"

If suggesting a possible implementation, label it as an implementation suggestion rather than an observed fact.

### 5. Extract visual anchors

Select **3–7 visual anchors**: concrete elements whose absence would make a recreation feel noticeably unlike the reference.

Good anchors:

- back-facing figure turning the head toward camera
- high bun with pearl accessory
- pale lavender backless dress with a large rear bow
- bouquet of purple-pink tulips held with both hands
- pure white background with soft cel shading

Bad anchors:

- beautiful
- high quality
- masterpiece
- cinematic
- detailed

Order anchors from most to least important.

### 6. Assign similarity priority

Internally assign each important element a rough priority from 0–100 based on its impact on resemblance.

Use the priority to order the final prompt. Do **not** expose numeric scores unless the user asks for them.

Typical priority hierarchy:

- subject / pose / layout: very high
- distinctive clothing, product geometry, major props: high
- lighting / dominant palette: medium-high
- minor accessories / microtexture: medium or low
- generic quality words: very low

### 7. Write the prompt in weighted order

Put the highest-impact information in the first third of the prompt.

Recommended order:

subject → pose/action → composition/viewpoint → distinctive appearance/structure → key props/relationships → lighting → color → material → background/depth → medium/style → finishing characteristics

Use coherent natural language. Avoid long tag dumps unless the target model benefits from tags.

### 8. Handle text, brands, and recognizable IP carefully

If text or branding is visually important, describe placement, typography, color, and layout separately from the rest of the scene.

Do not pretend an image model will reliably reproduce exact readable text. Mention that exact text is better added in a later editing/layout step when relevant.

For recognizable characters or styles, prioritize concrete visual traits and composition instead of making the prompt depend on a name alone.

### 9. Adapt to the target model

If the user names a target image model, read `references/model-adapters.md` and output only the relevant adapted version unless the user requests comparisons.

If no model is specified, default to a model-neutral natural-language prompt.

### 10. Negative / avoidance guidance

Do not automatically append a generic negative-prompt block.

- For SDXL or workflows with a dedicated negative input, provide a concise negative prompt tailored to the image category.
- For instruction-oriented models, convert important exclusions into natural-language constraints.
- Only include problems that are actually likely to damage resemblance.

## Default output

Read `references/output-schema.md` for the full structured format.

For ordinary user requests, keep the response practical and compact. Default to:

1. **画面概述** — 2–4 sentences
2. **视觉锚点** — 3–7 ordered items
3. **正向提示词** — one ready-to-use natural-language prompt
4. **负向 / Avoid** — only when useful for the target model
5. **模型适配说明** — only if a target model is specified or the user asks

If the user explicitly asks only for the prompt, output the prompt directly and omit analysis.

## Quality gate

Before answering, silently verify:

- Is the true primary subject identified?
- Are pose/action and gaze correct where relevant?
- Are subject-object relationships explicit?
- Are framing, viewpoint, and composition captured?
- Are the top visual anchors present early in the prompt?
- Did you avoid unsupported technical guesses?
- Did you avoid generic quality-word padding?
- Did you include only relevant subject-specific details?
- Does the final prompt read naturally and remain directly usable?

Revise internally if any answer is no. Do not reveal hidden reasoning.

## References

- For people, products, food, architecture, interiors, vehicles, animals, landscapes, and illustration-specific analysis: `references/visual-analysis.md`
- For GPT Image, Seedream, Qwen-Image, FLUX, SDXL, and Gemini Image prompt adaptation: `references/model-adapters.md`
- For expanded structured output and JSON-friendly fields: `references/output-schema.md`
