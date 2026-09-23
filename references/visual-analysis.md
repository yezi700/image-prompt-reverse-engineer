# Visual Analysis Reference

Use only the sections that match the image.

## Table of contents

- People
- Products
- Food
- Architecture
- Interiors
- Vehicles
- Animals
- Landscapes
- Illustration and anime
- Minimal still life and negative space
- Subject-prop interaction
- Recognizable characters and mascots
- Lighting
- Color
- Materials

## People

Prioritize pose, gaze, silhouette, clothing structure, and hair before micro-details.

Analyze when visible:

- apparent age range, number of people, body orientation, head orientation, gaze
- face shape tendency, brows, eyes, nose, mouth, expression, makeup
- hair length, part, bangs, tied structure, curl, color, accessories
- garment type, cut, neckline, sleeves, shoulders, waist, hem/pants shape, material, pattern, dominant colors, accessories
- body posture, weight distribution, shoulder/hip direction, hand placement, leg placement, head movement
- interaction with props or other people

Describe actions relationally. Prefer:

"The figure faces away from the camera, rotates the right shoulder slightly toward it, turns the head back, and holds a bouquet with both hands."

Over:

"A girl posing naturally."

For portraits, also identify the portrait subtype when useful:

- studio headshot
- business headshot
- lifestyle portrait
- fashion portrait
- environmental portrait

In these cases, expression, eye contact, hair silhouette, shirt/jacket shape, and background blur often matter more than exhaustive facial micro-description.

Do not infer real identity, nationality, ethnicity, medical state, or other sensitive traits from appearance.

## Products

Prioritize:

- product category and overall silhouette
- geometry and proportions
- viewing angle and orientation
- surface material and reflectivity
- transparent / translucent / metallic / plastic / glass behavior
- packaging construction
- placement and support surface
- shadow, reflection, suspension or floating state
- background and commercial lighting

For product recreation, product angle + geometry + material + lighting + background usually dominate resemblance.

For minimalist product setups, also inspect negative space, backdrop geometry, support-surface lines, and hard-edged shadow shapes.

## Food

Analyze:

- food category and visible ingredients
- shape, surface texture, browning/cooking appearance
- gloss, sauce, steam, garnish
- plating and vessel
- tabletop context
- light direction and softness
- depth of field

Do not invent recipes or unseen ingredients.

## Architecture

Analyze:

- building type and massing
- facade geometry
- material palette
- windows / openings / structural rhythm
- architectural style in descriptive visual terms
- relation to ground, vegetation, sky, roads, people, vehicles
- camera elevation and convergence/perspective

Pay attention to repeated structural rhythm and strong leading lines when they dominate the image.

Avoid claiming a specific architect unless explicitly established and useful to the user.

## Interiors

Analyze:

- room type and layout
- major furniture placement
- walls, floor, ceiling
- windows and natural-light direction
- artificial fixtures
- material palette
- decor density
- depth and circulation path

When present, explicitly capture corridor-like visual channels, vanishing paths, repeated columns, or strong foreground framing.

## Vehicles

Analyze:

- vehicle class
- body silhouette and proportion
- view angle and heading
- body color and reflection behavior
- wheel / light / glass characteristics
- stationary vs moving state
- road/environment context
- motion blur and light trails if present

Do not guess exact model unless the user is specifically asking for identification and the evidence is sufficient.

## Animals

Analyze:

- species/category when reasonably visible
- fur / feathers / scales
- dominant color pattern
- pose and motion
- gaze
- interaction with people/objects
- environment
- subject isolation versus environmental inclusion
- depth-of-field / blur behavior when visually important

Pay special attention to subject-object interaction.

Examples of high-value interaction cues:

- holding
- carrying
- biting
- wearing
- leaning on
- standing on
- sitting beside
- looking toward

Example:

"A golden retriever puppy sits front-facing on a stone path and holds a yellow tulip horizontally in its mouth."

This is much more useful than:

"A cute dog with a flower."

## Landscapes

Analyze:

- terrain
- water
- vegetation
- sky and cloud structure
- weather impression
- time-of-day cues
- light direction
- atmospheric perspective
- foreground / midground / background layering
- palette

