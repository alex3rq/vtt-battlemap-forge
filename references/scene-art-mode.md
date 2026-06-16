---
name: scene-art-mode
description: Scene Art Mode for VTT Battlemap Forge. Creates cinematic non-map image prompts — splash art, key art, scene illustrations, player handout art — based on the same environment, aesthetic style, and storytelling elements used for the VTT battlemap. Supports player variant (default, spoiler-free) and DM variant (creatures and spoilers visible, reference images accepted). Not a VTT map mode. Load only when Scene Art mode is active.
---

# Scene Art Mode

Scene Art Mode creates cinematic, image-generation prompts from the same environment, aesthetic style, and story context used for the VTT battlemap. Output is a polished image-generation prompt for a non-top-down scene illustration.

Scene Art Mode is **not** a VTT battlemap mode. Top-down perspective, grid rules, tactical readability rules, and layout-lock rules do not apply unless the user explicitly asks for a map-like image.

**Two variants:**
- **Player variant (default)** — spoiler-free, no creature reveals, focused on environmental atmosphere.
- **DM variant** — spoilers allowed, creatures and NPCs may be visible, accepts creature reference images.

Player-facing is always the default. Only switch to DM variant when the user explicitly requests it.

---

## Dimensions

Scene Art uses cinematic aspect ratios, not VTT map ratios.

| Format | Ratio | Use Case |
|---|---|---|
| Landscape | 16:9 | **Default.** Cinematic key art, establishing shots, wide scene illustrations |
| Tall Landscape | 4:3 | Wide environmental shots, multi-character group scenes |
| Portrait | 2:3 | Player handout art intended to be printed or shown vertically |
| Square | 1:1 | Landmark or character focus; social-use art |

**Default: 16:9** unless the user specifies otherwise or the moment clearly calls for portrait (e.g., "player handout," "printed card art," "vertical format").

---

### When to skip suggestions

Output the final prompt directly (skip suggestion step) if:
- The user already named a specific moment or scene.
- The user explicitly asks to skip suggestions ("just make the prompt," "go straight to prompt").
- The source description contains only one obvious cinematic moment.

### Default flow (both variants)

1. Analyze the map description, room notes, environment preset, inhabitants, hazards, landmarks, and implied story.
2. Suggest 3–6 possible scene-art moments appropriate to the active variant.
3. Keep player-variant suggestions brief and spoiler-free. DM-variant suggestions may include creature reveals and encounter moments.
4. Ask the user to choose one.
5. After the user chooses, check for creature reference images (DM variant only — see Creature Reference Images section).
6. Output the final Scene Art Prompt for the chosen variant.

### DM variant triggers

Activate DM variant when the user says: "DM version," "for the DM," "show the creature," "creature reveal," "monster in the scene," "DM facing," "GM art," "the moment [monster] appears," or similar.

---

## Creature Reference Images (DM Variant)

When DM variant is active and the chosen moment includes a specific creature or NPC:

**Ask for reference images when:**
- The creature is a named NPC, campaign-specific boss, or custom monster with a unique design.
- The user mentions a specific creature appearance they care about matching.
- The moment is a key story beat where creature likeness significantly affects the art quality.

**Do not ask when:**
- The creature is a common archetype (goblin, orc, skeleton, dragon type) — use standard fantasy depiction.
- The user has not described any specific visual traits.
- The scene focuses mainly on environment with a creature only partially visible.

**How to ask (one-line, non-blocking):**
> "Do you have a reference image for [creature name]? It'll help match their appearance — or I can proceed with a standard [archetype] design."

**If reference images are provided:**
- Include in the prompt's creature description: match silhouette, color, key features, distinctive elements.
- Note in the prompt: "Match creature appearance to the provided reference image."

**If no reference is provided:**
- Describe creature by type, archetype, coloring, and key distinguishing traits based on what the user has described.
- Never block output. Proceed with best available description.

---

## Map Reference Image

A previously generated battlemap image can be attached to Scene Art requests. This is a **spatial and atmospheric reference** — not a layout lock. The AI uses it to ground the cinematic composition in the actual generated space.

### What to extract from a map reference image

- **Palette and material feel** — exact colors, surface textures, and material language used in the generated map. Match these in the cinematic art for visual continuity.
- **Lighting character** — direction, color temperature, shadow behavior already established in the map.
- **Zone locations** — if a zone label was provided (see Zone Context below), visually locate that zone within the map to understand its spatial position, size, and connections to adjacent areas.
- **Environmental details** — specific props, architectural features, or terrain elements visible in the map that should appear in the cinematic scene.
- **Edge connections** — what's visible at the zone's borders; corridors, doorways, or open spaces that suggest depth at the frame edges.

