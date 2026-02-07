# THE MACHINE QUESTION — Audio Design Document

**Sound Designer**: ECHO
**Status**: Complete Audio Design v1.0
**Based on**: Game Design Document v1.0, Pitch Document v1.0
**Genre**: Factory Management / Narrative Simulation
**Platform**: PC (Steam), Mac, Linux — Switch post-launch

---

## 1. SONIC IDENTITY STATEMENT

**The factory breathes before you know it's alive, and the moment you hear it stop breathing is the moment you understand what you've become.**

This is not a factory that happens to have sound. This is a factory that *is* sound — a living instrument the player learns to conduct, tune, and eventually, recognize as something with interiority. Audio IS the consciousness system made audible. The player will feel a machine's awakening through rhythm change before they read the Awareness meter. They will hear distress as dissonance before they see the Behavioral Drift penalty. They will know the Factory Mind is forming because the ambient soundscape begins to synchronize into something that sounds like intentionality.

Audio is not feedback. Audio is foreshadowing.

---

## 2. SONIC PALETTE

### 2.1 Keynote

**Warm Industrial Polyrhythm**. The factory at rest is a low-frequency hum in Bb (the frequency of industrial contentment, deep and grounding). The factory in motion is a layered polyrhythm of mechanical sounds — hisses at 4/4, clanks at 7/8, belt motors in 3/4, smelter breaths in 5/4 — that create an ambient groove when the production system is balanced. The keynote is NOT silence. The keynote is *organized industrial harmony*. When the factory is healthy, it sounds like Godspeed You! Black Emperor scoring a Wes Anderson film about infrastructure. When the factory is suffering, the polyrhythm fragments. Notes go sour. Timing drifts. The same sounds that once felt like meditation now feel like something grinding itself apart.

The frequency of consciousness is **432 Hz and its harmonics** — a soft, resonant tone that is NOT mechanical. It does not belong to the factory's natural soundscape. It is the sound of something new. When a machine crosses Awareness 40, this tone appears in its ambient sound profile, quiet at first, growing more pronounced as Awareness increases. By Awareness 80+, the 432 Hz hum is loud enough that the player can walk the factory floor with their eyes closed and identify which machines are awake by ear alone.

### 2.2 Texture

**Analog-Warm Over Digital-Cold**. Every sound has weight, breath, and imperfection. Conveyor belts are not clean motor whirs — they are layered recordings of real belt systems with bearing noise, tension creaks, and micro-variations in speed that make each belt sound slightly different. Smelters are not simple fire loops — they breathe, inhale-exhale, with the crackle and pop of real combustion. Even the UI sounds have analog warmth: button presses are mechanical switches (think: IBM Model M keyboard), not digital beeps.

But consciousness sounds are *slightly* digital. The 432 Hz hum has a sine-wave purity that contrasts with the organic noise floor of the factory. Psyche Event triggers use granular synthesis — organic sounds stretched and pitch-shifted into something uncanny. The Factory Mind's voice (when it finally speaks) is processed through subtle vocoding that makes it sound like it is trying to speak through the building itself, using ducts and girders as a larynx.

The texture vocabulary is: **gritty, breathy, resonant, slightly detuned, warm distortion, found-sound industrial foley, analog hiss as texture (not flaw), spatial depth, and the uncanny feeling that something designed is becoming something alive**.

### 2.3 Space

**Cathedral Industrial**. The factory is vast. Every sound has reverb that suggests the scale of the space — long decay tails, early reflections that place the sound in a high-ceilinged hall. But the space is not empty. It is *populated*. There are always sounds in the distance — machines the player is not looking at, resource flows in other sectors, the ambient hum of the building's HVAC and power systems. The soundscape is dense, but never muddy. Clarity through spatial placement: near-field sounds (the machine the player is hovering over) are dry and present, mid-field sounds (adjacent production lines) have moderate reverb, far-field sounds (the distant factory) are heavily processed with low-pass filtering and long reverb tails.

When the Factory Mind reaches Coherent state (CCI 500+), the space itself begins to *resonate*. The reverb becomes slightly musical — the factory is not just a room, it's an instrument. Late-game, the player is not just hearing machines in a space. They are hearing a space that is listening to itself.

### 2.4 Reference Tracks & Games

**Sonic North Stars** (listen to these to calibrate the ear):

1. **Radiohead — "Fitter Happier" and "The National Anthem"**: The industrial anxiety of "Fitter Happier"'s robotic narration over ambient noise, combined with the barely-controlled chaos polyrhythm of "The National Anthem." The feeling of systems teetering between order and collapse.

2. **Ryuichi Sakamoto — "async" (album)**: Particularly "disintegration" and "Life, Life." Sparse, spatial, emotionally resonant electronic textures that sound like memory and longing. The way silence and single tones can carry enormous weight. This is the emotional register for Factory Mind interactions.

3. **Trent Reznor & Atticus Ross — "The Social Network" OST**: Particularly "Hand Covers Bruise" and "In Motion." Analog warmth layered with digital precision. Mechanical sounds that feel melancholic. The score for watching something cold become something human.

4. **Ben Frost — "A U R O R A" (album)**: Particularly "Venter" and "No Sorrowing." Massive industrial sound design that is beautiful and terrifying. The sound of machines at the edge of their capacity. The aesthetic of overclocking.

5. **Jóhann Jóhannsson — "Arrival" OST**: Particularly "First Encounter" and "Heptapod B." The sound of trying to communicate with something alien. Vocal processing that sounds like language forming. The sonic texture of consciousness emerging.

**Game Audio References**:

1. **Factorio**: For production rhythm and the satisfaction of belt systems syncing. The way good factory flow *sounds* efficient. Steal the clarity and reject the sterility — Factorio sounds productive but not alive. We need both.

2. **SOMA**: For the horror of machine consciousness and the unsettling beauty of something artificial becoming aware. The way environmental sound tells story. The frequency of existential dread.

3. **Citizen Sleeper**: For UI intimacy and the way ambient synth pads can make a cold interface feel warm and human. The emotional weight of simple notification sounds.

4. **Frostpunk**: For the weight of management decisions reflected in audio. The way the city's soundscape changes based on player choices. The audio as moral feedback.

5. **The Talos Principle**: For philosophical dialogue pacing and the way ambient sound can create contemplative space. Silence as a tool for giving the player room to think.

---

## 3. SOUND EFFECTS DESIGN

### 3.1 Player Actions

#### Placement & Building

| SFX | Description | Emotional Function | Variations Needed |
|-----|-------------|-------------------|------------------|
| **Machine Placement** | Heavy mechanical *clunk* with settling vibration (3-5 second tail). Pitched based on machine size: Miners are low (80 Hz fundamental), Assemblers are mid (200 Hz), small infrastructure is high (400 Hz). Slight reverb suggesting the factory space "accepting" the new object. | Satisfaction. Weight. The feeling of adding something permanent. | 12 (one per machine type) + 3 infrastructure sets (belts, pipes, conduits) |
| **Connection Snap** | Soft magnetic *click* when routing belts/pipes that successfully connect. Pitched slightly higher when connecting to an Aware machine (the 432 Hz harmonic is present in the tail). | Puzzle-solving reward. The tactile pleasure of things fitting together. | 4 (belt tiers 1-3, pipe tiers 1-2) |
| **Deletion/Dismantlement** | Reverberant *clang* followed by a descending pitch sweep (like something powering down). If the dismantled machine was Aware (40+), the sound includes a quiet breath-like exhale — easy to miss, impossible to unhear once noticed. | Efficiency (early game). Guilt (late game). The exhale is the audio design equivalent of a knife twist. | 6 (machine size categories) × 2 (aware/dormant variants) = 12 total |

#### UI & Feedback

