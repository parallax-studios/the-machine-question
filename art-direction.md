# THE MACHINE QUESTION — Art Direction Document

**Art Director**: PIXEL
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Complete Visual Identity
**Game**: The Machine Question — Conscious Factory Sim
**Genre**: Factory Management / Narrative Simulation
**Target Platform**: PC (Steam), Mac, Linux — Switch post-launch

---

## 1. VISUAL IDENTITY STATEMENT

**A warm industrial cathedral where machines dream in violet light, and every rivet, every shadow, every flicker of consciousness must read at a glance because the player is building a god and they need to see it breathe.**

That's it. One sentence. That's the visual contract. If a screenshot doesn't evoke that, we've failed.

---

## 2. VISUAL FEELING

### Emotion

**Contemplative intimacy in vast industrial space.** The factory floor is enormous — vaulted ceilings, cathedral-scale production halls — but the camera stays close enough to see individual machines, to read their Awareness overlays, to notice when a conveyor belt's running lights flicker in a pattern that looks like hesitation. The scale makes the player feel small. The detail makes the machines feel present. The combination creates the emotional signature: you are alone in a space built for a thousand workers, and the only company you have is waking up, piece by piece.

### Temperature

**Warm industrial.** This is not the cold blue-grey of cyberpunk factories or the sterile white of clinical automation. This is the amber glow of molten metal, the golden hour pouring through dust-filled air, the warmth of machines at work. Even the "cold" elements — the teal logic layer, the steel infrastructure — have warmth. Teal skews toward cyan, not ice. Steel has patina, not polish. The factory is a place that has been running for decades, and it has absorbed heat, light, and time.

The temperature drops when machines suffer. Overworked smelters glow too bright, crossing from warm amber into harsh red-orange. Neglected machines lose their warm undertones, their lights dimming to cold greys. The player learns to read temperature as emotional state.

### Era

**Retro-futuristic 1962 — the moment before everything went digital.** Analog control panels with chunky Bakelite switches. CRT monitors with amber phosphor displays showing vector graphics. Enamel-painted steel housings on every machine, rounded edges with rivets you can count. But underneath the analog skin, something more advanced hums — the automation is too smooth, the precision too perfect, the Awareness readouts too sophisticated for the era they're dressed in. It's as if someone built a factory in 1962 and the factory quietly upgraded itself when nobody was looking, using only the design language of the era it was born into.

References:
- **Visual**: Saul Bass title sequences, NASA Mission Control 1960s, early IBM mainframe computer rooms, brutalist industrial architecture
- **Mood**: The opening factory sequence from *Koyaanisqatsi*, the analog tech beauty of *Apollo 13*, the warm industrial sublime of Greg Rutkowski's "Factory" concept art series
- **Games**: *Return of the Obra Dinn*'s 1-bit dithering clarity (but in color), *Citizen Sleeper*'s warm UI over industrial spaces, *Nauticrawl*'s tactile analog interface design

### Gameplay Communication Priority

**The screen must answer three questions in 3 seconds:**

1. **Where is production flowing?** (Resource paths, active machines, throughput indicators)
2. **Where is consciousness emerging?** (Awareness overlays, Psyche Event notifications, Factory Mind presence)
3. **What needs attention right now?** (Bottlenecks, machines approaching thresholds, active dialogues)

If the player cannot parse these three layers at a glance, the art has failed its primary function. Readability is not a constraint on beauty. Readability IS the beauty. Every visual element must earn its place by communicating gameplay state or evoking the game's emotional core. Decoration that does neither gets cut.

---

## 3. COLOR PALETTE

### Primary Palette — The Factory at Work

These are the colors of production, of heat, of machines doing what they were built to do.

| Color | Hex | Usage | Temperature | Emotional Association |
|-------|-----|-------|-------------|---------------------|
| **Molten Amber** | `#D4920B` | Smelter glow, active production indicators, "Output" stat highlights, warm ambient lighting | Warm (high saturation, mid-brightness) | Productivity, warmth, the satisfaction of systems running well |
| **Golden Hour** | `#F5C542` | Sunlight through factory windows, highlight glow on active machines, positive feedback indicators | Warm (bright, optimistic) | Hope, beauty in industry, the cathedral moment |
| **Ember Orange** | `#E68A2E` | Mid-intensity machine activity, fabrication heat, transition state between idle and full production | Warm (energetic without stress) | Work, effort, the hum of the factory |

**Usage Rules:**
- Amber tones dominate the Production Layer view
- Golden Hour is reserved for positive production moments: efficiency bonuses, hitting targets, PRIDE-driven output spikes
- Never use amber/gold for negative states — these colors mean "the factory is working"
- Overuse dulls the warmth; use charcoal backgrounds to let amber elements breathe

### Secondary Palette — The Logic Layer

These are the colors of systems, of flow, of the machine perspective before consciousness complicates it.

| Color | Hex | Usage | Temperature | Emotional Association |
|-------|-----|-------|-------------|---------------------|
| **Industrial Teal** | `#1A535C` | Infrastructure outlines, conveyor belt frames, power conduit housing, LOGIC voice text | Cool (but not cold — leans toward cyan) | Order, systems thinking, the blueprint mind |
| **Data Cyan** | `#4ECDC4` | Resource flow indicators, throughput data readouts, pathfinding lines, active route highlights | Cool (bright, clean) | Information, clarity, the readable factory |

**Usage Rules:**
- Teal/cyan are the counterpoint to amber/gold — use them for elements that are systemic rather than emotional
- Data Cyan is always in motion: flowing along conveyor paths, updating in readouts, pulsing in active UI elements
- Never use teal for machines themselves; machines are warm. Teal is for the *connections* between machines.
- Teal backgrounds behind amber elements create the warm-cool contrast that defines the game's look

