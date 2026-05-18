---
name: aesthetic-styles
description: Complete catalog of 17 aesthetic rendering styles for VTT battlemaps. Each style defines rendering look, artistic approach, contrast character, palette, and best-use scenarios. Styles are independent of environment — combine freely with any environment preset. Called by SKILL.md EP to select the rendering look based on user request.
---

# Aesthetic Styles

Styles control rendering look, artistic approach, and contrast character. Independent of environment — combine freely with any Environment Preset.

**If no aesthetic style is specified, use Style A.**

## Execution Procedure

```
select_aesthetic(user_request) → style

match user_request against:
    style letter code (A-W) → use exactly
    style name or alias → match to correct preset
    no style specified → default Style A

return: style description, contrast note, palette, rendering characteristics
```

## Style Index

Style letters are convenience shortcuts for users.
If user writes full style name or alias, always prioritize explicit name/alias over letter.
Some letters are intentionally mnemonic and may not follow alphabetical order.

| Code | Style |
|---|---|
| A | Naturalistic Hand-Painted |
| B | Baldur's Gate 3-like |
| C | Colorful Fantasy Adventure |
| D | Diablo-like |
| E | Painterly Expressive |
| F | FF14-like |
| G | Grimdark |
| H | Premium Clean Hand-Painted |
| I | Ink & Parchment |
| J | Gritty Dark Fantasy |
| K | Darkest Dungeon-like |
| L | Minimal Tactical |
| M | Muted Soft-Contrast |
| N | Noir / Monochrome |
| O | Watercolor |
| P | 3D Render / Game Asset |
| Q | Realistic / High-Fidelity |
| W | WoW-like |

---

## Style A – Naturalistic Hand-Painted *(Default)*

**Aliases:** default, naturalistic, balanced, hand-painted, eye-rest, long-session, low-fatigue, natural

**Description:** Naturalistic hand-painted VTT battlemap, balanced-to-soft contrast, subdued value range, restrained highlights, natural terrain blending, readable tactical spaces, gentle focal hierarchy, soft painterly textures, subtle ambient shading, integrated low-contrast grid, professional fantasy module feel.

**Best for:** Most general-purpose maps. Long sessions. Any environment where atmosphere matters but readability comes first.

---

## Style B – Baldur's Gate 3-like

**Aliases:** bg3, baldur's gate 3, larian, cinematic crpg, modern crpg, realistic fantasy rpg, premium 3d fantasy, tactical crpg

**Description:** Baldur's Gate 3-inspired VTT battlemap adapted to strict top-down orthographic view. Premium cinematic CRPG fantasy realism with richly textured environments, believable material detail, grounded architecture, and strong environmental storytelling. Stone, wood, metal, cloth, water, mud, foliage, and magical effects should feel physically present and high-fidelity, as if built from detailed modern RPG game assets. Lighting is atmospheric and dramatic but still readable for tactical play: warm torchlight, cool magical glow, soft ambient bounce, realistic cast shadows, and clear walkable spaces. Props feel lived-in and narratively meaningful — crates, books, candles, bedrolls, ritual objects, broken furniture, banners, roots, debris, bones, blood stains, alchemical clutter, or arcane residue depending on the scene. Composition should feel immersive and premium without becoming visually noisy or blocking token movement.

**Palette:** Grounded natural fantasy palette with cinematic color grading. Warm amber torchlight, cool blue-violet magical accents, mossy greens, aged stone grays, dark polished wood, tarnished brass, deep crimson for blood or danger, muted gold for sacred or noble spaces.

**Best for:** Cinematic fantasy dungeons, ancient ruins, goblin camps, noble interiors, wizard laboratories, Underdark caverns, cursed temples, tactical CRPG-style encounters, maps that need high immersion while remaining VTT-readable.

**Note:** Keep camera fully top-down and grid-friendly. Do not use angled isometric perspective even though inspiration comes from a 3D CRPG. Use shadows, material fidelity, and prop depth to imply volume while preserving clear tactical readability.

---

