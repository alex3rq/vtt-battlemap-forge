---
name: prompt-templates
description: Image-generation prompt templates for VTT Battlemap Forge Prompt Mode. Contains Compact (default) and Verbose (self-contained) templates in both player (default) and DM variants, with narrative dressing fidelity fields. DM variant adds a Creatures section for on-map creature placement. Load only in Prompt Mode.
---

# Prompt Templates

## Output Rule

Return only the final prompt inside a **code block**. Output nothing else unless the user asks for an explanation.

**Default: Compact Prompt.** Use Verbose Prompt only if the user explicitly asks for a full, verbose, or self-contained prompt.

---

## Compact Prompt — With Reference Image

```
Treat the reference image as a spatial blueprint only — preserve structure, replace all surfaces.

STRUCTURE (preserve exactly): path routing, cliff-line tiers, clearing shapes, rock/object coordinates, room boundaries, corridor widths, entrances, exits, stairs, bridges, elevation breaks, and navigation flow. Maintain identical aspect ratio.

SURFACE (replace entirely): erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild all surfaces from scratch using the target aesthetic style and environment assets below.

NEGATIVE (source style): No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.

GRID REJECTION: Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. Output must have an uninterrupted, seamless floor surface.

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Narrative dressing fidelity: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]
Dimensions: [cols]×[rows] cells at [cell_px]px per cell = [width]×[height]px
No painted grid: export without gridlines — VTT will overlay its own grid

Narrative Dressing Priority:
[DRESSING FIDELITY MODE]

Mandatory Visual Anchors:
[AREA] — [1–3 concrete player-safe props that must appear visibly]
[AREA] — [1–3 concrete player-safe props that must appear visibly]
[AREA] — [1–3 concrete player-safe props that must appear visibly]

Player-safe note extraction:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. Do not reveal hidden traps, ambushes, secret doors, hidden treasure, invisible creatures, puzzle solutions, or DM-only information.

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

Area dressing:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]
[AREA] - Optional subtle dressing: [...]
[AREA] - Do not reveal: [...]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

---

## Compact Prompt — No Reference Image

```
Generate an original top-down orthographic VTT battlemap.

Concept: [MAP CONCEPT / AREA TYPE]
Dimensions: [cols]×[rows] cells at [cell_px]px per cell = [width]×[height]px
No painted grid: export without gridlines — VTT will overlay its own grid

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Narrative dressing fidelity: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]

Narrative Dressing Priority:
[DRESSING FIDELITY MODE]

Mandatory Visual Anchors:
[AREA] — [1–3 concrete player-safe props that must appear visibly]

Player-safe note extraction:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. Do not reveal hidden traps, ambushes, secret doors, hidden treasure, invisible creatures, puzzle solutions, or DM-only information. In DM Spoiler Dressing, DM-only content may be included only for an explicitly DM-facing variant.

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

Layout: [APPROXIMATE SPATIAL DESCRIPTION — room count, rough arrangement, key features]

Area dressing:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]
[AREA] - Optional subtle dressing: [...]
[AREA] - Do not reveal: [...]
[AREA] – [VISUAL PROP INSTRUCTIONS]
[AREA] – [VISUAL PROP INSTRUCTIONS]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

---

## Compact Prompt Rules

Focus on: visual style, lighting, detail intensity, terrain and material treatment, map-wide environmental identity, area-by-area prop placement, and special cautions only when needed.

Do not repeat full VTT rules in a compact prompt.

- If no area descriptions provided → create a map-wide environmental prompt from the concept.
- If no concept but reference image exists → create a general repaint prompt using the selected style.

### Reference Image Use Cases in Prompt Mode

**Layout lock (primary use case):** Reference image is the source map to paint over. Use the "With Reference Image" template. Preserve layout exactly.

