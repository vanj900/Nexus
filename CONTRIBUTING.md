# Contributing to Nexus

Contributions are welcome — examples, new genres, helper scripts, bug fixes, or better integration ideas.

Keep it practical. No feature bloat.

---

## What's Useful

### For Non-Coders / Writers / Tabletop GMs

**New world examples** are the most valuable contribution you can make.

A good example:
- Is a completed `WORLD_OVERVIEW.md` fill-in (all steps answered, even briefly)
- Has at least one expert review section with honest gap identification
- Includes a JSON seed at the end
- Is a genre or setting type not already covered

Other useful contributions:
- Improvements to question lists in `NEXUS_FRAMEWORK.md` — clearer wording, better coverage
- Additional expert review questions for domains not yet covered
- Corrections to the existing examples where they break their own rules

### For Developers

Useful code contributions:
- **Python JSON export helper** — parse a completed `WORLD_OVERVIEW.md` and output the JSON seed format (see `integration/procedural_notes.md` for the format spec)
- **GhostMeshBrain integration examples** — concrete code showing how to initialise a GhostMesh agent from a Nexus JSON seed
- **Validation script** — check a completed `WORLD_OVERVIEW.md` for missing required fields
- **Other procedural integration code** — Unity, Unreal, Godot, or custom simulation tools

---

## How to Contribute

1. Fork the repository.
2. Create a branch named after your contribution: `example/my-world-name`, `fix/framework-question-typo`, `script/json-export`, etc.
3. Make your changes.
4. Submit a pull request with a clear description of what you added and why.

---

## Standards

### For Examples

- Use the structure from `WORLD_OVERVIEW.md` — fill it in, don't invent a new format.
- All 7 steps must be present, even if some answers are brief.
- Include at least 10 careers generated from the infrastructure (Step 6 requirement).
- Include expert review notes (even brief ones) so the example shows the process, not just the output.
- Include a JSON seed at the end.
- Place the file in `examples/` and update `examples/README.md`.

### For Framework Changes

- Changes to question sets must not reduce the number of questions — additions and clarifications only.
- Changes to the core loop structure (Steps 1–7) require strong justification. The loop is the product.
- New expert review domains are welcome — add a full section to `EXPERT_INTEGRATION.md` following the existing pattern.

### For Code

- Match the style of existing code in the repository.
- No new dependencies without strong justification.
- Scripts should work with standard library tools where possible.
- Document what the script does and what inputs it expects.

---

## What Not to Submit

- Incomplete examples (stub files with half the questions answered)
- Changes that add complexity without adding usefulness
- World examples that are thinly veiled copies of existing media IP
- Code that requires a complex installation process

---

## Questions

Open an issue. Label it `question` if you want discussion before submitting a PR.
