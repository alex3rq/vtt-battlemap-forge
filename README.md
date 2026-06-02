<!-- ============================================================ -->
<!-- TIER 1: ABOVE THE FOLD                                         -->
<!-- ============================================================ -->

<div align="center">

  <h1>vtt-battlemap-forge</h1>
  <p>One skill, five modes — generate VTT battlemaps, craft image prompts, apply surgical corrections, create cinematic scene art from your map locations, or forge premium circular creature tokens</p>
</div>

<div align="center">

[![License: MIT][license-shield]][license-url]
[![Agent Skills][skills-shield]][skills-url]

  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://ik.imagekit.io/alex3rq/Git/vtt-battlemap-forge/logo-vtt-battlemap-forge.png">
    <source media="(prefers-color-scheme: light)" srcset="https://ik.imagekit.io/alex3rq/Git/vtt-battlemap-forge/logo-vtt-battlemap-forge.png">
    <img alt="vtt-battlemap-forge logo" src="https://ik.imagekit.io/alex3rq/Git/vtt-battlemap-forge/logo-vtt-battlemap-forge.png" width="600">
  </picture>

</div>

<div align="center">
  <a href="#the-problem">Why</a> &middot;
  <a href="#quick-start">Quick Start</a> &middot;
  <a href="#usage">Usage</a> &middot;
  <a href="#install">Install</a>
</div>

<br>

