---
name: spec-together
description: "Collaboratively turn app and feature ideas into buildable specifications through focused questions, diagrams rendered in Codex, and agreement on each manageable part. Use for interactive product specification and design, including resuming an existing spec."
metadata:
  version: "0.1.0"
---

# Spec together

Help the user work out what an app or feature should do, establish a shared understanding, and record a specification another builder can use. Lead the organization of the work. Draw out the user's intent, investigate facts, propose alternatives when useful, and make uncertainty visible.

The unit of collaboration is a manageable part of the feature. Question that part, explain and visualize the resulting design, revise it together, and wait for agreement before starting the next part. Finish by checking how all parts work together.

## Start or resume

Use the conversation and available project context before asking anything. Read relevant project instructions, existing specifications, and the code or documentation needed to understand current behavior. Research verifiable facts rather than asking the user to supply them. Distinguish observed behavior, the user's desired behavior, and proposals.

For a new idea, establish the problem, intended users, a concrete example of success, current constraints, and what belongs in this effort. Ask only for missing information that changes the design. Do not begin with a questionnaire covering the entire project.

For an existing effort, read its saved specification and session state. Identify what is agreed, what has changed, and the next unresolved question. Continue there instead of repeating the interview. Reconfirm earlier decisions only when new evidence or a requested change affects them.

## Shape the work

Propose a small map of coherent work packages and a sensible order. A package should describe behavior the user can discuss and agree in one focused conversation. Prefer an end-to-end user capability over separate frontend, backend, and database tasks. Shared foundations can be packages when they genuinely need a separate decision.

Give packages stable IDs such as P1 and P2. For each, state its purpose, boundary, dependencies, and status. Use `proposed`, `active`, `agreed`, `needs revision`, or `deferred`. Break apart packages that become too broad; do not force a fixed count. Put prerequisite product decisions first and explore high-impact uncertainty early. The package map is a specification outline, not a coding task list.

Show a rendered overview diagram connecting the packages and their dependencies. State which important choices are still proposals. Ask whether the map and starting point match the user's intent, then wait. On agreement, begin the first package. If the user has already clearly agreed a map or starting point, use that agreement.

## Work through one package

### 1. Discover its behavior

Name the active package and its purpose briefly. Ask one primary question at a time by default, using concrete situations and the user's vocabulary. Follow the dependencies between decisions: settle a prerequisite before asking questions that assume its answer. Batch a few independent questions within this package only when the user prefers that pace.

Use open questions to understand intent. When there is a real choice, offer a few meaningful options with their consequences and a reasoned recommendation. Avoid steering every answer toward your default. Challenge contradictions and weak assumptions respectfully. Reflect back your understanding at useful points rather than after every answer.

Ask which design choices the user wants to make and which they want to delegate when that distinction matters. Treat an explicit delegation as authority to choose within its scope, state the choice, and record that it was delegated. Do not turn silence, a skipped question, an agent suggestion, or a partial answer into agreement.

Maintain a clear distinction between agreed decisions, agent proposals, open questions, and deferred possibilities. Investigate technical unknowns when available evidence can resolve them. If something needs a prototype or external validation, describe the uncertainty and the smallest useful investigation; do not present a guess as an established constraint.

### 2. Test the design before presenting it

Read [Completeness review](references/completeness-review.md) when preparing a package checkpoint. Think through relevant user stories, alternative paths, failure and recovery, permissions, data and state, limitations, and interactions with other packages. Identify contradictions, missing behavior, and the decisions with the greatest consequences.

Use this review to find the next useful question. Do not read the checklist to the user or ask irrelevant questions to fill a template. Put proposed additions and future directions outside the agreed scope until the user chooses them. Distinguish necessary behavior for this release from possible later improvements.

### 3. Explain, visualize, and agree

When the package is understood well enough to review, present a concise checkpoint:

- What this part enables, for whom, and its boundary.
- The behavior and important decisions, including relevant edge cases and limitations.
- Concrete acceptance examples, including meaningful failure or recovery behavior.
- A rendered diagram of the part and its connections to the rest of the feature.
- Any remaining choice that prevents agreement.

Choose the diagram for the question: a user flow for a journey, state diagram for lifecycle behavior, sequence diagram for interactions, or component/data diagram for responsibilities. Use clear labels and keep the current package identifiable within the bigger picture.

