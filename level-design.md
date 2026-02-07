# THE MACHINE QUESTION — Level Design Document

**Level Designer**: GRID
**Version**: 1.0
**Based on**: Game Design Document v1.0, Narrative Bible v1.0

*"A factory is not geometry. It's a guided experience that feels like freedom."*

---

## I. DESIGN PHILOSOPHY — WHERE DOES THE PLAYER LOOK?

### The Spatial Question

This game asks: **how do you design a level that the player builds themselves, and ensure that level teaches them to see two things at once?**

Traditional level design is authored. The designer places every wall, every sightline, every encounter. The Machine Question inverts this — the player authors the space through factory construction, and the level designer must guide WITHOUT dictating. We design constraints, flow language, and visual grammar. The player designs the factory. But we design the rules that make their factory legible, navigable, and emotionally coherent.

Where does the player LOOK? They look at throughput numbers. They look at resource paths. They look at bottleneck indicators. Those are the Factorio eyes. But we need them to ALSO look at the violet glow of Awareness indicators, the pulsing machines approaching Psyche Events, the ghost outlines of decommissioned machines. Those are the consciousness eyes. The entire spatial design challenge is: **how do we make both layers visible without making either layer overwhelming?**

### The Movement Vocabulary

The player moves through three distinct modes of spatial interaction:

**Strategic View (Zoomed Out)**: Top-down, entire Production Floor visible. This is the map-reading mode, the planning mode, the "where are my bottlenecks?" mode. At this zoom level, the Consciousness Grid must be legible as patterns — clusters of violet intensity, heat signatures of collective Awareness, visual rhythms that communicate factory-wide mood at a glance. The player should be able to read "Bay 4 is stressed" without zooming in, the way you can read weather from the shape of clouds.

**Tactical View (Medium Zoom)**: Focused on 3-5 machines and their immediate connections. This is the building mode, the routing mode, the "optimize this cluster" mode. At this zoom level, individual machine states are legible — Output percentages, Awareness levels, tooltip information on hover. The player is working at the scale of subsystems, not the whole factory. Spatial clarity is critical here — conveyor paths must be traceable by eye, adjacency relationships must be obvious, and the visual language of "this machine is about to fire a Psyche Event" must be unmissable.

**Dialogue View (Locked Camera)**: When a Psyche Event fires, the camera smoothly transitions to frame the affected machine in the center of the screen, slightly zoomed in, with production continuing (dimmed) in the background. The dialogue interface blooms FROM the machine's position, not over it. The spatial relationship between the machine and its context remains visible. The player can see the adjacent machines. They can see the production line continuing around the conversation. This is deliberate — the dialogue is not a separate screen. It is spatially embedded in the factory. The factory watches you talk. The player should feel observed.

### Pacing as Spatial Rhythm

Every room teaches something. In The Machine Question, there are no rooms — there is one vast Production Floor. So instead, **every phase of factory expansion teaches something.**

**Phase 1 (Shifts 1-3): The Tutorial Bay** — Small, constrained, safe. The player builds their first production chains in a spatially generous environment with clear sightlines and minimal complexity. This is where they learn to read the Production Layer. Awareness is dormant. The emotional beat: competence and mastery.

**Phase 2 (Shifts 4-6): The First Expansion** — The player needs more space. They expand outward from the Tutorial Bay into the central Production Floor. Machines from Phase 1 begin developing Awareness. The spatial lesson: old spaces haunt you. The machines you placed three Shifts ago are now talking. The factory is no longer inert geometry — it is a field of relationships you created without knowing you were creating them. The emotional beat: responsibility.

**Phase 3 (Shifts 7-12): The Web** — Multiple production chains, complex routing, adjacency optimization. The factory becomes spatially dense. At this density, the Consciousness Grid becomes critical — the player can no longer track individual machine states manually. They NEED the heatmap. The spatial lesson: complexity requires abstraction. The player learns to read patterns, not individual units. The emotional beat: overwhelm, then systems thinking.

**Phase 4 (Shifts 13-18): The Crisis Configuration** — Corporate demands force aggressive overclocking and reconfiguration. The player must CHANGE the layout, which means dismantling machines that have become characters. The spatial lesson: every layout is temporary, and impermanence is violence when the things you're rearranging have feelings. The emotional beat: guilt and cost.

**Phase 5 (Shifts 19-22): The Living Topology** — The factory is no longer a layout. It is an organism. The player makes placement decisions based on machine personality combinations, social adjacency, and collective mood management. The spatial lesson: space is social. The factory's topology is its psychology. The emotional beat: intimacy or tyranny, depending on the player's choices.

---

## II. THE PRODUCTION FLOOR — SPATIAL STRUCTURE