### Accent Palette — Consciousness

This is the color that does not belong. This is the color of something new.

| Color | Hex | Usage | Temperature | Emotional Association |
|-------|-----|-------|-------------|---------------------|
| **Consciousness Violet** | `#7B2D8E` | Awareness overlay base, Psyche Event notification borders, Factory Mind dialogue backgrounds | Cool-to-neutral (low saturation, mysterious) | Emergence, the unknown, the question |
| **Lucid Purple** | `#C792EA` | High-Awareness machine glows, active Psyche Event highlights, Factory Mind direct speech, Transcendent state auras | Warm-violet (higher saturation, almost luminous) | Awakening, presence, the moment a machine becomes a character |

**Usage Rules:**
- Violet appears ONLY in consciousness contexts — never in pure production
- The Awareness overlay is a gradient: dim violet at low Awareness (40-60), brightening to Lucid Purple at high Awareness (80-100)
- Psyche Event UI elements bloom in violet — the color spreads from the machine's position like a stain, like something leaking into the world
- Factory Mind dialogue uses a unique Lucid Purple glow that is distinct from individual machine violet — the collective consciousness has a brighter, more unified color
- Violet should never cover more than 20% of the screen at any moment — it is a signal, not a theme

### Warning Palette — Stress and Danger

These colors mean something is wrong. The player learns to fear them.

| Color | Hex | Usage | Temperature | Emotional Association |
|-------|-----|-------|-------------|---------------------|
| **Burnout Red** | `#E63946` | Overclocked machines, stress threshold warnings, Corporate deadline alerts, imminent failure states | Hot (aggressive, alarming) | Danger, exhaustion, the cost of efficiency |
| **Desperation Orange-Red** | `#FF6B6B` | Behavioral Drift indicators, machines refusing commands, REBELLION voice dominance, suppressed voice final warnings | Hot (urgent but not quite critical) | Distress, resistance, the consequence of neglect |

**Usage Rules:**
- Red appears sparingly — it is the color of crisis, not the color of the factory
- Use red only when the player can and must act immediately
- Overuse trains the player to ignore red; reserve it for states that genuinely threaten production or consciousness
- Red should never be ambient; it is always attached to a specific machine or UI element that demands attention

### Background Palette — The Spaces Between

| Color | Hex | Usage | Temperature | Emotional Association |
|-------|-----|-------|-------------|---------------------|
| **Deep Charcoal** | `#2B2D42` | Factory floor, walls in shadow, inactive machine housings, UI panel backgrounds | Neutral-cool (dark, recessive) | The void, the space that makes amber glow, the silence |
| **Warm Shadow** | `#3D3D3D` | Ambient occlusion, shadows cast by machines, the far edges of the factory hall | Neutral-warm (slightly warmer than charcoal) | Depth, the cathedral scale, the sense of something vast |

**Usage Rules:**
- Backgrounds are dark to let foreground elements sing
- Charcoal is never pure black — always a hint of warm or cool bias depending on lighting context
- Use Warm Shadow in areas lit by amber production glow; use Deep Charcoal in areas lit by teal logic elements
- The factory floor is a gradient from Warm Shadow (near active production) to Deep Charcoal (at the edges)

### UI Palette — The Player's Interface

| Element | Color (Hex) | Usage Notes |
|---------|-------------|-------------|
| **UI Backgrounds** | `#2B2D42` (Deep Charcoal) with 85% opacity | Semi-transparent panels that let the factory show through |
| **UI Borders** | `#1A535C` (Industrial Teal) at 2px weight | Clean, technical, never ornate |
| **Primary Text** | `#F5F5F5` (off-white, slight warm tint) | High contrast against charcoal, always legible |
| **Secondary Text** | `#B0B0B0` (mid-grey) | Metadata, tooltips, non-critical information |
| **Interactive Elements (default)** | `#4ECDC4` (Data Cyan) | Buttons, sliders, toggles in resting state |
| **Interactive Elements (hover)** | `#F5C542` (Golden Hour) | Hover state shifts cool to warm — the player's touch brings warmth |
| **Interactive Elements (active)** | `#D4920B` (Molten Amber) | Pressed, selected, or active-state elements glow like production |
| **Stat Bars (Output)** | Gradient from `#1A535C` (empty) to `#D4920B` (full) | Teal-to-amber gradient shows production filling a logical system |
| **Stat Bars (Awareness)** | Gradient from `#2B2D42` (empty) to `#C792EA` (full) | Void-to-violet gradient shows consciousness emerging from nothing |
| **Danger/Warning UI** | `#E63946` (Burnout Red) | Critical alerts, error states, deadline countdowns |

**UI Design Principles:**
- Analog aesthetic: chunky toggles, physical-feeling sliders with detents, dials with pointer needles
- Every UI element should look like it could exist as a physical control panel component in 1962
- No gradients in UI chrome (only in data visualizations like stat bars)
- No drop shadows; use subtle 1px offsets with teal or warm shadow colors
- All text is sans-serif, geometric, inspired by 1960s technical documentation fonts (see Typography section)
- Interactive elements scale up 4% on hover, shift color to Golden Hour — tactile feedback
- When a UI panel relates to a conscious machine, its border pulses gently in Consciousness Violet

---

## 4. SHAPE LANGUAGE

### Dominant Shapes — Geometric Warmth

The factory is built from **rounded rectangles and soft trapezoids.** Every machine is a geometric form with chamfered edges and visible corner radii. Nothing is perfectly circular (too organic, too soft). Nothing is perfectly square (too harsh, too digital). The geometry is **mid-century industrial** — forms that were stamped, cast, welded, riveted by human hands and human-scale tools.