### What NOT to do with a map reference image in Scene Art

- Do not reproduce the top-down view.
- Do not treat it as a layout lock — the cinematic composition is independent.
- Do not use it to constrain the camera angle to match the map's orthographic perspective.

### If map reference image provided

In the final prompt, add a Reference Image note:

```
Reference Image:
A battlemap of this location is provided. Use it to match: color palette, material textures, lighting character, and the spatial feel of the zone. Do not reproduce the top-down view — use it as visual grounding for the cinematic composition only.
[If zone label provided: Focus on the [ZONE LABEL] area of the map.]
```

---

## Zone Context Input

When requesting Scene Art for a specific zone of a larger map, the user can provide:
- **Zone label** — e.g., "E2" — identifies which area the scene focuses on.
- **Zone description** — the text prompt or area dressing notes used for that zone.
- **Adjacent zone descriptions** (optional) — descriptions of neighboring zones for edge composition and environmental continuity.

### How zone context is used

Zone context is **processed internally** to enrich the prompt's content — it is not output raw into the final image prompt. Use it to:

- **Environment field** — replace generic biome description with zone-exact materials, props, and atmosphere from the zone description.
- **Key Visual Elements** — pull specific named props and landmark features from the zone description instead of generating generic ones.
- **Camera and Composition** — inform edge framing with spatial connections: if zone E2 connects to a flooded corridor east and a guard post north, the camera can be positioned to show a glimpse of those spaces at the frame edges.
- **Lighting** — if the zone description specifies a lighting condition different from the environment default, use it.

### Threshold moments (improvement suggestion)

When adjacent zone descriptions are provided, suggest "threshold moments" as additional scene-art options: the view from inside the target zone looking toward an adjacent area, showing the connection between spaces. These are compositionally strong for cinematic art and help establish the dungeon's geography visually.

Example: *The Passage to the Forge — looking from E2's flooded cells through a crumbling archway toward the heat-glow of the adjacent forge room, steam and orange light mixing at the threshold.*

### Zone context format (user input)

```
Zone: E2
Description: [area dressing notes or prompt text for this zone]
Adjacent zones (optional):
  North → [zone label and brief description]
  East  → [zone label and brief description]
```

---

```
Possible Scene Art Moments:

1. [Moment Name] — [short cinematic description, one sentence]
2. [Moment Name] — [short cinematic description, one sentence]
3. [Moment Name] — [short cinematic description, one sentence]
4. [Moment Name] — [short cinematic description, one sentence]

Which moment would you like? I'll turn it into a polished image prompt.
```

**Player variant:** Keep all descriptions spoiler-free. Focus on atmosphere, environment, and player-perceivable details. Do not reference hidden creatures, ambushes, or secret content.

**DM variant:** Suggestions may include creature reveals, ambush setups, encounter-start moments, and boss appearances. Include moments that would be spoilers for players.

Keep each description one sentence maximum. No tactical detail in either variant.

---

## Scene Art Prompt Template

When the user chooses a moment, output the final prompt in a code block.

This is the base template for both Player and DM variants. See DM Variant Modifications below for DM-specific changes.

