# git-branch-info

Extended `git branch` that shows created date, last modified date, and merge status for each branch.

## Example Output

```
Branch                    Created             Last Modified       Merged
──────────────────────    ─────────────────   ─────────────────   ────────
* main                    2024-01-15 10:30    2024-03-20 14:22    -
  feature/auth            2024-03-01 09:00    2024-03-18 16:45    no
  feature/api-v2          2024-02-20 11:15    2024-03-15 10:30    no
  bugfix/login            2024-03-10 14:00    2024-03-12 09:20    yes
```

## Installation

```bash
# Clone or download the script
curl -O https://raw.githubusercontent.com/YOUR_USERNAME/git-branch-info/main/git-branch-info
chmod +x git-branch-info

# Option 1: Add to PATH
mv git-branch-info /usr/local/bin/

# Option 2: Use as git subcommand (rename to git-branch-info in PATH)
# Then run as: git branch-info
```

## Usage

```bash
git-branch-info [OPTIONS] [asc|desc]
```

### Options

| Option | Description |
|--------|-------------|
| `--remote`, `-r` | Show remote branches instead of local |
| `-s`, `--sort COLUMN` | Sort by column: `name` (default), `created`, `modified`, `merged` |
| `asc` | Sort ascending (default) |
| `desc`, `dsc` | Sort descending |
| `-h`, `--help` | Show help |

### Examples

```bash
# Local branches sorted by name (default)
git-branch-info

# Sort by last modified, newest first
git-branch-info -s modified desc

# Remote branches sorted by creation date
git-branch-info --remote -s created

# Find branches already merged into main
git-branch-info -s merged
```

## Columns

- **Branch**: Branch name (current branch marked with `*`)
- **Created**: Date the branch diverged from main/master
- **Last Modified**: Date of the most recent commit on the branch
- **Merged**: Whether the branch has been merged into main/master (`yes`/`no`/`-` for main itself)

## Requirements

- Bash 3.2+ (compatible with macOS default)
- Git

## Notes

- Colors are automatically disabled when piping output
- Column widths adapt to terminal size
- For remote branches, runs `git fetch --prune` first for updating. 
