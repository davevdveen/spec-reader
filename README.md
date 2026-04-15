# SpecReader

Beautiful reading experience for [OpenSpec](https://openspec.dev) specification files and project documentation.

## Why

AI-assisted development generates specs, proposals, and designs faster than ever. But reviewing structured markdown in a terminal or a GitHub diff is painful. When specs are hard to read, they don't get read.

SpecReader gives your specifications a proper reading experience. Collapsible requirements, themed reading modes, and structured navigation make it natural to review proposals and specs, whether they're yours or someone else's.

## Quick start

```bash
npx @davevdveen/spec-reader
```

Works on any project directory. Auto-detects OpenSpec folders and renders everything readable: specs, proposals, READMEs, configs, and more.

Try it on the [OpenSpec framework](https://github.com/Fission-AI/OpenSpec) itself:

```bash
git clone https://github.com/Fission-AI/OpenSpec && cd OpenSpec && npx @davevdveen/spec-reader
```

## AI coding agent skill

SpecReader includes a skill for AI coding agents (Claude Code, OpenCode) that opens the viewer for any PR or branch:

```
/read-specs              # open specs for current branch
/read-specs 42           # checkout PR #42 and open its specs
/read-specs feature/xyz  # checkout branch and open specs
```

Install the skill in your project:

```bash
npx @davevdveen/spec-reader init
```

This auto-detects your agent (Claude Code, OpenCode, or both) and installs the skill in the right place.

## Scopes

| Scope | Shows |
|-------|-------|
| Specs | OpenSpec files |
| Docs | All markdown files |
| All | All readable files (.md, .yaml, .yml, .txt, extensionless) |
| Search | Filter across all files |

## Themes

Four reading themes, each with light and dark variants:

| Theme | Font |
|-------|------|
| Original | Sans-serif |
| Paper | Georgia serif |
| Calm | Serif, warm tones |
| Mono | Monospace |

Follows system light/dark preference with manual override.

## Commands

```bash
spec-reader                          # serve current directory
spec-reader ~/projects/myapp         # serve any project
spec-reader export openspec/ dist/   # export static site
spec-reader init                     # install AI agent skill
view-proposal add-dark-mode          # open viewer on a proposal
```

## Keyboard shortcuts

| Key | Action |
|-----|--------|
| `←` `→` | Previous / next page |
| `↑` `↓` | Scroll content |
| `-` | Expand / collapse all sections in the document |
| `Cmd+Shift+R` | Toggle sidebar |

## How it works

A single HTML file served by a shell script that walks your directory, generates a manifest, and starts Python's built-in HTTP server. Zero runtime dependencies beyond Python 3.

File changes are detected every 3 seconds. Edit a spec, see it update in the viewer.

## Prerequisites

- **Python 3** (used to serve files locally)
- **Node.js** (for `npx` installation only)
- **gh CLI** (optional, for the `/read-specs` skill to checkout PRs)

Works on macOS, Linux, and Windows (WSL). Tested in Safari, should work in any modern browser.

## Install

```bash
npm install -g @davevdveen/spec-reader
npx @davevdveen/spec-reader
```

## License

MIT
