# Project Workflow

## Guiding Principles

1. **The Plan is the Source of Truth:** All work must be tracked in `plan.md`
2. **The Tech Stack is Deliberate:** Changes to the tech stack must be documented in `tech-stack.md` *before* implementation
3. **Test-Driven Development (TDD):** Write unit and integration tests *before* implementing functionality.
4. **Anti-Mocking Philosophy:** Prefer real data and real environments (e.g., Testcontainers, local DBs) over heavy mocking. Mocks are for external APIs only.
5. **High Code Coverage & Strictness:** Aim for 100% coverage and zero linting/typing errors.
6. **Task Execution Philosophy:** 
   - **One Agent, One Task, One Prompt**: Each task is a self-contained operation.
   - **No Ambiguity**: Specifications must include line numbers, code snippets, and explicit instructions.
   - **Knowledge-Aware**: AI agents must consult the project's **Memory** (`conductor/memory.md`) before implementation and contribute to it after completion.
7. **Non-Interactive & CI-Aware:** Prefer non-interactive commands. Use `CI=true` for watch-mode tools.
8. **Commit Frequency:** Changes are committed once per phase to maintain a clean, high-level history.

## Track Lifecycle: PR & Dev Branches

1. **Initialize Track Branch:**
   - Before starting a track, create a dedicated dev branch: `git checkout -b dev/<track-id>`.
2. **Development**: Follow the standard task workflow below on the track branch.
3. **Quality Gates**:
   - Run `pnpm audit` for dependency security.
   - Run `pnpm test` (Anti-Mocking approach).
   - Perform "Strictness Audit" (Type checks & Linting).
4. **Pull Request (PR)**:
   - Once all tasks in `plan.md` are complete, create a PR to `main`.
   - AI Agent must verify the PR against the **Repository Pattern** and **Redundancy** check.
5. **Merge & Cleanup**: Merge to `main` and delete the dev branch.

## Standard Task Workflow

All tasks follow a strict lifecycle:

1. **Select Task:** Choose the next available task from `plan.md` in sequential order

2. **Mark In Progress:** Before beginning work, edit `plan.md` and change the task from `[ ]` to `[~]`

3. **Write Failing Tests (Red Phase):**
   - Create a new test file for the feature or bug fix.
   - Write one or more unit tests that clearly define the expected behavior and acceptance criteria for the task.
   - **CRITICAL:** Run the tests and confirm that they fail as expected. This is the "Red" phase of TDD. Do not proceed until you have failing tests.

4. **Implement to Pass Tests (Green Phase):**
   - Write the minimum amount of application code necessary to make the failing tests pass.
   - Run the test suite again and confirm that all tests now pass. This is the "Green" phase.

5. **Refactor (Optional but Recommended):**
   - With the safety of passing tests, refactor the implementation code and the test code to improve clarity, remove duplication, and enhance performance without changing the external behavior.
   - Rerun tests to ensure they still pass after refactoring.

6. **Verify Coverage:** Run coverage reports using the project's chosen tools. Target: 100% coverage for new code.

7. **Document Deviations:** If implementation differs from tech stack:
   - **STOP** implementation
   - Update `tech-stack.md` with new design
   - Add dated note explaining the change
   - Resume implementation

8. **Prepare for Phase Commit:**
   - Changes are staged but NOT committed until the entire phase is complete.
   - Detailed task summaries are recorded for inclusion in the final phase commit message (Business Standard).

9. **Knowledge Capture (Update Memory Log):**
   - **Action:** If the task resulted in a new reusable pattern, a significant lesson learned, or a unique technical fix, record it in `conductor/memory.md`.
   - **Meta-Awareness:** Pay special attention to documenting **Project Type** specific insights (e.g., "In extension development, always check for available skills before proceeding").
   - **Format:** Use the "Knowledge Snippet Format" defined in the memory file. Ensure the "Impact" section explains how this insight prevents future errors or redundancy.

10. **Get and Record Task Status:**
    - **Step 10.1: Update Plan:** Read `plan.md`, find the line for the completed task, and update its status from `[~]` to `[x]`.
    - **Step 10.2: Write Plan:** Write the updated content back to `plan.md`.

### Phase Completion Verification and Checkpointing Protocol

**Trigger:** This protocol is executed immediately after a task is completed that also concludes a phase in `plan.md`.

1.  **Announce Protocol Start:** Inform the user that the phase is complete and the verification and checkpointing protocol has begun.

2.  **Knowledge Synthesis (Update Brain):**
    -   **Action:** Review all task-level entries in the memory log for this phase.
    -   **Strategic Synthesis:** Identify insights that represent fundamental shifts in project understanding (e.g., "The repository is actually the tool source, not a target app").
    -   **Consolidate:** Promote the most significant insights to the **Pattern Library** or **Lessons Learned** sections of `conductor/memory.md`.
    -   **Skill Evolution Check:** Check if any pattern has been reused 3+ times. If so, recommend creating a permanent AI skill via `/conductor:createSkill`.
    -   **Documentation Update:** If the synthesis reveals a gap in the `Product Definition` or `Guidelines`, propose an update immediately.

3.  **Ensure Test Coverage for Phase Changes:**
    -   **Step 3.1: Determine Phase Scope:** Identify all changes since the last phase checkpoint or the start of the track.
    -   **Step 3.2: List Changed Files:** Use `git diff --name-only` to list modified files.
    -   **Step 3.3: Verify and Create Tests:** Ensure every modified code file has 100% test coverage.

4.  **Execute Automated Tests with Proactive Debugging:**
    -   Run the full test suite and announce the command.
    -   If tests fail, debug and fix (max 2 attempts) before asking for guidance.

5.  **Propose a Detailed, Actionable Manual Verification Plan:**
    -   Analyze requirements and present a step-by-step plan for the user to verify the phase goals.

6.  **Await Explicit User Feedback:**
    -   Wait for the user to confirm "yes" after manual verification.

7.  **Create Phase Checkpoint Commit:**
    -   Stage all changes (code and `plan.md`).
    -   Perform the commit with a detailed summary of all tasks completed in the phase (Business Standard summary format).
    -   Message format: `feat/fix(<scope>): Phase completion - <Phase Name>\n\n<Consolidated Task Summaries>`

8.  **Get and Record Phase Checkpoint SHA:**
    -   **Step 8.1: Get Commit Hash:** Obtain the hash of the phase checkpoint commit.
    -   **Step 8.2: Update Plan:** Record the SHA in `plan.md` next to the phase header: `[checkpoint: <sha>]`.

9.  **Announce Completion:** Inform the user that the phase is complete and the checkpoint has been created.

### Quality Gates

Before marking any task complete, verify:

- [ ] All tests pass
- [ ] Code coverage meets requirements (100%)
- [ ] Code follows project's code style guidelines
- [ ] All public functions/methods are documented
- [ ] Type safety is enforced
- [ ] No linting or static analysis errors
- [ ] Documentation updated if needed
- [ ] No security vulnerabilities introduced

## Commit Guidelines

### Message Format (Business Standard)
```
<type>(<scope>): <description>

Detailed summary of changes and technical rationale.
- Task 1: Implementation details...
- Task 2: Implementation details...
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting, missing semicolons, etc.
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `test`: Adding missing tests
- `chore`: Maintenance tasks
