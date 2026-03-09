# Specification: Active Memory and Skill Evolution

## Goal
Transform the **Conductor SDLC** memory system from a passive log into an active, context-injecting "Brain" and establish a pipeline for evolving frequently used patterns into permanent AI Skills.

## Core Features
1. **Active Memory (Context Injection)**:
   - Automated keyword-based `grep_search` of `conductor/memory.md` during track planning and task implementation.
   - Automatic injection of relevant "Lessons Learned" and "Patterns" into the AI agent's immediate context.
2. **Guided Skill Evolution**:
   - Enhancement of `/conductor:createSkill` to include a "Pattern Audit" phase.
   - The system must proactively suggest creating a skill if a pattern is detected 3+ times in the memory log.

## Acceptance Criteria
- `newTrack.toml` performs a memory check before drafting specs.
- `implement.toml` mandates a memory check for every task.
- `createSkill.toml` begins with an audit of `conductor/memory.md`.
- No regressions in standard setup or track management.