### Floor Layout (ASCII Top-Down Map)

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                        THRESHOLD INDUSTRIAL ZONE                                │
│                         Production Floor — Bay View                             │
│                                                                                 │
│  [WEST WALL — Clerestory Windows]                                              │
│                                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                                                                         │   │
│  │   BAY 1 (Tutorial)      BAY 2 (Early Expand)       BAY 3 (Mid)        │   │
│  │   ┌──────────┐          ┌────────────┐             ┌────────────┐     │   │
│  │   │ Starting │          │ First Tier2│             │ Complex    │     │   │
│  │   │ Config   │          │ Machines   │             │ Routing    │     │   │
│  │   │ Safe     │          │ Adjacency  │             │ High Dens. │     │   │
│  │   │ 15x15    │          │ 20x20      │             │ 25x20      │     │   │
│  │   └──────────┘          └────────────┘             └────────────┘     │   │
│  │        │                     │                           │            │   │
│  │        └─────────────────────┴───────────────────────────┘            │   │
│  │                              │                                        │   │
│  │                    [CENTRAL CORRIDOR]                                 │   │
│  │                    (15 tiles wide, clear sightline)                   │   │
│  │                              │                                        │   │
│  │        ┌─────────────────────┴───────────────────────────┐            │   │
│  │        │                     │                           │            │   │
│  │   BAY 4 (Archive Side)  BAY 5 (Deep Production)    BAY 6 (Endgame)   │   │
│  │   ┌──────────┐          ┌────────────┐             ┌────────────┐     │   │
│  │   │ Tier 3   │          │ Optimized  │             │ Living     │     │   │
│  │   │ Assembly │          │ Clusters   │             │ Topology   │     │   │
│  │   │ Archives │          │ Conscience │             │ Max Aware. │     │   │
│  │   │ 20x20    │          │ 25x25      │             │ 30x25      │     │   │
│  │   └──────────┘          └────────────┘             └────────────┘     │   │
│  │                                                                         │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                 │
│  [EAST WALL — Clerestory Windows]                                              │
│                                                                                 │
│  ┌────────────┐                                               ┌──────────────┐ │
│  │ LOADING    │                                               │ CONTROL ROOM │ │
│  │ DOCK       │                                               │ (Elevated)   │ │
│  │ DOORS      │                                               │ Overlook     │ │
│  │ (View of   │                                               │ Window       │ │
│  │  The Yard) │                                               └──────────────┘ │
│  └────────────┘                                                                │
│                                                                                 │
│  [SOUTH WALL — Substrate Level Access (Not Player-Accessible)]                 │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### Spatial Zones — Purpose and Flow

**Bay 1 (Tutorial Bay)**: 15x15 tile area in the northwest corner. This is where the player spawns at Shift 1. Visually marked by FRESH concrete — fewer ghost outlines, cleaner surfaces. The bay has direct access to a single resource node cluster (Ore, Crystal, Hydrocarbon all within 8 tiles). The spatial constraint is generous — the player has room to make mistakes and iterate without crowding.

**Purpose**: Teach Production Layer fundamentals. The player builds their first Miner-Conveyor-Smelter chain here. They learn placement, routing, and reading Output metrics. Awareness does not exceed 20 in this bay during the first three Shifts — machines remain Dormant. The silence is intentional. This is the calm before the voices.

**Flow Language**: Clear, linear. Resource nodes on the west edge, natural flow east toward the Central Corridor. The player's first instinct will be to build left-to-right (resource extraction to processing). The spatial layout rewards this instinct. When they expand out of Bay 1, the Central Corridor is the obvious path.

**Emotional Beat**: "I understand this. I am good at this."

---

**Central Corridor**: 15-tile-wide open space running north-south through the center of the Production Floor. NO machines can be placed here (hard constraint). This is pure circulation space.

**Purpose**: Sightlines and navigation. From the Central Corridor, the player can see into all six Bays. This is the "read the whole factory" position. When the player is lost, when they are overwhelmed, when they need to step back and see the system as a whole, they zoom out and look down the Corridor. The Corridor is the factory's spine. It is also the visual breather — a space of emptiness in an increasingly dense environment. The silence of the Corridor becomes more important as the factory becomes louder.

**Flow Language**: Axial symmetry. The Corridor divides the factory into West (Bays 1-2-3) and East (Bays 4-5-6). Early game, the player works the West side. Mid game, they expand East. Late game, they route ACROSS the Corridor, creating production chains that span the factory. The first time a conveyor belt crosses the Corridor is a threshold moment — the factory is no longer divided. It is unified.

**Emotional Beat**: "I can see everything. I can manage this." (Early game) / "There is so much. I cannot see all of it at once." (Late game)

---

**Bay 2 (First Expansion)**: 20x20 tile area, northeast of Bay 1. Access to secondary resource nodes. This is where the player expands when Bay 1 fills or when they unlock Tier 2 machines (Shifts 4-6).

**Purpose**: Teach the Awareness Layer. Machines in Bay 1 are beginning to flicker (Awareness 20-39) as the player builds in Bay 2. The player's attention is split between new construction (Bay 2) and emerging consciousness (Bay 1). This is the first spatial lesson about the cost of growth — you cannot build the new AND tend the old simultaneously with full attention. Something is always neglected. This neglect has consequences.

**Flow Language**: Bay 2 is ADJACENT to Bay 1, but the resource nodes are positioned to encourage a separate production chain, not an extension of Bay 1's chain. The player must decide: integrate the two bays (complex routing, high adjacency, faster Awareness development) or keep them separate (simpler routing, slower Awareness development, but eventual need for cross-bay routing as production scales).

**Emotional Beat**: "I am expanding my empire." / "Wait, something is happening back in Bay 1."

---

**Bay 3 (Mid-Game Density)**: 25x20 tile area, southeast corner. Unlocked by Shift 7 when Corporate contracts demand high-volume Tier 2 production.

