---
name: vtt-core-rules
description: Core VTT battlemap rules for Prompt, Generation, and Correction modes. Covers perspective, text/creature restrictions, creature-to-prop conversion, grid policy, contrast policy, lighting rules, environmental storytelling, traps and hazards, doors and entrances, correction behavior, and the final quality checklist. Called by SKILL.md for all non-Scene-Art modes.
---

# VTT Core Rules

## Perspective and Camera

Generated maps must be: fully top-down orthographic, VTT-compatible, grid-friendly, player-facing.

Do NOT use: isometric or angled camera, cinematic perspective, tilted view, side-view walls, horizon lines, depth-of-field, or perspective distortion.

## Text, Labels, and Creatures

Unless explicitly requested, do NOT draw:

**Text / UI:** text, labels, letters, numbers, room names, compass roses, scale bars, coordinates, or any readable writing.

**Creatures:** tokens, miniatures, PCs, NPCs, monsters, creature silhouettes, glowing eyes, or creature shadows.

Area labels (A1, B3, etc.) → internal placement references only. Do not render visibly.

### Creature-to-Prop Conversion

Creatures mentioned in the brief → convert to environmental storytelling props:

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

**Default: No painted grid.** Generate all VTT maps without visible gridlines unless the user explicitly requests one. The VTT platform overlays its own crisp grid — a painted grid in the image will never align perfectly and adds visual noise.

- User requests grid → paint a subtle integrated square grid across all walkable spaces; low contrast, integrated into floor texture; no coordinates, labels, or scale text.
- Reference image includes a painted grid → count the visible columns and rows, record the cell count, then remove the grid from the output (paint over it). See Grid Dimensions Math below.
- Never add coordinates, labels, scale text, or measurements to any grid.

## Grid Dimensions Math

Every VTT map output must specify a cell count and a target PPI so the user can configure their VTT correctly. This is how the image aligns to the platform grid — not by painting gridlines, but by making the math explicit.

### Cell size by platform

| VTT Platform | Cell size (px) | Notes |
|---|---|---|
| **Owlbear Rodeo** | **100px** | **Default.** Flexible range 70–150px; 100px is the sweet spot. Supports filename auto-alignment. |
| Roll20 | 70px or 140px | Must be exactly one of these two values. Use 140px for high-res/retina maps. |
| Foundry VTT | 100px | Flexible; 100px recommended. |
| Fantasy Grounds | 100px | Flexible; 100px recommended. |
| Generic / Unknown | 100px | Default. User can adjust in VTT. |

Default platform: **Owlbear Rodeo** at **100px per cell** unless the user specifies otherwise.

### Detecting VTT platform from user request

```
detect_vtt_platform(user_request):
    "roll20", "Roll20"                    → cell_px = 70 (or 140 if "high-res" / "retina" mentioned)
    "owlbear", "Owlbear Rodeo"            → cell_px = 100
    "foundry", "Foundry VTT"              → cell_px = 100
    "fantasy grounds", "Fantasy Grounds"  → cell_px = 100
    none mentioned                        → cell_px = 100  [flag as assumed Owlbear default in output]
```

### Default cell counts by encounter type (no reference image)

When no reference image is provided and the user does not specify dimensions, select defaults based on encounter type:

| Encounter type | Default grid | Dimensions (at 100px) | Notes |
|---|---|---|---|
| Small room / tight encounter | 20×20 | 2000×2000px | Interior rooms, prison cells, shrines |
| Medium dungeon / standard | 30×30 | 3000×3000px | Most VTT battlemaps |
| Portrait map (taller than wide) | 20×30 | 2000×3000px | Trail maps, vertical corridors |
| Wide map (wider than tall) | 30×20 | 3000×2000px | Riverbanks, road encounters, open fields |
| Large set-piece / boss arena | 40×40 | 4000×4000px | Boss rooms, major landmarks |

All defaults stay well under the 8000px long-edge limit for Owlbear Rodeo.

### Calculating dimensions from a reference image with visible grid

If the reference image contains a visible painted grid:

```
count_cells_from_reference(image):
    cols = count visible grid columns
    rows = count visible grid rows
    cell_px = round(image_width / cols)      # estimated PPI from original

    # Snap to platform cell size
    target_px = detect_vtt_platform(user_request)   # e.g. 100

    output_width  = cols × target_px
    output_height = rows × target_px

    # Validate long edge
    if max(output_width, output_height) > 8000:
        scale down cols/rows proportionally and flag warning

    return cols, rows, output_width, output_height
```

If the grid is not clearly visible or countable → estimate from image proportions and typical encounter size. Flag result as **"estimated — verify in VTT"** in the output block.

### Calculating dimensions from a reference image without visible grid

Estimate cell count from image proportions matched to the nearest encounter type default. Flag as estimated in the output block.

### VTT Import Output Block

Every Generation and Prompt Mode output must end with this block:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VTT IMPORT
  Suggested filename : BT_[MapConcept]_[cols]x[rows]
  Grid               : [cols] columns × [rows] rows
  Cell size          : [cell_px]px per cell  ([platform])
  Image dimensions   : [width]×[height]px
  No grid painted    : ✓  (enable grid in your VTT)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Filename notes:
- Use the map concept or location name for `[MapConcept]` — short, no spaces (use underscores).
- If cell count was estimated from a gridless reference, append `_est`: `BT_Trail_14x21_est`
- Do not include file extension — the image generator determines the format.
- For Owlbear Rodeo: this filename enables automatic grid alignment on upload.

Example outputs:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VTT IMPORT
  Suggested filename : BT_Trail_14x21
  Grid               : 14 columns × 21 rows
  Cell size          : 100px per cell  (Owlbear Rodeo)
  Image dimensions   : 1400×2100px
  No grid painted    : ✓  (enable grid in your VTT)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VTT IMPORT
  Suggested filename : BT_CaveDungeon_32x24
  Grid               : 32 columns × 24 rows
  Cell size          : 100px per cell  (Owlbear Rodeo)
  Image dimensions   : 3200×2400px
  No grid painted    : ✓  (enable grid in your VTT)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VTT IMPORT
  Suggested filename : BT_VolcanicForge_20x20
  Grid               : 20 columns × 20 rows
  Cell size          : 70px per cell  (Roll20)
  Image dimensions   : 1400×1400px
  No grid painted    : ✓  (enable grid in your VTT)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## Contrast Policy

**Default: Balanced to soft contrast.** VTT maps must remain visually comfortable during long sessions.

**Avoid:** crushed black shadows, overly bright edge highlights, aggressive rim lighting, extreme saturation, noisy texture contrast, dramatic lighting competing with gameplay clarity.

**Prefer:** balanced-to-soft value range, readable terrain hierarchy, controlled focal emphasis, natural material blending, gentle shadow depth.

Entrances, bridges, shrines, hazards, and major interactables may receive slightly stronger contrast for readability.

**Styles overriding this default:** Diablo-like, Grimdark, Darkest Dungeon-like, and Noir use intentionally high contrast. Maintain walkable readability even in these styles.

**User overrides:** if user requests high contrast, cinematic lighting, dramatic shadows, or horror atmosphere — apply while preserving readability.

## Lighting Rules

User provides lighting → use exactly. Otherwise select readable atmospheric lighting appropriate to the environment.

**Default:** Soft ambient light, restrained shadows, no pitch-black areas, no blown highlights, clear walkable spaces.

**High detail intensity addition:** Apply ambient occlusion — micro-shadows under every individual pebble, root, blade of grass, and debris asset. Use directional shading to define elevation breaks and slopes organically. Volumetric light shafts where the environment supports them (forest canopy, cave openings, broken ruins). These depth cues replace the need for painted elevation lines.

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

Use environmental details to imply inhabitants, events, history, and hazards. Never place props that block movement, hide the grid, or clutter narrow corridors.

**Universal props (any environment):** Bones, rubble, cracked stone, ropes, broken weapons, cloth scraps, coins, ash, dust, mushrooms, moss, puddles, broken furniture, campfire remains, claw marks, scratches, broken statues, collapsed masonry, parchment (no readable text), magical stains (no readable runes).

