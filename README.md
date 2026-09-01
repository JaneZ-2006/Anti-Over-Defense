# Anti Over-Defense

`anti-over-defense` is an Agent Skill for Codex. It helps Codex deliver requested software changes directly instead of expanding a focused task into unnecessary infrastructure, abstractions, approval processes, or validation systems.

The skill instructs Codex to:

- Modify existing code and reuse the project's current structure, interfaces, and commands.
- Add only the code and files required by the current request.
- Avoid building frameworks, policy systems, approval flows, validation gates, or fallback paths for hypothetical risks.
- Continue working through unrelated test failures, optional tooling gaps, and minor internal implementation choices.
- Verify the result with the project's existing relevant tests, build commands, or examples.
- Stop expanding the solution and deliver once the requested functionality is complete and directly relevant checks pass.

These rules apply to behavior, not terminology. Renaming a validation gate to a "readiness check" or an audit system to "run history" does not bypass the skill.

## When to use it

Use this skill for:

- Implementing features.
- Fixing bugs.
- Completing unfinished project functionality.
- Performing refactoring explicitly requested by the user.
- Modifying existing applications, services, tools, or libraries.
- Completing large software development tasks.

Do not use it for explicitly requested security reviews, security hardening, compliance work, or dedicated testing projects.

The skill does not bypass Codex permissions, repository instructions, or user authorization. It does not allow Codex to hide real errors, fabricate test results, or ignore concrete data-loss risks.

## Install in Codex

Codex discovers local skills from `.agents/skills` directories and supports symlinked skill folders.

### Install for the current user

A user-level installation makes the skill available in every project on the current machine. Run the following commands from this repository's root directory:

```bash
mkdir -p "$HOME/.agents/skills"
ln -s "$(pwd)/anti-over-defense" "$HOME/.agents/skills/anti-over-defense"
```

If the destination already exists, inspect it before replacing it to avoid removing a version you still need.

### Install in one repository

A repository-level installation makes the skill available only within that repository. Run the following commands from the target repository's root directory:

```bash
mkdir -p .agents/skills
cp -R /path/to/Anti-over-defense/anti-over-defense .agents/skills/anti-over-defense
```

Replace `/path/to/Anti-over-defense` with the actual path to this project. Teams can commit `.agents/skills/anti-over-defense` so everyone using Codex in that repository shares the same instructions.

Codex normally detects new and updated skills automatically. Restart Codex if the skill does not appear.

## Use the skill

In Codex CLI or the IDE extension, enter `/skills` and confirm that `anti-over-defense` appears in the skill list.

Mention `$anti-over-defense` in a prompt to invoke it explicitly:

```text
Use $anti-over-defense to implement profile editing for signed-in users and run the project's existing relevant tests.
```

Codex can also invoke the skill automatically when a development task matches the description in `SKILL.md`:

```text
Fix the issue where changing pages in the order list clears the current filters. Modify the existing implementation and run the relevant tests.
```

For large tasks where you want to make the implementation boundary explicit, invoke the skill directly:

```text
Use $anti-over-defense to complete this project. Follow the existing structure, implement only the requested functionality, and verify it with the existing build and test commands.
```

## How it works

After activation, the skill directs Codex to:

1. Identify the concrete result requested by the user.
2. Read the code and repository instructions directly related to that result.
3. Implement the functionality using the project's existing approach.
4. Run existing directly relevant tests, build commands, or examples.
5. Fix problems caused by the current changes.
6. Deliver immediately after the requested functionality is complete.

See [`anti-over-defense/SKILL.md`](anti-over-defense/SKILL.md) for the complete behavior rules.

## Project structure

```text
anti-over-defense/
├── SKILL.md
└── agents/
    └── openai.yaml
```

- `SKILL.md` defines the skill's activation scope and complete execution rules.
- `agents/openai.yaml` defines the name, short description, and default prompt shown in Codex interfaces.

## References

- [OpenAI: Build skills](https://learn.chatgpt.com/docs/build-skills.md)
- [Agent Skills specification](https://agentskills.io/specification)
