---
name: prompt-templates
description: Image-generation prompt templates for VTT Battlemap Forge Prompt Mode. Contains compact (default) and verbose (self-contained) templates assembled from shared blocks using conditional rules. DM variant adds a Creatures section for on-map creature placement. Load only in Prompt Mode.
---

# Prompt Templates

## Output Rule

Return only the final prompt inside a **code block**. Output nothing else unless the user asks for an explanation.

**Default: Compact Prompt.** Use Verbose Prompt only if the user explicitly asks for a full, verbose, or self-contained prompt.

**Character limit:** Keep the final prompt under 10,000 characters. If the filled template exceeds this limit, trim area dressing detail and reduce verbose expansions rather than losing structural instructions or critical rules.

---

## Shared Template Blocks

These blocks are inserted into the output template based on assembly rules below. They are defined once and referenced by both compact and verbose templates.

### Block A: Blueprint Protocol (Reference Image)

```
Treat the reference image as a spatial blueprint only — preserve structure, replace all surfaces.

STRUCTURE (preserve exactly): path routing, cliff-line tiers, clearing shapes, rock/object coordinates, room boundaries, corridor widths, entrances, exits, stairs, bridges, elevation breaks, and navigation flow. Maintain identical aspect ratio.

SURFACE (replace entirely): erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild all surfaces from scratch using the target aesthetic style and environment assets below.

NEGATIVE (source style): No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.

GRID REJECTION: Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. Output must have an uninterrupted, seamless floor surface.
```

### Block B: Player-Safe Note Extraction

```
Player-safe note extraction:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. Do not reveal hidden traps, ambushes, secret doors, hidden treasure, invisible creatures, puzzle solutions, or DM-only information.
```

### Block C: DM Note Extraction

```
Note extraction:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. In DM Spoiler Dressing, include DM-only visible traps, ambushes, secret treasure, hidden occupants, or other spoilers only when explicitly requested for the DM variant.
```

### Block D: Creature Specification (DM)

```
Creatures:
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
[AREA] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
```

### Block E: Creature Rendering (DM)

```
Creature rendering:
Illustrate all creatures as figures in the environment, consistent with the aesthetic style above. Creatures must not block doorways, stairs, corridors, or paths. Scale creatures to the map grid. No token circles, no floating overlays, no creature name labels.
[If creature reference images provided: Match creature appearance to the provided reference images.]
```

---

## Compact Prompt Template

### Assembly Rules

| Condition | Action |
|---|---|
| Reference image provided | Start with **Block A** (Blueprint Protocol) as the opening |
| No reference image | Start with: `Generate an original top-down orthographic VTT battlemap.[If DM:  — DM version with creature placement.]` then `Concept: [MAP CONCEPT / AREA TYPE]` |
| Player variant (default) | Use **Block B** (Player-Safe Note Extraction) in the Note Extraction position |
| DM variant active | Use **Block C** (DM Note Extraction) instead of Block B; append **Block D** + **Block E** after Area Dressing |
| No reference image | Include `Layout: [APPROXIMATE SPATIAL DESCRIPTION]` line after Map-wide details |
| No map-specific warnings | Omit the `Important:` section entirely |

### Template

```
[OPENING: Block A OR No-Reference Opening — per Assembly Rules]

Aesthetic Style: [SELECTED AESTHETIC STYLE DESCRIPTION]
Environment: [SELECTED ENVIRONMENT DESCRIPTION]
Lighting: [LIGHTING]
Detail intensity: [LOW / MEDIUM / HIGH]
Narrative dressing fidelity: [REFERENCE FAITHFUL / BALANCED NARRATIVE / STRONG NARRATIVE / DM SPOILER]
Contrast: [SOFT / BALANCED / HIGH — note if overriding default]
Dimensions: [cols]×[rows] cells at [cell_px]px per cell = [width]×[height]px
No painted grid: export without gridlines — VTT will overlay its own grid
Prop perspective: all objects rendered strictly top-down — chests, crates, barrels, tables, furniture, and debris show only top planes and silhouettes; no front face, no side face, no angled perspective on any prop

Narrative Dressing Priority:
[DRESSING FIDELITY MODE]

Mandatory Visual Anchors:
[AREA] — [1–3 concrete player-safe props that must appear visibly]
[AREA] — [1–3 concrete player-safe props that must appear visibly]

[BLOCK B or BLOCK C — per Assembly Rules]

Map-wide details:
[GENERAL ENVIRONMENT, MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD]

[IF NO REFERENCE IMAGE:]
Layout: [APPROXIMATE SPATIAL DESCRIPTION — room count, rough arrangement, key features]

Area dressing:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]

[AREA] - Do not reveal: [...]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]
[AREA LABEL] – [VISUAL PROP INSTRUCTIONS]

[IF DM VARIANT: Block D + Block E]

Important:
[SPECIAL WARNINGS FOR THIS MAP ONLY — omit section if none]
```

---

## Verbose Prompt Template

Use when the prompt will be sent to an external AI that does not have access to VTT rules. Same assembly rules as Compact, but all VTT domain rules are written inline (self-contained).

### Assembly Rules

| Condition | Action |
|---|---|
| Reference image provided | Include the Blueprint Protocol paragraph under PERSPECTIVE |
| No reference image | Include DIMENSIONS + LAYOUT fields under PERSPECTIVE |
| Player variant (default) | Include "Do not render creatures" text in CREATURES section |
| DM variant active | Include DM creatures section with creature list + rendering rules; change opening to "DM-facing" |
| Player variant (default) | Use Player-Safe note extraction paragraph |
| DM variant active | Use DM note extraction paragraph (allows DM Spoiler content) |

