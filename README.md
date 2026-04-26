# code-design-review-skills

AI mentoring and philosophy-review skills for simplicity-first software design.

This repository gives a dedicated home to two companion skills:

- `code-mentor` — explain the intended approach before coding, then review whether the finished implementation stayed simple, matched the plan, and avoided unnecessary code.
- `cs-philosophy-review` — apply deeper programming judgment after or around implementation: simplicity, restraint, deletion, abstraction cost, and clarity over cleverness.

## Why this repo exists

These skills started life inside a broader shared skills repository, but they serve a distinct purpose: they are not framework skills or language skills. They are **thinking skills** for implementation discipline.

They are meant to slow the agent down just enough to ask the right questions:

- What is the intended design?
- Is new code necessary at all?
- Is this the simplest solution?
- Did we add abstraction that does not earn its cost?
- If the implementation changed, why?

In other words, they provide a mentoring and philosophical review layer around coding work, not just task execution.

## The two skills

### `code-mentor`

`code-mentor` is the practical pre/post implementation guide.

Before coding, it asks the agent to:

1. restate the problem,
2. ask whether code is needed,
3. name the intended pattern or approach,
4. explain it briefly,
5. justify why it is simpler than obvious alternatives.

After coding, it asks the agent to:

1. summarize what changed,
2. check whether the implementation followed the plan,
3. explain deviations,
4. describe tradeoffs and pitfalls,
5. ask again whether this is the simplest solution.

### `cs-philosophy-review`

`cs-philosophy-review` is the deeper judgment pass.

It reviews a design or implementation through questions like:

- Is this the simplest solution?
- Should some code be deleted instead of added?
- Is the abstraction earning its cost?
- Did we generalize too early?
- Would plainer control flow or data shape be better?
- Is the code easier to explain than the obvious alternative?

This is where programming taste, restraint, and durable engineering wisdom matter.

## How we wired these into our process

These skills are not standalone curiosities. They are wired into the working system in four places.

### 1. Shared policy baseline

In `dknauss/.github`, we added two non-overridable policy blocks:

- `policies/design-intent-review.md`
- `policies/simplicity-first.md`

Those policies make the baseline behavior mandatory across the governed repos:

- explain intended design before substantial code changes,
- explain deviations after implementation,
- always ask whether less code or no code is the better answer.

### 2. Shared skill distribution

Operational copies of the two skills are mirrored into the shared skill system so they can be consumed by agents in practice:

- `dknauss/agent-skills/skills/code-mentor/SKILL.md`
- `dknauss/agent-skills/skills/cs-philosophy-review/SKILL.md`

That keeps them available alongside the broader workspace skillpack.

### 3. Generated agent instructions

The workspace `AGENTS.md` is generated from the skill inventory plus non-overridable governance policies.

That means these skills are discoverable in the shared instructions, and the baseline simplicity/design-review rules are visible even when a specific skill is not explicitly invoked.

### 4. Repo-level guidance and validation

For governed repositories, the same behavioral layer is reflected in repo-facing instructions:

- generated or validated `CLAUDE.md` files,
- default policy inheritance from `.github/repo-configs/_defaults.yml`,
- policy validation in `.github/scripts/validate-policies.mjs`.

In practice, that means the mentor mindset exists at both levels:

- **policy level** — mandatory baseline behavior,
- **skill level** — richer workflow when explicitly invoked.

## Operating model

Right now, this repo is the focused home for the skills and their rationale.

The active runtime copies are mirrored into the broader governance/skill distribution system because that is how the current workspace installs and advertises skills for Claude, Codex, Cursor, and repo-local `.github/skills` consumers.

The practical edit flow is:

1. refine the skill here,
2. sync the operational copy into `agent-skills`,
3. regenerate shared `AGENTS.md`,
4. revalidate governed repositories.

## Design stance

The core stance of this repo is simple:

- prefer clarity to cleverness,
- prefer fewer moving parts,
- prefer deletion over ornamental abstraction,
- treat no code as a serious candidate,
- explain design intent before code makes the explanation harder.

That is the common thread between both skills.

## Repository contents

- `skills/code-mentor/SKILL.md`
- `skills/cs-philosophy-review/SKILL.md`

## License

MIT
