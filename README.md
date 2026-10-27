# markdown-generator

`gitlog2markdown` turns the git history of a repository into a Markdown changelog, grouped by day.

## Installation

Copy the script into a directory on your `PATH` and make it executable:

```bash
cp gitlog2markdown ~/.local/bin/
chmod +x ~/.local/bin/gitlog2markdown
```

## Usage

Run it from inside a git repository:

```bash
gitlog2markdown [-a=AUTHOR] [-s=SINCE] [-u=UNTIL] [-o=FILE]
```

| Option | Description |
| --- | --- |
| `-a`, `--author=AUTHOR` | Only include commits by this author (the author's name is then left off each line) |
| `-s`, `--since=DATE` | Start date, inclusive (e.g. `2024-01-01`) |
| `-u`, `--until=DATE` | End date, inclusive (e.g. `2024-12-31`) |
| `-o`, `--output=FILE` | Output file (default `CHANGELOG.md`; use `-` to print to stdout) |
| `-h`, `--help` | Show help |

Merge commits are left out, and dates use your local timezone.

### Examples

```bash
# Full history to CHANGELOG.md
gitlog2markdown

# One author's commits in 2024, printed to the terminal
gitlog2markdown --author="Jane Doe" --since=2024-01-01 --until=2024-12-31 -o=-
```

### Sample output

```markdown
# Gitlog

## Version 2024-03-01
 * Add login page (Jane Doe) - a1b2c3d
 * Fix typo in README (John Smith) - e4f5a6b

## Version 2024-03-02
 * Refactor auth module (Jane Doe) - c7d8e9f
```