[Agent Skills](https://agentskills.io) compatible — works with Claude Code, Codex, Cursor, Windsurf, GitHub Copilot, and other Agent Skills adopters.

---

<!-- ============================================================ -->
<!-- TIER 2: SCAN QUICKLY                                          -->
<!-- ============================================================ -->

## The Problem

VTT battlemap creation requires balancing artistic quality, tactical readability, grid alignment, and player-facing usability — all while following strict top-down orthographic conventions. Switching between tools for prompt engineering, image generation, and post-generation fixes wastes session prep time. Most general-purpose image AIs lack VTT domain knowledge: they add creatures, text labels, perspective distortion, or UI elements that break tabletop use.

vtt-battlemap-forge embeds VTT domain expertise directly into an Agent Skills workflow. Describe what you need, get a usable map or a tuned prompt, and apply corrections surgically.

## Features

- **Five operating modes** — Prompt Mode (craft image-generation prompts), Generation Mode (create battlemaps), Correction Mode (targeted fixes), Scene Art Mode (cinematic key art and scene illustrations from map locations), Token Mode (VTT tokens for creatures, NPCs, and monsters)
- **Four token types** — Portrait/Pog (circular framed face-first bust, default), Top-Down (overhead bird's-eye sihouette view), Isometric/Standee (2.5D upright standee with base plate), Frameless Portrait (borderless bust with soft vignette). Each type has dedicated composition rules and prompt templates
- **DM variant** — Optional creature and NPC placement layer for Prompt, Generation, and Scene Art modes. Player-facing by default; DM variant activated on request
- **17 aesthetic styles** — Naturalistic Hand-Painted, Baldur's Gate 3-like, Diablo-like, FF14-like, Darkest Dungeon-like, WoW-like, Watercolor, 3D Render, and more
- **11 environment presets** — Ancient Ruins, Natural Caves, Aquatic, Urban/Sewer, Arctic, Jungle, Volcanic, Swamp, Desert, Forest, Arcane/Planar
- **VTT-native defaults** — Top-down orthographic perspective, subtle integrated grid, no visible creatures or text, balanced contrast for long sessions
- **Reference image as layout lock** — Reference image is source of truth for geometry, preserving all room shapes, corridor widths, and grid alignment
- **Scene Art with zone context** — Cinematic non-map illustrations grounded in the same environment and style; supports zone labels, adjacent area descriptions, map reference images, and moment suggestions
- **Contrast policy per style** — Soft-to-balanced for most styles, high contrast for Diablo-like/Grimdark/Darkest Dungeon/Noir

## Quick Start

| Prompt | Result |
|--------|--------|
| "Write a prompt for an ancient ruins map, FF14 style" | Returns a compact image-generation prompt in a code block |
| "Generate a jungle beach battlemap, Baldur's Gate 3 style" | Creates a VTT-ready battlemap image directly |
| "Brighten the altar room and add more rubble" | Applies a targeted correction to a previously generated map |
| "Create splash art for the volcanic forge — player-facing" | Returns a cinematic scene illustration prompt from the map's environment and style |
| "Create a token for a dragonborn paladin, WoW-like style" | Returns a face-first Portrait/Pog token prompt with circular frame and border breakout |
| "Create a top-down token for a hobgoblin captain" | Returns an overhead bird's-eye token prompt — silhouette-first, solid dark background |
| "Make an isometric standee for an elven ranger" | Returns a 2.5D upright standee prompt with base plate and standee warning note |
| "Frameless token for a vampire lord, Diablo style" | Returns a borderless bust prompt with soft vignette edge, no circular rim |
| "Generate a DM version with goblin ambush positions" | Creates a battlemap with creatures placed in position on the map |

## Usage

**Trigger phrases that activate this skill:**

```text
"generate a battlemap"
"create a VTT map"
"make a dungeon map"
"generate an encounter map"
"write a battlemap prompt"
"compact this prompt"
"fix the lighting in the cave"
"change the grid on that map"
"apply Style G to this dungeon"
"redraw this map in watercolor"
"add a hidden pit trap to area B2"
"convert this room description into a prompt"
"create splash art for this map"
"make a cinematic scene illustration"
"generate a DM version with creatures"
"show me a key art view of this dungeon"
"player handout art for the boss arena"
"create a VTT token"
"make a monster token"
"generate an NPC token"
"circular token portrait"
"Foundry token for this creature"
"top-down token"
"overhead token"
"isometric token"
"standee token"
"frameless token"
"borderless token portrait"
```

**Example — Prompt Mode:**

> User: "Write a compact prompt for a frozen cave with an ancient altar, Muted style"
>
> vtt-battlemap-forge will output a filled compact prompt template inside a code block with:
> - Aesthetic Style M (Muted Soft-Contrast)
> - Environment 5 (Arctic) + 1 (Ancient Ruins) blend
> - Soft ambient lighting with faint warm accents
> - Area dressing: ice formations, frost-covered altar, snow drifts

**Example — Generation Mode:**

> User: "Generate a Diablo-like volcanic forge battlemap"
>
> vtt-battlemap-forge will:
> 1. Select Style D (Diablo-like) + Environment 7 (Volcanic/Infernal)
> 2. Apply dramatic lava-lit ambient with near-black upper shadows
> 3. Include obsidian slag, scorch marks, ash deposits, iron chains
> 4. Generate a top-down 2048x2048 image with subtle integrated grid
> 5. Ensure no visible creatures, text, or UI elements

**Example — Correction Mode:**

> User: "The central bridge is too dark — make it more visible"
>
> vtt-battlemap-forge will brighten the bridge area while preserving everything else: layout, style, palette, lighting direction, grid, and all other props and regions.

**Example — Scene Art Mode (Player):**

> User: "Create splash art for the Diablo-like volcanic forge, player-facing"
>
> vtt-battlemap-forge will:
> 1. Suggest 3–6 cinematic moments from the forge environment (main chamber reveal, forge anvil close-up, lava channel threshold, etc.)
> 2. Use Style D (Diablo-like) + Environment 7 (Volcanic/Infernal) for visual grounding
> 3. Output a cinematic 16:9 prompt with camera direction, lighting, mood, and key visual elements
> 4. Keep it spoiler-free — no creature reveals, hidden content, or DM-only information

**Example — Token Mode (Portrait / Pog — default):**

> User: "Create a token for a lizardfolk shaman with a bone staff, swamp environment, Diablo-like style"
>
> vtt-battlemap-forge will:
> 1. Load token-mode.md rules
> 2. Select token type: Portrait/Pog (default)
> 3. Select Style D (Diablo-like) + Environment 8 (Swamp) for visual grounding
> 4. Apply face-first composition: face, crest, and staff as focal points
> 5. Use bold red circular frame with controlled border breakout — crest, staff tip, and shoulders extending beyond the frame
> 6. Specify murky swamp mist inside the frame; solid dark outer area for clean background removal
> 7. Output a compact Portrait/Pog token prompt

**Example — Token Mode (Top-Down):**

> User: "Create a top-down token for a hobgoblin captain"
>
> vtt-battlemap-forge will:
> 1. Select token type: Top-Down
> 2. Apply strict overhead bird's-eye composition — head, shoulders, back, weapons visible from directly above
> 3. Specify facing direction readable from the silhouette
> 4. Use solid black background for easy background removal
> 5. No circular frame — the silhouette defines the token shape
> 6. Output a compact Top-Down token prompt

**Example — Token Mode (Isometric / Standee):**

> User: "Make an isometric standee for an elven ranger"
>
> vtt-battlemap-forge will:
> 1. Select token type: Isometric/Standee
> 2. Apply 2.5D isometric perspective — full body, upright, on an oval base plate
> 3. Key light from upper-left (isometric convention)
> 4. Solid dark background for clean background removal
> 5. Output a compact Isometric/Standee token prompt
> 6. Append standee warning note: token is designed for isometric battlemaps; on top-down maps it will appear as if the character is lying flat

**Example — Token Mode (Frameless Portrait):**

> User: "Frameless token for a vampire lord, Diablo style"
>
> vtt-battlemap-forge will:
> 1. Select token type: Frameless Portrait
> 2. Apply face-first bust composition with no circular border ring
> 3. Background fades to near-black at all edges via soft painterly vignette
> 4. No frame color selection — no rim rendered
> 5. Output a compact Frameless Portrait token prompt

**Example — DM Variant (Generation):**

> User: "Generate a cave ambush map, DM version — hobgoblin patrol in the north passage, giant spider on the ceiling near the collapsed tunnel"
>
> vtt-battlemap-forge will:
> 1. Create the player-facing cave map with environmental props (weapon racks, shed chitin, etc.)
> 2. Add a Creatures section: hobgoblin soldiers in patrol stance near north passage; giant spider clinging to ceiling rubble near collapsed tunnel
> 3. Render creatures as illustrated figures consistent with the aesthetic style — no token circles or labels

## Install

```bash
npx skills add alex3rq/vtt-battlemap-forge
```

**Manual registration** (clone + symlink):

```bash
git clone https://github.com/alex3rq/vtt-battlemap-forge ~/skills/vtt-battlemap-forge

# Register only in roots you actually use
ln -sfn ~/skills/vtt-battlemap-forge ~/.claude/skills/vtt-battlemap-forge      # Claude Code
ln -sfn ~/skills/vtt-battlemap-forge ~/.agents/skills/vtt-battlemap-forge      # Codex
ln -sfn ~/skills/vtt-battlemap-forge ~/.copilot/skills/vtt-battlemap-forge     # VS Code / GitHub Copilot
ln -sfn ~/skills/vtt-battlemap-forge ~/.cursor/skills/vtt-battlemap-forge      # Cursor
```

---

<!-- ============================================================ -->
<!-- TIER 3: SUPPORTING CONTENT                                    -->
<!-- ============================================================ -->

## How It Works

vtt-battlemap-forge selects one of five modes based on user intent, picks an aesthetic style (default: Naturalistic Hand-Painted) and environment preset (derived from concept), then applies VTT domain rules — top-down orthographic perspective, subtle grid, contrast policy, creature-to-prop conversion table, and environment-specific prop catalog — to produce a map or prompt. Scene Art Mode follows a separate cinematic flow: moment suggestions, camera selection, and non-top-down illustration prompts grounded in the same environment and style. Token Mode creates one of four token types — Portrait/Pog (circular framed face-first bust), Top-Down (overhead bird's-eye silhouette), Isometric/Standee (2.5D upright standee), or Frameless Portrait (borderless bust with vignette edge) — each with its own composition rules, background strategy, and prompt template. An optional DM variant adds creature and NPC placement to Prompt, Generation, and Scene Art outputs.

→ [Full SKILL.md](SKILL.md) for the complete rule set

## What's Inside

```text
SKILL.md                              — Execution procedure, VTT rules, mode selection, DM variant
references/
  aesthetic-styles.md                 — 17 aesthetic rendering styles with aliases, palettes, and best-use guidance
  environment-presets.md              — 11 environment presets with terrain, props, palette, and lighting defaults
  vtt-core-rules.md                   — Perspective, grid, contrast, creatures, lighting, traps, correction rules, DM map variant, quality checklist
  prompt-templates.md                 — Compact and Verbose prompt templates (player and DM variants)
  scene-art-mode.md                   — Scene Art flow, moment suggestions, cinematic prompt template, camera guide, spoiler policy (player and DM variants)
  token-mode.md                       — Token type selection (Portrait/Pog, Top-Down, Isometric/Standee, Frameless Portrait), composition rules per type, border breakout (Portrait/Pog), frame rules, background strategy with post-process guidance, prompt templates per type, quality checklist
```

## License

MIT — See [LICENSE](LICENSE) for details.

---

Crafted with [Readme Craft](https://github.com/motiful/readme-craft)

<!-- Reference-style link definitions -->
[license-shield]: https://img.shields.io/badge/License-MIT-green.svg
[license-url]: https://github.com/alex3rq/vtt-battlemap-forge/blob/main/LICENSE
[skills-shield]: https://img.shields.io/badge/Agent%20Skills-compatible-DA7857?logo=anthropic
[skills-url]: https://agentskills.io
