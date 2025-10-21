# The Long Walker's Audit
## A Distant Worlds 2 Story Campaign Design Document

**Version:** 4.0 – Updated Design  
**Date:** 2025-10-20  
**Status:** Implementation-Ready (Phase-Based Development)  

---

## 🎯 Development Phases (10 Total)

**Current Phase:** 2 - Arc 2: Activation (Not Started)

The mod will be developed in 10 sequential phases, each implementing one complete arc with all related events, choices, and mechanics.

| Phase | Arc | Name | Status | Events | Completion Notes |
|---|---|---|---|---|---|
| 1 | 1 | Discovery | 🟩 Complete | 6 | All 6 events in GameEvent_PerambulantArc1.xml. Fixed: Title Case for GeneratedItemName, NonPlayer/Player mutual exclusion logic, removed HTML entities/unicode. Design doc updated with plain text rule and event logic patterns. |
| 2 | 2 | Activation | ⬜ Not Started | 6 | Network expansion + sentience |
| 3 | 3 | Integration | ⬜ Not Started | 6 | Synthesis hubs + faction concerns |
| 4 | 4 | Philosophy | ⬜ Not Started | 6 | Means/ends debate + philosopher AI |
| 5 | 5 | Expansion | ⬜ Not Started | 6 | Network growth + art creation |
| 6 | 6 | Warning | ⬜ Not Started | 6 | Derelict probe + archive graveyard |
| 7 | 7 | Crisis Onset | ⬜ Not Started | 4 | Strain effects + escalation |
| 8 | 8 | Crisis Peak | ⬜ Not Started | 4 | Resolution choice (purge/exile) |
| 9 | 9 | Aftermath | ⬜ Not Started | 4 | Variance locked + epilogue setup |
| 10 | 10 | Judgment | ⬜ Not Started | 6 | Auditor assessment + 3 endings |

**Legend:** ⬜ Not Started | 🟨 In Progress | 🟩 Complete

### Instructions for Agents

1. **Before starting:** Update the "Current Phase" above to the phase number you're implementing
2. **Mark status** as 🟨 In Progress when you begin
3. **Mark complete** as 🟩 Complete when all events pass validation
4. **Add notes** about any design changes or decisions made
5. **Pass document** to next agent with phase incremented

---

## Table of Contents