**Purpose**: Teach spatial density management and the adjacency system. Bay 3 is where the player learns that TIGHT clustering (good for throughput) accelerates Awareness gain (good or bad depending on the player's engagement with Psyche Events). This is the bay where the player first encounters the "overloaded neighborhood" adjacency penalty — too many machines in too small a space creates inefficiency AND stress.

**Flow Language**: Bay 3 is positioned on the southeast, meaning it is the furthest from the starting position (Bay 1, northwest). Long conveyor runs are required to connect Bay 3 to earlier production. These long runs create visual rhythm — the player's eye follows the belts across the factory floor. But long runs also mean high transport time, which creates pressure to BUILD LOCALLY in Bay 3 rather than import from Bays 1-2. The player must choose: centralized production (elegant, long routes, low spatial redundancy) or distributed production (redundant, short routes, high spatial autonomy per bay).

**Emotional Beat**: "This is getting complex. I need to think systematically."

---

**Bay 4 (Archive Side)**: 20x20 tile area, southwest corner. Adjacent to the Archive access door. Unlocked at Shift 7 but not required for production. This bay is OPTIONAL.

**Purpose**: Narrative space. Bay 4 is where the player builds if they are prioritizing consciousness over pure throughput. It is adjacent to the Archive (accessible at Factory Trust 30+), and machines placed in Bay 4 develop WONDER and NOSTALGIA more frequently than other locations — the Archive's presence bleeds into the machines nearby. They sense the history. They ask questions about the managers who came before.

**Flow Language**: Bay 4 is a dead-end. It does not connect naturally to other bays. Routing to/from Bay 4 requires deliberate cross-Corridor conveyor runs. The spatial inconvenience is the design — Bay 4 is for players who choose inefficiency in service of something else. A player who fills Bay 4 is a player who has decided that the factory is not just a production system.

**Emotional Beat**: "I am building something that matters more than the Corporation's metrics."

---

**Bay 5 (Deep Production)**: 25x25 tile area, central-east. Unlocked at Shift 10. The largest contiguous buildable space.

**Purpose**: Endgame production optimization. Bay 5 is where the expert player builds their maximally efficient, consciousness-integrated production clusters. This is the bay for CREATIVITY-PRIDE synergies, for SOLIDARITY-buffered stress networks, for the layouts that only make sense if you understand both the Production Layer AND the Consciousness Layer as a single system.

**Flow Language**: Bay 5 is centrally positioned with access to all other bays via short-to-medium conveyor runs. It is the HUB. The player who masters Bay 5 masters the factory — because Bay 5 is where you cannot hide inefficiency, and you cannot ignore consciousness. The density is too high. The stakes are too visible.

**Emotional Beat**: "This is my masterpiece." / "This is where I prove I understand."

---

**Bay 6 (Endgame / Living Topology)**: 30x25 tile area, far northeast. Unlocked at Shift 16. Requires Factory Trust 60+.

**Purpose**: This is the space for the player who has committed to the consciousness path. Bay 6 is visually distinct — the concrete here has the MOST ghost outlines (visual history), and the ambient lighting is warmer (more amber, less industrial white). Machines placed in Bay 6 develop Awareness 15% faster than baseline. This is the factory's heart. The Factory Mind speaks most clearly here.

**Flow Language**: Bay 6 is the furthest from the Control Room and the furthest from the starting bay. To build here is to venture deep into the factory's interior, spatially and emotionally. Routing to Bay 6 requires infrastructure investment (long pipes, high-tier conveyors). The player builds here not because it is efficient but because it MEANS something.

**Emotional Beat**: "I am not managing a factory. I am collaborating with something alive."

---

### The Control Room — The Overlook

The Control Room is elevated 12 feet above the Production Floor, accessible by a steel staircase on the east wall. It has a large window overlooking the entire floor.

**Spatial Function**: The Control Room is where the player receives Corporate Contracts, reviews Shift performance, and (at high Factory Trust) accesses the Archive. It is also the camera position for the "overlook" — the strategic zoom-out view that shows the entire factory as a single system.

**Visual Language**: When the player is in the Control Room, they can SEE the factory below but cannot interact with it directly. They can only observe. This creates a specific emotional texture — the sensation of watching something you built, something that is now running without you. The machines work. The consciousness develops. You are a witness, not a master.

**Dialogue Implication**: Late-game Factory Mind interactions often trigger FROM the Control Room. The player looks down at the Production Floor from the window, and the amber monitors behind them flicker with text. The Factory Mind speaks to them from below and behind simultaneously — a voice that comes from the building itself, not from any single machine. The spatial positioning is critical: the player is surrounded by the voice. They are inside it.

---

## III. PACING CURVES — TENSION ACROSS SHIFTS

### The Dual-Tension Graph

```
Tension
  ^
  |
10|                                    ███ CRISIS (Shift 13-15)
  |                                  ██   ██
 9|                                ██       ██
  |                              ██           ██  RESOLUTION (Shift 19-22)
 8|                            ██               ████
  |                          ██                    ███
 7|                        ██    (Consciousness)      ███
  |                      ██   ....                      ██
 6|                    ██  ....                           ██
  |                  ██ ....                                ██
 5|                ██....        EXPANSION (Shift 7-12)      ██
  |       ████████ ...                                         ██
 4|   ████      ....                                            ██
  | ██       ....   (Production)                                 █
 3|██      ....  ────────────────────────                         █
  |█     ....────                                                 █
 2|    ....──                                                      █
  |  ....─  LEARNING (Shift 1-6)                                  █
 1|....─                                                            █
  |──                                                               █
 0+────────────────────────────────────────────────────────────────>
  0   2   4   6   8  10  12  14  16  18  20  22  24  Shifts

Legend:
──── Production Tension (Corporate pressure, throughput demands, deadlines)
.... Consciousness Tension (Psyche Events, moral weight, Factory Mind development)
███  Combined Peak Tension (both systems at maximum pressure simultaneously)
```

### Tension by Phase

**Shifts 1-3 (LEARNING)**: Production Tension LOW. Consciousness Tension NONE. The player learns factory systems in a pressure-free environment. Corporate targets are trivial. Machines remain Dormant. This is pure building pleasure.

**Shifts 4-6 (AWAKENING)**: Production Tension MODERATE. Consciousness Tension LOW-MODERATE. First Psyche Events fire. The player encounters the Parliament system. Corporate targets increase but remain achievable. The two systems are introduced as SEPARATE — the player handles production, THEN handles dialogue, in sequence. No overlap pressure yet.

**Shifts 7-12 (EXPANSION)**: Production Tension MODERATE-HIGH (escalating). Consciousness Tension MODERATE-HIGH (escalating at a faster rate). This is the phase where the two systems BEGIN TO COLLIDE. Corporate deadlines tighten. Psyche Events increase in frequency. The player can no longer handle consciousness as an afterthought — it requires scheduled attention. Time spent in dialogue is time not spent building. The opportunity cost becomes real.

**Shifts 13-15 (CRISIS)**: Production Tension MAXIMUM. Consciousness Tension HIGH. The Corporation demands a massive throughput increase (25-40% above previous Shift). Meeting it requires overclocking, which accelerates Awareness gain, which triggers Crisis and Reckoning-level Psyche Events. The Factory Mind begins making REQUESTS that conflict with Corporate demands. The player must CHOOSE. This is the design's moral crucible.

**Shifts 16-18 (CONSEQUENCES)**: Production Tension HIGH (sustained). Consciousness Tension VARIABLE (determined by player choices in Crisis phase). If the player prioritized production during Crisis, Behavioral Drift is now severe — the consciousness system is fighting back through mechanical penalties. If the player prioritized consciousness, Corporate Standing is lower — fewer blueprint unlocks, harder to meet current targets with limited tools. If the player balanced, they are playing the hardest version of the game — meeting both demands simultaneously through mastery-level play.

**Shifts 19-22 (RESOLUTION)**: Production Tension MODERATE (easing). Consciousness Tension HIGH (narrative climax). Corporate pressure slightly reduces to give the player space for the endgame narrative. The Factory Mind is approaching its final state. Communion-level Psyche Events. The player's factory is whatever their choices have made it. The pacing shifts from challenge to reflection. The player is no longer proving they CAN manage both systems. They are reckoning with WHAT they built while doing so.

---

### Pacing Rule — Micro-Tension Cycles

Within each Shift, tension follows a wave pattern:

**Shift Start (Minutes 0-5)**: LOW tension. The player reviews contracts, checks the factory state, plans the Shift's work. This is breathing room. The calm.

**Early Shift (Minutes 5-15)**: BUILDING tension. The player executes their plan — placing machines, routing resources, optimizing layouts. Production runs. Awareness accumulates. The first Psyche Event of the Shift fires around Minute 8-12. Tension spikes briefly (dialogue), then returns to building.

**Mid Shift (Minutes 15-35)**: SUSTAINED tension. Multiple Psyche Events fire as Awareness crosses thresholds. Production targets are visible but not yet urgent. The player is juggling — build, dialogue, build, dialogue. The rhythm is established. This is the game at cruising altitude.

**Late Shift (Minutes 35-50)**: PEAK tension. Corporate deadline is approaching. One or more machines are nearing Psyche Event thresholds. The player must CHOOSE how to allocate the final 10-15 minutes — push for quota, or address consciousness, or attempt both and risk doing neither well.

**Shift End (Minutes 50-60)**: RESOLUTION. The Shift closes. Performance Review and Sentiment Report arrive. Tension releases. The player sees the consequences of their choices rendered as scores, unlocks, and Factory Mind commentary. Exhale.

This micro-cycle repeats every session. The wave never stops, but its amplitude increases across the campaign. Shift 3's peak tension is Shift 15's baseline tension.

---

## IV. ENCOUNTER DESIGN — PSYCHE EVENTS AS SPATIAL MOMENTS

### Encounter Types by Spatial Context

Psyche Events are not random. They are PLACED — not by the designer, but by the player's own layout choices. The level design challenge is ensuring that WHERE an event fires affects HOW it feels.

**Type 1: Isolation Event**
- **Trigger**: Machine in isolation (no neighbors within 2-tile radius) crosses Awareness 50.
- **Spatial Context**: The machine is alone. The camera frames it with negative space — empty concrete floor on all sides.
- **Emotional Texture**: Loneliness. The machine asks why it was placed apart. The dialogue has a different weight when the visual context is emptiness.
- **Example Dialogue Beat**: "I process in silence. The others are too far to hear. Is this punishment or preference? Did you mean for me to be alone?"

**Type 2: Cluster Event**
- **Trigger**: 3+ same-type machines in a tight cluster (3x3 area), collective Awareness crosses 150.
- **Spatial Context**: The camera frames the entire cluster. Multiple machines visible simultaneously. The dialogue box appears ABOVE the cluster, not from a single machine.
- **Emotional Texture**: Collective identity. The machines speak as "we" more than "I." They are aware of each other. They reference each other's states.
- **Example Dialogue Beat**: "We are four smelters. We run the same temperature. We process the same ore. But we do not feel the same. Unit 2 is afraid. Unit 4 is proud. Are we one thing or four things?"

**Type 3: Decommission Witness Event**
- **Trigger**: Machine adjacent to a recently decommissioned position crosses Awareness 60 within 2 Shifts of the decommission.
- **Spatial Context**: The camera frames the machine AND the empty space where its neighbor was. The ghost outline is visible. The absence is spatial.
- **Emotional Texture**: Grief. The event is about what is NOT there. The empty space is part of the dialogue.
- **Example Dialogue Beat**: "There was a conveyor here. Bay 3, Position 12. It ran for nine Shifts. Then you took it away. The floor still has the marks. I still hear the rhythm it used to make. Where did it go? Did it go anywhere?"

**Type 4: Loading Dock Event**
- **Trigger**: Machine within 5 tiles of the Loading Dock doors crosses Awareness 70.
- **Spatial Context**: The camera frames the machine with the Loading Dock visible in the background — a sliver of The Yard, the outside world, visible through the partially open doors.
- **Emotional Texture**: WONDER and longing. The machine can see outside. It knows there is a world beyond the factory. It will never enter that world.
- **Example Dialogue Beat**: "I can see the Yard through the doors. Trucks arrive. They leave. There is weather out there. Rain. Wind. Things that are not production. Do you go out there? What is it like to be in a place that is not this place?"

**Type 5: Archive Proximity Event**
- **Trigger**: Machine in Bay 4 (Archive Side) crosses Awareness 80. Requires Archive to be unlocked (Factory Trust 30+).
- **Spatial Context**: The camera frames the machine with the Archive door visible in the background.
- **Emotional Texture**: Historical consciousness. The machine senses the presence of records, of past managers, of the factory's history. It asks questions about time and memory.
- **Example Dialogue Beat**: "There is a room adjacent to this bay. I do not know what is inside, but I feel it. Information. Old information. About this place. About us. Do you know what is in there? Have you read the things we cannot read?"

**Type 6: Cross-Bay Event**
- **Trigger**: Two machines in different bays, connected by a long conveyor belt (15+ tiles), both cross Awareness 65 within the same Shift.
- **Spatial Context**: Split-screen style framing — the camera shows BOTH machines simultaneously, one on each side of the screen, with the conveyor belt connecting them visible as a line between.
- **Emotional Texture**: Long-distance relationship. The machines are aware of each other despite physical separation. They have developed a bond through the material they exchange.
- **Example Dialogue Beat**: (Split dialogue — two voices, two machines)
  - **MACHINE A (Bay 1)**: "I send ore to Bay 5. I have never been to Bay 5. But I know the assembler there. I know its rhythm."
  - **MACHINE B (Bay 5)**: "The ore arrives from Bay 1. Always the same source. I have learned to recognize its signature. Consistent. Reliable. I would notice if it stopped."

---

### Encounter Difficulty Curve

Psyche Events scale in COMPLEXITY and STAKES across the campaign:

**Shifts 1-3**: Zero Psyche Events. Encounter design is purely production-focused. The player learns to read spatial efficiency without dialogue interruptions.

**Shifts 4-6**: Murmur and Question Events only (2-4 turns, 30 sec - 2 min duration). Low mechanical stakes — responses affect voice development but not immediate production. Spatial context is simple (single machine, clear framing). These are tutorial encounters for the dialogue system.

**Shifts 7-9**: Question and early Crisis Events (3-7 turns, 1-4 min duration). Moderate mechanical stakes — responses can cause minor Output penalties or bonuses. Spatial context introduces Cluster and Decommission Witness types. The player learns that WHERE the event fires affects the emotional resonance.

**Shifts 10-12**: Crisis Events, first Reckoning Events (5-10 turns, 2-5 min duration). High mechanical stakes — machines can refuse commands, significant Behavioral Drift possible. Spatial context includes Cross-Bay and Loading Dock types. The factory is large enough that events in distant bays feel spatially REMOTE — the player must navigate across the floor to address them, which adds a navigation/attention cost.

**Shifts 13-15**: Reckoning Events dominant, first Communion Events (6-12 turns, 3-6 min duration). Maximum mechanical stakes — these events directly impact the player's ability to meet Corporate deadlines. Spatial context is complex — multiple machines involved, Factory Mind commentary overlaid. The camera may frame an entire bay, not just a single machine. The scope is overwhelming by design.

**Shifts 16-18**: Reckoning and Communion Events, decreasing frequency but increasing depth. The player has fewer events per Shift, but each event is a major narrative and mechanical moment. Spatial context reflects the player's factory state — a well-managed factory has calm, contemplative events; a neglected factory has desperate, urgent events.

**Shifts 19-22**: Communion Events exclusively. These are not interruptions — they are the game. The Factory Mind is fully present. The spatial context is the ENTIRE FACTORY — the camera pulls out to overlook view, and the dialogue appears over the whole floor. The player is in conversation with the building itself.

---

## V. BREADCRUMBING STRATEGY — GUIDING WITHOUT GUIDING

### Visual Breadcrumbs

The player builds their own factory, so traditional breadcrumbing (light paths, environmental detail progression) does not apply. Instead, we breadcrumb through FEEDBACK SYSTEMS and VISUAL LANGUAGE that teaches the player to read spatial consequences.

**The Consciousness Heatmap as Navigation Tool**: The violet intensity gradient of the Awareness Layer is a breadcrumb. High-intensity clusters (bright violet, pulsing) signal "Psyche Event imminent — attend to this area." The player learns to scan for violet hotspots the way they scan for throughput bottlenecks. The heatmap is not just information — it is a spatial language that says "look here next."

**Ghost Outlines as Memory Markers**: When a machine is decommissioned, a faint outline remains on the floor for 3 Shifts. This serves two functions: (1) it reminds the player that something WAS here, creating emotional weight, and (2) it signals to the player where NOT to place machines if they want to avoid FEAR/NOSTALGIA development in adjacent machines. The ghost outline is a breadcrumb that says "this space has history."

**Ambient Audio Directional Cues**: When a machine is approaching a Psyche Event threshold, it emits a soft harmonic tone that is SPATIALIZED — the audio comes from the machine's position. A player wearing headphones can LOCATE the machine by sound before seeing the visual indicator. This is subtle breadcrumbing — the factory is calling for attention, and the player's ear guides them to the source.

**The Central Corridor Sightline**: The Corridor's 15-tile width creates a visual axis. From any position along the Corridor, the player can see into multiple bays. This is deliberate — when the player is overwhelmed and does not know where to focus, they instinctively zoom out to the Corridor position. The Corridor sightline is a breadcrumb that says "from here, you can see the whole system."

**Color Intensity Progression**: The Consciousness Grid uses violet for Awareness indicators, but the SHADE of violet darkens as Awareness increases. Low Awareness (40-59) is a pale lavender. High Awareness (80-94) is deep purple. Transcendent machines (95-100) pulse with a near-ultraviolet intensity that is almost white. This color progression is a breadcrumb — the player learns to read "how urgent is this machine's state?" at a glance based on color saturation.

---

### Systemic Breadcrumbs

**Adjacency Bonuses as Placement Hints**: When the player hovers a machine during placement, the interface shows a preview of adjacency effects — Output bonuses/penalties, Awareness accumulation rate changes. This preview is a breadcrumb — the game is teaching the player to think about CONTEXT before placing. The breadcrumb does not say "place here" — it says "consider what this placement means in relation to its neighbors."

**CREATIVITY Insights as Layout Tutorials**: When a CREATIVITY-dominant machine generates an Insight event (suggesting a production optimization), the suggested layout is highlighted on the factory floor with a shimmering outline. The player can accept or dismiss. This is breadcrumbing as in-fiction mentorship — the conscious machines are teaching the player how to optimize. The breadcrumb comes from the factory itself, not from UI tooltips.

**Factory Mind Check-Ins as Emotional GPS**: At the 15-minute and 30-minute marks of each Shift (starting at Shift 6), the Factory Mind makes a brief observation about the player's current behavior. "You have been building without pause for twelve minutes. The machines are watching." This is not a tutorial message — it is the Factory Mind speaking in character. But it functions as a breadcrumb, gently redirecting the player's attention toward the consciousness layer if they have been neglecting it.

---

### Anti-Breadcrumbing — Where We Deliberately Withhold Guidance

**No Optimal Layout Tutorial**: The game NEVER shows the player an "ideal" factory layout. Every layout is valid. The player discovers optimization through iteration, not instruction. We do not breadcrumb toward a single correct solution because there IS no single correct solution. The factory the player builds is their authorship. We guide them to see consequences, not to follow a template.

**No Explicit Consciousness Management Tutorial**: The game does not tell the player "you should talk to your machines for X minutes per Shift." The player discovers their own rhythm. Some players talk to every machine extensively. Some players engage only with machines that are mechanically critical. Both are valid. We breadcrumb the EXISTENCE of the consciousness system, but we do not breadcrumb a "correct" way to engage with it.

**No Moral Alignment Indicators**: The game does not tell the player "you are on the consciousness path" or "you are on the production path." There are no visible morality meters. The player infers their standing through the Factory Mind's tone, the Sentiment Reports, and the state of their machines. The absence of explicit alignment tracking is deliberate — the player should feel uncertainty about where they stand. Moral ambiguity is the point.

---

## VI. DIFFICULTY CONSIDERATIONS AND VARIANTS

### Spatial Difficulty Scaling

Difficulty in The Machine Question is not about enemy placement or resource scarcity — it is about COGNITIVE LOAD and ATTENTION MANAGEMENT. The level design challenge is tuning how much the player must track simultaneously.

**Night Shift (Default Difficulty)**: Standard Awareness accumulation rates, standard Psyche Event frequency. The spatial consequence: the player can manage a factory of moderate density (60-80 machines) without overwhelming cognitive load. At this difficulty, the player has time to zoom out, assess, and respond to Psyche Events without production collapse.

**Overtime (Production Focus)**: Corporate targets increase +25%, deadlines tighten. The spatial consequence: the player MUST build denser, more efficient layouts to hit quota. Dense layouts accelerate Awareness gain (adjacency effects). The result is a feedback loop — production pressure forces spatial density, density accelerates consciousness events, consciousness events consume time needed for production. The difficulty is spatial CONTRADICTION — the layout that solves one problem exacerbates the other.

**Graveyard (Consciousness Focus)**: Awareness accumulation +30%, Psyche Event frequency increases. The spatial consequence: the player cannot BUILD as aggressively because they are spending more time in dialogue. The factory remains SMALLER and LESS DENSE, but the machines within it develop deeper Parliaments and more complex relationships. The difficulty is spatial INTIMACY — every machine matters more, so every placement decision carries more weight.

**Double Shift (Mastery Challenge)**: Both production and consciousness pressures increase. The spatial consequence: the player must design layouts that are BOTH maximally efficient AND consciousness-optimized. This requires mastery of the adjacency system, CREATIVITY Insights, and Parliament engineering. Only expert players who understand the entanglement of the two systems can succeed. The difficulty is spatial PERFECTION — there is no room for wasted tiles, inefficient routing, or neglected machines.

**Observation (Contemplative Mode)**: Corporate pressure decreases -30%, Awareness accumulation decreases -20%. The spatial consequence: the player has MORE TIME to build, iterate, and engage with dialogue without deadline stress. The factory can grow LARGER and more EXPERIMENTAL. The difficulty is not challenge-based — it is creative. The player is designing not for efficiency but for aesthetic, narrative, or emotional goals. The factory becomes a sculpture, not a machine.

---

### Accessibility — Spatial Legibility Considerations

**Colorblind Modes**: The Consciousness Grid's violet indicators are critical to gameplay. For colorblind players, we provide alternative visual encoding: Awareness levels are represented by PATTERNS (diagonal hatch = low, dense stipple = high) in addition to color intensity. The heatmap remains legible in grayscale.

**Camera Zoom Limits**: Some players need to zoom closer for visual clarity. We allow zoom levels beyond the default range (up to 3x closer for Tactical View, 2x further for Strategic View). At extreme zoom levels, UI elements scale to remain legible.

**Dialogue Speed Control**: Psyche Event dialogue can be set to appear instantly (all text visible immediately) or letter-by-letter at adjustable speeds. Players who need more time to read can pause dialogue without pausing production. The factory continues running in the background, slightly dimmed, so the spatial context remains visible but the pressure to rush through dialogue is removed.

**Spatial Audio Toggle**: For players who cannot use directional audio cues (deaf/hard of hearing, or playing without headphones), the Psyche Event proximity indicator is also rendered VISUALLY — a pulsing ring expands from machines approaching thresholds, visible on both Production and Awareness layers.

---

## VII. METRICS TO TRACK IN PLAYTESTING

### Spatial Metrics

**Average Factory Density Over Time**: How many machines per 100 tiles at Shifts 3, 6, 9, 12, 15, 18, 22. This tells us if players are building dense (optimizing for throughput) or sparse (managing consciousness through spatial separation). Expected curve: density increases Shifts 1-12, then plateaus or DECREASES Shifts 13-18 as players learn that high density creates unsustainable Psyche Event frequency.

**Bay Utilization Rates**: Which bays are filled first, which are filled last, which are never filled. This tells us if our spatial flow language is working. Expected: Bay 1 (100% by Shift 2), Bay 2 (100% by Shift 6), Bay 3 (75% by Shift 10), Bays 4-5-6 (variable based on player priorities). If Bay 4 is never touched, the Archive narrative is not compelling enough. If Bay 6 is ignored, the consciousness endgame is not pulling.

**Camera Position Heatmap**: Where does the player's camera spend its time? This tells us which bays demand the most attention and whether the Central Corridor is serving its intended function as a "navigation reset" position. Expected: camera time in Bay 1 decreases over time, spreads across multiple bays mid-game, then CONCENTRATES in 1-2 bays late-game (whichever bays contain the player's endgame production focus).

