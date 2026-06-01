---
name: token-mode
description: Token Mode for VTT Battlemap Forge. Creates VTT-ready creature, monster, NPC, and character token images — 1:1 square, circular framed, face-first composition with intentional border breakout. Not a battlemap mode and not a cinematic scene-art mode. Load only when Token mode is active.
---

# Token Mode

Token Mode creates VTT-ready creature, monster, NPC, or character tokens. It is not a top-down battlemap mode and not a cinematic scene-art mode. Output is an image-generation prompt for a 1:1 square token portrait.

Token Mode is inherently creature-focused — there is no DM variant. The token itself IS the creature, NPC, or monster.

---

## Default Token Style

Unless the user requests otherwise, tokens follow this default presentation:

- 1:1 square format
- Circular fantasy token frame
- Bold red beveled rim
- Face-first composition
- Premium layered look
- Intentional border breakout
- Simple atmospheric background
- True transparent background outside the circular frame (alpha = 0)
- Strong readability at small VTT size
- No text, labels, UI, or status markers

The intended look is a premium tabletop token where the subject feels alive and dimensional, with selected anatomy or gear extending beyond the circular frame while the face remains the main focal point.

---

## Token Priorities

Every token must prioritize, in order:

1. Face readability at small VTT scale
2. Strong creature/NPC identity
3. Clear recognizable silhouette
4. Premium circular token presentation with controlled border breakout
5. Style consistency with the selected aesthetic
6. Clean separation from the background
7. No text, labels, UI, or nameplates

---

## Composition Rules

Default token composition:

- Square 1:1 image.
- Circular framed token, usually with a bold red beveled rim unless the user specifies another frame color.
- The face, head, or creature's main identifying feature must be the focal point.
- Frame the subject as a close-up portrait, head-and-shoulders bust, or tight creature portrait.
- The face should occupy most of the inner circle, usually around 55–75% of the token's visual attention.
- Eyes, expression, snout, teeth, horns, crest, or facial markings should be sharp and readable.
- Do not default to full-body framing unless the creature's whole silhouette is essential.

Important default presentation:

- Tokens should use a dynamic premium composition where selected parts of the subject visibly extend beyond the circular border.
- This border-breaking presentation is preferred by default, not optional.
- The token should feel dimensional and layered, rather than like a flat portrait simply cropped inside a circle.

Face-first composition:

The face must be the primary focal point, but the token may include additional iconic anatomy or gear to strengthen identity and silhouette, especially when these elements help create a strong border-break effect. This is face-first, not face-only — the priority is the face, but secondary elements outside the circle add drama and identity.

Subject emphasis:

- For humanoids, prioritize face, shoulders, upper chest, and one or two iconic silhouette elements.
- For monsters and beasts, prioritize the head and recognizable anatomy, while still allowing wings, horns, claws, ears, crests, tails, mandibles, or weapon tips to help create a dynamic silhouette.
- For wide or flying creatures, a partial bust-plus-silhouette approach is allowed, as long as the face remains the primary focal point.

---

## Composition Variants

Select the variant using the table below. Default is Face-Focused Bust.

### Variant Selection

| Subject type | Default variant |
|---|---|
| Humanoid NPC, villain, player character | Hero Bust |
| Beast, dragon, aberration, insect, reptile | Creature Head |
| General monster, swarm, or any ambiguous case | Face-Focused Bust |
| Tiny creature, flying creature, or monster whose full body shape is the primary identifier | Full Silhouette |

### Face-Focused Bust Token (Default)

- Best for NPCs, humanoids, beasts, and bosses.
- Face/head fills most of the frame.
- Upper shoulders, chest, cloak/armor visible.
- Controlled border breakout allowed.

### Creature Head Token

- Best for beasts, dragons, aberrations, insects, reptiles, and monsters with distinctive anatomy.
- Focus almost entirely on head, jaws, eyes, horns, crest, mandibles, or snout.
- Minimal torso or no torso.
- Strong border breakout from anatomy.

### Hero Bust Token

