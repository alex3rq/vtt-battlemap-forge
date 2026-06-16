---
name: environment-presets
description: Catalog of 11 environment presets defining biome, terrain materials, natural palette, and prop language for VTT battlemaps. Each preset is independent of aesthetic style — combine freely with any style. Called by SKILL.md EP to select environment dressing based on user request or map concept. High-Detail Textures section at the bottom is loaded conditionally — only when mode=generation and detail=high.
---

# Environment Presets

Environment presets define biome, terrain materials, natural palette, and prop language of the map. Independent of aesthetic style — combine with any Aesthetic Style.

**If no environment is specified, derive environment from map concept or use a neutral stone/earth setting.**

## Execution Procedure

```
select_environment(user_request) → env_preset

match user_request against:
    environment number (1-11) → use exactly
    environment name or alias → match to correct preset
    no environment specified → derive concept from user_request
    no concept derivable → generic stone/earth dungeon

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

---

## High-Detail Textures

**Load conditionally — only when mode=generation AND detail=high.**

These photogrammetry-quality texture passes provide maximum visual richness for Generation Mode with High detail intensity. They specify micro-detail, ambient occlusion, and material fidelity beyond standard environment dressing. Load from here when the conditions above are met; otherwise skip this section entirely.

### Env 1 – Ancient Ruins / Lost Civilization (High Detail)

Photogrammetry stone surfaces with visible mineral grain and age staining. Micro-shadows under every stone fragment, carved edge, and rubble cluster. Moss growing into individual crevice seams. Dust motes in shafted light through collapsed ceilings. Worn floor stone showing erosion channels and root-lifted slabs. Vine root systems with individual tendril shadows.

### Env 2 – Natural Cave / Cavern (High Detail)

Procedural wet stone with visible mineral deposits, crystal inclusions, and water seep staining. Micro-shadows under every loose pebble and gravel cluster. Individual stalactite and stalagmite tips with condensation drip marks. Bioluminescent moss with soft self-illumination halos. Packed dirt floor with boot-print compression marks and embedded small stones.

### Env 3 – Aquatic / Flooded (High Detail)

Procedural caustic light patterns with real-time ripple simulation across the floor. Micro-shadows under every shell, pebble, and coral branch. Individual barnacle clusters with visible texture relief. Kelp fronds with translucent edge lighting. Silt layers with visible settlement gradients and disturbance trails. Waterlogged wood showing grain swelling and color saturation.

### Env 4 – Urban / Sewer (High Detail)

Street/Alley — individual cobblestone with visible mortar joints, wet-surface reflections, puddle depth with debris floating at edges. Sewer — slick biofilm coating on stone, corroded metal surfaces with rust bloom, stagnant water surface tension. Rooftop — individual roof tile overlap shadows, chimney mortar texture, rope fiber detail. Interior — worn plank floor boards with grain and knot detail, fabric texture on curtains, ceramic surface on vessels.

### Env 5 – Arctic / Frozen (High Detail)

Glacial ice with internal bubble inclusions and refraction depth. Micro-shadows in every boot track and animal print in compacted snow. Snow drift surface with wind-sculpted micro-ridges and blue-shadow hollows. Frost crystal formations on individual stone edges. Frozen puddle surfaces with air pocket shadows beneath the ice layer. Permafrost crack networks with shadow depth.

### Env 6 – Jungle / Overgrown (High Detail)

Procedural mud with compression ruts, footprint depressions, and puddle edges showing silt gradients. Individual root networks with micro-shadows beneath each root cable. Leaf litter layers with visible overlap, vein detail, and partial decomposition. Moss surface with individual stalk density variation. Volumetric humidity haze in shafted canopy light. Tropical leaf surfaces with waxy sheen and water bead micro-highlights.

### Env 7 – Volcanic / Infernal (High Detail)

Obsidian surfaces with high-gloss reflection and internal bubble voids. Active lava channels with viscous surface crust cracking to reveal orange-white core. Ash deposits layered in sheltered recesses with disturbed-trail marks. Basalt stone with columnar joint patterns and heat-spall fractures. Micro-shadows under every pumice fragment and heat-fractured rubble piece. Sulfur staining with color gradient from yellow at vents to white at edges.

### Env 8 – Swamp / Bog (High Detail)

Murky water surface with organic debris floating at tension boundary and depth-gradient opacity. Mud at water edges with viscous surface sheen and embedded organic material. Individual rot patterns on decaying wood — grain separation, fungal bloom, color gradient from healthy to decayed. Reed and cattail stems with node detail and micro-shadows. Gnarled root surfaces with bark texture and embedded mud staining. Bioluminescent fungi with soft self-glow halos on surrounding surfaces.

### Env 9 – Desert / Arid (High Detail)

Photogrammetry sandstone with visible sediment layer banding and wind-erosion channeling. Sand drift surfaces with micro-ripple wind patterns and shadow depth in each ripple trough. Cracked dry earth with individual polygon separation, curled edge lifting, and shadow depth in cracks. Bleached bone surfaces with sun-faded calcium texture and hairline fracture networks. Pottery shard edges with clay layer cross-section visible. Dried brush with individual twig shadow casting. Sun-directional shadows with hard edges from all raised geometry.

### Env 10 – Forest / Woodland (High Detail)

Heavily traveled dirt paths with procedural wagon ruts, organic footprints, individual scattered pebbles, and exposed root networks that ignore any stylized drawn lines. Multi-toned dense groundcover — grass variation, realistic leaf litter with individual leaf shape and shadow, fallen twigs, patches of moss, ferns, and scattered wildflowers blending naturally into path edges. Rock formations as weathered multi-layered geological outcrops with organic cracks, heavy moss growth, and lichen textures — not icon boulders. Dappled sunlight with volumetric shafts cutting across the map, casting long realistic shadows from tree canopies and stone ridges to define elevation naturally. Micro-shadows under every pebble, root cable, and debris fragment via ambient occlusion.

### Env 11 – Arcane / Ethereal / Planar (High Detail)

Crystal surfaces with internal light refraction, subsurface scattering, and spectral caustic projections on surrounding floors. Arcane residue with luminescent edge bloom and crystallized deposit texture. Floor inlay geometry with beveled edges and micro-shadow depth. Energy-stained stone with color gradient falloff from the stain origin point. Spatial seam cracks with inner glow and depth suggesting infinite void. Floating dust mote fields with soft self-illumination in the ambient magical light.
