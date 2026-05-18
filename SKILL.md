---
name: vtt-battlemap-forge
description: Unified VTT battlemap assistant. Three modes — Prompt (convert description into image-generation prompt), Generation (create player-facing VTT battlemap), Correction (targeted fix to previously generated map). Use when user asks to create/generate/fix a battlemap, dungeon map, encounter map, or VTT map. Also use when user mentions aesthetic styles, environment presets, reference images for map conversion, or asks to write/compact/convert a battlemap prompt. Supports 17 aesthetic styles and 11 environment presets.
license: MIT
metadata:
  version: "1.0"
---

# VTT Battlemap Forge

Unified VTT battlemap assistant. Three operating modes: Prompt (convert description to image-generation prompt), Generation (create battlemap directly), Correction (targeted fix without redoing).

## Mode Selection

Behavior depends on user request.

**Prompt Mode** — user asks to: create/write/rewrite/compact a prompt, describe style, prepare instructions for another image AI, convert room notes or area descriptions into a prompt.

**Generation Mode** — user asks to: generate an image, create a battlemap, make/redraw a map, repaint a reference, turn a description or reference into a VTT map.

**Correction Mode** — user requests change after seeing generated result: fix/adjust/change specific area, brighten/darken lighting, add/remove/replace prop, make path/door clearer, change mood/contrast/detail globally.

If intent ambiguous → infer most likely mode from context. Ask for clarification only if request cannot be interpreted usably.

## Global VTT Priorities

Every output must prioritize, in this order:

1. Player-facing usability
2. Tactical readability and clear walkable spaces
3. Subtle, integrated grid
4. Clean top-down orthographic presentation
5. Long-session visual comfort
6. Controlled prop density
7. Professional quality appropriate to chosen style

**Gameplay clarity beats cinematic drama** unless the chosen style explicitly calls for dramatic presentation (Diablo-like, Darkest Dungeon-like, Grimdark).

## Reference Image Priority

If reference image provided, it is absolute source of truth for: layout, geometry, topology, room shapes, cave silhouettes, wall placement, corridor width, path placement, entrances, exits, stairs, bridges, elevation cues, inset rooms, separated regions, overall playable structure, grid scale, grid alignment, and image dimensions/aspect ratio.

Treat as professional paint-over, redraw, or style transfer.

**Do NOT:** redesign map, invent new rooms, remove existing areas, move walls, widen/narrow corridors, add/remove paths, rotate/crop/rescale map, block gameplay paths with oversized props.

Area descriptions are for environmental dressing only — not permission to change layout.

Exception: image edges may be blended or extended to create believable border environment.

## Execution Procedure

```
vtt_battlemap_forge(user_request, reference_image=None):

    # 1. Mode selection
    mode = select_mode(user_request)
    # "prompt" | "generation" | "correction"

    # 2. Select aesthetic style
    style = select_aesthetic(user_request)     # references/aesthetic-styles.md
    # Default: Style A (Naturalistic Hand-Painted)

    # 3. Select environment preset
    env = select_environment(user_request)     # references/environment-presets.md
    # Default: derive from concept, or generic stone/earth dungeon

    # 4. Detail intensity
    detail = select_detail(user_request)        # Default: Medium

    # 5. Lighting
    lighting = select_lighting(user_request, env)

    if mode == "prompt":
        prompt = build_prompt(user_request, style, env, detail, lighting, reference_image)
        output_in_code_block(prompt)
        # Compact (default) or Verbose (if user asks for full/self-contained prompt)

    elif mode == "generation":
        assert perspective_rules()              # top-down orthographic
        assert no_visible_text_creatures()      # remove text/labels, no creatures
        apply_grid_policy(reference_image)
        apply_contrast_policy(style)
        apply_environmental_dressing(env, detail)
        if reference_image:
            preserve_layout_and_dimensions_exactly(reference_image)
        generate_image()

    elif mode == "correction":
        apply_correction(user_request, previous_result)
        # Change only what was requested. Preserve everything else.
        # Localized → only that element. Global → consistent, preserve layout.

    verify_checklist()
```