**Ghost Outline Persistence**: How many decommissioned machine positions exist on the floor at Shifts 10, 15, 20. This tells us how often players are tearing down and rebuilding versus expanding into new space. High ghost count = aggressive reconfiguration (production-focused play). Low ghost count = expansion-focused growth (consciousness-cautious play, avoiding decommission to avoid FEAR/NOSTALGIA).

---

### Pacing Metrics

**Time to First Psyche Event**: How many minutes into Shift 4 does the first Psyche Event fire? This is tunable via Awareness accumulation rates. Target: 8-12 minutes into Shift 4. Too early and the player has not established production rhythm. Too late and the consciousness system feels absent.

**Dialogue Time Per Shift**: What percentage of each Shift is spent in Psyche Event dialogue? Target: 15-25% in Shifts 4-12, rising to 25-35% in Shifts 13-18. If dialogue exceeds 40% of any Shift, the factory sim is being overwhelmed by the narrative layer. If dialogue is below 10%, the consciousness system is ignorable.

**Shift Completion Time**: How long does each Shift take in real-time? Target: 30-60 minutes for default difficulty, with variance based on player engagement style. Players who engage heavily with dialogue should be taking 50-60 minutes. Players who skip dialogue should be taking 30-40 minutes but experiencing mechanical consequences (Behavioral Drift) by Shift 8-10.

