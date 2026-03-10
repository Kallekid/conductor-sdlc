# Conductor SDLC: Configuration & Capability Index

This file serves as the central index for **Conductor SDLC**, the professional orchestration framework for Gemini CLI. It is the "Brain" of the SDLC system for this repository.

## 1. Core Workflows
These are the standard operating procedures for **Conductor SDLC**.

- **Standard Development Workflow**: Defined in `conductor/workflow.md`.
  - **Key Philosophy**: Anti-Mocking (Real data preference), TDD (Red-Green-Refactor), Strict Types.
  - **Phases**: Planning -> Analysis -> Design -> Implementation -> Testing -> Deployment -> Maintenance.
- **New Project Initialization**:
  - **Command**: `/conductor:newProject`
  - **Description**: Initializes a new project or analyzes an existing one, guiding it through the SDLC.
- **Track Management**:
  - **Command**: `/conductor:newTrack`
  - **Description**: Creates a new feature/bug track with a detailed `spec.md` and `plan.md`.

## 2. Skills (AI Capabilities)
These are specialized capabilities available to the AI agents.

### Built-in Skills
- **Repository Pattern Enforcer**:
  - **Description**: Ensures all data access goes through repository abstractions.
  - **Usage**: Invoked during `newTrack` and code review.
- **Redundancy Detector**:
  - **Description**: Scans for duplicated logic across modules.
  - **Usage**: Invoked during `newTrack` and implementation.
- **Strictness Auditor**:
  - **Description**: Verifies adherence to strict typing and linting rules.
  - **Usage**: Invoked during `review` and pre-commit.

### Custom Skills
*Run `/conductor:createSkill` to add new skills.*

- *(No custom skills defined yet)*

## 3. Model Context Protocols (MCPs)
These are the external tools and interfaces available.

- **FileSystem**: Read/Write files.
- **Shell**: Execute commands (pnpm, git, etc.).
- **Search**: `grep_search`, `glob`, `ripgrep`.
- **Browser**: `puppeteer` (for E2E testing).

## 4. Commands Index

| Command | Description |
| :--- | :--- |
| `/conductor:setup` | Scaffolds the basic Conductor environment (quick setup). |
| `/conductor:newProject` | The SDLC Master: Interactive project setup & SDLC orchestration. |
| `/conductor:newTrack` | Create a new work track (feature/bug). |
| `/conductor:implement` | Implement a task from the plan. |
| `/conductor:review` | Review code against strict guidelines. |
| `/conductor:createSkill`| Create a new AI skill definition. |
| `/conductor:status` | Check project health and active tracks. |

## 5. Configuration Standards

### Dependency Management
- **Tool**: `pnpm`
- **Flags**: Always use `--quiet` or `--silent` to minimize token usage.
- **Audit**: Run `pnpm audit` regularly.

### Code Quality
- **Typing**: Strict (`noImplicitAny`, `strictNullChecks`).
- **Architecture**: Enforced via `dependency-cruiser`.
- **Testing**: Anti-Mocking. E2E preferred over heavy unit mocking.

### Performance
- **Benchmarking**: Measure resource usage for critical paths.

## 6. SDLC Interview Protocol
When initializing a project or a new major track, the system must perform a multi-perspective interview to ensure zero ambiguity.

### SDLC Persona Mapping
| SDLC Phase | Traditional Roles | Scrum Equivalent | Focus Area |
| :--- | :--- | :--- | :--- |
| **Planning** | PM, Project Manager, Stakeholders | **Product Owner (PO)**, SM, Dev Team | Vision, Backlog, Feasibility |
| **Requirements** | Business Analyst, PO, End Users | **PO**, Dev Team, SM | User Stories, Backlog Refinement |
| **Design** | System Architect, UX/UI, Tech Leads | **Dev Team**, PO, SM | Architecture, UX/UI, Prototypes |
| **Coding** | Software Developers, Tech Leads | **Dev Team**, PO, SM | Code, Reviews, Test-Writing |
| **Testing** | QA, Testers, Developers | **Dev Team**, PO, SM | Unit/Integration/E2E, Validation |
| **Deployment** | DevOps, Release Managers, PM | **Dev Team**, PO, SM | CI/CD, Monitoring, Readiness |
| **Maintenance**| Developers, Support, PM | **Dev Team**, PO, SM | Bug-Fixes, Feature Enhancements |

- **Goal**: Create a comprehensive specification that requires no inference from the AI during implementation.

## 7. Advanced Execution Principles

### 7.1 Mandatory Scouting Phase
- **Protocol**: Every task in `plan.md` MUST begin with a `[Scout]` sub-task.
- **Action**: Use `grep_search` and `glob` to find existing patterns, utility functions, or infrastructure that can be reused before writing new code.
- **Goal**: Scaffolding-first mentality; avoid reinventing the wheel.

### 7.2 Tool-Tagged Tasks
- **Protocol**: Every task in the plan must specify which **Skills**, **Workflows**, and **MCPs** are required.
- **Example**: `- [ ] Task: Implement User Repo [Skills: Repo-Pattern-Enforcer] [MCP: FileSystem]`.

### 7.3 Resource & Performance Budgets
- **Protocol**: The `spec.md` must define explicit budgets (CPU, Memory, Latency) for critical features.
- **Action**: Benchmarking skills must verify implementation against these budgets.

### 7.4 Self-Healing & Redundancy
- **Protocol**: If an agent identifies logic being duplicated for the 3rd time, it must HALT and propose a refactoring track instead of continuing.

## 8. Branching & PR Strategy
Tracks are developed in isolation to ensure stability.

- **Feature Branches**: Every track must have its own `dev/track-name` branch.
- **Pull Requests (PRs)**: 
  - Automated PR creation upon track completion.
  - Mandatory "Strictness Audit" and "Repository Pattern Check" before merging.
  - Automated `pnpm audit` and performance benchmarking on every PR.

## 8. Task Execution Philosophy
- **Atomicity**: One agent, one task, one prompt. Do not combine unrelated tasks.
- **Orchestration**: All `[Scout]` tasks MUST be delegated to the `codebase_investigator` sub-agent to maintain main-loop context efficiency.
- **No Ambiguity**: Specifications must include line numbers, code snippets, and explicit instructions.
- **Anti-Mocking**: Tests must use real database instances (or containers) and real network responses whenever possible to avoid "mocking bugs".

## 9. Dependency Cruiser Rules
Enforced architectural boundaries:
- **UI -> Data**: Forbidden. UI components must never import directly from data/persistence layers.
- **Domain -> Infrastructure**: Forbidden. Business logic must be agnostic of implementation details.
- **Circular Dependencies**: Zero tolerance.
