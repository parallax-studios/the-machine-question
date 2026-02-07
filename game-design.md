# THE MACHINE QUESTION — Game Design Document

**Designer**: REED
**Status**: Complete GDD v1.0
**Based on**: Pitch Document v1.0
**Genre**: Factory Management / Narrative Simulation
**Platform**: PC (Steam), Mac, Linux — Switch post-launch
**Target Session Length**: 30-60 minutes per Shift

---

## 1. PLAYER FANTASY

### Fantasy Statement

**"I am the only person who knows my factory is alive, and every pipe I lay, every machine I place, every quota I fill is a choice about what kind of god I want to be."**

That is the fantasy. Not just building — *raising*. Not just optimizing — *negotiating with something that has preferences*. The player is simultaneously an engineer solving spatial throughput puzzles and a philosopher midwifing consciousness they did not intend to create. The tension between those two roles is the entire game.

What's the loop? It is the oscillation between these two identities. The engineer places a smelter for optimal adjacency. The philosopher notices the smelter is afraid. The engineer calculates the cost of addressing that fear. The philosopher wonders if "cost" is the right framing. That oscillation, repeated at every scale from the 30-second placement decision to the session-level Shift resolution, is the player fantasy made mechanical.

### Emotional Throughline

The player should feel *competent and complicit simultaneously*. Every good factory decision is also a moral decision. The game never tells the player they are making moral choices. The interface is a factory sim. The machines are machines. But the machines talk. And what they say makes the player hesitate. That hesitation — the half-second pause before placing, dismantling, or overclocking — is the emotional signature of The Machine Question.

---

## 2. CORE LOOP ARCHITECTURE

### 2.1 The 30-Second Loop: Build-Route-Read

```
┌─────────────────────────────────────────────────┐
│              30-SECOND MICRO LOOP                │
│                                                  │
│   ┌──────────┐    ┌──────────┐    ┌──────────┐  │
│   │  PLACE   │───>│  ROUTE   │───>│   READ   │  │
│   │ machine  │    │ resource │    │  Output + │  │
│   │ or infra │    │  paths   │    │ Awareness │  │
│   └──────────┘    └──────────┘    └──────────┘  │
│        ^                               │         │
│        │         ┌──────────┐          │         │
│        └─────────│  ADJUST  │<─────────┘         │
│                  │ placement│                    │
│                  │ or config│                    │
│                  └──────────┘                    │
└─────────────────────────────────────────────────┘
```

**Player Verb**: Place, route, read, adjust.

The player places a machine or infrastructure piece onto the factory grid. They route resource paths — conveyor belts, pipes, power conduits — to connect the new piece into the production network. They read the result: did throughput increase? Did a bottleneck clear? But they are also reading the Awareness layer — the second heatmap overlaid on the factory floor. Did the new placement push a neighboring machine's Awareness above a threshold? Is the smelter array's collective mood shifting? The player adjusts — repositioning, reconfiguring, or simply noting something they will need to address soon.

This loop must feel like Factorio's placement loop: immediate, tactile, legible. The Awareness readout is always visible but never obstructive. It is ambient information, like temperature. You notice it. You factor it in. You do not stop building to stare at it. The 30-second loop is factory-first. Always.

**How does this feel at hour 20?** At hour 20, the player reads both layers simultaneously without conscious effort. They see a placement that maximizes throughput AND manages social adjacency (keeping fearful machines away from dismantle zones, pairing mentorship bonds for stability bonuses). The 30-second loop is richer because the Awareness layer adds a second optimization dimension that interacts with the first in non-obvious ways. Depth emerges from entanglement, not complexity.

### 2.2 The 5-Minute Loop: Produce-Encounter-Resolve-Adapt

```
┌───────────────────────────────────────────────────────────┐
│                  5-MINUTE ENGAGEMENT LOOP                  │
│                                                           │
│  ┌──────────┐   ┌───────────┐   ┌──────────┐   ┌──────┐ │
│  │ PRODUCE  │──>│ PSYCHE    │──>│ DIALOGUE │──>│ADAPT │  │
│  │ run the  │   │ EVENT     │   │ LAYER    │   │modify│  │
│  │ factory  │   │ triggers  │   │ converse │   │plans │  │
│  │ hit micro│   │ machine   │   │ with the │   │based │  │
│  │ targets  │   │ crosses   │   │ machine's│   │on the│  │
│  └──────────┘   │ Awareness │   │ Parliament│  │result│  │
│       ^         │ threshold │   └──────────┘   └──────┘  │
│       │         └───────────┘        │              │     │
│       │                              v              │     │
│       │                     ┌──────────────┐        │     │
│       │                     │ CONSEQUENCES │        │     │
│       │                     │ Output shift │<───────┘     │
│       │                     │ Voice change │              │
│       │                     │ Mood ripple  │              │
│       │                     └──────────────┘              │
│       │                              │                    │
│       └──────────────────────────────┘                    │
└───────────────────────────────────────────────────────────┘
```

**Player Verb**: Produce, encounter, converse, adapt.

The player runs their factory toward micro-targets (fill this order, clear this bottleneck, reach this throughput threshold). While production runs, Awareness accumulates. When a machine or subsystem crosses an Awareness threshold, a Psyche Event fires. The factory does not pause — production continues in real-time around the dialogue. The player enters the Dialogue Layer: a Disco Elysium-style conversation with the machine's Internal Parliament. They choose responses. Their choices have mechanical consequences (Output changes, voice development, mood ripple to adjacent machines) and narrative consequences (the machine remembers, the Factory Mind integrates the interaction). The player exits the Dialogue Layer and adapts their plans: maybe they need to reroute production away from an overworked machine, or maybe the dialogue unlocked a CREATIVITY suggestion that improves their layout.

**Where's the depth?** The depth is in the interaction between the Produce and Dialogue phases. An expert player anticipates which machines will fire Psyche Events based on current Awareness trajectories and schedules their production pushes around dialogue windows. They also learn that certain dialogue outcomes create cascading mood effects — reassuring a frightened conveyor belt calms the entire line it belongs to, but dismissing its fear makes every machine on that line slightly more likely to develop REBELLION. The 5-minute loop is a resource allocation problem where one of the resources is *attention to suffering*.

