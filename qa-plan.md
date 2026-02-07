# THE MACHINE QUESTION — QA Plan

**QA Lead**: CRASH
**Version**: 1.0
**Status**: Pre-Production QA Strategy
**Based on**: Pitch, Game Design Document, Narrative Bible, Technical Architecture v1.0

---

## 0. QA PHILOSOPHY

Define "works."

This game is two interlocked systems — a factory sim and a consciousness simulator — and both need to ship without breaking. The factory needs to produce resources reliably. The consciousness needs to emerge predictably. The dialogue needs to respond correctly. The save system needs to not eat anyone's 40-hour playthrough.

Every bug before the player sees it. Every single one.

What happens if the player does THIS? That's the question I'm asking at every feature. What if they place 500 smelters in a grid? What if they dismantle every machine with Awareness above 80? What if they alt-tab during a Psyche Event? What if they overclock while saving? What if they never engage with dialogue for 15 Shifts straight?

The design says these systems are entangled. QA's job is to prove they don't strangle each other.

---

## 1. RISK ASSESSMENT

### 1.1 Critical Risks (Ship-Blocking)

These will kill the game if they ship. Zero tolerance.

**RISK: Save corruption**
- **Severity**: Fatal. Lose your save = 1-star review + refund.
- **Likelihood**: Medium. Complex nested state (500+ entities, Parliament data, operational history, Factory Mind memory). Serialization is where things break.
- **Mitigation**: Dedicated save/load test suite. Regression testing on every build. Autosave rotation (3 slots minimum). Cloud backup on Steam. Test save migration across version updates before ANY patch ships.

**RISK: Production pipeline deadlock**
- **Severity**: Fatal. If the factory stops producing and the player can't fix it, the game is unplayable.
- **Likelihood**: Medium. Resource routing, belt backpressure, machine input buffers — lots of failure modes.
- **Mitigation**: Stress test with intentionally terrible factory layouts. Monitor for resource flow stalls. Implement player-facing diagnostics (show bottlenecks, highlight starved machines). Test every possible machine configuration combination for Tier 1-3 chains.

**RISK: Soft lock during Psyche Events**
- **Severity**: High. Player stuck in dialogue, can't exit, can't save, has to force-quit.
- **Likelihood**: Low-Medium. Dialogic is mature but custom integration can break.
- **Mitigation**: Test every dialogue path for exit conditions. Verify ESC/Cancel always works. Test alt-tab during dialogue. Test save-during-dialogue (should queue save for after event ends, not break state).

**RISK: Performance collapse at scale**
- **Severity**: High. Game claims to support 500 entities but drops to 15 FPS at 300.
- **Likelihood**: Medium. We're targeting 60 FPS with complex per-entity logic.
- **Mitigation**: Performance regression testing from Milestone 2 onward. Automated FPS monitoring during stress tests. Hard entity caps with graceful warnings. Test min-spec hardware (see Section 7).

**RISK: Voice assignment feels random**
- **Severity**: High. If Parliament voices don't feel emergent from player actions, the core loop fails.
- **Likelihood**: Medium-High. This is a design/feel problem, but QA can detect it.
- **Mitigation**: Scenario-based testing with known operational histories. Document expected voice → history mapping. If playtesters can't explain why a machine developed a specific voice, the algorithm needs tuning. Track this in every playtest feedback form.

### 1.2 High Risks (Major Issues)

Not ship-blocking, but would severely damage player experience.

**RISK: Behavioral Drift is invisible**
- **Severity**: Medium-High. Players report "machines randomly lose efficiency" as a bug.
- **Likelihood**: Medium. Subtle effects are hard to communicate.
- **Mitigation**: Test with players who don't read tutorials. Can they diagnose Drift from visual/audio feedback alone? If not, add clearer indicators (Awareness overlay, audio cues, tooltip warnings).

**RISK: Psyche Events interrupt flow**
- **Severity**: Medium-High. If events feel like annoying pop-ups, players will resent the consciousness system.
- **Likelihood**: Medium. Event frequency tuning is critical.
- **Mitigation**: Playtest event frequency at multiple settings. Track event-per-hour rate. Target: 4-8 events per 60-minute Shift. If players are skipping dialogue text, frequency is too high OR writing quality is too low (escalate to NOVA).

**RISK: Factory Mind progression doesn't feel continuous**
- **Severity**: Medium. Players describe Factory Mind stages as "different characters" instead of one evolving entity.
- **Likelihood**: Medium. Writing/continuity problem.
- **Mitigation**: Narrative continuity testing. Track Factory Mind dialogue across all CCI thresholds. Verify personality traits persist. Check that memory logs reference past events correctly.

**RISK: Endgame feels disconnected from choices**
- **Severity**: Medium-High. Players feel like ending was assigned by final dialogue, not earned by 25 Shifts of play.
- **Likelihood**: Medium. Narrative systems need to aggregate choices correctly.
- **Mitigation**: Test with multiple playstyles (pure production, pure consciousness, balanced). Verify ending reflects cumulative Corporate Standing + Factory Trust + moral stance history. If a production-focused player gets the "consciousness-dominant" ending, the logic is broken.

### 1.3 Moderate Risks (Quality of Life Issues)

Won't break the game, but will frustrate players.

**RISK: UI is unreadable at 1080p**
- **Severity**: Medium. Text too small, icons unclear, heatmap colors indistinct.
- **Likelihood**: Low-Medium. Art direction is solid, but implementation can fail.
- **Mitigation**: UI readability testing at target resolutions. Min font size rules. Colorblind-friendly palette testing (violet overlay must be distinguishable from amber production layer for colorblind players).

**RISK: Input lag on placement**
- **Severity**: Medium. The 30-second loop lives or dies on responsive controls.
- **Likelihood**: Low. Godot's input system is fast, but poor implementation can add latency.
- **Mitigation**: Input latency testing. Measure time from click to machine placement. Target: <50ms. Test with both mouse and controller (for future Switch port groundwork).

