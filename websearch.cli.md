# websearch CLI

## Goal

Search the web from the terminal and print concise result cards with title, URL, and snippet.

## Usage

```bash
websearch QUERY
```

Limit result count:

```bash
websearch QUERY -n 3
```

Print JSON:

```bash
websearch QUERY --json
```

## Options

| Option | Description |
| --- | --- |
| `-n, --count NUMBER` | Number of results to print. Default: `10`. |
| `--json` | Print results as JSON. |
| `--timeout SECONDS` | Set request timeout. Default: `20`. |

## Examples

```bash
websearch python markdown extraction
websearch "site:docs.python.org pathlib" -n 3
websearch "trafilatura extract markdown" --json
```

## Notes

- Search results are fetched from DuckDuckGo's HTML endpoint.
- Some networks or search providers may rate-limit automated requests.
- Dependencies: `httpx` and `beautifulsoup4`.
