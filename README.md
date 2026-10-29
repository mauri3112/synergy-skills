# Synergy Skills

A collection of agent skills we create and use over time for collaborative specification and repeatable task execution in Codex.

## Skills created here

| Skill | Purpose | Version |
| --- | --- | --- |
| [spec-together](skills/spec-together/SKILL.md) | Turn an app or feature idea into a buildable specification through questions, diagrams, and agreement on each manageable part. | 0.1.0 |
| [run-task](skills/run-task/SKILL.md) | Execute or resume a recurring task with a runbook, compact recovery state, and selective learning notes. | 0.1.0 |
| [improve-task](skills/improve-task/SKILL.md) | Update a task runbook from verified evidence, preserving scope and reversible revisions. | 0.1.0 |

### Spec together

The agent proposes coherent work packages, explores one with you, and presents its behavior, diagram, acceptance criteria, and important edge cases. You agree on that part before moving to the next. A final review checks the complete feature and how its smaller parts interact.

The skill keeps a written specification and a short session record so the work can continue across conversations. It covers user stories, limitations, failure and recovery, data and permissions, and directions deliberately deferred from the current scope.

Install it with the [Skills CLI](https://github.com/vercel-labs/skills):

```sh
npx skills add mauri3112/synergy-skills@spec-together -g
```

In Codex, start with:

```text
Use $spec-together to help me specify [app or feature idea].
```

Its instructions are self-contained. The credited influences are Matt Pocock's grilling and grill-with-docs, and Superpowers' brainstorming. Links to the exact source versions appear in the [skill](skills/spec-together/SKILL.md#influences).

### Run task and improve task

Use `run-task` when the next action is doing the recurring task or recovering ongoing work. Use `improve-task` when the next action is changing how future runs should be performed. They work independently: improvement can use existing task evidence even if execution did not use `run-task`.

| Situation | Skill |
| --- | --- |
| Execute a weekly workflow using its established procedure | `run-task` |
| Continue a long review after context loss | `run-task` |
| Turn a verified workaround or recurring failure into a procedure change | `improve-task` |
| Apply a user correction to the reusable task requirements | `improve-task` |
| A routine run succeeded and nothing reusable changed | No improvement pass needed |
| A small one-off request | Neither skill is necessary |

Example prompts:

```text
Use $run-task for this week's research task, following its existing runbook.
Use $run-task to resume the release review from its saved checkpoint.
Use $improve-task to review the last run's failures and update the runbook where the evidence supports a change.
```

V1 uses ordinary local files: one runbook per task family, plus a checkpoint and selective journal per run. The coordinator records meaningful changes and uses the task's existing review. There is no observer, background process, lifecycle-hook installation, or mandatory extra model call. Journals stay outside conversation context until a relevant excerpt is needed.

The proposed efficiency target is below 5% additional learning cost, with a 10% admission allowance for optional learning when usage can be bounded. These are operating targets, not measured savings or hard limits enforced by Markdown instructions. Setup, repeated context input, and deferred maintenance count. Task verification and essential recovery state remain required. Validate quality and cost on comparable real tasks before relying on the targets.

Keep actual task records private. These public packages contain reusable instructions and generic templates only. The execution skill explains local Git exclusion for its default `.task-runbooks/` directory. Improvement preserves a previous runbook revision before changing it. Neither skill installs itself on other machines or edits global skills based on a task-specific lesson.

Install either package with the Skills CLI:

```sh
npx skills add mauri3112/synergy-skills@run-task -g
npx skills add mauri3112/synergy-skills@improve-task -g
```

## Skills adopted from elsewhere

No third-party skills are cataloged yet. When adopting one, record its upstream repository, the skill name, the version or commit used, its license, and any local changes. A researched influence is not automatically an adopted skill.

## Keeping the collection current

- Put reusable skill packages in `skills/<skill-name>/`, each with its own `SKILL.md` and any required resources.
- Update this catalog when a skill is added, changed, adopted, or retired. Record the purpose and version or upstream revision.
- Preserve upstream attribution and license files when third-party content is included. Use links when only tracking an external skill.
- Use Git history to keep track of changes. Installed copies are snapshots; update them deliberately from the repository.

## Layout

```text
skills/
  run-task/
    SKILL.md
    agents/openai.yaml
    references/record-format.md
  improve-task/
    SKILL.md
    agents/openai.yaml
    references/evaluation.md
  spec-together/
    SKILL.md
    agents/openai.yaml
    references/
      completeness-review.md
      specification-structure.md
```