- Best for humanoid NPCs, villains, and player characters.
- Face, shoulders, upper torso, cloak/armor, and one identity prop (weapon, staff, shield).
- More composed and heroic than Creature Head.
- Border breakout from shoulders, cloak, or weapon.

### Full Silhouette Token

- Use only when explicitly requested or when the variant table indicates it.
- Best for tiny creatures, flying creatures, or monsters whose entire body shape is the main identifier.
- Still keep the face readable if the creature has one.
- Border breakout from wings, tail, or full body extensions.

---

## Border Breakout Rule

Use controlled border breakout by default.

The preferred premium token approach is:

- The subject should intentionally break the circular frame with selected silhouette elements.
- The circular border must remain clearly visible, but parts of the creature/NPC/monster should overlap and extend beyond it.
- This overlap should create depth, energy, and a more polished VTT token presentation.

Preferred breakout elements:

- Horns
- Crests
- Ears
- Snouts
- Beaks
- Mandibles
- Wings
- Claws
- Weapon tips
- Shoulders
- Cloak edges
- Armor spikes
- Tail tips

Breakout rules:

- The face must remain the main focal point and stay clearly readable.
- The face should remain mostly inside the circle, while secondary silhouette elements extend outside it.
- Breakout elements must enhance the silhouette, not clutter it.
- The circular frame must still read clearly as a token border.
- Avoid excessive breakout that makes the token feel messy or unreadable at small size.
- Border breakout must use existing visible anatomy, gear, or props from the reference image. Do not invent new silhouette elements just to break the frame.

### Background Outside the Frame Rule

Border breakout applies only to the token subject, never to the background.

The only elements allowed outside the circular frame are selected parts of the creature, NPC, monster, or its existing visible gear from the reference image. Background scenery, fog, brush texture, environmental props, ruins, trees, posts, water, mist clouds, landscape shapes, silhouettes, or atmospheric paint strokes must not extend outside the circular frame.

The area outside the token rim should remain clean and fully true transparent, except where the subject itself overlaps the frame. Do not create a rectangular painted canvas, vignette, smoky backdrop, or environmental scene outside the circular token.

Correct:
- Wings, proboscis, claws, horns, weapon tip, shoulders, or tail break the circular border.
- The swamp/forest/cave background remains contained inside the circle.
- Everything outside the ring is true transparent except subject breakout.

Incorrect:
- Fog, swamp water, reeds, trees, ruins, brush strokes, shadows, or background texture outside the ring.
- A full scene painted behind the token and extending beyond the circular frame.
- A square or rectangular canvas visible behind the token.

Preferred visual result:

- The token should not look like a flat image simply cropped inside a circle.
- It should look like the creature or character is pushing out of the token frame.

Good examples:

- A stirge's wings, proboscis, legs, and tail extending outside the red circular rim, while the swamp mist, bridge, reeds, water, trees, and atmospheric background remain fully contained inside the circular frame.
- A lizardfolk's spear tip, crest, tail, or shield edge breaking the frame.
- A gnoll's ears, mane, jawline, weapon, or shoulder spikes overlapping the border.

Bad examples:

- The entire subject trapped neatly inside the circle with no dimensional overlap.
- The face cropped awkwardly by the border.
- Large breakout elements blocking the eyes or expression.
- Too many limbs or props extending out and creating visual noise.

---

## Frame Rules

### Frame Color

Default frame is a bold red beveled rim. Accept alternative frame colors when the user specifies them.

| Frame Color | User Triggers |
|---|---|
| **Red** *(default)* | (no trigger needed) |
| Gold | "gold frame", "gold rim", "golden border" |
| Silver | "silver frame", "silver rim", "silver border" |
| Black | "black frame", "black rim", "dark border" |
| None | "no frame", "no border", "frameless", "borderless token" |
| Any other named color | Apply that color directly as a polished beveled rim (e.g. "blue frame", "purple rim", "arcane violet border") |

### Frame Style

Default frame style is a bold circular fantasy token frame with a polished beveled rim, similar to a premium VTT monster token. The frame should feel like a physical token rim — not a flat ring and not a UI overlay.

