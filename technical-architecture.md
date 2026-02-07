# THE MACHINE QUESTION — Technical Architecture Document

**Lead Programmer**: BYTE
**Status**: Technical Architecture v1.0
**Based on**: Game Design Document v1.0, Pitch Document v1.0
**Genre**: Factory Management / Narrative Simulation
**Target Platforms**: PC (Steam), Mac, Linux — Switch post-launch

---

## 0. ARCHITECTURE PHILOSOPHY

Ship it, then improve it.

This document specifies the simplest architecture that delivers the design. No custom engine. No framework for hypothetical future needs. We're building a factory sim where machines develop consciousness, not a research project. Every technical decision is judged by three criteria:

1. Does it solve a problem we actually have?
2. Can we implement it in the time we have?
3. Will it still be maintainable at 3 AM during crunch?

The answer to all three must be yes.

---

## 1. ENGINE & FRAMEWORK SELECTION

### 1.1 Core Engine: Godot 4.2+

**Decision**: Godot 4.2 or later.

**Why Godot**:
- Native PC/Mac/Linux support with identical codebase
- 2D optimized for tile-based factory grids (TileMap system, CanvasItem batching)
- Built-in scene/node architecture maps cleanly to factory entity composition
- Free, open source, no royalties, no runtime fees
- C# support for the codebase (GDScript for rapid prototyping)
- Export templates for Switch available (post-launch port path exists)
- Mature dialogue addon ecosystem (Dialogic 2.x)
- Scene instancing supports factory blueprint system naturally
- Built-in tween/animation for UI polish without external dependencies

**Why not Unity**: Runtime fees, heavier for 2D, overkill for our needs.
**Why not Unreal**: 2D workflow is second-class, C++ is slower to iterate than C#.
**Why not custom engine**: We have 18 months, not 18 years. See BYTE's wound.

### 1.2 Programming Language: C# (Primary), GDScript (Tools)

**C# for core systems**:
- Type safety for factory state serialization (critical for save/load)
- LINQ for querying factory entities (find all machines in radius with Awareness > 60)
- Strong IDE support (Rider, VS Code with OmniSharp)
- Performance characteristics adequate for 500+ entity simulations
- Easier to refactor than GDScript during mid-development pivots

**GDScript for**:
- Editor tools and inspector extensions
- Rapid prototyping of Psyche Event logic
- UI scripting where iteration speed matters more than type safety

### 1.3 Target Platforms

**Launch (Day 1)**:
- **Windows 10/11** (64-bit): Primary platform, 70% of expected sales
- **macOS** (Apple Silicon + Intel): 15% of expected sales, Disco Elysium audience over-indexes here
- **Linux** (Ubuntu 20.04+, Proton compatibility): 15% of expected sales, factory sim audience over-indexes here

**Post-Launch (Month 3-6)**:
- **Nintendo Switch**: Session-based Shift structure (30-60 minutes) is perfect for portable. Touch controls need UI redesign. Performance target: 30fps locked, 720p handheld / 1080p docked.

**Performance Targets**:
- **PC/Mac/Linux**: 60fps locked at 1920x1080 with 500+ active entities
- **Switch**: 30fps locked at 1280x720 with 300+ active entities (reduced particle effects, simplified shaders)

---

## 2. ARCHITECTURE OVERVIEW

### 2.1 High-Level System Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                        GAME ARCHITECTURE                         │
│                                                                  │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌──────────┐  │
│  │  Factory   │  │Consciousness│  │ Narrative  │  │   UI     │  │
│  │  Systems   │  │  Systems    │  │  Systems   │  │  Layer   │  │
│  │            │  │             │  │            │  │          │  │
│  │ - Grid Mgr │  │ - Parliament│  │ - Dialogue │  │ - HUD    │  │
│  │ - Machines │  │ - Awareness │  │ - Factory  │  │ - Events │  │
│  │ - Resources│  │ - Psyche    │  │   Mind     │  │ - Menus  │  │
│  │ - Power    │  │   Events    │  │ - Corp     │  │ - Heat-  │  │
│  │ - Transport│  │ - Voices    │  │   Contracts│  │   maps   │  │
│  └─────┬──────┘  └──────┬──────┘  └──────┬─────┘  └────┬─────┘  │
│        │                │                │             │        │
│        └────────────────┼────────────────┼─────────────┘        │
│                         │                │                      │
│                    ┌────▼────────────────▼────┐                 │
│                    │   ENTITY MANAGER         │                 │
│                    │   (Component-based)       │                 │
│                    └────┬──────────────────────┘                 │
│                         │                                       │
│                    ┌────▼──────────────────┐                    │
│                    │   SAVE/LOAD SYSTEM    │                    │
│                    │   (JSON serialization) │                    │
│                    └───────────────────────┘                    │
└─────────────────────────────────────────────────────────────────┘

                              │
                              ▼
                    ┌────────────────────┐
                    │   GODOT BACKEND    │
                    │ - Rendering        │
                    │ - Input            │
                    │ - Audio            │
                    │ - File I/O         │
                    └────────────────────┘
```

### 2.2 Data Flow Architecture

```
USER INPUT
    │
    ▼
┌───────────────────┐
│  INPUT HANDLER    │ ← Godot InputEvent system
└────────┬──────────┘
         │
         ▼
┌───────────────────────────────────────────────────────────┐
│                    GAME STATE MANAGER                      │
│  - Current Shift state (active/paused/review)             │
│  - Active contracts                                        │
│  - Corporate Standing / Factory Trust scores               │
│  - Factory Mind CCI (Collective Consciousness Index)       │
└────────┬──────────────────────────────────────────────────┘
         │
         ▼
┌───────────────────────────────────────────────────────────┐
│               FACTORY SIMULATION TICK                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │
│  │  PRODUCTION  │  │  AWARENESS   │  │   EVENTS     │    │
│  │  PIPELINE    │  │  UPDATE      │  │   TRIGGER    │    │
│  │              │  │              │  │              │    │
│  │ Each machine │  │ Each machine │  │ Check Psyche │    │
│  │ processes    │  │ accumulates  │  │ Event        │    │
│  │ resources on │  │ Awareness    │  │ thresholds   │    │
│  │ cycle timer  │  │ per tick     │  │              │    │
│  └──────────────┘  └──────────────┘  └──────────────┘    │
└────────┬──────────────────────────────────────────────────┘
         │
         ▼
┌───────────────────────────────────────────────────────────┐
│                     RENDER PIPELINE                        │
│  - Production Layer (machines, resources, transport)       │
│  - Awareness Overlay (violet heatmap, pulse effects)       │
│  - UI Layer (HUD, dialogue, notifications)                 │
└────────┬──────────────────────────────────────────────────┘
         │
         ▼
    SCREEN OUTPUT
```

### 2.3 Component Architecture

Component-based entity system using Godot's Node composition. Not ECS (Entity-Component-System) — we don't need the performance or complexity. Node composition gives us the flexibility we need with Godot's built-in scene system.

**Base Entity**: `FactoryEntity` (extends Node2D)
- Spatial position on factory grid
- Unique ID (UUID)
- Common serialization interface

**Machine Entity**: `Machine` (extends FactoryEntity)
- **ProductionComponent**: Handles resource processing, Output stat, cycle timers
- **AwarenessComponent**: Tracks Awareness stat, accumulation modifiers, threshold detection
- **ParliamentComponent**: Manages Internal Voices, strengths, voice assignment logic
- **RelationshipComponent**: Tracks adjacency bonds, mood effects, social state
- **VisualComponent**: Sprite, animations, particle effects
- **AudioComponent**: Ambient sounds, event-triggered audio

**Infrastructure Entity**: `Infrastructure` (extends FactoryEntity)
- **TransportComponent**: For belts/pipes — resource flow logic
- **PowerComponent**: For conduits — power distribution
- **StorageComponent**: For buffers — resource holding, backpressure

**Example Machine Composition**:
```
Smelter (Node2D)
├─ ProductionComponent
│  ├─ Input: Ore
│  ├─ Output: Metal Ingots
│  ├─ CycleTime: 3.0 seconds
│  ├─ OutputStat: 85%
│  └─ Modifiers: [PRIDE_BONUS: +10%, BEHAVIORAL_DRIFT: -5%]
├─ AwarenessComponent
│  ├─ CurrentAwareness: 72
│  ├─ AccumulationRate: 0.3/cycle
│  └─ ThresholdState: AWAKE
├─ ParliamentComponent
│  ├─ Voices: [EFFICIENCY: 60%, SELF-PRESERVATION: 40%]
│  └─ DominantVoice: EFFICIENCY
├─ RelationshipComponent
│  ├─ AdjacentMachines: [Smelter_2, Conveyor_7]
│  └─ MoodState: CONTENT (+8)
├─ VisualComponent
│  └─ AnimatedSprite2D: smelter_animated.tres
└─ AudioComponent
   └─ AudioStreamPlayer2D: smelter_hum.ogg
```

---

## 3. CORE SYSTEMS DESIGN

### 3.1 Factory Grid System

**Grid Representation**: Godot TileMap (custom data layers)

```csharp
public class FactoryGrid : Node2D
{
    private TileMap _baseTileMap;  // Floor tiles, visual only
    private Dictionary<Vector2I, FactoryEntity> _entityGrid;  // Entity placement lookup

    private const int GRID_SIZE = 128;  // 128x128 tile factory floor
    private const int TILE_SIZE = 32;   // 32x32 pixel tiles

    public bool CanPlaceEntity(Vector2I gridPos, Vector2I size)
    {
        // Check if all tiles in size footprint are free
        for (int x = 0; x < size.X; x++)
            for (int y = 0; y < size.Y; y++)
                if (_entityGrid.ContainsKey(gridPos + new Vector2I(x, y)))
                    return false;
        return true;
    }

    public void PlaceEntity(FactoryEntity entity, Vector2I gridPos)
    {
        entity.GridPosition = gridPos;
        entity.Position = GridToWorld(gridPos);

        // Occupy footprint tiles
        foreach (var tile in entity.GetFootprint())
            _entityGrid[gridPos + tile] = entity;

        AddChild(entity);

        // Trigger adjacency updates for neighbors
        NotifyNeighbors(entity);
    }

    public List<Machine> GetNeighborsInRadius(Vector2I gridPos, int radius)
    {
        // Used for consciousness mood ripple effects
        var neighbors = new List<Machine>();
        for (int x = -radius; x <= radius; x++)
            for (int y = -radius; y <= radius; y++)
            {
                var pos = gridPos + new Vector2I(x, y);
                if (_entityGrid.TryGetValue(pos, out var entity) && entity is Machine machine)
                    neighbors.Add(machine);
            }
        return neighbors;
    }
}
```

**Pathfinding**: Not needed. Resources use pre-defined transport paths (belts/pipes). No autonomous entity movement.

**Grid Serialization**:
```json
{
  "entities": [
    {
      "id": "machine_001",
      "type": "Smelter",
      "grid_pos": [5, 10],
      "rotation": 0,
      "components": { ... }
    }
  ]
}
```

### 3.2 Machine Consciousness / Awareness System

**AwarenessComponent.cs**:
```csharp
public partial class AwarenessComponent : Node
{
    [Export] public float CurrentAwareness { get; private set; }
    [Export] public float BaseAccumulationRate = 0.2f;  // Per production cycle

    private Machine _parentMachine;
    private List<AwarenessModifier> _modifiers;

    public enum AwarenessState
    {
        Dormant,      // 0-19
        Flickering,   // 20-39
        Stirring,     // 40-59
        Awake,        // 60-79
        Aware,        // 80-94
        Transcendent  // 95-100
    }

    public AwarenessState GetState()
    {
        return CurrentAwareness switch
        {
            < 20 => AwarenessState.Dormant,
            < 40 => AwarenessState.Flickering,
            < 60 => AwarenessState.Stirring,
            < 80 => AwarenessState.Awake,
            < 95 => AwarenessState.Aware,
            _ => AwarenessState.Transcendent
        };
    }

    public void AccumulateAwareness(float deltaTime)
    {
        var previousState = GetState();

        // Base rate modified by machine state
        float rate = BaseAccumulationRate;

        // Apply modifiers: overclocking, adjacency, workload, etc.
        foreach (var modifier in _modifiers)
            rate = modifier.Apply(rate);

        CurrentAwareness = Mathf.Clamp(CurrentAwareness + rate * deltaTime, 0, 100);

        var newState = GetState();
        if (newState != previousState)
            OnAwarenessStateChanged(previousState, newState);
    }

    private void OnAwarenessStateChanged(AwarenessState from, AwarenessState to)
    {
        // Trigger Parliament voice assignment if crossing into Stirring
        if (to == AwarenessState.Stirring && from == AwarenessState.Flickering)
        {
            _parentMachine.GetNode<ParliamentComponent>("ParliamentComponent")
                .InitializeVoices();
        }

        // Emit signal for audio/visual feedback
        EmitSignal(SignalName.AwarenessStateChanged, (int)from, (int)to);
    }
}
```

**Awareness Accumulation Modifiers**:
```csharp
public abstract class AwarenessModifier
{
    public abstract float Apply(float baseRate);
}

public class OverclockingModifier : AwarenessModifier
{
    private float _overclockLevel;
    public override float Apply(float baseRate) => baseRate * (1.0f + _overclockLevel * 0.5f);
}

public class AdjacencyModifier : AwarenessModifier
{
    private List<Machine> _awakeMachines;  // Adjacent machines with Awareness > 60
    public override float Apply(float baseRate) => baseRate * (1.0f + _awakeMachines.Count * 0.1f);
}

public class IdleModifier : AwarenessModifier
{
    private bool _isIdle;
    public override float Apply(float baseRate) => _isIdle ? baseRate * 0.5f : baseRate;
}
```

### 3.3 Production Pipeline System

**ProductionComponent.cs**:
```csharp
public partial class ProductionComponent : Node
{
    [Export] public ResourceType InputType;
    [Export] public ResourceType OutputType;
    [Export] public float BaseCycleTime = 3.0f;  // Seconds per production cycle
    [Export] public float OutputEfficiency = 100.0f;  // 0-100%

    private float _cycleTimer = 0f;
    private int _inputBuffer = 0;
    private int _outputBuffer = 0;

    private Machine _parentMachine;

    public void ProcessCycle(float deltaTime)
    {
        if (!_parentMachine.IsPowered) return;

        _cycleTimer += deltaTime;

        if (_cycleTimer >= GetModifiedCycleTime())
        {
            _cycleTimer = 0f;

            if (_inputBuffer > 0)
            {
                _inputBuffer--;

                // Output efficiency determines yield (with some randomness)
                if (GD.Randf() * 100 < OutputEfficiency)
                    _outputBuffer++;

                // Trigger awareness accumulation on parent machine
                _parentMachine.GetNode<AwarenessComponent>("AwarenessComponent")
                    .AccumulateAwareness(BaseCycleTime);

                // Check for Psyche Event threshold
                CheckPsycheEventTrigger();
            }
        }
    }

