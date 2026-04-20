# Nexus Framework Loop

A practical, iterative system for building deep, coherent, and believable game worlds — from galaxy-spanning lore down to individual NPCs.

Created because most world-building advice is either vague hand-waving or endless spreadsheets that never connect. Nexus forces structure while staying flexible. It scales from entire universes to single characters, and it bakes in real psychology, sociology, and behaviour principles so your worlds don't feel like cardboard cutouts.

It pairs especially well with **[GhostMeshBrain](https://github.com/vanj900/GhostMeshBrain)** — a living AI agent framework that gives NPCs actual thermodynamic mortality, stress responses, personality masks, and active inference. Nexus defines the world; GhostMesh makes the inhabitants *feel* it.

---

## Why It Exists

Modern games are full of pretty but shallow worlds. Players poke once and the illusion collapses. Nexus is a loop that makes every layer influence the others:

- Geography shapes culture and jobs.
- Infrastructure creates believable careers and conflicts.
- Environmental stress affects behaviour and mental states.
- Everything iterates so contradictions get caught early.

Non-coders can use it with pen and paper or a doc. Devs can export the outputs to JSON and feed them into procedural systems or GhostMesh agents.

---

## Core Concept

The **Nexus Framework Loop** is a cyclical process with these main steps (applied at World, Area, Faction, or NPC level):

1. **Define the World** — Genre, theme, history, time period.
2. **Detail Geographical Data** — Layout, climate, terrain.
3. **Specify Flora and Fauna** — Ecosystems and their interactions.
4. **Identify Environmental Features** — Landmarks, hazards, anomalies.
5. **Establish World Infrastructure and Dynamics** — Politics, economy, technology/magic, social structures.
6. **Generate Careers from Infrastructures** — Jobs and daily lives that emerge naturally.
7. **Determine World Personality** — Cultural traits, norms, mood, rituals.

Then loop back: refine, stress-test with expert-style psych/soc/behaviour questions, and improve.

Full question lists, alignment checks, and expert integration process are in the docs.

---

## Quick Start

1. Clone or just read the files — no installation required for core use.
2. Open `WORLD_OVERVIEW.md` or `NEXUS_FRAMEWORK.md`.
3. Answer the structured questions for your setting.
4. Run one full loop.
5. Iterate as needed.

Example worlds are in the `examples/` folder (including the grimdark post-apocalyptic **Rust Belt** we built as a demo).

### For Non-Coders / Writers / Tabletop GMs

- Print the question sheets or copy them into Notion/Google Docs.
- Use it for novels, D&D campaigns, or solo world-building.
- The child-friendly proof-of-concept in the original doc shows it's accessible.

### For Game Developers

- Export outputs to JSON (basic helper script coming soon).
- Feed into procedural generation tools, Unity/Unreal, or directly into GhostMeshBrain agents.
- Tie environmental hazards to agent stress/heat/waste, infrastructure to available careers/actions, and world personality to baseline affect and masks.

---

## Repository Contents

| File / Folder | Description |
|---|---|
| `NEXUS_FRAMEWORK.md` | Full original framework with questions, flowchart, and expert review process |
| `WORLD_OVERVIEW.md` | Structured question set for starting a new world |
| `EXPERT_INTEGRATION.md` | Psych, sociology, and behaviour analyst alignment checks |
| `examples/` | Ready-to-use demo worlds (Rust Belt + others) |
| `integration/` | Notes on pairing with GhostMeshBrain and procedural tools |
| `CONTRIBUTING.md` | How to contribute |

---

## Integration with GhostMeshBrain

This is where it gets fun.

Nexus outputs become priors and parameters for GhostMesh agents:

- **World Personality** → baseline affect and personality masks.
- **Infrastructure & Careers** → available actions and metabolic costs.
- **Environmental Features & Hazards** → direct stressors (radiation = heat spikes, AI whispers = surprise terms).
- **Expert feedback loops** → tune the ethics engine and belief pruning.

Result: NPCs that don't just stand there reciting lore — they react, adapt, rigidify under pressure, or die in ways that make sense for your world.

See the GhostMeshBrain repo for the actual agent code: https://github.com/vanj900/GhostMeshBrain

---

## Contributing

Contributions are welcome — examples, new genres, helper scripts, bug fixes, or better integration ideas.

- Non-coders: Add world examples or improve the question lists.
- Coders: Python helpers for JSON export, GhostMesh integration, or small simulation tools are especially useful.
- Everyone: Keep it practical. No feature bloat.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for details.

---

## License

MIT — do whatever you want with it. Build games, run campaigns, fork it, sell tools built on top of it. Just don't be a dick about attribution if you repackage the whole thing.

---

## Contact / Thanks

Made by [vanj900](https://github.com/vanj900).  
GhostMeshBrain is the companion project if you want living agents inside these worlds.

If you build something cool with Nexus (or Nexus + GhostMesh), drop a link — I'd love to see it.

Now go make a world that doesn't fall apart when the player looks at it sideways.