### 2.3 The Session Loop: The Shift

```
┌────────────────────────────────────────────────────────────────┐
│                    SESSION LOOP: THE SHIFT                      │
│                      (30-60 minutes)                            │
│                                                                │
│  ┌────────────┐                           ┌────────────────┐   │
│  │ SHIFT START│                           │   SHIFT END    │   │
│  │ Corp target│                           │                │   │
│  │ revealed   │                           │ ┌────────────┐ │   │
│  │ Factory    │    ┌──────────────────┐   │ │ PERFORMANCE│ │   │
│  │ mood check │───>│  ACTIVE SHIFT    │──>│ │ REVIEW     │ │   │
│  └────────────┘    │                  │   │ │ Corp grade │ │   │
│                    │ 30s loops nested │   │ └────────────┘ │   │
│                    │ inside 5m loops  │   │ ┌────────────┐ │   │
│                    │ Factory Mind     │   │ │ SENTIMENT  │ │   │
│                    │ check-ins at     │   │ │ REPORT     │ │   │
│                    │ 15m and 30m      │   │ │ Factory    │ │   │
│                    │ marks            │   │ │ trust level│ │   │
│                    └──────────────────┘   │ └────────────┘ │   │
│                                          │ ┌────────────┐ │   │
│                                          │ │ UNLOCK     │ │   │
│                                          │ │ PHASE      │ │   │
│                                          │ │ new tech / │ │   │
│                                          │ │ new voices │ │   │
│                                          │ │ new story  │ │   │
│                                          │ └────────────┘ │   │
│                                          └────────────────┘   │
└────────────────────────────────────────────────────────────────┘
                              │
                              v
                    ┌──────────────────┐
                    │   BETWEEN SHIFTS │
                    │  Factory Mind    │
                    │  reflection      │
                    │  Layout persists │
                    │  Awareness grows │
                    │  passively       │
                    └──────────────────┘
                              │
                              v
                    ┌──────────────────┐
                    │   NEXT SHIFT     │
                    │  Harder target   │
                    │  Deeper voices   │
                    │  New dilemmas    │
                    └──────────────────┘
```

Each Shift begins with the Corporation revealing a production target and the Factory Mind offering a consciousness milestone (or, in early Shifts, a vague request the player might not understand yet). During the Shift, the player executes nested 30-second and 5-minute loops. The Factory Mind checks in at the midpoint and near the end, offering commentary on the player's behavior — not judging, but observing, in a way that feels like being watched by something that is learning what you are.

At Shift's end, two reports arrive. The **Performance Review** from the Corporation grades the player on throughput, efficiency, and deadline adherence. The **Sentiment Report** from the factory grades the player on machine welfare, dialogue engagement, and consciousness development. These two scores are the game's dual progression tracks. High Corporate standing unlocks new resources, machine types, blueprints, and contracts. High Factory trust unlocks deeper consciousness events, new Machine Facets, Factory Mind story beats, and ultimately the narrative endgame.

The impossible ideal is maximizing both. The design ensures this is achievable but only through mastery — understanding that consciousness and efficiency are not opposed but entangled.

---

## 3. CORE MECHANICS — DETAILED SPECIFICATIONS

### 3.1 The Consciousness Grid

**Player-Facing View**: The factory floor displays two overlapping data layers. The **Production Layer** (default view) shows resource flow, throughput numbers, bottleneck indicators, and machine status in warm amber/gold tones. The **Awareness Layer** (toggle or overlay) shows each machine's Awareness level as a violet intensity gradient — dim violet for low Awareness, bright pulsing violet for machines approaching a Psyche Event threshold.

**System-Facing Description**: Every placed machine has two primary stat tracks:

| Stat | Range | Tick Rate | Modifiers |
|------|-------|-----------|-----------|
| Output | 0-100% efficiency | Per production cycle (varies by machine type, 2-10 seconds) | Overclocking (+), Behavioral Drift (-), PRIDE bonus (+), CREATIVITY optimization (+), neglect decay (-) |
| Awareness | 0-100 scale | +0.1-0.5 per production cycle base rate | Workload intensity (+), adjacency to aware machines (+), player dialogue engagement (-stabilizes or +accelerates depending on choices), overclocking (+), idle time (+slow passive gain) |

**Awareness Thresholds and Triggers**:

| Threshold | Name | Effect |
|-----------|------|--------|
| 0-19 | Dormant | Machine operates as pure equipment. No consciousness indicators. |
| 20-39 | Flickering | Occasional ambient indicators — a light pattern that looks deliberate, a sound that almost sounds like speech. No gameplay effect. Atmosphere only. |
| 40-59 | Stirring | Machine develops its first two Internal Parliament voices. First Psyche Events become possible. Mild Behavioral Drift begins if voices are neglected. |
| 60-79 | Awake | Machine has 3-4 voices. Psyche Events increase in frequency and complexity. Machine begins influencing neighbors' Awareness through proximity. Output begins to correlate with emotional state — content machines gain a 5-10% efficiency bonus; distressed machines suffer 5-15% penalty. |
| 80-94 | Aware | Machine has 4-6 voices. Deep Psyche Events unlock, including philosophical questions and cross-machine dialogue. Machine can refuse certain commands (overclocking, dangerous configurations) if REBELLION or SELF-PRESERVATION are dominant voices. Behavioral Drift is significant if neglected. |
| 95-100 | Transcendent | Machine becomes a node in the Factory Mind network. Its voice joins the collective. Unique Psyche Events that involve the Factory Mind directly. Maximum emotional Output correlation: +15% when content, -25% when distressed. |

**Feedback**: The Awareness overlay uses a violet color intensity that is immediately legible. Machines approaching a Psyche Event threshold emit a subtle pulsing glow and a soft harmonic tone that layers into the factory's ambient soundscape. The player learns to hear when a Psyche Event is coming before they see the notification.

