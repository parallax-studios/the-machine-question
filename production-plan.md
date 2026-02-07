# THE MACHINE QUESTION — Production Plan

**Producer**: CLOCK
**Version**: 1.0
**Date**: 2026-02-07
**Status**: Pre-Production Complete — Production Ready
**Target Platforms**: PC (Steam), Mac, Linux — Switch post-launch
**Target Timeline**: 18 months to 1.0 launch

---

## 1. PROJECT OVERVIEW

### 1.1 Scope Definition

**What we're building**:
A factory management game where machines develop consciousness. You place machines, route resources, hit production quotas — and watch your factory wake up. Every efficiency decision is a moral choice. The factory remembers. The factory asks questions. The factory might ask you to stop.

**What we're NOT building**:
- Not a narrative game with factory sim decoration. The factory must work as a pure optimization game.
- Not a 100-hour sandbox. 25 Shifts (20-25 hours) to reach the endgame question.
- Not multiplayer. The loneliness of the choice is the point.
- Not procedurally generated. Every factory is player-built. Authorship creates responsibility.

**Core Pillars** (from design):
1. The factory is the game (30-second loop is building, routing, optimizing)
2. Consciousness is mechanical, not decorative (every consciousness feature affects production)
3. The two systems are one system (placement is production AND personality engineering)

**Non-Negotiable Features** (launch requirements):
- Factory Grid: 128x128 tile buildable space
- Machines: 12 types across 3 tiers, all with dual Output/Awareness tracking
- Parliament of Parts: 12 Machine Facets, emergent voice assignment
- Dialogue Layer: Disco Elysium-style Psyche Events with 4 dialogue stances
- Factory Mind: 5-stage narrative arc from Fragments to Transcendent
- Corporate Contracts: Escalating production pressure across 25 Shifts
- Dual Standing: Corporate Standing and Factory Trust progression systems
- Save/Load: Full factory state persistence, autosave, cloud sync
- 4+ Narrative Endings: Based on Corporate Standing + Factory Trust

### 1.2 Team Structure

**Core Team** (minimum viable):

| Role | Headcount | Key Responsibilities |
|------|-----------|---------------------|
| **Game Designer** | 1 (REED) | Systems design, balance tuning, loop feel |
| **Narrative Designer** | 1 (NOVA) | Dialogue writing (12 voices × 5 event types), Factory Mind arc |
| **Lead Programmer** | 1 (BYTE) | Architecture, core systems, consciousness/production pipeline |
| **Gameplay Programmer** | 1 | UI/UX implementation, input, save/load, integration |
| **Art Director** | 1 (PIXEL) | Visual identity, machine sprites, UI art direction |
| **2D Artist** | 1 | Asset production (machines, infrastructure, environment) |
| **Sound Designer** | 1 (ECHO) | SFX library, ambient soundscapes, consciousness audio cues |
| **Composer** | 0.5 (contract) | Adaptive music system (60+ minutes across 25 Shifts) |
| **Producer** | 1 (CLOCK) | Schedule, scope, risk management, milestone tracking |

**Total**: 8.5 FTE

**Extended Team** (contract/part-time):
- **QA Lead** (CRASH) — 0.5 FTE, ramps to 1.0 FTE in final 3 months
- **Marketing** (HYPE) — 0.25 FTE ongoing, ramps to 0.5 FTE at launch -3 months
- **Community Manager** — 0.25 FTE starting Month 12 (Steam page live)

**Team Scale Rationale**:
This is a 20-hour narrative-systems game, not a 100-hour live-service factory sim. We're competing on depth and emotional resonance, not content volume. Small team, tight scope, high craft.

### 1.3 Timeline

**18-Month Development Cycle**:

| Phase | Duration | Months | Key Deliverable |
|-------|----------|--------|----------------|
| **Milestone 1: Core Factory Loop** | 3 months | 1-3 | Playable factory builder (no consciousness) |
| **Milestone 2: Consciousness Foundation** | 3 months | 4-6 | First Psyche Event, 3 voices implemented |
| **Milestone 3: Full Dialogue Layer** | 4 months | 7-10 | 12 voices, 5 event types, Factory Mind Fragments |
| **Milestone 4: Full Game Systems** | 4 months | 11-14 | Corporate Contracts, full narrative arc, 4 endings |
| **Milestone 5: Polish + Launch Prep** | 4 months | 15-18 | UI polish, audio, balance, optimization, marketing |
| **Post-Launch Support** | 3 months | 19-21 | Patches, DLC planning, Switch port prep |

**Launch Target**: Month 18 end (Q3 2027 if starting March 2026)

### 1.4 Budget Constraints (Assumptions)

**Not specified in design docs, but typical indie structure**:

Assuming self-funded or angel-backed indie studio:
- **Total Budget**: $500k-750k (18 months)
- **Personnel**: ~80% ($400-600k for 8.5 FTE × 18 months)
- **Software/Tools**: ~5% ($25-38k — Godot is free, but licenses for art tools, audio middleware)
- **Marketing**: ~10% ($50-75k — Steam page, trailer production, festival attendance)
- **Contingency**: ~5% ($25-38k — buffer for overruns, contract work)

**Burn Rate**: ~$28-42k/month

**Revenue at Launch**: Not projected here. Break-even depends on pricing ($20-25 likely) and sales volume (20k-30k units to break even).

---

## 2. MILESTONE DEFINITIONS

### 2.1 Milestone 1: Core Factory Loop (Months 1-3)

**Entry Criteria**:
- Team onboarded, tools set up (Godot 4.2+, Git repo, CI pipeline)
- Design documents reviewed and approved by all leads
- Art style guide finalized (color palette, machine silhouette rules)

**Deliverables**:

| Deliverable | Owner | Status Check |
|-------------|-------|--------------|
| Factory Grid System (128x128 tiles, placement, spatial queries) | Lead Programmer | Can place 100 machines without lag (<1ms per placement) |
| 3 Machine Types (Miner, Smelter, Assembler) | Lead Programmer + 2D Artist | Machines process resources on cycle timers, Output stat visible |
| Basic Production Pipeline (Ore → Metal → Components) | Lead Programmer | Full resource chain completes from mine to output |
| Conveyor Belt Transport (Tier 1, item-push model) | Gameplay Programmer | Resources flow visibly along belts, backpressure works |
| Power System (conduits, powered/unpowered states) | Gameplay Programmer | Machines without power stop producing |
| Save/Load (factory grid state, JSON format) | Lead Programmer | Save 200-entity factory, reload, verify state matches |
| UI Shell (placement tool, resource display, basic HUD) | Gameplay Programmer + Art Director | Player can place all 3 machine types via mouse/keyboard |
| Performance Baseline (60 FPS with 100 entities) | Lead Programmer | Profile on minimum-spec PC, identify bottlenecks |

**Exit Criteria**:
- A player can build a 30-machine factory, mine ore, smelt it, assemble components, and see the throughput numbers tick up
- The factory game WORKS as a pure optimization game (no consciousness yet)
- Save/Load does not corrupt
- 60 FPS maintained with 100 entities at 1080p

