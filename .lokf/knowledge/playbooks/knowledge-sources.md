---
type: Playbook
id: https://w3id.org/ktl/federation/knowledge/playbooks/knowledge-sources
title: Knowledge sources
description: Map of the repository paths and outside pages this domain bundle is derived from, the concepts each yields, the files left out on purpose, and how to re-check each on a later refresh.
genre: how-to
resource: .
sources:
  - resource: README.md
  - resource: docs
  - resource: CONTRIBUTING.md
  - resource: CHANGELOG.md
  - resource: SECURITY.md
  - resource: AI_COVENANT.md
  - resource: CODE_OF_CONDUCT.md
  - resource: LICENSE
  - resource: llms.txt
  - resource: .releaserc.json
  - resource: .editorconfig
  - resource: .gitignore
  - resource: .markdownlint-cli2.jsonc
  - resource: lychee.toml
  - resource: .github
  - resource: website
  - resource: .assets
  - resource: scripts
  - resource: .lokf/domain.yaml
  - resource: https://w3id.org/ktl/docs/federation
  - resource: https://w3id.org/ktl/federation/workspace/index.md
generated:
  by: process:ktl-librarian
  at: "2026-10-26T18:19:07Z"
status: draft
---

# Overview

This map lists where the domain bundle's concepts come from, which concepts each source yields, and how a later run re-checks it. Most of what this bundle claims rests outside the repository: on each member's releases, and on KTL's federation pages.

| Source | Yields | Class(es) | Re-check by |
| --- | --- | --- | --- |
| each member's releases on its forge: the `knowledge-*.zip`, its `.sha256` and its build attestation | `members/` | `MemberBundle`, `MemberDomain` | running the members script, `knowledge-federate.py members`, which the librarian wrapper runs in place of an agent; a person confirms each change it proposes |
| `.lokf/domain.yaml` | the domain schema, and the settings the domain concept states | `Reference` (`references/domain-schema.md`), `Domain` (`domains/ktl-federation.md`) | re-reading the header comment and the `Domain` class's slots |
| `docs/architecture.md` | the domain, how it stays current, and the workspace | `Domain`, `Dataset` (`datasets/workspace.md`), `Reference` | re-reading "The domain", "How it stays current" and "The workspace" |
| `docs/curation.md` | the steps a person takes to confirm a member change or a new member | `Playbook` (`playbooks/confirming-a-member-change.md`) | re-reading the numbered steps and the three check commands |
| <https://w3id.org/ktl/docs/federation>, <https://w3id.org/ktl/docs/context-layer>, <https://w3id.org/ktl/knowledge/playbooks/domain-bundle> | admission, the gate, what a confirmation attests | `Policy` (`policies/federation.md`) | re-fetching each page for a changed admission rule or gate |
| <https://w3id.org/ktl/federation/workspace/index.md>, `.github/workflows/knowledge-federation.yaml` | the workspace each release builds | `Dataset` (`datasets/workspace.md`) | re-reading the index after a release, and diffing the workflow's jobs against the concept |
| `CONTRIBUTING.md`, `.github/pull_request_template.md`, `.github/workflows/lint-and-docs.yaml`, `AI_COVENANT.md` | setup, the checks before a pull request, and the rules for AI tools | `Playbook` (`playbooks/contributing.md`) | re-reading the checklist, and diffing the lint jobs against the concept |
| `.github/workflows/semantic-release.yml`, `.releaserc.json`, `.github/scripts/changelog-release.mjs`, `.github/workflows/knowledge-release.yaml`, `SECURITY.md` | what releases this domain, the changelog rule, and what the release job dispatches | `Playbook` (`playbooks/releasing.md`) | reading the release rules and the dispatch step |
| `website/README.md`, `website/site.config.mjs`, `.github/workflows/knowledge-website.yaml` | the knowledge website, and which workflow deploys it | `Playbook` (`playbooks/knowledge-website.md`) | re-reading the README's page list and "What to edit", and the `if:` conditions of each workflow's deploying job |
| `README.md`, `llms.txt` | the doorway: the members table and the note for agents | none of their own | checking the members table against `members/` |

## How to re-check

Start from `bash .lokf/scripts/knowledge-report.sh worklist`, which names each concept whose local source moved since it was derived or last checked. It compares nothing for a source that is a URL, so re-read KTL's pages and the workspace index on every run.

Check a sidecar copy against the ktl-sidecar templates at the release named by `TRUST_LADDER_SKILLS_REF` in `.github/workflows/knowledge-librarian.yaml`.

`bash .lokf/scripts/knowledge-report.sh coverage` counts the tracked files that no concept and no row of this map names.

## Left out on purpose

- The sidecar's copies, which keep this bundle and describe none of it: `.lokf/scripts/`, `.lokf/m365/`, `.github/workflows/knowledge-registrar.yaml`, `knowledge-librarian.yaml` and `knowledge-sync.yaml`, and `.github/PULL_REQUEST_TEMPLATE/knowledge-sync.md`. `SECURITY.md` says what holds each.
- The rest of `website/`, which is the ktl-website skill's code. `website/README.md` says which file to edit for each part of the site.
- `.assets/` and `scripts/companion-diagrams.mjs`: the context layer figure, its Archify companions, and the script a maintainer runs by hand to draw them again. Add a concept only if a figure starts to carry a claim the docs do not make.
- `LICENSE`, the Apache License 2.0 text, which the README's License section states, and `CODE_OF_CONDUCT.md`, the Contributor Covenant.
- `CHANGELOG.md`, which records history. The releasing playbook cites it only for the rule on `## [Unreleased]`.
- `.editorconfig`, `.gitignore`, `.markdownlint-cli2.jsonc`, `lychee.toml` and `.github/dependabot.yml`, which configure tools.