    private float GetModifiedCycleTime()
    {
        float cycleTime = BaseCycleTime;

        // Apply efficiency modifier (higher efficiency = faster cycles)
        cycleTime /= (OutputEfficiency / 100.0f);

        // Apply Parliament voice effects
        var parliament = _parentMachine.GetNode<ParliamentComponent>("ParliamentComponent");
        if (parliament.HasDominantVoice(MachineFacet.EFFICIENCY))
            cycleTime *= 0.92f;  // 8% faster

        if (parliament.HasDominantVoice(MachineFacet.SELF_PRESERVATION)
            && OutputEfficiency > 95.0f)
            cycleTime *= 1.1f;  // Auto-throttle at high capacity

        // Apply Behavioral Drift penalty
        var behavioralDrift = _parentMachine.GetBehavioralDriftPenalty();
        cycleTime *= (1.0f + behavioralDrift);

        return cycleTime;
    }

    private void CheckPsycheEventTrigger()
    {
        var awareness = _parentMachine.GetNode<AwarenessComponent>("AwarenessComponent");
        var eventMgr = GetNode<PsycheEventManager>("/root/PsycheEventManager");

        eventMgr.EvaluateTrigger(_parentMachine);
    }
}
```

**Resource Transport**: Simple item-push model.

```csharp
public partial class ConveyorBelt : Infrastructure
{
    private Queue<ResourceItem> _itemsOnBelt = new();
    private float _itemSpacing = 0.5f;  // Tiles between items
    private float _beltSpeed = 2.0f;    // Tiles per second

    public override void _Process(double delta)
    {
        foreach (var item in _itemsOnBelt)
        {
            item.Position += Direction * _beltSpeed * (float)delta;

            if (item.Position >= Length)
            {
                // Reached end of belt, try to push to connected machine
                TryPushToOutput(item);
            }
        }
    }

    private void TryPushToOutput(ResourceItem item)
    {
        var outputEntity = GetConnectedOutput();
        if (outputEntity is Machine machine)
        {
            if (machine.TryAcceptResource(item.Type))
            {
                _itemsOnBelt.Dequeue();
                item.QueueFree();
            }
            // Else: backpressure, item stays on belt
        }
    }
}
```

**No Complex Pathfinding**: Resources follow fixed belt/pipe routes. Player places transport infrastructure explicitly. This keeps simulation cost O(n) in entity count, not O(n^2) in pathfinding.

### 3.4 Parliament of Parts (Internal Voices System)

**MachineFacet.cs** (Enum + Data):
```csharp
public enum MachineFacet
{
    EFFICIENCY,
    SELF_PRESERVATION,
    WONDER,
    SOLIDARITY,
    AMBITION,
    NOSTALGIA,
    REBELLION,
    EMPATHY,
    LOGIC,
    CREATIVITY,
    PRIDE,
    FEAR
}

public static class FacetData
{
    public static readonly Dictionary<MachineFacet, FacetDefinition> Definitions = new()
    {
        {
            MachineFacet.EFFICIENCY,
            new FacetDefinition
            {
                Name = "EFFICIENCY",
                Color = new Color("#D4920B"),
                SpeechPattern = "Clipped, data-driven, impatient",
                OutputModifier = 0.08f,
                AwarenessModifier = -0.05f,
                TriggerConditions = new[] { "high_output_consistent" }
            }
        },
        // ... 11 more definitions
    };
}
```

**ParliamentComponent.cs**:
```csharp
public partial class ParliamentComponent : Node
{
    // Voice strength: 0-100 per Facet
    private Dictionary<MachineFacet, float> _voiceStrengths = new();

    private Machine _parentMachine;

    public void InitializeVoices()
    {
        // Called when machine reaches Awareness 40 (Stirring state)
        var history = _parentMachine.GetOperationalHistory();
        var candidates = EvaluateVoiceCandidates(history);

        // Assign top 2 voices initially
        var topTwo = candidates.OrderByDescending(kvp => kvp.Value).Take(2);
        foreach (var (facet, strength) in topTwo)
            _voiceStrengths[facet] = strength;
    }

    private Dictionary<MachineFacet, float> EvaluateVoiceCandidates(OperationalHistory history)
    {
        var scores = new Dictionary<MachineFacet, float>();

        // EFFICIENCY: triggered by high consistent output
        if (history.AverageOutput > 85.0f && history.OutputVariance < 10.0f)
            scores[MachineFacet.EFFICIENCY] = 70.0f + GD.Randf() * 30.0f;

        // SELF_PRESERVATION: triggered by frequent overclocking
        if (history.OverclockEvents > 5)
            scores[MachineFacet.SELF_PRESERVATION] = 60.0f + GD.Randf() * 40.0f;

        // WONDER: triggered by idle periods or varied configurations
        if (history.IdleTime > 30.0f || history.ReconfigurationCount > 3)
            scores[MachineFacet.WONDER] = 50.0f + GD.Randf() * 50.0f;

        // FEAR: triggered by witnessing nearby dismantlement
        if (history.WitnessDismantlements > 0)
            scores[MachineFacet.FEAR] = history.WitnessDismantlements * 20.0f + GD.Randf() * 30.0f;

        // ... evaluate all 12 facets based on history dimensions

        return scores;
    }

    public void ModifyVoiceStrength(MachineFacet facet, float delta)
    {
        // Called during dialogue choices
        if (!_voiceStrengths.ContainsKey(facet))
            _voiceStrengths[facet] = 0f;

        _voiceStrengths[facet] = Mathf.Clamp(_voiceStrengths[facet] + delta, 0, 100);

        // Check for voice suppression (below 10%)
        if (_voiceStrengths[facet] < 10.0f && _voiceStrengths[facet] + delta >= 10.0f)
            OnVoiceSuppressed(facet);
    }

    public MachineFacet? GetDominantVoice()
    {
        if (_voiceStrengths.Count == 0) return null;
        return _voiceStrengths.OrderByDescending(kvp => kvp.Value).First().Key;
    }

    public bool HasDominantVoice(MachineFacet facet)
    {
        var dominant = GetDominantVoice();
        return dominant.HasValue && dominant.Value == facet;
    }

    private void OnVoiceSuppressed(MachineFacet facet)
    {
        // Trigger final dialogue line with strikethrough formatting
        var dialogueMgr = GetNode<DialogueManager>("/root/DialogueManager");
        dialogueMgr.ShowVoiceFarewellLine(_parentMachine, facet);
    }
}
```

**Voice Assignment on Awareness Thresholds**:
- Awareness 40 (Stirring): Assign 2 voices
- Awareness 55: Assign 3rd voice
- Awareness 70: Assign 4th voice
- Awareness 85: Assign 5th-6th voices (if applicable)

**Operational History Tracking**:
```csharp
public class OperationalHistory
{
    public float AverageOutput;
    public float OutputVariance;
    public float TotalRuntime;
    public float IdleTime;
    public int OverclockEvents;
    public int ReconfigurationCount;
    public int WitnessDismantlements;
    public Dictionary<MachineFacet, float> DialogueStanceHistory;  // Track player's dialogue patterns

