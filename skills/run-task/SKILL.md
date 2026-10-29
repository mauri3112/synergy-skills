---
name: run-task
description: Execute or resume a repeatable task using its runbook, compact recovery state, and selective learning notes. Use for recurring workflows or long task loops that must survive context loss; skip small one-off requests.
metadata:
  version: "0.1.0"
---

# Run task

Complete the task and preserve useful recovery state. Reuse its verification and stopping criteria. No observer, background process, or extra agent is required.

## Start or resume

Find existing task records. Read applicable runbook guidance and the checkpoint, not the full journal. For a new task family, read [record format](references/record-format.md), create only needed records, and record their location once.

Recover the goal, constraints, runbook revision, progress, open findings, and next action. Verify artifacts, pending external actions, and delegates before continuing. A checkpoint proves neither success nor permission to retry. Follow later user corrections.

## Execute and checkpoint

Work normally. Delegate only when useful and authorized; give workers relevant instructions and request evidence and useful lessons in their ordinary result. The coordinator owns shared records.

Save state after meaningful progress, consequential decisions, or handoffs, including the next step and evidence pointers. Do not wait for compaction. Batch state and journal writes where practical.

Journal useful failures, verified workarounds, corrections, changed constraints, and consequential decisions with reasons. Aim for 50–100 tokens per event and 200–300 per checkpoint. Link evidence; do not copy logs. Routine success needs no entry. Mark uncertain lessons as candidates.

Stop at acceptance, exhausted budget, stalled progress, or a missing prerequisite. Save the outcome and unfinished work. Do not extend the task for a retrospective.

## Keep overhead small

Aim for 500–1,000 added context tokens including these instructions, relevant lessons, and checkpoint. Preserve essential constraints. Skip this machinery when overhead outweighs value.

Target below 5% learning overhead against comparable baseline cost; admit optional learning within 10% only when usage can be bounded. Count repeated context, all agents, setup, and deferred maintenance. These are targets, not enforced cost guarantees. Otherwise add no learning-only model calls.

Keep history on disk; retrieve bounded excerpts as needed. No per-tool reflection or learning-only reviewer. Defer lesson processing before sacrificing essential recovery state.

Use `$improve-task` for evidence-backed procedure changes or a requested retrospective. Ordinary runs can finish with unprocessed candidates; improvement is not mandatory.
