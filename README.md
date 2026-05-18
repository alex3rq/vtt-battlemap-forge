<!-- ============================================================ -->
<!-- TIER 1: ABOVE THE FOLD                                         -->
<!-- ============================================================ -->

<div align="center">

  <h1>vtt-battlemap-forge</h1>
  <p>One skill, three modes — generate VTT battlemaps, craft image prompts, or apply surgical corrections without redoing the whole map</p>
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

- **Three operating modes** — Prompt Mode (craft image-generation prompts for external AIs), Generation Mode (create battlemaps directly), Correction Mode (apply targeted fixes without regenerating)
- **17 aesthetic styles** — Naturalistic Hand-Painted, Baldur's Gate 3-like, Diablo-like, FF14-like, Darkest Dungeon-like, WoW-like, Watercolor, 3D Render, and more
- **11 environment presets** — Ancient Ruins, Natural Caves, Aquatic, Urban/Sewer, Arctic, Jungle, Volcanic, Swamp, Desert, Forest, Arcane/Planar
- **VTT-native defaults** — Top-down orthographic perspective, subtle integrated grid, no visible creatures or text, balanced contrast for long sessions
- **Reference image as layout lock** — Provide a reference image and the skill treats it as source of truth for geometry, preserving all room shapes, corridor widths, and grid alignment
- **Contrast policy per style** — Soft-to-balanced for most styles, high contrast for Diablo-like/Grimdark/Darkest Dungeon/Noir

## Quick Start

| Prompt | Result |
|--------|--------|
| "Write a prompt for an ancient ruins map, FF14 style" | Returns a compact image-generation prompt in a code block |
| "Generate a jungle beach battlemap, Baldur's Gate 3 style"<br>*— the kind where a certain sharp-eared rogue dramatically introduces himself* | Creates a VTT-ready battlemap image directly |
| "Brighten the altar room and add more rubble" | Applies a targeted correction to a previously generated map |

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

vtt-battlemap-forge selects one of three modes based on user intent, picks an aesthetic style (default: Naturalistic Hand-Painted) and environment preset (derived from concept), then applies VTT domain rules — top-down orthographic perspective, subtle grid, contrast policy, creature-to-prop conversion table, and environment-specific prop catalog — to produce a map or prompt.

→ [Full SKILL.md](SKILL.md) for the complete rule set

## What's Inside

```text
SKILL.md                              — Execution procedure, VTT rules, prompt templates
references/
  aesthetic-styles.md                 — 17 aesthetic rendering styles with aliases, palettes, and best-use guidance
  environment-presets.md              — 11 environment presets with terrain, props, palette, and lighting defaults
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
