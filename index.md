# ~/.bin CLI Index

Small personal CLI tools available from `PATH`.

## Directory Contract

Each command keeps one clear ownership trail:

- `command`: executable CLI script.
- `command.cli.md`: focused manual for that command.
- `index.md`: shared discovery index with classic usage.

Keep tools small, composable, and explicit about failures. Add options only when they improve daily use.

## Tool Index

| Command | Classic Usage | Manual | Description |
| --- | --- | --- | --- |
| `projbrief` | `projbrief .` | [`projbrief.cli.md`](./projbrief.cli.md) | Print a compact project brief for a directory. |
| `urlmd` | `urlmd https://example.com` | [`urlmd.cli.md`](./urlmd.cli.md) | Fetch a URL, extract main content, and convert it to Markdown. |
| `websearch` | `websearch python markdown extraction` | [`websearch.cli.md`](./websearch.cli.md) | Search the web and print concise result cards. |

## Skill Integration

This repository also exposes an opencode skill at:

```txt
SKILL.md
```

Register this directory in opencode config:

```json
{
  "skills": {
    "paths": ["/Users/linjun/.bin"]
  }
}
```

Restart opencode after changing skill configuration. The skill makes this index the first stop for discovering local CLI capabilities and classic usage.

## Add or Update a CLI

1. Define the smallest useful behavior and one classic usage.
2. Create or update the executable script with `--help`, stdout output, stderr errors, and non-zero failure exits.
3. Create or update the focused `command.cli.md` manual.
4. Update the table above.
5. Validate `./command --help` and the classic usage before finishing.