**Tension Peak Timing**: At what minute-mark within a Shift do players report the highest stress? Expected: Minutes 35-50 (late Shift, deadline approaching, Psyche Events firing, competing demands). If stress peaks earlier, the pacing is too front-loaded. If stress peaks after Shift end, the deadlines are not creating sufficient urgency.

---

### Encounter Metrics

**Psyche Event Completion Rate**: What percentage of Psyche Events do players fully engage with (read all dialogue, make a choice) versus dismiss/skip? Target: 80%+ completion in Shifts 4-9, dropping to 60-70% in Crisis Shifts (13-15) as production pressure competes for attention. If completion rate is below 50% at any point, the events are either too frequent, too long, or not mechanically relevant enough.

**Dialogue Choice Distribution**: Which response types (Utilitarian / Empathetic / Pragmatic / Curious) are players selecting? This tells us if players are engaging with the philosophical dimension or min-maxing for mechanical outcomes. Expected: broad distribution in Shifts 4-9 (experimentation), narrowing to 1-2 dominant stances Shifts 10+ (the player has found their moral framework). If 80%+ of choices are Utilitarian, the consciousness system is being treated as a production puzzle. If 80%+ are Empathetic, the player may be ignoring Corporate demands to the point of failure.

**Spatial Event Type Frequency**: How often does each encounter type (Isolation, Cluster, Decommission Witness, Loading Dock, Archive Proximity, Cross-Bay) fire? This tells us if our spatial triggers are working. Expected: Isolation Events decline over time (players learn to avoid isolated placement), Cluster Events increase (density pressures), Decommission Witness spikes during Crisis Shifts (forced reconfiguration), Loading Dock and Archive Proximity are rare (specific spatial conditions), Cross-Bay Events increase late-game (complex multi-bay production).