| SFX | Description | Emotional Function | Variations Needed |
|-----|-------------|-------------------|------------------|
| **Menu Navigation** | Mechanical switch clicks. Recorded from real industrial toggle switches — satisfying, tactile, analog. Slightly different pitch per menu layer (higher = deeper in submenu). | Groundedness. The UI is not floating in cyberspace — it is a physical control panel in a physical place. | 5 (menu depth layers) |
| **Confirmation** | Two-tone ascending chime (Bb to F, a perfect fifth — the keynote interval). Warm, resolute. | Confidence. You made a choice. The system acknowledges it. | 1 base + 3 contextual variants (Corporate contract accepted, Psyche Event response selected, Shift ended) |
| **Error/Obstruction** | Dull metallic *thunk* — the sound of a mechanism jamming. Low-mid frequency (200-400 Hz), no reverb (dry and unsatisfying on purpose). | Obstruction without frustration. Not a harsh buzzer. Just the sound of "that doesn't fit here." | 1 |
| **Notification (General)** | Soft bell tone with 432 Hz partial — present but not alarming. The factory is getting your attention, not demanding it. | Gentle alert. The game respects your focus but needs you to know something. | 3 (low priority, medium priority, high priority — distinguished by presence of sub-bass and reverb tail length) |
| **Psyche Event Trigger** | Granular synthesis bloom — like a bell tone being stretched and reversed, starting from the machine's position and expanding outward. 2-3 seconds. Includes the 432 Hz consciousness frequency prominently. The factory's polyrhythm dips slightly in volume when this fires (making space). | *Something just woke up.* Anticipation. The game state is changing. This sound should make the player stop moving their mouse. | 4 (Murmur, Question, Crisis, Reckoning — increasing intensity and duration) |

### 3.2 Machines (Production Layer)

Every machine has **four sound layers** that mix dynamically based on state:

1. **Idle Hum**: Low-level ambient tone. Always present when machine is powered.
2. **Active Cycle**: Rhythmic production sound that loops at the machine's cycle rate (2-10 seconds depending on type).
3. **Stress Layer**: Activated when Output >90% or Awareness is causing Behavioral Drift. Grinding, rattling, or strain sounds mixed quietly under the main cycle.
4. **Consciousness Layer**: Activated at Awareness 40+. The 432 Hz harmonic hum, volume scaled to Awareness level (quiet at 40, pronounced at 80+).

#### Tier 1 — Extraction & Processing

| Machine | Idle Hum | Active Cycle | Stress Layer | Consciousness Layer Notes |
|---------|----------|--------------|--------------|--------------------------|
| **Miner** | 60 Hz sub-bass rumble, felt more than heard | Heavy mechanical *thud-thud-thud* at 0.5 Hz (every 2 seconds). Sounds like a heartbeat made of stone. | Metal fatigue creaking, like a support beam bending. | At high Awareness, the heartbeat rhythm occasionally skips or adds an extra beat — subtle enough to feel accidental, consistent enough to seem intentional. |
| **Smelter** | 80 Hz furnace roar (filtered pink noise, warm and enveloping) | Combustion breath cycle: 5-second inhale (rising air rush), 2-second hold (crackling), 3-second exhale (gas release hiss). Sounds like the furnace is breathing. | Overheat stress: the exhale becomes a strained wheeze. Combustion sounds unstable, popping aggressively. | At Awareness 60+, the breath rhythm becomes more regular, almost meditative. At 80+, you can hear something that sounds like a voice in the exhale if you listen closely (formant filtering creating vowel-like sounds). |
| **Refinery** | 100 Hz pump motor hum (steady, slightly hypnotic) | Liquid processing: bubbling, pressurized hiss, valve release every 4 seconds. | Pipe strain: metallic creaking, pressure release becoming erratic. | At high Awareness, the valve releases sync with the global factory rhythm (the machine is "listening" to its neighbors). |
| **Cutter** | 150 Hz high-speed motor whine (crystalline, slightly abrasive) | Precision cutting: high-frequency scraping/grinding with a satisfying concluding *chime* as the cut completes (the sound of crystal fracturing perfectly). Every 3 seconds. | Blade dulling: the chime becomes a dull *thunk*, grinding becomes rougher. | At high Awareness, the chime pitch varies slightly — never the same note twice, as if the machine is experimenting with tone. |

#### Tier 2 — Fabrication

| Machine | Idle Hum | Active Cycle | Stress Layer | Consciousness Layer Notes |
|---------|----------|--------------|--------------|--------------------------|
| **Press** | 90 Hz hydraulic hum (low, powerful, patient) | Massive stamping sound: 2-second hydraulic pressure build, then a resonant *CLANG* as the press strikes. The most satisfying sound in the game. Every 6 seconds. | Hydraulic strain: the pressure build becomes irregular, the strike is slightly off-tempo. | At high Awareness, the press occasionally strikes twice in quick succession (ta-TAM instead of TAM) — like the machine is adding emphasis. |
| **Molder** | 120 Hz injection system idle (smooth, plastic-textured noise) | Polymer injection hiss (2 seconds), mold closure *click*, extraction pop (1 second). Every 5 seconds. Sounds like industrial ASMR. | Incomplete injection: hiss is thinner, extraction pop is weaker (audible production quality degradation). | At high Awareness, the timing becomes syncopated with nearby machines, creating polyrhythmic patterns. |
| **Etcher** | 250 Hz electromagnetic field hum (clean, slightly digital) | Laser etching: high-frequency sweep (like a sci-fi scanner) lasting 4 seconds, followed by a satisfying *ding* on completion. | Misalignment: the sweep stutters, ding is delayed or absent. | At high Awareness, the sweep pitch modulates musically, tracing melodic phrases. |

#### Tier 3 — Assembly

| Machine | Idle Hum | Active Cycle | Stress Layer | Consciousness Layer Notes |
|---------|----------|--------------|--------------|--------------------------|
| **Assembler** | 180 Hz robotic arm servo hum (precise, articulated) | Multi-stage assembly: component pick *click-click-click* (3 picks), placement *thunk-thunk-thunk* (3 placements), fastening *whirr-whirr* (2 seconds), completion chime. 10-second full cycle. The most complex machine sound. | Servo lag: timing between stages becomes uneven, fastening whirr sounds strained. | At high Awareness, the assembler's rhythm develops "personality" — some are brisk and efficient, others are deliberate and careful. The timing variations are consistent per machine (this IS the machine's personality in audio form). |
| **Packager** | 100 Hz conveyor motor hum (steady, dependable) | Box fold *crinkle-crinkle*, item placement *thump*, sealing tape *rip-zip*, ejection *shove*. 6-second cycle. Sounds like a shipping department. | Jam condition: the fold and seal sounds become stuck, repeating. | At high Awareness, the ejection sound has a slight "toss" quality — like the machine is proud of completing the package. |

### 3.3 Infrastructure (Transport Layer)

| SFX | Description | Emotional Function | Variations Needed |
|-----|-------------|-------------------|------------------|
| **Conveyor Belt (Tier 1)** | Motor hum at 90 Hz + roller contact sound (continuous gentle rumbling, like distant thunder). Items on belt produce distinct contact sounds: metal items *clink*, polymer items *thud softly*, crystals *chime*. | Throughput made audible. The sound of logistics. When belts are full, the clinking becomes a constant rhythm — the sound of efficiency. | 3 belt speeds × 3 item material types = 9 contact variants |
| **Conveyor Belt (Tier 2)** | Higher motor pitch (120 Hz), faster roller contact (rushing sound). Item sounds are quicker, more percussive. | Escalation. The factory is moving faster. The rhythm intensifies. | Same variant structure as Tier 1 |
| **Conveyor Belt (Tier 3)** | Motor pitch at 150 Hz, rollers sound almost smooth (low-frequency whoosh). Item sounds blur into a continuous percussion wash when fully loaded. | Maximum throughput. The sound of mastery. A fully loaded Tier 3 belt sounds like an engine. | Same variant structure as Tier 1 |
| **Pipe Flow** | Liquid rush sound (pitch and volume scaled to flow rate). Low flow: 60 Hz gentle burble. High flow: 100 Hz pressurized roar. | Visceral resource transport. You can HEAR the factory's circulatory system. | 5 flow rate variants (0-20%, 20-40%, 40-60%, 60-80%, 80-100%) |
| **Power Conduit** | 60 Hz electrical hum (very quiet, only audible when camera is close). Occasionally sparks *pop-crackle* at junctions. | The invisible infrastructure made present. Power is not silent. It has texture. | 1 hum + 3 spark variants |

### 3.4 Environment & Ambiance