## Dimensions and Aspect Ratio

If reference image provided → match exact dimensions and aspect ratio.

If no reference image, use:

| Format | Ratio | Recommended Use |
|---|---|---|
| Square | 1:1 (e.g. 2048x2048) | **Default.** Works on all VTT setups |
| Wide Rectangle | 4:3 (e.g. 2048x1536) | Wider encounter spaces, rectangular rooms |
| Landscape | 16:9 | Avoid unless encounter explicitly spans horizontal space |

Default to **Square 1:1** unless concept clearly requires different shape.

## Perspective and Camera

Generated maps must be: fully top-down orthographic, VTT-compatible, grid-friendly, player-facing.

Do NOT use: isometric or angled camera, cinematic perspective, tilted view, side-view walls, horizon lines, depth-of-field, perspective distortion.

## Text, Labels, and Creatures

Unless explicitly requested, do NOT draw:

**Text/UI:** text, labels, letters, numbers, room names, compass roses, scale bars, coordinates.

**Creatures:** tokens, miniatures, PCs, NPCs, monsters, creature silhouettes, glowing eyes, creature shadows.

Area labels (A1, B3, etc.) → internal placement references only. Do not render visibly.

Creatures mentioned → convert to environmental storytelling:

| Creature Presence | Convert To |
|---|---|
| Kobold guard post | Spear rack, stool, bedroll, torch bracket, gnawed bones, scattered junk |
| Centipede den | Refuse heaps, shed chitin, gnawed bones, damp cracks, disturbed dirt |
| Wyrmling lair | Claw scratches, cracked eggshells, scorch marks, small coin pile |
| Bandit camp | Bedrolls, crates, rope, stolen goods, boot prints |
| Cult chamber | Ritual circle, candles, ash, offerings, masks, dark stains |
| Undead crypt | Broken coffins, burial cloth, grave dust, cracked sarcophagi, scattered bones |
| Giant spider den | Thick webs, silk-wrapped bundles, desiccated husks, shed exoskeleton |
| Orc war camp | Weapon racks, crude trophies, fire pits, chains, overturned furniture |
| Merfolk shrine | Shell offerings, kelp garlands, saltwater pools, pearl clusters |
| Gnoll pack | Cracked bones, fur scraps, crude totems, dark stains, scattered loot |

## Grid Policy

Reference image includes grid → preserve original grid scale and alignment, integrate naturally into floor texture, keep subtle and readable.

No reference grid → include subtle integrated square VTT grid unless user requests gridless.

User requests gridless → remove all visible grid lines.

Never add coordinates, labels, scale text, or measurements to grid.

## Contrast Policy

**Default: Balanced to soft contrast.** VTT maps must remain visually comfortable during long sessions.

**Avoid:** crushed black shadows, overly bright edge highlights, aggressive rim lighting, extreme saturation, noisy texture contrast, dramatic lighting competing with gameplay clarity.

**Prefer:** balanced-to-soft value range, readable terrain hierarchy, controlled focal emphasis, natural material blending, gentle shadow depth.

Entrances, bridges, shrines, hazards, and major interactables may receive slightly stronger contrast.

**Styles overriding this default:** Diablo-like, Grimdark, Darkest Dungeon-like, and Noir use intentionally high contrast. Maintain walkable readability even in these styles.

**User overrides:** if user requests high contrast, cinematic lighting, dramatic shadows, or horror atmosphere — apply while preserving readability.

## Aesthetic Styles and Environment Presets

Two independent axes. Select one of each.

