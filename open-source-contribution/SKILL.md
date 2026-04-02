---
name: open-source-contribution
description: Contribute to a GitHub project like a careful open-source contributor. Use when asked to pick up a GitHub issue, implement the requested change, work in a fork, create a dedicated branch, commit cleanly, push, and open a pull request with issue references and a clear summary.
---

# Open Source Contribution

Contribute as if the target repo were a real external project: read first, change only what the issue asks for, keep history clean, and leave a reviewable PR behind.

## Quick workflow

1. Triage the issue before contributing.
2. Read the issue, comments, relevant files, and current repo structure before editing anything.
3. Decide go / no-go.
4. Infer the narrowest reasonable interpretation of the issue.
5. Fork the repo if you do not already have write access or if the task explicitly asks for a contributor-style flow.
6. Create a dedicated branch from the target default branch.
7. Make only the changes needed for the issue.
8. Validate the result locally when possible.
9. Commit with a clean message.
10. Push the branch to the fork.
11. Open a PR against the upstream repo and reference the issue.
12. Summarize what changed, what you assumed, and any limitations.

## Issue triage before contributing

Check these points before touching code:

- Is the issue still open and still relevant?
- Is someone already assigned?
- Is there already an open PR for the same issue or topic?
- Do issue comments show maintainer direction, constraints, or a preferred approach?
- Does the issue look blocked, postponed, or waiting on a refactor?
- Is the scope small enough for a focused contribution?

Do not assume an open issue is automatically ready for contribution.

## Go / no-go

### Go when

- the issue is clear enough to act on
- there is no active PR duplicating the work
- maintainer direction is either clear or not needed
- the scope is narrow and reviewable
- the change can be validated reasonably

### No-go when

- an open PR already covers the same work
- the issue is assigned and actively moving
- maintainer comments say to wait
- the change depends on a large refactor or unclear product/design decisions
- the issue is too ambiguous for a clean first pass

If in doubt, prefer no-go or comment-first over opening a speculative PR.

## Contribution rules

- Prefer a **fork + branch + PR** flow unless the user explicitly asks for direct pushes.
- Keep the scope tight. Do not slip in unrelated cleanup.
- Read the issue body, linked files, nearby docs, and issue comments before deciding on implementation.
- Search for open PRs or recent closed PRs that may already cover the same topic.
- If the issue is ambiguous, choose the most conservative reasonable interpretation and state that in the PR.
- Check for maintainer alignment before investing in implementation, especially for feature requests or UX changes.
- If the repo has contribution conventions, follow them.
- Check whether the project follows or expects **community standards** such as:
  - `README`
  - `CODE_OF_CONDUCT`
  - `CONTRIBUTING`
  - `LICENSE`
  - `SECURITY`
  - issue templates
  - pull request template
- If those files or templates exist, align with them before contributing.
- If tests or lint exist and are cheap to run, run them.
- If no automated checks exist, do a lightweight manual validation.
- Avoid force-push unless fixing your own branch and there is a clear reason.

## Branch naming

Use a readable branch name, for example:

- `issue-12-fix-readme-links`
- `issue-7-add-market-analysis`
- `issue-1-reformat-analysis`
- `docs/issue-3-improve-contributing-guide`
- `feat/issue-9-add-export-command`

Pattern:

- optional type prefix when useful (`docs/`, `fix/`, `feat/`, etc.)
- issue number
- short hyphenated task summary

Do not hardcode your own bot or username into the naming convention unless the target project explicitly wants that.

## Commit guidance

Prefer one clean commit for a small issue.

Good patterns:

- `docs: clarify onboarding steps for issue #12`
- `feat: add export command for issue #7`
- `fix: handle empty state in dashboard for issue #4`

If multiple commits help review, keep them intentional and easy to understand.

## PR guidance

The PR should contain:

- a clear title tied to the actual change
- a short context section
- a concise list of changes
- explicit issue reference (`Closes #<n>` or `Refs #<n>` depending on certainty)
- assumptions or limitations when relevant

When the issue asks for formatting, editorial cleanup, or documentation improvements, call out explicitly that the work focuses on structure/readability rather than strategy or functionality.

## Suggested GitHub CLI flow

Use `gh` when available.

### Inspect issue and repo

```bash
gh issue view 12 --repo owner/repo --comments
gh pr list --repo owner/repo --state open --search "12 in:title,body"
gh repo view owner/repo
gh repo clone owner/repo ./repo
```

### Fork and branch

```bash
cd ./repo
gh repo fork owner/repo --clone=false --remote=true

git checkout -b issue-12-short-summary origin/main
```

If the fork remote is not set as expected, inspect remotes and fix them deliberately.

### Implement and validate

Read relevant files first, then edit only the necessary files.

Examples:

```bash
git status
git diff --stat
```

Run project checks if they exist.

### Commit, push, PR

```bash
git add <files>
git commit -m "docs: improve X for issue #12"
git push -u fork issue-12-short-summary

gh pr create \
  --repo owner/repo \
  --base main \
  --head YOUR_FORK_OWNER:issue-12-short-summary \
  --title "Docs: improve X" \
  --body-file references/pr-body-template.md
```

Adjust base branch if the repo does not use `main`.

## Review checklist before opening the PR

- Issue fully read
- Issue comments read
- Existing PRs on the same topic checked
- Scope still narrow
- No unrelated file churn
- Diff is understandable
- Branch name is clean
- Commit message is clean
- PR body explains context and changes
- Issue reference included
- Maintainer alignment checked when relevant
- Community standards checked when present (`README`, `CODE_OF_CONDUCT`, `CONTRIBUTING`, `LICENSE`, `SECURITY`, issue templates, PR template)

## Read this reference when writing the PR

See `references/pr-body-template.md` for a compact PR structure you can adapt.
