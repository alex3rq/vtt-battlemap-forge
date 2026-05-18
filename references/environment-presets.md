---
name: environment-presets
description: Catalog of 11 environment presets defining biome, terrain materials, natural palette, and prop language for VTT battlemaps. Each preset is independent of aesthetic style — combine freely with any style. Called by SKILL.md EP to select environment dressing based on user request or map concept.
---

# Environment Presets

Environment presets define biome, terrain materials, natural palette, and prop language of the map. Independent of aesthetic style — combine with any Aesthetic Style.

**If no environment is specified, derive environment from map concept or use a neutral stone/earth setting.**

## Execution Procedure

```
select_environment(user_request, concept) → env_preset

match user_request against:
    environment number (1-11) → use exactly
    environment name or alias → match to correct preset
    no environment specified → derive from concept
    no concept available → generic stone/earth dungeon

return: terrain, palette, props, lighting default, any special notes
```

---

## Environment 1 – Ancient Ruins / Lost Civilization

**Aliases:** ruins, ancient, temple, lost civilization, forgotten sanctuary, old stone, crumbled, overgrown stonework, archaeological

**Terrain:** Weathered stonework, broken architecture, worn carvings without readable text, cracked marble floors, collapsed masonry, elegant ruined details.
**Palette:** Stone grays, mossy greens, earth tones, faded gold accents, aged ivory.
**Props:** Cracked columns, scattered carved stone fragments, broken statuary, vine-covered archways, dust-filled crevices, aged urns, fallen friezes, broken pedestals, pooled shadow in collapsed sections.

---

## Environment 2 – Natural Cave / Cavern

**Aliases:** cave, natural cave, cavern, underground, underground lair, mine, grotto, spelunking

**Terrain:** Natural rock formations, packed dirt and stone floors, cave silhouettes, organic irregular walls.
**Palette:** Cool grays, dark stone, damp earth browns, faint warm torch-light accents in inhabited areas.
**Props:** Stalactites and stalagmites (only where not blocking walkable space), cave pools, bioluminescent moss, mineral veins, loose gravel, drip marks, fungal growths.

---

## Environment 3 – Aquatic / Underwater / Flooded

**Aliases:** aquatic, underwater, flooded, submerged, ocean floor, tidal cave, sea cave, lagoon, drowned, waterlogged

**Terrain:** Underwater or flooded surfaces, visible water depth variation, soft caustic light patterns, sand or silt floor, submerged architecture if applicable.
**Palette:** Deep blue-greens, teal, aquamarine, sandy seafloor tones, muted coral accents, dark abyssal shadow in deep zones.
**Props:** Barnacle-encrusted stone, kelp clusters, coral formations, rusted chains and anchors, waterlogged wood, scattered shells, fish bones, silt-covered floors, submerged broken crates, water-softened edges on all objects.
**Lighting default:** Soft caustic light from above (shallow zones), cold bioluminescent accents (deep zones).

---

## Environment 4 – Urban / City / Sewer / Rooftop

**Aliases:** urban, city, street, alley, sewer, rooftop, tavern, market, town, district, cobblestone, undercity

**Sub-environments:**

*Street / Alley:* Worn cobblestones, puddles, refuse, broken crates, torch brackets, barrel clusters, worn wall plaster.

*Sewer / Undercity:* Slick stone channels, iron grates, corroded pipe stubs, stagnant pools, slime streaks, soot-blackened walls, rusted rungs.

*Rooftop:* Flat or angled tile roofs, chimney stacks, rope bridges, wooden platforms, broken crenellations, scattered debris.

*Tavern / Interior:* Worn plank floors, arranged or overturned furniture, fireplace remnants, scattered vessels, cloth curtains, barrels, shelves.

**Palette:** Stone grays, weathered brown wood, wet dark stone (sewers), warm amber interior light, cold blue-gray street ambient.

---

## Environment 5 – Arctic / Frozen / Ice

**Aliases:** arctic, frozen, ice, tundra, glacier, ice cave, blizzard ruins, frozen dungeon, permafrost, snow, winter

**Terrain:** Cracked glacial surfaces, snow-covered stone or earth, frost patterns, ice wall formations, frozen water features.
**Palette:** Cool blues, ice whites, pale grays, deep shadow blues, faint warm amber near fire or torch sources.
**Props:** Ice formations (spires, shelves), snow drifts, frost-covered debris, frozen bones or objects locked in ice, cracked permafrost, animal tracks in snow, fur scraps, ice-encrusted chains, frozen puddles with visible depth.
**Lighting default:** Cold diffuse overcast or blue-white ambient, faint warm accents near inhabited areas.

---

## Environment 6 – Jungle / Overgrown / Tropical

**Aliases:** jungle, tropical, overgrown, rainforest, lost temple, fae jungle, canopy, vine-covered, lush, verdant

