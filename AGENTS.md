# CLI Creation Workflow

This directory contains small personal CLI tools that are available from `PATH`.

## Goal

Every CLI should be immediately usable, documented in one focused manual, and discoverable from the shared index.

## Required Files

For each command named `toolname`, create or update:

| File | Purpose |
| --- | --- |
| `toolname` | Executable CLI script. |
| `toolname.cli.md` | Focused manual for that single CLI. |
| `index.md` | Shared index of all CLIs. |

## Workflow

### Understand the command

Define the smallest useful behavior first:

- What problem does the CLI solve?
- What is the classic one-line usage?
- What input does it accept?
- What output does it produce?
- What errors should be explicit?

Avoid speculative features. Add options only when they improve daily use.

### Create the executable

Use a direct command name with no extension:

```bash
toolname
```

The script must:

- Start with a valid shebang, for example `#!/usr/bin/env python3`.
- Be executable with `chmod +x toolname`.
- Provide `--help`.
- Print normal output to stdout.
- Print errors to stderr.
- Exit with non-zero status on failure.
- Use English for code, comments, and user-facing CLI text.

### Write the CLI manual

Create `toolname.cli.md` with these sections:

```md
# toolname CLI

## Goal

## Usage

## Options

## Examples

## Notes
```

Keep the manual concise. It should answer how to use the command, not explain unrelated implementation details.

### Update the index

Update `index.md` every time a CLI is added, renamed, or removed.

The index table must include:

| Column | Content |
| --- | --- |
| `Command` | Command name in backticks. |
| `Classic Usage` | One representative command that works as a quick reminder. |
| `Manual` | Link to `toolname.cli.md`. |
| `Description` | One short sentence describing the command. |

Example row:

```md
| `urlmd` | `urlmd https://example.com` | [`urlmd.cli.md`](./urlmd.cli.md) | Fetch a URL, extract main content, and convert it to Markdown. |
```

### Validate before finishing

Run these checks:

```bash
./toolname --help
./toolname <classic-usage-arguments>
```

If the command writes files, validate the file exists and contains expected content.

## Quality Rules

- Keep tools small and composable.
- Prefer clear failures over silent fallback behavior.
- Do not add compatibility shims for unused old behavior.
- Do not create extra docs when `toolname.cli.md` and `index.md` are enough.
- Do not store logs or temporary artifacts in this directory unless they are part of the tool's intended output.
- If dependencies are required, make them explicit in the manual's notes.

## Completion Checklist

- [ ] Executable script exists.
- [ ] Script has a shebang.
- [ ] Script is executable.
- [ ] `--help` works.
- [ ] Classic usage works.
- [ ] `toolname.cli.md` exists.
- [ ] `index.md` includes the command, classic usage, manual link, and description.
