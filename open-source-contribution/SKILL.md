---
name: open-source-contribution
description: Contribute to a GitHub project like a careful open-source contributor. Use when asked to pick up a GitHub issue, implement the requested change, work in a fork, create a dedicated branch, commit cleanly, push, and open a pull request with issue references and a clear summary.
---

# Open Source Contribution

Contribute as if the target repo were a real external project: read first, change only what the issue asks for, keep history clean, and leave a reviewable PR behind.

## Quick workflow

1. Read the issue, relevant files, and current repo structure before editing anything.
2. Infer the narrowest reasonable interpretation of the issue.
3. Fork the repo if you do not already have write access or if the task explicitly asks for a contributor-style flow.
4. Create a dedicated branch from the target default branch.
5. Make only the changes needed for the issue.
6. Validate the result locally when possible.
7. Commit with a clean message.
8. Push the branch to the fork.
9. Open a PR against the upstream repo and reference the issue.
10. Summarize what changed, what you assumed, and any limitations.

## Contribution rules

- Prefer a **fork + branch + PR** flow unless the user explicitly asks for direct pushes.
- Keep the scope tight. Do not slip in unrelated cleanup.
- Read the issue body, linked files, and nearby docs before deciding on implementation.
- If the issue is ambiguous, choose the most conservative reasonable interpretation and state that in the PR.
- If the repo has contribution conventions, follow them.
- If tests or lint exist and are cheap to run, run them.
- If no automated checks exist, do a lightweight manual validation.
- Avoid force-push unless fixing your own branch and there is a clear reason.

## Branch naming

Use a readable branch name, for example:

- `byteclaw/issue-12-fix-readme-links`
- `byteclaw/issue-7-add-market-analysis`
- `byteclaw/issue-1-reformat-analysis`

Pattern:

- actor prefix when useful
- issue number
- short hyphenated task summary

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
gh issue view 12 --repo owner/repo
gh repo view owner/repo
gh repo clone owner/repo ./repo
```

### Fork and branch

```bash
cd ./repo
gh repo fork owner/repo --clone=false --remote=true

git checkout -b byteclaw/issue-12-short-summary origin/main
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
git push -u fork byteclaw/issue-12-short-summary

gh pr create \
  --repo owner/repo \
  --base main \
  --head YOUR_FORK_OWNER:byteclaw/issue-12-short-summary \
  --title "Docs: improve X" \
  --body-file references/pr-body-template.md
```

Adjust base branch if the repo does not use `main`.

## Review checklist before opening the PR

- Issue fully read
- Scope still narrow
- No unrelated file churn
- Diff is understandable
- Branch name is clean
- Commit message is clean
- PR body explains context and changes
- Issue reference included

## Read this reference when writing the PR

See `references/pr-body-template.md` for a compact PR structure you can adapt.