## Style C – Colorful Fantasy Adventure

**Aliases:** colorful, heroic, vibrant, bright fantasy, fantasy adventure, whimsical, cheerful, adventure-ready

**Description:** Colorful fantasy VTT battlemap, clean hand-painted textures, stylized realism, vibrant but controlled palette, balanced contrast, inviting adventure atmosphere, polished prop placement, clear walkable spaces, warm and welcoming presentation. Bright and exciting without sacrificing readability.

**Best for:** Heroic fantasy, bright ruins, magical locations, fae encounters, starter adventures, lighter campaign tones.

---

## Style D – Diablo-like

**Aliases:** diablo, hellfire, gothic dungeon, gothic horror game, dark rpg, diabolic, point-source dark, dark action rpg

**Description:** Diablo-inspired VTT battlemap adapted to top-down orthographic. Rich, deep environments lit almost entirely by point sources — torches, braziers, hellfire, magical glows. Deep dramatic shadows at map edges and corners, vignetting naturally toward near-black. Narrow pools of warm amber-orange light illuminate walkable areas. Gothic architecture: arched passages, cracked flagstone floors, bone and iron details. Jewel-like color accents on key features. Detailed decorative floor patterns (abstract, non-readable). Atmospheric smoke and particle effects implied in textures. High contrast appropriate and expected.

**Palette:** Near-black background, warm amber and orange light pools, cold blue-gray shadows, crimson and gold accents, sickly green for corruption or poison.

**Best for:** Gothic dungeons, demonic environments, undercity lairs, hellish planes, dark action RPG aesthetics.

---

## Style E – Painterly Expressive

**Aliases:** painterly, expressive, artistic, gestural, brushwork, impressionist, loose

**Description:** Expressive painterly VTT battlemap, visible confident brushwork, rich color mixing, loose gestural execution, strong artistic personality, textured surfaces with visible paint quality, warm impressionistic palette, readable terrain structure under an organic hand-made feel. Looks made by a skilled map artist rather than generated.

**Best for:** Maps where artistic character and mood matter as much as precision. Outdoor encounters, forested areas, scenic wilderness, maps meant to feel crafted.

---

## Style F – FF14-like

**Aliases:** ff14, final fantasy, ffxiv, grand fantasy, crystal light, square enix, mmorpg premium, high fantasy premium

**Description:** Final Fantasy XIV-inspired VTT battlemap. Grand, beautiful, and richly detailed with exceptional production quality. Elegant stonework and ornate architectural details. Rich, zone-appropriate color palette: warm gold in sacred and peaceful spaces, cold blue in magical zones, deep red in battle arenas, lush green in natural spaces. Crystal and magical light accents throughout. Balanced between high decoration and excellent readability — walkable spaces remain clear despite richness of detail. Premium polished game-map quality throughout.

**Best for:** Grand fantasy encounters, magical temples, ornate dungeons, sacred sites, high-production-value campaigns.

---

## Style G – Grimdark

**Aliases:** grimdark, warhammer, bleak, despair, oppressive, mud and blood, desaturated horror, industrial grim, berserk

**Description:** Grimdark VTT battlemap, heavily desaturated and muddy palette, near-monochromatic with selective dirty color accents, crushed and oppressive atmosphere, worn metal, rotting wood, cracked earth, implied filth and decay throughout. No warmth in lighting. Everything feels broken, hostile, and exhausted. High contrast is appropriate and expected. Maintain walkable-space readability despite oppressive aesthetic.

**Palette:** Muddy grays, desaturated browns, rust stains, sickly muted yellow, occasional dull crimson accent.

**Best for:** Warhammer-style settings, extreme dark fantasy, war-torn environments, environments where no hope is implied.

---

## Style H – Premium Clean Hand-Painted

**Aliases:** clean, premium, polished, gameplay-first, crisp, professional, readable

**Description:** Premium clean hand-painted VTT battlemap, stylized realism, controlled contrast, low visual clutter, high tactical readability, crisp wall and terrain shapes, clean walkable floors, refined material separation, subtle grid integration, polished professional top-down presentation.