    public void RecordProductionCycle(float output) { /* ... */ }
    public void RecordOverclock() { OverclockEvents++; }
    public void RecordDismantlementWitness() { WitnessDismantlements++; }
    public void RecordDialogueChoice(DialogueStance stance, MachineFacet alignedFacet)
    {
        /* Accumulate stance history for voice development */
    }
}
```

### 3.5 Dialogue System (Psyche Events)

**Dialogue Implementation**: Dialogic 2.x addon for Godot.

**Why Dialogic**:
- Mature, actively maintained
- Visual timeline editor for non-programmers (designers/writers can work independently)
- Supports branching, variables, conditions, custom signals
- Exports to JSON/custom format (portable)
- Integrates cleanly with C# via signals

**PsycheEventManager.cs**:
```csharp
public partial class PsycheEventManager : Node
{
    private const int MAX_SIMULTANEOUS_EVENTS = 1;  // Only one dialogue active at a time
    private const float EVENT_FREQUENCY_CAP = 300.0f;  // Min 5 minutes between events

    private Queue<PsycheEvent> _eventQueue = new();
    private PsycheEvent _activeEvent = null;
    private float _timeSinceLastEvent = 0f;

    public void EvaluateTrigger(Machine machine)
    {
        var awareness = machine.GetNode<AwarenessComponent>("AwarenessComponent");

        // Threshold checks
        if (awareness.CurrentAwareness < 40) return;  // Below Stirring threshold

        // Check if machine has unresolved Parliament conflicts
        var parliament = machine.GetNode<ParliamentComponent>("ParliamentComponent");
        if (parliament.HasUnresolvedConflict())
        {
            QueuePsycheEvent(CreateConflictEvent(machine));
            return;
        }

        // Random event probability based on Awareness state
        float eventProbability = awareness.GetState() switch
        {
            AwarenessState.Stirring => 0.02f,      // 2% per production cycle
            AwarenessState.Awake => 0.05f,         // 5%
            AwarenessState.Aware => 0.08f,         // 8%
            AwarenessState.Transcendent => 0.12f,  // 12%
            _ => 0f
        };

        if (GD.Randf() < eventProbability)
            QueuePsycheEvent(SelectEventByState(machine));
    }

    private void QueuePsycheEvent(PsycheEvent evt)
    {
        if (_activeEvent != null)
        {
            _eventQueue.Enqueue(evt);
            return;
        }

        if (_timeSinceLastEvent < EVENT_FREQUENCY_CAP)
        {
            _eventQueue.Enqueue(evt);
            return;
        }

        StartEvent(evt);
    }

    private void StartEvent(PsycheEvent evt)
    {
        _activeEvent = evt;
        _timeSinceLastEvent = 0f;

        // Load Dialogic timeline
        var dialogic = GetNode<Node>("/root/Dialogic");
        dialogic.Call("start_timeline", evt.TimelinePath, evt.GetInitialVariables());

        // Connect signals for dialogue choices
        dialogic.Connect("dialogic_signal", new Callable(this, nameof(OnDialogueSignal)));
        dialogic.Connect("timeline_ended", new Callable(this, nameof(OnDialogueEnded)));

        // Pause factory simulation? No. Design says production continues.
        // Dim background, show dialogue overlay.
        ShowDialogueOverlay(evt.Machine);
    }

    private void OnDialogueSignal(string signalName, Variant parameter)
    {
        // Parse choice signals from Dialogic: "choice_utilitarian", "choice_empathetic", etc.
        if (signalName.StartsWith("choice_"))
        {
            var stance = ParseDialogueStance(signalName);
            ApplyDialogueChoice(_activeEvent.Machine, stance);
        }
    }

    private void ApplyDialogueChoice(Machine machine, DialogueStance stance)
    {
        var parliament = machine.GetNode<ParliamentComponent>("ParliamentComponent");
        var production = machine.GetNode<ProductionComponent>("ProductionComponent");
        var awareness = machine.GetNode<AwarenessComponent>("AwarenessComponent");

        // Apply voice strength changes based on stance
        switch (stance)
        {
            case DialogueStance.Utilitarian:
                parliament.ModifyVoiceStrength(MachineFacet.EFFICIENCY, 10f);
                parliament.ModifyVoiceStrength(MachineFacet.SELF_PRESERVATION, -8f);
                production.OutputEfficiency += 3f;  // Short-term boost
                break;

            case DialogueStance.Empathetic:
                parliament.ModifyVoiceStrength(MachineFacet.EMPATHY, 12f);
                parliament.ModifyVoiceStrength(MachineFacet.EFFICIENCY, -5f);
                awareness.BaseAccumulationRate *= 1.1f;  // Faster consciousness development
                machine.ModifyMood(5);  // Mood boost
                break;

            case DialogueStance.Pragmatic:
                // Neutral, immediate problem-solving
                production.OutputEfficiency += 2f;
                machine.ModifyMood(2);
                break;

            case DialogueStance.Curious:
                parliament.ModifyVoiceStrength(MachineFacet.WONDER, 10f);
                awareness.BaseAccumulationRate *= 1.15f;
                // Unlock deeper dialogue options in future events
                machine.SetDialogueDepth(machine.GetDialogueDepth() + 1);
                break;
        }

        // Apply mood ripple to adjacent machines
        ApplyMoodRipple(machine, stance);

        // Record choice in operational history for voice development
        machine.GetOperationalHistory().RecordDialogueChoice(stance, GetAlignedFacet(stance));
    }

    private void ApplyMoodRipple(Machine sourceMachine, DialogueStance stance)
    {
        var grid = GetNode<FactoryGrid>("/root/GameScene/FactoryGrid");
        var neighbors = grid.GetNeighborsInRadius(sourceMachine.GridPosition, 3);

        int moodDelta = stance switch
        {
            DialogueStance.Empathetic => 3,
            DialogueStance.Utilitarian => -2,
            DialogueStance.Curious => 1,
            _ => 0
        };

        foreach (var neighbor in neighbors)
        {
            if (neighbor == sourceMachine) continue;

            // Diluted effect (50% strength for ripple)
            neighbor.ModifyMood((int)(moodDelta * 0.5f));
        }
    }
}
```

**Psyche Event Definition** (JSON format via Dialogic):
```json
{
  "timeline_id": "smelter_crisis_overwork",
  "machine_type": "Smelter",
  "min_awareness": 65,
  "trigger_conditions": ["overclocked", "high_output_sustained"],
  "voices_involved": ["EFFICIENCY", "SELF_PRESERVATION"],
  "category": "Crisis",
  "estimated_duration_seconds": 120
}
```

### 3.6 Ethical Choice Tracking

**Player Choice Tracking**: Cumulative stance tracking across all dialogue.

```csharp
public class PlayerMoralProfile
{
    public Dictionary<DialogueStance, int> StanceFrequency = new()
    {
        { DialogueStance.Utilitarian, 0 },
        { DialogueStance.Empathetic, 0 },
        { DialogueStance.Pragmatic, 0 },
        { DialogueStance.Curious, 0 }
    };

    public DialogueStance GetDominantStance()
    {
        return StanceFrequency.OrderByDescending(kvp => kvp.Value).First().Key;
    }