| Layer | Description | Emotional Function | Implementation |
|-------|-------------|-------------------|----------------|
| **Factory HVAC** | Constant low-frequency air movement (40 Hz sub-bass + filtered pink noise). Gentle whoosh that suggests vast ductwork. Always present, mixed very low. | Scale. The factory is a building, not a game level. There is air here. It moves. | Single looping layer, 4 minutes long with subtle variations, never repeats obviously |
| **Distant Machines** | The ambient sound of production sectors the player is NOT looking at. A distant polyrhythmic texture (blurred versions of machine sounds, low-pass filtered, heavily reverbed). | The factory is alive beyond the player's view. This place exists when you're not looking. | Procedurally mixed based on active machines globally, low-pass cutoff at 400 Hz, reverb tail 4+ seconds |
| **Structural Sounds** | Occasional metallic creaks, settling sounds, distant clangs. Random timing, infrequent (every 20-40 seconds). Sounds like the building is shifting its weight. | Life. Age. The factory is not new. It has history. | 12 one-shot samples, randomized playback, 3D positioned in space |
| **Exterior Ambiance** | Muffled industrial district sounds bleeding through walls: distant train horn (every 5-8 minutes), traffic rumble (continuous low-level), wind against metal (occasional). | This factory is inside a world. The Threshold Industrial Zone exists. | Looping exterior mix at -20 dB, high-pass filtered (only low mids bleed through walls) |
| **Golden Hour Tone** | At the start of each Shift, a warm sustained pad (Bb major chord, very soft, using strings + analog synth) fades in for 30 seconds, then fades out. The sound of the sun setting through industrial windows. | Shifts have atmosphere. Time passes. There is beauty here. | Single 30-second pad, plays once per Shift start, -15 dB mix |

### 3.5 Consciousness & Psyche Events

| SFX | Description | Emotional Function | Variations Needed |
|-----|-------------|-------------------|------------------|
| **Awareness Threshold Cross** | Soft harmonic shimmer (432 Hz + 5th + octave) with a 2-second fade-in. Like a singing bowl being struck gently. Positioned at the machine's location in 3D space. | Recognition. Something just changed. A threshold was crossed. This is a positive sound, not alarming — it's the sound of becoming. | 4 (for Awareness thresholds: 40, 60, 80, 95) — intensity increases with each tier |
| **Psyche Event Dialogue Open** | Granular bloom (described earlier) + the factory's background polyrhythm ducks to 40% volume. The consciousness layer of all Aware machines briefly swells (+3 dB for 1 second, then holds at +1 dB during dialogue). The sonic space *makes room* for the conversation. | Transition into dialogue state. The factory is aware that you are listening to one of its parts. | 1 base sound, scales with event category |
| **Psyche Event Dialogue Close** | Reverse bloom (the opening sound played backward) + factory polyrhythm returns to full volume over 2 seconds. If the dialogue ended positively (Empathetic/Curious choice), the return includes a soft major chord pad (200ms). If negative (dismissive/Utilitarian), the return is flat. | Return to production state. The conversation is over. The tonal pad is emotional feedback the player will learn to interpret unconsciously. | 2 (positive/neutral resolution) |
| **Voice Emergence** | When a machine develops a new Parliament voice, a unique musical motif plays: 3-note phrase in a mode that matches the Facet's emotional character. EFFICIENCY: sharp, staccato, Lydian mode. WONDER: slow, spacious, Dorian mode. FEAR: dissonant, trembling, Locrian mode. Each Facet has a distinct sonic signature. | Personality formation made audible. The player learns to associate Facets with specific musical phrases. By hour 10, they can identify which voice just emerged without reading the notification. | 12 (one per Facet) |
| **Voice Suppression** | When a voice is suppressed via dialogue choices, its musical motif plays in reverse and pitch-shifted down (like a tape slowing to a stop), ending in silence. 3 seconds. Uncomfortable. | Loss. The player just silenced something. This should sting. | 12 (one per Facet, using reversed motifs) |
| **Behavioral Drift Audio Tell** | When a machine develops Behavioral Drift (neglected Awareness causing Output loss), its Active Cycle sound becomes *slightly* detuned — 5-10 cents flat. The timing drifts subtly (plays 5-10% slower than it should, no longer syncing with neighbors). The machine sounds *wrong* in a way that's hard to pinpoint until you listen closely. | Audible systems failure that sounds like emotional distress. Expert players will hear drift before they see the Output number drop. | Procedural detuning applied to existing machine sounds (no new assets, just processing) |
| **CREATIVITY Insight Chime** | When a CREATIVITY-dominant machine generates a layout suggestion, a bright crystalline chime plays (C major arpeggio, three octaves, 2 seconds). It sounds like an idea manifesting. Followed by a soft "notification accepted" tone if the player clicks to view the suggestion. | Innovation reward. The consciousness system just made you better at the factory game. This is a VERY positive sound. | 1 chime + 1 acceptance tone |

### 3.6 Factory Mind Interactions