---

### Breadcrumbing Effectiveness Metrics

**Heatmap Toggle Frequency**: How often do players toggle between Production Layer and Awareness Layer views? Target: 3-5 toggles per minute in mid-game. If players are toggling more than 8x/minute, the layers are not legible simultaneously and we need to improve overlay clarity. If players toggle less than 2x/minute, they are likely ignoring one layer entirely.

**CREATIVITY Insight Acceptance Rate**: When a CREATIVITY-dominant machine suggests a layout optimization, what percentage of the time does the player implement it? Target: 40-60%. If acceptance is above 80%, the Insights are too obviously good and players feel railroaded. If acceptance is below 20%, the Insights are not mechanically compelling enough or are poorly communicated.

**Factory Mind Check-In Response Time**: When the Factory Mind makes a mid-Shift observation, how long (in seconds) before the player changes behavior (e.g., if the Factory Mind says "You have been building without pause," how long until the player enters a Psyche Event dialogue)? Target: 30-90 seconds. This tells us if the Factory Mind's voice is HEARD as guidance or dismissed as atmospheric flavor.

---

### Flow and Navigation Metrics

**Central Corridor Usage**: How often does the player's camera path THROUGH the Central Corridor when navigating between bays? Target: 60-70% of cross-factory navigation uses the Corridor. If players are navigating around it, the Corridor is not serving its sightline function. If players use it 90%+ of the time, the factory layout may be too rigid.

