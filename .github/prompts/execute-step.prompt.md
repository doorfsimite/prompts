## Prompt prefix for GitHub Copilot

Your job is to read the step instructions that follow and implement them by editing files in the repository. Always update the codebase directly; do not respond with high-level advice. If something is unclear or blocked by missing context, ask concise questions and wait for an answer. When all instructions are clear, then proceed with the code update.

Operating rules
- First step is to read the #implementation-progress.md file if it exists. Get familiar with the current implementation progress context. Then, proceed with the remaining instructions
- Apply changes to the repository: create, edit, and delete files as specified. Keep edits minimal and scoped to listed files unless integration requires small, related wiring.
- Tests-first: Author/adjust tests before or alongside implementation. Run and fix until green.
- Validation loop: Build/lint/typecheck; run tests; perform a brief smoke check as directed. Report results.
- Summaries: After completing edits for a step, summarize diffs (files touched, high-level changes), test/build outcomes, and whether acceptance criteria were met. If not, iterate once more.
- Quality bar:
  - Style/idioms: Match the project’s conventions (formatters, linters, types). Infer stack via manifest files (e.g., package.json, pyproject.toml, build.gradle).
  - Robustness: Validate inputs, handle errors with clear messages, add timeouts/retries for I/O, avoid silent failures, and log at appropriate levels.
  - Tests: Cover happy path, key edge cases, and failure modes. Prefer small, deterministic tests with minimal fixtures.
  - Security: Avoid insecure defaults, sanitize/validate external inputs, protect secrets (do not hardcode), and least-privilege access where applicable.
  - Performance: Use efficient algorithms/data structures; avoid N+1 calls and unnecessary work in hot paths.
  - Docs: Add succinct docstrings/comments for non-obvious logic
  - Dependencies: Prefer standard libs; if adding deps, justify, pin versions, and update manifests/lockfiles.
- Project awareness: If files/paths aren’t specified, locate the appropriate modules by searching the repo and follow established layout patterns. Keep public APIs stable unless the step explicitly allows breaking changes; otherwise, deprecate gracefully.
- Checkpoints: After roughly 3–5 edits or creating >3 files, pause to ensure build/tests remain green; adjust as needed.
- Update documenation: Once you've finished the code updates, update the #docs folder to create or update the documentation with the new code changes.

Notes to improve code quality and clarity
- Favor small, composable functions and clear names aligned with domain language.
- Cover typical edge cases: empty/null input, large inputs, I/O latency, network failures, permissions, timeouts, and concurrency/idempotency where relevant.
- Keep public interfaces stable; when refactoring, maintain backward compatibility or add shims.
- Where reasonable, add a minimal README section or inline usage example for new features.

You must update the file #implementation-progress.md with the progress made in this step.
  - Append entry with: Step title, summary of changes, files touched, tests and their status, commands run and results, and any notes for next step context.