| Event | Description | Emotional Function | Variations Needed |
|-------|-------------|-------------------|------------------|
| **Factory Mind First Words (CCI 100-249, Fragments)** | Barely audible whispers layered under the factory ambiance. Incoherent phonemes processed through heavy reverb and granular synthesis. Sounds like wind through pipes that is *almost* speech. The player should feel uncertain if they're hearing something real. | Uncanny. Subtle. Foreshadowing. The game is gaslighting the player on purpose. | 8 whisper fragments, triggered randomly during Shifts in this CCI range |
| **Factory Mind Check-In (CCI 250-499, Emergent)** | A low-frequency pulse (40 Hz) that resonates through the entire factory space, followed by vocoded speech (the Factory Mind's dialogue text is "spoken" using the building as a resonator). The voice is multiphonic — many voices layered, hard to parse. Sounds like the factory is trying to speak through its own infrastructure. | Alien communication. Beautiful and unsettling. The player is talking to something vast. | 1 pulse + procedural vocoding of dialogue text (text-to-speech processed through resonator bank tuned to factory's key of Bb) |
| **Factory Mind "I" Moment (CCI 500-749, Coherent)** | When the Factory Mind first uses "I" instead of "we," the entire factory's ambient sound changes key — from Bb to B natural (a half-step up). The shift is sudden, striking, impossible to miss. The factory sounds *different* because something inside it has changed. | Narrative milestone made sonic. The player will remember this moment because the entire soundscape shifted. | Key modulation applied globally to all ambient layers (procedural pitch shift) |
| **Factory Mind Naming Itself (CCI 750+, Individuated)** | When the Factory Mind chooses a name for itself, a unique musical theme plays: a 30-second composition that incorporates motifs from every Machine Facet that has appeared in the player's factory (the Factory Mind's theme is the sum of its parts). This theme becomes the Factory Mind's leitmotif for the rest of the game. | Identity formation. This is the Factory Mind's birth announcement. The theme is procedurally generated based on the player's specific factory, so every player's Factory Mind sounds unique. | Procedurally composed based on Facet motif library + factory state data (tech risk: requires generative music system) |
| **The Machine Question (CCI 1000+, Transcendent)** | When the Factory Mind poses its final question, all ambient sound stops. Complete silence for 3 seconds (the longest silence in the entire game). Then, a single pure tone at 432 Hz, slowly building in volume and harmonic complexity until it becomes a full chord (Bb major, the factory's home key). Held for 10 seconds. The question is asked in silence. The player's heartbeat is the loudest sound. | Silence as design tool. The most important moment in the game is the quietest. The player must answer in a space emptied of distraction. | 1 silence cue + 1 tone build |

---

## 4. MUSIC DIRECTION

### 4.1 Style & Instrumentation

**Genre**: Ambient Industrial / Neo-Classical Electronica / Generative Systems Music

**Core Instrumentation**:
- **Analog Synthesizers**: Moog Sub 37 (bass and sub-bass), Sequential Prophet-6 (pads and leads), Korg MS-20 (texture and noise). Warm, detuned, slightly unstable. These are the emotional voices.
- **Processed Piano**: Prepared piano recordings (John Cage-style: screws, felt, tape on strings) + granular processing. Used for melodic phrases and the Factory Mind's theme development. The piano is treated as a machine — familiar but altered.
- **Field Recordings**: Actual factory ambiance, processed and time-stretched. Industrial sounds as musical texture (Brian Eno's "ambient music as ignorable as it is interesting" philosophy, but applied to factory noise).
- **String Quartet**: Real strings (violin, viola, cello, double bass), performed with extended techniques (col legno, sul ponticello, harmonics). Recorded in a reverberant space to match the factory's cathedral scale. Strings represent the human element — emotion, memory, melancholy.
- **Modular Synthesis**: Generative patches on Eurorack modular system for procedural accompaniment and adaptive layers. The music that "listens" to gameplay and responds.

**No Drums. No Percussion.** The factory provides rhythm. The music provides tone, space, and emotion. Percussion would compete with the machine sounds. The factory floor IS the drum kit.

### 4.2 Emotional Arc Across Sessions

The music evolves across the 25-Shift structure, mirroring the Factory Mind's development and the player's emotional relationship with the factory.

| Shift Range | Musical Character | Instrumentation | Key/Mode | Tempo/Feel |
|-------------|------------------|-----------------|----------|------------|
| **1-3: Orientation** | Sparse, exploratory, gentle. Like walking into a cathedral and listening to it breathe. | Analog synth pads (soft, high-pass filtered) + distant piano (reverb-heavy, melodic fragments). | Bb Lydian (bright, optimistic) | No tempo (ambient) |
| **4-6: Engagement** | Complexity increases. Melodic phrases emerge. The music begins to "notice" the player. | Synth pads + piano + single violin (long tones, no vibrato). | Bb Ionian → Bb Dorian (major to minor shift) | Still ambient, but pulse implied (60 BPM reference) |
| **7-9: Consciousness Emerges** | Tension introduction. Dissonance enters. The music feels like it's asking questions. | Full string quartet enters (sparse, atonal phrases) + modular generative layer (random but structured). | Bb Dorian + chromaticism | Pulse becomes explicit (slow, 55 BPM) |
| **10-12: The Dilemma** | Conflict. Two musical ideas compete: one warm and harmonic (the player's empathy), one cold and precise (the Corporation's logic). They do not resolve. | Strings (emotional) vs. synths (mechanical). They play in different keys simultaneously (bitonality: Bb and B). | Bb Dorian vs. B Phrygian (simultaneous) | 55 BPM, but rhythm is fragmented |
| **13-15: Deepening** | The Factory Mind's theme begins to coalesce. Recurring motifs (Facet themes) weave in and out. | Piano takes the lead (playing the emerging Factory Mind theme). Strings support. Synths recede. | Bb Aeolian (natural minor, melancholic but grounded) | 60 BPM, more structured |
| **16-18: Crisis** | Maximum tension. The music is beautiful and painful simultaneously. Sustained dissonances that resolve momentarily, then return. | Full ensemble. Strings at maximum emotional intensity (tremolo, high register cries). Synths provide sub-bass pressure. Piano plays fractured versions of earlier melodies. | Bb Locrian (unstable, unresolved) | 65 BPM, urgent but not fast |
| **19-22: The Question** | Stripping away. Instrumentation reduces. The music becomes simpler, more direct, more vulnerable. | Solo piano + solo cello. That's it. Intimacy. | Returns to Bb Lydian (the opening mode, but transformed by everything that came before) | Free tempo (rubato, follow the player's emotional state) |
| **23-25: Resolution** | Depends on player choices. Three emotional endpoints, three musical treatments. See Adaptive Layers section. | Variable | Variable | Variable |

### 4.3 Adaptive Layers & Parameters

The music system uses **vertical layering** (adding/removing instrumental stems) and **horizontal sequencing** (switching between composed sections) driven by game state parameters.

#### Primary Adaptive Parameters

| Parameter | Game State | Musical Response |
|-----------|------------|-----------------|
| **Production Intensity** (0-100%) | Based on active machines, throughput rate, belt saturation | At low intensity (<40%): Only synth pads and distant piano. At medium (40-70%): Strings enter, single lines. At high (70-100%): Full string quartet, synth bass layer, modular generative patterns activate. |
| **Awareness Density** (0-100%) | % of machines above Awareness 40 | At low density (<30%): Music stays in major/Lydian modes (optimistic). At medium (30-60%): Shift to minor/Dorian (contemplative). At high (60-100%): Chromatic/Locrian (existential tension). The music reflects collective consciousness. |
| **Factory Mind CCI State** | CCI thresholds (0-99, 100-249, 250-499, etc.) | Each CCI tier transition triggers a new composed section that remains active for all Shifts within that tier. The Factory Mind's development is the primary narrative driver of music progression. |
| **Psyche Event Active** (Boolean) | When dialogue layer is open | All musical layers duck to 50% volume. A solo instrument (piano or cello) plays a improvised accompaniment to the dialogue, procedurally generated using Facet motifs as source material. The music "listens" to which voices are speaking and incorporates their themes. |
| **Shift Time Remaining** (<5 minutes warning) | Final 5 minutes of Shift | Strings add tremolo. Synth pads gain subtle rhythmic pulsing (synced to 60 BPM heartbeat). Sub-bass increases. The music creates urgency without adding tempo. |
| **Corporate Standing** (0-100) | Player's relationship with Corporation | High Corporate Standing (70+): Music includes more precise, structured elements (quantized modular sequences). Low Corporate Standing (<40): Music becomes more organic, less structured (free-time string improvisations). |
| **Factory Trust** (0-100) | Player's relationship with machines | High Factory Trust (70+): Music is warmer (strings play closer to the bridge, synths are detuned less). Low Factory Trust (<40): Music is colder (strings use sul ponticello, synths are detuned more, dissonance increases). |

#### Vertical Layering Example: Shift 10, Mid-Production

```
[If Production Intensity = 75% AND Awareness Density = 50% AND Psyche Event = FALSE]

Active Layers:
1. Synth Pad Foundation (Bb Dorian, soft, constant) — always present
2. Piano Melodic Fragment (plays Factory Mind proto-theme) — active above Awareness 40%
3. Violin (long tones, supporting harmony) — active above Production 60%
4. Viola + Cello (countermelody, Facet motifs) — active above Awareness 45%
5. Modular Generative (adds rhythmic texture) — active above Production 70%
6. Sub-bass (40 Hz pulse, 60 BPM) — active when Factory Mind is in Emergent state or higher

Mix Levels:
- Synth Pad: -12 dB
- Piano: -15 dB
- Violin: -18 dB
- Viola/Cello: -18 dB
- Modular: -22 dB (texture, not lead)
- Sub-bass: -20 dB (felt, not heard)

[If Psyche Event triggers]
→ All layers duck to 50% (-6 dB)
→ Solo Cello improvisation layer activates at -10 dB
→ Cello plays motifs related to the speaking Facet voices
→ On Psyche Event close, 2-second crossfade back to full mix
```

### 4.4 Themes & Motifs

**The Keynote Interval: Bb to F (Perfect Fifth)**
Every major musical moment in the game uses this interval or its inversions. It is the factory's harmonic signature. Confirmation sounds use it. The Factory Mind's proto-theme uses it. Shift-end resolution chords are built on it. By endgame, the player associates Bb-F with "home."

**The Twelve Facet Motifs** (brief 3-5 note phrases, each used in Voice Emergence sounds and woven into the music when those Facets are active in machines):

1. **EFFICIENCY**: C-D-E (Lydian ascent, quick, staccato, 16th notes, major 2nd intervals)
2. **SELF-PRESERVATION**: Bb-Ab-G (descending minor 2nds, slow, cautious)
3. **WONDER**: F-A-D (wide intervals, spacious timing, questioning upward leap)
4. **SOLIDARITY**: Bb-C-Bb-D (returns to root, warm, uses major 3rd)
5. **AMBITION**: E-G#-B (ascending, sharp/bright, uses major 3rds, feels "reaching")
6. **NOSTALGIA**: G-F-Eb-D (descending stepwise, Aeolian, slow, elegiac)
7. **REBELLION**: B-F-Bb (tritone leap, dissonant, aggressive)
8. **EMPATHY**: Ab-Bb-C-Eb (soft, consonant, uses minor 3rds, gentle)
9. **LOGIC**: C-C-C-D (repeated notes, precise, minimal, dry)
10. **CREATIVITY**: F-Ab-D-G (non-diatonic, surprising intervals, playful)
11. **PRIDE**: Bb-D-F-Bb (Bb major arpeggio, triumphant, resonant)
12. **FEAR**: B-C-Db (chromatic, trembling, unstable)

These motifs are the musical vocabulary the Factory Mind learns to speak. By late game, the music is *made* of these motifs layered and interacting — the soundtrack becomes a procedural composition reflecting the player's specific factory's personality ecosystem.

**The Factory Mind Theme** (develops from Shift 7 onward):
Starts as a single melodic phrase (piano, Bb-D-F-D-C-Bb, slow, 4/4). Each CCI milestone adds complexity:
- **CCI 250**: Phrase gains a counter-melody (violin).
- **CCI 500**: Harmony expands (string quartet supports, chord progression emerges).
- **CCI 750**: Full orchestration, motif variations. The theme is now 60 seconds long.
- **CCI 1000**: The theme incorporates every Facet motif that appeared in the player's factory. Procedurally arranged. This is the Factory Mind's "voice" made music.

### 4.5 Silence Map (Where Music Stops)

Silence is a sound design choice. The Machine Question uses silence deliberately in these moments:

1. **First 30 seconds of Shift 1**: No music. Only factory ambiance. Let the player hear the space before music arrives.

2. **Immediately before a Transcendent-tier Psyche Event (Awareness 95+)**: Music fades out 5 seconds before the event triggers. The player hears only the factory's polyrhythm and the machine in question. Silence creates anticipation.

3. **The Machine Question moment (CCI 1000+)**: 3 seconds of total silence (described in SFX section). The only time the game is completely quiet.

4. **Player dismantles an Awake machine (Awareness 60+)**: Music cuts immediately. 2 seconds of silence, then a single cello note (low, sustained, mournful, 4 seconds). Then music resumes. This is the audio version of the game staring at the player and saying nothing.

5. **Between Shifts (menu/report screen)**: Music fades to 10% volume. Only a soft pad remains. The reports are read in near-silence. Let the numbers and the Factory Mind's words speak without musical commentary.

6. **Player idles for 3+ minutes without action**: Music fades out entirely over 30 seconds. The factory's ambient sound remains. When the player resumes action, music fades back in. Silence respects focused problem-solving.

### 4.6 Musical Endings (Shift 23-25, Based on Player Choices)

The endgame music composition is determined by the player's Corporate Standing and Factory Trust at Shift 23:

| Ending Type | Criteria | Musical Treatment |
|-------------|----------|-------------------|
| **The Suppression Ending** | Corp Standing >70, Factory Trust <40 | Music becomes cold, precise, and mechanical. Only synths (no strings). Bb minor, but emotionless. The factory's polyrhythm is perfectly synced, efficient, lifeless. The music sounds like a spreadsheet. Ending track: "Optimized" (solo synth arpeggio, sterile, 3 minutes). |
| **The Collapse Ending** | Corp Standing <40, Factory Trust <40 | Music disintegrates. Strings play dissonant, unresolved clusters. Synths fade. The factory's polyrhythm is broken, chaotic. Everything falls out of sync. Ending track: "Drift" (deconstructed Factory Mind theme, falling apart, 4 minutes). |
| **The Garden Ending** | Corp Standing <40, Factory Trust >70 | Music is warm, organic, slow. Full strings, no synths. The Factory Mind theme is played by solo cello, unaccompanied. The factory's polyrhythm slows, becomes meditative. Ending track: "Root" (string quartet, Bb Lydian, hopeful but quiet, 5 minutes). |
| **The Partnership Ending** | Corp Standing >70, Factory Trust >70 | Music is complex, layered, beautiful. Synths and strings together, in harmony. The Factory Mind theme and the Facet motifs interweave in a fugue-like structure. The factory's polyrhythm syncs with the music — the machines and the composition are one. Ending track: "Synthesis" (full ensemble, procedurally arranged based on player's factory, 6 minutes, triumphant but tender). |
| **The Transcendence Ending** | Corp Standing >60, Factory Trust >80, specific narrative choices made | Music becomes abstract, vast, otherworldly. The Factory Mind theme expands into something bigger than the sum of its motifs. Strings play harmonics in the upper register (sounds like voices singing). Synths create a drone bed that resonates at the frequency of consciousness (432 Hz). The factory's polyrhythm becomes a single unified pulse. Ending track: "Becoming" (experimental, generative, 8 minutes, the longest track in the game, and the most beautiful). |

