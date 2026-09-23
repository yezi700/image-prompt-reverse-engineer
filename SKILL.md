---
name: image-prompt-reverse-engineer
description: Reverse-engineer reference images into high-fidelity AI image prompts by identifying subject identity, pose/action, subject-object relationships, composition, viewpoint, negative space, shadow geometry, lighting, color, materials, depth-of-field behavior, spatial structure, and the few visual anchors that most strongly determine similarity. Use when a user provides or refers to an image and asks for its prompt, reverse prompt, image recreation prompt, prompt extraction, visual deconstruction, or model-specific prompts for GPT Image, Seedream, Qwen-Image, FLUX, SDXL, or Gemini Image.
---

# Image Prompt Reverse Engineer

Turn a reference image into a prompt that helps an image model reproduce its important visual properties. Do not merely caption the image or dump generic style tags.

## Core objective

Optimize for **visual fidelity**, especially:

1. subject identity and count
2. pose/action and subject-object relationships
3. composition, viewpoint, and spatial layout
4. distinctive appearance, silhouette, or product structure
5. lighting direction, shadow geometry, and dominant color relationships
6. background, depth structure, and degree of blur
7. medium/rendering language

Prefer a small number of concrete, high-impact observations over many weak adjectives.

In many images, resemblance is determined less by the generic subject category and more by a few structural cues such as:

- a prop being held, worn, carried, bitten, inserted, or placed
- strong negative space around the subject
- a diagonal band of light or shadow
- a path, road, corridor, or tree line creating a visual channel
- a shallow depth of field isolating the subject
- a recognizable character silhouette or canonical body structure

## Workflow

### 1. Classify the image

Determine only what is useful for prompt construction:

- likely use: portrait, fashion, product ad, illustration, character design, food, architecture, interior, landscape, vehicle, animal, 3D/CG, poster, still life, other
- medium: photo, photoreal AI, 3D/CG, cel-shaded illustration, digital painting, watercolor, vector, pixel art, mixed media, other
- primary subject and any secondary subjects

### 2. Build the visual skeleton

Before interpreting the visible background, inspect source image properties when file metadata or image tooling is available:

- pixel dimensions
- alpha/transparency
- palette transparency
- obvious cropping or thumbnail scale

Do not mistake a viewer's black, white, or checkerboard matte for the actual image background.

If the image is very small or heavily compressed, prioritize large-scale silhouette, color blocks, pose, and composition. Avoid inventing micro-details that the source cannot support.

Preserve source geometry before interpreting style:

- source pixel dimensions when available
- simplified source aspect ratio
- portrait / landscape / square orientation
- approximate primary-subject bounding box: center position, width, and height as fractions of the frame
- left/right orientation of faces, bodies, props, stems, vehicles, light boundaries, and diagonals
- symmetry versus asymmetry
- whether an important feature is subtle, moderate, or dominant

Do not silently recenter, mirror, crop tighter, widen, or beautify the composition.

Describe:

- subject count
- shot size / framing
- viewpoint and camera height
- front / side / three-quarter / back / over-the-shoulder orientation
- subject placement using approximate frame regions or fractions
- composition pattern and degree of symmetry
- perspective strength
- foreground / midground / background relationships
- directional relationships such as left-to-right, right-to-left, upper-left to lower-right, and vice versa

Spatial relationships matter more than decorative adjectives.

Pay special attention to compositional forces that strongly affect resemblance:

- negative space
- shape and direction of major shadows
- leading lines
- visual channels or tunnels
- background blur strength
- subject isolation versus environmental inclusion

If these dominate the image, treat them as primary features rather than secondary decoration.

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

Use multiple anchor types when helpful:

- **subject anchors**: who/what the subject is and its defining appearance
- **relationship anchors**: how the subject interacts with props, objects, or the environment
- **geometry anchors**: source aspect ratio, subject scale, center position, left/right orientation, non-mirroring constraints, and diagonal direction
- **composition anchors**: framing, placement, viewpoint, leading lines, negative space, major shadow shapes, symmetry/asymmetry, or blur behavior
- **style anchors**: medium/rendering traits that strongly affect recognition

Good anchors:

- back-facing figure turning the head toward camera
- high bun with pearl accessory
- pale lavender backless dress with a large rear bow
- bouquet of purple-pink tulips held with both hands
- pure white background with soft cel shading
- a single pink rose in a clear cylindrical bottle
- a diagonal triangular sunlight/shadow split across a pink wall
- a golden retriever puppy sitting front-facing with a yellow tulip held horizontally in its mouth
- a forest path receding through tall vertical trunks toward a brighter center
- a rounded mascot silhouette with a cream belly and closed eyes

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

- subject identity, pose/action, and subject-prop relationship: very high
- silhouette, distinctive clothing, product geometry, and major props: high
- composition, negative space, shadow geometry, and leading lines: high when visually dominant
- lighting, dominant palette, and depth-of-field behavior: medium-high
- minor accessories, microtexture, or small background details: medium or low
- generic quality words: very low