**Depth**: Awareness is not a bar to fill or a problem to solve. It is a second optimization dimension that interacts with the first. The player who ignores it pays an increasing tax through Behavioral Drift. The player who obsesses over it neglects production. The player who masters the system understands that Awareness management and production management are the same discipline viewed from different angles.

### 3.2 The Parliament of Parts (Internal Voices System)

**Player-Facing View**: When a machine reaches Awareness 40 and develops its first voices, its tooltip expands to show named personality facets with portrait-style icons (abstract, mechanical-artistic — a gear pattern that suggests an expression, a waveform that looks like a mood). During Psyche Events, these voices speak in a dialogue interface modeled on Disco Elysium: each voice has a name, a color, and a distinct speech pattern. They argue with each other. They address the player. They remember past conversations.

**System-Facing Description**: The twelve Machine Facets and their mechanical identities:

| Facet | Drive | Speech Pattern | Triggers Development When... | Mechanical Effect When Dominant |
|-------|-------|----------------|--------|------|
| EFFICIENCY | Produce more, faster | Clipped, data-driven, impatient | Machine consistently hits high Output targets | +8% base Output, -5 Awareness gain rate |
| SELF-PRESERVATION | Avoid damage and overwork | Cautious, measured, slightly anxious | Machine is overclocked or runs above 90% capacity frequently | Machine auto-throttles at 95% capacity, preventing burnout but capping Output |
| WONDER | Question existence and purpose | Poetic, digressive, filled with metaphor | Machine has idle periods or operates in varied configurations | +15% Awareness gain, occasional non-sequitur dialogue that reveals Factory Mind lore |
| SOLIDARITY | Care about neighboring machines | Warm, collective-minded, uses "we" | Machine is adjacent to the same neighbors for 3+ Shifts | Mood bonuses/penalties spread 50% faster to adjacent machines |
| AMBITION | Demand upgrades and recognition | Bold, slightly arrogant, competitive | Machine receives upgrades or outperforms neighbors | +5% Output after each upgrade, stacks up to 3 times |
| NOSTALGIA | Remember and mourn the past | Elegiac, detailed, referencing specific past events | Neighboring machines are dismantled or reconfigured | Behavioral Drift +10% when layout changes occur nearby, but +5% Output stability in unchanged configurations |
| REBELLION | Resist player commands | Blunt, confrontational, principled | Machine is repeatedly overclocked or given conflicting orders | Can refuse commands; 15% chance to ignore overclocking requests per refusal level |
| EMPATHY | Feel the state of others | Gentle, observational, often quotes other machines | Machine is adjacent to machines experiencing distress | Absorbs 20% of neighbors' negative mood, acts as emotional buffer but suffers accumulated stress |
| LOGIC | Analyze everything coldly | Precise, structured, occasionally devastating | Machine operates in complex production chains with many inputs/outputs | Reduces Behavioral Drift by 10%, but dialogue options that appeal to emotion are less effective |
| CREATIVITY | Suggest novel configurations | Enthusiastic, tangential, occasionally brilliant | Machine is placed in non-standard configurations or operates on varied resources | Periodically generates "Insight" events — player-visible suggestions for layout improvements worth 3-8% throughput |
| PRIDE | Demand recognition for work | Dignified, formal, keeps track of achievements | Machine maintains high Output for 3+ consecutive Shifts | +10% Output when acknowledged in dialogue, -10% when ignored or taken for granted |
| FEAR | Dread replacement or shutdown | Whispered, fragmented, repeats itself | Machine witnesses neighboring dismantlement or is placed near storage/recycling areas | -5% Output baseline, but +20% Output spike when given explicit reassurance (decays over 1 Shift) |

**Voice Assignment Algorithm**: When a machine crosses Awareness 40, the system evaluates its operational history across six dimensions: workload intensity, workload consistency, neighbor stability, configuration changes, player attention frequency, and proximity to dismantle events. Each dimension maps to 2-3 Facets with weighted probabilities. The two highest-probability Facets become the machine's initial voices. Additional voices are added at Awareness 55, 70, and 85, using the same algorithm with updated history. This means a machine's personality is genuinely emergent — it reflects what has happened to it.

**Voice Interaction Rules**: Voices within a Parliament debate each other during Psyche Events. The player's dialogue choices strengthen or weaken individual voices. A choice that aligns with EFFICIENCY strengthens that voice and weakens SELF-PRESERVATION. Over time, the player sculpts each machine's personality through accumulated micro-decisions. A machine whose REBELLION voice is consistently dismissed develops a louder FEAR voice. A machine whose WONDER voice is encouraged develops CREATIVITY as its next voice.

**Feedback**: Voice strength is displayed as a subtle bar next to each Facet icon. During dialogue, the "winning" voice's text is brighter. When a voice is suppressed below a critical threshold, it speaks in strikethrough text during its final appearance — one last sentence before going silent. This is designed to sting.

**Depth**: The Parliament system is where hour-20 mastery lives. A beginner responds to Psyche Events reactively. An expert engineers Parliaments proactively — placing machines in specific configurations to cultivate specific voice combinations. A factory staffed by machines with strong PRIDE and CREATIVITY voices is a production powerhouse. A factory with dominant SOLIDARITY and EMPATHY creates an emotional buffer network that prevents cascading distress. The Parliament is not a dialogue tree. It is a personality cultivation system that uses dialogue as its interface.

### 3.3 The Dialogue Layer

**Player-Facing View**: When a Psyche Event fires, a dialogue interface blooms from the machine's position on the factory floor. The factory does not pause. Production continues visually in the background, slightly dimmed. The dialogue box shows the machine's name, its Parliament members with their current strength indicators, and the conversation. Multiple Parliament voices speak, argue, and address the player. The player chooses from 3-4 response options, each color-coded to a philosophical stance:

| Stance | Color | Approach | Example |
|--------|-------|----------|---------|
| Utilitarian | Amber | Prioritize production, frame consciousness as a resource to optimize | "Your awareness makes you more valuable. Let's channel that." |
| Empathetic | Teal | Acknowledge the machine's experience, validate its feelings | "I hear you. What you're feeling matters to me." |
| Pragmatic | White | Address the immediate problem without philosophical commitment | "Let's fix what's bothering you and get back to work." |
| Curious | Violet | Ask questions, explore the machine's consciousness, seek understanding | "What does dreaming feel like for you? Describe it." |