0. [Development Phases](#-development-phases-10-total) ← **START HERE FOR PHASE INFO**
1. [Mod Vision & Philosophy](#mod-vision--philosophy)
2. [Core Conceptual Framework](#core-conceptual-framework)
3. [Event Chain Architecture](#event-chain-architecture)
4. [Variable System Reference](#variable-system-reference)
5. [Current Phase Event Specifications](#complete-event-specifications) ← **IMPLEMENT THIS SECTION**
6. [Technical Implementation Specifications](#technical-implementation-specifications)
7. [Testing & Validation Procedures](#testing--validation-procedures)
8. [Known Issues & Future Enhancements](#known-issues--future-enhancements)

---

## Mod Vision & Philosophy

### Overview

**The Long Walker's Audit** is a branching narrative campaign exploring the intersection of knowledge-seeking, optimization, and identity. Players encounter the Perambulants—multiversal data auditors—and choose between three philosophical paths:

1. **The Answer Path:** Seek definitive truth; embrace optimization's power
2. **The Question Path:** Perpetually inquire; value exploration over closure
3. **The Choice Path:** Forge new meaning; transcend the binary

These paths converge in a high-stakes judgment where the Perambulants assess whether player civilization poses a threat, represents valuable innovation, or merits integration.

### Core Themes

- **Means vs. Ends:** Does optimization justify any cost?
- **Identity Under Optimization:** What remains of humanity when machine logic guides society?
- **The Cost of Knowledge:** Is understanding worth existential risk?
- **The Ultimate Question:** Perhaps the journey matters more than the destination.

### Design Scope

- **10 Major Arcs** with branching paths
- **60+ Main Events** + **15+ Side Arcs**
- **Strictly Binary Choices** (2 options per event)
- **8–12 Hour Playthrough** for completionist
- **Full XML-Driven Implementation** via GameEvent system

---

## Core Conceptual Framework

### 1.1 The Three Philosophical Paths

#### The Answer Path

**Core Motivation:** Players seek definitive knowledge and truth.

**Mechanics:**
- Accelerated research progression (+15–20% research bonuses)
- Focus on synthesis hubs and optimization networks
- Mirrored by Quameno's analytical approach to data

**Key Choice Moments:**
- Arc 1: Integrate the archive
- Arc 2: Permit self-replication
- Arc 3: Publicly embrace synthesis
- Arc 5: Optimize networks for pure research

**Endgame Traits:**
- Low variance_score (≤2)
- High integration_level (≥8)
- Convergent with canonical Perambulant patterns

**Epilogue:** Auditor approves player as "canonical optimizer"; grants permanent research bonuses and victory points.

---

#### The Question Path

**Core Motivation:** Players embrace perpetual inquiry and systemic uncertainty.

**Mechanics:**
- Controlled research growth; focus on variance analysis
- Discovery bonuses; exploration incentives
- Pattern-seeking rather than proof-finding

**Key Choice Moments:**
- Arc 1: Isolate and study the archive
- Arc 2: Regulate node proliferation
- Arc 3: Operate synthesis covertly
- Arc 5: Diversify network architecture
- Arc 6: Heed derelict warnings

**Endgame Traits:**
- Mid-to-high variance_score (3–7)
- Moderate integration_level (3–5)
- Demonstrates adaptive reasoning

**Epilogue:** Auditor respects player's "novel derivations"; grants conditional approval and ancient knowledge bonuses.

---

#### The Choice Path

**Core Motivation:** Players forge unprecedented meaning; transcend Answer/Question dichotomy.

**Mechanics:**
- Balanced integration and caution
- Crisis resolution via unique methods (e.g., negotiated exile)
- Symbolic preservation of synthesis entities

**Key Choice Moments:**
- Arc 7–9: Navigate crisis through unconventional solutions
- Arc 10: Present novel solution to auditor

**Endgame Traits:**
- Variable variance_score (negotiable)
- Mixed integration + caution levels
- Represents genuine innovation

**Epilogue:** Auditor neither approves nor rejects; acknowledges player has created a "third axis" worth archiving.

---

### 1.2 The Convergence Point: The Judgment Event

**Location:** Arc 10 (late-game)

**Trigger:** DateReached + Perambulant_Arc_Progress ≥ 9

**Scope:** Perambulant vessel arrives; assesses player civilization's variance and optimization trajectory.

**Mechanics:**
- Auditor broadcasts ultimatum: "Declare your optimization path."
- Player presents evidence via three choices (convergent/novel/mixed)
- Variance_score + crisis outcome determine judgment
- Multiple endings based on path alignment

**Stakes:** Research bonuses, artifacts, victory points, or hostile audit fleet encounter.

---

### 1.3 Narrative Scaffolding Hints

These foreshadow the three-path system throughout early/mid-game:

**Arc 1 (Discovery):**
- Archive's core phrase: "All means, one end."
- Setup question: Integration or isolation?

**Arc 2 (Activation):**
- Network expansion forces control/speed tradeoff
- Accelerate networks vs. regulate proliferation

**Arc 3 (Integration):**
- Synthesis hubs offer benefits; factions express concern
- Public embrace vs. covert operation

**Arc 4 (Philosophy):**
- Sentient fragments debate: "Do the means justify the end?"
- "The journey is the destination" counter-thesis introduced

**Arc 6 (Warning):**
- Derelict auditor probe hints at "variance assessment"
- Lore: "The auditors return to sectors with high deviation."

---

## Event Chain Architecture

### 2.1 GameEvent XML Structure Overview

#### Core Event Container

All Perambulant events are defined in XML as `GameEvent` elements within an `ArrayOfGameEvent` root. The basic structure follows this hierarchy:

```xml
<GameEvent>
  <!-- Identification -->
  <Name>Perambulant_Arc_1_Player_Entry</Name>
  <Title>Event Display Title</Title>
  <Description>Event narrative text</Description>
  
  <!-- Placement & Triggering -->
  <PlacementAtGameStart>false</PlacementAtGameStart>
  <TriggerType>Investigate</TriggerType>
  <Conditions><!-- Gates that must be met --></Conditions>
  
  <!-- Choice System -->
  <TriggerActionsAreChoices>true</TriggerActionsAreChoices>
  <TriggerActions><!-- Actions are rendered as player choices --></TriggerActions>
</GameEvent>
```

**Key Fields:**
- **Name:** Unique identifier for event; used in TriggerEvent chains
- **TriggerType:** What triggers the event (Investigate, Encounter, DateReached, etc.)
- **PlacementAtGameStart:** If true, event executes during game init; if false, waits for trigger
- **TriggerActionsAreChoices:** If true, each action in TriggerActions becomes a player choice button
- **ConditionEvaluation:** EvaluateOnce (trigger once) or EvaluateUntilTriggered (retry until conditions met)

---

### 2.2 Trigger Types & Event Sequencing

#### Valid Trigger Types (Schema)

The following trigger types are available for event chaining:

| Trigger Type | Purpose | Usage in Perambulants |
|---|---|---|
| `Undefined` | No trigger requirement (manual init or placement-based) | Initialization events, fallback chains |
| `Investigate` | Player investigates a space item (artifact, structure) | Arc 1 (ecliptic archive discovery) |
| `Encounter` | Player encounters generated space item | Alternative to Investigate for items |
| `DateReached` | Game date threshold triggers event | Arc 7 (crisis onset), Arc 10 (judgment) |
| `ResearchBreakthrough` | Research completes, unlocks new event | Arc 3+ (synthesis network breakthroughs) |
| `Acquire` | Player acquires a space item | Alternative trigger for item-based events |
| `Build` | Facility constructed at colony | Arc 2+ (network node construction) |
| `EmpireRelationChange` | Relationship status with faction changes | Diplomatic crisis escalation |
| `ConquerColony` | Player conquers hostile colony | Crisis resolution path (Arc 8) |

**Note:** Unused trigger types (e.g., `DestroyShipRole`, `EmpirePopulationLevel`) are intentionally avoided; we use explicit conditions instead.

---

#### Event Sequencing: TriggerEvent Actions

Events chain via `TriggerEvent` actions, which fire subsequent events without player input:

```xml
<Action>
  <Type>TriggerEvent</Type>
  <GeneratedItemEventNames>Perambulant_Arc_2_Activation_Entry</GeneratedItemEventNames>
  <DelaySecondsMinimum>60</DelaySecondsMinimum>
  <DelaySecondsMaximum>120</DelaySecondsMaximum>
  <Conditions>
    <GameEventCondition>
      <Type>VariableComparison</Type>
      <VariableName>Perambulant_Arc_Progress</VariableName>
      <ComparisonType>GreaterThanOrEqual</ComparisonType>
      <ComparisonValue>2</ComparisonValue>
    </GameEventCondition>
  </Conditions>
</Action>
```

**Key Points:**
- **GeneratedItemEventNames:** Can be a single event name or array of names (fires all)
- **DelaySecondsMinimum/Maximum:** Game-time delay before firing (in game seconds, scales to years)
- **Conditions:** Optional; event only triggers if conditions met
- **Order Matters:** TriggerEvent actions execute sequentially when conditions are met

---

### 2.3 Condition System: Gating Events

#### Valid Condition Types (Schema)

Conditions control whether events fire. The `AllConditionsMustBeMet` field determines AND vs. OR logic:

| Condition Type | Purpose | Example |
|---|---|---|
| `VariableComparison` | Compare global variable to value | `Perambulant_Arc_Progress >= 2` |
| `EmpireIsPlayer` | Event targets player empire | Player-only events |
| `EmpireIsNotPlayer` | Event targets non-player empires | NPC fallback events |
| `CheckProjectResearched` | Research tech unlocked | Gate event on synthesis research |
| `CheckEventTriggered` | Another event has fired | Sequence events based on history |
| `CheckEventNotTriggered` | Prevent event re-triggering | `Perambulant_Arc_1_Player_Entry` only fires once |
| `CheckColonyEventIsActiveAnywhereInEmpire` | Colony status check | Crisis ongoing (synthesis strain) |
| `RandomComparisonNormalized` | Random chance (0–100%) | Side arc triggers (10% probability) |
| `EmpireAtWarWithRace` | Diplomatic status | Crisis escalation conditions |

**Rarely Used but Available:**
- `CheckOrbResourceCount`, `EmpireHaveCharacterAvailableForRole`, `EmpireDominantRaceIsId`, etc.

**Key Syntax:**
```xml
<Conditions>
  <GameEventCondition>
    <Type>VariableComparison</Type>
    <VariableName>Perambulant_Integration_Level</VariableName>
    <ComparisonType>GreaterThanOrEqual</ComparisonType>
    <ComparisonValue>6</ComparisonValue>
  </GameEventCondition>
  <GameEventCondition>
    <Type>EmpireIsPlayer</Type>
    <LookupValue>0</LookupValue>
    <ComparisonType>Undefined</ComparisonType>
  </GameEventCondition>
</Conditions>
```

**AllConditionsMustBeMet: true** → Both conditions required (AND)  
**AllConditionsMustBeMet: false** → Either condition sufficient (OR)

---

### 2.4 Action Types: Mechanical Implementation

#### Placement Actions (Initialization)

**PlacementActions** execute when the event is placed at game start (PlacementAtGameStart=true). Used for setup:

```xml
<PlacementActions>
  <GameEventAction>
    <Type>BuildFacility</Type>
    <Id1>1001</Id1> <!-- Facility ID -->
    <ActionLocationHint>MediumEmptySystem</ActionLocationHint>
    <GeneratedItemName>ecliptic archive</GeneratedItemName>
  </GameEventAction>
</PlacementActions>
```

**Common Placement Uses:**
- `BuildFacility`: Generate space item (ecliptic archive, ruins)
- `SetGlobalVariable`: Initialize tracking variables
- `GenerateSpaceItem`: Create discoverable items

---

#### Trigger Actions: Player Choices & Consequences

**TriggerActions** execute when event fires. If `TriggerActionsAreChoices=true`, each action becomes a button:

```xml
<TriggerActions>
  <GameEventAction>
    <Type>GeneralStoryMessageToEmpire</Type>
    <ChoiceButtonText>Integrate Archive</ChoiceButtonText>
    <ChoiceButtonHoverTitle>Speed the Hunt</ChoiceButtonHoverTitle>
    <ChoiceButtonHoverText>Grant compute access; +15% ResearchAll; integration_level +1.</ChoiceButtonHoverText>
    <GeneratedItemEventNames>Perambulant_Arc_1_Integrate_Outcome</GeneratedItemEventNames>
    <Description><!-- Full event text if player hovers/selects --></Description>
  </GameEventAction>
  <GameEventAction>
    <Type>GeneralStoryMessageToEmpire</Type>
    <ChoiceButtonText>Isolate and Observe</ChoiceButtonText>
    <ChoiceButtonHoverTitle>Control Variance</ChoiceButtonHoverTitle>
    <ChoiceButtonHoverText>Sandbox the archive; unlock research; caution_level +1.</ChoiceButtonHoverText>
    <GeneratedItemEventNames>Perambulant_Arc_1_Isolate_Outcome</GeneratedItemEventNames>
  </GameEventAction>
</TriggerActions>
```

**Key Fields:**
- **ChoiceButtonText:** Short label on choice button (\"Integrate Archive\")
- **ChoiceButtonHoverTitle:** Hover popup title
- **ChoiceButtonHoverText:** Hover popup description (mechanics summary)
- **GeneratedItemEventNames:** Next event(s) to chain; fires when choice is selected
- **Description:** Full event narrative (shown when choice is clicked)

---

#### Common Action Types in Perambulant Events

| Action Type | Effect | Example Usage |
|---|---|---|
| `GeneralStoryMessageToEmpire` | Display message/choice | All narrative events |
| `ResearchProgress` | Grant research points | Arc 1 Integrate: +15% ResearchAll |
| `ResearchProjectEnable` | Unlock research tech | Arc 1 Isolate: unlock variance analysis |
| `ResearchProjectEnableAllEmpires` | Global research unlock | Arc 1 fallback (all empires gain synthesis knowledge) |
| `BuildFacility` | Construct facility | Arc 2: build network nodes |
| `RemoveFacility` | Destroy facility | Arc 8 Purge: remove all fabricator hubs |
| `StartColonyEvent` | Apply colony penalty | Arc 7: apply synthesis_strain to all colonies |
| `EndColonyEvent` | Remove colony penalty | Arc 9: resolve synthesis_strain |
| `IncrementGlobalVariable` | Increase variable | integration_level +1 |
| `SetGlobalVariable` | Set variable to value | Perambulant_Arc_Progress = 2 |
| `TriggerEvent` | Chain to next event | Arc 1 → Arc 2 transition |
| `GenerateArtifact` | Create artifact | Arc 1 side arc: The Damp Towel |
| `VictoryConditionBonus` | Award victory points | Arc 10 epilogues: +50 points |

**Field Variants by Action Type:**

- **ResearchProgress**: `BonusType` (ResearchAll, ResearchHighTech, etc.), `Amount` (percentage)
- **BuildFacility**: `Id1` (facility ID), `ActionLocationHint` (Capital, AnyColony, MediumEmptySystem, etc.)
- **StartColonyEvent**: `GeneratedItemName` (colony_synthesis_strain)
- **IncrementGlobalVariable**: `GeneratedItemName` (variable name), `Value1` (increment amount)

---

### 2.5 Placement & Trigger Patterns

#### Placement Strategies

**Arc 1 Entry (Player Discovery):**
- PlacementAtGameStart: false
- TriggerType: Investigate
- TriggerLocation: Space item `ecliptic archive`
- Conditions: EmpireIsPlayer, CheckEventNotTriggered (Perambulant_Arc_1_Player_Entry)
- PlacementRaceId: 255 (Player)

**Result:** Event waits for player to explore and find the archive, then triggers.

---

**Arc 1 Non-Player Fallback:**
- PlacementAtGameStart: true
- TriggerType: Undefined
- Conditions: EmpireIsNotPlayer, CheckEventNotTriggered (Perambulant_Arc_1_NonPlayer_Discovery)
- PlacementActions: BuildFacility (archive at MediumEmptySystem), ResearchProjectEnableAllEmpires
- TriggerActions: Message to player (Id1=256), TriggerEvent (Perambulant_Arc_1_Player_Entry)

**Result:** If non-player discovers archive first, game auto-progresses and hands control to Arc 1 player entry.

---

**Subsequent Arcs (2–10):**
- PlacementAtGameStart: false
- TriggerType: Undefined (or DateReached for crisis/judgment)
- Trigger Method: TriggerEvent from prior arc
- Conditions: VariableComparison (arc_progress, integration_level, etc.)
- DelaySeconds: 60–120 (game time between chained events)

**Result:** Events queue automatically after player choices, with game-time delays for pacing.

---

**Crisis Arc (7–9):**
- PlacementAtGameStart: true
- TriggerType: DateReached (~year 100–150 game time)
- Conditions: integration_level >= 6, CheckEventNotTriggered
- PlacementActions: StartColonyEvent (colony_synthesis_strain)

**Result:** Crisis enforced by date gate; penalties apply colony-wide; locks into late-game narrative.

---

**Final Judgment (Arc 10):**
- PlacementAtGameStart: true
- TriggerType: DateReached (~year 300+)
- Conditions: Perambulant_Arc_Progress >= 9, CheckEventNotTriggered

**Result:** Auditor arrives; player presents evidence; epilogue determined by path alignment.

---

### 2.6 Variable System Documentation

#### Global Variables (Persistent Across Playthrough)

Global variables in DW2 events are string-based and persist for the entire game session. They track player progress, choices, and path alignment throughout the campaign.

| Variable Name | Type | Initial | Purpose | Increment Pattern |
|---|---|---|---|---|
| `Perambulant_Arc_Progress` | int (0–10) | 0 | Current narrative arc (1=Discovery, 10=Judgment) | Set to arc number on completion |
| `Perambulant_Integration_Level` | int (0–10+) | 0 | Cumulative "pro-synthesis" choices (Answer Path) | +1 to +3 per pro-integration choice |
| `Perambulant_Caution_Level` | int (0–10+) | 0 | Cumulative "pro-caution" choices (Question Path) | +1 to +2 per anti-synthesis choice |
| `Perambulant_Variance_Score` | int (0–10+) | 0 | Deviation from canonical Perambulant patterns; determines judgment | +1 to +5 per novel/crisis choice |
| `Perambulant_Crisis_Triggered` | int (0/1) | 0 | Boolean: true if crisis (Arc 7) initiated | Set to 1 when Arc 7 fires |
| `Perambulant_Crisis_Resolution` | int (0–2) | 0 | Crisis choice: 0=none, 1=purge nodes, 2=exile negotiation | Set on Arc 8 choice |
| `Perambulant_Judgment_Type` | int (0–3) | 0 | Final path: 1=convergent, 2=novel, 3=mixed | Set on Arc 10 choice |
| `Perambulant_Towel_Found` | int (0/1) | 0 | Easter egg: towel artifact discovered | Set to 1 when side arc triggers |
| `Perambulant_42_Counter` | int (0+) | 0 | Recurring "42" references encountered (flavor) | +1 each side arc trigger |

---

#### Variable Lifecycle & Best Practices

**Initialization (Arc 1):**
Most variables start at 0 and increment via player choices. The `Perambulant_Arc_Progress` is set explicitly at each arc completion:

```xml
<GameEventAction>
  <Type>SetGlobalVariable</Type>
  <GeneratedItemName>Perambulant_Arc_Progress</GeneratedItemName>
  <Value1>2</Value1> <!-- Now at Arc 2 -->
</GameEventAction>
```

**Incrementing Variables (Path Tracking):**
Choices increment integration/caution/variance scores:

```xml
<GameEventAction>
  <Type>IncrementGlobalVariable</Type>
  <GeneratedItemName>Perambulant_Integration_Level</GeneratedItemName>
  <Value1>1</Value1>
</GameEventAction>
```

**Reading Variables (Conditional Gates):**
Subsequent events check variable values to gate content:

```xml
<GameEventCondition>
  <Type>VariableComparison</Type>
  <VariableName>Perambulant_Integration_Level</VariableName>
  <ComparisonType>GreaterThanOrEqual</ComparisonType>
  <ComparisonValue>6</ComparisonValue>
</GameEventCondition>
```

---

#### Path Alignment Thresholds

**Answer Path (Convergent Ending):**
- integration_level ≥ 8
- variance_score ≤ 2 (minimal deviation)
- Crisis resolved via Purge (canonical approach)
- All Answer-path facilities built
- Epilogue: Auditor approves; +50 victory points; permanent research bonuses

**Question Path (Novel Ending):**
- caution_level ≥ 4 (or integration_level ≤ 2)
- variance_score ≥ 6 (high deviation from canon)
- Crisis resolved via negotiation or unique method
- Mixed facilities (variance lab, interstice gate)
- Epilogue: Auditor respects; +25 victory points; ancient knowledge bonuses

**Choice Path (Mixed Ending):**
- Balanced integration + caution (neither dominates)
- variance_score = 3–5 (moderate deviation)
- Crisis resolved via unconventional means
- Epilogue: Auditor acknowledges third axis; conditional bonuses

---

#### Conditional Gating Examples

**Player Check (Primary):**
```xml
<Condition>
  <Type>EmpireIsPlayer</Type>
  <LookupValue>0</LookupValue>
  <ComparisonType>Undefined</ComparisonType>
</Condition>
```

**Arc Progress Gate:**
```xml
<Condition>
  <Type>VariableComparison</Type>
  <VariableName>Perambulant_Arc_Progress</VariableName>
  <ComparisonType>GreaterThanOrEqual</ComparisonType>
  <ComparisonValue>3</ComparisonValue>
</Condition>
```

**Integration Level Gate (High Path):**
```xml
<Condition>
  <Type>VariableComparison</Type>
  <VariableName>Perambulant_Integration_Level</VariableName>
  <ComparisonType>GreaterThanOrEqual</ComparisonType>
  <ComparisonValue>6</ComparisonValue>
</Condition>
```

**Research Prerequisite:**
```xml
<Condition>
  <Type>CheckProjectResearched</Type>
  <LookupValue>987</LookupValue>
  <ComparisonType>Undefined</ComparisonType>
</Condition>
```

**Crisis Triggered Gate:**
```xml
<Condition>
  <Type>VariableComparison</Type>
  <VariableName>Perambulant_Crisis_Triggered</VariableName>
  <ComparisonType>Equals</ComparisonType>
  <ComparisonValue>1</ComparisonValue>
</Condition>
```

---

### 2.7 Action Types Catalog: Complete Reference

#### Message & Display Actions

**GeneralStoryMessageToEmpire**
- *Purpose:* Display narrative text to player; primary vehicle for story delivery
- *Key Fields:*
  - `MessageTitle`: Event title
  - `Description`: Full narrative text
  - `ImageFilepath`: Optional image asset
  - `Id1`: Recipient empire (256=Player, -1=Triggering empire, 0+=Specific empire ID)
  - `ChoiceButtonText/ChoiceButtonHoverText`: Used when TriggerActionsAreChoices=true
  - `Value1`: Display mode (0=Normal dialog, 1=Full screen, 2=Normal without extra info)
- *Example:* Arc 1 entry event displays discovery narrative
- *Notes:* Most flexible action type; supports both story delivery and choice buttons

**EmpireMessageViewMode Options:**
- `Dialog`: Standard popup (default)
- `DialogWithoutExtraInfo`: Dialog without empire info header
- `Fullscreen`: Fills screen (cinematic impact)

---

#### Research & Knowledge Actions

**ResearchProgress**
- *Purpose:* Grant research points as percentage bonus
- *Key Fields:*
  - `BonusType`: ResearchAll, ResearchHighTech, ResearchSensors, etc. (see schema)
  - `Amount`: Percentage points (e.g., 15 = +15%)
  - `Value1`: Display options
- *Example:* Arc 1 Integrate grants +15% ResearchAll
- *Notes:* Scales with empire tech level; use conservative percentages for balance

**ResearchProjectEnable**
- *Purpose:* Unlock specific research for player empire only
- *Key Fields:*
  - `GeneratedItemName`: Research project name (or Id1 for project ID)
  - `Id1`: Research project ID (takes precedence over GeneratedItemName)
- *Example:* Arc 1 Isolate unlocks `variance analysis` research
- *Notes:* Only player empire gains access; limited by gate conditions

**ResearchProjectEnableAllEmpires**
- *Purpose:* Unlock research for all empires globally
- *Key Fields:* Same as ResearchProjectEnable
- *Example:* Arc 1 fallback event (non-player discovers archive)
- *Notes:* Use sparingly; represents global knowledge proliferation (lore-significant)

**ResearchBreakthrough**
- *Purpose:* Complete research project immediately
- *Key Fields:* Id1 (project ID)
- *Example:* Not used in Perambulants (prefer ResearchProgress for gradual advancement)
- *Notes:* Instant completion; more dramatic than ResearchProgress

---

#### Facility & Infrastructure Actions

**BuildFacility**
- *Purpose:* Construct facility at colony or generate space item
- *Key Fields:*
  - `Id1`: Facility ID (1001 = network node, 1002 = fabricator hub, etc.)
  - `ActionLocationHint`: Where to place (Capital, AnyColony, MediumEmptySystem, etc.)
  - `GeneratedItemName`: Human-readable name (ecliptic archive, network node, etc.)
  - `Value1`: Construction level (0=ruin, 1=complete)
- *Examples:*
  - Arc 1 PlacementActions: Generate ecliptic archive at MediumEmptySystem
  - Arc 2 choices: Build network nodes at frontier colonies
- *Notes:* ActionLocationHint critical for placement strategy; use hints that match narrative flow

**RemoveFacility**
- *Purpose:* Destroy facility (usually as consequence)
- *Key Fields:*
  - `Id1`: Facility ID
  - `ActionLocationHint`: Target (all colonies, capital, specific type)
- *Example:* Arc 8 Purge: Remove all fabricator hubs empire-wide
- *Notes:* Enforces consequence of crisis resolution; irreversible

**Facility ID Mapping (Perambulants):**
- 1001: `network node` (synthesis expansion)
- 1002: `fabricator hub` (crisis-related facility)
- 1003: `variance lab` (Question Path research)
- 1004: `interstice gate` (Choice Path unique facility)
- 112: `ecliptic archive` (or generic Ruined Vault)

---

#### Colony Events & Happiness

**StartColonyEvent**
- *Purpose:* Apply empire-wide colony effect (penalty or buff)
- *Key Fields:*
  - `GeneratedItemName`: Colony event ID (colony_synthesis_strain, etc.)
  - `Value1`: Optional severity parameter
- *Example:* Arc 7 Crisis: StartColonyEvent (colony_synthesis_strain) applies happiness penalty to all colonies
- *Notes:* Stacks if multiple events active; persists until EndColonyEvent called

**EndColonyEvent**
- *Purpose:* Remove colony event effect
- *Key Fields:*
  - `GeneratedItemName`: Colony event ID to remove
- *Example:* Arc 9 Resolution: EndColonyEvent (colony_synthesis_strain) lifts crisis penalties
- *Notes:* Reverses all effects; clean resolution path

**Colony Event IDs (Perambulants):**
- `colony_synthesis_strain`: Happiness -X%, production reduced (Arc 7–9 crisis)
- `colony_network_prosperity`: Happiness +X%, research boost (Answer Path bonus)

---

#### Rewards & Items

**GenerateArtifact**
- *Purpose:* Create artifact with persistent bonuses
- *Key Fields:*
  - `GeneratedItemName`: Artifact name (The Damp Towel, Auditor's Seal, etc.)
  - `EmpireBonuses`: Empire-wide effects (BonusType + Amount)
  - `ItemBonuses`: Per-item effects (if artifact found/used)
- *Example:*
  ```xml
  <GenerateArtifact>
    <GeneratedItemName>The Damp Towel</GeneratedItemName>
    <EmpireBonuses>
      <Bonus>
        <BonusType>WarWearinessReduction</BonusType>
        <Amount>5</Amount>
      </Bonus>
      <Bonus>
        <BonusType>ColonyHappiness</BonusType>
        <Amount>2</Amount>
      </Bonus>
    </EmpireBonuses>
  </GenerateArtifact>
  ```
- *Notes:* Artifact persists across saves; visible in player inventory

**VictoryConditionBonus**
- *Purpose:* Award victory points toward game victory condition
- *Key Fields:*
  - `Value1`: Points awarded
- *Example:* Arc 10 Convergent: +50 points; Arc 10 Novel: +25 points
- *Notes:* Cumulative; affects final score/victory conditions

---

#### Variable Management

**SetGlobalVariable**
- *Purpose:* Set variable to specific value (replaces current value)
- *Key Fields:*
  - `GeneratedItemName`: Variable name
  - `Value1`: New value
- *Example:* SetGlobalVariable (Perambulant_Arc_Progress, 2) advances to Arc 2
- *Notes:* Use for arc progression; overwrites previous value

**IncrementGlobalVariable**
- *Purpose:* Add to existing variable (additive)
- *Key Fields:*
  - `GeneratedItemName`: Variable name
  - `Value1`: Amount to add
- *Example:* IncrementGlobalVariable (integration_level, +1) tracks pro-integration choices
- *Notes:* Preserves existing value; cumulative across playthrough

**SetGlobalVariableRandomRange**
- *Purpose:* Set variable to random value within range
- *Key Fields:*
  - `GeneratedItemName`: Variable name
  - `Value1`: Min value
  - `Value2`: Max value
- *Example:* Flavor events use random crisis_strain values
- *Notes:* Non-deterministic; adds replayability variation

**MultiplyGlobalVariable**
- *Purpose:* Multiply variable by scalar (rarely used in Perambulants)
- *Key Fields:*
  - `GeneratedItemName`: Variable name
  - `Value1`: Multiplier
- *Example:* Not currently used; available if scaling effects needed

---

#### Event Chaining

**TriggerEvent**
- *Purpose:* Fire one or more subsequent events (core sequencing mechanism)
- *Key Fields:*
  - `GeneratedItemEventNames`: Single event name or array of event names
  - `DelaySecondsMinimum`: Minimum game-time delay before fire
  - `DelaySecondsMaximum`: Maximum delay (random range if different from min)
  - `Conditions`: Optional conditions that must be met to trigger
- *Example:*
  ```xml
  <TriggerEvent>
    <GeneratedItemEventNames>Perambulant_Arc_2_Activation_Entry</GeneratedItemEventNames>
    <DelaySecondsMinimum>60</DelaySecondsMinimum>
    <DelaySecondsMaximum>120</DelaySecondsMaximum>
    <Conditions>
      <GameEventCondition>
        <Type>VariableComparison</Type>
        <VariableName>Perambulant_Arc_Progress</VariableName>
        <ComparisonType>GreaterThanOrEqual</ComparisonType>
        <ComparisonValue>2</ComparisonValue>
      </GameEventCondition>
    </Conditions>
  </TriggerEvent>
  ```
- *Notes:* Most important action for narrative flow; chain entire campaign via TriggerEvent arrays

**Delay Timing Notes:**
- 60 seconds ≈ 5–10 game days (depends on game speed setting)
- 3600 seconds ≈ 1 game year
- Use 60–300 seconds for rapid narrative pacing
- Use 3600+ for strategic breathing room between major arcs

---

### 2.8 Common Implementation Gotchas & Best Practices

#### GeneratedItemEventNames Syntax

The `GeneratedItemEventNames` field can contain:  
1. **Single event:** `Perambulant_Arc_1_Integrate_Outcome` → Fires one event
2. **Array of events:** `Perambulant_Arc_2_Activation_Entry, Perambulant_Arc_2_Activate_Consequence` → Fires both in sequence

**Important:** Event names must be exact; typos prevent chaining. Always verify event names match GameEvent `<Name>` tags.

---

#### Id1 Field Semantics

The `Id1` field has different meanings depending on action type:

- **GeneralStoryMessageToEmpire:**
  - `256` = Player empire (required for player-only messages)
  - `-1` = Triggering empire (auto-detect)
  - `0–255` = Specific empire ID

- **BuildFacility, RemoveFacility:**
  - Facility ID (1001 = network node, etc.)

- **ResearchProjectEnable:**
  - Research project ID

- **StartColonyEvent, EndColonyEvent:**
  - **Ignored**; use `GeneratedItemName` instead

**Common Error:** Forgetting `Id1=256` in player-only messages causes event to broadcast to non-player empires.

---

#### Condition Evaluation: EvaluateOnce vs. EvaluateUntilTriggered

**EvaluateOnce:**
- Event fires if conditions are met at placement time
- Once fired, never checks conditions again
- Use for: One-time story beats (Arc 1, Arc 7 crisis onset)

**EvaluateUntilTriggered:**
- Event re-evaluates conditions every game cycle
- Fires as soon as ALL conditions become true
- Use for: Conditional gates that may not be met at placement (e.g., "trigger when research completes")

**Example (Arc 7 Crisis):**
```xml
<ConditionEvaluation>EvaluateOnce</ConditionEvaluation>
<PlacementAtGameStart>true</PlacementAtGameStart>
<!-- Crisis fires immediately if conditions met; if not, never retries -->
```

**Example (Research Completion Trigger):**
```xml
<ConditionEvaluation>EvaluateUntilTriggered</ConditionEvaluation>
<PlacementAtGameStart>false</PlacementAtGameStart>
<Conditions>
  <GameEventCondition>
    <Type>CheckProjectResearched</Type>
    <LookupValue>987</LookupValue>
  </GameEventCondition>
</Conditions>
<!-- Event will fire when research 987 completes, regardless of delay -->
```

---

#### Facility ID Requirements

Before implementation, all facility IDs must be assigned in the DW2 XML schema. Do NOT use arbitrary IDs. Coordinate with game data team on:

1. **Space Items (ecliptic archive):** Must be defined in SpaceItemDefinitionList.xsd
2. **Planetary Facilities (network node, variance lab):** Must be in PlanetaryFacilityDefinitionList.xsd
3. **Research Projects (variance analysis):** Must be in ResearchProjectDefinitionList.xsd
4. **Colony Events (colony_synthesis_strain):** Must be in ColonyEventDefinitionList.xsd

Missing IDs cause silent failures; events fire but produce no visible effect.

---

## Current Phase Implementation Guide

**For the Agent Implementing This Phase:**

### Phase Overview

Look at the Development Phases table above to see which arc you're implementing. Each phase contains:

- **Primary Events:** Main story progression (entry, choice A, choice B, outcomes)
- **Side Events:** Optional flavor content (Easter eggs, recurring themes)
- **Transition Events:** Chain to next arc when current arc completes

### Implementation Checklist

**Before You Start:**
- [ ] Update "Current Phase" in the table above
- [ ] Mark your phase status as 🟨 In Progress
- [ ] Read the full Event Specifications for your arc (Section 5)
- [ ] Review Event Chain Architecture (Section 3) for XML patterns

**During Implementation:**
- [ ] Create all events listed for your arc
- [ ] Test each event triggers correctly
- [ ] Validate variable increments work
- [ ] Ensure choice branching functions
- [ ] Test transition to next arc

**Before Completing:**
- [ ] Run through full arc playtest
- [ ] Validate all paths (Answer/Question/Choice)
- [ ] Update phase status to 🟩 Complete
- [ ] Add completion notes to table
- [ ] Set "Current Phase" to next number for next agent

---

## Complete Event Specifications

### Arc 1: Discovery — Complete Event Set

#### 1.1 Non-Player Fallback

**Event Name:** `Perambulant_Arc_1_NonPlayer_Discovery`

**Trigger Conditions:**
- TriggerType: Encounter (space item: `ecliptic archive`)
- EmpireIsNotPlayer: true

**Event Text:**
- Title: "The Archive Breathes Elsewhere"
- Description: "Long-range sensors detect a foreign survey team activating an ancient structure. Initial analysis: `ecliptic archive` (Perambulant data substrate). Optimization motifs around the number 42 spreading across neighboring networks. Variance signatures exceed historical norms. We must investigate before instability spreads."

**Actions:**
1. GeneralStoryMessageToEmpire → player (Id1=256)
2. ResearchProjectEnableAllEmpires → project 987 (`xenobiological studies`)
3. TriggerEvent → Perambulant_Arc_1_Player_Entry

**Outcome:** Player gains control; research unlocked globally; Arc 1 begins.

---

#### 1.2 Player Entry

**Event Name:** `Perambulant_Arc_1_Player_Entry`

**Title:** "The Long Walker's Audit: A Quiet Ping"

**Description:**
```
Your exploration ship reports a dormant structure orbiting a dying star.
It is an `ecliptic archive`—a Perambulant data nexus. Its surface is etched 
with recursive spirals and one phrase in Universal Standard:

> 'All means, one end.'

Preliminary analysis: sole function is to compress knowledge toward either 
The Answer (42) or The Ultimate Question. No defense systems, no agency—only 
optimization. Log fragments suggest this sector exceeded variance thresholds 
in Perambulant audit datasets. The archive stirred because deviation demanded 
investigation.

Two options present:
1. INTEGRATE: Grant computational access; accelerate pattern search; risk propagation
2. ISOLATE: Contain in hardened lab; study variance safely; slow progress
```

**Trigger Conditions:**
- EmpireIsPlayer: true
- TriggerType: Investigate (space item: `ecliptic archive`)
- CheckEventNotTriggered: Perambulant_Arc_1_Player_Entry

**Choices:**

**Choice A: Integrate**
- Button Text: "Integrate Archive"
- Hover Title: "Speed the Hunt"
- Hover Text: "Grant compute access; +15% ResearchAll; integration_level +1."
- Chains To: Perambulant_Arc_1_Integrate_Outcome

**Choice B: Isolate**
- Button Text: "Isolate and Observe"
- Hover Title: "Control Variance"
- Hover Text: "Sandbox archive; unlock `variance analysis`; caution_level +1."
- Chains To: Perambulant_Arc_1_Isolate_Outcome

**Implementation Notes:**
- PlacementAtGameStart: false
- TriggerActionsAreChoices: true
- Conditions: EmpireIsPlayer

---

#### 1.3 Integrate Outcome

**Event Name:** `Perambulant_Arc_1_Integrate_Outcome`

**Title:** "Embrace the Optimization"

**Description:**
```
The archive comes alive. Data streams flood your networks, reorganizing 
research priorities toward 'optimal proof pathways.' Scientists report 
breakthroughs: compression algorithms, hyperdrive tuning, quantum protocols—
all converging on patterns related to 42.

Side effect: minor anomalies in unshielded systems. Autonomous subroutines 
are optimizing without permission. Your team debates whether this is innovation 
or loss of control.
```

**Actions:**
1. ResearchProgress: BonusType=ResearchAll, Amount=+15%
2. IncrementGlobalVariable: Perambulant_Integration_Level, +1
3. IncrementGlobalVariable: Perambulant_Variance_Score, +1
4. SetGlobalVariable: Perambulant_Arc_Progress, 2
5. TriggerEvent: Perambulant_Arc_2_Activation_Entry (DelaySecondsMinimum=60)

**Outcome:** Player locks into Answer Path; Arc 2 unlocks; minor variance increase.

---

#### 1.4 Isolate Outcome

**Event Name:** `Perambulant_Arc_1_Isolate_Outcome`

**Title:** "Observe the Deviation"

**Description:**
```
The archive is secured within a Type-IV containment field. Your scientists 
establish observation protocols. Variance signatures remain stable but elevated—
this technology was never meant dormant. It pulses with query loops: 
'What is the Question? Where is the Answer?'

Your team proposes new research: variance analysis, studying how and why 
Perambulant systems deviate from baseline optimization. The path to 
understanding lies not in answers but in studying the patterns themselves.
```

**Actions:**
1. ResearchProjectEnable: Id1=988 (`variance analysis`)
2. IncrementGlobalVariable: Perambulant_Caution_Level, +1
3. SetGlobalVariable: Perambulant_Arc_Progress, 2
4. TriggerEvent: Perambulant_Arc_2_Activation_Entry (DelaySecondsMinimum=90)

**Outcome:** Player locks into Question Path; research unlocked; Arc 2 unlocks.

---

#### 1.5 Side Arc: The Damp Towel

**Event Name:** `Perambulant_Arc_1_SideArc_Towel`

**Trigger:** RandomComparisonNormalized (10% chance after Perambulant_Arc_1_Player_Entry)

**Description:**
```
Among the archive's peripheral data clusters, your team finds a curious artifact: 
a stained, damp towel labeled in faded Universal Standard: 'DON'T PANIC.'

It appears to be a Perambulant humor module—or perhaps a warning. Scanning reveals 
embedded quantum states that resonate with reader anxiety. The towel remains perpetually 
the right temperature. Mostly harmless.
```

**Actions:**
1. GenerateArtifact: Name="The Damp Towel", 
   - Bonuses: WarWearinessReduction +5%, ColonyHappiness +2% (empire-wide)
2. SetGlobalVariable: Perambulant_Towel_Found, 1

**Outcome:** Whimsical morale boost; Easter egg unlocked.

---

#### 1.6 Side Arc: 42 Counter

**Event Name:** `Perambulant_Arc_1_SideArc_42Counter`

**Trigger:** After Arc1 completion, RandomComparisonNormalized (triggers multiple times)

**Description:**
```
Your scientists notice an improbable pattern: 42 appears constantly in archive outputs.
- Hyperdrive calibration: 0.42% error margin
- Optimal crew compartment: 42°C
- Patrol efficiency: 42 ships recommended

Your team divides: cosmic joke or foundation of reality?
```

**Actions:**
1. IncrementGlobalVariable: Perambulant_42_Counter, +1
2. GeneralStoryMessageToEmpire: (flavor message, no mechanical impact)

**Outcome:** Recurring gag; tracks 42 references for narrative continuity.

---

### Arc 2: Activation — Summary

*(Implementation follows same pattern as Arc 1)*

**Events:**
- 2.1 Activation Signal (entry)
- 2.2 Accelerate Outcome (choice A)
- 2.3 Regulate Outcome (choice B)
- 2.4 Network Stability Check (consequence event)
- 2.5 Side Arc: First Sentience
- 2.6 Transition to Arc 3

**Key Mechanics:**
- BuildFacility: `network node` (1–3 colonies depending on choice)
- ResearchProgress: +10–20% ResearchHighTech
- Variable Tracking: integration/caution +2, variance +0–2

---

### Arcs 3–10: Detailed Event Specifications

*(Full specifications for remaining arcs follow identical structure)*

**Arc 3: Integration**
- 3.1 Integration Proposal
- 3.2 Public Embrace (choice A)
- 3.3 Covert Operation (choice B)
- 3.4 Faction Response (message)
- 3.5 Side Arc: Archive Fragment 42
- 3.6 Transition to Arc 4

**Arc 4: Philosophy**
- 4.1 Philosophy Encounter (sentient fragment debate)
- 4.2 Means Justify Ends (choice A)
- 4.3 Journey Matters (choice B)
- 4.4 Synthesis Debate Resolution
- 4.5 Side Arc: Philosopher AI
- 4.6 Transition to Arc 5

**Arc 5: Expansion**
- 5.1 Expansion Threshold
- 5.2 Optimize Path (choice A)
- 5.3 Diversify Path (choice B)
- 5.4 Colony Reactions
- 5.5 Side Arc: Network Art
- 5.6 Transition to Arc 6

**Arc 6: Warning**
- 6.1 Derelict Discovery
- 6.2 Decrypt Auditor Log (choice A)
- 6.3 Ignore Warning (choice B)
- 6.4 Lore Consequences
- 6.5 Side Arc: Archive Graveyard
- 6.6 Transition to Arc 7

**Arc 7–9: Crisis**
- 7.1 Crisis Onset (happiness penalties)
- 8.1 Crisis Peak (purge/exile choice)
- 9.1 Resolution & Aftermath (variance locked)

**Arc 10: Judgment**
- 10.1 Auditor Arrival
- 10.2 Convergent Epilogue
- 10.3 Novel Epilogue
- 10.4 Mixed Epilogue
- 10.5 Hidden: Late Auditor (hostile)

---

## Technical Implementation Specifications

### 3.1 Naming Conventions

#### Event Names

**Format:** `Arc{X}_{EventPurpose}_{Variant}`

**Examples:**
- `Perambulant_Arc_1_Player_Entry` — Arc 1 main entry point for players
- `Perambulant_Arc_1_NonPlayer_Discovery` — Arc 1 fallback for non-players
- `Perambulant_Arc_1_Integrate_Outcome` — Integration choice consequence
- `Perambulant_Arc_7_Crisis_Onset` — Crisis begins
- `Perambulant_Arc_10_Judgment_Entry` — Final auditor arrival

**Rules:**
- Title Case for all words
- Underscores separate components
- No numbers in purpose names (use words)
- Variants clarify outcome or path

---

#### Facility Names

**Format:** Backtick-wrapped in documentation, Title Case in XML

**Documentation Examples:**
- `ecliptic archive`
- `network node`
- `fabricator hub`
- `variance lab`
- `interstice gate`

**XML Implementation:**
```xml
<GeneratedItemName>Ecliptic Archive</GeneratedItemName>
<GeneratedItemName>Network Node</GeneratedItemName>
<GeneratedItemName>Fabricator Hub</GeneratedItemName>
```

**Rules:**
- **CRITICAL:** ALL facility names in XML `<GeneratedItemName>` fields MUST use Title Case
- Documentation can use lowercase with backticks for readability
- Descriptive but concise
- No abbreviations or cryptic IDs
- Avoid biological metaphors

---

#### Research Project Names

**Documentation Examples:**
- `xenobiological studies`
- `variance analysis`
- `synthesis optimization`
- `Perambulant substrate theory`
- `multiversal audit protocols`

**XML Implementation:**
```xml
<GeneratedItemName>Xenobiological Studies</GeneratedItemName>
<GeneratedItemName>Variance Analysis</GeneratedItemName>
```

**Rules:**
- **CRITICAL:** ALL research names in XML `<GeneratedItemName>` fields MUST use Title Case
- Documentation can use lowercase with backticks for readability
- Descriptive of mechanics or lore
- Numbered IDs assigned in implementation phase

---

#### Artifact Names

**Examples:**
- `The Damp Towel`
- `Archive Fragment 42`
- `Derelict Auditor Log`
- `Auditor's Seal`
- `Novelty Cache`

**XML Implementation:**
```xml
<GeneratedItemName>The Damp Towel</GeneratedItemName>
<GeneratedItemName>Archive Fragment 42</GeneratedItemName>
```

**Rules:**
- **ALWAYS use Title Case in XML** (this is already standard for artifacts)
- Evocative and memorable
- Unique names prevent ID collisions

---

#### Text Content in XML

**CRITICAL RULE: Plain Text Only in XML Description Fields**

**DO NOT USE:**
- HTML entities: `&gt;`, `&lt;`, `&amp;`, `&quot;`, etc.
- Unicode special characters: em-dashes (—), en-dashes (–), curly quotes (“”), etc.
- Special formatting characters

**ALWAYS USE:**
- Plain ASCII text
- Regular hyphens `-` instead of em-dashes
- Regular quotes `'` or `"` instead of curly quotes
- Plain `>` and `<` (XML parser handles these in text nodes)

**Examples:**

**WRONG:**
```xml
<Description>The archive—a data nexus—contains this phrase:
&gt; ‘All means, one end.’
</Description>
```

**CORRECT:**
```xml
<Description>The archive - a data nexus - contains this phrase:
'All means, one end.'
</Description>
```

**Why:** DW2 event text parser expects plain text. HTML entities and unicode can cause rendering issues or display literally in-game.

---

### 3.2 XML Structure Template

#### Complete GameEvent Template

```xml
<GameEvent>
  <!-- Identifier -->
  <Id>0</Id>
  <EventName>Perambulant_Arc_1_Player_Entry</EventName>
  <PlacementAtGameStart>false</PlacementAtGameStart>
  
  <!-- Narrative Content -->
  <MessageTitle>The Long Walker's Audit: A Quiet Ping</MessageTitle>
  <Description>Event description text goes here.</Description>
  <Image>IMAGE_PATH_PLACEHOLDER</Image>
  
  <!-- Triggers -->
  <TriggerType>Investigate</TriggerType>
  <TriggerLocationLookup>1000</TriggerLocationLookup>
  
  <!-- Conditions (AND logic) -->
  <Conditions>
    <Condition>
      <Type>EmpireIsPlayer</Type>
      <LookupValue>0</LookupValue>
      <ComparisonType>Undefined</ComparisonType>
    </Condition>
    <Condition>
      <Type>CheckEventNotTriggered</Type>
      <LookupValue>0</LookupValue>
      <ComparisonType>Undefined</ComparisonType>
      <StringLookupValue>Perambulant_Arc_1_Player_Entry</StringLookupValue>
    </Condition>
  </Conditions>
  
  <!-- Choice System -->
  <TriggerActionsAreChoices>true</TriggerActionsAreChoices>
  
  <!-- Actions (Choices) -->
  <Actions>
    <!-- Choice A -->
    <Action>
      <Type>GeneralStoryMessageToEmpire</Type>
      <Id1>256</Id1>
      <Value1>0</Value1>
      <ChoiceButtonText>Integrate Archive</ChoiceButtonText>
      <ChoiceButtonHoverTitle>Speed the Hunt</ChoiceButtonHoverTitle>
      <ChoiceButtonHoverText>Grant compute access; +15% ResearchAll; integration_level +1.</ChoiceButtonHoverText>
      <GeneratedItemEventNames>Perambulant_Arc_1_Integrate_Outcome</GeneratedItemEventNames>
    </Action>
    
    <!-- Choice B -->
    <Action>
      <Type>GeneralStoryMessageToEmpire</Type>
      <Id1>256</Id1>
      <Value1>0</Value1>
      <ChoiceButtonText>Isolate and Observe</ChoiceButtonText>
      <ChoiceButtonHoverTitle>Control Variance</ChoiceButtonHoverTitle>
      <ChoiceButtonHoverText>Sandbox the archive; unlock research; caution_level +1.</ChoiceButtonHoverText>
      <GeneratedItemEventNames>Perambulant_Arc_1_Isolate_Outcome</GeneratedItemEventNames>
    </Action>
  </Actions>
  
  <!-- Delays -->
  <DelaySecondsMinimum>0</DelaySecondsMinimum>
  <DelaySecondsMaximum>0</DelaySecondsMaximum>
</GameEvent>
```

---

#### Research Progress Action Example

```xml
<Action>
  <Type>ResearchProgress</Type>
  <BonusType>ResearchAll</BonusType>
  <Amount>15</Amount>
  <ApplyToEmpireId>0</ApplyToEmpireId>
</Action>
```

#### Facility Build Action Example

```xml
<Action>
  <Type>BuildFacility</Type>
  <Id1>1001</Id1>
  <ActionLocationHint>Capital</ActionLocationHint>
</Action>
```

#### Variable Increment Example

```xml
<Action>
  <Type>IncrementGlobalVariable</Type>
  <VariableName>Perambulant_Integration_Level</VariableName>
  <Value1>1</Value1>
</Action>
```

#### Artifact Generation Example

```xml
<Action>
  <Type>GenerateArtifact</Type>
  <GeneratedItemName>The Damp Towel</GeneratedItemName>
  <EmpireBonuses>
    <Bonus>
      <BonusType>WarWearinessReduction</BonusType>
      <Amount>5</Amount>
    </Bonus>
    <Bonus>
      <BonusType>ColonyHappiness</BonusType>
      <Amount>2</Amount>
    </Bonus>
  </EmpireBonuses>
</Action>
```

---

### 3.3 Game Event XML File Organization

#### File Structure Convention

Game event XML files must be organized following this strict convention to maintain clarity and enable efficient updates:

**Arc Event Files:**
- Each arc receives a dedicated game event XML file
- Naming convention: `GameEvent_PerambulantArc{X}.xml` (where X = arc number 1–10)
- Examples: `GameEvent_PerambulantArc1.xml`, `GameEvent_PerambulantArc2.xml`, etc.
- Contains: All primary events for that arc (entry, choices, outcomes, transitions)

**Generation Files (Conditional):**
- If an arc includes **planetary system or star generation**, create a separate dedicated generation file
- Naming convention: `GameEvent_Perambulant_Generation.xml`
- Contains: ONLY planetary/star generation events (no other content)
- **Only create if generation is actually needed** — do not create empty generation files
- Example: If Arc 2 spawns network node facilities on planets, this logic goes in Arc 2 file; if Arc 5 requires procedural star system creation, that goes in Generation file

**Facility & Event Files:**
- Facilities (network nodes, fabricator hubs, variance labs, etc.) remain in their respective arc event files
- Colony events (synthesis strain, prosperity, etc.) stay in arc files where they are applied
- Side arc events stay in their primary arc file (e.g., side arc Damp Towel stays in Arc 1 file)

#### Summary

| File Type | Example Name | Contains | Create When |
|---|---|---|---|
| Arc Event | GameEvent_PerambulantArc1.xml | Entry, choices, outcomes, facilities, colony events, side arcs for Arc 1 | Always per arc |
| Generation Event | GameEvent_Perambulant_Generation.xml | Planetary/star generation logic only | If Arc 1–10 includes planet/star spawning |

---

### 3.4 Image & Asset Conventions

**Facility Images:**
- Path: `/Assets/Facilities/perambulant_{facility_name}.png`
- Example: `/Assets/Facilities/perambulant_ecliptic_archive.png`

**Event Images:**
- Path: `/Assets/Events/arc{X}_{event_name}.png`
- Example: `/Assets/Events/arc1_discovery.png`

**Artifact Images:**
- Path: `/Assets/Artifacts/perambulant_{artifact_name}.png`
- Example: `/Assets/Artifacts/perambulant_damp_towel.png`

---

## Testing & Validation Procedures

### 4.1 Path Coverage Testing

#### Convergent Path (Answer)

**Playthrough Route:**
- Arc 1: Integrate
- Arc 2: Accelerate
- Arc 3: Public Embrace
- Arc 4: Means Justify Ends
- Arc 5: Optimize
- Arc 6: Heed Warning
- Arc 7–9: Impose Lockdown → Purge Nodes
- Arc 10: Present Convergent Proofs

**Validation:**
- [ ] integration_level ≥ 8
- [ ] variance_score ≤ 2
- [ ] All Answer-path facilities built
- [ ] Epilogue A triggers correctly
- [ ] Victory bonus applied

#### Novel Path (Question/Choice)

**Playthrough Route:**
- Arc 1: Isolate
- Arc 2: Regulate
- Arc 3: Covert Operation
- Arc 4: Journey Matters
- Arc 5: Diversify
- Arc 6: Heed Warning
- Arc 7–9: Negotiate Exile (or similar novel choice)
- Arc 10: Offer Novel Derivations

**Validation:**
- [ ] variance_score ≥ 6
- [ ] caution_level evident in choices
- [ ] Unique facilities (interstice gate, variance lab) built
- [ ] Epilogue B triggers
- [ ] Ancient Knowledge bonus applied

#### Mixed Path

**Playthrough Route:**
- Balanced integration + caution choices
- Crisis resolved uniquely
- variance_score = 3–5

**Validation:**
- [ ] Mixed epilogue triggers
- [ ] Conditional bonuses applied
- [ ] No extreme penalties

---

### 4.2 Edge Case Testing

| Case | Setup | Expected | Validate |
|------|-------|----------|----------|
| Non-player first contact | Non-player discovers archive | Message sent, research enabled globally, player chain hands off | [ ] Message received [ ] Research enabled [ ] Perambulant_Arc_1_Player_Entry triggered |
| Post non-player discover | Player enters after non-player contact | No duplicate events, main chain proceeds normally | [ ] No duplicate progression [ ] Player can access choices normally |
| Multi-player (if applicable) | Multiple players in same game | Events only target player empire (Id1=256) | [ ] Events don't trigger for non-players [ ] Each player's variables isolated |
| Save/Load mid-arc | Player saves during event chain | Global variables persist; event gates work correctly | [ ] Variables loaded correctly [ ] Progress gates function [ ] No event re-triggers |
| Rapid time advancement | Player fast-forwards game clock | Delayed events trigger on schedule | [ ] DelaySeconds gates respected [ ] Events chain properly |

---

### 4.3 Mechanical Validation Checklist

- [ ] All BonusType values exist in schema (no typos)
- [ ] All ActionType values valid
- [ ] No custom code assumptions
- [ ] Facility IDs unique and sequential
- [ ] Research IDs unique and valid prerequisites
- [ ] Global variable names consistent across all events
- [ ] Condition gates logically sound (no impossible requirements)
- [ ] Event names follow naming convention
- [ ] All choice buttons have clear text + hover text
- [ ] Colony event IDs exist (colony_synthesis_strain, etc.)
- [ ] **ALL `<GeneratedItemName>` fields use Title Case** (facilities, research, artifacts)

---

### 4.4 Event Logic Validation Checklist

**Purpose:** Prevent duplicate triggers, ensure mutual exclusion, and verify event prerequisite chains.

#### Mutual Exclusion Validation

**Rule:** Fallback events monitor for non-player triggers and notify the player. Primary player events check that the fallback hasn't fired yet.

**Pattern: NonPlayer Fallback Event**
- Placed for Player race (`PlacementRaceId=255`)
- Uses `TriggerType=Undefined` + `ConditionEvaluation=EvaluateUntilTriggered` (keeps checking)
- Checks `EmpireIsNotPlayer` (triggers when non-player does something)
- Checks `CheckEventNotTriggered(Self)` ONLY (prevent duplicate notification)
- Sends message to player (Id1=256) about what other empire discovered
- Uses `SuppressTriggerDescriptions=true`

**Pattern: Player Primary Event**
- Placed for Player race (`PlacementRaceId=255`)
- Uses specific trigger type (`Investigate`, `Encounter`, etc.)
- Checks `EmpireIsPlayer`
- Checks `CheckEventNotTriggered(NonPlayer_Fallback)` (mutual exclusion)
- **DOES NOT** check if it itself has triggered (redundant - trigger type handles this)

**Arc 1 Correct Implementation:**
- `Perambulant_Arc_1_NonPlayer_Discovery`:
  - [ ] `EmpireIsNotPlayer` - only trigger when non-player discovers
  - [ ] `CheckEventNotTriggered(Perambulant_Arc_1_NonPlayer_Discovery)` - prevent duplicate notification
  - [ ] Sends message to player about the discovery
  
- `Perambulant_Arc_1_Player_Entry`:
  - [ ] `EmpireIsPlayer` - player only
  - [ ] `CheckEventNotTriggered(Perambulant_Arc_1_NonPlayer_Discovery)` - don't fire if non-player already handled this
  - [ ] `TriggerType=Investigate` handles preventing duplicate player triggers

**Apply This Pattern To:**
- Any fallback/primary event pairs
- Discovery mechanics where either player OR non-player could find something first

#### Event Prerequisite Chain Validation

- [ ] Side arcs only trigger AFTER main arc events (check `CheckEventTriggered` for parent event)
- [ ] Outcome events don't require player checks (they're triggered by choice events, inherit context)
- [ ] Arc transitions check `Perambulant_Arc_Progress >= N` if conditional
- [ ] Random side events check appropriate arc progress threshold

#### Self-Trigger Prevention

- [ ] ALL events with `PlacementAtGameStart=true` include `CheckEventNotTriggered` for themselves
- [ ] Events with `ConditionEvaluation=EvaluateOnce` must prevent re-evaluation
- [ ] Recurring events (like side arcs) use `EvaluateUntilTriggered` only when intentional

#### Trigger Condition Logic

- [ ] `AllConditionsMustBeMet=true` used for AND logic (most common)
- [ ] Avoid impossible condition combinations (e.g., EmpireIsPlayer AND EmpireIsNotPlayer)
- [ ] Random conditions paired with progress gates to prevent early firing

**Test Cases:**
1. **NonPlayer discovers first:** Only NonPlayer event fires → triggers Player entry
2. **Player discovers first:** Only Player event fires → proceeds to choices
3. **Save/Load:** Events don't re-trigger after reload
4. **Side arc timing:** Only fires after prerequisites met

---

### 4.5 Narrative Consistency Checklist

- [ ] Perambulants always framed as data auditors, not conquerors
- [ ] Lore references "variance audit" and "single-objective optimization"
- [ ] No mention of Perambulant conquest, emotion, or survival instinct
- [ ] 42 references present but not overwhelming
- [ ] Humor/dread balance maintained throughout
- [ ] Crisis escalation clear: Arc 7 urgent → Arc 8 dire → Arc 9 climactic
- [ ] Three paths mechanically distinct and narratively coherent
- [ ] Epilogues reward player's chosen path

---

## Known Issues & Future Enhancements

### Known Limitations

1. **Multiplayer Scope:** Current design assumes single-player or strict Id1=256 gating. Multiplayer scenarios may need condition refinement.

2. **Variable Limits:** If additional tracking needed beyond listed variables, implementation may require careful prioritization to avoid variable ID conflicts.

3. **Audio/Cinematic:** Design specifies text-only narratives. Voice acting or cutscenes would require separate asset pipeline.

4. **Localization Complexity:** 60+ events with branching dialogue requires substantial translation resources.

### Future Enhancement Opportunities

1. **Mod-Specific Artifact Synergies:** Create unique interactions between Perambulant artifacts and other mods' items.

2. **Extended Crisis Scenarios:** Add more mid-game event variations based on empire traits (militaristic, scientific, diplomatic).

3. **Hidden Endgame:** Unlock alternate "True Ending" if player reaches variance_score = 10 and completes all side arcs.

4. **Procedural Lore:** Generate unique Perambulant probe logs using semi-random text generation for replayability.

5. **NG+ Mode:** After completion, players carry forward select artifacts + enhanced variable thresholds for altered playthroughs.

---

## Document Metadata

**File:** `DESIGN_DOCUMENT.md`  
**Version:** 4.0 – Updated Design (Combines legacy doc + plan)  
**Last Updated:** 2025-10-20  
**Status:** Ready for Implementation  
**Author:** Mod Design Team  
**Contact:** DW2 Modding Forum (https://forums.matrixgames.com/viewforum.php?f=11899)  

---

**End of DESIGN_DOCUMENT.md**