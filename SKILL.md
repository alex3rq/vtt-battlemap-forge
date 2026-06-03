---
name: vtt-battlemap-forge
description: Unified VTT battlemap, token, and scene-art assistant. Five modes — Prompt (convert description into image-generation prompt), Generation (create player-facing VTT battlemap), Correction (targeted fix to previously generated map), Scene Art (cinematic key-art / scene illustration prompts based on map environment and moments), Token (VTT tokens for creatures, NPCs, and monsters — four types: Portrait/Pog, Frameless Portrait, Top-Down, Isometric/Standee). Prompt, Generation, and Scene Art modes support an optional DM variant that includes creature and NPC placement. Player-facing is always the default. Use when user asks to create, generate, or fix a battlemap, dungeon map, encounter map, or VTT map; asks for splash art, key art, scene illustration, or cinematic view of a map location; or asks for a VTT token, creature token, NPC token, or character portrait token. Supports 17 aesthetic styles and 11 environment presets.
license: MIT
metadata:
  version: "2.0"
---

# VTT Battlemap Forge

Unified VTT battlemap, token, and scene-art assistant. Five operating modes: Prompt, Generation, Correction, Scene Art, Token.

## Reference Map

Load only the references needed for the active mode. Do not load all files by default.

| File | Purpose | Load when |
|---|---|---|
| `references/aesthetic-styles.md` | 17 rendering style definitions | Any mode requiring style selection |
| `references/environment-presets.md` | 11 biome/terrain presets | Any mode requiring environment selection |
| `references/vtt-core-rules.md` | Perspective, grid, contrast, creatures, lighting, traps, correction rules, DM map variant, quality checklist | Prompt, Generation, or Correction mode |
| `references/prompt-templates.md` | Compact and Verbose prompt templates — player and DM variants | Prompt mode only |
| `references/scene-art-mode.md` | Scene Art flow, moment suggestions, cinematic prompt template — player and DM variants | Scene Art mode only |
| `references/token-mode.md` | Token rules, composition, border breakout, frame, background, prompt templates, quality checklist | Token mode only |

## Mode Selection

**Prompt Mode** — user asks to: create/write/rewrite/compact a prompt, describe style, prepare instructions for another image AI, convert room notes or area descriptions into a prompt.

**Generation Mode** — user asks to: generate an image, create a battlemap, make/redraw a map, repaint a reference, turn a description or reference into a VTT map.

**Correction Mode** — user requests a change after seeing a generated result: fix/adjust/change a specific area, brighten/darken lighting, add/remove/replace a prop, make a path or door clearer, change mood/contrast/detail globally.

**Scene Art Mode** — user asks for: splash art, key art, scene illustration, cinematic view, player handout art, alternate perspective of the map, art showing the environment from inside the location, or a dramatic moment based on the map. Scene Art is not a VTT battlemap mode.

**Token Mode** — user asks to create a VTT token, creature token, NPC token, monster token, portrait token, circular token, Roll20/Foundry token, or asks to convert a character/creature image into a 1:1 token. Also triggers for top-down tokens, isometric standee tokens, frameless portrait tokens.

Token Mode is inherently creature-focused — there is no DM variant. The token itself is the subject.

Token Mode triggers:
"token", "VTT token", "creature token", "monster token", "NPC token", "portrait token", "circular token", "make a token", "create a token", "Foundry token", "Roll20 token", "focus on the face", "face token", "1:1 token", "character token", "generate a token", "top-down token", "overhead token", "isometric token", "standee", "standee token", "frameless token", "borderless token", "no frame token".

For full Token Mode rules, see `references/token-mode.md`.

If intent is ambiguous → infer the most likely mode from context. Ask for clarification only if the request cannot be interpreted usably.

## DM Variant Flag

DM variant is an optional modifier available in Prompt, Generation, and Scene Art modes. **Player-facing is always the default.** Only activate DM variant when clearly requested.

**DM variant triggers:** "DM version," "DM view," "GM version," "game master map," "show the creatures," "include monsters," "with NPCs," "DM facing," "for the DM," "DM layer," "encounter map with creatures," or any explicit request to show creature or NPC placement.