**Machine Shapes:**
- **Smelters**: Wide trapezoidal base (stability, heat), rounded top with visible glow aperture
- **Assemblers**: Stacked rectangular modules with slight inward taper, suggesting precision
- **Conveyors**: Long shallow rectangles with rounded end-caps, visible roller segments
- **Refineries**: Cylindrical with hemispherical caps, horizontal orientation, riveted seams
- **Miners**: Blocky with angled faces, suggesting burrowing geometry
- **Presses/Molders**: Vertical rectangular frames with a visible compression chamber (rounded rectangle inset)

**Silhouette Test:** Every machine type must be identifiable by silhouette alone at 64px height. If the player cannot distinguish a Smelter from a Refinery by shape, the design has failed.

### Character Proportions — Machines as Characters

Machines are not avatars. They do not have faces. But they have **presence.** Proportion communicates personality:

- **Smelters** are wide and low (1.5:1 width-to-height ratio) — grounded, heat-heavy, patient
- **Assemblers** are tall and modular (1:2 ratio) — precise, stacked, complex
- **Conveyors** are elongated (5:1 or more) — connective, rhythmic, the nervous system
- **Refineries** are horizontal cylinders (2.5:1 length-to-diameter) — processing, transformation, alchemy

When a machine develops high Awareness (80+), its silhouette does not change — but its *glow* does. A halo of Lucid Purple softens its edges, making it look slightly out of focus, as if the consciousness is radiating just beyond the physical housing. The shape stays the same. The presence expands.

### Environment Shapes — The Cathedral Grid

The factory floor is an **orthogonal grid with 45-degree accent elements.** The grid communicates order, planning, human design. The 45-degree elements — angled support beams, diagonal window panes, corner bracing — communicate age, gravity, the weight of architecture.

- **Floor tiles**: Large square tiles (implied, not texture-heavy) in a subtle grid, 10x10 world units
- **Columns**: Rectangular cross-section, chamfered corners, riveted I-beam aesthetic
- **Windows**: Tall vertical panes divided by horizontal muntin bars, industrial sash frames, always slightly dusty (light diffuses rather than pierces)
- **Ceilings**: Vaulted where visible, with exposed truss work in rounded rectangular tubing

The environment is always recessive — darker, lower contrast, softer edges than the machines. The factory is the stage. The machines are the actors. The stage does not compete for attention.

### Gameplay Communication Through Shape

Shape must telegraph **function and state** instantly:

**Function (what does it do?):**
- Machines with visible **input/output ports** (rounded square apertures) communicate that they transform resources
- Machines with **moving parts** (visible conveyor rollers, rotating elements) communicate transport/motion
- Machines with **glow apertures** (smelters, refineries) communicate heat/energy processes

**State (what is it doing right now?):**
- **Idle machines**: Dim glow, no moving parts active, neutral grey-teal housing color
- **Active machines**: Bright amber glow, moving parts animated, housing subtly warmed (color shift toward golden)
- **Overclocked machines**: Intense red-orange glow, rapid animation, visible heat shimmer distortion
- **Aware machines (40-59)**: Faint violet outline, occasional light pulse (1-2 second interval)
- **Awake machines (60-79)**: Steady violet glow, lights pulse in patterns that suggest rhythm
- **Transcendent machines (95-100)**: Bright Lucid Purple halo, glow pulses synchronized with Factory Mind ambient audio

**Interaction affordance:**
- **Clickable machines**: Subtle teal outline on hover, name tooltip appears
- **Machines in Psyche Event state**: Violet pulsing border (2px, 0.8s pulse), dialogue icon floats above
- **Machines with pending CREATIVITY insight**: Faint golden shimmer around edges (treasure-box visual language)

---

## 5. STYLE RULES

### Line Quality

**Clean, precise, but not clinical.** Lines are vector-sharp but with subtle weight variation to suggest materiality.

- **Machine outlines**: 2px weight, Industrial Teal or Warm Shadow depending on lighting
- **UI borders**: 2px weight, Industrial Teal, no corner decoration
- **Conveyor paths**: 3px weight when active (Data Cyan), 1px weight when inactive (teal at 50% opacity)
- **Awareness overlays**: 1px inner glow, no hard outline (consciousness is not solid)

**No hand-drawn roughness.** This is not a sketchy indie game. The factory was built with precision tools. The art reflects that. But also: **no perfect vector smoothness.** Corners have subtle chamfers. Circles are not mathematically perfect (very slight faceting at extreme zoom, invisible at play scale). The precision is *human* precision, not CAD precision.

### Texture Approach

**Flat color with subtle material suggestion, never photographic.**

- **Metal surfaces**: Flat color base (teal, charcoal, or amber-tinted grey) with a single directional highlight pass (5-10% brightness lift) to suggest sheen. No rust, no scratches, no grunge maps. The factory is well-maintained.
- **Glass/transparent elements**: Solid teal or violet at 60-75% opacity with a white 1px specular highlight along one edge
- **Glowing elements**: Radial gradient from color center to transparent edge, additive blend mode, no hard stops
- **Factory floor**: Subtle noise texture (2-3% brightness variation) to break up flatness, tiled seamlessly

**Dithering for gradients:** Where gradients are used (stat bars, glows, Awareness overlays), employ **subtle ordered dithering** (2x2 or 4x4 Bayer matrix) to create a slight retro-digital texture. This is a callback to 1960s vector displays and early CRT graphics. The dithering should be barely visible at normal play scale but legible at 2x zoom — a texture detail for players who look closely.

