---
type: Playbook
id: https://w3id.org/ktl/federation/knowledge/playbooks/contributing
title: Contributing to this domain
description: How to set up a clone, what to check before a pull request to this domain, and the rules for AI-assisted changes. It names the gate's two checks, the lint CI runs, the sidecar copies never edited here, and the changelog entry a change in behaviour needs.
genre: how-to
resource: CONTRIBUTING.md
references:
  - https://w3id.org/ktl/federation/knowledge/playbooks/confirming-a-member-change
  - https://w3id.org/ktl/federation/knowledge/policies/federation
sources:
  - resource: CONTRIBUTING.md
  - resource: .github/pull_request_template.md
  - resource: .github/workflows/lint-and-docs.yaml
  - resource: AI_COVENANT.md
generated:
  by: process:ktl-librarian
  at: "2026-10-26T18:19:07Z"
status: draft
---

# Overview

This playbook says how to change this repository: the setup, the checks before a pull request, and the rules for AI tools. [Confirming a member change](confirming-a-member-change.md) gives a person's steps to confirm a member.

## Setup

You need [uv](https://docs.astral.sh/uv/) and [just](https://github.com/casey/just), and Node.js 24 for the website. Clone the repository, then run `just lokf-install && just lokf-check-refs` from `.lokf/`.

The agent skills that maintain the bundle come from knowledge-trust-ladder. Install them, and never commit them:

```bash
npx skills add noelmcloughlin/knowledge-trust-ladder --skill ktl-curator --yes
```

Where a company proxy or an internal npm registry blocks `npx`, the GitHub CLI installs the skill instead: `gh skill install noelmcloughlin/knowledge-trust-ladder ktl-curator --scope user --agent <yours>`.

## Before a pull request

- A member names one release, the newest that carries a `knowledge-*.zip`. Its `checksum` is the digest in that release's `.sha256`.
- A confirmation is a person's own act. Record it with ktl-curator, in a signed commit. No agent writes a confirmation.
- Copy nothing from a member. The domain names releases, and the workspace is built from them.
- Run the gate's two checks from `.lokf/`: `just lokf-check-refs` and `bash scripts/knowledge-conventions.sh knowledge`.
- Leave the sidecar's copies alone: `.lokf/scripts/`, `.lokf/m365/` and the `knowledge-*.yaml` workflows. Change them in KTL. Each week `knowledge-sync.yaml` checks the newest skills release and, when this host is behind, opens one pull request that copies its templates over them.
- When the `lokf` toolkit's version changes, copy `.lokf/lokf.yaml` again from the installed package in the same pull request. The sync leaves that file alone.
- Lint as CI does. `lint-and-docs.yaml` runs markdownlint against `.markdownlint-cli2.jsonc`, lychee against `lychee.toml` and codespell over every `*.md`, and actionlint and ShellCheck over the workflows and scripts.
- Add an entry under `## [Unreleased]` in `CHANGELOG.md` when your change alters behaviour.

The pull request template repeats these checks as a checklist. When a pull request records a confirmation, the template asks the person to state that they opened the release named by every confirmation they approve.

## AI tools

AI assistance is welcome. `AI_COVENANT.md` sets the rules, for people and the scheduled librarian alike: you are the author of what you submit.

For any change under `.lokf/knowledge/`, name the release it rests on, by its tag and its page, and check the checksum against that release's `.sha256`. The members script's hand-off lines say what it verified. They are evidence for the person who confirms, not a confirmation.

## License

Contributions are licensed under the Apache License 2.0. The knowledge bundle is published under CC BY 4.0, as its `index.md` says.
