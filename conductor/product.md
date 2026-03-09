# Product Guide: Conductor SDLC

## Initial Concept
**Project Name:** Conductor SDLC
**Goal:** To provide a professional, AI-driven orchestration framework for the Gemini CLI that enforces strict software development lifecycle (SDLC) standards, including architectural patterns, testing strategies, and quality gates.

## Vision
Conductor SDLC aims to transform Gemini CLI usage from ad-hoc task execution into a disciplined engineering process. By integrating expert personas (Product Owner, QA, Architect), it ensures that every line of code is intentional, specified, and verified.

## Core Features
1.  **SDLC Master (`/conductor:newProject`)**: Interactive project initialization with multi-persona interviews to define clear technical vision.
2.  **Architectural Enforcement**: Automated checks for the Repository Pattern, strict boundaries (e.g., no UI -> Data direct imports), and anti-mocking strategies.
3.  **Scouting-First Workflow**: Mandates a "scout" phase to analyze existing code before implementation to prevent redundancy.
4.  **Automated Quality Gates**: Integrated `pnpm audit`, strict TypeScript/ESLint rules, and performance benchmarking for every track.
5.  **Granular Task Management**: "One Agent, One Task, One Prompt" philosophy to minimize AI hallucinations and errors.
6.  **Project Memory & Knowledge Base**: A dynamic "Brain" (`conductor/memory.md`) that stores project-specific insights, patterns, and technical fixes for continuous improvement.

## Target Audience
-   **Senior Engineers**: Who value rigorous standards and want to automate the enforcement of best practices.
-   **Teams**: Who need consistent architectural patterns across multiple developers using AI assistance.
-   **Gemini CLI Users**: Who want to move beyond simple scripts to building complex, production-grade applications.