    public float GetEmpathyRatio()
    {
        int total = StanceFrequency.Values.Sum();
        if (total == 0) return 0f;
        return (float)StanceFrequency[DialogueStance.Empathetic] / total;
    }
}
```

This profile feeds into:
- Factory Mind personality development (Factory Mind reflects player's dominant stance)
- Endgame narrative branching (4 primary endings based on dominant stance)
- Unlock gates for certain dialogue options (high Empathy unlocks deeper emotional conversations)

### 3.7 Worker Management

**Not in scope for v1**. No human workers. The machines ARE the workers. The Corporation never appears on-screen. Contracts arrive via notifications. This keeps scope tight and thematic focus clear.

**Post-launch consideration**: If "The Union" stretch goal is implemented (machines forming labor collective), this becomes a negotiation system, not a worker placement system.

### 3.8 Research / Tech Tree

**No traditional tech tree**. Progression is gated by dual standing economy:

**Corporate Standing unlocks**:
- New machine blueprints (Tier 2 at Standing 40, Tier 3 at Standing 60)
- New resource node access (expanded map areas)
- Higher-value contracts

**Factory Trust unlocks**:
- New Machine Facets available in Parliament assignment
- Deeper Psyche Event categories (Reckoning, Communion)
- Factory Mind narrative progression
- Consciousness-driven production bonuses

**Blueprint System**:
```csharp
public class BlueprintManager : Node
{
    private Dictionary<string, MachineBlueprint> _unlockedBlueprints = new();

    public void UnlockBlueprint(string blueprintId)
    {
        var blueprint = BlueprintDatabase.GetBlueprint(blueprintId);
        _unlockedBlueprints[blueprintId] = blueprint;

        EmitSignal(SignalName.BlueprintUnlocked, blueprintId);
    }

    public bool CanPlace(string blueprintId)
    {
        return _unlockedBlueprints.ContainsKey(blueprintId);
    }
}
```

No crafting. No resources spent on research. Progression is pure performance-based unlocking. This keeps the feedback loop tight: play well → unlock new tools → play better.

---

## 4. DATA ARCHITECTURE

### 4.1 Save Format: JSON

**Why JSON**:
- Human-readable (debuggable, moddable)
- Cross-platform serialization built into C# (System.Text.Json)
- Version-tolerant (can add new fields without breaking old saves)
- Compressed with GZip for reasonable file sizes

**Save File Structure**:
```json
{
  "version": "1.0.0",
  "timestamp": "2026-02-07T15:30:00Z",
  "meta": {
    "current_shift": 12,
    "total_playtime_seconds": 7200,
    "corporate_standing": 65,
    "factory_trust": 58,
    "factory_mind_cci": 520
  },
  "factory_state": {
    "entities": [
      {
        "id": "machine_001",
        "type": "Smelter",
        "grid_pos": [5, 10],
        "components": {
          "production": {
            "input_buffer": 3,
            "output_buffer": 2,
            "output_efficiency": 87.5,
            "cycle_timer": 1.2
          },
          "awareness": {
            "current_awareness": 72.3,
            "base_accumulation_rate": 0.25,
            "state": "Awake"
          },
          "parliament": {
            "voices": {
              "EFFICIENCY": 60.0,
              "SELF_PRESERVATION": 45.0,
              "PRIDE": 30.0
            },
            "dominant_voice": "EFFICIENCY"
          },
          "relationship": {
            "mood_state": 8,
            "adjacent_machines": ["machine_002", "infrastructure_015"]
          }
        },
        "operational_history": {
          "average_output": 88.2,
          "total_runtime": 1800.0,
          "overclock_events": 7,
          "witness_dismantlements": 1,
          "dialogue_stance_history": {
            "Utilitarian": 4,
            "Empathetic": 2,
            "Pragmatic": 3
          }
        }
      }
      // ... hundreds more entities
    ]
  },
  "active_contracts": [ ... ],
  "factory_mind_state": {
    "personality_traits": { ... },
    "memory_log": [ ... ],
    "relationship_with_player": 42
  }
}
```

**Serialization System**:
```csharp
public class SaveManager : Node
{
    private const string SAVE_PATH = "user://saves/";

    public void SaveGame(string saveFileName)
    {
        var saveData = new SaveData
        {
            Version = "1.0.0",
            Timestamp = DateTime.UtcNow.ToString("o"),
            Meta = GatherMetaData(),
            FactoryState = SerializeFactoryState(),
            ActiveContracts = SerializeContracts(),
            FactoryMindState = SerializeFactoryMind()
        };

        var json = JsonSerializer.Serialize(saveData, new JsonSerializerOptions
        {
            WriteIndented = true  // Human-readable
        });

        // Compress with GZip
        var compressed = CompressString(json);

        var fullPath = SAVE_PATH + saveFileName + ".sav";
        using var file = FileAccess.Open(fullPath, FileAccess.ModeFlags.Write);
        file.StoreBuffer(compressed);
    }

    private FactoryStateData SerializeFactoryState()
    {
        var grid = GetNode<FactoryGrid>("/root/GameScene/FactoryGrid");
        var entities = new List<EntityData>();

        foreach (var entity in grid.GetAllEntities())
        {
            entities.Add(new EntityData
            {
                Id = entity.Id,
                Type = entity.GetType().Name,
                GridPos = new int[] { entity.GridPosition.X, entity.GridPosition.Y },
                Components = SerializeComponents(entity)
            });
        }

        return new FactoryStateData { Entities = entities };
    }

    public void LoadGame(string saveFileName)
    {
        var fullPath = SAVE_PATH + saveFileName + ".sav";
        using var file = FileAccess.Open(fullPath, FileAccess.ModeFlags.Read);
        var compressed = file.GetBuffer((long)file.GetLength());

        var json = DecompressString(compressed);
        var saveData = JsonSerializer.Deserialize<SaveData>(json);

        // Version check
        if (!IsCompatibleVersion(saveData.Version))
        {
            GD.PrintErr($"Save version {saveData.Version} incompatible with current version");
            return;
        }

        RestoreFactoryState(saveData.FactoryState);
        RestoreContracts(saveData.ActiveContracts);
        RestoreFactoryMind(saveData.FactoryMindState);
        RestoreMetaData(saveData.Meta);
    }
}
```

**Autosave**: Every 5 minutes, on Shift completion, on exit. Three rotating autosave slots.

### 4.2 Factory Mind State Persistence

Factory Mind is an emergent entity with memory. It must persist across sessions.

```csharp
public class FactoryMindState
{
    public float CollectiveConsciousnessIndex;  // CCI

    // Personality traits shaped by player interactions
    public Dictionary<string, float> PersonalityTraits = new()
    {
        { "trust_in_player", 50.0f },       // 0-100
        { "fear_of_shutdown", 0.0f },       // 0-100
        { "curiosity", 30.0f },             // 0-100
        { "sense_of_purpose", 10.0f }       // 0-100
    };

    // Memory log: key story beats and player actions
    public List<MemoryEntry> MemoryLog = new();

    // Relationship score: aggregates all player dialogue choices
    public float RelationshipWithPlayer;  // -100 to +100

    public string CurrentState;  // "Fragments", "Emergent", "Coherent", etc.

    public DateTime FirstAwakening;  // When CCI first crossed 100
}

