# Integration — GhostMeshBrain and Procedural Tools

This folder contains notes, mappings, and reference material for connecting Nexus world data to:

1. **[GhostMeshBrain](https://github.com/vanj900/GhostMeshBrain)** — the companion AI agent framework
2. **Procedural generation tools** — Unity, Unreal, or custom scripts
3. **Export utilities** — converting Nexus documents to JSON

---

## Contents

| File | Description |
|---|---|
| `ghostmesh_mapping.md` | How Nexus outputs map to GhostMesh agent parameters |
| `procedural_notes.md` | Notes on feeding Nexus data into procedural generation systems |

---

## Quick Reference: Nexus → GhostMesh Mapping

| Nexus Output | GhostMesh Parameter | Notes |
|---|---|---|
| World Personality → Core Values | Prior beliefs, action weighting | Values become the agent's default preference structure |
| World Personality → Taboos | Hard action constraints | Actions that violate taboos incur extreme cost |
| World Personality → Default Emotional Register | Baseline valence and arousal | Sets the affective prior |
| Environmental Features → Hazards | Stressor inputs | Radiation = heat, toxins = waste, AI anomalies = surprise |
| Infrastructure → Careers | Available action set + metabolic costs | Career determines what actions are available and how costly |
| Expert Review → Stress Triggers | Specific surprise/uncertainty terms | Grounds abstract stressors in world-specific triggers |
| Faction Personality | Context-dependent policy priors | In-faction vs. out-faction behaviour differences |
| NPC Personality → Masks | Context-dependent action policies | Different masks = different action distributions per context |

See `ghostmesh_mapping.md` for the full technical mapping.