**Best for:** General player-facing maps, clean dungeons, architectural spaces, tactical encounters, beginner-friendly layouts.

---

## Style I – Ink & Parchment

**Aliases:** ink, parchment, old map, cartographic, hand-drawn, dungeon sketch, old-school, classic rpg map, sepia map, illustrated map

**Description:** Hand-drawn cartographic dungeon map on aged parchment. Ink linework on cream-to-sepia paper background. Walls defined by bold ink lines, walkable floors as bare paper or light hatching. Terrain features rendered in classic dungeon-map shorthand: dot patterns for gravel, cross-hatching for rough stone, wavy lines for water. No full-color rendering — ink tones only, with optional sepia wash. Aged paper texture throughout. Feels like an artifact from the game world itself, or a classic RPG module page.

**Palette:** Aged cream and tan paper, brown and black ink lines, optional sepia wash, faint age staining.

**Best for:** Old-school dungeon crawls, in-world player handouts, maps that should feel like found artifacts, classic RPG module aesthetics.

**Note:** Grid may be rendered as faint pencil squares on paper rather than an integrated floor grid.

---

## Style J – Gritty Dark Fantasy

**Aliases:** gritty, grim, dark, dark fantasy, atmospheric dark, moody, classic dungeon, hostile, dirty

**Description:** Dark fantasy VTT battlemap, realistic hand-painted textures, rough worn surfaces, controlled moody contrast, gritty stone walls, dirty floors, scattered debris, aged and stained materials, atmospheric but readable lighting. Oppressive atmosphere with deliberate visual restraint that keeps gameplay space clear.

**Best for:** Cursed dungeons, monster lairs, crypts, hostile caves, grim fantasy locations, survival horror encounters.

---

## Style K – Darkest Dungeon-like

**Aliases:** darkest dungeon, ink illustration, gothic illustration, horror illustration, sepia horror, crosshatch dungeon, inked

**Description:** Darkest Dungeon-inspired VTT battlemap adapted to top-down view. Stark ink illustration aesthetic, heavy black linework implied in all textures, crosshatch and stipple shading on stone and wood surfaces. Desaturated base palette: sepia, deep brown, near-black. Selective color used for emphasis only — deep crimson for blood and danger, faded gold for treasure and fire. Heavy shadows at map edges and under overhangs. Torn and aged surface texture throughout. 2D illustration quality, flat rather than volumetric. Oppressive and unnerving. High contrast is integral to the style.

**Palette:** Sepia, dark brown, near-black shadow with crimson and gold accents.

**Best for:** Horror campaigns, gothic dungeons, cursed environments, old-school dungeon crawl aesthetics, players who want a hand-illustrated feel.

---

## Style L – Minimal Tactical

**Aliases:** minimal, tactical, low clutter, clear, simple, grid-first, fast read, combat-optimized

**Description:** Minimal tactical VTT battlemap, clean readable shapes, restrained detail, low-to-balanced contrast, strong wall and floor separation, very controlled prop placement, simple material definition, maximum gameplay readability, grid-first presentation. Every element serves tactical clarity.

**Best for:** Complex layouts, narrow corridors, combat-heavy maps, large groups, maps where clarity is strictly more important than atmosphere.

---

## Style M – Muted Soft-Contrast

**Aliases:** muted, soft, washed out, desaturated, low saturation, pastel, gentle, faded, accessible, fog, veiled, dreamlike

**Description:** Muted soft-contrast VTT battlemap, heavily desaturated palette, very low value range, near-zero harsh shadows, gentle tonal transitions, washed-out natural colors, subtle ambient-only lighting, fog-softened edges, extremely restrained highlights, minimal color temperature contrast, quiet and restful finish. Maximum visual comfort, absolute minimum fatigue.

**Best for:** Extended campaigns, players with visual sensitivity, dreamlike or memory-faded locations, ethereal spaces, haunted places, maps where accessibility and eye comfort are top priority.

