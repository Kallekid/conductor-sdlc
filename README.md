# Conductor SDLC 🚀

**Conductor SDLC** is an advanced, AI-driven orchestration framework for the Gemini CLI. It transforms software development into a high-fidelity, spec-driven lifecycle (SDLC) by integrating expert personas, strict architectural enforcement, and automated quality gates.

## Core Pillars

- **SDLC Master (`/conductor:newProject`)**: A high-fidelity initialization engine. It conducts multi-persona interviews (Product Owner, Lead Developer, QA/Scrum Master) to eliminate ambiguity and define a clear technical vision before coding begins.
- **Architectural Enforcement**: Natively supports and enforces the **Repository Pattern**, **Anti-Mocking**, and clean architectural boundaries (e.g., blocking `UI -> Data` imports via `dependency-cruiser`).
- **Scouting-First Mentality**: AI agents are directed to "scout" existing infrastructure and patterns before implementation, ensuring maximum reuse and zero redundancy.
- **One Agent, One Task, One Prompt**: Granular task decomposition that ensures AI focus and minimizes errors.
- **Security & Quality Gates**: Integrated `pnpm audit`, strict TypeScript/ESLint rules, and performance benchmarking for every track.

## Installation

```bash
gemini extensions install github.com/Kallekid/conductor
```

## Quick Start

1. **Initialize or Import a Project**:
   ```bash
   /conductor:newProject
   ```
   Let the SDLC Master interview you to define your vision, tech stack, and resource budgets.

2. **Plan a New Feature**:
   ```bash
   /conductor:newTrack "Add user authentication"
   ```
   Define the specification and implementation plan with the AI.

3. **Execute and Verify**:
   ```bash
   /conductor:implement
   ```
   Follow the TDD (Red-Green-Refactor) lifecycle with mandatory scouting and real-data verification.

## Documentation

- **Core Index**: Check `GEMINI.md` for the central index of all Workflows, Skills, and MCPs.
- **Workflow Standards**: See `conductor/workflow.md` for details on the TDD and PR process.

## Credits & License

This project is a fork of the original [Conductor](https://github.com/gemini-cli-extensions/conductor) extension, significantly enhanced with professional SDLC capabilities and architectural enforcement.

Licensed under the **Apache License 2.0**. See the `LICENSE` file for the full text.
