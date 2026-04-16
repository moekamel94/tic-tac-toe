# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file browser Tic Tac Toe game (`tictactoe.html`). No build tools, no dependencies, no server — open the file directly in a browser.

## Running the Game

```bash
start tictactoe.html        # Windows: open in default browser
open tictactoe.html         # macOS
xdg-open tictactoe.html     # Linux
```

## Architecture

Everything lives in `tictactoe.html` as one self-contained file with three inline sections:

- **CSS** (`<style>`) — layout (CSS Grid 3×3), theming (dark palette), and win animation (`pulse` keyframe)
- **HTML** — static board of 9 `.cell` divs, a score display, and a status line
- **JavaScript** (`<script>`) — plain vanilla JS, no frameworks

### Game Logic

| Concern | How it works |
|---|---|
| State | `board[]` (9-element array), `current` (X/O), `over` (boolean), `score` object |
| Win detection | `WINS` constant — 8 hard-coded winning index triples, checked after every move |
| Turn flow | Click handler on each `.cell` → update `board[]` → check win/tie → swap `current` |
| Score | Persists across rounds in the `score` object; reset only on page reload |

## Git Workflow

**After every meaningful change, commit and push immediately.** Never leave working changes uncommitted. This ensures the GitHub repo (`moekamel94/tic-tac-toe`) always reflects the latest working state and any version can be recovered.

```bash
git add <file>
git commit -m "short imperative description"
git push
```

### Commit message rules
- Use the imperative mood: "Add X", "Fix Y", "Remove Z"
- One concise subject line (50 chars or less)
- No trailing periods

### When to commit
- After adding a new feature or UI element
- After fixing a bug
- After any refactor, even small ones
- After updating CLAUDE.md or project config
