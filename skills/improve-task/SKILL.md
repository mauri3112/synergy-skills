---
name: improve-task
description: Improve a repeatable task's runbook using evidence from completed or ongoing runs. Use after a recurring failure, verified workaround, user correction, or explicit process review; ordinary execution and recovery belong to run-task.
metadata:
  version: "0.1.0"
---

# Improve task

Make the next execution better with a small, supported procedure change. This skill reviews process knowledge; it does not start a new task run, observer, or background loop. It works independently of `run-task` with equivalent existing evidence.

## Select evidence

Find the task's runbook and the relevant journal entries, outcomes, user corrections, or artifacts. Use their existing location and format. Resolve ambiguity from available context before asking. Read the applicable procedure and bounded evidence excerpts, not entire conversations or all previous runs.

If there is no new reusable evidence, finish with no change. If evidence is missing, identify the gap and retain a candidate; do not invent a lesson or rerun the task just to fill it.

## Check the proposed change

State the condition, observed result, proposed action, evidence, and limits. Separate observation from inferred cause. Check whether the lesson already exists, whether another rule conflicts, and whether it applies beyond this one case. Read [evaluation examples](references/evaluation.md) when generalization, conflicting evidence, or cost is unclear.

Reuse actual task verification and outcomes. A successful workaround supports its observed scope; broader claims need further evidence. User corrections can directly update the task contract within their stated scope. Otherwise keep unverified claims as candidates. Do not promote agent agreement or confident wording as evidence.

## Revise and finish

Change only supported guidance. Preserve acceptance criteria and authorization boundaries. Keep entries conditional and actionable; replace superseded wording rather than accumulating warnings. A task lesson does not authorize changing global skills, configuration, or unrelated runbooks.

Before replacement, preserve the exact pre-edit runbook in existing history or a local revision snapshot. Verify the source has not changed, then save the new revision and a short change record with evidence references. Read back the changed guidance. Leave active runs on their recorded revision unless the correction must apply now; record that transition explicitly.

Report the change, its supporting check, remaining candidates, and any unmeasured benefit. No supported change is a valid result. Do not claim improvement merely because the runbook changed.

## Keep overhead small

No extra agents or model calls solely for reflection. Prefer existing checks and later ordinary runs over dedicated replay. Bound this review to the evidence that could change a decision; stop when there is no supported change.

Target learning overhead below 5% of comparable baseline cost; optional learning has a 10% admission allowance only when usage can be bounded. Charge retrieval, repeated context, generated notes, setup, all agents, and deferred work. A skill cannot enforce exact monetary limits. Without reliable accounting, use bounded in-flow work and report estimates; defer extra evaluation. An explicit user request for deeper evaluation sets that separate scope and budget.

Use `$run-task` when the next action is executing or resuming the actual task. Do not automatically start it after editing the runbook.