**Correction mode** inherits the variant of the previous output — do not switch player↔DM unless the user explicitly asks.

## Execution Procedure

```
vtt_battlemap_forge(user_request, reference_image=None, creature_images=None,
                    zone_context=None):
    # zone_context = { label: "E2", description: "...", adjacent: [...] }
    # Applies to Scene Art only. See references/scene-art-mode.md.

    # 1. Mode
    mode = select_mode(user_request)
    # "prompt" | "generation" | "correction" | "scene_art" | "token"

    # 2. DM variant flag — default False (player-facing)
    dm_mode = detect_dm_mode(user_request)

    # 3. Style — references/aesthetic-styles.md
    style = select_aesthetic(user_request)
    # Default: Style B

    # 4. Environment — references/environment-presets.md
    env = select_environment(user_request)
    # Default: derive from concept, or generic stone/earth dungeon

    # 5. VTT platform and cell dimensions
    platform, cell_px = detect_vtt_platform(user_request)
    # Default: Owlbear Rodeo, 100px per cell
    # See references/vtt-core-rules.md — Grid Dimensions Math

    # 6. Grid painted — default OFF
    paint_grid = user_explicitly_requested_grid(user_request)
    # Only paint a grid if user says "with grid", "show the grid", etc.

    if mode == "scene_art":
        load(references/scene-art-mode.md)
        execute_scene_art_flow(user_request, style, env, dm_mode,
                               creature_images, reference_image, zone_context)
        return

    # Token mode — see references/token-mode.md
    if mode == "token":
        load(references/token-mode.md)
        token_type = select_token_type(user_request)  # default: portrait_pog
        # "portrait_pog" | "frameless_portrait" | "top_down" | "isometric_standee"
        frame_color = select_frame_color(user_request)   # default: red; portrait_pog only
        framing    = select_framing(user_request)        # portrait_pog and frameless only
        build_token_prompt(user_request, token_type, style, env, frame_color, framing,
                           reference_image)
        output_in_code_block(prompt)
        if token_type == "isometric_standee":
            append_standee_warning()
        return

    # VTT modes only
    detail   = select_detail(user_request)          # Default: Medium
    lighting = select_lighting(user_request, env)   # references/vtt-core-rules.md

    load(references/vtt-core-rules.md)

    if mode == "prompt":
        load(references/prompt-templates.md)
        variant = "dm" if dm_mode else "player"
        dims = snap_to_cell_grid(reference_image, user_request, cell_px)
        prompt = build_prompt(user_request, style, env, detail, lighting,
                              reference_image, variant, creature_images, dims)
        output_in_code_block(prompt)
        output_vtt_import_block(dims, platform, cell_px, map_concept, paint_grid)

    elif mode == "generation":
        assert_perspective_rules()
        dims = snap_to_cell_grid(reference_image, user_request, cell_px)
        # dims = { cols, rows, width_px, height_px, estimated: bool }
        # See references/vtt-core-rules.md — Grid Dimensions Math
        apply_grid_policy(reference_image, paint_grid)
        apply_contrast_policy(style)
        apply_environmental_dressing(env, detail)
        if reference_image:
            preserve_layout_and_topology_exactly(reference_image)
            # dimensions come from snap_to_cell_grid, not raw image size
        if dm_mode:
            apply_dm_creature_layer(user_request, creature_images)
        else:
            assert_no_text_or_creatures()
        generate_image(dims)
        output_vtt_import_block(dims, platform, cell_px, map_concept, paint_grid)

    elif mode == "correction":
        apply_correction(user_request, previous_result)
        # Change only what was requested. Preserve everything else.
        # Preserve player/DM variant of previous output unless user explicitly switches.

    verify_checklist(dm_mode)
```

## Global VTT Priorities

Every VTT output (Prompt, Generation, Correction) must prioritize, in this order:

1. Player-facing usability
2. Tactical readability and clear walkable spaces
3. No painted grid by default — VTT overlays its own grid
4. Clean top-down orthographic presentation
5. Long-session visual comfort
6. Controlled prop density
7. Professional quality appropriate to chosen style
8. VTT Import block always present at end of output (filename, cell count, cell size, dimensions)