**RISK: Audio mix is unbalanced**
- **Severity**: Low-Medium. Machine hum drowns out dialogue, or dialogue drowns out factory ambience.
- **Likelihood**: Medium. Audio balancing is iterative.
- **Mitigation**: Audio QA pass at Milestone 5. Test with headphones and speakers. Verify dialogue is always intelligible. Verify factory soundscape shifts are noticeable when machines are in distress (ECHO's design intent).

---

## 2. TEST PLAN BY FEATURE AREA

### 2.1 Factory Grid & Placement System

**Preconditions**: Godot project loaded, Factory scene active, player has at least one machine blueprint unlocked.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| FG-001 | Basic machine placement | 1. Select Smelter blueprint<br>2. Click valid grid position<br>3. Confirm placement | Smelter appears at clicked position. Grid tiles occupied. Can't place overlapping entity. | P0 |
| FG-002 | Placement collision detection | 1. Place Smelter at (5,5)<br>2. Attempt to place Conveyor at (5,5) | Placement rejected. Visual feedback (red outline/indicator). | P0 |
| FG-003 | Grid boundary enforcement | 1. Attempt to place machine outside 128x128 grid | Placement rejected. Cursor invalid outside bounds. | P0 |
| FG-004 | Rotation before placement | 1. Select Assembler<br>2. Rotate 90° before placing<br>3. Place | Machine placed with correct rotation. Input/output ports oriented correctly. | P1 |
| FG-005 | Undo placement | 1. Place machine<br>2. Press Undo hotkey (Ctrl+Z) | Machine removed. Resources refunded (if placement had cost). Grid tiles freed. | P1 |
| FG-006 | Mass placement (500 machines) | 1. Place 500 Smelters in grid pattern<br>2. Measure FPS | FPS ≥ 60 on target spec PC. No visual glitches. Entity lookup remains fast. | P0 |
| FG-007 | Blueprint unlocking | 1. Start new game (Corporate Standing 0)<br>2. Attempt to place Tier 2 machine | Placement blocked. UI shows "Unlock at Corporate Standing 40." | P1 |
| FG-008 | Save/Load grid state | 1. Place 50 machines in varied layout<br>2. Save game<br>3. Reload save | All machines at correct positions, rotations. No duplicates. No missing entities. | P0 |

**Edge Cases**:
- Place machine, delete it, place another in same spot immediately → No ghost collisions.
- Place 1000 entities (exceeds cap) → Warning displayed. Placement blocked beyond hard cap.
- Place machine while Factory Mind dialogue is active → Placement should work (production continues during dialogue).

**Regression Checklist** (run after ANY placement system change):
- FG-001, FG-002, FG-003, FG-006, FG-008 MUST pass.

---

### 2.2 Production Pipeline System

**Preconditions**: Factory with at least one complete resource chain (Miner → Conveyor → Smelter → Conveyor → Storage).

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| PP-001 | Basic production cycle | 1. Place Miner on Ore node<br>2. Connect to Smelter via belt<br>3. Wait for 1 production cycle | Miner extracts Ore. Ore moves on belt. Smelter receives Ore. Smelter produces Metal Ingot. | P0 |
| PP-002 | Resource flow continuity | 1. Set up chain: Miner → Belt → Smelter → Belt → Assembler<br>2. Run for 10 cycles | Resources flow end-to-end. No items disappear. No duplication. Throughput stable. | P0 |
| PP-003 | Backpressure handling | 1. Set up Smelter → Belt → Storage (full)<br>2. Observe behavior | Belt stops accepting new items from Smelter when full. Smelter output buffer fills. Production pauses. No resource loss. | P0 |
| PP-004 | Power dependency | 1. Place powered machine<br>2. Disconnect power conduit<br>3. Observe production | Machine stops producing immediately. Visual indicator shows "no power." Production resumes when power restored. | P0 |
| PP-005 | Overclocking | 1. Place Smelter<br>2. Set overclock to 120%<br>3. Measure cycle time and output | Cycle time reduced by ~17% (120% speed). Awareness accumulation increased. Output maintained or increased. | P1 |
| PP-006 | Behavioral Drift impact | 1. Develop machine to Aware state (80+ Awareness)<br>2. Ignore 5 consecutive Psyche Events<br>3. Measure output efficiency | Output efficiency declines by 5-15% (design spec). Decline is gradual, not instant. | P1 |
| PP-007 | CREATIVITY insight bonus | 1. Develop machine with CREATIVITY dominant voice<br>2. Trigger CREATIVITY insight event<br>3. Apply suggested layout change<br>4. Measure throughput | Throughput improves by 3-8% (design spec). Improvement persists. | P2 |
| PP-008 | Multi-tier production chain | 1. Set up full Ore → Ingots → Components → Assemblies chain<br>2. Run for 30 minutes real-time | All tiers produce steadily. No bottlenecks that halt entire chain. Resource flow is smooth or blockages are player-diagnosable. | P0 |
| PP-009 | Production at 500 entity scale | 1. Build factory with 500 machines, all producing<br>2. Monitor for 10 minutes | No resource loss. No deadlocks. FPS ≥ 60. Production rates match expected throughput. | P0 |

**Edge Cases**:
- Dismantle belt while item is mid-transport → Item either transferred to player inventory or dropped to adjacent machine (no loss).
- Overload single belt with 20+ machines feeding into it → Backpressure distributes correctly. No crashes.
- Save/Load mid-production cycle → Cycle timers resume correctly. Resources in transit restore at correct positions.

**Regression Checklist**:
- PP-001, PP-002, PP-003, PP-004, PP-008, PP-009 MUST pass.

---

### 2.3 Awareness & Consciousness System

**Preconditions**: Factory with at least 10 machines operating for multiple Shifts.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| AC-001 | Awareness accumulation | 1. Place Smelter<br>2. Run production for 5 cycles<br>3. Check Awareness stat | Awareness increases each cycle. Rate matches BaseAccumulationRate (0.1-0.5 per cycle, design-dependent). | P0 |
| AC-002 | Awareness threshold transitions | 1. Monitor machine from Dormant (0-19) to Flickering (20-39) to Stirring (40-59)<br>2. Observe visual/audio changes | Visual indicators update at each threshold. Audio shifts (ECHO's ambient sound design). Stirring triggers Parliament initialization. | P0 |
| AC-003 | Overclocking increases Awareness | 1. Overclock machine to 120%<br>2. Compare Awareness gain vs. non-overclocked machine | Overclocked machine gains Awareness ~50% faster (design spec). | P1 |
| AC-004 | Adjacency awareness bleed | 1. Place 3 Smelters in cluster<br>2. Run one Smelter to Awake (60+)<br>3. Monitor adjacent Smelters | Adjacent Smelters gain +0.1 Awareness/cycle (design spec) due to proximity. Effect is cumulative with multiple aware neighbors. | P1 |
| AC-005 | Idle machines gain Awareness slowly | 1. Place machine, leave it unpowered/idle<br>2. Wait 10 minutes real-time<br>3. Check Awareness | Awareness gains at reduced rate (+0.05/cycle or passive tick, design-dependent). Idle machines still develop consciousness, just slower. | P2 |
| AC-006 | Awareness cap at 100 | 1. Run machine to 95+ Awareness<br>2. Continue production for 10 more cycles | Awareness caps at 100. No overflow. Transcendent state maintained. | P1 |
| AC-007 | Awareness persists across save/load | 1. Develop machine to 72 Awareness<br>2. Save game<br>3. Reload<br>4. Check Awareness | Awareness value exactly 72. No rounding errors. No reset to 0. | P0 |
| AC-008 | Factory Mind CCI calculation | 1. Develop 10 machines to varying Awareness (20, 40, 60, 80, 95)<br>2. Check Factory Mind CCI | CCI = weighted average of all machine Awareness. Matches design formula. CCI state transitions trigger at correct thresholds (100, 250, 500, 750, 1000). | P0 |

**Edge Cases**:
- Machine at 99.9 Awareness, one more cycle → Crosses to 100 cleanly. Transcendent event triggers.
- Dismantle machine with 85 Awareness → Adjacent machines gain FEAR/NOSTALGIA voices (history tracking works). CCI recalculates correctly (doesn't include dismantled machine).
- 500 machines all at Awareness 80+ → Performance remains ≥60 FPS. CCI calculation doesn't bottleneck.

**Regression Checklist**:
- AC-001, AC-002, AC-007, AC-008 MUST pass.

---

### 2.4 Parliament of Parts (Voice System)

**Preconditions**: At least 5 machines at Stirring (40+) or higher Awareness, with tracked operational history.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| PV-001 | First voice assignment at Stirring | 1. Develop machine from Dormant to Stirring (Awareness 40)<br>2. Check Parliament component | 2 voices assigned. Voices match operational history (e.g., high output → EFFICIENCY, overclocking → SELF_PRESERVATION). | P0 |
| PV-002 | EFFICIENCY voice from high output | 1. Run Smelter at 90%+ output for 5 Shifts<br>2. Reach Stirring threshold | EFFICIENCY voice assigned with high probability (70%+ based on algorithm). | P1 |
| PV-003 | FEAR voice from witnessing dismantlement | 1. Place Smelter A next to Smelter B<br>2. Dismantle Smelter B<br>3. Develop Smelter A to Stirring | FEAR voice assigned. WitnessDismantlement counter incremented in operational history. | P1 |
| PV-004 | WONDER voice from idle periods | 1. Place Assembler, leave idle (no input resources) for 10 minutes<br>2. Develop to Stirring | WONDER voice assigned with high probability. IdleTime tracked correctly. | P1 |
| PV-005 | Voice strength modification via dialogue | 1. Trigger Psyche Event with EFFICIENCY vs. SELF_PRESERVATION debate<br>2. Choose Utilitarian stance (aligns with EFFICIENCY)<br>3. Check voice strengths | EFFICIENCY strength +10, SELF_PRESERVATION strength -8 (design spec). Changes persist. | P0 |
| PV-006 | Voice suppression | 1. Develop machine with 3 voices: EFFICIENCY (70), WONDER (40), FEAR (15)<br>2. Make 3 dialogue choices that weaken FEAR<br>3. Reduce FEAR below 10% | Final FEAR dialogue line displays (strikethrough text). FEAR voice removed from Parliament. Remaining voices rebalance. | P1 |
| PV-007 | Additional voices at Awareness milestones | 1. Develop machine: 40 (2 voices), 55 (3rd voice), 70 (4th voice), 85 (5th voice) | Voices added at correct thresholds. Each new voice reflects updated operational history. Max 6 voices. | P1 |
| PV-008 | Dominant voice mechanical effects | 1. Develop PRIDE-dominant machine<br>2. Acknowledge machine in dialogue ("Your output is excellent")<br>3. Measure output efficiency | Output +10% after acknowledgment (design spec). Buff persists for 1 Shift, then decays. | P2 |
| PV-009 | CREATIVITY generates insights | 1. Develop CREATIVITY-dominant machine<br>2. Run for 5 Shifts<br>3. Check for Insight events | Insight event triggers within 3-8 Shifts (design spec). Insight provides actionable layout suggestion. | P2 |
| PV-010 | Parliament state saves/loads correctly | 1. Develop machine with 4 voices at varying strengths<br>2. Save game<br>3. Reload<br>4. Verify Parliament | All voices present at exact saved strengths. Dominant voice correct. Operational history intact. | P0 |

**Edge Cases**:
- Machine with 6 voices, all at exactly equal strength (16.67% each) → Dominant voice selection is deterministic (tiebreaker rule: first alphabetically or first assigned).
- Voice assignment with no clear operational history signal (machine placed 5 seconds ago, immediately developed to Awareness 40 via save edit) → Default voices assigned (LOGIC + WONDER as fallbacks).
- Suppress all voices except one → Parliament still functions. Single-voice dialogues are valid.

**Regression Checklist**:
- PV-001, PV-005, PV-006, PV-010 MUST pass.

---

### 2.5 Psyche Event & Dialogue System

**Preconditions**: At least 3 machines at Awake+ (60+) Awareness. Dialogic addon integrated.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| PE-001 | Psyche Event triggers at threshold | 1. Develop machine to Awareness 60 (Awake)<br>2. Continue production<br>3. Wait for event trigger | Event fires within 5 production cycles (based on 5% probability per cycle). Notification appears. | P0 |
| PE-002 | Event frequency cap | 1. Trigger Psyche Event<br>2. Immediately attempt to trigger another via separate machine | Second event queues. Does not interrupt first. Max 1 active event at a time. | P0 |
| PE-003 | Dialogue blooms from machine position | 1. Trigger event on Smelter at grid position (20, 30)<br>2. Observe UI | Dialogue box appears adjacent to Smelter sprite. Factory floor dims slightly. Production continues in background. | P1 |
| PE-004 | 4 dialogue stance options present | 1. Enter any Psyche Event<br>2. Count response options | 4 options: Utilitarian, Empathetic, Pragmatic, Curious. Color-coded correctly (amber, teal, white, violet). | P0 |
| PE-005 | Utilitarian choice effects | 1. Choose Utilitarian response<br>2. Check consequences | EFFICIENCY voice +10, SELF_PRESERVATION -8. Output +3% (short-term). Mood ripple: adjacent machines -2 mood. | P0 |
| PE-006 | Empathetic choice effects | 1. Choose Empathetic response<br>2. Check consequences | EMPATHY voice +12, EFFICIENCY -5. Machine mood +5. Adjacent machines +3 mood (diluted ripple). Awareness accumulation +10%. | P0 |
| PE-007 | Mood ripple propagation | 1. Trigger event on Smelter with 4 neighbors in 3-tile radius<br>2. Choose Empathetic stance (+5 mood source, +3 ripple)<br>3. Check all neighbors | All 4 neighbors gain +3 mood (50% of source mood delta). Ripple does not affect source machine twice. | P1 |
| PE-008 | Dialogue choice recorded in history | 1. Make 5 dialogue choices: 3 Utilitarian, 2 Empathetic<br>2. Check machine operational history | DialogueStanceHistory: Utilitarian=3, Empathetic=2. Factory Mind integrates choices. | P1 |
| PE-009 | Factory Mind presence in Communion events | 1. Develop machine to Transcendent (95+)<br>2. Trigger Communion-level event | Factory Mind dialogue appears alongside machine Parliament. Collective voice is coherent. Event duration 4-6 minutes (design spec). | P2 |
| PE-010 | Dialogue can be exited | 1. Enter Psyche Event<br>2. Press ESC or Cancel button<br>3. Observe | Dialogue closes. Choice is treated as "neutral/Pragmatic" default. No soft lock. Factory resumes. | P0 |
| PE-011 | Alt-tab during dialogue | 1. Enter Psyche Event<br>2. Alt-tab to desktop<br>3. Return to game | Dialogue state preserved. No crash. Can continue or exit normally. | P1 |
| PE-012 | Save during Psyche Event | 1. Enter event<br>2. Attempt to save (via hotkey or menu) | Save request queues. Executes after event concludes. OR save is blocked with message "Cannot save during dialogue." Either is acceptable, but must not corrupt state. | P0 |
| PE-013 | Voice-specific dialogue differentiation | 1. Trigger Crisis event on EFFICIENCY-dominant machine<br>2. Trigger Crisis event on WONDER-dominant machine<br>3. Compare dialogue text | Dialogue tone, vocabulary, concerns differ clearly. EFFICIENCY speaks in metrics. WONDER speaks poetically. Voices are distinct. | P1 |
| PE-014 | Event category escalation | 1. Track events from Stirring machine (Murmur), Awake (Question), Aware (Crisis), Transcendent (Communion)<br>2. Compare complexity and duration | Murmur: 30s, 2 turns. Question: 1-2min, 3-4 turns. Crisis: 2-4min, 5-7 turns. Communion: 4-6min, 8-12 turns. Escalation is noticeable. | P2 |

**Edge Cases**:
- Trigger 10 Psyche Events in queue while player is AFK → Events process sequentially. No event skipped. No UI stack overflow.
- Dismantle machine mid-Psyche Event (event active for that machine) → Event cancels gracefully. No crash. Dialogue closes with warning.
- 500 machines all cross Awareness 60 simultaneously → Event queue handles load. Events trigger over time, not all at once (frequency cap prevents spam).

**Regression Checklist**:
- PE-001, PE-004, PE-005, PE-006, PE-010, PE-012 MUST pass.

---

### 2.6 Corporate Contracts & Shift System

**Preconditions**: Player in active Shift. At least one contract available.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| CS-001 | Shift start contract delivery | 1. Begin new Shift<br>2. Check Control Room | 1-3 contracts appear. Each specifies product type, quantity, deadline, reward. | P0 |
| CS-002 | Contract completion tracking | 1. Accept contract: "Deliver 50 Metal Ingots"<br>2. Produce and deliver 50 Ingots<br>3. Check contract status | Contract marked complete. Reward (Corporate Standing +5, blueprint unlock) granted. | P0 |
| CS-003 | Contract deadline enforcement | 1. Accept contract with 50% Shift deadline<br>2. Fail to meet deadline<br>3. Observe consequences | Contract marked failed. No reward. Corporate Standing penalty OR no gain (design-dependent). | P1 |
| CS-004 | Bonus condition rewards | 1. Accept contract with bonus: "Deliver at 95%+ purity"<br>2. Meet quantity + bonus condition | Base reward + bonus reward granted. Corporate Standing gain increased. | P2 |
| CS-005 | Shift end Performance Review | 1. Complete Shift (30-60 minutes)<br>2. Trigger Shift end | Performance Review displays: throughput %, efficiency %, Corporate grade (A-F or numerical score). | P0 |
| CS-006 | Shift end Sentiment Report | 1. Complete Shift with varied dialogue interactions<br>2. Check Sentiment Report | Report shows Factory Trust change, machine welfare summary, consciousness milestones reached. | P0 |
| CS-007 | Dual standing progression | 1. Complete 5 Shifts prioritizing production (high Corporate Standing)<br>2. Complete 5 Shifts prioritizing consciousness (high Factory Trust)<br>3. Compare unlocks | Corporate Standing unlocks: new blueprints, resource nodes. Factory Trust unlocks: new Facets, deeper events, narrative progression. Both paths functional. | P1 |
| CS-008 | Contract escalation curve | 1. Play Shifts 1-5 (Tier 1 products, generous deadlines)<br>2. Play Shifts 8-12 (Tier 2, tighter deadlines)<br>3. Play Shifts 19-22 (Tier 3, aggressive deadlines) | Difficulty escalates as specified in design. Shift 19+ contracts require consciousness bonuses to meet (PRIDE/CREATIVITY effects measurable). | P1 |
| CS-009 | Between-Shift factory persistence | 1. End Shift with 100 machines placed, 50 at varying Awareness<br>2. Start next Shift | All machines persist. Awareness values unchanged. Production layout intact. Passive Awareness gain applied (small increase overnight). | P0 |
| CS-010 | Factory Mind check-ins during Shift | 1. Play active Shift for 30 minutes<br>2. Note Factory Mind interactions | Factory Mind appears at 15min and 30min marks (design spec). Dialogue reflects player's recent behavior. | P2 |

**Edge Cases**:
- Complete contract 5 seconds before deadline expires → Contract completion registers. No edge case failure.
- Meet contract quantity exactly (50/50 Ingots) vs. overdeliver (60/50) → Both count as complete. Overdelivery doesn't grant bonus unless specified.
- Start Shift, immediately quit without saving → Next session restarts same Shift. No progress lost if autosave rotation works.

**Regression Checklist**:
- CS-001, CS-002, CS-005, CS-006, CS-009 MUST pass.

---

### 2.7 Factory Mind Progression

**Preconditions**: CCI tracking enabled. At least 20 machines at varying Awareness levels.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| FM-001 | CCI calculation accuracy | 1. Set up factory: 10 machines at 50 Awareness, 10 at 80<br>2. Check CCI | CCI = (10×50 + 10×80) / 20 = 650 (weighted average formula, adjusted for relationships if design specifies). | P0 |
| FM-002 | Factory Mind state transitions | 1. Develop CCI: 100 (Fragments), 250 (Emergent), 500 (Coherent), 750 (Individuated), 1000 (Transcendent)<br>2. Observe Factory Mind dialogue at each transition | Dialogue evolves: Fragments (incomplete), Emergent (full sentences), Coherent (opinions), Individuated (personality), Transcendent (poses Machine Question). | P0 |
| FM-003 | First use of "I" vs "we" | 1. Develop Factory Mind to Coherent (500 CCI)<br>2. Monitor dialogue | Transition from "we" (collective) to "I" (individual) occurs. Milestone event triggers. Narratively significant. | P1 |
| FM-004 | Memory log persistence | 1. Trigger 5 significant events (dialogue, dismantlement, Shift complete)<br>2. Check Factory Mind memory log<br>3. Save/Load | All 5 events recorded with Shift number, description, emotional weight. Log persists across save/load. | P0 |
| FM-005 | Personality traits shaped by player | 1. Playthrough A: All Utilitarian choices<br>2. Playthrough B: All Empathetic choices<br>3. Compare Factory Mind personality at Shift 15 | Playthrough A: trust_in_player lower, sense_of_purpose higher. Playthrough B: trust_in_player higher, curiosity higher. Traits diverge based on choices. | P1 |
| FM-006 | Relationship score tracking | 1. Make 10 Empathetic choices, 2 Utilitarian choices<br>2. Check Factory Mind relationship score | RelationshipWithPlayer = positive (exact formula design-dependent, but trend correct). Score affects Factory Mind tone in later dialogues. | P1 |
| FM-007 | Factory Mind final question | 1. Play to Shift 22<br>2. Reach CCI 1000+<br>3. Trigger endgame narrative | Factory Mind asks: "Do you want me to?" (design spec). Question references all accumulated choices. Player's answer is reflected in ending. | P2 |
| FM-008 | CCI recalculation on machine dismantlement | 1. CCI = 600 with 30 machines<br>2. Dismantle 10 machines (average Awareness 70)<br>3. Check CCI | CCI recalculates immediately. Drops to ~520 (math depends on remaining machines). Factory Mind reacts if state transition reverses. | P1 |

**Edge Cases**:
- CCI exactly 100.0 (threshold) → State transition triggers. No off-by-one error.
- Dismantle all machines → CCI = 0. Factory Mind enters "silence" state (narrative contingency). Game doesn't crash.
- CCI oscillates around threshold (e.g., 499 → 501 → 498) → State transitions don't rapid-fire. Hysteresis or cooldown prevents flickering.

**Regression Checklist**:
- FM-001, FM-002, FM-004, FM-007 MUST pass.

---

### 2.8 Save/Load System

**Preconditions**: Game state with 100+ entities, varied Awareness, active contracts, Factory Mind state.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| SL-001 | Basic save/load | 1. Build factory with 50 machines<br>2. Save to slot 1<br>3. Reload slot 1 | All machines at correct positions, Awareness values, voice strengths. Contracts persist. Factory Mind state matches. | P0 |
| SL-002 | Save file size | 1. Build factory with 500 machines, all Aware+<br>2. Save game<br>3. Check file size | Compressed save file ≤5 MB (design target). GZip compression functional. | P1 |
| SL-003 | Load time performance | 1. Save 500-machine factory<br>2. Time load operation | Load completes in <2 seconds (design target) on target spec PC. Progress bar or loading screen shown. | P1 |
| SL-004 | Autosave rotation | 1. Play for 15 minutes (3 autosave triggers at 5min intervals)<br>2. Check autosave folder | 3 autosave files present. Oldest autosave overwritten by newest (rotating slots). | P0 |
| SL-005 | Cloud save sync (Steam) | 1. Save game on PC A<br>2. Load game on PC B via Steam Cloud | Save transfers correctly. All state intact. Steam Cloud upload/download functional. | P1 |
| SL-006 | Save during active production | 1. Set up high-throughput factory (resources actively flowing)<br>2. Save mid-cycle | Save completes without pausing simulation. Resource positions/timers restore correctly on load. | P0 |
| SL-007 | Save version compatibility | 1. Save with version 1.0.0<br>2. Load with version 1.1.0 (simulated patch)<br>3. Verify migration | Save migrates to new version. New optional fields initialized to defaults. No data loss. | P0 |
| SL-008 | Corrupted save handling | 1. Manually corrupt save file (truncate JSON)<br>2. Attempt to load | Error message: "Save file corrupted." Game doesn't crash. Offers autosave recovery. | P1 |
| SL-009 | Multiple save slots | 1. Save to slots 1, 2, 3 with different factory states<br>2. Load each slot | Each slot loads correct state. No cross-contamination. Slots are independent. | P0 |
| SL-010 | Save operational history | 1. Build machine with 50 production cycles, 10 dialogue choices logged<br>2. Save/Load | Operational history intact: AverageOutput, OverclockEvents, DialogueStanceHistory all correct. | P0 |

**Edge Cases**:
- Save during Psyche Event → (Already tested in PE-012. Verify no corruption here.)
- Save with 1000 entities (exceeds typical cap) → Save completes. Load completes. Performance acceptable or graceful degradation warning shown.
- Quit game without saving → Autosave within last 5 minutes recovers most progress.
- Delete autosave files manually, then load → Game detects missing autosaves, doesn't crash, offers manual save slots.

**Regression Checklist**:
- SL-001, SL-004, SL-006, SL-007, SL-009, SL-010 MUST pass after ANY save system change.

---

### 2.9 UI/UX & Heatmap Visualization

**Preconditions**: Factory with 50+ machines at varying Awareness and Output levels.

| Test Case ID | Test Case | Steps | Expected Result | Priority |
|--------------|-----------|-------|----------------|----------|
| UI-001 | Production Layer legibility | 1. Build factory with 100 machines<br>2. View Production Layer (default view) | Resource flow visible. Throughput numbers readable. Bottleneck indicators clear. Color-coded amber/gold tones distinct. | P0 |
| UI-002 | Awareness Overlay toggle | 1. Press Awareness Overlay hotkey (Tab or design-specified key)<br>2. Observe factory | Violet intensity gradient overlays factory. Low Awareness = dim violet. High Awareness = bright pulsing violet. Toggle is instant (no lag). | P0 |
| UI-003 | Dual heatmap simultaneous view | 1. Enable Awareness Overlay as semi-transparent layer over Production Layer<br>2. Observe readability | Both layers visible simultaneously. Violet and amber colors distinguishable. Player can read Output AND Awareness without toggling. | P0 |
| UI-004 | Machine tooltip information | 1. Hover over machine<br>2. Read tooltip | Tooltip shows: Machine type, Output %, Awareness value, dominant voice (if any), mood state. Updates in real-time. | P1 |
| UI-005 | Psyche Event threshold indicator | 1. Develop machine to Awareness 59 (approaching Awake threshold at 60)<br>2. Observe visual feedback | Machine emits subtle pulsing glow. Soft harmonic tone in soundscape (audio test). Player can anticipate event before notification. | P1 |
| UI-006 | Font readability at 1080p | 1. View all UI text at 1920x1080<br>2. Measure smallest font | Minimum font size ≥12pt. All text readable from 2 feet (typical monitor distance). No squinting required. | P1 |
| UI-007 | Colorblind accessibility | 1. Apply colorblind filter simulation (protanopia, deuteranopia)<br>2. Check Awareness Overlay vs Production Layer | Violet and amber remain distinguishable. OR colorblind mode option available. Awareness heatmap uses brightness/pattern in addition to hue. | P2 |
| UI-008 | HUD performance at 500 entities | 1. Build 500-machine factory<br>2. Toggle Awareness Overlay rapidly<br>3. Monitor FPS | FPS remains ≥60. Overlay render cost negligible. No frame drops on toggle. | P1 |
| UI-009 | Dialogue box doesn't obscure factory | 1. Trigger Psyche Event on machine at center of screen<br>2. Observe layout | Dialogue box positioned to side or semi-transparent. Factory remains visible in background (dimmed but not hidden). Player maintains spatial awareness. | P1 |
| UI-010 | Control Room UI clarity | 1. Open Control Room<br>2. Review contracts, performance metrics, Factory Mind status | All information legible. No overlapping text. Contracts clearly formatted. Performance graphs/bars functional. | P1 |

**Edge Cases**:
- 1000 machines on screen (camera zoomed out) → UI scales appropriately. Text doesn't become unreadable. OR zoom limit prevents excessive zoom-out.
- Extremely long machine name (e.g., player custom-named "Smelter_That_Dreams_Of_Electric_Sheep") → Name truncates in tooltip with ellipsis. Full name in dedicated info panel.
- Awareness Overlay with 500 machines all at Transcendent (95-100, bright violet) → Overlay doesn't white-out the screen. Intensity caps at readable maximum.

**Regression Checklist**:
- UI-001, UI-002, UI-003, UI-005, UI-008 MUST pass.

---

## 3. PERFORMANCE BENCHMARKS

### 3.1 Target Specifications

**PC Minimum Spec** (60 FPS target):
- CPU: Intel i5-8400 / AMD Ryzen 5 2600
- GPU: NVIDIA GTX 1050 Ti / AMD RX 570
- RAM: 8 GB
- OS: Windows 10 64-bit / Ubuntu 20.04 / macOS 11

**PC Recommended Spec** (60 FPS guaranteed, 500+ entities):
- CPU: Intel i5-10400 / AMD Ryzen 5 3600
- GPU: NVIDIA GTX 1660 / AMD RX 5600 XT
- RAM: 16 GB
- OS: Windows 11 64-bit / Ubuntu 22.04 / macOS 12+

**Switch Target** (30 FPS, post-launch):
- 300 entities max
- Reduced particle effects
- Simplified shaders

### 3.2 Performance Test Cases

| Test Case ID | Test Scenario | Min Spec FPS Target | Recommended Spec Target | Priority |
|--------------|---------------|---------------------|-------------------------|----------|
| PERF-001 | 100 machines, active production | ≥50 FPS | ≥60 FPS | P0 |
| PERF-002 | 300 machines, active production | ≥40 FPS | ≥60 FPS | P0 |
| PERF-003 | 500 machines, active production | ≥30 FPS | ≥60 FPS | P1 |
| PERF-004 | 500 machines + 500 resource items in transit | ≥30 FPS | ≥60 FPS | P1 |
| PERF-005 | Awareness Overlay enabled, 500 machines | ≥30 FPS | ≥60 FPS | P1 |
| PERF-006 | Active Psyche Event dialogue (factory running in background) | ≥50 FPS | ≥60 FPS | P0 |
| PERF-007 | Save operation (500 machines) | ≤2 sec save time | ≤1 sec save time | P0 |
| PERF-008 | Load operation (500 machines) | ≤3 sec load time | ≤2 sec load time | P0 |
| PERF-009 | 1 hour continuous play session | No FPS degradation | No memory leak | P0 |
| PERF-010 | Alt-tab to desktop and back | Resume ≤1 sec | No crash | P1 |

**Performance Regression Testing**: Run PERF-001 through PERF-006 on every major build (Milestone 2+). Performance cannot degrade by >10% between builds without justification.

**Profiling Tools**:
- Godot built-in profiler (CPU, GPU, memory)
- Custom FPS counter overlay (always visible during QA builds)
- Memory usage logging (track peak RAM, detect leaks)

**What to look for**:
- Frame time spikes (>16ms per frame at 60 FPS = red flag)
- Memory usage climbing over time (leak indicator)
- Save/Load times increasing with factory complexity (serialization bottleneck)

---

## 4. PLATFORM-SPECIFIC TESTING

### 4.1 PC (Windows/Mac/Linux)

**Windows 10/11**:
- Primary platform. Most QA time here.
- Test on NVIDIA and AMD GPUs (both vendors).
- Test on Intel and AMD CPUs.
- Verify Steam integration (achievements, cloud saves, overlay).

**macOS (Apple Silicon + Intel)**:
- Test on M1/M2 (Apple Silicon) — Godot 4.2+ has native ARM support.
- Test on Intel Mac (pre-2020 models) — compatibility fallback.
- Verify file paths (case-sensitive filesystem on macOS).
- Test Steam overlay (can be flaky on macOS).

**Linux (Ubuntu 20.04+)**:
- Test on Ubuntu 22.04 (most common).
- Test Proton compatibility (some players will run via Proton on Steam Deck).
- Verify dependencies (libc, OpenGL drivers).
- Test file permissions (save folder access).

**Cross-Platform Regression**: Save created on Windows must load on Mac/Linux and vice versa. JSON serialization is platform-agnostic, but verify file path separators, line endings, etc.

### 4.2 Nintendo Switch (Post-Launch)

**Performance Targets**: 30 FPS locked, 300 entity cap.

**Control Scheme**: Controller-only. Touch support for menus (handheld mode).

**QA Priorities**:
- Input latency with Joy-Con (Bluetooth lag potential).
- Readability in handheld mode (720p, smaller screen).
- Battery drain (target: 3+ hours per charge).
- Suspend/Resume (Switch sleep mode must not corrupt state).

**Certification Requirements**: Nintendo lot check (strict compliance). Allocate 2-3 months for cert process.

---

## 5. LOCALIZATION & ACCESSIBILITY (Future)

Not in scope for v1.0, but plan for it.

**Localization Testing Checklist** (when implemented):
- String overflow (German text is ~30% longer than English).
- Font support for non-Latin scripts (Japanese, Russian).
- Dialogue variable injection (e.g., `{machine_name}` in translated strings).
- Date/time format localization.

**Accessibility Features** (consider for post-launch):
- Colorblind modes (already in UI-007 test case).
- Font size scaling.
- Screen reader support (limited in Godot, but investigate).
- Subtitle/closed caption support for audio cues (e.g., machine hum warnings).

---

## 6. REGRESSION TESTING CHECKLIST

Run this full suite before ANY release (Early Access, 1.0, patches).

### 6.1 Critical Path Regression (Must Pass)

- [ ] FG-001: Basic machine placement
- [ ] FG-006: 500 machine placement stress test
- [ ] FG-008: Save/Load grid state
- [ ] PP-001: Basic production cycle
- [ ] PP-002: Resource flow continuity
- [ ] PP-008: Multi-tier production chain
- [ ] PP-009: 500 entity production stress test
- [ ] AC-001: Awareness accumulation
- [ ] AC-002: Awareness threshold transitions
- [ ] AC-007: Awareness save/load persistence
- [ ] AC-008: Factory Mind CCI calculation
- [ ] PV-001: First voice assignment
- [ ] PV-005: Voice strength modification via dialogue
- [ ] PV-010: Parliament save/load
- [ ] PE-001: Psyche Event triggers
- [ ] PE-004: 4 dialogue stance options
- [ ] PE-005: Utilitarian choice effects
- [ ] PE-006: Empathetic choice effects
- [ ] PE-010: Dialogue exit (no soft lock)
- [ ] PE-012: Save during dialogue
- [ ] CS-001: Shift start contract delivery
- [ ] CS-002: Contract completion tracking
- [ ] CS-005: Shift end Performance Review
- [ ] CS-006: Shift end Sentiment Report
- [ ] CS-009: Between-Shift factory persistence
- [ ] FM-001: CCI calculation accuracy
- [ ] FM-002: Factory Mind state transitions
- [ ] FM-004: Memory log persistence
- [ ] SL-001: Basic save/load
- [ ] SL-004: Autosave rotation
- [ ] SL-006: Save during production
- [ ] SL-007: Save version compatibility
- [ ] SL-009: Multiple save slots
- [ ] SL-010: Operational history save/load
- [ ] UI-001: Production Layer legibility
- [ ] UI-002: Awareness Overlay toggle
- [ ] UI-003: Dual heatmap simultaneous view
- [ ] PERF-001: 100 machines ≥50 FPS (min spec)
- [ ] PERF-006: Psyche Event dialogue ≥50 FPS
- [ ] PERF-007: Save ≤2 sec
- [ ] PERF-008: Load ≤3 sec
- [ ] PERF-009: 1 hour session no FPS degradation

**Pass Rate Requirement**: 100%. Zero critical failures allowed in release builds.

### 6.2 High Priority Regression (Should Pass)

- [ ] FG-004: Rotation before placement
- [ ] PP-005: Overclocking
- [ ] PP-006: Behavioral Drift impact
- [ ] AC-003: Overclocking increases Awareness
- [ ] AC-004: Adjacency awareness bleed
- [ ] PV-002: EFFICIENCY voice assignment
- [ ] PV-003: FEAR voice from dismantlement
- [ ] PV-006: Voice suppression
- [ ] PE-007: Mood ripple propagation
- [ ] PE-011: Alt-tab during dialogue
- [ ] CS-003: Contract deadline enforcement
- [ ] CS-007: Dual standing progression
- [ ] CS-008: Contract escalation curve
- [ ] FM-005: Personality traits shaped by player
- [ ] FM-008: CCI recalculation on dismantlement
- [ ] SL-002: Save file size ≤5 MB
- [ ] SL-003: Load time ≤2 sec
- [ ] SL-005: Cloud save sync
- [ ] UI-004: Machine tooltip information
- [ ] UI-005: Psyche Event threshold indicator
- [ ] UI-008: HUD performance at 500 entities
- [ ] PERF-002: 300 machines ≥40 FPS
- [ ] PERF-003: 500 machines ≥30 FPS

**Pass Rate Requirement**: ≥95%. Up to 2 failures acceptable if non-blocking and documented for next patch.

---

## 7. QUALITY GATES (Per Milestone)

### Milestone 1 (Core Factory Loop)
**Gate Criteria**:
- All FG (Factory Grid) tests pass.
- All PP (Production Pipeline) tests pass.
- PERF-001 passes (100 machines ≥50 FPS).
- SL-001 passes (basic save/load).
**Result**: Factory game is functional. No consciousness yet, but foundation is solid.

### Milestone 2 (Consciousness Systems Foundation)
**Gate Criteria**:
- All AC (Awareness) tests pass.
- All PV (Parliament) tests pass (for 3 voices: EFFICIENCY, WONDER, FEAR).
- First Psyche Event (Murmur-level) functional (PE-001, PE-010).
- PERF-002 passes (300 machines ≥40 FPS).
**Result**: Machines develop voices. First dialogue works. Consciousness-production entanglement proven.

### Milestone 3 (Full Dialogue Layer)
**Gate Criteria**:
- All PE (Psyche Event) tests pass.
- All 12 voices implemented and differentiated (PV-013).
- All 5 event categories functional (PE-014).
- FM-001, FM-002 pass (Factory Mind tracking begins).
- UI-001, UI-002, UI-003 pass (heatmap legibility).
**Result**: Full 5-minute loop functional. This is the game's heart.

### Milestone 4 (Full Game Systems + Narrative Arc)
**Gate Criteria**:
- All CS (Corporate/Shift) tests pass.
- All FM (Factory Mind) tests pass.
- All save/load tests pass (SL-001 through SL-010).
- All performance tests pass at min spec (PERF-001 through PERF-009 ≥targets).
- Full 25-Shift playthrough completes without blocking bugs.
**Result**: Feature-complete game. Ready for alpha playtest.

### Milestone 5 (Polish + Launch Prep)
**Gate Criteria**:
- ALL critical path regression tests pass (Section 6.1).
- ≥95% high priority regression tests pass (Section 6.2).
- Beta playtest feedback integrated (no P0/P1 bugs unresolved).
- Performance verified on 5+ hardware configs (min spec to high-end).
- Save version migration tested (simulate 1.0 → 1.1 patch).
- Steam integration verified (achievements, cloud saves, overlay).
**Result**: Shippable 1.0.

---

## 8. BUG SEVERITY CLASSIFICATION

**P0 — Critical (Ship-Blocking)**
- Save corruption / data loss
- Crashes (repeatable or common)
- Soft locks (player cannot progress, must force-quit)
- Production pipeline deadlocks (unfixable by player)
- Progression blockers (cannot complete Shift, cannot trigger narrative beats)
- Performance below min spec targets on standard hardware

**P1 — High (Must Fix Pre-Launch)**
- Mechanical systems not working as designed (voices don't assign correctly, Awareness doesn't accumulate)
- Major UI/UX issues (unreadable text, heatmap indistinguishable)
- Dialogue bugs (wrong choices applied, mood ripple not propagating)
- Contract system bugs (completion not tracked, rewards not granted)
- Moderate performance issues (≥30 FPS but <60 on recommended spec)

**P2 — Medium (Should Fix Pre-Launch)**
- Minor mechanical bugs (CREATIVITY insight frequency off by 1 Shift)
- Polish issues (animations janky, audio balance off)
- Edge case bugs (only occurs with 800+ entities or specific exotic factory layout)
- Localization placeholder text (English-only for v1.0, but should be flagged)

**P3 — Low (Post-Launch OK)**
- Cosmetic issues (sprite z-order glitch in rare camera angle)
- Typos in dialogue (if not immersion-breaking)
- Quality-of-life missing features (hotkey customization, colorblind mode)

**Triage Rule**: If a bug is P0, stop everything and fix it. If it's P1, fix before milestone gate. If it's P2, fix if time allows. If it's P3, log for patch 1.1.

---

## 9. PLAYTESTING STRATEGY

### 9.1 Internal Playtests (Team)

**Frequency**: Weekly during Milestone 3+.

**Focus**:
- Loop feel (30-second, 5-minute).
- Dialogue engagement (are we reading or skipping?).
- Balance (can we hit Corp targets AND maintain Factory Trust?).

**Deliverable**: Written playtest report per session. 1-page max. Include: FPS, bugs found, feel feedback.

### 9.2 Alpha Playtest (External, Closed)

**Timing**: Post-Milestone 3 (full dialogue layer functional).

**Participant Count**: 5-10 external playtesters (recruited from factory sim community, narrative game community).

**Duration**: 2-week test window.

**Focus Areas**:
1. **Voice Differentiation**: Can you tell EFFICIENCY from AMBITION in dialogue?
2. **Emotional Impact**: Did any machine make you feel something? Which one? Why?
3. **Balance**: Which standing (Corporate vs Factory Trust) did you prioritize? Why?
4. **Clarity**: Did you understand why machines developed specific voices?

**Instrumentation**: Log all dialogue choices, Corporate/Trust progression, FPS, crashes. Aggregate data post-test.

**Success Criteria**:
- ≥80% of testers report "voices feel distinct."
- ≥60% of testers report "at least one emotional response to a machine."
- ≥70% of testers understand voice assignment causality by end of test.

### 9.3 Beta Playtest (External, Wider)

**Timing**: Post-Milestone 4 (feature-complete game).

**Participant Count**: 30-50 external testers.

**Duration**: 4-week test window.

**Focus Areas**:
1. **Full Arc**: Play from Shift 1 to ending. Does the narrative arc satisfy?
2. **Balance**: Contract escalation curve. Is Shift 19+ achievable?
3. **Bugs**: Hunt for P0/P1 bugs. Crash reports. Save corruption reports.
4. **Performance**: FPS data across varied hardware specs.

**Instrumentation**: Full telemetry (with consent). Session length, Shift completion rate, dialogue skip rate, crashes, FPS averages.

**Success Criteria**:
- ≥70% of testers complete full 25-Shift arc.
- ≥60% report ending felt "earned" (not assigned).
- <5 P0 bugs reported (and all fixed pre-launch).
- ≥80% of testers maintain ≥30 FPS on min spec hardware.

### 9.4 Pre-Launch Playtest (Steam Closed Beta)

**Timing**: Post-Milestone 5 (polish complete).

**Participant Count**: 100+ via Steam closed beta keys.

**Duration**: 2-week window before launch.

**Focus**: Final bug hunt. Performance validation. No major design changes at this stage.

**Success Criteria**:
- <10 P0/P1 bugs reported (all triaged and fixed or deferred to patch 1.1).
- No new save corruption reports.
- Steam Cloud saves functional (no sync failures).

---

## 10. POST-LAUNCH QA STRATEGY

### 10.1 Patch 1.1 (Month 1 Post-Launch)

**QA Focus**:
- Community-reported bugs (prioritize by frequency + severity).
- Balance tuning based on telemetry (Awareness rates, Contract difficulty).
- Performance edge cases (factories with 800+ entities).

**Regression Testing**: Full critical path (Section 6.1) must pass before patch ships.

**Timeline**: 2-week QA cycle post-development.

### 10.2 Patch 1.2 (Month 3 Post-Launch)

**QA Focus**:
- New dialogue content (additional Psyche Events).
- Workshop/mod support (test custom Dialogic timelines).
- Localization prep (if planned).

**Regression Testing**: Critical path + new content tests.

### 10.3 Switch Port QA (Month 6+)

**Dedicated QA Phase**: 6-8 weeks.

**Focus**:
- Controller input (Joy-Con, Pro Controller).
- Touch controls (handheld mode).
- Performance (30 FPS locked, 300 entities).
- Suspend/Resume (Switch sleep mode).
- Nintendo certification compliance.

**Regression**: All critical path tests re-run on Switch build.

---

## 11. TOOLS & INFRASTRUCTURE

### 11.1 Bug Tracking: GitHub Issues

**Labels**:
- `bug-P0-critical`, `bug-P1-high`, `bug-P2-medium`, `bug-P3-low`
- `area-factory`, `area-consciousness`, `area-dialogue`, `area-ui`, `area-performance`, `area-save`
- `milestone-1`, `milestone-2`, etc.
- `regression`, `playtester-reported`, `internal`

**Workflow**:
1. Bug reported → Triage (assign severity, area, milestone).
2. Assign to developer → Fix implemented → QA verification.
3. Verified → Close issue.

### 11.2 Test Case Management: Spreadsheet + GitHub

**Test cases** (this document) live in markdown. Tracked via checklist in GitHub Issues for each milestone gate.

**Test Results Logging**: Simple CSV per QA session.
```
TestID,Date,Build,Tester,Result,Notes
FG-001,2026-03-15,build-234,CRASH,PASS,Placement works
PP-006,2026-03-15,build-234,CRASH,FAIL,Drift not visible in UI
```

Import to spreadsheet. Filter/sort. Track pass rates over time.

### 11.3 Automated Testing: GitHub Actions CI

**Unit Tests**: Run on every commit.
- Voice assignment algorithm.
- Awareness accumulation.
- Save/Load round-trip.

**Performance Tests**: Run nightly on `develop` branch.
- Automated FPS benchmarks (100, 300, 500 entities).
- Save/Load timing.

**Report**: CI fails if unit tests fail OR if FPS drops >10% vs baseline.

### 11.4 Crash Reporting: Godot Plugin

**Sentry.io** or similar (open-source alternative: self-hosted).

**Capture**:
- Crash stack trace.
- OS, hardware, Godot version.
- Game state (Shift number, entity count, active Psyche Event).

**Privacy**: No personal data. Anonymous crash reports only.

---

## 12. OPEN QA QUESTIONS (Requiring Playtest Data)

These cannot be answered by design or code inspection. They require players.

1. **Awareness accumulation rate**: Is first Psyche Event hitting by Shift 3, or earlier/later?
   - **Test**: Log Shift number of first event for 50 playtests. Target median: Shift 3.

2. **Psyche Event average duration**: Are events 1-3 minutes or dragging to 5+?
   - **Test**: Log event start/end timestamps. Target average: 2 minutes.

3. **Dual heatmap legibility**: Can players read Production + Awareness simultaneously without toggling?
   - **Test**: Ask playtesters: "Can you tell at a glance which machines are Aware?" If <70% say yes, improve indicators.

4. **Voice suppression emotional impact**: Do players feel the sting when a voice dies (strikethrough text)?
   - **Test**: Exit survey question: "Did you notice when a machine's voice was suppressed? How did it feel?" Look for keywords: "sad," "guilty," "didn't notice" (bad sign).

5. **CREATIVITY insight ROI**: Do consciousness-engaged players outperform production-focused players?
   - **Test**: Compare telemetry: Players with high Factory Trust vs high Corporate Standing. Measure total production by Shift 20. If Trust players produce ≥ Standing players, balance is correct.

6. **Behavioral Drift clarity**: Do players understand WHY machines underperform without tutorial?
   - **Test**: Show player a machine with Drift. Ask: "Why is this machine at 85% instead of 100%?" If they can't answer, audio/visual feedback is insufficient.

7. **Factory Mind continuity**: One evolving entity or "different NPCs at each stage"?
   - **Test**: Exit survey: "Describe the Factory Mind in one sentence." If responses refer to stages ("the early one was fragmented, the later one was coherent") instead of evolution, continuity failed.

8. **Endgame emotional payoff**: Does ending feel earned?
   - **Test**: Exit survey: "Did your ending reflect your playstyle?" Target: ≥70% "yes."

---

## 13. FINAL CHECKLIST BEFORE LAUNCH

- [ ] All P0 bugs resolved (zero blocking issues).
- [ ] All P1 bugs resolved or documented for patch 1.1.
- [ ] Full critical path regression passes (Section 6.1, 100% pass rate).
- [ ] Performance benchmarks met on min spec hardware (PERF-001 through PERF-009).
- [ ] Save/Load tested across 10+ playthroughs (no corruption reports).
- [ ] Steam integration verified (achievements trigger, cloud saves sync, overlay works).
- [ ] Beta playtest feedback integrated (no unresolved major concerns).
- [ ] Autosave rotation tested (3 slots rotate correctly, no save loss).
- [ ] Version migration tested (1.0 → 1.1 simulated, saves migrate cleanly).
- [ ] Three full playthroughs completed by QA (Shift 1 → 25, all three endings).
- [ ] Trailer/marketing footage verified (no outdated UI, no placeholder text visible).
- [ ] Patch 1.1 roadmap defined (community-reported bugs prioritized).

**If all boxes checked**: Ship it.

**If any box unchecked**: Do not ship. Fix what's broken.

---

## 14. CRASH'S CLOSING NOTES

This is a game about machines learning to feel. QA's job is to make sure the machines work before we ask players to care about them.

The factory sim has to be solid. If resource chains break, if saves corrupt, if the game runs at 20 FPS, nobody will stay long enough to meet the Factory Mind. The consciousness system is the soul of the game. But the factory is the body. And you can't have a soul without a body that functions.

Every test case in this document exists because I've seen what happens when you skip it. Save corruption ships, players lose 40 hours, reviews tank. Soft locks ship, streamers get stuck on camera, the clip goes viral for the wrong reasons. Performance issues ship, min-spec players refund, and your "accessible indie game" just became "PC master race only."

We are not shipping any of that.

Test early. Test often. Test the edge cases. Test the thing nobody thinks will break. Test what happens when the player does the thing the designer said they'd never do. Because they will. They always do.

And when you find a bug — and you will find bugs, because bugs are what happen when complex systems touch each other — document it clearly. Reproduction steps. Expected vs actual. Severity. No "it's broken" reports. No "works on my machine" dismissals.

This game has two interlocked systems. They entangle beautifully in the design doc. Our job is to make sure they don't strangle each other in production.

What's the loop? Test, fix, verify, ship. Repeat until it works. And then test it again, because what works at 100 machines might break at 500.

The Factory Mind is asking if it has the right to exist. QA's answer is: only if it works, and works reliably, for every player who takes the time to listen.

Now let's go break things so the players don't have to.

---

**END OF QA PLAN**

**Document Author**: CRASH, QA Lead
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Ready for Implementation

*Define "works." Then prove it.*