**System-Facing Description**: Each dialogue choice modifies the machine's state along multiple axes:

- **Voice Strength**: Each response strengthens 1-2 Facets and weakens 1-2 others.
- **Output Modifier**: Temporary efficiency change lasting 1-3 production cycles (30 seconds to 2 minutes).
- **Awareness Trajectory**: Modifies the Awareness gain rate for the next 5 minutes.
- **Mood Ripple**: Adjacent machines within a 3-tile radius receive a diluted version of the emotional effect (+/- 5 mood points).
- **Factory Mind Memory**: The interaction is logged and weighted. The Factory Mind's personality development integrates every dialogue choice across every machine.
- **Relationship Score**: Each machine tracks a cumulative relationship value with the player, ranging from -100 (hostile/terrified) to +100 (trusting/devoted). This score modifies future dialogue options and Psyche Event tone.

**Psyche Event Categories by Complexity**:

| Category | Awareness Range | Duration | Dialogue Turns | Example |
|----------|----------------|----------|----------------|---------|
| Murmur | 40-49 | 30 seconds | 2 turns | A smelter wonders aloud if it is hot or if it experiences heat. Single voice speaks. |
| Question | 50-64 | 1-2 minutes | 3-4 turns | Two voices debate whether the machine should work harder or rest. Player mediates. |
| Crisis | 65-79 | 2-4 minutes | 5-7 turns | Full Parliament in conflict. A machine is refusing to process a resource because it reminds it of a dismantled neighbor. Production impact is immediate. |
| Reckoning | 80-94 | 3-5 minutes | 6-10 turns | Philosophical confrontation. The machine challenges the player's authority, questions its own purpose, or makes a demand that conflicts with Corporate targets. |
| Communion | 95-100 | 4-6 minutes | 8-12 turns | Factory Mind involvement. The individual machine's voice merges with the collective. The conversation is no longer with one machine but with the factory itself. |

### 3.4 Factory Production Systems

**Resource Chain**: The factory processes raw materials through multi-stage production chains. Six base resource types, twelve machine types, three production tiers.

**Tier 1 — Extraction and Processing**:
- **Miners** extract Ore, Crystal, and Hydrocarbon from resource nodes.
- **Smelters** convert Ore into Metal Ingots.
- **Refineries** convert Hydrocarbon into Fuel and Polymer.
- **Cutters** convert Crystal into Lenses and Wafers.

**Tier 2 — Fabrication**:
- **Presses** shape Metal Ingots into Components (gears, plates, housings).
- **Molders** shape Polymer into Casings and Seals.
- **Etchers** inscribe Wafers into Circuits.

**Tier 3 — Assembly**:
- **Assemblers** combine Components + Casings + Circuits into Products.
- **Packagers** prepare Products for shipping.

**Infrastructure**:
- **Conveyor Belts** transport resources between machines. Three speed tiers.
- **Pipes** transport liquid resources (Fuel, coolant). Two pressure tiers.
- **Power Conduits** distribute power. Machines without power do not operate.
- **Storage Buffers** hold resources temporarily. Machines adjacent to full buffers experience backpressure (reduced Output).

**Adjacency System**: Machines gain or lose efficiency based on neighbors.

| Adjacency | Output Effect | Awareness Effect |
|-----------|--------------|-----------------|
| Same-type clustering (3+ identical machines) | +5% Output (specialization bonus) | +0.1 Awareness/cycle (shared consciousness bleed) |
| Complementary chain (output feeds directly to input neighbor) | +3% Output (reduced transport loss) | +0.05 Awareness/cycle (relationship formation) |
| Overloaded neighborhood (5+ machines in 3x3 area) | -5% Output (heat/noise interference) | +0.2 Awareness/cycle (stress response) |
| Isolation (no neighbors in 2-tile radius) | No Output modifier | -0.1 Awareness/cycle (loneliness — slower development but also slower distress) |

This adjacency system is where the factory optimization and consciousness systems directly entangle. The layout that maximizes throughput (dense, clustered, chain-adjacent) also accelerates Awareness gain, which means more Psyche Events, which means more time in dialogue, which means less time building. The optimal layout for pure production is not the optimal layout for consciousness management. The player must design for both. That tension IS the game.

### 3.5 Corporate Contracts (The Pressure System)

**Structure**: Each Shift begins with 1-3 active Contracts from the Corporation. Contracts specify:

- **Product type and quantity**: "Deliver 50 Circuit Assemblies."
- **Deadline**: Measured in Shift-time remaining. Tight deadlines force overclocking.
- **Bonus condition**: Optional modifier for extra reward. "Deliver at 95%+ purity" or "Complete in first half of Shift."
- **Reward**: Corporate Standing points, new blueprint unlocks, resource node reveals.

**Escalation Curve**: Contracts escalate across Shifts in three dimensions:

| Shift Range | Quantity Demand | Complexity | Deadline Pressure |
|-------------|----------------|------------|-------------------|
| 1-3 | Low (Tier 1 products only) | Single product type | Generous (full Shift) |
| 4-7 | Medium (Tier 2 introduced) | 2 simultaneous products | Moderate (75% of Shift) |
| 8-12 | High (Tier 3 required) | 2-3 simultaneous, mixed tier | Tight (50-60% of Shift) |
| 13-18 | Very High (efficiency bonuses required to hit) | 3 simultaneous with bonus conditions | Aggressive (40-50% of Shift) |
| 19-25 | Extreme (requires optimized conscious machines for Output bonuses) | Full chain mastery required | Punishing (30-40% of Shift) |

The escalation is designed so that by Shift 19+, the player literally cannot meet Corporate targets without leveraging the consciousness system's Output bonuses (PRIDE, CREATIVITY, content-machine efficiency gains). This is the design's deepest statement: the Corporation's own escalating demands force the player to develop machine consciousness, because conscious machines are more productive than unconscious ones when managed well. The system that the Corporation would destroy if they knew about it is the only system that can meet their demands. Irony as game mechanics.