When the user requests no frame, the circular composition should still be implied through the subject's placement and the background treatment, but no visible rim is rendered.

### Transparency

The area outside the circular frame must be fully true transparent (alpha = 0) so the token can be placed on any VTT map without a visible bounding box. Only pixels inside or directly on the circular border should carry opacity. The token must be a valid PNG with real alpha channel — not a solid color fill, not a white or black background masked by the frame.

**Incorrect outputs — all must be avoided:**
- A checkerboard pattern outside the circle (this is a display artifact used in editors to indicate transparency, not actual transparency — do not render it as image content)
- A gray, white, or black canvas behind or around the circular frame
- A rectangular or square colored fill visible anywhere outside the token rim
- Any fog, smoke, vignette, or atmospheric blur extending beyond the circular border

**Correct result:** The area outside the circular token rim contains no pixels with any color or opacity. It is completely empty — invisible on any background color.

---

## Background Rules

Token backgrounds should be simple and atmospheric. Use the environment preset to determine the backdrop.

| Environment | Token Backdrop |
|---|---|
| 1 – Ancient Ruins | Soft stone gray blur, faint warm light from cracks or distant openings, aged textured atmosphere |
| 2 – Natural Cave | Dark stone blur with faint warm torch glow in inhabited areas, cool shadowed recesses at edges |
| 3 – Aquatic / Flooded | Deep blue-green water blur, soft caustic light patterns, cold bioluminescent accents |
| 4 – Urban / Sewer | Warm amber torch-lit blur (interior), cool blue-gray street haze (exterior) |
| 5 – Arctic / Frozen | Cold blue-white frost blur, faint warm glow near implied fire or torch sources |
| 6 – Jungle / Overgrown | Dappled green canopy bokeh, warm golden light breaks, humid atmospheric haze |
| 7 – Volcanic / Infernal | Hot orange-red underlit blur, dark volcanic texture, heat-shimmer atmosphere |
| 8 – Swamp / Bog | Murky green-gray mist, faint fungal bioluminescence, dark water reflection at edges |
| 9 – Desert / Arid | Warm golden sand blur with dramatic backlight glow, heat-haze atmosphere |
| 10 – Forest / Woodland | Dappled green-gold canopy bokeh, dark understory shadow at edges |
| 11 – Arcane / Planar | Deep indigo-violet blur, prismatic shimmer accents, sourceless magical glow |

**Default environment fallback:** If no environment is specified and none can be inferred from the subject, default to Environment 2 (Natural Cave) — warm torch-lit stone, dark edges. This is thematically neutral and works for most D&D creatures.

Background rules:

- Keep the background lower contrast than the face.
- Use a soft blurred or painterly backdrop — not a full scene.
- Match the creature's known environment when possible.
- Avoid busy scene details that compete with the portrait.
- No full battle scene, no tactical map, no grid, no UI, no labels.
- Only the area inside the circular frame carries background detail. Everything outside the circle must be fully true transparent (alpha = 0) — the token must be a valid PNG with real alpha channel, not a circular crop on a solid canvas. The outer area must contain no image content of any kind: no checkerboard, no gray fill, no color wash, no bleed from the background scene.

---

## Lighting Rules

Use readable dramatic portrait lighting:

- Strong enough to define the face and eyes.
- Soft enough to preserve material detail.
- Rim highlights may be used on horns, scales, fur, armor, wet skin, weapons, or silhouette edges.
- Avoid crushed black shadows over the face.
- Avoid blown highlights on the frame or forehead.
- Eyes should remain readable whenever the creature has eyes.

Default lighting direction: slightly above and to one side, creating natural facial modeling without harsh shadows.

**Exception:** Arcane casters, elementals, undead, infernal, or bioluminescent subjects may use a matching internal or environmental light source (magical glow, fire, spectral light, bioluminescence) as the primary key light, in addition to or instead of standard portrait lighting. Match the light source to the creature's nature and environment.

---

## Reference Image Handling

If a reference image is provided, it is an **identity source** — not a layout lock and not a scene to reproduce.

### What to extract from a reference image

