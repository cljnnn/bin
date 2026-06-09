# urlmd CLI

## Goal

Fetch a URL, extract the readable main content, and convert it to Markdown.

## Usage

```bash
urlmd URL
```

Write to a file:

```bash
urlmd URL -o article.md
```

Include the extracted page title:

```bash
urlmd URL --title
```

Keep links and images where extraction supports them:

```bash
urlmd URL --links --images
```

Convert the full HTML when main-content extraction fails:

```bash
urlmd URL --raw-html
```

## Options

| Option | Description |
| --- | --- |
| `-o, --output PATH` | Write Markdown to a file instead of stdout. |
| `--title` | Prefix output with the extracted page title as `# Title`. |
| `--links` | Preserve links in Markdown output. |
| `--images` | Preserve images in Markdown output when available. |
| `--timeout SECONDS` | Set request timeout. Default: `20`. |
| `--raw-html` | Convert the full fetched HTML instead of extracting main content first. |

## Examples

```bash
urlmd https://example.com
urlmd https://example.com -o example.md
urlmd https://example.com --title --links
```

## Notes

- Main-content extraction uses `trafilatura`.
- Raw HTML conversion uses `markdownify`.
- The command expects HTML-like pages. PDFs and binary files are intentionally unsupported.
