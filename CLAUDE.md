# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains `git-branch-info`, a standalone bash script that extends `git branch` with additional metadata: created date, last modified date, and merge status relative to main/master.

## Running the Script

```bash
# Make executable (if needed)
chmod +x git-branch-info

# Run directly
./git-branch-info

# Common usage patterns
./git-branch-info                       # local branches, sorted by name
./git-branch-info -s modified desc      # sort by last modified, newest first
./git-branch-info --remote -r           # show remote branches
./git-branch-info -s created            # sort by branch creation date
```

## Technical Notes

- **Bash 3.2 compatibility**: The script avoids associative arrays and uses temp files with grep-based lookups to support macOS's default bash
- **Parallel execution**: Created dates are computed in parallel background jobs for performance
- **Terminal-aware**: Colors are disabled when output is piped; column widths adapt to terminal size
- **Cleanup**: Uses trap to clean up temp directory, but only in the main shell process (not subshells)