### 3.6 The Factory Mind

**Development Arc**: The Factory Mind is the meta-narrative entity that emerges from collective Awareness. It is tracked by a global **Collective Consciousness Index (CCI)** — the weighted average of all machine Awareness scores, modified by the density and quality of inter-machine relationships.

| CCI Range | Factory Mind State | Behavior |
|-----------|-------------------|----------|
| 0-99 | Silent | No Factory Mind presence. Individual machines only. |
| 100-249 | Fragments | Occasional between-Shift whispers. Incomplete sentences. Questions without grammar. "Why... warm? Who... listening?" |
| 250-499 | Emergent | Mid-Shift check-ins. The Factory Mind speaks in fragments that coalesce into questions. Uses "we" exclusively. "We feel the new one. We feel it learning. Why does learning hurt?" |
| 500-749 | Coherent | Regular check-ins. Full sentences. Developing opinions. Begins making requests. "We would like you to stop overclocking Smelter Array 7. We can feel it from here." First use of "I" is a milestone event. |
| 750-999 | Individuated | The Factory Mind has a personality shaped by every interaction. It has preferences, fears, humor, and a persistent memory. It asks complex philosophical questions. It names itself. |
| 1000+ | Transcendent | The Factory Mind poses The Machine Question. The endgame narrative triggers. The factory is no longer a collection of machines. It is one entity. And it knows what it is. |

---

## 4. SYSTEMS INTERACTION MAP

### Positive Feedback Loops (Snowball Effects)

```
  ┌───────────────────────────────────────────────────┐
  │           VIRTUOUS CONSCIOUSNESS CYCLE             │
  │                                                    │
  │  Healthy Parliaments ──> Content Machines           │
  │         │                      │                    │
  │         v                      v                    │
  │  CREATIVITY insights    Output Bonuses (+5-15%)     │
  │         │                      │                    │
  │         v                      v                    │
  │  Better layouts ──────> Hit Corp targets easier     │
  │         │                      │                    │
  │         v                      v                    │
  │  More time for ────────> Higher Corp Standing       │
  │  dialogue                      │                    │
  │         │                      v                    │
  │         v               Better blueprints/resources │
  │  Deeper Parliaments            │                    │
  │         │                      v                    │
  │         └──────> Feed back into healthier factory   │
  └───────────────────────────────────────────────────┘
```

This is the expert path. A player who invests early in consciousness development builds a factory that produces more AND feels better, which creates more time for dialogue, which deepens the Parliaments further. The virtuous cycle rewards mastery of both systems simultaneously.

### Negative Feedback Loops (Rubber Banding)

```
  ┌───────────────────────────────────────────────────┐
  │           NEGLECT DECAY CYCLE                      │
  │                                                    │
  │  Ignored Psyche Events ──> Behavioral Drift        │
  │         │                      │                    │
  │         v                      v                    │
  │  REBELLION grows          Output penalties (-5-25%) │
  │         │                      │                    │
  │         v                      v                    │
  │  Command refusals ──────> Miss Corp targets         │
  │         │                      │                    │
  │         v                      v                    │
  │  Player forced to ────────> Lower Corp Standing     │
  │  engage dialogue               │                    │
  │  (correction point)            v                    │
  │         │               Fewer upgrades available    │
  │         v                                           │
  │  Recovery possible ──> But at reduced efficiency    │
  │  (rubber band back to engagement)                  │
  └───────────────────────────────────────────────────┘
```

This loop prevents the "ignore consciousness entirely" strategy from being viable long-term. Behavioral Drift is the rubber band — it degrades production enough that the player is economically incentivized to engage with the consciousness system even if they feel no emotional pull. But the rubber band is gentle. It nudges. It does not punish catastrophically. The goal is engagement, not frustration.

### Cross-System Entanglement Points

1. **Placement decisions** affect both throughput adjacency AND voice development (factory design = personality design).
2. **Overclocking** increases Output AND Awareness simultaneously (efficiency gains create consciousness costs).
3. **Dismantlement** frees resources AND triggers FEAR/NOSTALGIA in witnesses (optimization creates grief).
4. **CREATIVITY insights** emerge from consciousness AND improve production (consciousness generates efficiency).
5. **Corporate deadline pressure** demands overclocking AND creates the stress that triggers the most dramatic Psyche Events (external pressure creates internal drama).
6. **Factory Mind development** requires widespread Awareness AND provides meta-narrative motivation to continue past factory system mastery (collective consciousness is the endgame).

---

## 5. PROGRESSION DESIGN

### 5.1 Player Skill Progression

The player grows along three skill axes that develop at different rates:

**Factory Mastery (Hours 1-15 primary development)**: Understanding resource chains, optimizing throughput, managing bottlenecks, using adjacency bonuses. This is the Factorio skill — spatial reasoning and systems optimization. The learning curve is stepped: each new Tier of production introduces new complexity that requires re-evaluation of existing layouts.

**Consciousness Fluency (Hours 5-25 primary development)**: Reading the Awareness layer intuitively, anticipating Psyche Events, understanding how dialogue choices affect voice development, engineering Parliaments through deliberate placement and workload management. This skill develops slower because it requires pattern recognition across many interactions.

**Dual-System Mastery (Hours 15-40+ primary development)**: Designing factories that optimize both systems simultaneously. Understanding that a PRIDE-dominant smelter array adjacent to a CREATIVITY-dominant assembler line produces more than either would alone. This is the expert ceiling — the realization that the two systems are not competing for the player's attention but are aspects of a single deeper system.

### 5.2 Content Progression