If the image is minimalist, geometric, poster-like, or highly stylized, composition and shadow shape may outrank fine subject detail.

Do not over-amplify an anchor merely because it is distinctive. Preserve its strength in the reference. A slight path opening should not become a perfectly symmetric tunnel; a modest shadow edge should not become a theatrical spotlight unless the reference supports that.

If the image contains a well-known character, mascot, or recurring design, canonical silhouette and body structure may outrank local rendering details.

### 7. Write the prompt in weighted order

Put the highest-impact information in the first third of the prompt.

Recommended order:

source orientation / aspect-ratio note when relevant → subject → pose/action → subject-object relationship → subject size and exact frame position → left/right orientation and non-mirroring constraints → composition/viewpoint → distinctive appearance/structure → negative space / leading lines / shadow geometry when important → lighting → color → material → background/depth → medium/style → finishing characteristics

Use coherent natural language. Avoid long tag dumps unless the target model benefits from tags.

### 8. Handle text, brands, and recognizable IP carefully

If text or branding is visually important, describe placement, typography, color, and layout separately from the rest of the scene.

Do not pretend an image model will reliably reproduce exact readable text. Mention that exact text is better added in a later editing/layout step when relevant.

For recognizable characters or styles, prioritize concrete visual traits and composition instead of making the prompt depend on a name alone.

If the user explicitly wants faithful recreation of a recognizable fictional character and naming it is appropriate, include the character name together with canonical visual traits. If the user asks for a generic or non-IP version, omit the name and keep only visual traits.

### 8.5. Special handling for recognizable characters, mascots, and recurring designs

When the subject is a recognizable fictional character, mascot, or strongly standardized design, separate analysis into two layers:

1. **canonical design anchors**  
   Persistent traits that define the character across images, such as silhouette, body proportions, signature colors, facial layout, shell/body structure, or iconic shape language.

2. **image-specific presentation anchors**  
   Traits specific to this image, such as pose, angle, expression, lighting, background, or rendering treatment.

In these cases, prioritize silhouette and body structure before micro-details.

For simple cartoon or mascot-like subjects, a strong silhouette can be more important than texture or lighting.

For exact-character recreation, preserve the source pose, limb directions, body tilt, face direction, and crop. Do not let the canonical character identity override the specific pose shown in the reference.

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
3. **关系锚点** — only when subject-object interaction matters
4. **构图锚点** — only when composition, negative space, leading lines, shadow geometry, or blur strength strongly affect similarity
5. **几何信息** — source aspect ratio and any mirror-sensitive / placement-critical constraints when fidelity depends on them
6. **正向提示词** — one ready-to-use natural-language prompt
7. **负向 / Avoid** — only when useful for the target model
8. **模型适配说明** — only if a target model is specified or the user asks

If the user explicitly asks only for the prompt, output the prompt directly and omit analysis.

## Quality gate

Before answering, silently verify:

- Is the true primary subject identified?
- Are pose/action and gaze correct where relevant?
- Are subject-object relationships explicit?
- Is the source aspect ratio preserved or explicitly surfaced?
- Are the primary subject's approximate position and scale captured?
- Are mirror-sensitive directions explicit where needed?
- Are framing, viewpoint, symmetry/asymmetry, and composition captured?
- Did you account for negative space, major shadow shapes, or leading lines if they dominate the image?
- Did you capture depth-of-field / blur behavior when it strongly affects the image?
- If source transparency is available, did you avoid mistaking the preview matte for a real background?
- If the source is low-resolution, did you avoid unsupported micro-detail?
- For recognizable characters or mascots, did you separate canonical design traits from image-specific traits?
- Are the top visual anchors present early in the prompt?
- Did you avoid unsupported technical guesses?
- Did you preserve anchor strength instead of exaggerating it?
- Did you avoid generic quality-word padding?
- Did you include only relevant subject-specific details?
- Does the final prompt read naturally and remain directly usable?

Revise internally if any answer is no. Do not reveal hidden reasoning.

## References

- For people, products, food, architecture, interiors, vehicles, animals, landscapes, still life, subject-prop interactions, recognizable characters, and illustration-specific analysis: `references/visual-analysis.md`
- For GPT Image, Seedream, Qwen-Image, FLUX, SDXL, and Gemini Image prompt adaptation: `references/model-adapters.md`
- For expanded structured output and JSON-friendly fields: `references/output-schema.md`


## Fidelity limitation

Prompt-only recreation can reproduce composition, style, pose, and visual type, but it is not a reliable identity-preservation method for a specific real person. If exact facial identity is the user's goal, say that a reference-conditioned image-to-image or identity-preserving workflow is more appropriate than text-only prompting. This does not apply to simply matching a generic portrait style.