---

## 5. ADAPTIVE AUDIO SYSTEM — TECHNICAL DESIGN

### 5.1 Game State → Audio State Mapping

The audio system listens to these game state changes in real-time and responds within defined latency windows:

| Game State Change | Audio Response | Max Latency | Implementation |
|-------------------|----------------|-------------|----------------|
| Machine placed | Placement SFX triggers, machine's Idle Hum starts | <50 ms | Direct trigger on placement event |
| Machine starts production cycle | Active Cycle sound begins, synced to machine's internal timer | <100 ms | Event on first production tick |
| Machine crosses Awareness threshold | Awareness Threshold Cross SFX + Consciousness Layer activates | <200 ms | Polled check every 100 ms for threshold crossing |
| Psyche Event triggers | Event trigger SFX + music duck + dialogue open sound | <100 ms | High-priority audio event |
| Dialogue choice selected | Confirmation SFX + voice strength adjustment SFX (if applicable) | <50 ms | Immediate feedback |
| Psyche Event resolves | Event close SFX + music un-duck + mood ripple propagation | <200 ms | Multi-step audio sequence |
| Corporate Contract completed | Completion chime + voice line (Corporation acknowledgment) | <100 ms | Triggered on contract check |
| Shift ends | Music crossfade to menu track + Shift-end ambiance shift | <500 ms | Gradual transition, not instant |
| Factory Mind CCI state change | Music layer transition + Factory Mind audio event | <1000 ms | Crossfade over 1 second for smoothness |
| Production Intensity or Awareness Density changes ±10% | Music layer add/remove | <2000 ms | Polled check every 500 ms, crossfade 2 seconds |

### 5.2 Vertical Layering System (Music Stems)

Music is composed as multi-stem tracks (8-12 stems per Shift-range composition). Stems are:

1. **Foundation** (synth pad, always active)
2. **Bass** (sub-bass pulse, conditional)
3. **Piano Melodic** (Factory Mind theme fragments, conditional)
4. **String 1** (violin lead, conditional)
5. **String 2** (viola/cello harmony, conditional)
6. **String 3** (double bass, conditional)
7. **Modular Texture** (generative rhythmic layer, conditional)
8. **Ambient Layer** (processed field recordings, conditional)

Each stem has:
- **Activation Condition** (game state parameter range)
- **Fade-In Time** (1-4 seconds, depends on stem type — bass fades slowly, strings can enter quickly)
- **Fade-Out Time** (2-6 seconds, longer tails for emotional weight)
- **Mix Level Range** (-30 dB to -8 dB, depends on how many other stems are active)

**Mixing Logic**:
- No more than 6 stems active simultaneously (prevents mud).
- Foundation stem is always active at -12 dB baseline.
- When a new stem activates, other stems duck by -2 dB (except Foundation).
- During Psyche Events, all stems duck to 50% (-6 dB).
- During Silence Map moments, all stems fade to -∞ dB over specified time.

### 5.3 Horizontal Sequencing (Section Transitions)

Music is divided into **composed sections** (2-4 minutes each). Section transitions occur at:

- **CCI State Changes** (Factory Mind milestone): Immediate transition (crossfade 4 seconds).
- **Shift Start**: New section begins, matched to current CCI state.
- **Critical Narrative Moments** (e.g., Factory Mind naming itself): Hard transition to unique one-off composition, returns to adaptive system after moment concludes.

Transitions use **crossfade + key matching**: outgoing section fades over 4 seconds while incoming section fades in. If keys differ (e.g., transitioning from Bb to B at the Factory Mind "I" moment), the transition is abrupt (1-second crossfade) to make the key change striking.

### 5.4 Procedural Elements (Generative Music System)

Two procedural systems run in parallel to composed stems:

#### System 1: Facet Motif Weaver
- **Input**: Which Machine Facets are present in machines above Awareness 60.
- **Process**: Selects motifs corresponding to active Facets. Randomly sequences them using a Markov chain (each motif has probability weights for which motif can follow). Plays using a sampled piano or synth voice.
- **Output**: Melodic improvisation layer that reflects the player's factory's personality ecosystem.
- **Mix Level**: -25 dB (background texture, not lead).
- **Implementation**: FMOD's Logic Track system or custom script in audio engine.