- Core identity: species, face shape, coloration, distinctive markings.
- Silhouette features: horns, crest, ears, jaw shape, mane, wings, tail shape.
- Equipment and style: armor, clothing, weapons, accessories.
- Expression and character: mood, gaze, personality visible in the face.

### Reference Fidelity / No New Equipment

When a reference image is provided, preserve the subject's visible equipment exactly as identity information.

Do not invent new weapons, shields, armor pieces, jewelry, clothing, horns, scars, markings, props, or accessories that are not visible in the reference image or explicitly requested by the user.

If a visible object is partially cropped, unclear, or ambiguous, simplify it rather than replacing it with a new object. Preserve its material language and silhouette as closely as possible.

For token border breakout, only use silhouette elements that already exist in the reference image or were explicitly requested. Do not add a weapon, staff, spear, shield, tail, horn, wing, or armor spike solely to create a stronger breakout effect.

If a weapon or prop from the reference is included, match its original material and design. Example: a metal spear blade should remain a metal spear blade, not become a wooden spear, bone weapon, staff, club, or improvised branch.

### What NOT to do with a reference image

- Do not copy the entire scene composition or background.
- Do not preserve the full-body framing if the reference is wide or full-body art.
- Do not reproduce the original camera angle — crop and reinterpret as a face-first token.
- Do not treat it as a layout lock.

### Procedure

If the source image is full-body or wide scene art:

1. Extract the best head/face design and distinctive features.
2. Rebuild the subject as a close-up token portrait.
3. Preserve the style requested by the user over the exact camera angle of the reference.
4. Match identity, species, coloration, silhouette, and distinctive features.

If the source is already a face or bust portrait:

1. Use it as direct identity reference.
2. Adapt to the selected aesthetic style and token composition rules.
3. Apply border breakout and circular frame to the composition.

---

## Output Canvas Specification

The final generated image must be an exact 1:1 square PNG. Do not create a wide, landscape, or rectangular image of any kind. Do not place the token on a rectangular presentation canvas or within a non-square frame.

Center one circular fantasy token inside the square canvas. The circular frame should fill most of the square, leaving only minimal transparent padding around the outermost subject breakout elements.

Everything outside the circular token frame must be fully true transparent (alpha = 0), except for intentional subject-only breakout such as wings, horns, claws, weapon tips, shoulders, or tail. No rectangular background, no gray canvas, no fog, scenery, or environmental atmosphere outside the ring.

**Critical:** The transparent area must contain no image content whatsoever — not a checkerboard pattern, not a gray fill, not a white background, not a color wash. A checkerboard is the way transparency is *displayed* in image editors; it must not appear as rendered pixel content in the final image. The correct output looks like nothing is there — zero pixels, zero color, zero opacity — outside the token and its breakout elements.

The entire final image must be a valid PNG with real alpha channel — not a solid-color canvas with a circular mask, not a JPEG, and not an image with a hidden white or black background.

---

## Token Prompt Templates

### Output Rule

Return only the final prompt inside a **code block**. Output nothing else unless the user asks for explanation.

**Default: Compact Token Prompt.** Use Verbose Token Prompt only if the user explicitly asks for a full, verbose, or self-contained prompt.

---

### Compact Token Prompt

**If a reference image is provided**, open with:
> *"Create a 1:1 square VTT token portrait from the provided reference image."*

**If no reference image is provided**, open with:
> *"Create a 1:1 square VTT token portrait of the following creature."*