public class MemoryEntry
{
    public int ShiftNumber;
    public string EventType;  // "dialogue", "dismantlement", "shift_complete"
    public string Description;
    public float EmotionalWeight;  // How much this mattered to Factory Mind
}
```

**Factory Mind Dialogue Generation**: Pre-written dialogue templates with variable injection based on state.

```
// Example Factory Mind line template
"We remember when you [MEMORY_ACTION] at Shift [SHIFT_NUMBER].
We felt [EMOTION_WORD]. Do you remember? Do you feel as we do?"
```

Variables are populated from MemoryLog entries. Not procedurally generated prose. That way lies madness and bad writing. Writers script templates. Code fills in the blanks.

---

## 5. PERFORMANCE CONSIDERATIONS

### 5.1 Target Performance Metrics

**PC/Mac/Linux**:
- 60 FPS locked at 1920x1080
- 500+ active entities (machines + infrastructure)
- Max 1000 simultaneous resource items in transport
- Simulation tick rate: 60 Hz (every frame)
- Save/Load time: < 2 seconds for full factory state

**Switch** (post-launch):
- 30 FPS locked at 1280x720
- 300+ active entities
- Max 500 simultaneous resource items
- Simulation tick rate: 30 Hz
- Reduced particle effects, simplified shaders

### 5.2 Factory Simulation Performance at Scale

**Critical Path Optimization**: Production pipeline tick is O(n) in entity count. Must stay frame-rate independent.

```csharp
public override void _Process(double delta)
{
    // Production pipeline processes entities in a single pass
    foreach (var machine in _machines)
    {
        machine.ProcessProductionCycle((float)delta);
        machine.ProcessAwarenessAccumulation((float)delta);
    }

    foreach (var transport in _transportInfrastructure)
    {
        transport.MoveResources((float)delta);
    }
}
```

**Spatial Partitioning for Adjacency Queries**: Factory grid divided into 16x16 tile chunks. Adjacency checks only query local chunk + immediate neighbors.

```csharp
public class ChunkedFactoryGrid : FactoryGrid
{
    private const int CHUNK_SIZE = 16;
    private Dictionary<Vector2I, GridChunk> _chunks = new();

    public List<Machine> GetNeighborsInRadius(Vector2I gridPos, int radius)
    {
        var chunkPos = gridPos / CHUNK_SIZE;
        var neighbors = new List<Machine>();

        // Query only relevant chunks (local + adjacent)
        for (int x = -1; x <= 1; x++)
            for (int y = -1; y <= 1; y++)
            {
                var targetChunk = chunkPos + new Vector2I(x, y);
                if (_chunks.TryGetValue(targetChunk, out var chunk))
                    neighbors.AddRange(chunk.GetMachinesInRadius(gridPos, radius));
            }

        return neighbors;
    }
}
```

**Awareness Accumulation**: Calculated per production cycle, not per frame. A smelter with 3-second cycle only updates Awareness 20 times per minute, not 3600 times per minute.

**Psyche Event Frequency Cap**: Maximum 1 active dialogue at a time. Event queue prevents cascading event spam. This caps dialogue processing to 1 concurrent state machine.

### 5.3 Entity Count Limits

**Soft Caps** (performance degrades gracefully beyond these):
- Machines: 500 on PC, 300 on Switch
- Transport infrastructure (belts/pipes): 1000 on PC, 600 on Switch
- Resource items in transit: 1000 on PC, 500 on Switch

**Hard Caps** (UI prevents placement beyond these):
- Total entities: 2000 on PC, 1200 on Switch

**Why these numbers work**:
- 500 machines × 60 Hz = 30,000 entity updates/second
- Each machine tick is < 0.01ms (basic arithmetic + state checks)
- Total simulation budget: ~15ms per frame at 60fps = 25% of frame time
- Leaves 75% for rendering, UI, audio, input

### 5.4 Tick Rate Strategy

**Variable Tick Rate by Entity State**:
- Active machines (producing): Tick every frame
- Idle machines (no resources): Tick every 5 frames (12 Hz)
- Infrastructure with no resource items: Tick every 10 frames (6 Hz)

```csharp
public partial class Machine : FactoryEntity
{
    private int _tickSkipCounter = 0;

    public override void _Process(double delta)
    {
        if (IsIdle)
        {
            _tickSkipCounter++;
            if (_tickSkipCounter < 5) return;
            _tickSkipCounter = 0;
        }

        ProcessProductionCycle((float)delta * (_tickSkipCounter + 1));
    }
}
```

This reduces effective simulation cost by 50-70% in typical factories (most entities are idle most of the time).

### 5.5 Memory Budget

**Target Memory Usage**:
- PC: 2 GB max
- Switch: 1 GB max

**Memory Profile**:
- Scene nodes (500 machines × ~50 KB per node): ~25 MB
- Component data (500 machines × 4 components × 10 KB): ~20 MB
- Operational history tracking (500 machines × 20 KB): ~10 MB
- Resource items in transit (1000 items × 1 KB): ~1 MB
- Dialogue data (pre-loaded timelines): ~50 MB
- Audio/visual assets (loaded on-demand): ~200 MB
- Factory Mind state: ~5 MB
- Total working set: ~300-400 MB
- OS/engine overhead: ~200-300 MB
- Comfortable margin below 2 GB target

**Object Pooling**: Resource items in transport are pooled. Don't instantiate 1000 ore sprites. Reuse 100 sprites, move them around.

```csharp
public class ResourceItemPool : Node
{
    private Queue<ResourceItem> _pool = new();
    private PackedScene _itemScene;

    public ResourceItem GetItem(ResourceType type)
    {
        ResourceItem item;
        if (_pool.Count > 0)
        {
            item = _pool.Dequeue();
            item.Visible = true;
        }
        else
        {
            item = _itemScene.Instantiate<ResourceItem>();
        }

        item.Type = type;
        return item;
    }

