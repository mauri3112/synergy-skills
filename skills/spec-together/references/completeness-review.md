# Completeness review

Read this when preparing a package checkpoint and during the final integration review. Think through the relevant cases; bring the user only the choices and gaps that matter. These are prompts for analysis, not mandatory features or an interview script.

## Within a package

**Intent and scope.** What problem does this solve? Who benefits, who can be affected, and what observable outcome counts as success? Is the package coherent? What belongs now, later, or outside this feature? Could a simpler design satisfy the same need?

**Stories and journeys.** Consider the first use, ordinary use, repeated use, different relevant roles, cancellation, and returning after an interruption. Cover less common but consequential paths. A story should identify the actor, need, and reason; acceptance criteria should make its behavior observable.

**States and transitions.** Which states actually exist, who may change them, and which transitions are allowed? Consider empty, loading, partial, stale, invalid, unavailable, and completed states where applicable. What happens after refresh, navigation away, deletion, or an interrupted operation? Resolve ambiguous ownership of state.

**Failure and recovery.** Consider bad input, missing data, timeouts, partial success, lost connectivity, dependency failure, and an operation that succeeds while its acknowledgement is lost. Can a user retry, cancel, undo, recover, or understand what happened? Specify the user-visible outcome and preservation of work rather than merely saying "handle errors."

**Ordering and concurrency.** Where relevant, reason about double actions, retries, simultaneous edits, multiple devices, out-of-order events, duplicates, and operations racing with deletion or permission changes. Identify what must remain true and who resolves a conflict. Do not invent distributed infrastructure for a simple local feature.

**Data and access.** What is created, read, changed, retained, shared, exported, or removed? Who owns it and who may see or change it? Which identities or permissions matter? Are sensitive values involved? Consider relevant misuse and data exposure. Include consent, retention, or policy questions only where they affect this feature; identify external verification needs instead of inventing legal requirements.

**Dependencies and boundaries.** What does the package expect from other packages, existing software, or external services? What does it provide? Where can its assumptions fail? State the relevant inputs, outputs, invariants, failure behavior, and compatibility expectations. Verify important capability claims against available evidence.

**Practical constraints.** Explore relevant accessibility, device/platform, localization, time zones, scale, performance, reliability, operating cost, and offline constraints. Use measurable targets when they affect acceptance, or record them as unresolved. Avoid invented numbers and blanket enterprise requirements.

**Existing users and operations.** For a change to an existing product, consider current behavior, existing data, compatibility, migration, introduction of the change, rollback, support, and how a failure could be noticed. Include only the operational detail the feature actually needs.

**Alternatives and directions.** Surface a worthwhile alternative or extension when it changes a meaningful tradeoff. Record the user's chosen boundary and reason. An attractive possibility is not automatically part of the release.

## Concrete acceptance examples

For each important rule, describe conditions, an action or event, and the observable result. Include normal behavior and a meaningful failure, boundary, or recovery case. Given/when/then is useful when it improves precision, not a compulsory writing style.

Check limits immediately below, at, and above a boundary when applicable. Avoid "works correctly," "fast," and "intuitive" without defining the observable expectation. A requirement without an acceptance example may still be ambiguous; a testable technical detail may still fail to capture the user's actual goal.

## Across the full feature

Walk through realistic journeys spanning the packages, including at least one consequential failure or recovery path. Ask:

- Do the packages together deliver the outcome, or is there a gap between them?
- Does each shared piece of data or state have an agreed owner and lifecycle?
- Do names, identifiers, permissions, event ordering, and interface expectations agree?
- Can one package report success while another leaves the user in an inconsistent state?
- Are cross-package rules owned explicitly rather than assumed by both sides?
- Does each important user story lead to agreed requirements and observable acceptance behavior?
- Do the diagrams show the same boundaries, dependencies, and flows as the prose?
- Have changed decisions been carried into affected packages and visuals?
- Are remaining unknowns genuine non-blockers, or do they prevent someone from building the intended behavior?
- Are deferred directions clearly separate from the agreed release?

Resolve significant gaps through the normal question, visualization, and agreement loop. Do not silently rewrite approved behavior during final assembly.
