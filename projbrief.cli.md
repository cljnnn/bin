# projbrief CLI

## Goal

Print a compact project brief so an agent or developer can quickly understand a directory.

## Usage

```bash
projbrief [path]
```

If `path` is omitted, `projbrief` summarizes the current directory.

## Options

| Option | Description |
| --- | --- |
| `--depth N` | Directory tree depth to print. Defaults to `2`. |
| `--files N` | Maximum tree entries to print. Defaults to `80`. |
| `--help` | Show help text. |

## Examples

```bash
projbrief .
projbrief ~/code/my-project --depth 3
projbrief . --files 40
```

## Notes

- Output is written to stdout.
- Errors are written to stderr and exit with a non-zero status.
- The tree skips common heavy directories such as `.git`, `node_modules`, `dist`, `build`, and `.venv`.
- Git repositories include changed files and changed directory counts from `git status --short`.
- JavaScript package scripts use the detected package manager from lockfiles: `pnpm`, `yarn`, `bun`, or `npm`.
- Recent files are based on filesystem modification time and are separate from Git changes.
