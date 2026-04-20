# GhostMeshBrain Integration Mapping

This document provides the detailed technical mapping between Nexus Framework outputs and GhostMeshBrain agent parameters. It is a reference for developers integrating the two systems.

For the GhostMeshBrain repository and agent code, see: https://github.com/vanj900/GhostMeshBrain

---

## Overview

Nexus defines the world's structure, physics, culture, and economics. GhostMeshBrain provides the agent model that populates that world with NPCs that respond to it in physiologically and psychologically plausible ways.

The integration is conceptually simple: Nexus outputs become the priors and parameters that initialise each GhostMesh agent. The world shapes the agent's expectations; the agent's behaviour makes the world visible.

---

## World-Level Mappings

### World Personality → Agent Priors

**Source:** Step 7 of the Nexus loop (World Personality)

| Nexus Element | GhostMesh Target | Mapping Details |
|---|---|---|
| Core values | `belief_priors` | Values become weighted prior beliefs about what actions are good/expected |
| Taboos | `hard_constraints` | Taboo-violating actions are assigned near-infinite cost in the action selection model |
| Default emotional register | `baseline_valence`, `baseline_arousal` | "Flat grinding" → low valence, moderate arousal; "expressive" → higher variance on both |
| Trust level | `prior_precision_other_agents` | Low-trust culture → lower precision on beliefs about other agents' intentions |
| Status markers | `social_observation_weights` | Which environmental cues the agent attends to for social information |

### Environmental Features → Stressor Inputs

**Source:** Step 4 of the Nexus loop (Environmental Features)

GhostMesh uses a thermodynamic mortality model. Environmental hazards map directly to the agent's physical state variables:

| Environmental Feature | GhostMesh Variable | Effect |
|---|---|---|
| Radiation zones | `heat` accumulation | Sustained exposure drives heat above homeostatic range |
| Toxic / contaminated areas | `waste` accumulation | Toxin exposure increases metabolic waste production |
| Low-resource areas | `energy` depletion rate | Sparse environments increase baseline metabolic cost |
| Supernatural anomalies / AI signals | `surprise` term in free energy | Unpredictable sensory input increases prediction error |
| Social threats (surveillance, violence risk) | `threat_prior` | Increases precision-weighting on threat-related observations |
| Extreme cold / heat | `temperature_stress` | Deviations from optimal temperature increase entropy production |

### Infrastructure and Careers → Action Space

**Source:** Steps 5 and 6 of the Nexus loop

| Nexus Element | GhostMesh Target | Mapping Details |
|---|---|---|
| Career type | `available_actions` set | Career determines which actions are in the agent's repertoire |
| Career metabolic cost | `action_cost` values | High-exertion careers have higher metabolic cost per action |
| Career social status | `social_reward_prior` | Higher-status actions receive higher social reward weighting |
| Infrastructure access | `resource_access_map` | What resources the agent can reach determines survival options |
| Career failure / unemployment | `action_availability` flags | Job loss removes career actions; may require retraining transitions |

---

## Faction-Level Mappings

### Faction Personality → Group Prior

Each faction produces a set of priors that are applied to agents who are members:

| Faction Element | GhostMesh Target | Notes |
|---|---|---|
| Faction ideology | `group_belief_prior` | Faction members share a belief prior that differs from cultural baseline |
| In-group vs. out-group norms | `social_context_policy` | Different action policies apply when inside vs. outside the faction |
| Faction propaganda | `narrative_prior` | Official narrative shapes how agents interpret ambiguous evidence |
| Faction taboos | `contextual_constraints` | Faction-specific constraints on top of cultural constraints |

---

## NPC-Level Mappings

### NPC Personality → Individual Agent Configuration

Individual NPC personality data from the Nexus loop maps to the agent's initialisation parameters:

| NPC Element | GhostMesh Target | Notes |
|---|---|---|
| Personality masks | `context_policy_map` | Each mask is a separate action policy that activates in its context |
| Core rigid beliefs | `fixed_beliefs` | Beliefs that are not updated regardless of evidence (identities, loyalties) |
| Flexible beliefs | `updatable_beliefs` | Beliefs that respond to prediction errors in normal operation |
| Stress triggers | `high_precision_sensory_inputs` | Specific inputs that cause disproportionate surprise response |
| Coping strategies | `default_stress_response_policy` | The action policy that activates under high-stress conditions |
| Trauma history | `prior_surprise_accumulation` | Pre-loaded accumulated prediction error that shapes sensitivity |

---

## Stress Response Integration

The Expert Integration document (EXPERT_INTEGRATION.md) psychology section identifies stress triggers and coping strategies. These map to GhostMesh's stress response system:

**Psychology Review → GhostMesh Stress Model:**

| Psychology Element | GhostMesh Mapping |
|---|---|
| Trauma vectors | Historical `surprise` accumulation |
| Attachment style | `social_bond_precision` and loss response weighting |
| Adaptive cognitive distortions | `biased_likelihood` parameters in relevant domains |
| Psychological safety valves | `stress_relief_actions` with high action value under high stress |
| Identity structure collapse triggers | `identity_prior` disruption → large free energy spike |

---

## Implementation Notes

### Priority Order for Integration

1. **Start with environmental hazards** — these are the most direct mappings and have the highest impact on behaviour
2. **Add career action spaces** — determines what agents can do day-to-day
3. **Set cultural priors** — baseline beliefs and values
4. **Layer faction priors** on top of cultural priors
5. **Configure individual NPC parameters** last

### Known Limitations

- Nexus operates at description level; GhostMesh requires numeric parameters. Most mappings require a translation step where the developer decides on specific parameter values consistent with the description.
- Personality masks in Nexus are qualitative descriptions; GhostMesh requires explicit context triggers and policy definitions for each mask.
- "Trust level" in Nexus is a cultural descriptor; in GhostMesh it becomes a precision parameter that requires calibration against the specific social dynamics of the setting.

### Suggested Workflow

1. Complete a full Nexus loop for the world and relevant factions/NPCs.
2. Export to JSON using the seed format shown in the examples.
3. Write a translation layer script that maps JSON fields to GhostMesh initialisation parameters.
4. Run a small test simulation with 3–5 agents in a representative environment.
5. Check that agent behaviour matches the Nexus description. Adjust parameter values.
6. Iterate.