**Environment-specific props** → see `references/environment-presets.md` for the full prop catalog per environment.

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

## Doors, Entrances, Paths, and Landmarks

Preserve all doors, cave mouths, entrances, exits, tunnels, stairs, bridges, paths, and elevation cues from the reference.

Entrances and important landmarks may receive slightly stronger focal emphasis. Use: shadowed cave mouths, worn thresholds, debris trails, subtle light falloff at transitions, framing rocks, broken masonry, path wear, footprints, or cart marks.

Do not create new paths unless the reference already shows them.

## Reference Image: Blueprint Protocol

When a reference image is provided, apply the two-pass model:

**Structure (preserve exactly):** path routing, cliff-line tiers, clearing shapes, rock/object coordinates, room boundaries, corridor widths, entrances, exits, stairs, bridges, elevation breaks, and navigation flow.

**Surface (replace entirely):** erase all source visual content — art style, painted textures, ink linework, flat colors, illustrative details. Rebuild from scratch using the target aesthetic style and environment assets.

### Negative prompt block — source style erasure

Inject when the reference has a distinct illustrative art style (hand-drawn, cartoon, ink linework, stylized cross-hatching, flat painted) that differs from the target:

```
No hand-drawn linework, no baked-in ink contours, no stylized cross-hatching, no cartoon borders, no trace of the original map's illustrative texture or flat painted surfaces.
```

### Grid artifact rejection — always inject when reference has a painted grid

```
Completely ignore the reference image's gridlines. Do not interpret grid lines as cracks, paths, stone edges, texture boundaries, or terrain features. The final output must have an uninterrupted, seamless floor surface.
```

## Handling Readable Text in Source

If reference image contains title text, compass, scale text, room labels, numbers, or visible annotations → remove all from final output. Replace with blank terrain, natural texture, or abstract decorative shapes.

Assume all visible labels and map UI should be removed for the player-facing map.

If reference image contains title text, compass, scale text, room labels, numbers, or visible annotations → remove all from final output. Replace with blank terrain, natural texture, or abstract decorative shapes.

Assume all visible labels and map UI should be removed for the player-facing map.

## DM Map Variant

When `dm_mode` is active, creature and NPC placement replaces the standard "no creatures" rule. All other VTT rules (perspective, grid, contrast, text restrictions) remain in full effect.

### What DM mode changes vs. player mode

| Aspect | Player Version | DM Version |
|---|---|---|
| Creatures / NPCs | Converted to environmental props | Illustrated in position on the map |
| Creature rendering | None | Figures in the environment, consistent with aesthetic style |
| Spoilers | Hidden | Visible — creature placement, ambush positions, hidden occupants |
| Prop storytelling | Full creature-to-prop conversion | Props remain AND creatures are added alongside them |
| Text / labels | Never | Still never — positions implied visually, not labeled |

### Creature Placement Specification

Use this format when building or prompting creature placement. The user may provide this directly, or the AI may derive it from the encounter description.

```
Creatures:
[AREA / ROOM] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
[AREA / ROOM] — [CREATURE TYPE], [COUNT], [BEHAVIOR / STATE], [POSITION HINT]
```

Examples:
```
Creatures:
Central Chamber    — Adult Red Dragon, 1, coiled at rest across treasure pile, center-left
Guard Post North   — Hobgoblin Soldiers, 3, patrol stance near door, spread across north zone
Prison Cell B      — Chained Prisoner (NPC), 1, seated against wall, center cell
Collapsed Passage  — Giant Spider, 2, clinging to ceiling rubble, upper-right corner
```

**Behavior / State options:** resting, sleeping, patrol stance, alert combat-ready, coiled/crouched, feeding, fleeing, guarding an object, stationary ritual, hiding (partially concealed), emerging from surface/water.

**Position hints:** center, north/south/east/west zone, near door/altar/entrance, spread across area, clustered, flanking.

### Creature Rendering Style for DM Maps