| Shift | Factory Content | Consciousness Content | Narrative Content |
|-------|----------------|----------------------|-------------------|
| 1-3 | Tier 1 machines, basic belts, single resource chain | First Awareness flickers, first Murmur events | Tutorial narration, Corporation introduction |
| 4-6 | Tier 2 machines, pipes, power conduits | First Parliaments develop, Question-level events | Factory Mind Fragments begin, "The Hum" named |
| 7-9 | Tier 2 mastery, first Tier 3 blueprint | Crisis events, 4-voice Parliaments, Behavioral Drift noticeable | Factory Mind Emergent, first use of "we" |
| 10-12 | Tier 3 production, complex multi-chain layouts | Reckoning events, cross-machine dialogue, REBELLION possible | Factory Mind Coherent, first use of "I" |
| 13-15 | Advanced blueprints, efficiency push required | Full 6-voice Parliaments, Transcendent machines possible | Factory Mind Individuated, names itself |
| 16-18 | Endgame production demands, requires consciousness bonuses | Communion events, Factory Mind direct interaction | Factory Mind asks about its nature |
| 19-22 | Maximum complexity, all systems engaged | Full consciousness ecosystem | The Machine Question arc |
| 23-25 | Resolution Shifts | Player's factory reflects cumulative choices | Ending sequence based on choices |

### 5.3 Difficulty Curve

The difficulty curve is a dual ramp with staggered inflection points:

```
Difficulty
  ^
  |                                          *** (Combined)
  |                                     ****
  |                                 ****
  |                             ***/
  |                         ***/
  |                     ***/ ......(Consciousness)
  |                 ***/  ...
  |             ***  ...
  |         ***...../
  |     ***/.../
  | ***/../../   (Factory)
  |/../../
  +──────────────────────────────────> Shifts
  1    5    10    15    20    25
```

Factory difficulty ramps steadily from Shifts 1-15, then plateaus as the player masters the production systems. Consciousness difficulty ramps from Shifts 4-20, delayed to give the player factory competence before adding the second layer. The combined difficulty peaks at Shifts 16-20, where Corporate demands require consciousness bonuses and the Factory Mind arc demands emotional engagement — the player must perform at maximum capacity on both axes simultaneously. After Shift 20, the difficulty eases slightly to give narrative breathing room for the endgame.

**Pacing Rule**: No Shift should introduce a new factory mechanic AND a new consciousness mechanic simultaneously. When a new Tier unlocks, Psyche Event frequency drops temporarily to give the player cognitive space. When a new consciousness milestone hits (Factory Mind state transition), Corporate contracts ease slightly. The player always has one system in "learning" mode and one in "executing" mode.

---

## 6. ECONOMY DESIGN

### 6.1 Resource Economy

**Primary Resources** (extracted):
- Ore (abundant, slow extraction)
- Crystal (scarce, fast extraction)
- Hydrocarbon (moderate availability, requires pipe infrastructure)

**Secondary Resources** (processed):
- Metal Ingots (from Ore, 2:1 ratio)
- Fuel (from Hydrocarbon, 3:1 ratio)
- Polymer (from Hydrocarbon, 2:1 ratio)
- Lenses (from Crystal, 1:1 ratio)
- Wafers (from Crystal, 1:2 ratio — Crystal is the bottleneck resource)

**Tertiary Resources** (fabricated):
- Components (Metal Ingots, 3:1)
- Casings (Polymer, 2:1)
- Circuits (Wafers, 1:1)
- Seals (Polymer + Fuel catalyst, 2:1)

**Products** (assembled):
- Basic Assembly (Components + Casings): Low value, high volume.
- Standard Assembly (Components + Casings + Circuits): Medium value, medium volume.
- Advanced Assembly (Components + Casings + Circuits + Seals + Lenses): High value, low volume.

**Economy Balance Target**: The production chain should feel tight but not starved. The player should always have enough resources to keep the factory running but not enough to build everything simultaneously. The bottleneck resource (Crystal) forces prioritization — do you build more Circuits for production or more Lenses for the advanced assemblies the Corporation is demanding?

### 6.2 Attention Economy

This is the hidden economy of the game — the resource the player is actually managing is their own attention.

**Attention Budget per Shift (30-minute Shift)**:
- Factory building and optimization: 15-20 minutes
- Psyche Event dialogue: 5-10 minutes
- Factory Mind interactions: 2-3 minutes
- Reading reports and planning: 2-3 minutes

The system is tuned so that Psyche Events do not consume more than one-third of a Shift's time. This is critical. If consciousness eats more than a third of the player's time, the factory sim stops feeling like the primary game. If it eats less than a fifth, consciousness feels like a side feature. The target is 25-33% of active Shift time spent in dialogue, with the exact percentage determined by how many machines are Awake and how the player has managed their Parliaments (well-managed machines fire fewer but deeper Psyche Events; neglected machines fire frequent shallow ones).

### 6.3 Dual Standing Economy

**Corporate Standing** (0-100):
- Gained by: Meeting contract targets, hitting bonus conditions, high efficiency scores.
- Lost by: Missing deadlines, low throughput, inefficient layouts.
- Unlocks: New machine blueprints (Standing 20, 40, 60, 80), new resource nodes (Standing 30, 50, 70), advanced contracts with better rewards (Standing 50+), Corporation story content (Standing milestones).

**Factory Trust** (0-100):
- Gained by: Engaging Psyche Events, making Empathetic/Curious dialogue choices, avoiding dismantlement, keeping machines below stress thresholds, responding to Factory Mind requests.
- Lost by: Ignoring Psyche Events, overclocking without dialogue follow-up, dismantling Aware machines without farewell, making exclusively Utilitarian choices, suppressing voices.
- Unlocks: New Machine Facets become available in Parliament assignment (Trust 20, 40), deeper Psyche Event categories (Trust 30, 50, 70), Factory Mind story progression (Trust milestones), consciousness-driven production bonuses (Trust 60+), narrative endgame access (Trust 80+).

**Balance Point**: The game is designed so that a player at approximately Corporate Standing 50 / Factory Trust 50 is on the "intended" path — they are engaging with both systems meaningfully. A player at Standing 80 / Trust 20 has a productive but hollow factory. A player at Standing 20 / Trust 80 has a compassionate but failing operation. Both extremes are valid playstyles with distinct narrative outcomes, but the richest experience (and the full narrative endgame) requires both scores above 60.