**Visual continuity reference:** A previously generated map is provided not to repaint, but to maintain palette, material feel, and environmental consistency when generating a *new adjacent or related area*. In this case:
- Do NOT use the layout-lock template language.
- Instead, add a Continuity Reference note to the "No Reference Image" template:
  ```
  Continuity Reference:
  A previously generated map from the same location is provided. Match: color palette, material textures, lighting character, and environmental feel. This is a new adjacent area — do not reproduce the reference map's layout.
  ```

---

## Verbose Prompt — Self-Contained (Player)

Use when the prompt will be sent to an external AI that does not have access to VTT rules.

```
[BRIEF DESCRIPTION OF MAP CONCEPT]

You are generating a player-facing VTT battlemap. Follow all instructions precisely.

PERSPECTIVE:
Fully top-down orthographic. No isometric view, no angled or tilted camera, no horizon line, no perspective distortion, no depth-of-field effects.

[If reference image provided:]
BLUEPRINT PROTOCOL:
Treat the reference image as a spatial blueprint only — preserve structure, replace all surfaces.
STRUCTURE (preserve exactly): path routing, room shapes, corridor widths, wall placement, stairs, bridges, entrances, exits, elevation breaks, and navigation flow. Maintain identical aspect ratio.
SURFACE (replace entirely): erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild all surfaces from scratch using the aesthetic style and environment specified below.
NEGATIVE (source style): No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.
GRID REJECTION: Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. Output must have an uninterrupted, seamless floor surface.

[If no reference image:]
DIMENSIONS: [cols] columns × [rows] rows at [cell_px]px per cell = [width]×[height]px total
LAYOUT: [MAP LAYOUT DESCRIPTION — room count, arrangement, key spatial features]

AESTHETIC STYLE: [FULL AESTHETIC STYLE DESCRIPTION]
ENVIRONMENT: [FULL ENVIRONMENT DESCRIPTION]
LIGHTING: [FULL LIGHTING DESCRIPTION]
DETAIL INTENSITY: [LOW / MEDIUM / HIGH with description]
NARRATIVE DRESSING FIDELITY: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER with description]

CONTRAST:
[Default: Balanced to soft contrast. Avoid crushed shadows, overly bright highlights, aggressive rim lighting, extreme saturation, noisy texture contrast.]
[Override here if style or user requires high contrast]

GRID:
[Default: No painted grid. Export without visible gridlines — the VTT will overlay its own grid for perfect alignment.]
[Override: Include a subtle integrated square VTT grid — only if user explicitly requested it. Low contrast, integrated into floor texture. No coordinates, labels, or scale text.]

TEXT AND LABELS:
Do not render any text, letters, numbers, room names, compass roses, scale bars, or UI elements of any kind.

CREATURES:
Do not render creatures, tokens, miniatures, NPCs, monsters, or creature silhouettes.
Convert all creature presence to environmental storytelling only — props, debris, marks, and implied occupation.

NARRATIVE DRESSING PRIORITY:
[DRESSING FIDELITY MODE]

MANDATORY VISUAL ANCHORS:
These are concrete player-safe props that must appear visibly in the final map. They have higher priority than atmospheric dressing but must not block movement or reveal spoilers.

[AREA] — [1–3 concrete visible props]
[AREA] — [1–3 concrete visible props]

PLAYER-SAFE NOTE EXTRACTION:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. Do not reveal hidden traps, ambushes, secret doors, hidden treasure, invisible creatures, puzzle solutions, or DM-only information.

MAP-WIDE ENVIRONMENT:
[MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD, REPEATING PROPS]

AREA DRESSING:
[AREA] - Required visible dressing: [...]
[AREA] - Optional subtle dressing: [...]
[AREA] - Do not reveal: [...]
[AREA] – [PROPS AND DRESSING]
[AREA] – [PROPS AND DRESSING]

CRITICAL RULES:
- Walkable tactical spaces must be clearly readable and unobstructed
- Props must not block doorways, stairs, bridges, corridors, or paths
- No pitch-black areas that hide gameplay space
- No visible creatures, text, labels, or UI elements
- Contrast policy must be followed as specified above
- If reference image is provided, preserve layout and topology exactly; dimensions are set by cell count above
```