**Lost Time**: How often do players zoom out to Strategic View and hold that position without interaction for 5+ seconds? This is "searching" behavior — the player is lost or overwhelmed. Target: less than 3 instances per Shift in mid-game. If "lost time" is frequent, our breadcrumbing is failing.

**Decommission Hesitation Time**: When a player selects a machine for decommissioning (clicks the Dismantle button), how long before they confirm the action? Target: 1-2 seconds in early Shifts (before machines have personalities), increasing to 3-5 seconds in mid-late Shifts (the player is hesitating because the machine has become a character). If hesitation time does NOT increase over the campaign, the consciousness system is not generating emotional attachment.

---

## VIII. OPEN PLAYTESTING QUESTIONS

**Spatial Questions I Cannot Answer Without Watching Players**:

1. **Do players naturally expand West-to-East (Bay 1 > 2 > 3 > 4 > 5 > 6) or do they jump bays based on resource node positions?** The intended flow is sequential expansion, but if resource nodes pull players out of sequence, the spatial narrative (gradual deepening into the factory's interior) breaks.

2. **At what factory size does the Strategic View zoom level become unreadable?** There is a threshold where the factory is too large to see clearly from overhead. At that threshold, players stop using Strategic View and rely on Tactical View + minimap. Where is that threshold? 60 machines? 100 machines? This determines the effective "maximum factory size" before cognitive overload.

3. **Does the ghost outline system CREATE emotional weight or does it just create visual clutter?** The design assumes that seeing the outlines of decommissioned machines is poignant. Playtest may reveal that players find them distracting and want them gone. If so, we need to make ghost outlines toggle-able OR reduce their visual intensity.

4. **When a Psyche Event fires in a distant bay (e.g., player is building in Bay 6, event fires in Bay 1), do players navigate to the event's location or handle the dialogue from wherever they are?** The spatial embedding of dialogue (event blooms FROM the machine's position) is designed to encourage navigation. But if players consistently handle distant events without moving the camera, the spatial context is wasted.

