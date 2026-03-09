# Implementation Plan: Enhance Extension Self-Awareness and Skills Discovery

## Phase 1: Self-Awareness & Skills Audit [checkpoint: 1839019]
- [x] Task: [Scout] Current extension discovery logic in `setup.toml` and `newProject.toml` [Skills: Repo-Pattern-Enforcer] [MCP: Search, FileSystem]
    - [x] Analyze how the system currently handles "Brownfield" detection.
    - [x] Search for any references to "Skills" or "Extension Source" in current prompts.
- [x] Task: Implement Meta-Project Detection [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Update `commands/conductor/setup.toml` to explicitly check for `gemini-extension.json` and the `commands/` directory.
    - [x] Ensure that detection results in a unique greeting and memory initialization.
- [x] Task: Implement Skills Readiness Protocol [Skills: Strict-Type-Auditor] [MCP: Shell, FileSystem]
    - [x] Add a step to the setup process to verify available skills using `activate_skill`.
    - [x] Create a protocol for handling missing skills.
- [x] Task: Conductor - User Manual Verification 'Self-Awareness & Skills Audit' (Protocol in workflow.md)

## Phase 2: Knowledge Base & Memory Refinement [checkpoint: 1839019]
- [x] Task: Initialize Project Memory with Meta-Context [Skills: Repo-Pattern-Enforcer] [MCP: FileSystem]
    - [x] Update `conductor/memory.md` to define the repository as the **Conductor SDLC extension source code**.
    - [x] Map the relationship between source code and management files.
- [x] Task: Update Knowledge Capture Protocol [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Ensure the "Brain" update in the workflow captures why certain project-level contexts are important.
- [x] Task: Conductor - User Manual Verification 'Knowledge Base & Memory Refinement' (Protocol in workflow.md)

## Phase 3: Documentation & Architectural Clarity [checkpoint: 1839019]
- [x] Task: Create Architectural Map in `product.md` [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Explain the roles of `commands/`, `templates/`, and `conductor/`.
    - [x] Detail how prompt logic drives the SDLC phases.
- [x] Task: Final Verification [Skills: Strict-Type-Auditor] [MCP: Shell]
    - [x] Run a simulated project initialization to verify self-awareness and skills discovery.
- [x] Task: Conductor - User Manual Verification 'Final Verification' (Protocol in workflow.md)