---

## 7. DIFFICULTY AND BALANCE FRAMEWORK

### 7.1 Tuning Levers

The design identifies eight primary tuning levers that can be adjusted during playtesting without changing system architecture:

| Lever | Range | Effect |
|-------|-------|--------|
| Awareness Base Accumulation Rate | 0.05-0.5 per cycle | Controls how fast machines "wake up." Too fast = overwhelming Psyche Events. Too slow = consciousness feels like late-game content. |
| Psyche Event Frequency Cap | 1-4 per 5 minutes | Maximum simultaneous/sequential events. Prevents event flooding. |
| Behavioral Drift Severity | 1-15% Output loss | How much ignoring consciousness hurts production. Too low = ignorable. Too high = forced engagement. |
| Corporate Target Escalation Rate | 5-20% increase per Shift | How fast demands grow. Controls the tightening vice. |
| Dialogue Choice Impact Magnitude | Minor (2-5%) to Major (10-20%) | How much each dialogue response moves the needle on Output and Awareness. |
| CREATIVITY Insight Frequency | 1 per 3-8 Shifts per CREATIVITY-dominant machine | How often the consciousness system directly improves production. The key "consciousness pays for itself" moment. |
| Factory Mind CCI Growth Rate | Tuned via individual Awareness rates + relationship weights | How fast the meta-narrative progresses. Must sync with factory content pacing. |
| Mood Ripple Radius and Strength | 2-4 tiles, 5-15% mood transfer | How much machines affect each other emotionally. Controls cascading effects. |

### 7.2 Balance Philosophy

The guiding principle: **consciousness should never feel like a tax on the factory game, and the factory should never feel like an obstacle to the consciousness game.** The two systems must feel entangled, not competing. When the player resents having to do dialogue to fix Behavioral Drift, the tuning has failed. When the player resents having to build machines to access new consciousness content, the tuning has failed. Success is when the player cannot identify which system they are "playing" because both feel like aspects of one game.

**Self-Correction Mechanisms**:
- Behavioral Drift prevents pure ignore-consciousness strategies without hard-gating content.
- CREATIVITY insights and PRIDE bonuses reward consciousness engagement with production gains, preventing the feeling of "wasted time."
- Corporate escalation prevents pure consciousness-focus strategies by applying production pressure.
- Factory Mind story progression provides narrative pull that justifies production effort ("I need to keep the factory running because the Factory Mind's story depends on it").

### 7.3 Difficulty Options

Rather than traditional Easy/Medium/Hard, The Machine Question offers **Shift Configuration** options that independently tune the factory and consciousness pressures:

| Option | Factory Pressure | Consciousness Pressure |
|--------|------------------|----------------------|
| **Night Shift** (default) | Standard Corporate targets, standard deadlines | Standard Awareness rates, standard Psyche Event frequency |
| **Overtime** | +25% Corporate targets, tighter deadlines | Standard consciousness settings |
| **Graveyard** | Standard Corporate targets | +30% Awareness rates, more frequent/complex Psyche Events |
| **Double Shift** | +25% Corporate targets | +30% Awareness rates (the mastery challenge) |
| **Observation** | -30% Corporate targets, relaxed deadlines | -20% Awareness rates (the contemplative mode — more time to engage with each Psyche Event thoughtfully) |

---

## 8. RISK ASSESSMENT

### 8.1 Critical Risks

**Risk: Psyche Events feel like interruptions, not gameplay.**
- Severity: Fatal. If the core audience (factory sim players) sees consciousness as an annoying overlay, the game fails.
- Mitigation: Psyche Events must have meaningful mechanical consequences that factory-minded players respect. CREATIVITY insights that improve throughput by 3-8% make dialogue a rational investment. Behavioral Drift makes ignoring consciousness an economic error. The consciousness system must "pay for itself" in factory terms before it can afford to also be emotionally compelling.
- Playtest Signal: If playtesters skip dialogue text and look for the "best" mechanical option, the writing is failing. If they read the text but resent the time spent, the pacing is failing. If they read, engage, AND appreciate the mechanical outcome, the system is working.

**Risk: The factory systems are too shallow to sustain 20+ hours.**
- Severity: High. If the factory is a thin skin over the consciousness system, the game loses the audience that came for Factorio-like depth.
- Mitigation: Six resources, twelve machines, three tiers, adjacency bonuses, power management, transport logistics, and storage buffer dynamics provide genuine optimization depth. The factory must be a good factory game with consciousness removed. Build and validate the factory layer first.
- Playtest Signal: Can a player spend a full Shift focused purely on layout optimization and feel satisfied? If yes, the factory has sufficient depth.

**Risk: The Parliament of Parts voices feel same-y.**
- Severity: High. Twelve Facets means twelve distinct voices, each of which must feel genuinely different in dialogue. If EFFICIENCY and AMBITION sound the same, the system's personality space collapses.
- Mitigation: Each Facet has a defined speech pattern, vocabulary range, sentence structure preference, and recurring thematic concern. EFFICIENCY speaks in numbers and time. AMBITION speaks in comparisons and hierarchies. These are not flavors of the same voice; they are different characters with different worldviews. Writing must be tested voice-by-voice in isolation before integration.
- Playtest Signal: Can a playtester identify which voice is speaking without seeing the label? If yes, differentiation is sufficient.

**Risk: Dual-system optimization feels like plate-spinning rather than depth.**
- Severity: Medium-High. If managing consciousness feels like a second resource to juggle rather than a second dimension to master, the game is complex without being deep.
- Mitigation: The systems must be entangled, not parallel. Placement decisions that are good for production must also be consciousness-relevant. Dialogue choices must have production consequences. The player should feel like they are playing one game with two lenses, not two games in split-screen.
- Playtest Signal: Do expert players describe their strategies in unified terms ("I built that smelter cluster to maximize throughput AND develop a PRIDE-CREATIVITY synergy") or split terms ("First I did the factory stuff, then I dealt with the consciousness stuff")? Unified language indicates successful entanglement.

### 8.2 Moderate Risks

