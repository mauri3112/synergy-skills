# Task records

Read this when setting up records or repairing an ambiguous layout. Keep an established equivalent format. The default needs three Markdown files, not a database or logging service.

## Location and ownership

Use a known task-private location. Otherwise use `<workspace>/.task-runbooks/<task-slug>/`. In a Git workspace, exclude `.task-runbooks/` locally before writing task data; use the repository's existing exclusion or `.git/info/exclude`, resolving the Git directory through Git for worktrees. If exclusion cannot be established or this location is otherwise shared, choose a private location outside the repository and report it. Never stage personal records into a public skills collection.

Give the task family a stable identity. Within its directory, use `runs/<run-id>/state.md` and `runs/<run-id>/journal.md`. Use an unambiguous run identifier and locate the intended active run from recorded context; do not silently resume a different run merely because its file is newest. One coordinator writes shared records. Workers return findings through the task's normal result channel, or use separate files if that is already the project convention.

Update related files in one tool operation where practical. Replace the checkpoint atomically using a same-directory temporary file and rename when supported. Preserve prior journal entries; append only meaningful new evidence. A failed write is not a saved checkpoint. Ordinary file tools suffice for v1.

## Reusable runbook

`runbook.md` describes the task family. Establish it from user instructions and verified existing procedure; label assumptions and open choices. Do not require a separate interview if the task is already clear.

```markdown
# Task name
Revision: 1

## Goal and acceptance
What counts as a useful accepted result, scope, and stopping conditions.

## Procedure
The few steps, evidence sources, and checks that change how this task is done.

## Conditional lessons
When [condition], do [action], verified by [check]. Evidence: [reference].
```

Use only relevant headings. Do not pad the file with generic instructions or empty sections. A first run can begin with a minimal goal, procedure, and acceptance criteria. Keep detailed evidence outside the runbook.

## Recovery state

`runs/<run-id>/state.md` is a replaceable checkpoint, not a transcript.

```markdown
# Current run
Run: [id]; status: active | complete | needs-input | stopped
Runbook revision: [revision or snapshot reference]
Goal and active constraints: [brief, including consequential user corrections]
Completed: [verified work and artifact references]
Open: [unresolved findings, unknown action outcomes, and delegates if any]
Next: [specific next action and its acceptance check]
Latest journal entry: [id or marker, if any]
Outcome: [at stopping; acceptance result and unfinished work]
Usage: [available measurements or estimates, otherwise unknown]
```

Drop inapplicable fields. Preserve required detail in referenced artifacts when a compact checkpoint cannot contain it. On recovery, inspect actual state before retrying actions with external effects. An interrupted call can have succeeded without a recorded receipt. If its outcome cannot be reconciled, treat it as unknown rather than repeat it blindly.

Keep a run on its recorded runbook revision. If the canonical procedure changes, read the preserved revision or reconcile the relevant difference explicitly; do not pretend a new revision was the one originally used. Current user corrections take precedence.

## Selective journal

`runs/<run-id>/journal.md` records only events worth recovering or learning from.

```markdown
### E1: short event
Observed: [result and evidence reference]
Decision: [action and the reason it was chosen]
Learning: candidate | verified for [scope] | rejected | superseded
```

Include a date, agent, source, or follow-up reference only when it resolves ambiguity. Distinguish an observed result from a suspected explanation. Do not paste credentials, unnecessary personal details, raw transcripts, or whole tool outputs. If nothing reusable or consequential happened, no journal entry is needed.

At completion, record the outcome in state rather than creating another report solely for this skill. A later `improve-task` review can use these records, but does not need every file loaded.

## Overhead accounting

Measure comparable cases with the same acceptance criteria. Include setup and later maintenance in cumulative cost; separately report recurring overhead to show whether the design is worthwhile over time. Count generated notes and repeated inclusion of learning context across requests, not just the bytes written to files. Use model-specific and cached-input usage where available; token totals alone are a proxy for monetary cost. Do not manufacture measurements that the runtime does not expose.

The 5% target and 10% optional-learning allowance do not cap necessary task execution or prove total savings. If a bound cannot be established, do not add separate model calls for learning. Record the useful evidence cheaply and defer processing.
