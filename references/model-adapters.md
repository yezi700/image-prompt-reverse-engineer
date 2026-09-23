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

## Qwen-Image 2.1

Prefer the official Qwen-Image-2.1 prompt-rewrite shape when the user's workflow supports it:

- write one detailed English description of the finished image
- describe it as an observer, not as a command to the renderer
- keep the aspect ratio separate from the prose as `wh_ratio`
- preserve a user/source ratio when known instead of silently switching to a nearby ratio
- do not put pixel dimensions or aspect-ratio numbers inside the descriptive paragraph

For text-to-image recreation, make the spatial map unusually explicit:

- medium/style + subject + background in the opening sentence
- source orientation
- subject center position and approximate scale in the frame
- left/right orientation and any mirror-sensitive relationships
- upper-left / top / center / right / lower-third / edge positions when relevant
- foreground, midground, and background order
- lighting source, direction, quality, and cast-shadow direction
- balance and symmetry/asymmetry in the closing sentence

For a simple single-subject reference, do not mechanically inflate the prompt to hundreds of words when that would invent unsupported details. Be detailed about geometry and relationships, not imaginative about absent content.

Recommended machine-friendly output when requested:

```json
{"rewritten_prompt":"<English finished-image description>","wh_ratio":"<source ratio such as 2:3 or 3:2>"}
```

If the local workflow accepts only a text prompt, return the English `rewritten_prompt` and separately tell the user which ratio to set in the workflow.

Avoid unnecessarily fragmented tags.

### Qwen-Image 2.1 fidelity notes

- A 600×900 reference is 2:3; do not substitute 3:4 merely because it is a common portrait preset.
- A 600×400 reference is 3:2; do not substitute 4:3.
- Explicitly state mirror-sensitive directions, e.g. which side a flower head, tail, face, or prop occupies.
- Preserve asymmetry. Do not turn a loose forest path into a perfectly centered tunnel unless the reference is actually symmetric.
- For recognizable characters, if the user wants the exact character, use the character name plus canonical traits and the source-specific pose. If the user wants a generic/non-IP equivalent, omit the name.


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