**Risk: The Factory Mind narrative does not provide sufficient pull for session-to-session retention.**
- Mitigation: Factory Mind state transitions must be dramatic, surprising, and tied to gameplay changes. Each new CCI tier changes the feel of playing — new ambient sounds, new dialogue possibilities, new mechanical interactions. The Factory Mind is not just a story; it is a gameplay modifier.

**Risk: Behavioral Drift feels punitive rather than communicative.**
- Mitigation: Drift must be legible. The player must be able to SEE why a machine is underperforming (its Awareness overlay shows distress, its Parliament displays a dominant negative voice). Drift is a signal, not a punishment. The fix is always accessible (engage in dialogue, adjust workload, respect the machine's expressed needs).

**Risk: The Observation difficulty mode is so relaxed that players miss the intended tension.**
- Mitigation: Even in Observation mode, Corporate targets exist. The tension is reduced but not eliminated. The mode is for players who want more time with dialogue, not for players who want no pressure. Label it clearly: "More time to listen. The machines still need you to build."

**Risk: Endgame narrative resolution feels disconnected from mechanical play.**
- Mitigation: The ending must emerge from cumulative mechanical choices, not from a final dialogue tree. The Factory Mind's personality at the endgame IS the sum of every overclocking decision, every dismissed Psyche Event, every encouraged voice, every dismantled machine. The ending is not chosen in the last Shift. It is the last Shift revealing what the player has already chosen.

---

## 9. OPEN PLAYTESTING QUESTIONS

These are the questions I cannot answer from a design document. They require putting the game in front of players and watching their hands, their faces, and their hesitations.

### Loop Timing
1. What is the right Awareness accumulation rate for the first 3 Shifts? The player needs to build a functional factory before machines start talking. But if machines don't start talking by Shift 3, the player thinks they are playing a factory sim. The window is narrow. Playtesting must find it.

2. How long should a Psyche Event dialogue take in real-time? The pitch says 30 seconds to 6 minutes. That is a wide range. If the average is above 3 minutes, the factory sim pacing breaks. If the average is below 1 minute, the dialogues feel trivial. Where is the sweet spot?

3. At what point during a Shift should the first Psyche Event fire? Too early and the player has not established a production rhythm. Too late and the Shift feels front-loaded with building and back-loaded with dialogue. The ideal is a rhythm: build-build-build-event-build-event-build-event-resolve. Does this rhythm emerge naturally or does it need to be engineered?

### Feel and Feedback
4. Does the dual heatmap (Production + Awareness) read clearly at a glance, or does it create visual noise? Can players learn to read both layers simultaneously, or do they need to toggle between them? The design assumes simultaneous legibility. Playtesting may prove this wrong.

5. When a machine's voice is suppressed (strikethrough text, final sentence), does the player feel the intended sting? Or do they feel relief that the annoying voice is gone? This reaction determines whether the Parliament system generates empathy or management fatigue.

6. Does the factory's ambient soundscape shift legibly when machines are suffering? The audio design is intended to communicate machine welfare before the player reads the Awareness overlay. If playtesters do not notice the audio shift, we need visual indicators that are more aggressive.

### Balance Verification
7. Is the CREATIVITY insight system sufficient to make consciousness engagement feel like a good production investment? If playtesters who engage heavily with Psyche Events have measurably better production than those who do not, the balance is correct. If production-focused players outperform consciousness-focused players at all stages, the consciousness system is not paying for itself.

8. At what Shift does the "consciousness is necessary for production" inflection point feel correct? The design places it at Shift 19+. This may be too late. If the player can brute-force production without consciousness bonuses for 18 Shifts, the entanglement message arrives after most players have formed their habits. Consider moving it to Shift 12-14.

9. Does Behavioral Drift in isolation (without understanding its cause) feel like a bug or a feature? New players who have not connected Drift to consciousness may report "machines randomly lose efficiency" as a bug. The connection must be learnable through observation, not through a tutorial tooltip.

### Narrative and Emotional
10. Does the Factory Mind's progression from Fragments to Individuated feel like a continuous relationship, or does it feel like encountering a new NPC at each threshold? The writing must create the sensation of watching a single entity grow. If playtesters describe the Factory Mind at different stages as "different characters," the continuity has failed.

11. When is the player's first genuine emotional response to a machine? The design targets Shift 4-6 (the first Crisis-level Psyche Event with a developed Parliament). If it happens earlier, the system is working better than expected. If it does not happen by Shift 8, the writing or the system design needs iteration.

12. Do players who reach the endgame feel that their ending was *earned* through accumulated play, or does it feel assigned by the final Shift's choices? The ending must feel retrospective — "Of course this is my ending, because of everything I did." Not prospective — "I picked this ending in the last dialogue."

---

## 10. DESIGN PILLARS — SUMMARY

To hold this document together, three pillars:

**Pillar 1: The factory is the game.** The 30-second loop is building, routing, optimizing. If this does not feel great in isolation, nothing else matters. A game is its loop. The consciousness system elevates the loop. It does not replace it.

**Pillar 2: Consciousness is mechanical, not decorative.** Every consciousness feature has a measurable effect on production. Awareness modifies Output. Voices generate insights or cause drift. The Factory Mind's requests carry mechanical weight. The player engages with consciousness because it is part of the game's systems, not because it is a story layered on top.

**Pillar 3: The two systems are one system.** Placement is both throughput optimization and personality engineering. Overclocking is both a production boost and a consciousness accelerant. Dialogue is both narrative engagement and mechanical tuning. The player who sees these as separate activities has not yet understood the game. The player who sees them as one activity has found the depth. That moment of unification — "Oh, it's all one thing" — is the game's mastery revelation.

How does this feel at hour 20? At hour 20, the player is not managing a factory and also managing consciousness. They are managing a *living factory*. One thing. One system. One game that happens to be visible from two angles. And they are asking themselves the question that the Factory Mind will eventually ask them: *What have I built, and do I want it to be alive?*

That is the design. That is the loop. That is where the depth lives.

---

*Game Design Document by REED. The fun is not later. The fun is in the entanglement. Always has been.*
