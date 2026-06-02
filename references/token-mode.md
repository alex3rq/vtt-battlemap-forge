---
name: token-mode
description: Token Mode for VTT Battlemap Forge. Creates VTT-ready creature, monster, NPC, and character token images. Four token types — Portrait/Pog (circular framed face-first bust, default), Top-Down (bird's-eye overhead view), Isometric/Standee (2.5D upright standee), Frameless Portrait (bust with no border ring, soft vignette). Not a battlemap mode and not a cinematic scene-art mode. Load only when Token mode is active.
---

# Token Mode

Token Mode creates VTT-ready creature, monster, NPC, or character tokens. It is not a top-down battlemap mode and not a cinematic scene-art mode. Output is an image-generation prompt for a 1:1 square token portrait.

Token Mode is inherently creature-focused — there is no DM variant. The token itself IS the creature, NPC, or monster.

---

## Token Type

Select the token type based on the user's request. **Default is Portrait/Pog.**

| Type | Description | Default use case |
|---|---|---|
| **Portrait / Pog** *(default)* | Circular framed face-first bust. Bold beveled rim. Intentional border breakout. Subject anatomy and gear extend beyond the ring. | All creatures, NPCs, monsters, and player characters. General-purpose VTT default. |
| **Top-Down** | Bird's-eye overhead view. Subject rendered from directly above. Sihouette-first. No circular frame — uses soft vignette or shadow base. Facing direction is visible. | Tactical immersion. Grids where directional facing matters (backstab mechanics). Seamless blending with top-down battlemaps. |
| **Isometric / Standee** | 2.5D angled perspective. Subject stands upright on a flat base plate, viewed from a 45° elevated side angle. Mimics a physical standee or miniature. | Isometric battlemaps only. Players who prefer a physical tabletop aesthetic. Not recommended for top-down maps. |
| **Frameless Portrait** | Same face-first bust composition as Portrait/Pog but with no circular border ring. Separation from background achieved through soft vignette, painterly edge blur, or subtle shadow. | Foundry VTT users who prefer the borderless look. Modern digital tabletop aesthetic. |

### Token Type Triggers

| Type | User triggers |
|---|---|
| Portrait / Pog | *(no trigger — default)*, "portrait token", "pog token", "circular token", "with frame", "with border", "framed token" |
| Top-Down | "top-down token", "top down", "overhead token", "bird's eye token", "overhead view", "facing direction", "tactical token", "viewed from above", "overhead portrait" |
| Isometric / Standee | "isometric token", "standee", "standee token", "iso token", "2.5D token", "miniature token", "mini token", "standing token" |
| Frameless Portrait | "frameless", "no frame", "no border", "borderless", "borderless token", "no rim", "without frame", "without border", "soft portrait" |

### Isometric / Standee Warning

When generating an Isometric/Standee token, include this note to the user alongside the prompt:

> **Note:** Isometric standee tokens are designed for isometric battlemaps. On a standard top-down VTT map, they will appear as if the character is lying flat on the ground — this is a perspective mismatch inherent to the format, not an error.

---

## Default Token Style — Portrait / Pog

Unless the user requests otherwise, tokens follow this default presentation:

- 1:1 square format
- Circular fantasy token frame
- Bold red beveled rim
- Face-first composition
- Premium layered look
- Intentional border breakout
- Simple atmospheric background with uniform, low-variance color for easy background removal
- Strong readability at small VTT size
- No text, labels, UI, or status markers

The intended look is a premium tabletop token where the subject feels alive and dimensional, with selected anatomy or gear extending beyond the circular frame while the face remains the main focal point.

---

## Token Priorities

Every token must prioritize, in order:

1. Subject readability at small VTT scale (face for Portrait/Frameless; silhouette for Top-Down; full body for Isometric)
2. Strong creature/NPC identity
3. Clear recognizable silhouette
4. Token type presentation applied correctly and intentionally
5. Style consistency with the selected aesthetic
6. Clean separation from the background
7. No text, labels, UI, or nameplates

---

## Composition Rules

All token types use a square 1:1 image. Composition rules vary by token type — apply the rules for the selected type.

---

### Portrait / Pog — Composition Rules

- Circular framed token with a bold red beveled rim (or user-specified color).
- The face, head, or creature's main identifying feature must be the focal point.
- Frame the subject as a close-up portrait, head-and-shoulders bust, or tight creature portrait.
- The face should occupy most of the inner circle, around 55–75% of the token's visual attention.
- Eyes, expression, snout, teeth, horns, crest, or facial markings should be sharp and readable.
- Do not default to full-body framing unless the creature's whole silhouette is essential.
- Tokens should use a dynamic premium composition where selected anatomy or gear visibly extends beyond the circular border. This border-breaking presentation is preferred by default, not optional.
- The token should feel dimensional and layered, not like a flat portrait cropped into a circle.

Face-first, not face-only: the face is the primary focal point, but secondary elements outside the circle add drama and identity — especially when they help create a strong border-break effect.

Subject emphasis:
- Humanoids: face, shoulders, upper chest, and one or two iconic silhouette elements.
- Monsters and beasts: head and recognizable anatomy, with wings, horns, claws, ears, crests, tails, mandibles, or weapon tips extending beyond the frame.
- Wide or flying creatures: partial bust-plus-silhouette, face remaining dominant.

---

### Frameless Portrait — Composition Rules

- No circular border ring and no beveled rim.
- Same face-first bust or creature head framing as Portrait/Pog.
- Subject separation from background achieved through soft painterly vignette, edge blur, or subtle cast shadow — not a hard crop or frame.
- Border breakout does not apply — the subject blends naturally into the edges.
- Background should be kept simple, atmospheric, and softly bokeh'd so the vignette reads cleanly.
- The background area at the image corners and edges should fade to near-black or a dark, uniform tone to enable clean background removal if the user desires it.
- No frame color selection needed. Skip frame color step.

---

### Top-Down — Composition Rules

- No circular frame. No beveled rim.
- Camera angle is strict overhead / bird's-eye: subject rendered from directly above, looking straight down.
- Composition shows head (or top of head), shoulders, back, weapons, and distinctive anatomy — nothing is in perspective.
- The creature's facing direction must be clearly readable from the silhouette. Head, snout, beak, or weapon tip should indicate which way the creature faces.
- Full body is acceptable — this is the expected framing for this type.
- Soft drop shadow or subtle base ring below the subject to separate it from the background and ground the token on the map.
- Background: solid black or very dark near-black. High contrast with the subject. Uniform enough for easy background removal using selection tools.
- No circular frame. The silhouette IS the token shape.
- Border breakout does not apply.

---

### Isometric / Standee — Composition Rules

- Camera angle is 2.5D isometric: subject viewed from approximately 45° elevation and 45° side angle, standing upright.
- Full body visible: head, torso, legs, feet, and any held weapons or props.
- Subject stands on a flat oval or elliptical base plate (standard standee base).
- The base plate color should complement the aesthetic style — stone gray, dark wood, dark metal, or environment-matched surface.
- Expression and face still visible and readable where possible, but full silhouette and posture take priority over the face.
- No circular frame. No beveled rim.
- Background: solid black or very dark near-black. Uniform enough for easy background removal.
- Border breakout does not apply.

---

## Composition Variants

**Applies to Portrait / Pog and Frameless Portrait only.** Top-Down and Isometric/Standee always use full-body or silhouette framing and do not use these variants.

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
- Controlled border breakout allowed (Portrait/Pog); soft vignette edge (Frameless).

### Creature Head Token

- Best for beasts, dragons, aberrations, insects, reptiles, and monsters with distinctive anatomy.
- Focus almost entirely on head, jaws, eyes, horns, crest, mandibles, or snout.
- Minimal torso or no torso.
- Strong border breakout from anatomy (Portrait/Pog); soft vignette at anatomy edges (Frameless).

### Hero Bust Token

- Best for humanoid NPCs, villains, and player characters.
- Face, shoulders, upper torso, cloak/armor, and one identity prop (weapon, staff, shield).
- More composed and heroic than Creature Head.
- Border breakout from shoulders, cloak, or weapon (Portrait/Pog); soft vignette (Frameless).

### Full Silhouette Token

- Use only when explicitly requested or when the variant table indicates it.
- Best for tiny creatures, flying creatures, or monsters whose entire body shape is the main identifier.
- Still keep the face readable if the creature has one.
- Border breakout from wings, tail, or full body extensions (Portrait/Pog); soft vignette (Frameless).

---

## Border Breakout Rule

**Applies to Portrait / Pog only.** Top-Down, Isometric/Standee, and Frameless Portrait do not use a circular frame and therefore do not use border breakout.

Use controlled border breakout by default for Portrait/Pog tokens.

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

**Applies to Portrait / Pog only.** Top-Down, Isometric/Standee, and Frameless Portrait do not use a circular frame. Skip frame color and frame style selection for those types.

### Frame Color

Default frame is a bold red beveled rim. Accept alternative frame colors when the user specifies them.

| Frame Color | User Triggers |
|---|---|
| **Red** *(default)* | (no trigger needed) |
| Gold | "gold frame", "gold rim", "golden border" |
| Silver | "silver frame", "silver rim", "silver border" |
| Black | "black frame", "black rim", "dark border" |
| Any other named color | Apply that color directly as a polished beveled rim (e.g. "blue frame", "purple rim", "arcane violet border") |

### Frame Style

Default frame style is a bold circular fantasy token frame with a polished beveled rim, similar to a premium VTT monster token. The frame should feel like a physical token rim — not a flat ring and not a UI overlay.

---

## Background Rules

Token backgrounds should be simple and atmospheric. Use the environment preset to determine the backdrop for Portrait/Pog and Frameless Portrait tokens. Top-Down and Isometric/Standee use a solid dark background regardless of environment — see type-specific rules below.

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

### Portrait / Pog — Background

- Keep the background lower contrast than the face.
- Use a soft blurred or painterly backdrop — not a full scene.
- Match the creature's known environment when possible.
- Avoid busy scene details that compete with the portrait.
- The backdrop must remain inside the circular frame. No background content, fog, blur, or paint strokes outside the circular rim.
- No full battle scene, no tactical map, no grid, no UI, no labels.

### Frameless Portrait — Background

- Use the same environment backdrop table as Portrait/Pog.
- The background should be kept simple and softly bokeh'd.
- The background must fade to a dark, uniform tone at all image edges (near-black preferred). This creates a natural vignette that both separates the subject and enables clean background removal if needed.
- Avoid complex or high-contrast scene details at the image edges.

### Top-Down — Background

- Use solid black or very dark near-black (hex #0a0a0a or equivalent). No atmospheric scene.
- The uniform dark background enables magic wand / selection-based background removal with no color contamination.
- A subtle soft drop shadow or faint radial shadow below the subject is allowed to ground the token.

### Isometric / Standee — Background

- Use solid black or very dark near-black. No atmospheric scene behind the subject.
- The base plate beneath the subject's feet may carry a subtle environment-matched texture (stone tile, dark soil, etc.) but must fade to near-black at the edges.
- Uniform dark edges enable clean background removal.

---

## Background Removal — Post-Process Note

Image generation models do not produce true transparent PNG alpha channels. The prompts in this skill are written to maximize background simplicity and uniformity, which makes background removal as easy as possible in post. After generating a token, use one of the following approaches:

- **Remove.bg, Adobe Express, or Canva Background Remover** — automated one-click removal; works best on Portrait/Pog tokens with the circular frame as a clear boundary.
- **VTT importer with built-in background removal** — Foundry VTT and some Roll20 modules include background removal on token import.
- **Magic wand / fuzzy select** — for Top-Down and Isometric tokens with solid black backgrounds, select the black area and delete; the uniform background makes this reliable.
- **Token Stamp 2 (tokenstamp2.co)** — free tool that accepts an image and applies a circular frame with configurable border; eliminates the need for manual background removal for Portrait/Pog tokens.

Do not prompt the image AI to produce a checkerboard pattern — a checkerboard is how image editors *display* transparent areas. If one appears in the output, it means the AI rendered the display artifact as image content; remove it in post the same way as a white or black background.

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

The final generated image must be an exact 1:1 square. Do not create a wide, landscape, or rectangular image of any kind.

### Portrait / Pog

Center one circular fantasy token inside the square canvas. The circular frame should fill most of the square, leaving only minimal padding around the outermost subject breakout elements. The area outside the circular frame must be fully transparent (alpha = 0) — only the subject's breakout elements (horns, wings, claws, shoulders, etc.) may appear outside the rim. No solid fill, no black background, no white background, no gray background, no checkerboard pattern outside the ring.

### Frameless Portrait

Fill the full square canvas with the subject portrait. The subject should be centered and dominant. Background fades to near-black at all four edges via a natural painterly vignette.

### Top-Down

Fill the full square canvas. Subject centered. Background is solid black or near-black. Soft drop shadow below the subject is allowed.

### Isometric / Standee

Fill the full square canvas. Subject standing upright on an oval base plate, centered horizontally, positioned in the lower two-thirds of the canvas to allow headroom. Background is solid black or near-black.

---

## Token Prompt Templates

### Output Rule

Return only the final prompt inside a **code block**. Output nothing else unless the user asks for explanation.

**Default: Compact Token Prompt.** Use Verbose Token Prompt only if the user explicitly asks for a full, verbose, or self-contained prompt.

For Isometric/Standee tokens, append the standee warning note after the code block.

---

### Compact Token Prompt — Portrait / Pog

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
Use a bold circular fantasy token frame with a polished [FRAME COLOR] beveled rim. The subject MUST intentionally break and overlap the circular border — this border-breaking effect is required, not optional. The token must feel dimensional and layered, not like a flat portrait cropped inside a circle. The creature must feel like it is pushing out of the frame. Use horns, crests, ears, snout, mandibles, wings, claws, weapon tips, shoulders, cloak edges, armor spikes, or tail tips extending visibly beyond the rim. Keep the face mostly inside the circle, fully readable, and visually dominant. Background elements must stay completely inside the circular frame.

Subject Identity:
[IF REFERENCE PROVIDED:] Match the subject's identity, species, coloration, silhouette, armor/clothing, visible equipment, weapons, props, and distinctive features from the reference image. Do not invent or redesign equipment, weapons, armor, accessories, anatomy, or props not present in the reference image.
[IF NO REFERENCE:] Render the subject based on the description above. Use genre-appropriate anatomy, coloration, and equipment typical of the subject's type.

Aesthetic Style:
[SELECTED AESTHETIC STYLE DESCRIPTION]

Background:
Simple atmospheric backdrop inside the circular frame only: [TOKEN BACKDROP from environment]. Keep it subdued, softly blurred, and lower contrast than the face. No tactical map, no grid, no full scene, no clutter. The area outside the circular frame must be fully transparent (alpha = 0) — no black fill, no white fill, no gray fill, no checkerboard pattern. Only the subject's breakout elements (horns, wings, claws, etc.) may appear outside the circular rim.

Lighting:
Dramatic but readable portrait lighting. Highlight the face, eyes, and defining features. Use subtle rim light on silhouette edges, horns, scales, fur, armor, or wet surfaces. Avoid crushed black shadows over the face and avoid overbright highlights.

Restrictions:
No text, labels, UI, nameplates, numbers, captions, watermarks, status icons, tactical map, grid, or readable writing. No fog, scenery, props, brush texture, shadows, or background atmosphere outside the circular frame. The area outside the ring must be fully transparent — subject breakout elements only, nothing else.
```

---

### Compact Token Prompt — Frameless Portrait

**If a reference image is provided**, open with:
> *"Create a 1:1 square VTT frameless token portrait from the provided reference image."*

**If no reference image is provided**, open with:
> *"Create a 1:1 square VTT frameless token portrait of the following creature."*

```
[OPENING LINE — see above]

Token Subject:
[CREATURE / NPC / MONSTER NAME OR TYPE — include key visual traits if no reference image]

Composition:
Use a face-first close-up composition: face, head, eyes, expression, and most recognizable features as the clear focal point. Head-and-shoulders bust or tight creature portrait. No circular frame or border ring — the subject blends naturally into the background through a soft painterly vignette at the edges.

Subject Identity:
[IF REFERENCE PROVIDED:] Match the subject's identity, species, coloration, silhouette, armor/clothing, visible equipment, weapons, props, and distinctive features from the reference image.
[IF NO REFERENCE:] Render the subject based on the description above. Use genre-appropriate anatomy, coloration, and equipment.

Aesthetic Style:
[SELECTED AESTHETIC STYLE DESCRIPTION]

Background:
Simple atmospheric backdrop: [TOKEN BACKDROP from environment]. Keep it subdued, softly blurred or painterly, and lower contrast than the face. The background must fade to near-black or solid black at all four image edges via a natural vignette — no sharp crop, no frame, no border ring. Dark uniform edges enable clean background removal.

Lighting:
Dramatic but readable portrait lighting. Highlight the face, eyes, and defining features. Subtle rim light on silhouette edges. Avoid crushed shadows over the face and overbright highlights.

Restrictions:
No circular frame. No border ring or beveled rim. No text, labels, UI, nameplates, numbers, captions, watermarks, status icons, tactical map, or grid. No white background, no checkerboard pattern.
```

---

### Compact Token Prompt — Top-Down

**If a reference image is provided**, open with:
> *"Create a 1:1 square VTT top-down overhead token from the provided reference image."*

**If no reference image is provided**, open with:
> *"Create a 1:1 square VTT top-down overhead token of the following creature."*

```
[OPENING LINE — see above]

Token Subject:
[CREATURE / NPC / MONSTER NAME OR TYPE — include key visual traits if no reference image]

Composition:
Strict overhead bird's-eye view — camera is directly above the subject, looking straight down. Show the head (or top of skull), shoulders, back, any held weapons, wings, tail, or distinctive anatomy as seen from above. The creature's facing direction must be clearly readable from the silhouette — head, snout, beak, or weapon tip indicates which way the subject faces. Full-body silhouette is expected and correct for this type.

Subject Identity:
[IF REFERENCE PROVIDED:] Match the subject's species, coloration, anatomy, armor, weapons, and distinctive features from the reference. Reinterpret all visible anatomy into the overhead perspective.
[IF NO REFERENCE:] Render the subject based on the description above. Use the most iconic top-down anatomy for this creature type.

Aesthetic Style:
[SELECTED AESTHETIC STYLE DESCRIPTION]

Background:
Solid black or near-black (#0a0a0a). No atmospheric scene. No environmental props. A subtle soft drop shadow or radial shadow directly below the subject is allowed. Uniform dark background enables clean background removal.

Lighting:
Overhead ambient lighting consistent with the aesthetic style. Keep the subject readable and well-defined from above. Rim highlights on armor, scales, fur, or silhouette edges. Avoid deep shadow pools that hide the silhouette shape.

Restrictions:
No circular frame. No border ring. No text, labels, UI, nameplates, numbers, captions, watermarks, status icons, tactical map, grid, or readable writing. No white, gray, or patterned background fill — background must be solid dark. No perspective distortion — camera is strictly overhead.
```

---

### Compact Token Prompt — Isometric / Standee

**If a reference image is provided**, open with:
> *"Create a 1:1 square VTT isometric standee token from the provided reference image."*

**If no reference image is provided**, open with:
> *"Create a 1:1 square VTT isometric standee token of the following creature."*

```
[OPENING LINE — see above]

Token Subject:
[CREATURE / NPC / MONSTER NAME OR TYPE — include key visual traits if no reference image]

Composition:
2.5D isometric perspective: subject viewed from approximately 45° elevation and 45° side angle, standing fully upright. Full body visible — head, torso, legs, feet, and any held weapons or props. The subject stands on a flat oval base plate. Center the subject horizontally, positioned in the lower two-thirds of the canvas to allow headroom. Full-body posture and silhouette take priority; show the character's attitude, equipment, and bearing.

Subject Identity:
[IF REFERENCE PROVIDED:] Match the subject's species, coloration, anatomy, armor, weapons, and distinctive features. Reinterpret full anatomy into the isometric standing pose.
[IF NO REFERENCE:] Render the subject based on the description above. Use genre-appropriate anatomy, equipment, and posture.

Aesthetic Style:
[SELECTED AESTHETIC STYLE DESCRIPTION]

Base Plate:
Flat oval or elliptical base beneath the subject's feet. Color: [dark stone / dark wood / dark metal — match environment and aesthetic]. Fades to near-black at its edges.

Background:
Solid black or near-black. No atmospheric scene behind the subject. Uniform dark background enables clean background removal.

Lighting:
Isometric portrait lighting: key light from the upper-left (matching standard isometric convention), fill light from the right to avoid crushed shadows. Highlight the face, silhouette edges, armor, and weapons. Readable from the isometric angle.

Restrictions:
No circular frame. No border ring. No text, labels, UI, nameplates, numbers, captions, watermarks, status icons, tactical map, grid, or readable writing. No white, gray, or patterned background fill — background must be solid dark. Maintain consistent isometric perspective throughout — no mixed camera angles.
```

---

### Verbose Token Prompt — Self-Contained

Use when the prompt will be sent to an external AI without access to token rules. Select the appropriate opening line and composition block for the active token type.

**Opening lines by type and reference image:**

| Type | No reference | With reference |
|---|---|---|
| Portrait / Pog | "Create a 1:1 square VTT token portrait of the following creature." | "Create a 1:1 square VTT token portrait based on the provided reference image." |
| Frameless Portrait | "Create a 1:1 square VTT frameless token portrait of the following creature." | "Create a 1:1 square VTT frameless token portrait based on the provided reference image." |
| Top-Down | "Create a 1:1 square VTT top-down overhead token of the following creature." | "Create a 1:1 square VTT top-down overhead token based on the provided reference image." |
| Isometric / Standee | "Create a 1:1 square VTT isometric standee token of the following creature." | "Create a 1:1 square VTT isometric standee token based on the provided reference image." |

```
[OPENING LINE — see table above]

TOKEN SUBJECT:
[CREATURE / NPC / MONSTER — name, type, species, key traits. If no reference, include coloration, distinctive anatomy, equipment, and personality.]

COMPOSITION:
[INSERT COMPOSITION BLOCK FOR ACTIVE TYPE — see below]

TOKEN FRAME / PRESENTATION:
[Portrait/Pog:] Bold circular fantasy token frame with a polished [FRAME COLOR] beveled rim. The circular border must remain clearly visible and recognizable, even where the subject overlaps it. The border should feel like a physical token rim, not a flat ring or UI overlay. Selected anatomy or gear extends beyond the frame for a dimensional, premium look.
[Frameless Portrait:] No circular frame or border ring. Subject blends into the background through a soft painterly vignette. Background fades to near-black at all edges.
[Top-Down:] No frame. Subject silhouette-only presentation on a solid dark background. Subtle drop shadow allowed.
[Isometric / Standee:] No frame. Subject on an oval base plate. Solid dark background.

SUBJECT IDENTITY:
[IF REFERENCE PROVIDED:] Match the subject's species, face shape, coloration, distinctive markings, expressive features, silhouette, and any armor, clothing, or equipment shown in the reference image. If the reference is full-body or wide scene art, extract the face design and rebuild the subject as a close-up token portrait. Do not preserve the original framing — reinterpret as specified by the token type.
[IF NO REFERENCE:] Render the subject from the description above. Use genre-appropriate anatomy, species traits, coloration, and equipment. Do not invent traits not described — when in doubt, use the most iconic version of this creature type.

AESTHETIC STYLE:
[FULL AESTHETIC STYLE DESCRIPTION]

BACKGROUND:
[Portrait/Pog:] Simple atmospheric backdrop inside the circular frame only: [TOKEN BACKDROP from environment]. Subdued, softly blurred or painterly, lower contrast than the face. Outside the circular frame: fully transparent (alpha = 0) — subject breakout elements only, no scene content, no fog, no texture, no fill of any color.
[Frameless Portrait:] Simple atmospheric backdrop: [TOKEN BACKDROP from environment]. Subdued and painterly. Fades to near-black at all four image edges via a natural vignette.
[Top-Down / Isometric:] Solid black or near-black. No atmospheric scene. Drop shadow or base plate as specified.

LIGHTING:
[Portrait/Pog / Frameless:] Dramatic but readable portrait lighting from slightly above and to one side. Highlight the face, eyes, and defining features clearly. Subtle rim light on silhouette edges, horns, scales, fur, armor, and wet surfaces. Avoid crushed black shadows over the face. Eyes must remain readable. Exception: arcane, elemental, undead, infernal, or bioluminescent subjects may use a matching internal or environmental light source as the primary key light.
[Top-Down:] Overhead ambient lighting. Rim highlights on armor, scales, fur, or silhouette edges. Subject must remain clearly readable from above.
[Isometric:] Key light from upper-left (isometric convention), fill from the right. Highlight face, silhouette edges, armor, weapons. Readable from isometric angle.

RESTRICTIONS:
- No text, labels, UI, nameplates, numbers, captions, watermarks, or readable writing of any kind.
- No status icons, condition markers, or token overlays.
- No full tactical map backgrounds, no grid, no coordinates.
- No multiple main subjects unless explicitly requested.
- [Portrait/Pog:] The area outside the circular frame must be fully transparent (alpha = 0). Only subject breakout elements (horns, wings, claws, etc.) may appear outside the rim. No black, white, gray, or patterned fill. No checkerboard pattern. No scene content outside the ring.
- [All other types:] Background must be solid black or near-black. No white, gray, or patterned fill. No checkerboard pattern.

STYLE QUALITY:
High-quality fantasy rendering. Polished professional finish. Strong material detail. Clear recognizable silhouette. [Portrait/Pog / Frameless:] Readable facial structure. Expressive eyes. [Top-Down:] Readable directional silhouette from overhead. [Isometric:] Full body attitude and posture readable from the isometric angle.
```

**Composition blocks by type — insert into COMPOSITION field above:**

*Portrait / Pog:*
```
Face-first close-up token portrait. The face, head, eyes, and most recognizable features must be the primary focal point. Use a tight close-up or head-and-shoulders bust framing rather than full-body art. The face should be large, sharp, and readable at small VTT size — aim for the face to occupy 55–75% of the token's visual attention. The token should use a dynamic layered composition where selected anatomy or gear intentionally extends beyond the circular border for a premium, dimensional look. This border-break effect is required, not optional. Use horns, crests, ears, snout, mandibles, wings, claws, weapon tips, shoulders, cloak edges, armor spikes, or tail tips to overlap and break the frame edge. The face must remain mostly inside the circle, fully readable, and clearly dominant.
```

*Frameless Portrait:*
```
Face-first close-up token portrait. The face, head, eyes, and most recognizable features are the primary focal point. Use a tight close-up or head-and-shoulders bust. No circular frame or border ring — the subject transitions into the background through a soft painterly vignette. No hard crop or frame edge. The face should be large, sharp, and readable at small VTT size.
```

*Top-Down:*
```
Strict overhead bird's-eye view — camera is directly above the subject looking straight down. Show the top of the head, shoulders, back, held weapons, wings, tail, or distinctive anatomy as viewed from directly above. The creature's facing direction must be clearly readable from the silhouette. Full-body overhead silhouette is the expected and correct composition for this type.
```

*Isometric / Standee:*
```
2.5D isometric perspective — subject viewed from approximately 45° elevation and 45° side angle, standing fully upright on an oval base plate. Full body visible: head, torso, legs, feet, and any held weapons or props. Centered horizontally, positioned in the lower two-thirds of the canvas to allow headroom. Full-body posture, silhouette, and equipment are the primary focus. Maintain consistent isometric perspective throughout.
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
- Excessively small faces (Portrait/Pog and Frameless Portrait).
- Full-body character art when a face-first token is requested (Portrait/Pog and Frameless Portrait).
- Any fill color outside the circular frame for Portrait/Pog tokens — the outer area must be fully transparent, not black, not white, not gray.
- Checkerboard patterns — a checkerboard is how editors display transparency; it must not appear as rendered pixel content.
- Contained breakout for Portrait/Pog — the subject MUST visibly break the circular border. A token where all anatomy fits neatly inside the circle is incorrect.

---

## Token Quality Checklist

Before producing a token prompt, verify:

- [ ] Output is 1:1 square
- [ ] Token type selected correctly (Portrait/Pog / Frameless Portrait / Top-Down / Isometric/Standee)
- [ ] Correct compact prompt template used for the selected type
- [ ] For Portrait/Pog: circular frame present, frame color matches user request (default red), border breakout explicitly required in prompt
- [ ] For Portrait/Pog: outer area specified as transparent (alpha = 0), not solid black or dark fill
- [ ] For Frameless Portrait: no frame, vignette edge, dark edges specified
- [ ] For Top-Down: overhead camera, facing direction readable from silhouette, solid dark background
- [ ] For Isometric/Standee: 2.5D perspective, oval base plate, full body, solid dark background; standee warning note appended after code block
- [ ] Composition variant selected (Portrait/Pog and Frameless Portrait only): Face-Focused Bust / Creature Head / Hero Bust / Full Silhouette
- [ ] Face/head is the main focal point (Portrait/Pog and Frameless); silhouette is primary for Top-Down and Isometric
- [ ] Subject identity matches the reference image (or description if no reference provided)
- [ ] Silhouette is strong and recognizable
- [ ] For Portrait/Pog: prompt uses imperative language — breakout is REQUIRED, not suggested
- [ ] Background is correct for type: atmospheric inside frame + transparent outside (Portrait/Pog), vignette to near-black (Frameless), solid dark (Top-Down / Isometric)
- [ ] Environment backdrop selected (or fallback to Env 2 if unspecified) for Portrait/Pog and Frameless Portrait
- [ ] No text, labels, UI, numbers, nameplates, icons, captions, or readable writing
- [ ] No tactical map, grid, or coordinates in the background
- [ ] Prompt opening line matches token type and whether a reference image was provided