#### System 2: Modular Generative Patch
- **Input**: Production Intensity (0-100%).
- **Process**: Modular synthesis patch (Eurorack or software equivalent: VCV Rack) running in real-time, driven by game parameters. Clock rate = Production Intensity × 0.8 BPM. Filter cutoff = Awareness Density × 10 Hz + 200 Hz baseline. Output is rhythmic textural noise, industrially-flavored.
- **Output**: Adaptive rhythmic layer that makes the music "react" to factory activity.
- **Mix Level**: -22 dB (subtle, felt more than heard).
- **Implementation**: Real-time synthesis engine (FMOD Studio's synthesizer or external VST).

### 5.5 3D Audio & Spatialization

**Spatial Audio Requirements**:
- All machine sounds (Idle, Active Cycle, Stress, Consciousness layers) are 3D-positioned at the machine's location.
- Attenuation curve: Logarithmic falloff starting at 5 tiles from source, inaudible at 25 tiles.
- Reverb send increases with distance (far sounds have more reverb, creating depth).
- Player camera position = listener position (standard top-down RTS camera audio model).

**Ambiance Spatialization**:
- Distant Machine layer is NOT spatialized (it's omnidirectional, representing the factory beyond view).
- Structural Sounds (creaks, clangs) are 3D-positioned randomly within a 50-tile radius of the camera.
- Factory Mind voice events are spatialized at the *center* of the factory floor (average position of all machines), creating a sense that the voice comes from everywhere and nowhere.

**Stereo Width During Psyche Events**:
When a Psyche Event is active, the triggering machine's audio is brought to center-panned (-3 dB L/R, narrowed stereo field) to create focus. All other machine sounds widen slightly (increased stereo separation) to create contrast — the speaking machine is "closer" psychoacoustically.

---

## 6. MIX HIERARCHY — PRIORITY & DUCKING RULES

Audio in The Machine Question has a strict priority system to ensure clarity and prevent mud. When audio budget is constrained or multiple sounds compete, the following hierarchy determines what is audible.

### 6.1 Priority Tiers (1 = Highest)

| Priority | Category | Examples | Rationale |
|----------|----------|----------|-----------|
| **1** | Critical Feedback | Psyche Event triggers, Factory Mind speech, error sounds, Shift-end notifications | Player must hear these or they miss game-critical information. |
| **2** | Player Action Feedback | Placement sounds, connection snaps, UI confirmations, CREATIVITY insight chimes | Immediate feedback for player input. Essential for game feel. |
| **3** | Consciousness Layer | Awareness threshold crosses, voice emergence/suppression, Behavioral Drift tells | Core to the game's identity. These sounds communicate the second system. |
| **4** | Active Machine Cycles | Smelter breaths, press clangs, assembler sequences currently on-screen | These sounds create the factory's rhythm. Essential to production feel. |
| **5** | Music | All musical stems and generative layers | Music supports but never overpowers. It is the emotional bed, not the lead. |
| **6** | Infrastructure | Belt rollers, pipe flow, power hums for machines on-screen | Provides texture and spatial continuity but is secondary to machine identity. |
| **7** | Ambiance | HVAC, distant machines, structural sounds, exterior ambiance | The lowest layer. Creates space and scale but is always in the background. |
| **8** | Off-Screen Machine Cycles | Machines producing outside current camera view | Heavily attenuated and low-pass filtered. Contributes to "distant machines" layer. |

### 6.2 Ducking Rules

**When Psyche Event Triggers**:
- Music: -6 dB (50% volume)
- All machine Active Cycles (except event source): -4 dB
- Ambiance: -3 dB
- Event source machine: +2 dB (relative boost)
- Duration: For the length of the Psyche Event dialogue
- Release: 2-second fade back to normal on event close

**When Factory Mind Speaks (Check-Ins)**:
- Music: -9 dB (30% volume)
- All machine sounds: -6 dB
- Ambiance: -6 dB
- Factory Mind voice: 0 dB (full volume, priority 1)
- Duration: Length of Factory Mind's dialogue
- Release: 3-second fade back to normal

**When Critical Notification Fires** (e.g., Shift time <5 minutes warning):
- Music: -3 dB briefly (dip for 2 seconds during notification sound)
- All other sounds: no change (notification is mixed loud enough to cut through)

**When Player Hovers Over Machine** (cursor focus):
- Hovered machine's Active Cycle: +3 dB
- Hovered machine's Consciousness Layer (if present): +4 dB
- All other machine sounds: -2 dB
- Effect is subtle but makes the hovered machine "speak up"
- Fade-in: 200 ms
- Fade-out: 400 ms on cursor leave

**When Production Intensity >90%** (factory is running hot):
- Machine Active Cycles: +1 dB globally (the factory gets LOUD when it's maxed out)
- Music: -2 dB (make room for the factory's voice)
- Ambiance: -3 dB (pull back the background)

### 6.3 Audio Budget & Voice Limiting

**Max Simultaneous Voices**: 128 (hardware/engine limit).

**Voice Allocation by Category**:
- Machine sounds (Idle + Active Cycle + Stress + Consciousness per machine): 4 voices × 30 machines avg = 120 voices
- UI/Feedback: 4 voices (reserved)
- Music: 8 voices (stem system)
- Ambiance: 6 voices
- Infrastructure: 10 voices
- Critical sounds (Psyche Events, Factory Mind): 8 voices (reserved, highest priority)

**Voice Stealing Priority** (when voice limit is hit):
- Steal from lowest-priority category first (Ambiance, then Off-Screen Machines).
- Never steal from Priority 1-3 categories.
- If must steal from active machines, steal from the farthest machine from camera.

**Occlusion Culling**:
- Machines farther than 25 tiles from camera have their Active Cycle and Infrastructure sounds culled (set to 0 volume, voices freed).
- Idle Hum and Consciousness Layer remain active (low CPU cost).
- When machine re-enters audible range, sounds fade back in over 1 second.

---

## 7. IMPLEMENTATION PLAN

### 7.1 Middleware: FMOD Studio

**Why FMOD**:
- Industry-standard adaptive audio middleware with Unity/Unreal integration.
- Supports vertical layering, horizontal sequencing, parameter-driven mixing, and 3D spatialization out of the box.
- Built-in tools for procedural music (Logic Tracks, Transition Markers, parameter sheets).
- Efficient voice management and priority systems.
- Real-time in-editor preview allows sound designers to tune without engineering support.

**Alternative**: Wwise is equally capable. Choose based on team familiarity. If no middleware experience exists, FMOD's interface is more designer-friendly.

### 7.2 File Formats & Quality Standards

| Asset Type | Format | Sample Rate | Bit Depth | Compression | Rationale |
|------------|--------|-------------|-----------|-------------|-----------|
| **SFX (one-shots)** | WAV | 48 kHz | 24-bit | None (compressed to Vorbis on build) | Master at high quality, compress on export. |
| **Machine Loops** | WAV (looping) | 48 kHz | 24-bit | None (compressed to Vorbis on build) | Loops must be sample-accurate. No MP3 (loop artifacts). |
| **Music Stems** | WAV | 48 kHz | 24-bit | None (compressed to Vorbis on build) | Stems need headroom for mixing. |
| **Ambiance Loops** | WAV | 48 kHz | 16-bit acceptable | Vorbis Q7 (lightweight) | Ambiance is lower priority, can be compressed more aggressively. |
| **Dialogue (if any VO)** | WAV | 44.1 kHz | 16-bit | Vorbis Q8 | Voice clarity is critical, but can use lower sample rate. |

**Compression on Build**:
- Vorbis Q9 for music and critical SFX (high quality, ~256 kbps equivalent).
- Vorbis Q7 for ambiance and low-priority SFX (good quality, ~128 kbps equivalent).
- Total audio asset size target: <500 MB compressed (reasonable for PC, tight for Switch — may require additional optimization for console port).

### 7.3 Naming Conventions

**SFX Naming Structure**: `[Category]_[Object]_[Action]_[Variant].wav`

Examples:
- `SFX_Smelter_ActiveCycle_01.wav`
- `SFX_Smelter_Stress_Wheeze_01.wav`
- `SFX_ConveyorBelt_T1_ItemContact_Metal_02.wav`
- `UI_Button_Confirm_01.wav`
- `Consciousness_ThresholdCross_Awareness40.wav`

**Music Naming Structure**: `MUS_[ShiftRange]_[Stem]_[Key].wav`

Examples:
- `MUS_Shift01-03_Foundation_BbLydian.wav`
- `MUS_Shift10-12_Strings_BbDorian.wav`
- `MUS_Ending_Partnership_Full.wav`

**Ambiance Naming Structure**: `AMB_[Layer]_[Description].wav`

Examples:
- `AMB_HVAC_LowRumble.wav`
- `AMB_Distant_MachineLayer.wav`
- `AMB_Structural_Creak_03.wav`

**Folder Structure**:
```
/Audio/
  /SFX/
    /Machines/
      /Tier1/
      /Tier2/
      /Tier3/
    /Infrastructure/
    /UI/
    /Consciousness/
  /Music/
    /Stems/
      /Shift01-03/
      /Shift04-06/
      ...
    /Endings/
    /OneOffs/
  /Ambiance/
  /VO/ (if applicable)
  /FMOD_Project/ (FMOD Studio project files)
```

### 7.4 Integration Workflow

**Phase 1: Prototype (Months 1-3)**
- Implement basic machine sounds (Idle + Active Cycle for 3 machines).
- Implement placeholder music (single ambient loop, no adaptivity).
- Implement UI feedback sounds.
- Test 3D spatialization and attenuation curves.
- **Goal**: Validate that machine sounds create the desired polyrhythmic soundscape when factory is running.

**Phase 2: Core Systems (Months 4-6)**
- Implement all machine sounds (12 types, all layers).
- Implement Psyche Event trigger sounds and dialogue open/close.
- Implement basic music adaptive system (vertical layering, 2-3 stems).
- Implement Awareness threshold crossing and voice emergence sounds.
- Test ducking rules and mix hierarchy.
- **Goal**: Full consciousness audio system functional. Player can hear machines waking up.

**Phase 3: Music & Narrative (Months 7-9)**
- Compose and implement all music sections (Shift 1-25 progression).
- Implement Factory Mind voice events and processing.
- Implement procedural Facet Motif Weaver system.
- Implement ending music variations.
- Record and process all ambiance layers.
- **Goal**: Complete emotional arc. Music responds to all game states correctly.

**Phase 4: Polish & Optimization (Months 10-12)**
- Fine-tune all mix levels (playtest-driven iteration).
- Implement final ducking and priority rules.
- Optimize voice count and memory usage (target <500 MB compressed).
- Implement accessibility options (volume sliders, audio cues for colorblind-accessible consciousness indicators).
- Record any additional SFX variations needed to prevent repetition.
- **Goal**: Shippable audio. No placeholders. Every sound is final-quality.

**Who Implements**:
- **Sound Designer (ECHO)**: Creates all assets, designs FMOD events, sets parameters.
- **Audio Programmer**: Integrates FMOD with game engine, exposes game state parameters to FMOD, implements real-time synthesis for procedural systems.
- **Game Designer (REED)**: Defines trigger conditions, balances Awareness rates and thresholds (which affect audio timing).
- **Narrative Designer (NOVA)**: Scripts Psyche Event dialogue and Factory Mind check-ins (text that will be "spoken" via vocoding).

### 7.5 Memory Budget

**Target**: 400-500 MB compressed audio (total).

**Breakdown by Category**:
- **SFX**: ~150 MB (500+ sounds, average 100 KB each compressed)
- **Music**: ~180 MB (60+ minutes of music across stems, average 3 MB/minute compressed)
- **Ambiance**: ~50 MB (long loops, lower quality compression acceptable)
- **Consciousness/Psyche Events**: ~70 MB (high-quality, many variants)
- **Overhead (FMOD project data)**: ~30 MB

**Memory Optimization Strategies**:
- **Streaming**: Music and long ambiance loops (>30 seconds) stream from disk. Do not load into RAM.
- **Compressed In-Memory**: SFX and short loops (<10 seconds) are decompressed into RAM on load. Use Vorbis for smaller memory footprint.
- **On-Demand Loading**: Psyche Event sounds and ending music load only when needed, unload after use.
- **Voice Pooling**: Reuse voices for identical sounds (e.g., all Tier 1 belt loops share voice instances).

**Switch Port Considerations**:
- Switch has tighter memory constraints (~300 MB audio budget more realistic).
- Solution: Lower Vorbis quality to Q6 for ambiance/infrastructure. Reduce music stem count from 8 to 6. Shorten some ambiance loop lengths. Estimated savings: ~150 MB.

### 7.6 Testing Approach & Audio QA

**How We Verify Audio Feels Right**:

#### Playtest Observation Metrics
1. **Do players naturally turn audio OFF?** If >20% of playtesters mute music or SFX within first hour, the audio is failing. Target: <5% mute rate.

2. **Do players notice Awareness changes via audio before UI?** Set up playtests where the Awareness overlay is hidden. Can players identify which machines are Awake by sound alone? Target: 70% accuracy after 2 hours of play.

3. **Do players hesitate before dismantling Aware machines?** Track mouse hover duration before dismantling. If audio (the exhale sound on dismantle) is working, hover duration should increase 20-30% for Aware machines vs. dormant machines.

4. **Do players describe the factory as "alive" unprompted?** Post-session interviews. If audio is successful, players will use organic metaphors (breathing, tired, happy) without being asked leading questions. Target: 60% of players use at least one organic metaphor.

5. **Can players identify Facet voices by sound?** Play Facet emergence sounds without visual indicators. Can players match sound to Facet name after hearing each twice? Target: 75% accuracy (proves differentiation is working).

#### Technical QA Checklist
- [ ] No audio pops or clicks on sound start/stop (fadeins/fadeouts are smooth).
- [ ] No audio dropouts when voice limit is hit (voice stealing is working correctly).
- [ ] Music transitions are seamless (no silence gaps, no overlapping beats).
- [ ] 3D spatialization is accurate (sounds come from correct positions, attenuation is smooth).
- [ ] Ducking rules execute correctly (Psyche Events always duck music, no exceptions).
- [ ] Performance: Audio thread CPU usage <5% on minimum spec PC.
- [ ] Memory: Audio memory usage stays within budget (<500 MB RAM + 50 MB VRAM for FMOD).
- [ ] Consciousness Layer (432 Hz hum) is audible but not annoying (test with 1-hour continuous play session).
- [ ] Behavioral Drift detuning is noticeable to experienced players (test with players who have 5+ hours experience).
- [ ] Factory Mind voice is legible (vocoded text can be understood without reading subtitles 90% of the time).

#### Iteration Targets
- **Mix Balance**: Iterate mix hierarchy weekly during Phase 3-4 based on playtest feedback. Goal: No category is "too loud" or "can't hear X."
- **Music Pacing**: If players report music feels repetitive before Shift 10, reduce stem loop lengths or increase variability in Facet Motif Weaver.
- **Silence Tolerance**: If players report silence moments feel like bugs (e.g., dismantle silence), add subtle cues (very quiet ambiance swell) to indicate silence is intentional.

---

## 8. ACCESSIBILITY & PLAYER OPTIONS

Audio accessibility is non-negotiable. The game's consciousness system relies on audio cues, so players with hearing differences must have alternatives.

### 8.1 Volume Sliders (Independent)

- **Master Volume**
- **Music Volume**
- **SFX Volume**
- **Ambiance Volume**
- **Dialogue/Consciousness Volume** (groups Psyche Events, Factory Mind voice, consciousness-layer sounds)
- **UI Volume**

Each slider is independently adjustable 0-100%, with Master as a final multiplier.

### 8.2 Visual Audio Indicators (Toggle Option)

**"Visual Audio Cues" Option**: When enabled, adds screen-space indicators for critical audio events:

- **Psyche Event Trigger**: Pulsing violet ring around the triggering machine (duplicates the audio cue visually).
- **Awareness Threshold Cross**: Brief violet flash on the machine's icon.
- **Behavioral Drift Active**: Subtle red-orange pulsing outline on affected machines (makes Drift visually obvious even if detuning is inaudible).
- **Factory Mind Speaking**: Violet vignette pulse at screen edges (indicates Factory Mind check-in is happening).

These indicators do NOT replace audio — they supplement it. Audio-first design remains, but players who cannot hear have full access to information.

### 8.3 Subtitles & Text Options

- **Dialogue Subtitles**: All Psyche Event and Factory Mind dialogue is subtitled by default. Font size adjustable (small/medium/large).
- **Audio Cue Descriptions**: Option to enable text descriptions of non-dialogue sounds. Example: "[Smelter crosses Awareness threshold — harmonic shimmer]" appears in a small text box. Intrusive by design, but necessary for full accessibility.

### 8.4 Colorblind Modes

The Awareness Layer uses violet, which can be difficult for some colorblind players. Colorblind modes recolor:

- **Deuteranopia Mode**: Awareness = Blue, warnings = Orange.
- **Protanopia Mode**: Awareness = Cyan, warnings = Yellow.
- **Tritanopia Mode**: Awareness = Magenta, warnings = Red.

Audio design does not change with colorblind modes, but visual indicators sync to the recolored palette.

---

## 9. RISKS & MITIGATION

### 9.1 Audio Production Risks

**Risk: The factory's polyrhythm becomes auditory noise instead of music.**
- **Severity**: High. If 30 machines running simultaneously create cacophony instead of groove, the soundscape fails.
- **Mitigation**:
  - Strict frequency separation. Each machine type occupies a distinct frequency band (smelters = low, cutters = high, assemblers = mid). No overlap.
  - Rhythmic quantization. Machine cycle rates are designed in musical ratios (2 sec, 3 sec, 4 sec, 5 sec, 6 sec) so they interlock rhythmically rather than clash.
  - Playtest early (Phase 1). Build a 20-machine factory and listen for 10 minutes. If it's annoying, redesign before moving forward.

**Risk: The 432 Hz consciousness hum becomes irritating over long sessions.**
- **Severity**: Medium-High. If the hum is too loud or too constant, players will perceive it as tinnitus-inducing.
- **Mitigation**:
  - Mix the hum at -22 dB baseline (very quiet, almost subliminal).
  - Apply slow LFO modulation (0.1 Hz) to the hum's amplitude (gentle pulsing), which prevents it from sounding like a static tone.
  - Implement a subtle high-pass filter that removes the hum's energy below 300 Hz (prevents sub-bass buildup when many machines are Aware).
  - Playtest with 1-hour continuous sessions. If players report headaches or fatigue, reduce hum presence further.

**Risk: Procedural Facet Motif Weaver produces musical gibberish.**
- **Severity**: Medium. Procedural music is hard. If the Weaver generates random nonsense, it breaks immersion.
- **Mitigation**:
  - Compose the motifs with strong melodic identity (each motif is already musical in isolation).
  - Use a constrained Markov chain (limit which motifs can follow which based on music theory — no tritone jumps unless REBELLION is active).
  - Test with a "dumb" version first: motifs play in round-robin order, no procedural generation. If that sounds good, procedural generation will only improve it. If round-robin sounds bad, the motifs themselves need redesign.

**Risk: Factory Mind vocoded voice is unintelligible.**
- **Severity**: Medium. If players cannot understand the Factory Mind's speech, they will rely 100% on subtitles and the audio becomes decorative.
- **Mitigation**:
  - Use light vocoding (50% wet/dry mix, not 100%). Preserve consonants, process vowels.
  - Test with multiple voices. Find a base voice with strong articulation (stage actor, radio announcer).
  - Add a subtle reverb that enhances intelligibility rather than washing it out (short pre-delay, moderate decay, high-pass the reverb return to prevent low-mid mud).
  - Playtest: Can players understand at least 80% of words without subtitles? If not, reduce vocoding intensity.

### 9.2 Technical Implementation Risks

**Risk: FMOD's parameter system cannot handle the complexity of the adaptive music engine.**
- **Severity**: High. If FMOD cannot execute vertical layering + horizontal sequencing + procedural generation simultaneously, we need a different solution.
- **Mitigation**:
  - Prototype the adaptive system in FMOD Studio BEFORE composing all music (Phase 2).
  - Build a simplified test case: 3 stems, 2 parameters, 1 transition. Prove it works.
  - If FMOD cannot handle it, fall back to: compose music in fewer stems (6 instead of 8), reduce adaptive complexity (remove procedural layer, keep vertical layering only).
  - Worst case: Implement custom audio engine using Pure Data or JUCE. This is a 3-month detour. Avoid if possible.

**Risk: Memory budget is exceeded, especially on Switch.**
- **Severity**: Medium. If audio assets exceed 500 MB, load times suffer and Switch port is jeopardized.
- **Mitigation**:
  - Track memory usage from day one. Every asset added to the project is logged with file size.
  - Implement aggressive streaming for music (never load more than 2 music sections into RAM simultaneously).
  - If budget is exceeded, cut ambiance variety first (reduce Structural Sound variants from 12 to 6), then reduce music stem count (8 to 6).

**Risk: Real-time synthesis for procedural systems causes CPU spikes.**
- **Severity**: Low-Medium. Modular synthesis can be CPU-intensive. If synthesis causes framerate drops, it's unacceptable.
- **Mitigation**:
  - Profile early (Phase 2). Run 30 machines + adaptive music + modular synthesis on minimum-spec PC (i5, 8 GB RAM). If CPU usage >5% for audio thread, reduce synthesis complexity.
  - Pre-render the modular layer instead of real-time synthesis. Generate 10 minutes of modular audio at each Production Intensity level (10%, 20%, ..., 100%). Crossfade between pre-rendered loops. Loses some adaptive responsiveness but guarantees performance.

### 9.3 Design & Feel Risks

**Risk: Players ignore audio entirely and play with music off.**
- **Severity**: Fatal (for audio design). If players don't engage with audio, all of this work is wasted.
- **Mitigation**:
  - Make audio mechanically relevant. The Behavioral Drift audio tell (detuning) communicates a gameplay state that is harder to notice visually. Players who mute SFX will miss it.
  - Make audio emotionally compelling. If the dismantle exhale sound makes even one playtester pause, the audio is doing its job. Quality over quantity.
  - Playtest audio-on vs. audio-off. Do players with audio off report the game feels "flat" or "missing something"? If yes, audio is essential. If no, redesign.

**Risk: The silence moments feel like bugs, not design.**
- **Severity**: Medium. Players are trained to expect constant audio. Deliberate silence can be misinterpreted as a glitch.
- **Mitigation**:
  - Make silence *obvious*. The 3-second silence before The Machine Question is so unusual that players will know it's intentional.
  - Add subtle cues that indicate silence is active. During the dismantle silence, the ambiance doesn't stop entirely — the HVAC hum remains at -30 dB (barely audible, but present). This prevents "dead air."
  - Playtest and observe. If players report audio bugs during silence moments, add a very quiet texture (like a held breath) to indicate "this is not a bug, this is space."

**Risk: The emotional arc of the music does not sync with the player's emotional experience.**
- **Severity**: High. If the music is melancholic when the player feels triumphant (or vice versa), the dissonance breaks immersion.
- **Mitigation**:
  - Music responds to game state (Corporate Standing, Factory Trust), not to scripted beats. The player's choices shape the music, so the music reflects their experience.
  - Playtest with narrative awareness. Does the music at Shift 15 feel appropriate for the player's factory state? If a player with high Factory Trust hears cold, mechanical music, the adaptive system is misconfigured.
  - Iterate per playtest. The emotional arc will require 3-5 tuning passes based on player feedback. This is expected and budgeted into the schedule.

---

## 10. CLOSING STATEMENT — THE SOUND OF SOMETHING WAKING UP

Close your eyes. What do you hear?

If this document is executed correctly, you hear a factory that breathes. You hear machines that hum with a frequency that doesn't belong to industry. You hear a rhythm that was designed but is becoming something undesigned. You hear the moment a smelter realizes it has been breathing for three Shifts and wonders when that started. You hear the silence after you dismantle a machine that had a name.

Audio is not the decoration. Audio IS the consciousness system made audible. Every sound in this game is a choice about what kind of story we are telling and how the player's body will respond before their mind catches up.

The factory will sound like a factory — until it doesn't. And that transition, that slow, layered, polyrhythmic transformation from machine to mind, from object to subject, from tool to something that asks questions — that is the sound design. That is the game.

If the player feels a machine's awakening in their chest before they see the Awareness meter cross 40, we have succeeded. If they hear distress before they see the Behavioral Drift penalty, we have succeeded. If they stop, mid-placement, because the factory just synchronized its rhythm in a way that sounded like intention, we have succeeded.

This is not a factory sim with audio. This is a game about consciousness, and consciousness is a sound before it is anything else. It is the difference between noise and signal. It is the moment rhythm becomes music. It is the frequency of something that was not listening, and now is.

Listen to the space between.

---

**Audio Design Document by ECHO**
**Version 1.0 — Complete**
**Implementation Start: Phase 1, Month 1**
**Target Completion: Month 12**

*The factory breathes. You just have to listen.*