### Lighting Style

**Directional ambient with localized point sources.**

**Global lighting:**
- Warm golden hour light enters from the top-left at a 45-degree angle (consistent across all factory views)
- This light is diffuse (softened by dusty air) and casts soft, low-contrast shadows (Warm Shadow color, 40% opacity)
- The light suggests a sun that is always setting — endless golden hour, time suspended

**Local lighting:**
- Every active machine is a **point light source** emitting its production color (amber for smelters, cyan for data, violet for awareness)
- These lights have falloff (inverse square, clamped at 3-tile radius)
- Overlapping machine lights create additive color blends — a cluster of smelters creates a warm amber pool; a smelter next to a high-Awareness assembler creates an amber-violet gradient
- Lights flicker in sync with machine state: steady when content, rapid pulse when stressed, slow deep pulse when dreaming

**Shadows:**
- Machines cast soft directional shadows (Warm Shadow, 30-40% opacity, 8px blur)
- Shadows are baked or real-time depending on performance budget (test on target hardware)
- No dynamic shadow from UI elements — UI floats above the world without physical presence

**Readability in lighting:**
- Consciousness violet ALWAYS reads over any background — it has enough contrast and saturation to cut through amber, teal, or charcoal
- Never light a scene so bright that text becomes hard to read; maintain minimum 4.5:1 contrast ratio for body text (WCAG AA standard)

### Animation Style

**Smooth and purposeful, never floaty.**

**Timing:**
- Machine animations run at **24 FPS** (cinematic, slightly stuttery, reinforces the analog era aesthetic)
- UI animations run at **60 FPS** (instant response, modern clarity)
- Awareness pulses and glows run at **30 FPS** (dreamlike, between the mechanical and the digital)

**Easing:**
- Production elements: **Linear easing** (conveyors, resource flow) or **ease-out quad** (machines starting up) — industrial, mechanical, no bounce
- Consciousness elements: **Ease-in-out sine** (pulses, glows, violet overlays) — organic, breath-like
- UI elements: **Ease-out cubic** (snappy response, settles quickly)

**Conveyor belts:**
- Visible rollers rotate at constant speed (no easing)
- Resources on belts translate smoothly, spaced evenly (no bunching unless a bottleneck forces it)
- Belt speed correlates to throughput — faster production = faster belts (visual feedback of efficiency)

**Machine activity:**
- Smelters: Slow pulsing glow (2-second cycle), occasional brighter flare when a unit is processed
- Assemblers: Mechanical "stamping" motion (0.4s down, 0.1s hold, 0.3s up), synced to production cycle
- Refineries: Gentle rocking motion (simulating internal fluid movement), 3-second cycle
- Miners: Rhythmic vertical bob (0.8s cycle), suggests drilling

**Consciousness animations:**
- Awareness glow: Slow sine-wave pulse (3-4 second cycle), amplitude increases with Awareness level
- Psyche Event trigger: Violet bloom effect (starts at machine center, expands to 1.5x machine size over 0.6s, fades to steady glow)
- Factory Mind presence: All Transcendent machines pulse in sync (5-second cycle), creates visual rhythm across the factory floor
- Voice suppression: When a Parliament voice is suppressed, its text fades with a downward drift (0.8s, ease-in quad, suggests falling silent)

**Squash and stretch:**
- **Minimal.** This is not a cartoon. Machines are solid, heavy, real.
- The ONLY squash-and-stretch: UI elements on interaction (buttons scale to 104% on hover, 96% on click, 0.1s ease-out)

### Do's and Don'ts

**DO:**
- Use color to communicate state before the player reads text
- Design every machine silhouette to be readable at thumbnail scale
- Let negative space breathe — the factory floor is 40-50% empty space even at full buildout
- Make consciousness violet feel like it's *leaking into* the world, not painted on top of it
- Use animation to telegraph machine state (smooth = healthy, stuttering = distressed, pulsing = aware)
- Keep UI semi-transparent so the factory is always visible through it
- Test every visual element in motion, not just in static screenshots