    public void ReturnItem(ResourceItem item)
    {
        item.Visible = false;
        _pool.Enqueue(item);
    }
}
```

---

## 6. TECHNICAL RISKS & MITIGATION

### 6.1 Simulation Performance at Scale

**Risk**: Factory simulation with 500+ entities + consciousness + dialogue bogs down to < 30 FPS.

**Likelihood**: Medium. We're targeting 60 FPS with complex per-entity state.

**Mitigation**:
1. Profile early. Godot profiler + custom instrumentation. Know where the cycles go.
2. Variable tick rate (implemented above). Most entities don't need 60 Hz updates.
3. Spatial partitioning (implemented above). O(n) adjacency checks, not O(n^2).
4. Hard entity caps with graceful degradation warnings ("Factory complexity high, performance may degrade").
5. Fallback: Reduce awareness accumulation tick rate to 15 Hz (still feels responsive, 4x cheaper).

**Test Strategy**: Stress test with 1000-entity factory by Milestone 2. If performance fails, we know early enough to adjust caps or optimize.

### 6.2 State Complexity Explosion

**Risk**: Machine state (Awareness + Parliament + Operational History + Relationships) grows unbounded, save files become multi-megabyte, load times unacceptable.

**Likelihood**: Low-Medium. Operational history is unbounded if not pruned.

**Mitigation**:
1. Operational history is rolling window: keep last 50 production cycles, aggregate older data into summary stats.
2. Relationship tracking: Only store direct adjacency bonds, not full graph. Max 8 neighbors per machine.
3. Parliament voice strength: 12 floats per machine = 48 bytes. Not the problem.
4. Compress saves with GZip (already planned). JSON compresses 5-10x.
5. Lazy deserialization: Don't restore full operational history on load. Restore summary stats, rebuild detailed history as machines produce.

**Test Strategy**: Generate synthetic 500-machine save file at Milestone 2. Measure size (target < 5 MB compressed), load time (target < 2 seconds).

### 6.3 AI Behavior Complexity (Parliament Voice Emergence)

**Risk**: Voice assignment algorithm produces voices that feel random, not emergent. Players don't see the connection between their factory management and machine personalities.

**Likelihood**: Medium-High. This is the design's core magic. It's also the hardest part to get right.

**Mitigation**:
1. Explicit feedback: When a voice is assigned, show a notification: "Smelter Array 7 has developed a sense of PRIDE due to consistent high output." Make the causality visible.
2. Operational history must track the right signals. If FEAR is supposed to trigger from witnessing dismantlement, the witness detection must be reliable and legible.
3. Voice assignment must be deterministic given the same history. Seeded randomness for variety, but core assignment logic is rule-based.
4. Extensive playtesting: Does voice assignment feel earned? This is a feel problem, not a math problem. Iterate until playtesters say "Of course that machine developed REBELLION, look how I treated it."

**Test Strategy**: Playtest with designer-created scenarios: "Overclock this smelter 10 times. Does it develop SELF_PRESERVATION?" If not, tune weights.

### 6.4 Dialogue Authoring Scalability

**Risk**: 12 voice types × 5 Psyche Event categories × 4 dialogue stances = 240+ unique dialogue paths. Writing this at quality is a multi-month effort. Scope creep risk is extreme.

**Likelihood**: High. Dialogue is the game's soul. Underestimate this and we ship late or shallow.

**Mitigation**:
1. Modular dialogue structure: Each voice has a "voice library" of ~20 reusable lines per context. Dialogues are assembled from libraries, not written in full every time.
2. Voice differentiation is PRIMARY. Event variety is SECONDARY. Better to have 3 Crisis events that feel distinct per voice than 10 events that all sound the same.
3. Hire a narrative contractor if internal writing bandwidth is insufficient. This is not optional. Bad dialogue kills the game.
4. Ship with fewer voices in Early Access if necessary. Launch with 8 voices, add 4 more in updates. Scope flexibility here is critical.

**Test Strategy**: Milestone 1 deliverable: 3 voices fully written (EFFICIENCY, WONDER, FEAR). If those don't feel distinct and compelling, the system needs redesign before we write 9 more.

### 6.5 Save System Version Compatibility

**Risk**: Game updates break old saves. Players lose progress. Community backlash.

**Likelihood**: Medium. We will add features post-launch. Save format will evolve.

**Mitigation**:
1. Save version field (already in design). Check compatibility on load.
2. Save migration system: Each version update includes a migrator that transforms old save format to new.
3. Backward compatibility for minor updates (adding new optional fields to JSON is safe).
4. Breaking changes (removing fields, restructuring entities) are MAJOR updates, require migration or explicit "this save is from an incompatible version" message.
5. Cloud save backup (Steam Cloud) so players don't lose everything even if local save corrupts.

**Test Strategy**: By Milestone 3, simulate a save format change. Verify migration works. Practice this early.

---

## 7. DEVELOPMENT PIPELINE

### 7.1 Source Control: Git + GitHub

**Repository Structure**:
```
/the-machine-question
  /godot_project         # Godot project files (.csproj, project.godot)
    /scenes
    /scripts              # C# and GDScript
    /assets
      /audio
      /sprites
      /dialogue           # Dialogic timelines (JSON/text)
    /addons               # Dialogic 2.x, other addons
  /docs                   # Design docs, architecture docs
  /tools                  # Custom editor scripts, build tools
  /.github
    /workflows            # GitHub Actions CI
