---
name: personal-cli-tools
description: Use when a task may be solved by Linjun's local CLI capabilities. Read index.md as the capability directory, then use manuals or --help only when more detail is needed.
---

# Personal CLI Tools

Use this skill when the user asks for something that may already be covered by Linjun's local command-line capabilities in this directory.

This skill is a **capability router**, not a command catalog. The source of truth is `index.md`.

## Source of Truth

Before choosing a command, use:

```txt
index.md
```

Treat that file as the current capability directory. It contains enough information for common use:

- Available commands.
- Classic usage for each command.
- Links to focused manuals for deeper detail when needed.
- One-line capability descriptions.

Do not maintain a duplicated command list in this skill. If the index changes, follow the index.

## Workflow

### Discover

Read `index.md` and identify whether any listed capability matches the user's goal.

Match by intent, not by command name. The user should not need to know the command names.

### Inspect Only When Needed

If the `index.md` row gives enough information, use the classic usage directly and adapt it to the user's request.

Read the linked `*.cli.md` manual only when you need more detail, such as:

- Non-obvious options.
- Output behavior that affects the task.
- File-writing behavior.
- Dependency notes.
- Failure modes.

Run `command --help` only when the manual is unavailable, stale, or still leaves ambiguity.

### Execute

Run the selected CLI through the shell from the appropriate working directory.

Use the classic usage from `index.md` as the starting point, then adjust arguments to the user's actual request.

Prefer stdout for normal results. Write files only when the user asked for a file or the task clearly requires one.

### Report

Return the result the user needs, not a transcript of command mechanics.

If a command fails, explain the command-level reason and the next useful action.

## Usage Rules

- Call commands through `bash` from an appropriate working directory.
- Use `index.md` as the first stop for capability discovery and classic usage.
- Read the linked command manual only when the task needs more than the index provides.
- Run `--help` only when useful for resolving uncertainty.
- Keep command output in stdout unless the user asks to write files.
- If writing files, confirm the output path is inside the intended workspace.
- Surface clear command errors to the user instead of hiding them.
- Do not use these CLIs for secrets, private credentials, or destructive operations.

## When No Capability Matches

If `index.md` does not list a suitable capability, do not force a CLI.

Answer normally, or build a new CLI only if the user asks to create or automate that capability.