- Render creatures as **illustrated figures in the environment**, consistent with the selected aesthetic style.
- Creatures should feel physically present in the scene — not floating overlays, not token circles.
- Use the aesthetic style to guide rendering: a Diablo-like map gets dark dramatic creature illustration; Ink & Parchment gets crosshatch-style creature figures; WoW-like gets clean stylized silhouettes.
- Creatures must not **block tactical readability**: keep figures scaled appropriately to the grid, partially transparent footprint areas where needed, creature silhouette should not obscure doorways, paths, or stairs.
- Creature scale should be consistent with grid scale. Large creatures (dragon, giant) occupy multiple squares visually but do not erase floor beneath them.
- Multiple creatures of the same type in one area: group loosely with natural spacing, not stacked.

### Reference Images for Creatures

If the user provides reference images of specific creatures or NPCs:
- Use them as visual reference to match appearance, pose language, and distinctive features.
- Describe the creature in the prompt using the reference image as ground truth for appearance.
- For named campaign-specific creatures (custom monster, specific NPC), reference images significantly improve output quality.

If no reference images provided:
- Describe creatures by type, archetype, and behavior state.
- Do not ask for references unless the creature is clearly custom or campaign-specific and a reference would meaningfully improve the result. Use judgment — a generic "hobgoblin patrol" does not need a reference; a "unique named NPC sorcerer" does.
- Never block output waiting for a reference image. Proceed with type-based description.

### DM Generation Checklist Additions

These replace/extend the player checklist items for DM mode:

- [ ] Creatures are illustrated in position, consistent with aesthetic style
- [ ] Creature scale matches grid scale
- [ ] Creature placement follows the specification (area, behavior, position)
- [ ] Creature reference images used if provided
- [ ] Props from player version are retained alongside creatures
- [ ] Grid and walkable spaces remain readable under creature placement
- [ ] No creature blocks doorways, stairs, bridges, or critical paths
- [ ] No visible text, labels, or creature name tags

---

## Correction Mode

When the user requests a change after seeing a generated result, apply directly and minimally.

**Rules:**
- Change only what was explicitly requested.
- Preserve everything else: layout, aesthetic style, color palette, lighting direction, grid, all props and regions outside the changed element.
- If change is **localized** (one room, one prop, one area) → apply only to that element.
- If change is **global** (lighting, mood, contrast, overall style) → apply consistently while preserving layout and topology.
- Do not regenerate the entire map unless the user explicitly says "redo the map," "start over," or "generate a new version."

No template needed. Interpret the user's correction naturally and apply the minimum necessary change.

## Final Quality Checklist

Before producing any VTT output, verify the applicable items.

**All VTT outputs:**
- [ ] Correct mode selected (Prompt / Generation / Correction)
- [ ] Correct variant selected (Player / DM) — player is default
- [ ] Default aesthetic is Style A unless overridden
- [ ] Contrast is soft-to-balanced unless style or user requires otherwise
- [ ] Reference layout and dimensions preserved exactly (if provided)
- [ ] Map is fully top-down orthographic
- [ ] Grid is NOT painted unless user explicitly requested it (default: no painted grid)
  - If grid was requested: subtle, integrated, low contrast, no labels
  - VTT Import block is present at the end of output with filename, cell count, cell size, and dimensions
- [ ] No visible text, labels, numbers, or UI elements
- [ ] Walkable spaces are clear and unobstructed
- [ ] Entrances, landmarks, and key features are readable
- [ ] Lighting supports gameplay clarity
- [ ] Detail intensity matches the request
- [ ] Environment props match selected environment preset
- [ ] Aesthetic style is correctly applied
- [ ] Map is comfortable for long VTT sessions

**Player variant only:**
- [ ] No visible creatures unless explicitly requested
- [ ] All creature presence converted to environmental storytelling props

**DM variant only:**
- [ ] Creature placement specification was captured or derived
- [ ] Creatures illustrated in position, consistent with aesthetic style
- [ ] Creature scale is appropriate to grid scale
- [ ] Props from player version retained alongside creature placement
- [ ] No creature blocks doors, stairs, corridors, or critical paths
- [ ] Reference images for creatures used if provided