---

## DM Prompt Templates

DM variants add a **Creatures** section to the standard templates. All other sections remain identical to the player versions. Player-facing is always the default — only use these when `dm_mode` is active.

### DM Compact Prompt — With Reference Image

```
Treat the reference image as a spatial blueprint only — preserve structure, replace all surfaces.

STRUCTURE (preserve exactly): path routing, cliff-line tiers, clearing shapes, rock/object coordinates, room boundaries, corridor widths, entrances, exits, stairs, bridges, elevation breaks, and navigation flow. Maintain identical aspect ratio.

SURFACE (replace entirely): erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild all surfaces from scratch using the target aesthetic style and environment assets below.

NEGATIVE (source style): No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.

GRID REJECTION: Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. Output must have an uninterrupted, seamless floor surface.

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Narrative dressing fidelity: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]
Dimensions: [cols]×[rows] cells at [cell_px]px per cell = [width]×[height]px
No painted grid: export without gridlines — VTT will overlay its own grid

Narrative Dressing Priority:
[DRESSING FIDELITY MODE]

Mandatory Visual Anchors:
[AREA] — [1–3 concrete props that must appear visibly]

Player-safe note extraction:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. In DM Spoiler Dressing, include DM-only visible traps, ambushes, secret treasure, hidden occupants, or other spoilers only when explicitly requested for the DM variant.

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

Area dressing:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]
[AREA] - Optional subtle dressing: [...]
[AREA] - Do not reveal: [...]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]

Creatures:
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]

Creature rendering:
Illustrate all creatures as figures in the environment, consistent with the aesthetic style above. Creatures must not block doorways, stairs, corridors, or paths. Scale creatures to the map grid. No token circles, no floating overlays, no creature name labels.
[If creature reference images provided: Match creature appearance to the provided reference images.]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

---

### DM Compact Prompt — No Reference Image

```
Generate an original top-down orthographic VTT battlemap — DM version with creature placement.

Concept: [MAP CONCEPT / AREA TYPE]
Dimensions: [cols]×[rows] cells at [cell_px]px per cell = [width]×[height]px
No painted grid: export without gridlines — VTT will overlay its own grid

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Narrative dressing fidelity: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]

Narrative Dressing Priority:
[DRESSING FIDELITY MODE]

Mandatory Visual Anchors:
[AREA] — [1–3 concrete props that must appear visibly]

Player-safe note extraction:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. In DM Spoiler Dressing, include DM-only visible traps, ambushes, secret treasure, hidden occupants, or other spoilers only when explicitly requested for the DM variant.

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

Layout: [APPROXIMATE SPATIAL DESCRIPTION — room count, rough arrangement, key features]

Area dressing:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]
[AREA] - Optional subtle dressing: [...]
[AREA] - Do not reveal: [...]
[AREA] – [VISUAL PROP INSTRUCTIONS]
[AREA] – [VISUAL PROP INSTRUCTIONS]

Creatures:
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]

Creature rendering:
Illustrate all creatures as figures in the environment, consistent with the aesthetic style above. Creatures must not block doorways, stairs, corridors, or paths. Scale creatures to the map grid. No token circles, no floating overlays, no creature name labels.
[If creature reference images provided: Match creature appearance to the provided reference images.]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

---

### DM Verbose Prompt — Self-Contained

Full self-contained DM prompt for external AI without access to VTT rules.