### Template

```
[BRIEF DESCRIPTION OF MAP CONCEPT — append " — DM VERSION WITH CREATURE PLACEMENT" if DM variant]

You are generating a [player-facing / DM-facing] VTT battlemap. Follow all instructions precisely.

PERSPECTIVE:
Fully top-down orthographic. No isometric view, no angled or tilted camera, no horizon line, no perspective distortion, no depth-of-field effects.

[IF REFERENCE IMAGE PROVIDED:]
BLUEPRINT PROTOCOL:
Treat the reference image as a spatial blueprint only — preserve structure, replace all surfaces.
STRUCTURE (preserve exactly): path routing, room shapes, corridor widths, wall placement, stairs, bridges, entrances, exits, elevation breaks, and navigation flow. Maintain identical aspect ratio.
SURFACE (replace entirely): erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild all surfaces from scratch using the aesthetic style and environment specified below.
NEGATIVE (source style): No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.
GRID REJECTION: Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. Output must have an uninterrupted, seamless floor surface.

[IF NO REFERENCE IMAGE:]
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

PROPS PERSPECTIVE:
All props, objects, and environmental dressing must obey strict top-down orthographic camera — the same perspective as the map itself. Only top planes, silhouettes, contact shadows, and ambient occlusion may show depth. No object may show a front face, side face, horizon-facing plane, or isometric/angled perspective. Chests, coffers, crates, and sarcophagi must show only the rectangular top/lid — no front face, no side face, no angled chest icon. Barrels and urns must show only the circular top. Tables, beds, benches, and furniture must show only the flat top surface. Columns and pillars show only the circular top cross-section. Weapons, logs, bones, and debris appear as overhead silhouettes with contact shadow only.

TEXT AND LABELS:
Do not render any text, letters, numbers, room names, compass roses, scale bars, or UI elements of any kind.[If DM: Do not render creature name labels.]

[IF PLAYER VARIANT:]
CREATURES:
Do not render creatures, tokens, miniatures, NPCs, monsters, or creature silhouettes.
Convert all creature presence to environmental storytelling only — props, debris, marks, and implied occupation.

[IF DM VARIANT:]
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
These are concrete player-safe props that must appear visibly in the final map. They have higher priority than atmospheric dressing but must not block movement or reveal spoilers.

[AREA] — [1–3 concrete visible props]
[AREA] — [1–3 concrete visible props]

[IF PLAYER VARIANT:]
PLAYER-SAFE NOTE EXTRACTION:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. Include only details players could safely perceive before discovering hidden content. Do not reveal hidden traps, ambushes, secret doors, hidden treasure, invisible creatures, puzzle solutions, or DM-only information.

[IF DM VARIANT:]
NOTE EXTRACTION:
Use markdown, adventure notes, or room descriptions to enrich each area with visible environmental storytelling. For Reference Faithful, Balanced Narrative, or Strong Narrative, include only player-safe visible dressing. For DM Spoiler Dressing, include DM-only visible traps, ambush positions, secret treasure, hidden occupants, or other spoiler elements only when explicitly requested for this DM-facing map.

MAP-WIDE ENVIRONMENT:
[MATERIALS, TERRAIN, FLOOR/WALL TREATMENT, MOOD, REPEATING PROPS]

AREA DRESSING:
[AREA] - Visual anchor priority: [repeat the single most important mandatory prop if any]
[AREA] - Required visible dressing: [...]

[AREA] - Do not reveal: [...]
[AREA] – [PROPS AND DRESSING]
[AREA] – [PROPS AND DRESSING]

CRITICAL RULES:
- Walkable tactical spaces must be clearly readable and unobstructed
- Props must not block doorways, stairs, bridges, corridors, or paths
- No pitch-black areas that hide gameplay space
- No visible creatures, text, labels, or UI elements[If DM:  — except rendered creature figures as specified above]
- [If DM: - Creature scale must match grid scale; creatures must not block tactical paths]
- All props must obey strict top-down orthographic camera — no object may show a front face, side face, or isometric angle
- Contrast policy must be followed as specified above
- If reference image is provided, preserve layout and topology exactly; dimensions are set by cell count above
```

---

## Compact Prompt Rules

Focus on: visual style, lighting, detail intensity, terrain and material treatment, map-wide environmental identity, area-by-area prop placement, and special cautions only when needed.

Do not repeat full VTT rules in a compact prompt.

- If no area descriptions provided → create a map-wide environmental prompt from the concept.
- If no concept but reference image exists → create a general repaint prompt using the selected style.

### Reference Image Use Cases in Prompt Mode

**Layout lock (primary use case):** Reference image is the source map to paint over. Use Block A (Blueprint Protocol) as opening. Preserve layout exactly.

**Visual continuity reference:** A previously generated map is provided not to repaint, but to maintain palette, material feel, and environmental consistency when generating a *new adjacent or related area*. In this case:
- Do NOT use the layout-lock template language (Block A).
- Instead, add a Continuity Reference note to the template:
  ```
  Continuity Reference:
  A previously generated map from the same location is provided. Match: color palette, material textures, lighting character, and environmental feel. This is a new adjacent area — do not reproduce the reference map's layout.
  ```

---

## Creature Specification Quick Reference

```
[AREA / ROOM] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
```

**Behavior / State:** resting, sleeping, patrol stance, alert combat-ready, coiled/crouched, feeding, guarding an object, hiding (partially concealed), emerging, mid-ritual, fleeing.

**Position hints:** center, near [north/south/east/west] door, spread across area, clustered near [landmark], flanking entrance, at perimeter, crouched behind cover.
