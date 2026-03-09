# Specification: Enhance Extension Self-Awareness and Skills Discovery

## Goal
Improve the **Conductor SDLC** extension's internal logic to be self-aware of its own repository and robust against missing dependencies like "Skills." This ensures that when a user (or AI) initializes the project, the system immediately recognizes it is working on the Conductor source code and captures this in the Project Memory.

## Core Features
1. **Meta-Project Detection**:
   - Update `setup` and `newProject` prompts to check for the presence of `gemini-extension.json` and the `commands/conductor` directory.
   - If detected, immediately record "Project Type: Conductor Extension Development" in `conductor/memory.md`.
2. **Skills Readiness Check**:
   - Implement a protocol to list available skills during project initialization.
   - If no skills are found, provide the user with a "Skill Scaffolding" track suggestion.
3. **Architectural Memory**:
   - Document the relationship between the **Source Code** (`commands/`, `templates/`) and the **Management Layer** (`conductor/`).
   - Map how prompt logic in `.toml` files drives the SDLC phases.

## Quality Gates
- [ ] Memory file contains the correct "Meta-Project" context after setup.
- [ ] Setup command correctly warns if skills are missing.
- [ ] Documentation clearly explains the "Brain" vs. "Source" distinction.