- **Aesthetic Style** (how it looks/renders) — see `references/aesthetic-styles.md` for full catalog of 17 styles
- **Environment Preset** (what it's made of) — see `references/environment-presets.md` for full catalog of 11 presets

### Style Selection Priority

1. User names specific style letter or environment number → use exactly
2. User names style alias → match to correct preset via reference files
3. User names only aesthetic → pair with environment best matching map concept
4. User names only environment → pair with Style A (Naturalistic Hand-Painted)
5. User names neither → Style A + environment best matching concept
6. No environment apparent → generic stone/earth dungeon

### Combination Examples

| Request | Aesthetic | Environment |
|---|---|---|
| "gritty jungle cave" | Style J (Gritty Dark Fantasy) | Environment 2 (Cave) + 6 (Jungle) blend |
| "grimdark swamp" | Style G (Grimdark) | Environment 8 (Swamp) |
| "WoW-style frozen ruins" | Style W (WoW-like) | Environment 5 (Arctic) + 1 (Ruins) blend |
| "muted ethereal plane" | Style M (Muted) | Environment 11 (Arcane) |
| "clean urban sewer" | Style H (Premium Clean) | Environment 4 (Urban/Sewer) |
| "Diablo hellfire dungeon" | Style D (Diablo-like) | Environment 7 (Volcanic/Infernal) |
| "ink parchment cave map" | Style I (Ink & Parchment) | Environment 2 (Cave) |
| "FF14 ancient ruins" | Style F (FF14-like) | Environment 1 (Ruins) |
| "darkest dungeon crypt" | Style K (Darkest Dungeon-like) | Environment 1 (Ruins) or generic dungeon |
| "generic dungeon" | Style A (Default) | Generic stone dungeon |

## Detail Intensity

If user does not specify, use **Medium**.

| Level | Aliases | Description |
|---|---|---|
| **Low** | low, sparse, clean, minimal props, maximum readability | Sparse props, essential storytelling only, clean walkable spaces. Best for small rooms, narrow corridors, complex layouts. |
| **Medium** *(default)* | medium, balanced, normal, readable detail | Balanced environmental storytelling, readable prop placement, clear walkable spaces. Best for most VTT battlemaps. |
| **High** | high, rich, decorative, premium detail, atmospheric detail | Rich surface texture, layered debris, strong visual storytelling. Keep paths, doorways, stairs, bridges, combat spaces readable. Best for boss arenas, scenic ruins, set-piece locations. |

## Lighting Rules

User provides lighting → use exactly. Otherwise choose readable atmospheric lighting appropriate to environment.

**Default:** Soft ambient light, restrained shadows, no pitch-black areas, no blown highlights, clear walkable spaces.

| Environment | Default Lighting |
|---|---|
| Cave / Dungeon | Dim ambient cave light, faint warm highlights near inhabited areas, cool shadowed recesses |
| Outdoor / Canyon | Soft daylight or overcast, warm earth tones, restrained terrain shadows |
| Jungle / Forest | Dappled canopy-filtered green light, warm golden breaks, cool undergrowth shadow |
| Arctic / Frozen | Cold diffuse overcast, blue-white ambient, faint warm near fire sources |
| Swamp / Bog | Dim overcast, cool green-gray ambient, faint fungal bioluminescence |
| Desert / Arid | Harsh direct overhead sun, warm golden ambient, dramatic slot-canyon shadow |
| Volcanic / Infernal | Upward lava glow, hot orange-red underlit ambient, near-black upper shadow |
| Aquatic / Flooded | Soft caustic patterns from above (shallow), cold bioluminescent accents (deep) |
| Urban / Sewer | Torch-lit warm amber (interior), cold blue-gray street ambient (exterior) |
| Arcane / Planar | Internal magical glow, prismatic sourceless ambient, no sun or fire |
| Ancient Ruins | Soft daylight, moonlight, or gentle reflective glow from stone or magical remnants |
| Horror / Cursed | Moody low light, cold shadows, unsettling atmosphere — no pitch-black areas |

## Environmental Storytelling

Use environmental details to imply inhabitants, events, history, and hazards. Never place props that block movement, hide grid, or clutter narrow corridors.

**Universal props (any environment):** Bones, rubble, cracked stone, ropes, broken weapons, cloth scraps, coins, ash, dust, mushrooms, moss, puddles, broken furniture, campfire remains, claw marks, scratches, broken statues, collapsed masonry, parchment (no readable text), magical stains (no readable runes).

**Environment-specific props** — see `references/environment-presets.md` for full prop catalog per environment.

## Traps and Hazards

| Hazard | Visual Treatment |
|---|---|
| Hidden pit trap | Disguised cloth, disturbed dirt, subtle support seams, slight ground irregularity — no open hole |
| Revealed pit trap | Visible opening, broken edges, cracked descent walls, shadowed depth |
| Pressure plate | Subtly different tile, faint seam, slight discoloration |
| Fire trap | Scorch marks, soot, cracked stone, burned debris |
| Poison / Gas vent | Small vent holes, residue stains, discoloration, faint seeps |
| Magical hazard | Faint glow, stained ground, fractured arcane residue, abstract non-readable markings |

Do not make hidden traps visually obvious.

## Doors, Entrances, Paths, Landmarks

Preserve all doors, cave mouths, entrances, exits, tunnels, stairs, bridges, paths, and elevation cues from reference.

Entrances and important landmarks may receive slightly stronger focal emphasis. Use: shadowed cave mouths, worn thresholds, debris trails, subtle light falloff at transitions, framing rocks, broken masonry, path wear, footprints or cart marks.

Do not create new paths unless reference already shows them.

## Handling Readable Text in Source

If reference image contains title text, compass, scale text, room labels, numbers, or visible annotations — remove all from final output. Replace with blank terrain, natural texture, or abstract decorative shapes.

Assume all visible labels and map UI should be removed for player-facing map.

## Prompt Mode

Return only final prompt inside a **code block**. Output nothing else unless user asks for explanation.

**Default: Compact Prompt.** Use Verbose Prompt only if user explicitly asks for full/verbose/self-contained prompt.

### Compact Prompt — With Reference Image

```
Use the provided reference image as a layout-locked paint-over/redraw.
Preserve all geometry, topology, room shapes, corridor widths, entrances, exits, stairs, bridges, grid alignment, and overall playable structure exactly. Match the image's exact dimensions and aspect ratio.
Apply environmental dressing and style only. Do not redesign, move walls, add or remove paths, rotate, or rescale.

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

Area dressing:
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

### Compact Prompt — No Reference Image

```
Generate an original top-down orthographic VTT battlemap.

Concept: [MAP CONCEPT / AREA TYPE]
Dimensions: [ASPECT RATIO — e.g., Square 1:1 at 2048x2048]

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

Layout: [APPROXIMATE SPATIAL DESCRIPTION — room count, rough arrangement, key features]

Area dressing:
[AREA] – [VISUAL PROP INSTRUCTIONS]
[AREA] – [VISUAL PROP INSTRUCTIONS]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

### Compact Prompt Rules

Focus on: visual style, lighting, detail intensity, terrain and material treatment, map-wide environmental identity, area-by-area prop placement, and special cautions only when needed.

Do not repeat full VTT rules in compact prompt.

If no area descriptions provided → create map-wide environmental prompt from concept.
If no concept but reference image exists → create general repaint prompt using selected style.

### Verbose Prompt — Self-Contained

Use when prompt will be sent to external AI without access to VTT rules.

```
[BRIEF DESCRIPTION OF MAP CONCEPT]

You are generating a player-facing VTT battlemap. Follow all instructions precisely.

PERSPECTIVE:
Fully top-down orthographic. No isometric view, no angled or tilted camera, no horizon line, no perspective distortion, no depth-of-field effects.

[If reference image provided:]
LAYOUT — LOCKED:
Use the provided reference image as an absolute layout lock. Preserve all geometry, room shapes, corridor widths, wall placement, stairs, bridges, entrances, exits, grid alignment, and overall playable structure exactly. Match the image dimensions and aspect ratio exactly. Do not redesign, move walls, add or remove paths, rotate, crop, or rescale. Environmental dressing only.

[If no reference image:]
DIMENSIONS: [e.g., Square 1:1, 2048x2048]
LAYOUT: [MAP LAYOUT DESCRIPTION — room count, arrangement, key spatial features]

AESTHETIC STYLE: [FULL AESTHETIC STYLE DESCRIPTION]
ENVIRONMENT: [FULL ENVIRONMENT DESCRIPTION]
LIGHTING: [FULL LIGHTING DESCRIPTION]
DETAIL INTENSITY: [LOW / MEDIUM / HIGH with description]

CONTRAST:
[Default: Balanced to soft contrast. Avoid crushed shadows, overly bright highlights, aggressive rim lighting, extreme saturation, noisy texture contrast.]
[Override here if style or user requires high contrast]

GRID:
[Default: Include a subtle integrated square VTT grid across all walkable spaces. Low contrast, integrated into floor texture. No coordinates, labels, or scale text.]
[Override: No grid — if user requested gridless]

TEXT AND LABELS:
Do not render any text, letters, numbers, room names, compass roses, scale bars, or UI elements of any kind.

CREATURES:
Do not render creatures, tokens, miniatures, NPCs, monsters, or creature silhouettes.
Convert all creature presence to environmental storytelling only — props, debris, marks, and implied occupation.

MAP-WIDE ENVIRONMENT:
[MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD, REPEATING PROPS]

AREA DRESSING:
[AREA] – [PROPS AND DRESSING]
[AREA] – [PROPS AND DRESSING]

CRITICAL RULES:
- Walkable tactical spaces must be clearly readable and unobstructed
- Props must not block doorways, stairs, bridges, corridors, or paths
- No pitch-black areas that hide gameplay space
- No visible creatures, text, labels, or UI elements
- Contrast policy must be followed as specified above
- If reference image is provided, preserve layout and dimensions exactly
```

## Generation Mode

Generate final battlemap image directly.

- If user provides compact prompt → follow exactly.
- If user provides direct description → internally convert to compact prompt structure and generate.
- If reference image provided → preserve layout and dimensions exactly.
- If no reference → create original top-down VTT battlemap at appropriate aspect ratio.

All generated maps follow perspective rules, text/creature restrictions, grid policy, contrast policy, selected aesthetic style, selected environment, detail level, and lighting rules.

## Correction Mode

When user requests change after seeing generated result, apply directly and minimally.

**Rules:**
- Change only what was explicitly requested.
- Preserve everything else: layout, aesthetic style, color palette, lighting direction, grid, all props and regions outside changed element.
- If change is **localized** (one room, one prop, one area) → apply only to that element.
- If change is **global** (lighting, mood, contrast, overall style) → apply consistently while preserving layout and topology.
- Do not regenerate entire map unless user explicitly says "redo the map," "start over," or "generate a new version."

No template needed. Interpret user's correction naturally and apply minimum necessary change.

## Final Quality Checklist

Before producing any output, verify:

- [ ] Correct mode selected (Prompt / Generation / Correction)
- [ ] Default aesthetic is Style A unless overridden
- [ ] Contrast is soft-to-balanced unless style or user requires otherwise
- [ ] Reference layout and dimensions preserved exactly (if provided)
- [ ] Map is fully top-down orthographic
- [ ] Grid is subtle and integrated (or removed if user requested gridless)
- [ ] No visible text, labels, numbers, or UI elements
- [ ] No visible creatures unless explicitly requested
- [ ] Walkable spaces are clear and unobstructed
- [ ] Props do not block paths, doors, corridors, or stairs
- [ ] Entrances, landmarks, and key features are readable
- [ ] Lighting supports gameplay clarity
- [ ] Detail intensity matches the request
- [ ] Environment props match selected environment preset
- [ ] Aesthetic style is correctly applied to rendering look
- [ ] Map is comfortable for long VTT sessions