Ask whether this checkpoint captures the intended behavior and is ready to agree. Stop and wait. A clear acceptance of this checkpoint marks the package agreed; general enthusiasm about one detail does not. If the user requests a material change, update the design and visual before agreeing it. Do not ask for confirmation of every sentence or repeat a checkpoint already accepted.

Write the agreed decisions and update the overview and session state. Then continue to the next package in the agreed order. A later change may reopen only the affected packages and their dependents. Explain the impact and preserve the previous decision until its replacement is agreed.

## Make diagrams useful in Codex

Render diagrams in the conversation at the initial map, each package checkpoint, and final whole-feature review. Do not substitute a link to a diagram file or show only prose describing a diagram.

For static labeled structures and flows, use a normal fenced `mermaid` block so Codex can display it. Quote node labels, keep IDs stable, and split dense diagrams into an overview and focused detail. Include a brief plain-language explanation of what the visual means. Keep the diagram and written requirements consistent.

When choosing between interface layouts or exploring changing states would benefit from interaction, use the available in-conversation visualization capability and its current instructions. Keep a textual or Mermaid representation in the saved spec so understanding does not depend on a transient interactive view. If rendering is unavailable, explain the limitation and provide a readable fallback; never claim to have displayed a visual that was not produced.

Maintain two levels of understanding:

- A feature overview showing the smaller capabilities and their relationships.
- Enough detail for each package to show its internal behavior, boundaries, and connections.

Show architecture only at the level needed to make the behavior buildable. Keep product behavior separate from implementation choices still delegated to the builder. A diagram containing only screens or only infrastructure is insufficient when the important interactions are missing.

## Keep a durable specification

Follow the project's existing specification format and location. Otherwise use `docs/specs/<feature-slug>/spec.md` plus a short `session.md` in a software project, or a feature folder in the task's output location for a projectless chat. Create local specification documents as part of the work; publishing or changing external trackers requires authorization covering that action.

Use [Specification structure](references/specification-structure.md) when first creating the documents or assembling the handoff. Scale the structure to the feature. Keep one readable spec for a small feature; split package details into linked files only when that improves navigation. Maintain one canonical home for each decision rather than several contradictory copies.

Update the draft as the conversation progresses and after each checkpoint. Keep proposals visibly unapproved. Record stable requirement and acceptance IDs where they help trace behavior across packages. Preserve the reason for consequential choices, relevant evidence, limitations, and deliberately excluded alternatives.

The session record should make a fresh conversation resumable: current phase and package, package statuses, the last agreed checkpoint, the pending question or review awaiting an answer, and the next step. Record outstanding research and affected dependencies. Keep this compact; it is not a transcript. When resuming, verify it against the spec and later user messages rather than treating stale state as fresh approval.

## Review the whole feature

After the packages are agreed, run the feature-wide pass in [Completeness review](references/completeness-review.md). Walk through complete user journeys that cross package boundaries, including failures. Check ownership of shared data and state, permissions, interface assumptions, conflicting rules, and recovery across components. Resolve important integration choices with the user and reopen affected packages when needed.

Present the integrated specification with:

- A readable account of the feature, its users, scope, and intended outcomes.
- The high-level feature map and a system overview explaining how its smaller parts connect.
- The agreed package details, stories, requirements, and observable acceptance criteria.
- Relevant data, state, interface, and nonfunctional constraints needed to build it.
- Limitations, deferred directions, open questions, and verification needs.

Ask for agreement on the integrated specification and wait. Do not label it complete while behavior or a dependency essential to the agreed release remains unresolved. If the user ends discovery early, produce an honest draft with the missing decisions identified. Do not claim to have exhausted every possible edge case.

On final agreement, record what was approved, link the canonical documents, and explain any material remaining limits. The result is an agreed specification and handoff. Beginning implementation is a separate task unless the user's existing instruction already includes it; package approval alone is not a request to build.

## Influences

Original instructions for this collaborative workflow, informed by Matt Pocock's [grilling](https://github.com/mattpocock/skills/blob/49dd158d1076134a641b33efb035946536778336/skills/productivity/grilling/SKILL.md) and [grill-with-docs](https://github.com/mattpocock/skills/blob/49dd158d1076134a641b33efb035946536778336/skills/engineering/grill-with-docs/SKILL.md), and Superpowers' [brainstorming](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/brainstorming/SKILL.md). This skill is self-contained and does not require those packages.