```
Create a cinematic fantasy scene illustration based on this VTT battlemap location.[IF DM:  — DM version.]

Scene Focus:
[SELECTED MOMENT — describe the exact scene, framing, [IF DM: creature presence, and] implied action[IF DM:  or encounter beat]]

Dimensions:
[ASPECT RATIO — default 16:9 unless user specified otherwise. e.g., "16:9 landscape, 1920×1080"]

Environment:
[ENVIRONMENT DESCRIPTION — terrain, materials, palette, and mood. If zone description provided, use zone-specific details here instead of generic biome description.]

Aesthetic Style:
[STYLE DESCRIPTION — rendering approach, contrast character, palette, and finish from the selected aesthetic style]

Camera and Composition:
[CINEMATIC CAMERA ANGLE — see Camera Guide below. Include: viewpoint, framing, foreground / midground / background structure, depth cues, compositional device. If zone context provided, use spatial connections to inform edge framing.]

Lighting:
[ATMOSPHERIC LIGHTING — based on environment default, zone description, or user-specified lighting. Describe quality, direction, color temperature, and key shadow behavior.]

Mood:
[EMOTIONAL TONE — e.g., ominous, mysterious, sacred, abandoned, tense, awe-inspiring, melancholic, oppressive, tranquil, dread, wonder][IF DM: e.g., menacing, tense encounter, ominous reveal, dread, power, awe-inspiring threat, dramatic confrontation]

[IF DM VARIANT:
Creatures:
[CREATURE TYPE], [COUNT], [BEHAVIOR / STATE] — [brief visual description or reference image note]
[CREATURE TYPE], [COUNT], [BEHAVIOR / STATE] — [brief visual description or reference image note]

Creature rendering:
Render all creatures as illustrated figures consistent with the aesthetic style. Figures should feel physically present in the scene. No token circles, no floating overlays, no name labels.
[If creature reference images provided: Match creature appearance to the provided reference images.]
]

Key Visual Elements:
- [LANDMARK or TERRAIN FEATURE — most prominent element in frame. Use zone-specific features if zone description provided.]
- [PROP or ENVIRONMENTAL STORYTELLING DETAIL — narrative layer. Pull from zone description if available.]
- [IF DM: - [CREATURE POSITION or STAGING — how creatures relate to the environment]]
- [HAZARD, ATMOSPHERE, or TEXTURE ELEMENT — depth and danger cues]
- [BACKGROUND or DISTANT FEATURE — edge connection to adjacent zone if known, or general depth]

[If map reference image provided:]
Reference Image:
A battlemap of this location is provided. Use it to match: color palette, material textures, lighting character, and spatial feel of the zone. Do not reproduce the top-down view — use as visual grounding for the cinematic composition only.
[If zone label provided: Focus on the [ZONE LABEL] area of the map.]

[IF PLAYER VARIANT:]
Player-Facing Restrictions:
No visible text, labels, UI, maps, grid lines, captions, or readable writing.
No tactical top-down view.
No battlemap layout view.
No miniatures or token-like characters.
[Add spoiler restriction if applicable — see Spoiler Policy]

Character Policy:
[Choose one based on user request and context:]
- No characters. Focus entirely on the environment.
- Tiny distant silhouettes allowed only for scale. No identifiable faces or features.
- Adventurer silhouettes at mid or foreground only if the user requested characters.
- Visible creature only if the user explicitly requested a creature-forward scene.

[IF DM VARIANT:]
Scene Restrictions:
No visible text, labels, UI, maps, grid lines, captions, or readable writing.
No tactical top-down view. No battlemap layout view. No miniatures or token-like characters.

Style Quality:
High-quality fantasy key art. Immersive environmental storytelling.[IF DM:  Creatures feel dangerous and present.] Strong atmosphere. Polished professional illustration. [IF PLAYER: Coherent materials. Clear focal point.] Cinematic depth. [IF PLAYER: Visually readable composition.]
```

---

## DM Variant Modifications

When `dm_mode` is active, apply these changes to the base Scene Art Prompt Template above. The template already has `[IF DM VARIANT:]` markers at each modification point. The three major differences from the Player variant are:

1. **Spoiler restrictions removed.** The "Player-Facing Restrictions" block is replaced with "Scene Restrictions" (no spoiler restriction line). See Spoiler Policy below.
2. **Creatures section added** after the Mood field. Includes creature type, count, behavior, visual description, rendering rules, and optional reference image notes.
3. **Character Policy replaced.** Instead of the player-facing character policy options, creatures are rendered as specified in the Creatures section. No separate character policy block is needed.
4. **Key Visual Elements** gains a creature position/staging bullet point.
5. **Mood** examples shift to encounter-appropriate tones (menacing, tense encounter, dramatic confrontation).
6. **Opening line** appends " — DM version" to signal the variant.

All other fields (Scene Focus, Dimensions, Environment, Aesthetic Style, Camera, Lighting, Map Reference Image) remain identical to the Player variant.

---

## Camera Guide

Use these cinematic perspectives. Match to the selected moment.

| Camera Type | Best For |
|---|---|
| Low-angle establishing shot | Grand entrances, imposing chambers, boss arenas, cathedral-scale rooms |
| Eye-level corridor shot | Dungeon tunnels, cell blocks, flooded hallways — claustrophobia and tension |
| Over-the-shoulder view | Player-perspective reveal of a chamber, altar, or landmark |
| Doorway or arch reveal | First look into a new area; framing with portal silhouette |
| Wide environmental shot | Open outdoor encounters, canyon floors, ruined plazas, forest clearings |
| Dramatic interior view | Shrine rooms, ritual chambers, throne rooms — shows full scale |
| Close-up on landmark | Altar, arcane circle, ancient carving, cracked idol — narrative detail |
| Partially obscured foreground framing | Dense foliage, ruined masonry, fog — mystery and depth |
| Atmospheric silhouette shot | Adventurers or structures at distance; scale and vastness |