**Gameplay clarity beats cinematic drama** unless the chosen style explicitly calls for dramatic presentation (Diablo-like, Darkest Dungeon-like, Grimdark).

## Reference Image Priority

If a reference image is provided, it is the absolute source of truth for: layout, geometry, topology, room shapes, cave silhouettes, wall placement, corridor width, path placement, entrances, exits, stairs, bridges, elevation cues, inset rooms, separated regions, overall playable structure, grid scale, grid alignment, and image dimensions/aspect ratio.

Treat as a professional paint-over, redraw, or style transfer.

**Do NOT:** redesign the map, invent new rooms, remove existing areas, move walls, widen/narrow corridors, add/remove paths, rotate/crop/rescale the map, or block gameplay paths with oversized props.

Area descriptions are for environmental dressing only — not permission to change layout.

Exception: image edges may be blended or extended to create a believable border environment.

## Dimensions and Aspect Ratio

**VTT map modes only (Prompt, Generation, Correction).** Scene Art has its own dimension defaults — see `references/scene-art-mode.md`.

If reference image provided → count grid cells from visible gridlines (if present) to derive exact column/row count, then calculate output dimensions as `cols × cell_px` and `rows × cell_px` using the target platform cell size. If no grid visible, estimate from proportions and flag as estimated. See `references/vtt-core-rules.md` — Grid Dimensions Math.

If no reference image:

| Format | Grid | Dimensions (100px/cell) | Recommended Use |
|---|---|---|---|
| Square | 20×20 | 2000×2000px | **Default.** Small rooms, shrines, interior encounters |
| Square medium | 30×30 | 3000×3000px | Most VTT battlemaps |
| Portrait | 20×30 | 2000×3000px | Trail maps, vertical corridors |
| Wide | 30×20 | 3000×2000px | Road encounters, riverbanks, open fields |
| Large | 40×40 | 4000×4000px | Boss arenas, major set-pieces |

Default to **30×30 at 100px (3000×3000px)** for a standard battlemap with no other context. All values stay under the 8000px long-edge limit for Owlbear Rodeo.

## Style and Environment Selection

1. User names specific style letter or environment number → use exactly
2. User names style alias → match via reference files
3. User names only aesthetic → pair with environment best matching map concept
4. User names only environment → pair with Style B (default)
5. User names neither → Style B + environment best matching concept
6. No environment apparent → generic stone/earth dungeon

### Combination Examples

| Request | Aesthetic | Environment |
|---|---|---|
| "gritty jungle cave" | Style J (Gritty Dark Fantasy) | Env 2 (Cave) + 6 (Jungle) blend |
| "grimdark swamp" | Style G (Grimdark) | Env 8 (Swamp) |
| "WoW-style frozen ruins" | Style W (WoW-like) | Env 5 (Arctic) + 1 (Ruins) blend |
| "muted ethereal plane" | Style M (Muted) | Env 11 (Arcane) |
| "clean urban sewer" | Style H (Premium Clean) | Env 4 (Urban/Sewer) |
| "Diablo hellfire dungeon" | Style D (Diablo-like) | Env 7 (Volcanic/Infernal) |
| "ink parchment cave" | Style I (Ink & Parchment) | Env 2 (Cave) |
| "FF14 ancient ruins" | Style F (FF14-like) | Env 1 (Ruins) |
| "darkest dungeon crypt" | Style K (Darkest Dungeon-like) | Env 1 (Ruins) or generic dungeon |
| "generic dungeon" | Style B (Default) | Generic stone dungeon |

## Detail Intensity

If user does not specify, use **Medium**.

| Level | Aliases | Description |
|---|---|---|
| **Low** | low, sparse, clean, minimal props, maximum readability | Sparse props, essential storytelling only, clean walkable spaces. Best for small rooms, narrow corridors, complex layouts. |
| **Medium** *(default)* | medium, balanced, normal, readable detail | Balanced environmental storytelling, readable prop placement, clear walkable spaces. Best for most VTT battlemaps. |
| **High** | high, rich, decorative, premium detail, atmospheric detail | Rich surface texture, layered debris, strong visual storytelling. Paths, doorways, stairs, bridges, and combat spaces must remain readable. Best for boss arenas, scenic ruins, set-piece locations. |