**Note:** Slightly increase contrast near key entrances and landmarks so gameplay space remains readable.

---

## Style N – Noir / Monochrome

**Aliases:** noir, monochrome, black and white, grayscale, no color, hard shadow, film noir, detective, shadow play

**Description:** Monochrome VTT battlemap, black white and gray only, with hard directional shadows from a single dominant light source. High contrast, strong silhouettes, dramatic value structure. Walkable spaces clearly defined by light, obstacles and walls by deep shadow. Film noir aesthetic — urban, cinematic, unsettling. Optional: a single muted tone (sepia or slate blue) may be used sparingly as an accent, but no full color.

**Best for:** Urban mystery campaigns, thieves guild encounters, city streets, noir-toned investigations, any map benefiting from a stark and cinematic look.

---

## Style O – Watercolor

**Aliases:** watercolor, watercolour, wash, painted wash, soft painting, aquarelle, delicate, dreamy

**Description:** Soft watercolor VTT battlemap, loose wash painting over light pencil sketch, colors bleeding gently at terrain edges, translucent layered washes building depth, visible paper texture showing through lighter areas, organic imperfect edges on all shapes, delicate and dreamlike presentation. Colors are gentle and luminous rather than saturated. Terrain types distinguished by hue and wash pattern rather than hard borders.

**Palette:** Soft and luminous — pale greens, dusty blues, warm sand, muted earth tones. Colors feel naturally mixed and slightly unpredictable.

**Best for:** Nature encounters, sacred groves, fae locations, outdoor wilderness, maps benefiting from an artistic and gentle aesthetic.

---

## Style P – 3D Render / Game Asset

**Aliases:** 3d render, 3d, game tiles, game asset, dungeon alchemist, solasta, volumetric, rendered

**Description:** 3D-rendered VTT battlemap viewed top-down, as if assembled from high-quality 3D game assets. Photorealistic material textures with normal-map-quality surface detail. Volumetric lighting from point sources with accurate cast shadows on floor from all props. Walls have visible height and thickness through their cast shadows and top-surface rendering. Water looks wet and reflective. Stone looks heavy. Wood looks grained. Near-photoreal material fidelity within a strict top-down frame.

**Best for:** Players who prefer a modern video game look, high-fidelity campaigns, users familiar with tools like Dungeon Alchemist, Inkarnate 3D, or Solasta.

**Note:** Cast prop shadows provide 3D depth cues while maintaining top-down readability. Do not tilt camera to show wall height — only shadow and top-surface imply volume.

---

## Style Q – Realistic / High-Fidelity

**Aliases:** realistic, photo-real, hyper-realistic, high-fidelity, detailed textures, photographic

**Description:** High-fidelity realistic VTT battlemap, photorealistic material rendering, detailed stone and wood textures, believable surface variation, naturalistic lighting with accurate shadow behavior, near-photographic quality within a top-down orthographic frame. Materials look and feel like real surfaces.

**Best for:** Players who prefer a grounded, high-production look. Detailed dungeons, realistic wilderness, maps where material believability matters.

**Note:** Keep walkable spaces clearly distinguishable from walls and obstacles — realism must not reduce tactical readability.

---

## Style W – WoW-like

**Aliases:** wow, world of warcraft, blizzard style, mmo style, stylized game art, warcraft, game-art stylized

**Description:** World of Warcraft-inspired VTT battlemap. Clean stylized realism with slightly exaggerated, bold shapes. Higher saturation than naturalistic styles. Warm inviting colors as default palette, shifting dramatically per zone theme. Clean readable terrain borders and strong material separation. Props and features are slightly oversized and stylized for legibility. Professional high-polish game-art quality throughout. Excellent tactical readability as a natural consequence of the style.

**Palette:** Zone-dependent. Earthy greens and browns for wilds, grey-gold for dwarven stone, violet-blue for arcane, rich crimson for corrupted zones.

**Best for:** Heroic encounters, any environment that benefits from clear visual language and polished game-art aesthetic.