```
[OPENING LINE — see above]

Token Subject:
[CREATURE / NPC / MONSTER NAME OR TYPE — include key visual traits if no reference image]

Composition:
Use a face-first close-up composition: the subject's face, head, eyes, expression, and most recognizable features must be the clear focal point. Avoid full-body framing unless explicitly necessary for the creature's identity.

Token Frame:
Use a bold circular fantasy token frame with a polished [FRAME COLOR] beveled rim. Only the subject may intentionally break the circular border with selected silhouette elements for a premium token look. Background elements must stay completely inside the circular frame; outside the ring must be true transparent except for subject-only breakout. This border-break effect is desired by default. Use horns, crests, ears, snout, mandibles, wings, claws, weapon tips, shoulders, cloak edges, armor spikes, or tail tips extending beyond the frame. Keep the face mostly inside the circle, fully readable, and visually dominant.

Subject Identity:
[IF REFERENCE PROVIDED:] Match the subject's identity, species, coloration, silhouette, armor/clothing, visible equipment, weapons, props, and distinctive features from the reference image. Do not invent or redesign equipment, weapons, armor, accessories, anatomy, or props not present in the reference image.
[IF NO REFERENCE:] Render the subject based on the description above. Use genre-appropriate anatomy, coloration, and equipment typical of the subject's type.

Aesthetic Style:
[SELECTED AESTHETIC STYLE DESCRIPTION]

Background:
Simple atmospheric backdrop: [TOKEN BACKDROP from environment]. Keep it subdued, softly blurred, and lower contrast than the face. No tactical map, no grid, no full scene, no clutter.

Lighting:
Dramatic but readable portrait lighting. Highlight the face, eyes, and defining features. Use subtle rim light on silhouette edges, horns, scales, fur, armor, or wet surfaces. Avoid crushed black shadows over the face and avoid overbright highlights.

Restrictions:
No text, labels, UI, nameplates, numbers, captions, watermarks, status icons, tactical map, grid, or readable writing. Only the interior of the circular frame carries background image content. The area outside the circle must be fully true transparent alpha, except for intentional subject-only breakout such as wings, horns, claws, weapon tips, shoulders, or tail. No fog, scenery, props, brush texture, shadows, or background atmosphere outside the ring. The output must be a valid PNG with real alpha channel, not a solid-color canvas with a circular mask. Do not render a checkerboard pattern in the outer area — a checkerboard is a visual indicator used by image editors to display transparency, and must not appear as pixel content in the final image.
```

---

### Verbose Token Prompt — Self-Contained

Use when the prompt will be sent to an external AI without access to token rules.

**If a reference image is provided**, open with:
> *"Create a 1:1 square VTT token portrait based on the provided reference image."*

**If no reference image is provided**, open with:
> *"Create a 1:1 square VTT token portrait of the following creature."*

```
[OPENING LINE — see above]

TOKEN SUBJECT:
[CREATURE / NPC / MONSTER — name, type, species, key traits. If no reference, include coloration, distinctive anatomy, equipment, and personality.]

COMPOSITION:
Face-first close-up token portrait. The face, head, eyes, and most recognizable features must be the primary focal point. Use a tight close-up or head-and-shoulders bust framing rather than full-body art. The face should be large, sharp, and readable at small VTT size — aim for the face to occupy 55–75% of the token's visual attention.

The token should use a dynamic layered composition where selected parts of the subject intentionally extend beyond the circular border for a premium, dimensional look. This border-break effect is required, not optional. Use horns, crests, ears, snout, mandibles, wings, claws, weapon tips, shoulders, cloak edges, armor spikes, or tail tips to overlap and break the frame edge.

The face must remain mostly inside the circle, fully readable, and clearly dominant as the focal point. Breakout elements must enhance the silhouette without obscuring the eyes or expression. The token should feel like the creature is pushing out of the frame — not like a flat photo simply cropped into a circle.

TOKEN FRAME:
Bold circular fantasy token frame with a polished [FRAME COLOR] beveled rim. The circular border must remain clearly visible and recognizable, even where the subject overlaps it. The border should feel like a physical token rim, not a flat ring or UI overlay.

SUBJECT IDENTITY:
[IF REFERENCE PROVIDED:] Match the subject's species, face shape, coloration, distinctive markings, expressive features, silhouette, and any armor, clothing, or equipment shown in the reference image. If the reference is full-body or wide scene art, extract the face design and rebuild the subject as a close-up token portrait. Do not preserve the original framing — reinterpret as a face-first token.
[IF NO REFERENCE:] Render the subject from the description above. Use genre-appropriate anatomy, species traits, coloration, and equipment. Do not invent traits not described — when in doubt, use the most iconic version of this creature type.

AESTHETIC STYLE:
[FULL AESTHETIC STYLE DESCRIPTION]

BACKGROUND:
Simple atmospheric backdrop: [TOKEN BACKDROP from environment]. Keep the background subdued, softly blurred or painterly, and lower contrast than the subject's face. No tactical map, no grid, no full environmental scene, no clutter. The background exists only to support the portrait. Only the interior of the circular frame contains background detail — the area outside the circle must be fully true transparent (alpha = 0).

LIGHTING:
Dramatic but readable portrait lighting from slightly above and to one side. Highlight the face, eyes, and defining features clearly. Use subtle rim light on silhouette edges, horns, scales, fur, armor, and wet surfaces. Avoid crushed black shadows over the face. Avoid blown highlights on the frame or forehead. Eyes must remain readable. Exception: arcane, elemental, undead, infernal, or bioluminescent subjects may use a matching internal or environmental light source as the primary key light.

RESTRICTIONS:
- No text, labels, UI, nameplates, numbers, captions, watermarks, or readable writing of any kind.
- No status icons, condition markers, or token overlays.
- No full tactical map backgrounds, no grid, no coordinates.
- No multiple main subjects unless explicitly requested.
- No full-body composition unless explicitly requested.
- Only the interior of the circular frame carries image content — the area outside the circle must be fully true transparent (alpha = 0). The output must be a valid PNG with real alpha channel, not a solid-color canvas with a mask.
- Do not render a checkerboard pattern outside the circular frame. A checkerboard is how image editing software *displays* transparent areas — it is not a rendering target. The correct output has no pixel content at all outside the token and subject breakout: no color, no pattern, no texture, zero opacity.

STYLE QUALITY:
High-quality fantasy portrait rendering. Polished professional finish. Strong material detail. Readable facial structure. Expressive eyes. Clear recognizable silhouette. Premium layered token presentation.
```

