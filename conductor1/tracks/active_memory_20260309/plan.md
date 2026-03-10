# Implementation Plan: Active Memory and Skill Evolution

## Phase 1: Active Memory Injection [checkpoint: 0cb543a]
- [x] Task: [Scout] Search for keyword extraction patterns and `grep_search` usage in existing `.toml` prompts. [Skills: Repo-Pattern-Enforcer] [MCP: Search, FileSystem]
    - [x] Analyze how `implement.toml` and `newTrack.toml` can be modified to include automated memory lookups.
- [x] Task: Update `newTrack.toml` with Active Memory logic. [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Inject the "Memory Scan" protocol into Section 2.1 and 2.2.
    - [x] Mandate the agent to `grep_search` `conductor/memory.md` for track description keywords.
- [x] Task: Update `implement.toml` with mandatory Knowledge Retrieval. [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Revise Section 3.4.c.i (Knowledge Retrieval) to explicitly command a `grep_search` of the memory log for the task's keywords.
- [x] Task: Conductor - User Manual Verification 'Active Memory' (Protocol in workflow.md)

## Phase 2: Skill Evolution Pipeline [checkpoint: b32c068]
- [x] Task: [Scout] Analyze `createSkill.toml` for integration points and existing pattern extraction methods. [Skills: Repo-Pattern-Enforcer] [MCP: Search, FileSystem]
    - [x] Identify where to insert the "Pattern Audit" logic.
- [x] Task: Implement Pattern Audit logic in `createSkill.toml`. [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Add Section 1.1 "Pattern Audit" to `createSkill.toml`.
    - [x] Protocol must instruct the agent to analyze `conductor/memory.md` for patterns with 3+ occurrences.
- [x] Task: Update `workflow.md` to reflect Skill Evolution triggers. [Skills: Strict-Type-Auditor] [MCP: FileSystem]
    - [x] Add a note to the "Knowledge Synthesis" section in the Phase Completion Protocol about skill evolution checks.
- [x] Task: Conductor - User Manual Verification 'Skill Evolution' (Protocol in workflow.md)

## Phase 3: Final Meta-Verification [checkpoint: 0a1d992]
- [x] Task: End-to-End Simulation of Active Memory and Skill Audit. [Skills: Strict-Type-Auditor] [MCP: Shell]
    - [x] Verify that `newTrack` and `implement` correctly grep the memory file.
    - [x] Verify that `createSkill` correctly identifies "repeated" patterns.
- [x] Task: Conductor - User Manual Verification 'Final Verification' (Protocol in workflow.md)