When present, strongly prioritize **leading lines** and **visual channels**, such as:

- roads
- trails
- rivers
- corridors
- rows of trees
- bridges
- canyon gaps

Also identify where the brightest area sits:

- foreground
- midground
- background
- off-center opening

Example:

"A forest path recedes into the distance between tall vertical trunks, guiding the eye toward a brighter central opening."

This is more useful than:

"A peaceful green forest with a path."

## Illustration and anime

Analyze the actual rendering language rather than relying on artist names:

- line weight and cleanliness
- flat vs graded color
- cel-shadow shape and hardness
- highlight shape
- saturation and palette size
- character proportions / head-to-body relation
- facial simplification
- edge softness
- watercolor / paper / brush texture
- background complexity
- graphic vs painterly treatment

Example:

"clean thin line art, restrained pastel palette, soft cel-shaded shadows, sparse watercolor texture"

If the subject is a recurring character or mascot, also read the **Recognizable characters and mascots** section.

## Minimal still life and negative space

For minimalist still life, simple product setups, and sparse editorial images, do not underestimate:

- negative space
- subject placement within empty space
- major shadow shape
- direction and boundary of light/shadow divisions
- wall or backdrop texture
- table or surface line
- object tilt or stem direction
- amount of visual breathing room

In some images, these matter more than fine subject detail.

Example:

"A single pink rose stands in a clear cylindrical glass bottle half-filled with water, placed low in the frame against a pale pink textured wall, with a large diagonal sunlight-and-shadow split creating a geometric triangular shape across the background."

## Subject-prop interaction

Whenever a prop or secondary object is essential to resemblance, extract the interaction explicitly.

Common interaction types:

- holding
- carrying
- biting
- wearing
- hugging
- sitting on
- standing beside
- inserting into
- placing on
- leaning against

Do not merely list both objects separately.

Weak:

"dog, tulip"

Strong:

"dog holding a tulip horizontally in its mouth"

Weak:

"rose, bottle"

Strong:

"single rose inserted into a clear bottle of water"

If the interaction is visually central, it should appear early in the final prompt.

## Recognizable characters and mascots

When the image shows a recognizable fictional character, mascot, or recurring standardized design, split analysis into two layers.

### A. Canonical design anchors

Persistent traits that define the character across images:

- silhouette
- body proportions
- head-to-body ratio
- signature colors
- facial layout
- shell / belly / tail / ear / limb structure
- iconic markings or body segmentation

### B. Image-specific presentation anchors

Traits specific to the current image:

- pose
- angle
- facial expression
- gesture
- background
- lighting
- line quality
- shading style

For mascot-like or cartoon subjects, prioritize silhouette and structure before micro-detail.

Examples:

- a rounded, heavy blue-and-cream body silhouette with closed eyes and lifted arms
- a small blue turtle-like character with a cream segmented belly and brown shell

## Lighting

Describe only visible effects.

### Direction

- front
- side
- side-back
- backlight
- top
- under-light
- window light
- ambient / diffuse

### Quality

- hard
- soft
- diffuse
- direct
- studio-like

### Contrast

- high key / low key
- high contrast / low contrast
- soft shadow / deep shadow
- rim or edge light

### Shadow geometry

When a cast shadow or light boundary becomes a major compositional element, describe:

- direction
- edge hardness
- approximate shape
- area of the frame it occupies
- whether it cuts across the background or subject

Do not reduce a dominant geometric shadow to a generic phrase such as "dramatic lighting."

### Special effects

Only when present:

- volumetric rays
- haze/glow
- neon
- colored environmental spill
- sunset/golden-hour look
- blue-hour look

## Color

Summarize, do not overcount colors.

- up to 3 dominant colors
- up to 3 supporting colors
- warm / cool / neutral / mixed temperature
- low / medium / high saturation
- low / medium / high value range
- useful palette descriptors such as pastel, cream, gray-pink, warm brown, cold blue, teal-orange when actually visible

## Materials

Only describe visible materials that matter to the recreation:

- skin, hair, cotton, silk, denim, leather
- metal, acrylic, plastic, glass
- wood, stone, concrete, ceramic
- flower petals, foliage, fur, feathers, water, food surfaces
