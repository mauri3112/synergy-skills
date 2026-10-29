# Evaluate a runbook change

Read only when the scope of a lesson or its validation is unclear. Use the actual task's acceptance criteria and available evidence. This is not a required additional review pass.

## Minimal change record

Keep the record beside the task's existing journal, or append it to the relevant run journal. Include only enough to explain and reverse the change:

```markdown
Change: [old revision] -> [new revision]
Condition and action: [when the revised instruction applies]
Evidence and check: [artifact or event references; what was verified]
Limits: [unverified generalization or known counterexample, if material]
Previous revision: [history or private snapshot reference]
```

For the default three-file format, preserve the old runbook as `revisions/<old-revision>.md` before replacing `runbook.md`. Use existing version history when it already provides reliable recovery. Do not overwrite an existing revision snapshot. Resolve concurrent changes before writing, and keep the snapshot in the same private task store.

## Examples of decisions

**A single timeout.** A source timed out once; an alternative source answered. Record the failure and successful fallback. This does not establish that the original source should never be used. A conditional fallback can be justified if it preserves the task's evidence requirements.

**A successful workaround.** The existing process failed on an input format, and a different transformation produced an output that passed the actual acceptance check. Add the workaround for that format with its check and evidence. Broader format support remains unverified.

**A user correction.** The user changes an eligibility requirement for this task family. Update the requirement within that scope without waiting for repeated failures. Preserve its source and reconcile an active run if affected. Do not apply it to unrelated tasks.

**Conflicting outcomes.** A shortcut reduced time in one run but omitted a required check in another. Keep the acceptance check. Narrow or reject the shortcut instead of optimizing completion time alone.

**Repeated rediscovery.** Multiple journal entries describe the same verified issue. Consolidate one conditional runbook instruction with evidence references. Do not add a separate warning for each repetition.

**No new evidence or no budget.** Leave the runbook unchanged. Retain an already recorded candidate or briefly identify the missing evidence. Do not add model calls, replay a full task, or rewrite the runbook for cosmetic consistency.

## Validation and claims

Prefer checks already performed during the task. Use the next ordinary run to collect further evidence when a proposed change needs broader validation. Dedicated replay or independent evaluation requires scope and budget covering that work; this skill does not request subagents.

Report verified correctness within its observed scope separately from expected efficiency benefits. Compare accepted quality, repeat failures, user corrections, and model cost or elapsed time where available. Similarity of cases matters. Fewer review rounds or agreement between agents is not itself evidence of better task performance.

If evidence later contradicts a promoted lesson, narrow, supersede, or revert it. Preserve why the procedure changed without keeping superseded advice in active instructions.