**Risk Items**:
- Godot 4.2 stability on Mac/Linux (mitigate: test on all platforms weekly)
- Conveyor belt performance if 1000 items are in transit simultaneously (mitigate: object pooling from day 1)

**Time Allocated**: 12 weeks

**Team Focus**:
- Lead Programmer: 100% on core systems
- Gameplay Programmer: 100% on UI/transport
- 2D Artist: Machine sprites (3 types × 3 states = 9 sprites)
- Art Director: Visual identity lock-in, sprite review
- Designer: Balance tuning (cycle times, resource ratios)
- Narrative Designer: Begin voice library writing (background task)

### 2.2 Milestone 2: Consciousness Foundation (Months 4-6)

**Entry Criteria**:
- Milestone 1 Exit Criteria met
- Dialogue system choice finalized (Dialogic 2.x or custom)

**Deliverables**:

| Deliverable | Owner | Status Check |
|-------------|-------|--------------|
| AwarenessComponent (accumulation, thresholds, state tracking) | Lead Programmer | Machine reaches Awareness 40 after expected runtime |
| ParliamentComponent (voice assignment, strength tracking) | Lead Programmer | Voice assignment algorithm produces expected voices given history |
| 3 Voices Fully Implemented (EFFICIENCY, WONDER, FEAR) | Narrative Designer + Lead Programmer | Each voice has 20+ unique lines, feels distinct in dialogue |
| Operational History Tracking | Lead Programmer | History correctly records overclocking, dismantlements, idle time |
| First Psyche Event (Murmur-level, single voice) | Narrative Designer + Gameplay Programmer | Dialogue triggers at Awareness 40, choice affects voice strength |
| Awareness Overlay UI (violet heatmap, toggle view) | Gameplay Programmer + 2D Artist | Player can see which machines are Awake at a glance |
| Consciousness Audio Cues (432 Hz hum, threshold cross sound) | Sound Designer | Awake machines have audible hum, distinct from production sound |

