# Synergy Skills

A collection of agent skills we create and use over time, starting with collaborative app and feature specification in Codex.

## Skills created here

| Skill | Purpose | Version |
| --- | --- | --- |
| [spec-together](skills/spec-together/SKILL.md) | Turn an app or feature idea into a buildable specification through questions, diagrams, and agreement on each manageable part. | 0.1.0 |

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
  spec-together/
    SKILL.md
    agents/openai.yaml
    references/
      completeness-review.md
      specification-structure.md
```