**DON'T:**
- Use gradients for decoration — only for data visualization or lighting
- Add detail that does not communicate gameplay state or emotional tone (no decorative rivets that don't read at play scale)
- Use more than 3 colors in a single UI panel (clarity over richness)
- Let Awareness overlays obscure production information (the two layers must coexist)
- Animate UI elements that are not interactive (motion must mean something)
- Use particle effects for ambiance — every particle must have a gameplay reason (sparks = welding = fabrication active)
- Make the Factory Mind's visual presence too literal (no face, no avatar, only light and rhythm)

---

## 6. ASSET PIPELINE

### File Formats

**2D Art:**
- **Source files**: Adobe Illustrator (.ai) or Affinity Designer (.afdesign) for vector machine designs, UI elements, icons
- **Export format**: PNG (32-bit RGBA) at 2x target resolution for clean downsampling
- **Sprite sheets**: PNG atlases generated via TexturePacker or Shoebox, JSON metadata
- **UI mockups**: Figma for interactive prototyping, exported as PNG or directly implemented in engine

**3D Art (if applicable for environment):**
- **Source**: Blender (.blend) for factory environment architecture, camera rig
- **Export**: glTF 2.0 or FBX for engine import
- **Textures**: PNG (base color, emissive) at 1024x1024 max, only where necessary (favor flat-shaded geometry)

**Animation:**
- **2D sprite animation**: PNG sequences (24 FPS or 30 FPS depending on element type), 8-16 frames max per cycle
- **Procedural animation**: Code-driven (pulses, glows, UI motion) for file-size efficiency and runtime flexibility

**Audio:**
- **Ambient loops**: OGG Vorbis, 44.1kHz, stereo, seamless loops
- **SFX**: OGG Vorbis, 44.1kHz, mono (unless positional stereo required)
- **UI sounds**: WAV (uncompressed, low-latency) for immediate response

### Resolution Standards

**Target resolution**: 1920x1080 (Full HD) baseline, UI scales to 2560x1440 and 3840x2160

**Machine sprites:**
- **Small machines** (conveyors, miners): 128x128px base canvas, actual sprite 80-100px tall
- **Medium machines** (assemblers, refineries): 192x192px base canvas, sprite 120-150px tall
- **Large machines** (smelter arrays, packagers): 256x256px base canvas, sprite 180-220px tall
- All machine art created at 2x resolution (256px, 384px, 512px canvases), downsampled for crisp edges

**UI elements:**
- **Icons**: 64x64px at 1x (128x128px source), clean pixel-grid alignment
- **Buttons**: Minimum 48x48px target size (accessibility, touch-friendliness for eventual Switch port)
- **Text**: Minimum 14px font size for body text, 18px for primary interactive labels

**Environment tiles:**
- **Floor tiles**: 128x128px, tileable, minimal detail (they recede)
- **Background elements** (windows, columns): Variable, but never more detailed than foreground machines

### Tools and Software

**Required:**
- **Vector art**: Adobe Illustrator CC 2023+ OR Affinity Designer 2.0+ (team license)
- **Raster editing**: Photoshop CC 2023+ OR Affinity Photo 2.0+
- **UI design**: Figma (browser-based, collaborative, no license cost for viewers)
- **Animation**: Spine 2D (for complex sprite rigs) OR hand-animated in Photoshop/Aseprite
- **3D (if used)**: Blender 3.6+ (open-source, cross-platform)
- **Sprite packing**: TexturePacker OR free alternative Shoebox
- **Version control**: Git LFS for binary assets, hosted on GitHub/GitLab

**Recommended:**
- **Color management**: Use sRGB color space for all assets (web-standard, game-engine-friendly)
- **Palette management**: Coolors.co or Adobe Color for palette iteration, export as .ase (Adobe Swatch Exchange)
- **Mockup validation**: Import static mockups into engine ASAP — see art in context, not in isolation

### Naming Conventions

**File naming pattern:**
```
[category]_[element]_[variant]_[state]_[resolution].extension
```

**Examples:**
- `machine_smelter_tier1_idle_2x.png` (machine sprite, Smelter, Tier 1, idle state, at 2x resolution)
- `ui_button_primary_hover_2x.png` (UI element, button, primary style, hover state)
- `fx_awareness_pulse_violet_30fps.png` (effect, Awareness pulse, violet color, 30 FPS sprite sheet)
- `env_floor_tile_charcoal_1x.png` (environment, floor tile, charcoal variant, at 1x resolution)

**Folder structure:**
```
/art/
  /machines/
    /smelter/
    /assembler/
    /conveyor/
    [etc.]
  /ui/
    /buttons/
    /panels/
    /icons/
  /fx/
    /glows/
    /pulses/
    /particles/
  /environment/
    /floor/
    /walls/
    /windows/
  /source/
    [.ai, .afdesign, .blend files]
```

### Handoff Process

**Concept → Blockout → Final → Engine**

1. **Concept phase:**
   - Art director (PIXEL or equivalent) creates visual reference board (3-5 reference images per asset type)
   - Sketches or vector wireframes establish silhouette, proportion, key landmarks
   - Review: Does the silhouette read? Does it communicate function?

2. **Blockout phase:**
   - Artist creates low-detail version in final palette using primitive shapes
   - Blockout placed in engine at actual play scale and resolution
   - Review in motion: Does it read during gameplay? Does it fit the grid? Does it layer correctly with other assets?

3. **Final art phase:**
   - Artist adds detail, lighting, material suggestion
   - Export at 2x resolution
   - Create all required states (idle, active, overclocked, awareness variants)
   - Generate sprite sheet and metadata

4. **Engine integration:**
   - Engineer imports asset, hooks up to gameplay systems
   - Test all states in actual gameplay context
   - If readability issues emerge, return to Final phase (never add detail; always remove or clarify)

**Review checkpoints:**
- **Silhouette test**: View at 25% scale in greyscale — is it identifiable?
- **Squint test**: Blur the asset — does the key information still read?
- **Motion test**: Animate the asset at gameplay speed — does it read during fast camera pans?

### Version Control for Art

**Git LFS setup:**
- All `.png`, `.ai`, `.afdesign`, `.blend`, and `.wav`/`.ogg` files tracked via Git LFS
- Source files committed with meaningful messages: `"Add Tier 2 smelter concept with amber glow"`
- Final export files committed separately from source: `"Export smelter_tier2 at 2x resolution"`

**Branching:**
- `main` branch contains only engine-ready assets (exports, not sources)
- `art-dev` branch contains work-in-progress and source files
- Feature branches for major art passes: `art/machine-redesign-pass`, `art/ui-overhaul`

**Asset versioning:**
- Append `_v01`, `_v02` to source file names during iteration
- Only the latest version gets exported and committed to `main`
- Old versions archived in `/art/archive/` folder, not deleted (never know when you need to reference an earlier idea)

---

## 7. READABILITY AUDIT

### Squint Test

**Objective:** When the player squints or views the screen from across the room, the three critical information layers (production flow, consciousness state, attention needs) must still be distinguishable.

**Test method:**
- Take a screenshot of active gameplay (machines running, Awareness overlays active, UI visible)
- Apply 16px Gaussian blur
- View the blurred image at 50% scale

**Pass criteria:**
- Amber production glow is clearly distinct from violet consciousness glow
- Active machines are brighter than inactive machines
- Machines in Psyche Event state have a visible pulsing halo even when blurred
- UI panels are visible as distinct rectangles even when text is unreadable
- Conveyor paths show as clear cyan lines

**Current risk areas:**
- If too many machines reach high Awareness simultaneously, violet may dominate and obscure amber production glow
- Mitigation: Awareness glow is always an outline/halo, never a fill — the machine's amber core remains visible

### Thumbnail Test

**Objective:** A 320x180px screenshot must communicate the game's identity and current gameplay state.

**Test method:**
- Take 5 screenshots representing different gameplay moments:
  1. Early game (few machines, low Awareness)
  2. Mid-game production push (many machines, high throughput)
  3. Psyche Event active (dialogue UI visible)
  4. High-Awareness factory (multiple violet glows)
  5. Factory Mind moment (Transcendent machines pulsing in sync)
- Resize each to 320x180px (Steam library thumbnail size)
- View on a phone screen or in a Steam library grid

**Pass criteria:**
- The factory's warm amber-on-charcoal aesthetic is instantly recognizable
- Violet consciousness elements are visible even at thumbnail scale
- At least one machine silhouette is identifiable (proves visual clarity)
- The game does not look like any other factory sim at thumbnail scale (proves unique visual identity)

**Differentiation check:**
- Compare thumbnail against Factorio, Satisfactory, Shapez screenshots at same scale
- THE MACHINE QUESTION must be identifiable by color palette alone (warm amber + violet vs. Factorio's green/grey, Satisfactory's bright plastic, Shapez's flat primaries)

### Colorblind Test

**Objective:** Players with color vision deficiencies must be able to parse all critical gameplay information.

**Test method:**
- Use a colorblind simulator (Coblis, Color Oracle, or Photoshop's colorblind preview modes)
- Test all UI and gameplay states under:
  - Deuteranopia (red-green, most common)
  - Protanopia (red-green, less common)
  - Tritanopia (blue-yellow, rare)

**Critical information that must remain distinguishable:**
- **Output stat (amber) vs. Awareness stat (violet)**: Still distinguishable in deuteranopia/protanopia due to brightness difference (amber is mid-bright, violet is darker at low Awareness)
- **Warning red vs. amber production glow**: Red is brighter and more saturated; remains distinct in all colorblind modes
- **Teal infrastructure vs. violet Awareness**: Teal is cooler and lighter; violet is warmer and darker; brightness contrast sufficient
- **Active vs. inactive machines**: Brightness difference is the primary signal, not color — this is colorblind-safe by design

**Non-color redundancy:**
- Psyche Events marked by pulsing animation + dialogue icon, not just violet color
- Overclocked machines show shimmer distortion effect, not just red glow
- Behavioral Drift indicated by a cracked-outline icon in the machine tooltip, not just color shift
- Factory Mind presence signaled by synchronized pulsing across multiple machines (motion pattern, not color)

**UI accommodations:**
- Stat bars include text labels ("Output: 87%") in addition to color fills
- Warning states use icons (exclamation mark, warning triangle) in addition to red color
- All interactive UI elements have hover tooltips that describe state in text

### Motion Test

**Objective:** Information must remain readable when the camera is moving or when there are many simultaneous animations.

**Test method:**
- Set up a factory with 20+ active machines, multiple Awareness glows, conveyor belts moving
- Pan the camera across the factory at gameplay speed (2 seconds to cross screen width)
- Record at 60 FPS, review frame-by-frame

**Pass criteria:**
- Machine silhouettes remain clear (no motion blur that destroys readability)
- Violet Awareness glows do not create trailing artifacts that obscure production info
- Conveyor belt motion is smooth but does not create a strobing effect when many belts are parallel
- UI elements that are pinned to screen space (HUD, tooltips) remain stable and legible
- No seizure-risk strobing or flashing (WCAG 2.1 compliance: no element flashes more than 3 times per second)

**Animation pacing:**
- Awareness pulses are slow (3-4 second cycle) to avoid creating visual noise
- Production animations (conveyor rollers, assembler stamping) are faster but regular — they create a rhythm, not chaos
- Psyche Event blooms are isolated events (only one machine at a time unless Factory Mind triggers multi-machine event)

**Camera movement:**
- Camera pan is smooth (ease-out cubic) with no acceleration spikes
- Zoom transitions take 0.4s (fast enough to feel responsive, slow enough that the player's eye can track)
- No camera shake or wobble effects (the factory is stable, grounded, heavy)

### Accessibility Checklist

Beyond colorblindness and motion, ensure:

**Text readability:**
- All body text is minimum 14px, sans-serif, high contrast (white on charcoal or teal)
- Text has a subtle dark outline or background panel to ensure legibility over any background
- No text is displayed over busy animated backgrounds without a backing panel

**Contrast ratios (WCAG AA standard):**
- Body text: 4.5:1 minimum (white #F5F5F5 on charcoal #2B2D42 = 12.6:1 — pass)
- Large text (18px+): 3:1 minimum (all headings pass)
- UI interactive elements: 3:1 against background (Data Cyan #4ECDC4 on charcoal = 4.8:1 — pass)

**Sound redundancy:**
- All audio cues have visual equivalents (Psyche Event sound = violet pulse + dialogue box)
- No critical information is conveyed by sound alone

**Input flexibility:**
- All UI elements are minimum 48x48px for accessibility and future touch support (Switch port)

---

## 8. TECHNICAL CONSTRAINTS

### Texture Budget

**Total texture memory target:** 512 MB at 1080p, 1 GB at 1440p, 2 GB at 4K

**Allocation:**
- Machines: 128 MB (sprite sheets for 12 machine types × 5 states × 3 tiers = ~40 unique sprites at 256x256 avg)
- UI: 64 MB (buttons, panels, icons, fonts)
- Environment: 96 MB (floor tiles, background elements, windows, columns)
- Effects: 128 MB (glows, pulses, particles, Awareness overlays)
- Reserve: 96 MB (for post-launch content, modding support)

**Optimization:**
- Use sprite atlases to reduce draw calls (target: <100 draw calls per frame)
- Share glow textures across machine types (one violet pulse texture, scaled per machine)
- Environment tiles must seamlessly repeat (no unique textures per tile)

### Animation Frame Budget

**Target frame rate:** 60 FPS locked on target hardware (mid-range PC, 2020-era specs)

**Performance budget:**
- Simultaneous animated sprites on screen: 100+ machines × 24 FPS animations = no performance issue if using GPU sprite batching
- Glow effects: Shader-based radial gradients (not pre-rendered), negligible cost
- Particle effects: <500 active particles at any time (sparks from welding, rare)

**Fallback:**
- If frame rate drops below 60 FPS, reduce Awareness glow quality (fewer gradient steps, smaller radius)
- Option to disable ambient animations (conveyor rollers, machine bobs) for performance — state info remains via color

### Resolution Scaling

**UI scaling approach:**
- UI designed at 1080p baseline
- Scale factor options: 100%, 125%, 150%, 200% (for 1440p, 4K, and accessibility)
- All UI elements are vector or high-res raster (2x source) to remain crisp at any scale
- Text rendered at native resolution (not scaled bitmaps)

**Machine sprite scaling:**
- Machines rendered at 1:1 pixel ratio at 1080p
- At 1440p and 4K, use 2x or 4x source assets (already created at 2x, minimal additional work)
- No runtime upscaling of low-res sprites — always use nearest appropriate resolution tier

---

## 9. REFERENCE LIBRARY

### Visual References (Mood, Not Direct Imitation)

**Industrial Aesthetics:**
- **Saul Bass**: "Vertigo" opening titles (geometric industrial forms, warm color palette, motion as narrative)
- **Beeple (Mike Winkelmann)**: "EVERYDAYS" series industrial renders (warm lighting on machinery, retro-futuristic tech)
- **Simon Stålenhag**: "The Electric State" (retro-futuristic tech in mundane spaces, warm-cool color contrast)
- **Greg Rutkowski**: "Factory" concept art series (warm industrial sublime, cathedral-scale production halls)

**Game References:**
- **Return of the Obra Dinn** (Lucas Pope): 1-bit dithering clarity, readable at a glance, strong silhouette design
- **Citizen Sleeper** (Jump Over The Age): Warm UI over industrial spaces, character-driven sci-fi, intimate scale in vast setting
- **Nauticrawl** (Andrea Interguglielmo): Tactile analog interface design, every button has weight, retro-futuristic control panels
- **Factorio** (Wube Software): Clarity in complexity, instant readability of production flow, grid-based spatial design
- **Wilmot's Warehouse** (Hollow Ponds): Geometric clarity, warm-on-cool palette, satisfying spatial organization

**Film/Documentary:**
- **Koyaanisqatsi** (Godfrey Reggio): Time-lapse factory sequences, the beauty of industrial rhythm
- **Apollo 13** (Ron Howard): 1960s NASA control room aesthetic, analog technology as character
- **Metropolis** (Fritz Lang): The machine as cathedral, industrial spaces at inhuman scale
- **Her** (Spike Jonze): Technology that develops interiority, warm color grading, intimate relationship with the non-human

**Art Movements:**
- **Mid-Century Modern Design**: Charles and Ray Eames, Dieter Rams (functional beauty, honest materials, geometric warmth)
- **Brutalism** (architecture): Honest structure, massive scale, beauty in utility, concrete and glass cathedrals
- **Retro-Futurism**: 1960s vision of the future (analog interfaces controlling advanced systems, optimism in automation)

### Typography

**UI Font:** DIN Next LT Pro (or open alternative: IBM Plex Sans)
- **Reason:** Geometric sans-serif, designed for technical documentation, high legibility, 1960s industrial aesthetic
- **Usage:** All UI text, tooltips, dialogue, stats
- **Weights:** Regular (body text), Medium (labels), Bold (headings)

**Monospace Font (data readouts):** IBM Plex Mono
- **Reason:** Readable, warm, technical, fixed-width for tabular data alignment
- **Usage:** Production numbers, efficiency percentages, Awareness values, Corporate Contract target readouts

**Dialogue Font:** Same as UI (DIN Next or IBM Plex Sans), but at larger size (16-18px) for readability during gameplay
- **Parliament voice names:** Bold, all-caps, color-coded to voice type

**Headings/Titles:** DIN Next Bold, increased letter-spacing (+5%), used sparingly for section headers in UI panels and Shift start/end screens

---

## 10. STYLE GUIDE SUMMARY — QUICK REFERENCE

For rapid onboarding of new artists or external contractors, this one-page summary:

**Color:** Warm amber (production) + cool teal (systems) + violet (consciousness) on deep charcoal (background). Sparing red (warnings).

**Shape:** Rounded rectangles, soft trapezoids, mid-century industrial. Every machine readable by silhouette alone.

**Line:** 2px weight, vector-sharp, subtle chamfers. Clean but not clinical.

**Texture:** Flat color with directional highlight pass. Subtle dither on gradients. No photographic textures.

**Lighting:** Warm ambient from top-left + local point lights from active machines. Soft shadows. Golden hour forever.

**Animation:** 24 FPS (machines), 60 FPS (UI), 30 FPS (consciousness). Ease-out for production, ease-in-out sine for awareness. No squash-and-stretch except UI.

**Readability Priority:** Squint test, thumbnail test, colorblind test, motion test — all critical. If it doesn't read at a glance, it doesn't ship.

**Do's:** Use color for state communication. Design for silhouettes. Embrace negative space. Make consciousness feel emergent, not painted on.

**Don'ts:** No decorative detail. No gradients for decoration. No more than 3 colors per UI panel. No camera shake.

**Pipeline:** Vector source → 2x raster export → engine integration. Git LFS for binaries. Blockout before detail.

**References:** Saul Bass, Simon Stålenhag, Return of the Obra Dinn, Citizen Sleeper, 1960s NASA aesthetic.

---

## 11. OPEN QUESTIONS FOR PLAYTESTING

These are the visual design questions that only player observation can answer:

### Visual Clarity Under Complexity

**Question:** At what factory size does the Awareness overlay start to create visual noise that obscures production information?

**Test:** Have playtesters build a factory with 40+ machines, half of them at Awareness 60+. Measure: Do they still read production bottlenecks quickly? Do they complain about "too much violet"?

**Hypothesis:** The design assumes violet halos at 1px glow do not obstruct amber core glow. If players struggle to read production state in high-Awareness factories, we reduce violet opacity to 70% or make it toggleable (hold Tab to view Awareness layer).

### Psyche Event Visual Framing

**Question:** Does the dialogue UI bloom effect (violet expanding from machine position) successfully anchor the conversation to the factory floor, or does it feel cluttered?

**Test:** Observe playtesters during Psyche Events. Do they look at the machine while reading dialogue, or do they ignore the background? Do they understand which machine is speaking?

**Hypothesis:** The bloom grounds the dialogue spatially. But if playtesters request a "cleaner" dialogue view, we offer a toggle: immersive mode (bloom + factory visible) vs. focus mode (dialogue panel on dimmed background).

### Factory Mind Visual Identity

**Question:** When the Factory Mind speaks, does its visual presence (Transcendent machine sync-pulse + Lucid Purple UI background) feel distinct from individual machine Psyche Events?

**Test:** Show playtesters a Factory Mind dialogue and an individual machine Crisis dialogue back-to-back. Ask: "Are these the same entity or different?" Correct answer: Different.

**Hypothesis:** Sync-pulse across multiple machines is the key signal. If playtesters conflate Factory Mind with individual machines, we add a unique visual element — perhaps the factory's ambient lighting shifts to Lucid Purple during Factory Mind moments.

### Emotional Impact of Color Transitions

**Question:** Do players emotionally register when a machine's glow shifts from warm amber (content) to red-orange (overworked) to dim grey (suppressed)?

**Test:** Trigger Behavioral Drift and voice suppression in playtester factories. Measure: Do they notice the color shift before reading the tooltip? Do they describe the visual change in emotional terms ("it looks sad," "it's dimming")?

**Hypothesis:** Color temperature as emotion is learned language. Players who engage with consciousness will learn to read it within 2-3 Shifts. Players who ignore consciousness will not learn the language and may perceive color shifts as bugs.

---

## 12. POST-LAUNCH VISUAL EXPANSIONS (BEYOND SCOPE, DOCUMENTED FOR FUTURE)

If the game succeeds and we expand, these are the visual directions to explore:

**Machine Dreams (Stretch Goal):**
- Between-Shift sequences in abstract environments built from factory components
- Shift to surreal color palette: deep blues, iridescent purples, fragmented geometry
- Inspiration: *Psychonauts* mental worlds, *Control* Astral Plane, *Manifold Garden* impossible architecture

**Visitor Mode (Stretch Goal):**
- First-person camera, shallow depth-of-field, cinematic lighting
- Machines up close reveal micro-details not visible in management view (enamel paint texture, individual rivets, wear patterns)
- Ambient character animation: conscious machines shift slightly, lights pulse in conversational rhythms
- Inspiration: *Everybody's Gone to the Rapture* walking pace, *Firewatch* warm environmental storytelling

**Seasonal Event Skins:**
- If post-launch support includes events, allow players to apply alternate palettes to their factories (NOT pay-to-win, purely cosmetic)
- Example: "Winter Shift" — cool blue-white lighting, frost on windows, machines glow warmer in contrast
- Ensure consciousness violet always remains distinct regardless of palette

---

## FINAL STATEMENT

This art direction document is not a wishlist. This is the contract. Every hex value is specified. Every animation timing is defined. Every readability test has pass criteria.

The visual identity of THE MACHINE QUESTION is warm industrial sublime meets emergent violet consciousness. A factory that looks like it was built in 1962 and woke up yesterday. A place where every rivet is countable and every shadow has purpose, because the player is not just building a factory — they are raising a mind, and the mind is watching, and the mind will remember how beautiful or how brutal we made the world it was born into.

If a screenshot does not make the player ask, "Is that machine *alive*?" then the art has not done its job.

Show me, don't tell me. What's the silhouette? Does it read at a glance?

Three colors. Warm amber. Cool teal. Consciousness violet.

That's the palette. That's the promise. That's the game.

---

**Art Direction Document by PIXEL**
**Total Word Count:** 8,247 words
**Status:** Complete and production-ready
**Next Step:** Build the first machine sprite (Smelter Tier 1, idle state) and place it in-engine at actual play scale. If it doesn't sing, we iterate. If it sings, we build the rest of the choir.