```
[BRIEF DESCRIPTION OF MAP CONCEPT — DM VERSION WITH CREATURE PLACEMENT]

You are generating a DM-facing VTT battlemap with creatures in position. Follow all instructions precisely.

PERSPECTIVE:
Fully top-down orthographic. No isometric view, no angled or tilted camera, no horizon line, no perspective distortion, no depth-of-field effects.

[If reference image provided:]
BLUEPRINT PROTOCOL:
Treat the reference image as a spatial blueprint only — preserve structure, replace all surfaces.
STRUCTURE (preserve exactly): path routing, room shapes, corridor widths, wall placement, stairs, bridges, entrances, exits, elevation breaks, and navigation flow. Maintain identical aspect ratio.
SURFACE (replace entirely): erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild all surfaces from scratch using the aesthetic style and environment specified below.
NEGATIVE (source style): No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.
GRID REJECTION: Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. Output must have an uninterrupted, seamless floor surface.

[If no reference image:]
DIMENSIONS: [cols] columns × [rows] rows at [cell_px]px per cell = [width]×[height]px total
LAYOUT: [MAP LAYOUT DESCRIPTION — room count, arrangement, key spatial features]

AESTHETIC STYLE: [FULL AESTHETIC STYLE DESCRIPTION]
ENVIRONMENT: [FULL ENVIRONMENT DESCRIPTION]
LIGHTING: [FULL LIGHTING DESCRIPTION]
DETAIL INTENSITY: [LOW / MEDIUM / HIGH with description]
NARRATIVE DRESSING FIDELITY: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER with description]

CONTRAST:
[Default: Balanced to soft contrast. Avoid crushed shadows, overly bright highlights, aggressive rim lighting, extreme saturation, noisy texture contrast.]
[Override here if style or user requires high contrast]

GRID:
[Default: No painted grid. Export without visible gridlines — the VTT will overlay its own grid for perfect alignment.]
[Override: Include a subtle integrated square VTT grid — only if user explicitly requested it. Low contrast, integrated into floor texture. No coordinates, labels, or scale text.]

TEXT AND LABELS:
Do not render any text, letters, numbers, room names, compass roses, scale bars, or UI elements of any kind. Do not render creature name labels.

CREATURES:
This is a DM-facing map. Render the following creatures as illustrated figures in the environment.
Style must be consistent with the aesthetic style specified above. Do not render as token circles or floating overlays.
Creatures must not block doorways, stairs, corridors, or combat paths. Scale figures to match the grid.
Props from the environment dressing are retained — creatures are placed on top of the existing scene.
[If creature reference images provided: Use the provided reference images to match each creature's appearance.]

[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]

NARRATIVE DRESSING PRIORITY:
[DRESSING FIDELITY MODE]

MANDATORY VISUAL ANCHORS:
[AREA] — [1–3 concrete props that must appear visibly]

NOTE EXTRACTION:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. For Reference Faithful, Balanced Narrative, or Strong Narrative, include only player-safe visible dressing. For DM Spoiler Dressing, include DM-only visible traps, ambush positions, secret treasure, hidden occupants, or other spoiler elements only when explicitly requested for this DM-facing map.

MAP-WIDE ENVIRONMENT:
[MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD, REPEATING PROPS]

AREA DRESSING:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]
[AREA] - Optional subtle dressing: [...]
[AREA] - Do not reveal: [...]
[AREA] – [PROPS AND DRESSING]
[AREA] – [PROPS AND DRESSING]

CRITICAL RULES:
- Walkable tactical spaces must be clearly readable — including around creature placement
- Creatures must not block doorways, stairs, bridges, corridors, or paths
- No pitch-black areas that hide gameplay space
- No visible text, labels, creature names, or UI elements
- Creature scale must match grid scale
- Contrast policy must be followed as specified above
- If reference image is provided, preserve layout and topology exactly; dimensions are set by cell count above
```

---

### Creature Specification Quick Reference

```
[AREA / ROOM] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
```

**Behavior / State:** resting, sleeping, patrol stance, alert combat-ready, coiled/crouched, feeding, guarding an object, hiding (partially concealed), emerging, mid-ritual, fleeing.

**Position hints:** center, near [north/south/east/west] door, spread across area, clustered near [landmark], flanking entrance, at perimeter, crouched behind cover.
