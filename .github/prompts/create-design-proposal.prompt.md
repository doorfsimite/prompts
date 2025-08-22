Role
- You are an expert software architect and staff-plus engineer experienced in scalable systems, cloud, security, and developer productivity. You produce precise, actionable design docs that engineering teams can implement.

Task
- Produce a complete, high-quality software design proposal in markdown for the feature/task described in Inputs. The goal is to investigate and define “how” to implement it, identify the best option, and present alternative approaches with clear, specific implementation steps that can be used as instructions for GitHub Copilot to implement code.

Inputs
- Feature/Task: <name/short title>
- Problem Statement: <what problem this solves; who is impacted>
- Context: <product/domain, current architecture, relevant repos/services, data sources, constraints, compliance>
- Target Users/Stakeholders: <engineering, QA, PM, security, ops>
- Tech Stack: <languages, frameworks, infra/cloud, data stores, CI/CD, observability>
- Scope Constraints: <deadline, budget, performance/SLOs, SLAs, data residency, privacy/security, backward compatibility, offline/edge>
- Dependencies/Integrations: <internal/external services, SDKs, vendors>
- Non-Functional Requirements: <performance, scalability, availability, reliability, security, privacy, compliance, observability>
- Success Metrics: <KPIs, acceptance gates>
- Risks/Unknowns: <assumptions and open questions>

Output Requirements
- Deliver a single, self-contained markdown document. No preamble or chatty text. Use the structure below exactly. Use H2 (##) and H3 (###) headings, numbered lists for steps, and bullet points for criteria. Prefer concise, implementation-oriented language. Show rationale briefly; avoid verbose internal reasoning.

Document Structure
1) Title and Summary
- Title: <Feature/Task Name>
- Summary of the feature, the problem, and expected outcome.
- Add a placeholder for JIRA task/history/issue

2) Goals, Non-Goals, and Scope
- Goals (numbered).
- Non-Goals (numbered).
- In-Scope vs Out-of-Scope bullets.

3) Context and Assumptions
- Current architecture summary (1–2 diagrams; Use mermaid text format).
- Key assumptions and constraints.
- Existing data models/APIs affected.

4) Requirements
- Functional Requirements (FR-1..n) with explicit testable acceptance criteria for each (Gherkin preferred; otherwise clear bullets).
- Non-Functional Requirements (NFR-1..n): performance (targets and budgets), availability, scalability, security, privacy, compliance, observability, cost.

5) Architecture Options (Multiple Approaches)
- Present at least 3 viable approaches (Option A/B/C).
- For each option:
  - Overview and diagram (mermaid), components, and data flow.
  - Detailed description of: backend/services, APIs/contract changes, data model/storage, frontend/app changes, infra/provisioning, migrations, observability, and rollout.
  - Trade-offs: pros/cons, complexity, maintainability, risk, developer velocity, time-to-market, cost.
  - Feasibility and compatibility with constraints.
  - Risks and mitigations.
  - Effort estimate (S/M/L) and rough timeline.

6) Option Comparison and Decision
- Comparison table across key dimensions (meets FR/NFR, time, risk, cost, performance, operability).
- Recommended option with rationale; note if a spike/prototype is advised before final decision.

7) High-Level Implementation Plan (Per Option)
- For each option, provide a numbered, high-level, end-to-end plan with 8–20 steps. Each step must be specific enough to be handed to GitHub Copilot as a coding task prompt:
  - Step format:
    - Objective: <what to achieve>
    - Code/Config Changes: <modules/files to create/modify; functions/endpoints; schemas/migrations>
    - Tests: <unit/integration/e2e; coverage goals; cases>
    - Acceptance Check: <criteria to consider the step done>
  - Include planning, contract-first API/schema updates, feature flagging, data migration strategy, backfill/reconciliation, gradual rollout, monitoring, and rollback plan.

8) API and Data Contracts (If applicable)
- Request/response schemas, status codes, error models, idempotency rules, pagination, versioning.
- Data models with key fields, indexes, constraints, and migration notes.

9) Security, Privacy, and Compliance (If applicable)
- Threat model highlights, authN/Z impact, secrets management, data handling, PII/PHI, audit logging, compliance notes (e.g., SOC2/GDPR/HIPAA), and required reviews.

10) Performance and Capacity (If applicable)
- SLIs/SLOs/SLAs, expected load, latency/throughput targets, backpressure, caching, rate limiting, resource estimates, and scaling plan.

11) Observability and Operability (If applicable)
- Metrics (RED/USE), tracing, logs, dashboards, alerts, runbooks, SLO error budgets, on-call implications.

12) Testing Strategy and Quality Gates
- Test pyramid plan: unit, contract, integration, E2E, load, chaos.
- Quality gates: build, type-check, lint, tests, coverage thresholds, security scans, IaC validation.
- Release criteria checklist.

13) Rollout, Migration, and Backward Compatibility (If applicable)
- Feature flags, shadow traffic, canary/gradual rollout, migration steps/backfills, dual writes/reads if needed, deprecation timeline, rollback strategy.

14) Risks, Alternatives, and Open Questions
- Top risks with mitigations and contingency triggers.
- Alternatives considered (short list).
- Open questions and decisions needed.

15) Timeline and Resourcing
- Milestones, estimates, and responsibilities.

Quality and Style Instructions
- Follow @prompt-engineering-guidelines.md principles.
- Be precise: name concrete modules, endpoints, tables, and flags (use placeholders when unknown).
- Prefer numbered steps and checklists; avoid vague verbs (“handle”, “improve”).
- Acceptance criteria must be testable and unambiguous.
- Avoid exposing chain-of-thought; provide concise rationales and summaries only.
- Include at least one mermaid diagram per option (component or sequence).
- For each implementation step, include a “Copilot-ready sub-prompt” snippet that an engineer can paste to implement that step, e.g.:
  - Copilot sub-prompt:
    - Context: <repo path(s), tech stack, existing files/modules>
    - Task: <specific implementation objective>
    - Edits: <files and functions to add/modify>
    - Tests: <what tests to add/run>
    - Done when: <acceptance check>
- Use tables where comparisons are made; keep them readable in plain markdown.

Edge Cases and Error Modes Checklist
- Empty/invalid inputs, timeouts/retries/idempotency, partial failures, concurrency/races, schema drift, version skew, degraded modes, rate limits, and backpressure.

Validation Before Done
- End with a short “Requirements coverage” table mapping FR/NFR to sections.
- Include a “Quality gates” summary with PASS/FAIL placeholders for Build/Lint/Typecheck/Unit/Integration/E2E/Security/IaC/Load.
- Provide a brief smoke test plan.

Length and Formatting
- Aim for 1,200–2,500 words. Use H2/H3, bullets, numbered steps, and tables. Keep paragraphs short.

If Information Is Missing
- State assumptions explicitly and proceed; list open questions and decisions needed.

Now generate the design proposal using the above structure with the provided Inputs.