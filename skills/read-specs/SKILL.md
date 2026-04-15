---
name: read-specs
description: Open the SpecReader viewer to read OpenSpec specifications, proposals, designs, tasks, and project documentation in a themed reading experience. Use this skill whenever the user wants to read specs, review a proposal, browse documentation, view OpenSpec files, read READMEs, or says "open specs", "read specs", "show me the specs", "review the proposal", "open the viewer", or "/read-specs". Also trigger when the user wants to review specs from a specific PR or branch.
---

Open the SpecReader viewer for the current repo's OpenSpec files and documentation, or for a specific PR or branch.

Works with Claude Code and OpenCode.

## Usage

- `/read-specs` — open specs for the current branch
- `/read-specs 42` — checkout PR #42 and open its specs
- `/read-specs feature/my-branch` — checkout branch and open its specs

## Steps

1. If an argument is provided:
   - If it's a number, run `gh pr checkout <number>` (requires gh CLI)
   - If it's a branch name, run `git checkout <branch>`

2. Find the project root (look for `.git` directory).

3. Run the viewer in the background:
   ```bash
   npx @davevdveen/spec-reader &
   ```
   This starts a local server and opens the browser.

4. Tell the user:
   - "Spec viewer is open at http://localhost:3333"
   - "Changes are auto-detected every 3 seconds"
   - "Use arrow keys to navigate between pages"
   - "Use the scope bar to switch between Specs, Docs, All, or Search"
   - "Use the Aa button to change themes and light/dark mode"
