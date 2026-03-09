# Product Guidelines

## Design Principles
1.  **Strictness over Flexibility**: The system should error early and explicitly rather than making unsafe assumptions.
2.  **Explicit Context**: All AI prompts and file operations must be fully self-contained.
3.  **Zero Hallucination Tolerance**: Prefer "I don't know" or halting execution over guessing file paths or commands.
4.  **Professional Tone**: All communication with the user must be concise, professional, and signal-heavy.
5.  **Continuous Learning**: AI agents must contribute to and consult the project's "Brain" to improve performance over time.

## User Experience (UX)
1.  **CLI First**: Optimizations should prioritize command-line efficiency (minimal keystrokes, clear output).
2.  **Actionable Errors**: Every error message must suggest a clear next step or fix.
3.  **Progress Transparency**: Long-running operations must provide periodic status updates.

## Code Quality
1.  **Type Safety**: Use `strict: true` in TypeScript. No `any` allowed.
2.  **Anti-Mocking**: Tests should use real filesystem/shell interactions where possible to catch integration issues.
3.  **Repository Pattern**: Isolate data access logic from business logic.
4.  **Immutability**: Prefer immutable data structures and pure functions.

## Documentation
1.  **Markdown Everywhere**: All documentation and logs must be in standard Markdown.
2.  **Self-Documenting Code**: Code should be readable without comments; use comments to explain *why*, not *what*.