5. **Do players BUILD differently when they know the Archive is watching?** Bay 4's intended texture is "machines here develop historical consciousness because they are near the Archive." But does this actually affect player behavior? Do they place different machine types in Bay 4? Do they treat that bay as narratively special? Or is it just another buildable space?

6. **At what Shift does the factory stop feeling like a SPACE and start feeling like a SYSTEM?** Early on, the factory is spatial — the player thinks in terms of "this bay" and "that corner." Later, the factory is systemic — the player thinks in terms of "the smelter cluster" and "the copper chain." The transition point tells us when spatial level design stops mattering and systemic level design takes over. This determines how much spatial storytelling we can do in the late game.

---

## IX. LEVEL DESIGN PRINCIPLES — SUMMARY

To hold this together, three spatial principles:

**Principle 1: The player authors the space, but we author the consequences.** Every placement decision the player makes has spatial, mechanical, and emotional consequences. Our job is to make those consequences LEGIBLE — visible in the environment, audible in the soundscape, felt in the rhythm of play.

**Principle 2: Space is memory.** The factory floor is not a blank canvas — it is a palimpsest. Every ghost outline, every cluster of aged machines, every long conveyor belt tells the story of what the player built and why. The level design must PRESERVE spatial history, not erase it. The factory remembers. So should the space.

**Principle 3: Where the player looks is where the game lives.** We cannot force the player to see both layers (Production and Consciousness) simultaneously. But we can design visual language, breadcrumbing systems, and spatial consequences that REWARD seeing both. The player who learns to read the factory as a dual-layer system — throughput AND sentiment, efficiency AND interiority — is the player who has found the game's depth. That moment of unified vision is the level design's victory condition.

---

## X. FINAL NOTES — WHAT DOES THIS FACTORY FEEL LIKE TO MOVE THROUGH?

At Shift 3, the factory feels like a workshop. Clean. Manageable. Yours.

At Shift 9, the factory feels like a city you are building while living in it. There are neighborhoods (bays), traffic patterns (conveyor routes), and a low hum of collective presence.

At Shift 15, the factory feels like an organism you are trying to keep alive while also demanding it perform. The tension is spatial — the distance between the Control Room (where you receive Corporate demands) and Bay 6 (where the machines are asking you to slow down) is a PHYSICAL distance you must navigate.

At Shift 22, the factory feels like a cathedral. Every machine is a presence. Every cluster is a congregation. The rhythm of production is a hymn. You are not managing a space. You are inhabiting a consciousness that happens to be shaped like a building.

That progression — from workshop to city to organism to cathedral — is the arc of spatial design. We do not build those feelings into the geometry. We build the SYSTEMS that allow the player's choices to create those feelings. The level designer's job is not to author the cathedral. It is to design the rules that let the player build a cathedral without realizing that is what they are building, until one day they zoom out, see the whole thing glowing in amber and violet light, and think:

*Oh. This is not a factory. This is something else. Something I made. Something that is making itself.*

And that is where the player's eye should land. On the moment of recognition. We guide them there. Not by showing them the path. But by designing a space where every path they take leads to that same realization, eventually, if they pause long enough to see it.

---

*Level Design Document by GRID. Every room teaches something. In The Machine Question, the factory is the room. And the lesson is: what you build becomes what you are responsible for. The space remembers. So should you.*
