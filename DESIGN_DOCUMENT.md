# The Long Walker's Audit
## A Distant Worlds 2 Story Campaign Design Document

**Version:** 4.0 – Updated Design  
**Date:** 2025-10-20  
**Status:** Implementation-Ready  

---

## Table of Contents

1. [Mod Vision & Philosophy](#mod-vision--philosophy)
2. [Core Conceptual Framework](#core-conceptual-framework)
3. [Event Chain Architecture](#event-chain-architecture)
4. [Variable System Reference](#variable-system-reference)
5. [Complete Event Specifications](#complete-event-specifications)
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

**Trigger:** DateReached + perambulant_arc_progress ≥ 9

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

### 2.1 Placement & Trigger Patterns

#### Placement Strategies

**Arc 1 Entry:**
- PlacementAtGameStart: false (auto-triggered by exploration)
- TriggerType: Encounter (space item: `ecliptic archive`)
- Location: Generated at game start in random system

**Arc 1 Non-Player Fallback:**
- PlacementAtGameStart: true
- Conditions: EmpireIsNotPlayer
- Outcome: Message to player; enables research globally; hands control to Arc 1_Player_Entry

**Subsequent Arcs (2–10):**
- PlacementAtGameStart: false
- Trigger Method: TriggerEvent from prior arc
- DelaySeconds: 60–120 (game time between events)
- Gated by: Global variables (perambulant_arc_progress, integration_level, etc.)

**Crisis Arc (7–9):**
- Hard date gate: ~mid-game (~year 100–150)
- Prerequisite: integration_level ≥ 6
- Trigger: StartColonyEvent (colony_synthesis_strain) before crisis onset

**Final Judgment (Arc 10):**
- Hard date gate: ~late-game (~year 300+)
- Prerequisite: perambulant_arc_progress ≥ 9 AND variance_score locked

---

#### Event Sequencing via TriggerEvent Actions

Each event chains to the next via TriggerEvent actions:

```xml
<Action>
  <Type>TriggerEvent</Type>
  <GeneratedItemEventNames>Arc2_Activation_Entry</GeneratedItemEventNames>
  <ConditionSet>
    <Condition>
      <Type>VariableComparison</Type>
      <VariableName>perambulant_arc_progress</VariableName>
      <ComparisonType>GreaterThanOrEqual</ComparisonType>
      <ComparisonValue>2</ComparisonValue>
    </Condition>
  </ConditionSet>
  <DelaySecondsMinimum>60</DelaySecondsMinimum>
</Action>
```

---

#### Choice Implementation Pattern

All events use TriggerActionsAreChoices=true with exactly 2 actions:

```xml
<GameEvent>
  <TriggerActionsAreChoices>true</TriggerActionsAreChoices>
  <!-- Action 1: Choice A -->
  <Actions>
    <Action>
      <Type>GeneralStoryMessageToEmpire</Type>
      <ChoiceButtonText>Integrate Archive</ChoiceButtonText>
      <ChoiceButtonHoverTitle>Speed the Hunt</ChoiceButtonHoverTitle>
      <ChoiceButtonHoverText>Grant compute access; +15% ResearchAll; raise integration_level.</ChoiceButtonHoverText>
      <GeneratedItemEventNames>Arc1_Integrate_Outcome</GeneratedItemEventNames>
    </Action>
    <!-- Action 2: Choice B -->
    <Action>
      <Type>GeneralStoryMessageToEmpire</Type>
      <ChoiceButtonText>Isolate and Observe</ChoiceButtonText>
      <ChoiceButtonHoverTitle>Control Variance</ChoiceButtonHoverTitle>
      <ChoiceButtonHoverText>Sandbox the archive; unlock `variance analysis` research; raise caution_level.</ChoiceButtonHoverText>
      <GeneratedItemEventNames>Arc1_Isolate_Outcome</GeneratedItemEventNames>
    </Action>
  </Actions>
</GameEvent>
```

---

### 2.2 Variable System Documentation

#### Global Variables (Persistent Across Playthrough)

| Variable Name | Type | Initial | Purpose | Affected By |
|---------------|------|---------|---------|-------------|
| `perambulant_arc_progress` | int | 0 | Tracks current arc (1–10) | Arc completion events |
| `perambulant_integration_level` | int | 0 | Cumulative "pro-synthesis" choices (0–10+) | Integration-path events |
| `perambulant_caution_level` | int | 0 | Cumulative "anti-synthesis" choices (0–10+) | Question-path events |
| `perambulant_variance_score` | int | 0 | Tracks deviation from canonical patterns (determines judgment) | Crisis resolution, novel choices |
| `perambulant_crisis_triggered` | bool | 0 | True if crisis (Arc 7–9) initiated | Arc 7 onset |
| `perambulant_towel_found` | bool | 0 | Easter egg state | Side arc trigger |
| `perambulant_42_counter` | int | 0 | Easter egg: "42" references encountered | Recurring 42 side event |
| `perambulant_crisis_resolution` | int | 0 | Stores crisis choice (0=none, 1=purge, 2=exile) | Arc 8 choice |
| `perambulant_judgment_type` | int | 0 | Final path (1=convergent, 2=novel, 3=mixed) | Arc 10 choice |

#### Variable Increment Patterns

**Integration Path (Answer):**
- Arc 1 Integrate: +1 to integration_level
- Arc 2 Accelerate: +2 to integration_level, +2 to variance_score
- Arc 3 Public Embrace: +2 to integration_level, +1 to variance_score
- Arc 5 Optimize: +3 to integration_level

**Question Path (Caution):**
- Arc 1 Isolate: +1 to caution_level
- Arc 2 Regulate: +2 to caution_level
- Arc 3 Covert Operation: +1 to caution_level
- Arc 5 Diversify: +2 to caution_level
- Arc 6 Heed Warning: +1 to caution_level, +1 to variance_score

**Choice Path (Novel):**
- Arc 8 Negotiate Exile: +5 to variance_score
- Arc 9 Preserve Nodes: +3 to variance_score

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
  <VariableName>perambulant_arc_progress</VariableName>
  <ComparisonType>GreaterThanOrEqual</ComparisonType>
  <ComparisonValue>3</ComparisonValue>
</Condition>
```

**Integration Level Gate (High Path):**
```xml
<Condition>
  <Type>VariableComparison</Type>
  <VariableName>perambulant_integration_level</VariableName>
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
  <VariableName>perambulant_crisis_triggered</VariableName>
  <ComparisonType>Equals</ComparisonType>
  <ComparisonValue>1</ComparisonValue>
</Condition>
```

---

### 2.3 Action Types Catalog

#### Story Delivery

**GeneralStoryMessageToEmpire**
- *Purpose:* Display narrative text to player
- *Key Fields:* MessageTitle, Description, Id1 (256 = player)
- *Example:* Arc 1 entry event
- *Notes:* Most event text uses this action

#### Research & Knowledge

**ResearchProjectEnable**
- *Purpose:* Unlock research for player empire only
- *Key Fields:* Id1 (project ID)
- *Example:* Unlock "Variance Analysis" on Arc 1 Isolate path

**ResearchProjectEnableAllEmpires**
- *Purpose:* Unlock research for all empires
- *Key Fields:* Id1 (project ID)
- *Example:* Arc 1 Non-Player Fallback event
- *Notes:* Only use for global accessibility (fallback events)

**ResearchProgress**
- *Purpose:* Grant research points directly
- *Key Fields:* BonusType, Amount, ApplyTo (player empire)
- *Example:* +15% ResearchAll on Arc 1 Integrate choice
- *Notes:* Use conservative percentages; scales with arc progression

#### Facility & Infrastructure

**BuildFacility**
- *Purpose:* Construct facility at colonies
- *Key Fields:* Id1 (facility ID), ActionLocationHint (capital/random)
- *Example:* Build `network node` on Arc 2 choices
- *Notes:* ActionLocationHint controls placement

**RemoveFacility**
- *Purpose:* Destroy facility
- *Key Fields:* Id1 (facility ID), ActionLocationHint (all/specific)
- *Example:* Remove all `fabricator hub` on Arc 8 Purge
- *Notes:* Use to enforce consequence of crisis path

#### Colony Events & Happiness

**StartColonyEvent**
- *Purpose:* Apply empire-wide colony effect
- *Key Fields:* Id1 (colony event ID)
- *Example:* StartColonyEvent (colony_synthesis_strain) on Arc 7 Crisis
- *Notes:* Applies penalties to all colonies; stacks if multiple triggered

**EndColonyEvent**
- *Purpose:* Remove colony event
- *Key Fields:* Id1 (colony event ID)
- *Example:* EndColonyEvent (colony_synthesis_strain) after Arc 8 resolution
- *Notes:* Reverses penalties applied by StartColonyEvent

#### Rewards & Items

**GenerateArtifact**
- *Purpose:* Create artifact with bonuses
- *Key Fields:* GeneratedItemName, EmpireBonuses, ItemBonuses
- *Example:* Generate `The Damp Towel` on Arc 1 side arc
- *Notes:* Use descriptive names; artifact persists across saves

**VictoryConditionBonus**
- *Purpose:* Grant victory points
- *Key Fields:* Value1 (points)
- *Example:* +50 points on Convergent Epilogue
- *Notes:* Use for endgame reward

#### Variable Management

**SetGlobalVariable**
- *Purpose:* Set variable to specific value
- *Key Fields:* VariableName, Value1
- *Example:* SetGlobalVariable (perambulant_arc_progress = 7)
- *Notes:* Use for arc progression gates

**IncrementGlobalVariable**
- *Purpose:* Add value to existing variable
- *Key Fields:* VariableName, Value1
- *Example:* IncrementGlobalVariable (integration_level, +1)
- *Notes:* Use for tracking choice alignment

---

## Complete Event Specifications

### Arc 1: Discovery — Complete Event Set

#### 1.1 Non-Player Fallback

**Event Name:** `Arc1_NonPlayer_Discovery`

**Trigger Conditions:**
- TriggerType: Encounter (space item: `ecliptic archive`)
- EmpireIsNotPlayer: true

**Event Text:**
- Title: "The Archive Breathes Elsewhere"
- Description: "Long-range sensors detect a foreign survey team activating an ancient structure. Initial analysis: `ecliptic archive` (Perambulant data substrate). Optimization motifs around the number 42 spreading across neighboring networks. Variance signatures exceed historical norms. We must investigate before instability spreads."

**Actions:**
1. GeneralStoryMessageToEmpire → player (Id1=256)
2. ResearchProjectEnableAllEmpires → project 987 (`xenobiological studies`)
3. TriggerEvent → Arc1_Player_Entry

**Outcome:** Player gains control; research unlocked globally; Arc 1 begins.

---

#### 1.2 Player Entry

**Event Name:** `Arc1_Player_Entry`

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
- CheckEventNotTriggered: Arc1_Player_Entry

**Choices:**

**Choice A: Integrate**
- Button Text: "Integrate Archive"
- Hover Title: "Speed the Hunt"
- Hover Text: "Grant compute access; +15% ResearchAll; integration_level +1."
- Chains To: Arc1_Integrate_Outcome

**Choice B: Isolate**
- Button Text: "Isolate and Observe"
- Hover Title: "Control Variance"
- Hover Text: "Sandbox archive; unlock `variance analysis`; caution_level +1."
- Chains To: Arc1_Isolate_Outcome

**Implementation Notes:**
- PlacementAtGameStart: false
- TriggerActionsAreChoices: true
- Conditions: EmpireIsPlayer

---

#### 1.3 Integrate Outcome

**Event Name:** `Arc1_Integrate_Outcome`

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
2. IncrementGlobalVariable: perambulant_integration_level, +1
3. IncrementGlobalVariable: perambulant_variance_score, +1
4. SetGlobalVariable: perambulant_arc_progress, 2
5. TriggerEvent: Arc2_Activation_Entry (DelaySecondsMinimum=60)

**Outcome:** Player locks into Answer Path; Arc 2 unlocks; minor variance increase.

---

#### 1.4 Isolate Outcome

**Event Name:** `Arc1_Isolate_Outcome`

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
2. IncrementGlobalVariable: perambulant_caution_level, +1
3. SetGlobalVariable: perambulant_arc_progress, 2
4. TriggerEvent: Arc2_Activation_Entry (DelaySecondsMinimum=90)

**Outcome:** Player locks into Question Path; research unlocked; Arc 2 unlocks.

---

#### 1.5 Side Arc: The Damp Towel

**Event Name:** `Arc1_SideArc_Towel`

**Trigger:** RandomComparisonNormalized (10% chance after Arc1_Player_Entry)

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
2. SetGlobalVariable: perambulant_towel_found, 1

**Outcome:** Whimsical morale boost; Easter egg unlocked.

---

#### 1.6 Side Arc: 42 Counter

**Event Name:** `Arc1_SideArc_42Counter`

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
1. IncrementGlobalVariable: perambulant_42_counter, +1
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
- `Arc1_Player_Entry` — Arc 1 main entry point for players
- `Arc1_NonPlayer_Discovery` — Arc 1 fallback for non-players
- `Arc1_Integrate_Outcome` — Integration choice consequence
- `Arc7_Crisis_Onset` — Crisis begins
- `Arc10_Judgment_Entry` — Final auditor arrival

**Rules:**
- Title Case for all words
- Underscores separate components
- No numbers in purpose names (use words)
- Variants clarify outcome or path

---

#### Facility Names

**Format:** Backtick-wrapped plain English

**Examples:**
- `ecliptic archive`
- `network node`
- `fabricator hub`
- `variance lab`
- `interstice gate`

**Rules:**
- Lowercase with spaces
- Descriptive but concise
- No abbreviations or cryptic IDs
- Avoid biological metaphors

---

#### Research Project Names

**Examples:**
- `xenobiological studies`
- `variance analysis`
- `synthesis optimization`
- `Perambulant substrate theory`
- `multiversal audit protocols`

**Rules:**
- Descriptive of mechanics or lore
- Lowercase with spaces
- Numbered IDs assigned in implementation phase

---

#### Artifact Names

**Examples:**
- `The Damp Towel`
- `Archive Fragment 42`
- `Derelict Auditor Log`
- `Auditor's Seal`
- `Novelty Cache`

**Rules:**
- Title Case for proper nouns/artifacts
- Evocative and memorable
- Unique names prevent ID collisions

---

### 3.2 XML Structure Template

#### Complete GameEvent Template

```xml
<GameEvent>
  <!-- Identifier -->
  <Id>0</Id>
  <EventName>Arc1_Player_Entry</EventName>
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
      <StringLookupValue>Arc1_Player_Entry</StringLookupValue>
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
      <GeneratedItemEventNames>Arc1_Integrate_Outcome</GeneratedItemEventNames>
    </Action>
    
    <!-- Choice B -->
    <Action>
      <Type>GeneralStoryMessageToEmpire</Type>
      <Id1>256</Id1>
      <Value1>0</Value1>
      <ChoiceButtonText>Isolate and Observe</ChoiceButtonText>
      <ChoiceButtonHoverTitle>Control Variance</ChoiceButtonHoverTitle>
      <ChoiceButtonHoverText>Sandbox the archive; unlock research; caution_level +1.</ChoiceButtonHoverText>
      <GeneratedItemEventNames>Arc1_Isolate_Outcome</GeneratedItemEventNames>
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
  <VariableName>perambulant_integration_level</VariableName>
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

### 3.3 Image & Asset Conventions

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
| Non-player first contact | Non-player discovers archive | Message sent, research enabled globally, player chain hands off | [ ] Message received [ ] Research enabled [ ] Arc1_Player_Entry triggered |
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

---

### 4.4 Narrative Consistency Checklist

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