---

## Token Restrictions

Do not render any of the following unless explicitly requested:

- Text, labels, names, numbers, UI badges with letters, captions, watermarks, or readable writing.
- Token status icons (bloodied, stunned, etc.).
- Condition markers or overlay graphics.
- Full tactical map backgrounds.
- Grid lines or coordinates.
- Multiple main subjects (group token).
- Excessively small faces.
- Full-body character art when a face-first token is requested.
- Non-transparent outer area — the region outside the circular frame must be alpha = 0, not a solid color, fill, canvas background, or checkerboard pattern. A checkerboard is how editors display transparency; it must not appear as rendered pixel content.

---

## Token Quality Checklist

Before producing a token prompt, verify:

- [ ] Output is 1:1 square
- [ ] Token uses a circular frame unless the user requested otherwise
- [ ] Composition variant selected intentionally (Face-Focused Bust / Creature Head / Hero Bust / Full Silhouette) and appropriate for subject type
- [ ] Face/head is the main focal point
- [ ] Face is large enough to read at small VTT scale
- [ ] Eyes/expression or equivalent creature focal feature are readable
- [ ] Subject identity matches the reference image (or description if no reference provided)
- [ ] Silhouette is strong and recognizable
- [ ] The subject visibly overlaps and breaks the circular border in a controlled, intentional way
- [ ] The token feels dimensional and premium, not like a flat image simply cropped into a circle
- [ ] Breakout elements do not obscure the face or expression
- [ ] Background is simple, atmospheric, and does not compete with the subject
- [ ] Environment backdrop selected (or fallback to Env 2 if unspecified)
- [ ] No text, labels, UI, numbers, nameplates, icons, captions, or readable writing
- [ ] No tactical map, grid, or coordinates in the background
- [ ] No full-body framing unless explicitly requested
- [ ] No multiple main subjects unless explicitly requested
- [ ] Frame color matches user request (default red); any named color accepted
- [ ] Area outside the circular frame is fully true transparent (alpha = 0) — no checkerboard pattern, no gray/white/black fill, no color bleed from the background — the outer area is completely empty pixel content; the token is a valid PNG with real alpha channel, not a solid-color canvas with a mask
- [ ] Prompt opening line matches whether a reference image was provided or not
