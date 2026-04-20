# Procedural Generation Notes

Notes on feeding Nexus data into procedural generation systems — Unity, Unreal, custom scripts, or other tools.

---

## General Approach

Nexus produces structured descriptions. Procedural tools need structured data. The bridge is JSON export.

The workflow is:
1. Complete Nexus loop → produces world description
2. Export relevant sections to JSON (see format below)
3. Feed JSON into procedural system as seed data
4. Generate content constrained by the seed

Nexus doesn't generate content directly — it constrains the space of valid generated content so that everything produced is consistent with the world.

---

## JSON Export Format

A basic Nexus world export follows this structure. The Rust Belt example in `examples/rust_belt.md` shows this in practice.

```json
{
  "world_id": "your_world_id",
  "genre": ["genre1", "genre2"],
  "tech_level": "tech_descriptor",

  "geography": {
    "biomes": ["biome1", "biome2"],
    "resources_abundant": ["resource1"],
    "resources_scarce": ["resource2"],
    "hazard_zones": ["zone1", "zone2"],
    "chokepoints": ["location1"]
  },

  "ecology": {
    "primary_crops": ["crop1"],
    "fauna_economic": ["animal1"],
    "fauna_dangerous": ["predator1"],
    "endemic_diseases": ["disease1"]
  },

  "infrastructure": {
    "government_type": "descriptor",
    "economic_primary": "descriptor",
    "tech_access": "broad|restricted|monopolised",
    "social_mobility": "high|moderate|low|none"
  },

  "factions": [
    {
      "id": "faction_id",
      "type": "type_descriptor",
      "legitimacy": "legitimacy_source",
      "disposition": "disposition_descriptor",
      "control": ["resource1", "location1"]
    }
  ],

  "careers": ["career1", "career2"],

  "culture": {
    "core_values": ["value1", "value2"],
    "taboos": ["taboo1", "taboo2"],
    "trust_level": "high_generalised|low_particularised|tribal",
    "baseline_affect": "descriptor",
    "status_markers": ["marker1", "marker2"]
  },

  "environmental_hazards": ["hazard1", "hazard2"],

  "primary_stressors": ["stressor1", "stressor2"]
}
```

---

## Unity Integration Notes

### Terrain Generation

Use the `geography` section to constrain terrain generation:
- `biomes` → biome map zones and their asset assignments
- `resources_abundant/scarce` → deposit density parameters in resource placement algorithms
- `hazard_zones` → no-go or high-danger zone flagging
- `chokepoints` → forced settlement/fortification placement points

### NPC Generation

Use `careers` and `culture` sections to generate NPC profiles:
- Each career maps to a behavioural archetype and appearance asset set
- `core_values` constrain NPC dialogue options and response trees
- `taboos` determine refusal behaviours and hostility triggers
- `trust_level` sets the initial disposition toward the player

### Faction Dynamics

Use `factions` section to seed faction AI:
- `disposition` determines starting faction relationship modifiers
- `control` fields define territorial claims for conflict generation
- `legitimacy` field determines how factions respond to challenges to their authority

---

## Unreal Integration Notes

The same principles apply in Unreal. The JSON seed approach works identically — the difference is which Unreal systems consume which fields:

- Terrain → Landscape layers, PCG (Procedural Content Generation) Graph
- NPCs → Mass Entity framework, Smart Objects
- Factions → Gameplay Tag system for faction affiliation and disposition

The key is that Nexus gives you the semantic layer — what things *mean* in the world. The Unreal PCG tools give you the generation layer — how to instantiate things. These are separate concerns and should be kept separate.

---

## Python Export Helper (Planned)

A basic Python script to parse a completed `WORLD_OVERVIEW.md` and output a JSON seed is planned. It will:

1. Parse the markdown headers and code blocks
2. Extract key values from structured answers
3. Output a JSON file in the format above
4. Flag any missing required fields

This will be added to the repository when complete.

---

## Custom Simulation Tools

If building a custom simulation (e.g., an economic or population model), the Nexus data provides the initial conditions:

- Population size and distribution → from geography and infrastructure
- Resource availability → from geography and ecology
- Career distribution → from Step 6
- Faction control → from infrastructure
- Environmental stress curves → from environmental features

Start with a simple agent-based model where agents have a career, a faction affiliation, and basic resource needs. The Nexus data tells you what the starting distribution of these should look like and what the major stress vectors are.