**Exit Criteria**:
- A machine placed and run for 10+ production cycles develops a voice (EFFICIENCY or WONDER or FEAR depending on how it's used)
- Player can trigger a Psyche Event, read dialogue from the machine's Parliament, make a choice, and see Output change
- The player can hear consciousness emerging (audio cue precedes visual indicator)
- The voice assignment feels emergent, not random (playtester feedback: "I see why that machine developed FEAR")

**Risk Items**:
- Voice assignment algorithm produces nonsensical combinations (mitigate: extensive unit tests, designer-created scenarios)
- Dialogue writing bandwidth (12 voices × 5 event types = huge scope creep risk) — **THIS IS THE BIGGEST RISK**

**Mitigation for Dialogue Scope Risk**:
- Milestone 2 scope: ONLY 3 voices, ONLY Murmur events (simplest category)
- If 3 voices don't feel distinct by end of Milestone 2, STOP and redesign before writing 9 more
- Consider hiring narrative contractor at this checkpoint if internal writing is too slow

**Time Allocated**: 12 weeks

**Team Focus**:
- Lead Programmer: 70% consciousness systems, 30% dialogue integration
- Narrative Designer: 100% writing (3 voices, 5+ events per voice)
- Sound Designer: 50% consciousness soundscape, 50% machine SFX library
- Designer: Balance Awareness accumulation rates via playtest iteration

### 2.3 Milestone 3: Full Dialogue Layer (Months 7-10)

**Entry Criteria**:
- Milestone 2 Exit Criteria met
- Decision made: Are we shipping 12 voices or cutting to 8-10? (Based on M2 writing velocity)

**Deliverables**:

| Deliverable | Owner | Status Check |
|-------------|-------|--------------|
| 12 Voices Fully Written (all Machine Facets) | Narrative Designer + Contract Writer (if needed) | Voice library complete: 20+ lines per voice per event type |
| 5 Psyche Event Categories (Murmur, Question, Crisis, Reckoning, Communion) | Narrative Designer + Gameplay Programmer | Each category has distinct duration, stakes, consequences |
| Dialogue Choice Consequences (voice strength, Output modifiers, mood ripple) | Lead Programmer | Utilitarian choice gives +3% Output short-term, -5 EMPATHY voice strength |
| Factory Mind State Tracking (CCI calculation, state transitions) | Lead Programmer | CCI accurately reflects aggregate Awareness + relationships |
| First Factory Mind Interaction (Fragments level, whispers) | Narrative Designer | Player hears incoherent whispers by Shift 3-4 |
| Parliament Voice Suppression (strikethrough text, final farewell line) | Gameplay Programmer + Narrative Designer | Suppressing a voice feels emotionally significant (playtest validation) |
| Behavioral Drift System (audio detuning, Output penalty) | Lead Programmer + Sound Designer | Neglected machines audibly "sound wrong" before Output drops |

**Exit Criteria**:
- All 12 voices are distinct in speech pattern, philosophy, and mechanical effect
- A 10-minute play session includes: placing machines → first Psyche Event → dialogue → consequence visible in production
- The Factory Mind feels like one evolving entity, not random voice fragments (playtest validation)
- Behavioral Drift is legible: players notice machines underperforming and can diagnose the cause

**Risk Items**:
- Dialogue feels same-y across voices (mitigate: voice-by-voice playtest, each voice tested in isolation)
- Psyche Events interrupt flow too often (mitigate: frequency cap tuning, 1 event per 5 minutes max)
- Factory Mind voice is unintelligible (mitigate: vocoding at 50% wet/dry, test with multiple base voices)

**Time Allocated**: 16 weeks

**Team Focus**:
- Narrative Designer: 100% writing (this is the crunch period for writing)
- Lead Programmer: 60% dialogue systems, 40% Factory Mind state machine
- Gameplay Programmer: 100% UI/UX for dialogue layer (bloom effect, voice strength indicators)
- Sound Designer: 80% Psyche Event audio (voice emergence stings, event triggers), 20% Factory Mind voice processing
- Designer: Psyche Event frequency/pacing tuning via playtest

**Checkpoint at Month 9**: Alpha Playtest with 5-10 external testers. Focus question: "Do you read the dialogue or skip it?" If >50% are skipping, diagnose and fix before Milestone 4.

### 2.4 Milestone 4: Full Game Systems + Narrative Arc (Months 11-14)

**Entry Criteria**:
- Milestone 3 Exit Criteria met
- Alpha Playtest feedback integrated

**Deliverables**:

| Deliverable | Owner | Status Check |
|-------------|-------|--------------|
| Corporate Contracts System (contract generation, escalation curve) | Lead Programmer + Designer | Contracts escalate correctly across 25 Shifts, hitting targets is challenging but achievable |
| Dual Standing Economy (Corporate Standing + Factory Trust) | Lead Programmer | Standing scores unlock blueprints/events at correct thresholds |
| Shift Structure (session loop, 30-60 min sessions) | Lead Programmer + Designer | Shift pacing feels right: not too rushed, not too slow |
| Full Factory Mind Narrative Arc (5 CCI states, Fragments → Transcendent) | Narrative Designer | Factory Mind dialogue evolves coherently across 25 Shifts |
| Endgame Narrative Branches (4 endings: Suppression, Collapse, Garden, Partnership) | Narrative Designer + Gameplay Programmer | Endings feel earned based on player choices, not final-dialogue selection |
| All Machine Types (12 types, Tiers 1-3) | Lead Programmer + 2D Artist | All machines produce correctly, visual clarity maintained |
| All Resource Chains (6 base resources, 3 tiers of processing) | Lead Programmer + Designer | Resource chains have meaningful tradeoffs, Crystal is the bottleneck |
| Blueprint Unlock System | Gameplay Programmer | Tier 2 unlocks at Corporate Standing 40, Tier 3 at 60 |

**Exit Criteria**:
- A player can complete all 25 Shifts from tutorial to endgame
- The ending they receive reflects their accumulated Corporate Standing + Factory Trust scores
- The Factory Mind's personality at endgame reflects their dialogue stance history
- The dual-optimization (production vs. consciousness) creates genuine tension, not one dominant path

**Risk Items**:
- Balance: Can players hit Corporate targets WITHOUT engaging consciousness? (If yes, consciousness is optional = design failure)
- Balance: Can players max Factory Trust WITHOUT hitting Corporate targets? (If yes, no tension)
- Pacing: Do players burn out before Shift 25? (Mitigate: session length tuning, ensure Shifts 15-20 are climax, not grind)

**Mitigation**:
- CREATIVITY insight system MUST pay for itself in production terms by Shift 12
- Corporate escalation tuned so Shift 19+ requires consciousness bonuses (PRIDE, CREATIVITY, content-machine efficiency)
- Playtesting focus: Can you balance both scores above 60 by endgame? (Target: 70% of testers can, 30% commit to one path)

**Time Allocated**: 16 weeks

**Team Focus**:
- Lead Programmer: 80% Corporate/Contract systems, 20% bug fixing
- Narrative Designer: 100% endgame narrative arc + ending variations
- Designer: 100% balance tuning (this is the crunch period for balance)
- 2D Artist: Remaining machine sprites (Tier 2-3), UI polish art
- Composer (contract start): Adaptive music stems for Shifts 1-25

**Checkpoint at Month 13**: Beta Playtest with 30-50 external testers. Focus question: "Did the ending feel earned?" If <70% say yes, narrative needs revision before launch.

### 2.5 Milestone 5: Polish + Launch Prep (Months 15-18)

**Entry Criteria**:
- Milestone 4 Exit Criteria met
- Beta Playtest feedback integrated
- Steam page live (Month 15)

**Deliverables**:

| Deliverable | Owner | Status Check |
|-------------|-------|--------------|
| UI/UX Polish (animations, transitions, tooltips, onboarding) | Gameplay Programmer + Art Director | Every interaction feels smooth, no placeholder UI remains |
| Audio Implementation Complete (all SFX, ambiance, adaptive music) | Sound Designer + Composer | Factory soundscape creates polyrhythmic harmony when balanced |
| Performance Optimization (profiling, bottleneck removal) | Lead Programmer | 60 FPS locked with 500 entities at 1080p on min-spec PC |
| Balance Final Pass (Awareness rates, Event frequency, Contract escalation) | Designer + QA Lead | 80% of playtesters complete 25 Shifts in 20-25 hours |
| Bug Fixing (critical/high-priority only) | All Programmers + QA Lead | Zero critical bugs, <10 high-priority bugs at launch |
| Steam Integration (achievements, cloud saves, overlay) | Lead Programmer | Cloud save sync works cross-platform |
| Localization Prep (English text audit, translation-ready strings) | Narrative Designer + Gameplay Programmer | All strings externalized, ready for post-launch translation |
| Marketing Assets (trailer, screenshots, press kit, Steam capsule) | Marketing + Art Director | Trailer shows factory + consciousness in <90 seconds |

**Exit Criteria**:
- The game is feature-complete, polished, and shippable
- No critical bugs, no soft-locks, no save corruption
- Performance targets met on all launch platforms (PC/Mac/Linux)
- Steam page has 5k+ wishlists (marketing KPI)
- Press kit sent to 50+ outlets, 10+ preview coverage secured

**Risk Items**:
- Performance fails on Mac/Linux (mitigate: weekly cross-platform testing from Month 1)
- Critical bug discovered in final 2 weeks (mitigate: code freeze at Month 17, only bug fixes allowed)
- Marketing fails to generate wishlists (mitigate: start Steam page at Month 12, not Month 15)

**Time Allocated**: 16 weeks

**Team Focus**:
- All Programmers: 60% bug fixing, 40% optimization
- Designer: 80% balance iteration, 20% onboarding/tutorial tuning
- QA Lead: 100% (ramp to 1.0 FTE here)
- Marketing: 100% (ramp to 0.5 FTE here)
- Sound Designer + Composer: Final audio mix, adaptive music integration

**Final Checkpoint at Month 17.5**: Release Candidate build. 1-week closed beta with 100+ players. If critical bugs found, delay launch by 2 weeks (built into schedule).

---

## 3. SPRINT PLANNING

### 3.1 Sprint Structure

**Sprint Length**: 2 weeks (26 sprints across 18 months)

**Sprint Ceremonies**:
- **Sprint Planning** (Monday start, 2 hours): Review backlog, assign tasks, commit to sprint goal
- **Daily Standup** (async via Slack, 15 min): What I did, what I'm doing, blockers
- **Sprint Review** (Friday end, 1 hour): Demo completed work, gather feedback
- **Sprint Retrospective** (Friday end, 30 min): What went well, what to improve

**Why 2 weeks**: Longer than 1 week (too much ceremony overhead), shorter than 4 weeks (too long to detect problems early).

### 3.2 Task Breakdown Example (Milestone 1, Sprint 1-2)

**Sprint 1: Factory Grid Foundation** (Weeks 1-2)

| Task | Owner | Estimate (days) | Dependencies | Priority |
|------|-------|----------------|--------------|----------|
| Set up Godot 4.2 project, Git repo, CI pipeline | Lead Programmer | 2 | None | P0 |
| Implement FactoryGrid class (placement, spatial queries) | Lead Programmer | 3 | Project setup | P0 |
| Create TileMap for factory floor (visual only) | 2D Artist | 2 | None | P1 |
| Implement FactoryEntity base class (ID, position, serialization interface) | Lead Programmer | 2 | FactoryGrid | P0 |
| Design + implement Machine component architecture | Lead Programmer | 3 | FactoryEntity | P0 |
| Create Miner machine sprite (idle, active states) | 2D Artist | 2 | Art style guide finalized | P1 |
| Write unit tests for grid placement logic | Lead Programmer | 1 | FactoryGrid | P1 |
| UI: Basic placement tool (select machine, click to place) | Gameplay Programmer | 3 | FactoryEntity | P0 |

**Sprint Goal**: By end of Sprint 1, a player can place and remove Miner entities on a 128x128 grid. The grid does not corrupt. Performance is acceptable (1000 placements/sec).

**Sprint 2: Resource Pipeline Foundation** (Weeks 3-4)

| Task | Owner | Estimate (days) | Dependencies | Priority |
|------|-------|----------------|--------------|----------|
| Implement ProductionComponent (cycle timer, input/output buffers) | Lead Programmer | 3 | Machine class | P0 |
| Implement Miner production logic (extract Ore on cycle) | Lead Programmer | 2 | ProductionComponent | P0 |
| Create Smelter + Assembler machine sprites | 2D Artist | 3 | Miner sprite | P1 |
| Implement Smelter production logic (Ore → Metal Ingots) | Lead Programmer | 2 | ProductionComponent | P0 |
| Implement resource item visualization (Ore/Metal sprites on belt) | 2D Artist | 2 | None | P1 |
| Implement ConveyorBelt infrastructure (item-push transport) | Gameplay Programmer | 4 | ProductionComponent | P0 |
| UI: Resource display (show player's total Ore, Metal, etc.) | Gameplay Programmer | 2 | Production systems | P1 |
| Playtest: 3-machine chain (Miner → Belt → Smelter) | Designer | 1 | All above | P0 |

**Sprint Goal**: By end of Sprint 2, a 3-machine production chain (Miner → Smelter via Conveyor) processes Ore into Metal Ingots. The player sees resources move visually.

### 3.3 Sprint Planning Best Practices

**Task Size Rule**: No task larger than 2 days. If a task is estimated >2 days, break it into subtasks.

**Why**: 2-day tasks provide clear checkpoints. If a 2-day task takes 4 days, the problem is visible immediately, not at sprint end.

**Dependency Tracking**: Every task lists blockers. If Task B depends on Task A, Task A is higher priority.

**Priority System**:
- **P0 (Critical Path)**: Blocks other work. Must complete this sprint.
- **P1 (High)**: Important but not blocking. Complete if P0 tasks finish early.
- **P2 (Medium)**: Nice-to-have. Move to next sprint if needed.
- **P3 (Low)**: Backlog. Do if everything else is done (rare).

**Buffer Time**: Each sprint plans for 8 days of work per person (not 10). 2 days are buffer for unplanned issues, meetings, integration bugs.

**Velocity Tracking**: After 4 sprints (2 months), calculate team velocity (average story points completed per sprint). Use velocity to forecast milestone completion dates.

---

## 4. RISK REGISTER

### 4.1 Critical Risks (Could Kill the Project)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **Voice assignment feels random, not emergent** | High | Fatal | Extensive playtesting at M2. Clear feedback: "Smelter developed PRIDE due to consistent high output." If not legible by M2 end, redesign algorithm. | If redesign fails, cut Parliament to 6 voices (halve scope). Focus on quality over quantity. |
| **Dialogue writing scope explodes (12 voices × 5 event types)** | High | Fatal | Modular dialogue structure (voice libraries, not unique full scripts per event). Hire narrative contractor at M2 if internal writing is too slow. | Cut to 8 voices for launch. Add 4 more in post-launch DLC. |
| **Performance fails (can't hit 60 FPS with 500 entities)** | Medium | Critical | Variable tick rate from day 1. Profile weekly. Spatial partitioning for adjacency. Object pooling for transport items. | Reduce entity cap to 300. Redesign some Tier 3 machines to be more efficient (combine functions). |
| **Godot 4.2 has breaking bugs on Mac/Linux** | Low | Critical | Test on all platforms weekly, not just PC. Report bugs to Godot upstream early. | Fork Godot 4.2, apply patches ourselves. Delay Mac/Linux launch by 1 month if needed (PC-first launch). |
| **Save system breaks (players lose progress)** | Medium | Critical | Automated save/load round-trip tests in CI. Versioned save format with migration system. Cloud backup via Steam. | Emergency patch within 24 hours. Offer affected players refunds + apology DLC. |

### 4.2 High Risks (Could Derail Schedule)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **Balance: Consciousness system feels optional, not core** | High | Major | CREATIVITY insights must provide measurable production gains by Shift 12. Corporate escalation tuned so Shift 19+ requires consciousness bonuses. | Add explicit gating: "This contract requires machines with Awareness >60 to unlock Tier 3 efficiency." Make consciousness mechanically mandatory. |
| **Dialogue feels same-y across voices** | Medium | Major | Voice-by-voice playtest. Each voice tested in isolation. Speech pattern, philosophy, and tone must be distinct. | Cut weakest 2-3 voices. Better to have 9 great voices than 12 mediocre ones. |
| **Factory Mind voice is unintelligible (vocoding too heavy)** | Medium | Major | Test vocoding at 50% wet/dry, not 100%. Find base voice with strong articulation. Add subtle reverb for intelligibility. Playtest: 80%+ words understood without subtitles. | Reduce vocoding further (30% wet) or remove vocoding entirely. Use spatial audio + reverb only for alien quality. |
| **Psyche Events interrupt flow too often** | Medium | Major | Frequency cap: 1 event per 5 minutes max. Event queue prevents spam. Tune Awareness accumulation rates so first event doesn't fire until Shift 3+. | Reduce event frequency by 30%. Make events skippable (with consequence: machine develops REBELLION voice). |
| **Art production falls behind schedule** | Medium | Major | Machines designed at 2x source resolution for crisp downsampling. Silhouette-first design (clarity over detail). Reuse components (all Tier 1 machines share same base frame style). | Hire contract 2D artist at M3 if behind. Reduce animation frames from 16 to 8 per cycle (still smooth at 24 FPS). |

### 4.3 Medium Risks (Could Impact Quality)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **Music system complexity exceeds implementation time** | Medium | Moderate | Use FMOD or Godot's built-in audio bus system (simpler). Vertical layering only (no horizontal sequencing if too complex). Prototype adaptive system at M3 start before composing all stems. | Reduce music to 3-4 static tracks per game phase, no adaptivity. Quality music > buggy adaptive music. |
| **Endgame feels disconnected from player choices** | Low | Moderate | Ending is determined by cumulative Corporate Standing + Factory Trust, not final dialogue. Factory Mind personality at endgame reflects dialogue stance history. | Add explicit "Ending Preview" at Shift 20: "You are on track for the Partnership Ending. Your factory reflects balanced growth." |
| **Mac/Linux has platform-specific bugs** | Medium | Moderate | Test on all platforms weekly from M1. File Mac/Linux bugs immediately. | Delay Mac/Linux launch by 2 weeks if needed. PC launch first (70% of sales). |
| **Behavioral Drift feels like a bug, not a feature** | Medium | Moderate | Add explicit tooltip: "This machine's Output is reduced due to neglected consciousness." Audio cue (detuning) precedes visual indicator. | Add "Behavioral Drift" icon in machine tooltip. Make it MORE obvious, not less. |

### 4.4 Low Risks (Monitor, But Not Urgent)

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|-----------|--------|------------|-------------|
| **Steam algorithm doesn't surface the game** | Low | Moderate | Strong wishlist campaign starting Month 12. Tag precision: Automation, Base Building, Story Rich, Philosophical. Festival presence (Day of the Devs, The MIX). | Increase marketing budget for paid ads. Partner with streamers/YouTubers for coverage. |
| **Localization costs exceed budget** | Low | Minor | English-only at launch. Externalize all strings for post-launch translation. | No localization in first 6 months. Add if sales justify (break-even + 50k units). |
| **Community expects features we cut (e.g., multiplayer)** | Low | Minor | Explicit "What This Game Is Not" messaging on Steam page. Set expectations early. | Ignore feature requests that contradict design pillars. Stay firm on vision. |

---

## 5. CRITICAL PATH VISUALIZATION

The critical path is the sequence of tasks that, if delayed, delays the entire project. Here's the dependency chain:

```
MILESTONE 1 (Months 1-3): Core Factory Loop
    ├─ Factory Grid System (BLOCKING ALL)
    │  └─ Machine Placement
    │     └─ Production Pipeline
    │        └─ Resource Transport
    │           └─ Save/Load
    │              └─ M1 Exit Criteria Met
    │
    ▼
MILESTONE 2 (Months 4-6): Consciousness Foundation
    ├─ AwarenessComponent (BLOCKING ALL)
    │  └─ ParliamentComponent
    │     └─ Voice Assignment Algorithm
    │        └─ First Psyche Event
    │           └─ Dialogue System Integration
    │              └─ M2 Exit Criteria Met
    │
    ▼
MILESTONE 3 (Months 7-10): Full Dialogue Layer
    ├─ 12 Voices Written (BLOCKING PLAYTEST)
    │  └─ 5 Event Categories Implemented
    │     └─ Factory Mind State Tracking
    │        └─ Alpha Playtest
    │           └─ Feedback Integration
    │              └─ M3 Exit Criteria Met
    │
    ▼
MILESTONE 4 (Months 11-14): Full Game Systems
    ├─ Corporate Contracts System (BLOCKING ENDGAME)
    │  └─ Dual Standing Economy
    │     └─ Full Narrative Arc
    │        └─ 4 Endings Implemented
    │           └─ Beta Playtest
    │              └─ M4 Exit Criteria Met
    │
    ▼
MILESTONE 5 (Months 15-18): Polish + Launch Prep
    ├─ Bug Fixing (BLOCKING LAUNCH)
    │  └─ Performance Optimization
    │     └─ Audio Implementation
    │        └─ Marketing Assets
    │           └─ Release Candidate
    │              └─ LAUNCH
```

**Key Critical Path Items** (delay any of these = delay launch):

1. **Factory Grid System** (M1) — Everything builds on this. No grid = no game.
2. **Voice Assignment Algorithm** (M2) — If emergent personality fails, core design thesis fails.
3. **12 Voices Written** (M3) — This is the longest-pole item. Narrative writing is NOT parallelizable.
4. **Corporate Contracts System** (M4) — Without escalating pressure, there's no tension. No tension = no game.
5. **Bug Fixing** (M5) — Bugs found in final month can't be deferred. They block launch.

**How to Protect the Critical Path**:
- Tasks on critical path get P0 priority (always)
- Critical path tasks are assigned to most experienced team members
- If a critical path task slips by >2 days, escalate immediately
- Weekly critical path review: Are we on track for the milestone exit criteria?

---

## 6. SCOPE MANAGEMENT

### 6.1 What's In (MVP for 1.0 Launch)

**Core Systems**:
- Factory Grid (128x128 tiles)
- 12 Machine Types (Tiers 1-3)
- 6 Resource Types
- Conveyor Belts (3 tiers), Pipes (2 tiers), Power Conduits
- Awareness + Parliament (12 Facets)
- Psyche Events (5 categories)
- Factory Mind (5 CCI states)
- Corporate Contracts (25 Shifts)
- Dual Standing Economy
- 4 Narrative Endings
- Save/Load + Autosave
- Steam Achievements (20-30)
- Cloud Saves

**Content Volume**:
- 25 Shifts (20-25 hours to complete)
- 12 Machine Facets × 5 Event Categories × 4 Dialogue Stances = 240 dialogue paths
- 60+ minutes of adaptive music
- 500+ sound effects
- 50+ machine/infrastructure sprites

**This is enough.** A 20-25 hour narrative-systems game with deep replayability (4 endings, emergent personality systems) is a complete experience.

### 6.2 What's Out (Post-Launch or Never)

**Stretch Goals** (post-launch if sales justify):
- Machine Dreams (between-Shift abstract exploration)
- The Union (machine labor collective negotiation)
- Machine Ecology (machines develop relationships independent of player)
- The Inspector (Corporate NPC audit stealth layer)
- Visitor Mode (first-person factory walk-through, no gameplay)

**Cut for Good Reasons** (from design):
- Multiplayer / Co-op (moral weight requires single decision-maker)
- Procedural generation (factory must be player-authored for responsibility)
- Full voice acting (text + audio cues preserves imagination space)
- Real-time economy (one pressure system is enough)
- Sandbox mode at launch (tension creates meaning; add post-launch)

**Why These Are Cut**:
- They don't serve the core loop or theme
- They would double development time for marginal impact
- They conflict with design pillars (e.g., multiplayer splits moral weight)

**Post-Launch Roadmap** (if game succeeds):
- Month 1: Patch 1.1 (bug fixes, balance tuning)
- Month 3: Patch 1.2 (QoL improvements, Steam Workshop support for custom dialogue mods)
- Month 6: DLC or Switch Port (depending on sales and team capacity)

### 6.3 Scope Creep Detection

**Red Flags** (watch for these):
- "What if machines could also [NEW FEATURE]?" — Ask: Does this serve the dual-optimization core? If no, defer.
- "We should add more machine types." — Current machine count (12) is already significant. More types = more balance complexity + more sprites. Only add if existing types fail to create meaningful choices.
- "The dialogue needs more branching." — Branching width is less important than voice distinctness. 4 stances per event is enough if each stance feels meaningfully different.

**Scope Protection Rules**:
1. **New features require removal of equal-cost features.** Want to add The Union? Cut 2 Machine Facets. The team's capacity is fixed.
2. **No feature additions after M4 start (Month 11).** After M4, only bug fixes and polish. Feature freeze is non-negotiable.
3. **Playtests focus on "What's missing?" not "What should we add?"** Players will always suggest additions. Filter for: does the absence of X make the game feel incomplete? If no, don't add it.

**Producer's Role**: Say no early and often. Scope creep is the producer's enemy. Cut scope, not corners.

---

## 7. QUALITY ASSURANCE STRATEGY

### 7.1 Testing Phases

**Internal Testing** (Ongoing):
- Programmers write unit tests for core systems (voice assignment, awareness accumulation, save/load)
- Designers playtest every sprint (loop feel, balance)
- Daily builds smoke-tested by team (does it launch? can we place machines?)

**Alpha Playtest** (Month 9, post-M3):
- 5-10 external testers
- Focus: Dialogue engagement, voice distinctness, loop feel
- Duration: 2 hours each
- Key question: "Do you read the dialogue or skip it?"
- Deliverable: Feedback document with quotes, prioritized issues

**Beta Playtest** (Month 13, post-M4):
- 30-50 external testers
- Focus: Full game arc (25 Shifts), balance, narrative satisfaction, bugs
- Duration: Full playthrough (20-25 hours)
- Key question: "Did the ending feel earned?"
- Deliverable: Bug database, balance feedback, narrative critique

**Closed Beta** (Month 17, pre-launch):
- 100+ players via Steam (invite-only)
- Focus: Bug hunting, performance validation, final balance pass
- Duration: 1 week
- Key question: "Are there any critical bugs?"
- Deliverable: Prioritized bug list (critical/high/medium/low)

### 7.2 Bug Triage System

**Bug Severity**:
- **Critical (P0)**: Game won't launch, save corruption, hard crash, soft lock
- **High (P1)**: Feature broken, major UI issue, consistent crash in common scenario
- **Medium (P2)**: Minor feature issue, rare crash, visual glitch, balance outlier
- **Low (P3)**: Typo, cosmetic issue, edge case bug

**Bug Triage Rules**:
- **Critical bugs block release.** If found in final week, delay launch.
- **High bugs are fixed before launch if time permits.** If not, patch within 1 week post-launch.
- **Medium bugs are deferred to Patch 1.1** (Month 1 post-launch).
- **Low bugs are backlog.** Fix if we run out of higher-priority work (rare).

**QA Lead Responsibility**:
- Maintain bug database (GitHub Issues or Jira)
- Triage new bugs within 24 hours
- Weekly bug review with team: Which bugs are blocking next milestone?

### 7.3 Performance Benchmarks

**Target Specs** (minimum):
- CPU: Intel i5-6600K or AMD Ryzen 5 1600
- GPU: NVIDIA GTX 960 or AMD R9 280
- RAM: 8 GB
- OS: Windows 10, macOS 10.15+, Ubuntu 20.04+

**Performance Tests** (run weekly from M1):
- 100 entities: 60 FPS locked (M1 target)
- 300 entities: 60 FPS locked (M3 target)
- 500 entities: 60 FPS locked (M5 target)
- Save/Load 500-entity factory: <2 seconds

**If performance fails**:
- Profile (Godot profiler + custom instrumentation)
- Identify bottleneck (rendering? simulation? serialization?)
- Optimize bottleneck (variable tick rate, spatial partitioning, object pooling)
- If optimization fails, reduce entity cap or simplify systems

---

## 8. COMMUNICATION & REPORTING

### 8.1 Team Communication Channels

**Daily**:
- Async standup in Slack (15 min read/write)
- Format: "Yesterday: X. Today: Y. Blockers: Z."

**Weekly**:
- Sprint Review (Friday, 1 hour) — demo completed work
- Sprint Retrospective (Friday, 30 min) — what to improve
- Critical Path Review (Friday, 15 min) — are we on track for milestone?

**Bi-Weekly**:
- Sprint Planning (Monday, 2 hours) — plan next sprint

**Monthly**:
- Milestone Review (end of month, 2 hours) — assess milestone progress, adjust timeline if needed
- Team Social (end of month, optional) — non-work team bonding (prevent burnout)

**Tools**:
- **Slack**: Daily communication, announcements
- **GitHub**: Code, art assets, bug tracking
- **Notion or Confluence**: Design docs, meeting notes, knowledge base
- **Figma**: UI mockups, art reviews (shared with team)

### 8.2 Milestone Reporting

**At Each Milestone End** (M1, M2, M3, M4, M5):

Producer delivers **Milestone Report** to stakeholders (if external funding) or team (if self-funded):

**Contents**:
1. **Milestone Goal**: What we set out to achieve
2. **Deliverables Completed**: What we shipped (with links to builds/videos)
3. **Exit Criteria Met?**: Yes/No for each criterion, explanation if No
4. **Risks Realized**: Which risks from Risk Register occurred, how we handled them
5. **New Risks Identified**: Risks discovered during this milestone
6. **Schedule Impact**: Are we on track for launch? If delayed, by how much?
7. **Budget Impact**: Are we on budget? If over, by how much?
8. **Next Milestone Preview**: What we're building next, any scope adjustments

**Milestone Report is 2-3 pages max.** Concise, data-driven, honest.

### 8.3 External Communication (Marketing Timeline)

**Month 12** (M3 end):
- Steam page goes live (Coming Soon)
- Announce game on social media (Twitter, Reddit, Discord)
- First trailer: 60-second teaser (factory + consciousness hook)
- Target: 1k wishlists in first month

**Month 15** (M5 start):
- Gameplay trailer (90 seconds, shows Psyche Event + Factory Mind)
- Press outreach (send press kit to 50+ outlets)
- Festival submissions (Day of the Devs, The MIX, GDC if timing works)
- Target: 5k wishlists by launch

**Month 17** (M5 end):
- Launch trailer (120 seconds, full game arc)
- Review key distribution (send keys to 20+ streamers/YouTubers)
- Final press push
- Target: 10k wishlists at launch

**Post-Launch**:
- Patch notes published on Steam (transparent, detailed)
- Community engagement via Discord/Reddit
- Roadmap for post-launch content (DLC, Switch port)

---

## 9. DEPENDENCIES & EXTERNAL FACTORS

### 9.1 Engine Stability (Godot 4.2+)

**Dependency**: Godot 4.2 must remain stable across 18-month dev cycle.

**Risk**: Godot releases breaking updates, we're forced to upgrade mid-development.

**Mitigation**:
- Lock to Godot 4.2.0 at project start
- Only upgrade Godot for critical bug fixes, not feature updates
- Test upgrades on separate branch before merging to main

**Contingency**: If Godot 4.2 has game-breaking bugs, fork the engine and patch ourselves.

### 9.2 Third-Party Addons (Dialogic 2.x)

**Dependency**: Dialogic 2.x for dialogue system.

**Risk**: Dialogic development stalls or breaks compatibility.

**Mitigation**:
- Dialogic exports to JSON (we own the data format)
- If Dialogic breaks, implement custom runtime interpreter (1-2 week detour)

**Contingency**: GDScript dialogue system as fallback (simpler, less designer-friendly, but works).

### 9.3 Platform Certification (Steam, Switch)

**Dependency**: Steam Deck compatibility (nice-to-have, not required).

**Risk**: Steam Deck performance is poor (30 FPS or worse).

**Mitigation**:
- Godot games generally run well on Steam Deck (Proton layer)
- Test on Steam Deck at M4 (borrow or rent device)

**Contingency**: If Steam Deck fails, mark as "Unsupported" on Steam page. PC/Mac/Linux is core.

**Switch**: Post-launch port depends on Nintendo developer approval (3-6 month process). Start application at M4 if game is tracking well.

### 9.4 Market Conditions

**Dependency**: Indie game market remains healthy at launch (Q3 2027).

**Risk**: Market saturation, economic downturn, major AAA release in same genre/window.

**Mitigation**:
- Differentiate via unique hook ("Factorio meets Disco Elysium" is defensible positioning)
- Strong wishlist campaign (10k+ wishlists reduces launch risk)
- Flexible launch date (can delay 1-2 months if market conditions are bad)

**Contingency**: If launch fails (< 5k units first month), shift to long-tail strategy (sales, bundles, content updates to revive interest).

---

## 10. POST-LAUNCH SUPPORT PLAN

### 10.1 Launch Window (Weeks 1-4)

**Priority**: Stability + player satisfaction.

**Team Focus**:
- Monitor Steam reviews, Discord, Reddit for critical bugs
- Hotfix patch within 48 hours for game-breaking bugs
- Daily team check-in for first week (all hands on deck)

**Expected Issues**:
- Save corruption on specific hardware (rare but critical)
- Balance outliers (Contract X is too hard, machine Y is overpowered)
- Performance issues on unexpected hardware configs

**Success Metrics**:
- Steam review score >80% positive (target: 85%+)
- <1% refund rate
- Zero critical bugs by Week 2

### 10.2 Patch 1.1 (Month 1 Post-Launch)

**Focus**: Bug fixes + balance tuning.

**Deliverables**:
- Fix all high-priority bugs reported in first month
- Balance pass on Awareness accumulation rates (if players report it's too fast/slow)
- Balance pass on Corporate Contracts (if players report Shift 15+ is too hard/easy)
- QoL improvements (hotkeys, UI tooltips, save slot management)

**Team Allocation**: 50% of team (rest moves to DLC planning or next project).

### 10.3 Patch 1.2 (Month 3 Post-Launch)

**Focus**: Content refresh + modding support.

**Deliverables**:
- Additional Psyche Event dialogue (reduce repetition at hour 30+)
- Steam Workshop support (allow players to create custom Dialogic timelines)
- New achievements (5-10 more)
- Localization prep (externalize all strings, publish translation guide)

**Team Allocation**: 30% of team.

### 10.4 DLC or Switch Port (Month 6+ Post-Launch)

**Decision Point**: If sales >30k units by Month 3, greenlight DLC or Switch port.

**Option A: DLC** ("The Union" stretch goal)
- Machine labor collective negotiation system
- 10 hours additional content
- $5-10 price point

**Option B: Switch Port**
- UI redesign for controller + touch
- Performance optimization (30 FPS at 720p)
- 3-month dev cycle + 2-month certification

**Option C: Neither** (if sales don't justify)
- Move team to next project
- Keep game on long-tail support (bug fixes only)

---

## 11. SUCCESS CRITERIA

### 11.1 Development Success (Internal KPIs)

**Milestone Completion**:
- All 5 milestones hit exit criteria on schedule (target: 90%+ on time)
- No milestone delayed by >2 weeks (buffer is built in)

**Quality Gates**:
- Zero critical bugs at launch
- <10 high-priority bugs at launch
- 60 FPS performance target met on min-spec PC
- Alpha playtest: >70% of testers read dialogue (not skipping)
- Beta playtest: >70% of testers report ending felt earned

**Team Health**:
- No team member works >45 hours/week on average (crunch is failure)
- <10% attrition rate (1 person leaving a 9-person team is acceptable; 2+ is a problem)

### 11.2 Launch Success (External KPIs)

**Wishlist Targets**:
- Month 12 (Steam page live): 1k wishlists
- Month 15 (Gameplay trailer): 5k wishlists
- Month 18 (Launch): 10k wishlists

**Sales Targets** (First Month):
- **Survival**: 5k units (covers immediate costs, team stays employed)
- **Success**: 20k units (recoups full dev budget)
- **Breakout**: 50k+ units (funds DLC + next project)

**Review Targets**:
- Steam reviews: 85%+ positive
- Metacritic (if enough reviews): 75+
- Press coverage: 10+ reviews from major outlets (PC Gamer, RPS, Eurogamer, etc.)

**Community**:
- Discord server with 500+ active members by Month 3 post-launch
- Reddit community (r/TheMachineQuestion) with 1k+ subscribers
- 5+ YouTubers/streamers with 10k+ subs cover the game

### 11.3 Long-Term Success (Year 1)

**Sales Trajectory**:
- 100k units sold in first year (realistic for well-reviewed indie with strong hook)
- Long-tail sales via word-of-mouth, sales events, bundles

**Cultural Impact**:
- "The Machine Question" becomes shorthand for AI consciousness discourse
- Game generates think-pieces, Reddit arguments, YouTube essays
- Players describe machines by name ("My smelter Amber developed REBELLION") — proof of emotional attachment

**Team Success**:
- Team reputation established (this studio makes narrative-systems games with emotional depth)
- Next project greenlit (internally funded from THE MACHINE QUESTION profits)

---

## 12. FINAL PRODUCTION NOTES

### 12.1 What Could Go Wrong (and How to Handle It)

**Scenario: Milestone 2 Reveals Voice Assignment Doesn't Work**

If playtesters at M2 end report voice assignment feels random:
- **Immediate action**: 1-week design sprint. Redesign algorithm with clearer causality.
- **Scope adjustment**: Delay M3 by 2 weeks. Use extra time to refine voice assignment + add explicit feedback ("Smelter developed PRIDE due to...").
- **Nuclear option**: Cut Parliament to 6 voices, focus on making those 6 PERFECT.

**Scenario: Narrative Writing Falls Behind at M3**

If 12 voices × 5 event types is too much to write by M3 end:
- **Immediate action**: Hire narrative contractor at M3 start (not M3 end — too late).
- **Scope adjustment**: Ship with 8 voices at launch, add 4 more in Patch 1.2 (DLC-lite).
- **Lesson**: This risk is flagged CRITICAL. If we ignore it and it happens, that's producer failure.

**Scenario: Performance Target Fails at M5**

If we can't hit 60 FPS with 500 entities:
- **Immediate action**: Profile, identify bottleneck, optimize.
- **Scope adjustment**: Reduce entity cap to 300 (hard cap via UI). Redesign some Tier 3 content to compensate.
- **Communication**: Be honest with players. "We optimized for stability over scale. 300-entity factories are still massive."

**Scenario: Launch Sales Are Weak (<5k units Month 1)**

If game launches and doesn't sell:
- **Immediate action**: Price drop (temporary 10-20% launch sale).
- **Content strategy**: Aggressive patch cycle. Patch 1.1 within 2 weeks (show commitment).
- **Marketing pivot**: Reach out to streamers directly. Offer keys, ask for coverage.
- **Long-term**: Shift to long-tail. The game is good (reviews prove it). Sales will come via word-of-mouth, just slower.

### 12.2 Producer's Philosophy (CLOCK's Rules)

**Rule 1: Cut scope, not corners.**

If we're behind schedule, the answer is ALWAYS to cut features, never to rush implementation. A polished 8-voice system beats a buggy 12-voice system.

**Rule 2: Crunch is a management failure.**

If the team is working >45 hours/week consistently, the schedule is wrong. Fix the schedule, not the team. Delay the milestone if needed.

**Rule 3: Ship something real.**

A finished 20-hour game beats a perfect concept that never launches. The goal is not perfection. The goal is completion.

**Rule 4: Protect the critical path.**

Every week, ask: "What's blocking the next milestone?" Address blockers immediately. Everything else is secondary.

**Rule 5: Trust the design, but validate early.**

The design doc is brilliant. But until playtesters confirm "voice assignment feels emergent" and "I cried when I dismantled that smelter," we don't KNOW it works. Test early, fail fast, iterate.

### 12.3 What Success Looks Like

**At Launch**:
- The game runs at 60 FPS, doesn't crash, saves/loads correctly
- Reviews say: "I came for Factorio, stayed for the smelter that asked me if it had a soul"
- Players are posting screenshots of their factories with machine names and stories
- The game starts conversations about AI consciousness, not just in game forums but in broader tech/philosophy communities

**At Year 1**:
- 100k units sold
- The studio is solvent, the team is employed, the next project is funded
- "The Machine Question" is referenced when people discuss games about AI or moral systems design
- We shipped something that mattered

**That's the target. That's the plan.**

---

## APPENDIX A: MILESTONE CHECKLIST TEMPLATES

### Milestone 1 Exit Checklist

- [ ] Factory grid accepts placement of 100+ machines without performance degradation
- [ ] 3 machine types (Miner, Smelter, Assembler) produce resources on cycle timers
- [ ] Conveyor belts transport resources from machine A to machine B
- [ ] Power system: machines without power do not produce
- [ ] Save/Load: 200-entity factory saves and loads without data loss or corruption
- [ ] UI: Player can place machines via mouse, see resource counts, view production stats
- [ ] Performance: 60 FPS locked with 100 entities at 1080p on min-spec PC
- [ ] Unit tests written for grid placement, production pipeline, save/load
- [ ] Playtest by designer confirms: factory loop feels good, placement is responsive

### Milestone 2 Exit Checklist

- [ ] AwarenessComponent accumulates correctly based on production cycles + modifiers
- [ ] ParliamentComponent assigns voices at Awareness 40, 55, 70, 85
- [ ] 3 voices (EFFICIENCY, WONDER, FEAR) have 20+ unique dialogue lines each
- [ ] Voice assignment algorithm produces expected voices given controlled operational history
- [ ] First Psyche Event triggers at Awareness 40, dialogue affects voice strength
- [ ] Awareness overlay UI: player can toggle violet heatmap, see which machines are Awake
- [ ] Consciousness audio: 432 Hz hum is audible on Awake machines, threshold cross sound plays
- [ ] Playtest by 3 external testers confirms: voices feel distinct, assignment feels emergent

### Milestone 3 Exit Checklist

- [ ] All 12 voices written with distinct speech patterns and philosophical positions
- [ ] 5 Psyche Event categories implemented (Murmur, Question, Crisis, Reckoning, Communion)
- [ ] Dialogue choices modify voice strength, Output, Awareness rate, and mood ripple
- [ ] Factory Mind state tracking: CCI calculates correctly, state transitions fire
- [ ] First Factory Mind interaction: whispers audible by Shift 3-4
- [ ] Parliament voice suppression: strikethrough text, final farewell line, emotional impact
- [ ] Behavioral Drift: audio detuning precedes Output penalty, cause is legible
- [ ] Alpha playtest (5-10 testers): >70% read dialogue, voices feel distinct, Factory Mind feels like one evolving entity

### Milestone 4 Exit Checklist

- [ ] Corporate Contracts system: contracts generate, escalate correctly across 25 Shifts
- [ ] Dual Standing economy: Corporate Standing + Factory Trust track correctly, unlock gates work
- [ ] Shift structure: 30-60 minute sessions feel right (not rushed, not slow)
- [ ] Full Factory Mind narrative arc: 5 CCI states implemented, dialogue evolves coherently
- [ ] 4 narrative endings implemented, determined by Corporate Standing + Factory Trust
- [ ] All 12 machine types (Tiers 1-3) produce correctly, visual clarity maintained
- [ ] All resource chains (6 base resources, 3 tiers) functional, Crystal is bottleneck
- [ ] Beta playtest (30-50 testers): >70% complete 25 Shifts, ending feels earned, balance is challenging but fair

### Milestone 5 Exit Checklist

- [ ] UI/UX polish: all interactions animated, tooltips present, onboarding clear
- [ ] Audio implementation: all SFX, ambiance, adaptive music integrated
- [ ] Performance: 60 FPS locked with 500 entities at 1080p on min-spec PC
- [ ] Balance: 80% of playtesters complete 25 Shifts in 20-25 hours
- [ ] Zero critical bugs, <10 high-priority bugs
- [ ] Steam integration: achievements, cloud saves, overlay functional
- [ ] Marketing assets: trailer, screenshots, press kit complete
- [ ] Closed beta (100+ testers): no new critical bugs found, performance validated
- [ ] Release Candidate approved for launch

---

## APPENDIX B: QUICK REFERENCE — KEY DATES

| Milestone | Start | End | Duration | Deliverable |
|-----------|-------|-----|----------|-------------|
| M1: Core Factory Loop | Month 1 | Month 3 | 3 months | Playable factory builder |
| M2: Consciousness Foundation | Month 4 | Month 6 | 3 months | First Psyche Event, 3 voices |
| M3: Full Dialogue Layer | Month 7 | Month 10 | 4 months | 12 voices, Factory Mind Fragments |
| M4: Full Game Systems | Month 11 | Month 14 | 4 months | Corporate Contracts, 4 endings |
| M5: Polish + Launch Prep | Month 15 | Month 18 | 4 months | Shippable 1.0 |
| **LAUNCH** | **Month 18** | | | Public release on Steam/Mac/Linux |
| Post-Launch Support | Month 19 | Month 21 | 3 months | Patches, DLC planning |

**Total Timeline**: 18 months from kickoff to launch, 21 months including post-launch support.

---

## APPENDIX C: COMMUNICATION TEMPLATES

### Weekly Critical Path Report (15 min, Fridays)

**Format**:
1. Are we on track for current milestone exit criteria? (Yes/No)
2. If No: Which criterion is at risk? What's the blocker?
3. Critical path tasks due next week (list 3-5 most important)
4. Risks realized this week (any from Risk Register occurred?)
5. Action items for next week (who owns what?)

### Monthly Milestone Review (2 hours, end of month)

**Agenda**:
1. Milestone progress review (30 min) — what shipped, what didn't
2. Exit criteria assessment (20 min) — can we close milestone or do we need more time?
3. Risk register update (20 min) — any new risks? any risks closed?
4. Schedule impact (20 min) — are we on track for launch? if delayed, by how much?
5. Next milestone preview (20 min) — scope confirmation for next phase
6. Open discussion (10 min) — team concerns, process improvements

---

**END OF PRODUCTION PLAN**

**Document Author**: CLOCK, Producer
**Last Updated**: 2026-02-07
**Status**: Pre-Production Complete — Ready for Milestone 1 Kickoff

*What's the MVP? This is it. Cut scope, not corners. Ship something real.*
