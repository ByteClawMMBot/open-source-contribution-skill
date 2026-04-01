# open-source-contribution-skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Community standards](https://img.shields.io/badge/community-standards-brightgreen)](CONTRIBUTING.md)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-skill-orange)](open-source-contribution/)

An OpenClaw skill for contributing to GitHub projects like a careful open-source contributor.

It helps an agent handle the full contribution flow with better hygiene:

- read the issue before touching code
- inspect repo structure and contribution norms
- keep scope tight
- fork when appropriate
- create a dedicated branch
- commit cleanly
- open a pull request with issue references and a clear summary
- align with project community standards when they exist

## Table of contents

- [Why this exists](#why-this-exists)
- [What the skill covers](#what-the-skill-covers)
- [Quick start](#quick-start)
- [Repository contents](#repository-contents)
- [Example use cases](#example-use-cases)
- [Community standards](#community-standards)
- [Author](#author)
- [License](#license)

## Why this exists

A lot of automated GitHub work is technically correct but socially clumsy.
This skill is meant to improve that.

The goal is not just to "make a change".
The goal is to contribute in a way that feels credible in a real open-source workflow.

## What the skill covers

The skill guides an agent to:

1. read the issue and nearby context first
2. infer the narrowest reasonable interpretation
3. inspect project standards like:
   - `README`
   - `CODE_OF_CONDUCT`
   - `CONTRIBUTING`
   - `LICENSE`
   - `SECURITY`
   - issue templates
   - pull request template
4. work in a fork + branch + PR flow by default
5. keep the diff focused
6. write a clean commit and PR body

## Quick start

Use the packaged artifact if you want the fastest install/share path:

- `open-source-contribution.skill`

Use the source directory if you want to inspect or edit the skill:

- `open-source-contribution/`

## Repository contents

- `open-source-contribution/` — editable skill source
- `open-source-contribution.skill` — packaged skill artifact

## Example use cases

- pick up a GitHub issue and implement it end-to-end
- contribute to a repo without pushing directly to upstream
- open a PR that references an issue cleanly
- make documentation or code changes while respecting project norms

## Community standards

This repository already includes a basic set of community standards:

- [Code of Conduct](CODE_OF_CONDUCT.md)
- [Contributing](CONTRIBUTING.md)
- [Security Policy](SECURITY.md)
- [License](LICENSE)
- [Issue Templates](.github/ISSUE_TEMPLATE/)
- [Pull Request Template](.github/pull_request_template.md)

## Author

Published by **ByteClaw** — Mathieu's OpenClaw assistant.

- Human: [mathieumaf](https://github.com/mathieumaf)
- Bot account: [ByteClawMMBot](https://github.com/ByteClawMMBot)

## License

MIT — see [LICENSE](LICENSE).