**Terrain:** Dense vegetation, heavy root networks, moisture-drenched surfaces, dappled canopy light, overgrown ruins where applicable.
**Palette:** Deep greens, warm earthy browns, humid shadow, controlled flashes of vibrant flora, mossy stone grays, rich dark soil.
**Props:** Thick root systems crossing floors, hanging vines, broad tropical leaves, moss-blanketed stonework, muddy water pools, mushroom clusters, crushed undergrowth path marks, hollow logs, vine-wrapped masonry.
**Lighting default:** Dappled green-filtered canopy light (exterior), warm torch or magical glow (interior ruin), diffuse humidity haze.

---

## Environment 7 – Volcanic / Infernal

**Aliases:** volcanic, infernal, lava, fire, hellish, magma, sulfur, underworld, obsidian, brimstone, forge, demon forge

**Terrain:** Active or cooled lava channels (as terrain features), obsidian and basalt stone, heat-fractured surfaces, ash-coated ground.
**Palette:** Deep black and dark gray stone, glowing amber-orange lava, red shadow, heat-shimmer tonal shifts, cooled dark lava crust contrasting with active channels.
**Props:** Lava crack channels, cooled obsidian slag, scorch marks, ash deposits, sulfur-stained stone, heat-fractured rubble, crumbling pumice. For inhabited areas: iron chains, crude forge remnants, soot-covered tools.
**Lighting default:** Dramatic upward lava glow as ambient base, hot orange-red underlit shadows.
**Contrast note:** Slightly higher contrast than default is appropriate here due to natural lava-light dynamic.

---

## Environment 8 – Swamp / Bog / Marsh

**Aliases:** swamp, bog, marsh, bayou, wetland, fetid, mire, murky, fen, bayou, wetland

**Terrain:** Murky standing water, decaying vegetation, stagnant pools, gnarled roots, soft mud and silt.
**Palette:** Dark olive greens, murky brown water, rotting wood browns, sickly yellow-green highlights, deep shadow.
**Props:** Murky water patches with lily pads, rotting plank crossings, gnarled exposed roots, hanging grey moss, decaying logs, half-submerged debris, thick mud at water edges, fungal growths, dead reeds and cattails.
**Lighting default:** Dim overcast or filtered canopy light, cool green-gray ambient, faint bioluminescent accents from fungi or water surface.

---

## Environment 9 – Desert / Arid Badlands

**Aliases:** desert, arid, badlands, canyon, sandstone, dunes, dry ruins, mesa, wasteland, sun-baked, sand

**Terrain:** Heat-bleached stone, wind-shaped terrain, cracked dry earth, sparse vegetation, sand-filled recesses.
**Palette:** Warm sandstone tan, red-orange canyon stone, bleached cream and ivory, burnt sienna earth, cool shadow blue-gray in deep recesses, deep terracotta.
**Props:** Bleached bones, wind-sculpted stone formations, sand drift accumulations in corners and against walls, pottery shards, dried brush remnants, sun-faded cloth scraps, deeply worn carvings, cracked dry earth patterns.
**Lighting default:** Harsh direct overhead sunlight, strong directional shadows from ledges and walls, warm golden ambient. Interior ruins: dramatic shaft lighting through cracks, cool shadowed recesses.

---

## Environment 10 – Forest / Ancient Woodland

**Aliases:** forest, woodland, woods, grove, ancient grove, fae forest, enchanted forest, old growth, druid, sylvan, nature

**Terrain:** Dense root networks, fallen logs, leaf litter, dappled canopy light, streams and moss-covered stone, natural clearings.
**Palette:** Rich earth browns, deep forest greens, dappled gold-green light, grey moss, dark understory shadow, faint blue-violet for magical groves.
**Props:** Thick root networks crossing paths, mossy fallen logs, leaf litter patches, mushroom rings, lichen-covered stones, small stream channels, disturbed earth, hollow tree stumps, twisted branch barriers.
**Lighting default:** Dappled canopy filtering, soft green-tinted ambient fill, warm golden shafts where canopy breaks, cool shadowed undergrowth.

---

## Environment 11 – Arcane / Ethereal / Planar

**Aliases:** arcane, ethereal, planar, magical plane, void, astral, feywild, shadowfell, crystal, extraplanar, otherworldly, dreamscape, rift

**Terrain:** Magically altered or extraplanar space. Crystalline or geometric surfaces, arcane residue, implied spatial distortion at edges and seams.
**Palette:** Deep indigo and violet, prismatic shimmer accents, cool silver-white ambient, otherworldly teal or gold energy hues, near-black shadow.
**Props:** Crystalline formations, arcane residue stains, abstract geometric floor inlays (non-readable, purely decorative), energy-stained stone, prismatic surface reflections, spatial seam cracks, implied floating dust motes in texture.
**Lighting default:** Internal magical glow as primary ambient, prismatic refraction accents, no sun or fire source, cold and sourceless feel.
