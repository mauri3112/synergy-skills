# Specification structure

Use this when creating the draft and assembling the final specification. Adapt the headings and detail to the project; this is a content guide, not a form the user must fill out. Prefer existing project conventions.

## Canonical specification

Include the content a builder needs without the original conversation:

1. **Purpose and status.** The feature, intended users, problem, concrete outcomes, and current review status. State which parts are agreed and which remain proposals.
2. **Scope and constraints.** The agreed release, non-goals, relevant existing behavior, constraints, and choices explicitly delegated to the builder. List deferred directions separately.
3. **Overview.** A rendered feature hierarchy or capability map, plus an interaction/dependency overview showing how the parts connect and the boundary with existing or external systems. One diagram may cover both when clear.
4. **Package index.** Stable ID, purpose, dependencies, status, and a link or heading for each package. Do not label coding tasks as product capabilities.
5. **Package specifications.** The package content below, inline or in linked files.
6. **Shared behavior.** Cross-package journeys, common data and state ownership, access rules, interfaces, invariants, and relevant nonfunctional expectations. Place each shared rule here once and reference it from packages.
7. **Decisions and limits.** Consequential decisions with reasons, evidence that constrains the design, known limitations, and alternatives deliberately set aside. Distinguish user agreement from delegated choices and agent proposals.
8. **Acceptance and handoff.** Feature-wide acceptance scenarios, integration checks, open questions and their impact, remaining validation needs, and the recorded final agreement when it occurs.

An agreed specification does not prove that implementation, user testing, or external validation has occurred. Keep these statuses separate.

## Package content

Include relevant content at enough detail to avoid a builder guessing important behavior:

- ID, name, purpose, boundary, dependencies, and agreement status.
- Actors and user stories tied to concrete needs.
- Normal and alternative journeys, including relevant UI states and interactions.
- Behavioral requirements and invariants, with stable IDs when useful.
- Important data, state transitions, permissions, and interface expectations.
- Edge cases, failure and recovery behavior, limitations, and chosen tradeoffs.
- Observable acceptance criteria and representative scenarios.
- A focused diagram, with the package's connections to the whole feature visible.
- Open questions, deferred possibilities, and the scope of the user's agreement.

Technical precision is warranted when it resolves a real ambiguity, for example a permission matrix, state machine, or interface contract. Do not fabricate endpoints, schemas, architectures, timing targets, or implementation paths merely to make a document look detailed. Explicitly leave delegated implementation choices to the builder.

Keep diagram labels, package IDs, and requirement names consistent. Split a diagram when it stops being readable. Distinguish a hierarchy that means "is part of" from arrows that mean "depends on," "sends data to," or "happens next."

## Session record

Keep a short `session.md` beside the specification. Use these fields or their clear equivalents:

| Field | What to preserve |
| --- | --- |
| Canonical spec | The relative path to the specification |
| Current phase | Framing, package mapping, package discovery/review, integration, or final review |
| Active package | Stable ID and name, if any |
| Package statuses | Proposed, active, agreed, needs revision, or deferred |
| Last agreement | The specific checkpoint and scope accepted by the user |
| Awaiting answer | The actual question or review the user still needs to answer |
| Open work | Unresolved choices, pending fact-finding, and affected packages |
| Next step | What to do when the answer or evidence arrives |

Update after meaningful decisions and checkpoints. Do not invent an agreement date or reset an unanswered review merely because a session resumed.