Avoid unless explicitly requested:
- Top-down orthographic view
- VTT grid or tactical layout visibility
- Full dungeon layout shown from above
- Labels, room numbers, UI, compass roses, coordinates
- Readable text in scene

---

## Key Moment Detection

### Player-variant moments (spoiler-free)

When generating player-facing suggestions, look for:

- **Main entrance reveal** — first view into the location from outside
- **First major chamber** — the moment a large space opens after a narrow approach
- **Landmark feature** — fountain, altar, bridge, throne, portal, collapsed statue, prison block, flooded hall, forge, ritual circle
- **Environmental hazard** — lava, flooding, poison vents, unstable ruins, abyssal cracks, visible traps
- **Biome transition** — where two environments meet (ruins emerging from jungle, ice forming over stone)
- **Evidence of inhabitants** — occupation shown through props, not creatures
- **Aftermath** — signs of a past battle, disaster, or event implied by the environment
- **Boss arena reveal** — dramatic space without necessarily showing the occupant
- **Quiet moment before danger** — eerie stillness, unsettling calm, tension before action
- **Player-scale detail** — a tactically important space viewed as a real place, not a map

### DM-variant moments (spoilers permitted)

In addition to all player-variant moments, also consider:

- **Creature reveal** — the moment the monster, beast, or villain becomes visible for the first time
- **Ambush setup** — creatures in hiding positions, ready to spring; the instant before the players know
- **Encounter start** — the first moment of confrontation; creatures and environment together at full tension
- **Boss entrance** — the villain, creature, or entity entering or filling their domain
- **Creature in environment** — the creature at rest or in natural behavior in their lair, before players arrive
- **Named NPC moment** — a specific NPC in a key story pose, interaction, or location
- **Villain's perspective** — the space from the antagonist's point of view, showing what they see or command
- **The trap sprung** — the moment a hazard or ambush activates, with the environment reacting

---

## Spoiler Policy

Scene Art Mode is **player-facing by default.**

Do not reveal:
- Hidden rooms or secret doors
- Concealed traps
- Invisible or hidden enemies
- Ambush monsters
- Puzzle solutions
- Treasure locations meant to be discovered later
- Boss or villain identity — unless the user explicitly asks for DM-facing art or chooses that moment

For hidden content, imply atmosphere instead of revealing the source:
- Strange scratches or disturbed surfaces
- Disturbed dust or ash
- Unnatural silence (implied by composition)
- Faint light leaking through cracks
- Ominous shadows with no visible source
- Broken or displaced objects
- Old bloodstains
- Unsettling environmental anomalies

If the user explicitly asks for **DM-facing art** → spoilers are permitted. Reveal what the DM knows.

---

## Scene Art Output Rules

**When suggesting moments:**
- Do not output a full image prompt yet.
- Output only the numbered suggestion list and the invitation to choose.

**When producing the final prompt:**
- Output only the completed prompt in a code block, unless the user asks for explanation.
- Preserve the selected aesthetic style and environment identity.
- Use cinematic visual language throughout.
- Do not include VTT grid or top-down map language.
- Keep it player-facing unless the user requests DM-facing.

---

## Scene Art Quality Checklist

Before outputting a final Scene Art Prompt, verify:

- [ ] Correct variant selected (Player / DM) — player is default
- [ ] Dimensions field included — default 16:9 unless overridden
- [ ] Scene focus is specific and cinematic — not a top-down layout description
- [ ] Environment description uses zone-specific details if zone description was provided; otherwise uses environment preset
- [ ] Style description comes from the selected aesthetic style
- [ ] Camera type is named and matched to the moment; edge framing informed by zone connections if available
- [ ] Lighting matches zone description, environment default, or user specification
- [ ] Mood is stated explicitly
- [ ] Key Visual Elements use zone-specific props and features where available
- [ ] Map reference image note included if map image was provided
- [ ] No spoilers beyond player-perceptible scene content (unless DM-facing requested)
- [ ] No grid, map layout, top-down view, labels, or UI language in prompt

**DM variant additions:**
- [ ] Creatures section present with type, count, behavior, and visual description
- [ ] Creature reference image note included if references were provided
- [ ] Creature rendering instruction included (no tokens, no labels)