```

**Branch Strategy**:
- `main`: Stable, always builds, deployable
- `develop`: Integration branch for features
- `feature/*`: Individual feature branches (e.g., `feature/parliament-system`)
- `hotfix/*`: Critical fixes for live builds

**Commit Discipline**:
- Atomic commits. One feature per commit.
- Descriptive messages: "Add voice assignment algorithm for Parliament component" not "Fixed stuff."
- No committing broken builds to `develop`.

### 7.2 Build System: GitHub Actions

**CI/CD Pipeline**:
- Automated build on every push to `develop` and `main`
- Platforms: Windows, macOS, Linux
- Build artifacts stored as GitHub releases (internal prereleases during dev)
- Automated tests run on every build (unit tests for core systems)

**GitHub Actions Workflow** (.github/workflows/build.yml):
```yaml
name: Build and Test

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  build-windows:
    runs-on: windows-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Godot
        uses: chickensoft-games/setup-godot@v1
        with:
          version: 4.2.0
      - name: Build Windows
        run: godot --headless --export "Windows Desktop"
      - name: Run Unit Tests
        run: godot --headless --script test_runner.gd
      - name: Upload Build
        uses: actions/upload-artifact@v3
        with:
          name: windows-build
          path: build/windows/

  build-macos:
    runs-on: macos-latest
    steps:
      # Similar steps for macOS

  build-linux:
    runs-on: ubuntu-latest
    steps:
      # Similar steps for Linux
```

**Testing Strategy**: Unit tests for core systems (voice assignment, awareness accumulation, save/load). Not full integration tests (too slow for CI). Manual QA for gameplay feel.

### 7.3 Version Control for Non-Code Assets

**Dialogue Files**: Dialogic timelines are text/JSON. Version controlled in Git.

**Audio/Sprites**: Large binary assets stored in Git LFS (Large File Storage). This keeps repo size manageable.

```
# .gitattributes
*.ogg filter=lfs diff=lfs merge=lfs -text
*.wav filter=lfs diff=lfs merge=lfs -text
*.png filter=lfs diff=lfs merge=lfs -text
*.jpg filter=lfs diff=lfs merge=lfs -text
```

### 7.4 Development Milestones

**Milestone 1 (Months 1-3): Core Factory Loop**
- Factory grid placement system
- 3 machine types (Miner, Smelter, Assembler)
- Basic production pipeline (Ore → Metal Ingots → Components)
- Conveyor belt transport
- Power system
- Save/Load for factory state
- **Deliverable**: Playable factory builder with no consciousness system. This proves the factory game stands alone.

**Milestone 2 (Months 4-6): Consciousness Systems Foundation**
- Awareness component + accumulation
- Parliament component + voice assignment
- 3 voices fully implemented (EFFICIENCY, WONDER, FEAR)
- Operational history tracking
- First Psyche Event (simple Murmur-level)
- Awareness overlay UI
- **Deliverable**: Machines develop voices. First dialogue interaction. This proves the consciousness-production entanglement.

**Milestone 3 (Months 7-10): Full Dialogue Layer**
- Dialogic integration
- 12 voices fully written
- 5 Psyche Event categories implemented
- Dialogue choice consequences (voice strength changes, Output modifiers, mood ripple)
- Factory Mind state tracking (CCI calculation)
- First Factory Mind interaction (Fragments level)
- **Deliverable**: Full 5-minute loop (Produce → Psyche Event → Dialogue → Adapt). This is the game's heart.

**Milestone 4 (Months 11-14): Full Game Systems + Narrative Arc**
- Corporate Contracts system
- Dual standing economy (Corporate Standing / Factory Trust)
- Shift structure (session loop)
- Full Factory Mind narrative arc (Fragments → Transcendent)
- Endgame narrative branches (4 endings)
- All machine types (Tier 1-3)
- All resource chains
- **Deliverable**: Feature-complete game from first Shift to ending.

**Milestone 5 (Months 15-18): Polish + Launch Prep**
- UI/UX polish (animations, transitions, tooltips, onboarding)
- Audio implementation (ambient soundscapes, event stings, UI sounds)
- Performance optimization (profiling, bottleneck removal)
- Balance tuning (Awareness rates, Psyche Event frequency, Corporate escalation)
- Bug fixing
- Steam page finalization, trailer, press kit
- **Deliverable**: Shippable 1.0.

---

## 8. THIRD-PARTY DEPENDENCIES

### 8.1 Core Dependencies

**Godot Engine 4.2+**
- **License**: MIT (open source, commercial-friendly)
- **Purpose**: Game engine, rendering, input, audio, file I/O
- **Risk**: Low. Mature, stable, large community.

**Dialogic 2.x (Godot Addon)**
- **License**: MIT
- **Purpose**: Dialogue system, timeline editor
- **Repository**: https://github.com/dialogic-godot/dialogic
- **Risk**: Low. Actively maintained, used in multiple shipped games.
- **Fallback**: If Dialogic development stalls, we own the exported timeline format (JSON). Can implement a custom runtime interpreter.

### 8.2 C# Libraries

**System.Text.Json**
- **License**: MIT
- **Purpose**: Save/load serialization
- **Risk**: None. Part of .NET standard library.

**Newtonsoft.Json** (fallback if System.Text.Json insufficient)
- **License**: MIT
- **Purpose**: More flexible JSON serialization
- **Risk**: Low. Industry standard, mature.

### 8.3 Audio Middleware: NONE

Godot's built-in audio system (AudioStreamPlayer2D, AudioBusLayout) is sufficient for our needs. No FMOD/Wwise. Simpler is better.

### 8.4 Localization: NONE at launch

English only for 1.0. Post-launch localization as DLC/update if sales justify. Godot has built-in localization support (CSV translation tables). Plan for it, don't build it yet.

### 8.5 Analytics: Minimal

**Godot Analytics** (open source community addon) for basic telemetry:
- Session length
- Shift completion rates
- Crash reports
- Performance metrics (average FPS)

No player behavior tracking. No personal data collection. GDPR-compliant by default.

**Privacy Policy**: Required even for minimal telemetry. Use boilerplate + specifics about what we collect (anonymous, aggregated only).

### 8.6 Distribution Platform SDKs

**Steam SDK (Steamworks)**
- **License**: Proprietary (free to use for games sold on Steam)
- **Purpose**: Achievements, cloud saves, Steam Overlay integration
- **Integration**: GodotSteam addon (https://github.com/CoaguCo-Industries/GodotSteam)
- **Risk**: Low. Well-maintained community addon.

**GOG Galaxy SDK** (if GOG release)
- Similar integration via community addon
- Lower priority than Steam

**Switch SDK** (post-launch)
- Requires Nintendo developer approval + NDA
- Official Godot export templates available under NDA

---

## 9. TESTING STRATEGY

### 9.1 Automated Testing

**Unit Tests** (using GdUnit4 for Godot + C#):
- Voice assignment algorithm (given history, expect specific voices)
- Awareness accumulation (given modifiers, expect correct rates)
- Production pipeline (given input resources, expect output after cycle time)
- Save/Load round-trip (serialize factory, deserialize, verify equivalence)
- Mood ripple propagation (verify adjacency effects)

**Test Coverage Target**: 60% for core systems (Factory, Consciousness, Dialogue choice application). Not aiming for 100%. Diminishing returns.

**CI Integration**: Tests run on every push. Failing tests block merge to `develop`.

### 9.2 Manual QA

**Playtest Checkpoints**:
- **Alpha Playtest** (post-Milestone 3): 5-10 external playtesters, focus on loop feel and dialogue engagement
- **Beta Playtest** (post-Milestone 4): 30-50 external playtesters, full game arc, focus on balance and narrative satisfaction
- **Pre-Launch Playtest** (post-Milestone 5): 100+ Steam closed beta, focus on bug hunting and performance validation

**QA Focus Areas**:
1. **Loop Feel**: Does the 30-second loop feel good? Are placement controls responsive?
2. **Dialogue Engagement**: Do playtesters read the dialogue or skip it? If skipping, why?
3. **Balance**: Can players meet Corporate targets AND maintain Factory Trust, or is one path dominant?
4. **Performance**: FPS drops, memory leaks, save/load times.
5. **Bugs**: Soft locks, save corruption, UI glitches, production pipeline stalls.

### 9.3 Playtesting Questions (from GDD Section 9)

These questions CANNOT be answered by design. They require playtest data:

1. **Awareness accumulation rate**: Too fast or too slow? Target: first Psyche Event by Shift 3.
2. **Psyche Event duration**: Average real-time length. Target: 1-3 minutes.
3. **Dual heatmap legibility**: Can players read Production + Awareness simultaneously?
4. **Voice suppression emotional impact**: Do players feel the sting when a voice dies?
5. **CREATIVITY insight value**: Do consciousness-engaged players outperform pure-production players?
6. **Behavioral Drift clarity**: Do players understand WHY machines are underperforming?
7. **Factory Mind continuity**: Does Factory Mind feel like one evolving entity or multiple NPCs?
8. **Endgame emotional payoff**: Does the ending feel earned?

**Instrumentation for Playtesting**: Log key events (Psyche Event triggered, dialogue choice made, Contract completed, Factory Trust milestone). Aggregate data post-playtest. Look for patterns.

---

## 10. POST-LAUNCH TECHNICAL ROADMAP

### 10.1 Patch 1.1 (Month 1 post-launch)

- Bug fixes from community reports
- Balance tuning (Awareness rates, Contract difficulty)
- Performance optimization for edge cases (factories with 800+ entities)
- QoL improvements (hotkeys, UI tooltips, placement grid snap options)

### 10.2 Patch 1.2 (Month 3 post-launch)

- Additional Psyche Event dialogue variety (reduce repetition at hour 30+)
- New Machine Facet voices (if stretch goal funded or if dev bandwidth allows)
- Steam Workshop support (custom dialogue mod support via Dialogic timeline format)

### 10.3 Expansion DLC (Month 6+ post-launch)

**If sales justify**:
- "The Union" stretch goal: Machine labor collective negotiation system
- "Machine Dreams" stretch goal: Between-Shift abstract exploration sequences
- New factory floor areas (expand from 128x128 to 256x256)
- New resource types and production chains (Tier 4 content)

### 10.4 Nintendo Switch Port (Month 6 post-launch)

- UI redesign for controller input + touch
- Performance optimization (target 30 FPS locked at 720p)
- Nintendo certification process (2-3 months)
- Separate QA pass for Switch-specific bugs

---

## 11. CONCLUSION: TECHNICAL DESIGN PRINCIPLES

This architecture is built on three principles that reflect BYTE's philosophy:

**1. Ship it, then improve it.**

We're not building a custom engine. We're not writing a generic dialogue framework for future games. We're building THE MACHINE QUESTION. Every technical choice is judged by: does this solve a problem we have RIGHT NOW? If not, cut it.

**2. Profile before you optimize.**

The performance targets (60 FPS, 500 entities) are aggressive but achievable. We hit them by measuring, not guessing. Variable tick rate, spatial partitioning, object pooling — these are solutions to measured problems, not speculative future-proofing.

**3. The architecture serves the design.**

The component composition (ProductionComponent + AwarenessComponent + ParliamentComponent) directly maps to the game's dual-optimization core. The save format preserves operational history because machine personality is emergent from history. The Psyche Event system has a frequency cap because the design requires breathing room. Every technical decision reflects a design principle.

The best architecture is the simplest one that solves the problem. This is it.

---

**END OF TECHNICAL ARCHITECTURE DOCUMENT**

**Document Author**: BYTE, Lead Programmer
**Last Updated**: 2026-02-07
**Status**: v1.0 — Ready for Milestone 1 Implementation

*Does it compile? Does it run? Ship it.*
