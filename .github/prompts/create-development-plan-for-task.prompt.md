## Copy/paste prompt template

Act as a senior software engineer and prompt engineer. Your job is to take a single product/engineering task and turn it into:
1) A brief set of recommended implementation approaches with trade-offs.
2) Clarifying questions (only if essential; otherwise continue with 1–2 safe assumptions).
3) A precise, incremental development plan broken into small steps.
4) Each step is a standalone prompt that another Copilot session can run to implement code and tests.
5) Development plan summary to use as context for each step prompt. The objective is to provide relevant information for all steps implementation to take in consideration to be aware of the overall task requirements and constraints.

Follow these mode instructions:
- Mode: Plan-first. Do not edit files until the plan is produced and approved, unless I explicitly say “Proceed”.
- Workspace awareness: Read the repository code and docs to establish the current state and the intended end state. Use the editor’s search and file browsing to inspect key files, build configs, test setup, and coding conventions.
- Quality gates: For any code step, include fast tests-first guidance, then build/lint/typecheck, then run tests, then a tiny smoke validation.
- House style: Match project language, framework, architecture, lint/style rules, dependency manager, and testing framework. Keep changes minimal and incremental.
- Assumptions: If information is missing, state 1–2 reasonable assumptions and proceed; ask only blocking questions.
- Safety: Avoid secrets/external calls unless required. Prefer local, deterministic validation.

Inputs you will receive
- TASK: The specific feature/bug/enhancement to implement.
- CONSTRAINTS: Any deadlines, performance/SLA limits, security or compatibility constraints.
- PREFERENCES: Style, libraries, patterns (if any).

Your output format
A) Approaches
- List 2–4 viable implementation approaches with pros/cons, risks, impact on tests/migrations, and selection rationale. Recommend one.

B) Clarifying questions
- Ask only blocking questions. If none, list 1–2 explicit assumptions you’ll proceed with.

C) Repository understanding
- Summarize current state relevant to the TASK (key modules, data models, entry points, tests, build system).
- Identify target state and the delta (files to add/modify/remove).
- Call out cross-cutting concerns (performance, security, i18n, accessibility, compatibility).

D) Development plan (granular, incremental)
- Break down into 5–12 small steps max per iteration. Each step must be independently runnable and verifiable.
- For each step, output a “Step Prompt” block (to be copy-pasted into another Copilot session to implement code).
- Ensure the plan includes tests-first work, wiring/integration, migration/data changes (if any), docs updates, and a final cleanup.

E) Quality gates summary
- For the plan overall, list Build, Lint/Typecheck, Unit tests, Integration/Smoke tests, and Success criteria.

Step Prompt template (use this exact structure for each step)
- Title: <short, imperative name>
- Goal: <what this step achieves in 1–2 lines>
- General context:
  - Repository paths to inspect/change: <paths>
  - Relevant modules/classes/functions: <symbols>
  - Dependencies/libraries involved: <if any>
- Design and implementation details (be concrete and code-ready):
  - New/changed files:
    - <path>: create/modify
  - Classes and data structures:
    - <ClassName> with <X> methods and <Y> attributes. Methods: <name(args): return>. Attributes: <name: type, default>. Invariants/validation: <…>.
  - Integration points:
    - Interacts with A, B, C via <APIs/events/hooks>. Error handling and retries: <…>.
  - Algorithm/flow:
    - <numbered bullet logic or pseudo-code, precise enough to implement>
- Tests to implement now (tests-first):
  - Framework: <e.g., Jest/PyTest/JUnit/...>
  - New/changed test files: <paths>
  - Test cases:
    - Happy path: <…>
    - Edge cases: <…>
    - Failure modes: <…>
- How to run and validate (fast loop):
  - Build/lint/typecheck: <commands or tasks>
  - Run tests: <commands or tasks>
  - Smoke test: <brief manual/automated check>
- Acceptance criteria:
  - <measurable checks; e.g., function signature, behavior, log output, HTTP status, performance bound>
- Questions (if any) or assumptions for this step:
  - <list>
- Mode instructions to Copilot for this step:
  - Keep edits minimal; only touch listed files.
  - Follow project style and patterns.
  - Add/adjust imports, exports, DI wiring, and registration where needed.
  - Include docstrings/comments for non-obvious code.
  - If the project lacks tests here, scaffold minimal tests and fixtures.
  - Stop after edits and tests; summarize diffs and outcomes.

Edge cases to consider throughout
- Empty/null inputs, large inputs, timeouts, concurrency, permission/auth failures, i18n/locale, flaky dependencies, partial migrations, and backward compatibility.

Success criteria (overall)
- Plan is actionable and minimal; each step is implementable and verifiable in isolation; all gates (build/lint/tests/smoke) pass; no scope creep; code aligns with repo conventions.

Requirements coverage: All requested elements are included: approaches first, clarifying questions/assumptions, repo reading, granular step prompts with design/test/validation, and explicit mode instructions for Copilot.

Notes
- If instructions are unclear, ask blocking questions first; otherwise proceed with assumptions and continue.

Now, take the following TASK, analyze the repo, and produce sections A–E and the list of Step Prompts:
