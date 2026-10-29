---
type: Playbook
id: https://w3id.org/ktl/federation/knowledge/playbooks/releasing
title: Releasing this domain
description: How a merge to main releases this domain and rebuilds the workspace. It names the commit types that release, the changelog rule, the release job's Environment, the two workflows the release dispatches, and the repository settings that hold main.
genre: how-to
resource: .github/workflows/semantic-release.yml
references:
  - https://w3id.org/ktl/federation/knowledge/datasets/workspace
  - https://w3id.org/ktl/federation/knowledge/playbooks/confirming-a-member-change
sources:
  - resource: .github/workflows/semantic-release.yml
  - resource: .releaserc.json
  - resource: .github/scripts/changelog-release.mjs
  - resource: .github/workflows/knowledge-release.yaml
  - resource: CONTRIBUTING.md
  - resource: SECURITY.md
generated:
  by: process:ktl-librarian
  at: "2026-10-26T18:19:07Z"
status: draft
verified:
  - by: process:ktl-librarian
    at: "2026-10-29T11:44:32Z"
---

# Overview

A merge to `main` releases this domain when its commits carry a releasing type. A domain release is what rebuilds the workspace, so a merged member change releases a minor version.

## What releases

semantic-release reads the Conventional Commits on `main`. Besides `feat` and `fix`, `.releaserc.json` releases:

- a minor version for `chore(lokf)`, the type the librarian's pull requests carry;
- a patch for `security`;
- a minor version for a breaking change, so the repository stays below 1.0.0.

The `v0.1.0` baseline tag points at the first commit, so the first release was `0.2.0`, not `1.0.0`.

A squash merge takes its commit subject from the pull request's title. So a pull request whose commits would release must carry a releasing type in its title too. The `plan` job previews every pull request into `main` with `--dry-run`. It fails a pull request whose commits would release but whose title has no releasing type.

## The changelog

Write `## [Unreleased]` in `CHANGELOG.md` as you go. `.github/scripts/changelog-release.mjs` refuses a release whose Unreleased section is empty. When a release runs, the script renames that section to `## [<version>] - <date>`, uses its text as the release notes, and opens an empty `## [Unreleased]` above it.

The librarian cannot write the changelog. A person adds the line for a confirmed member change, as [Confirming a member change](confirming-a-member-change.md) says.

## The release job

The `release` job runs only on a push to `main`, in the `release` GitHub Environment. It commits the promoted changelog, tags `vX.Y.Z` and publishes the GitHub Release. A release made with the default `GITHUB_TOKEN` starts no workflow, so the job then dispatches two workflows for the tag:

- `knowledge-release.yaml`, once `KNOWLEDGE_RELEASE_ENABLED` is `true`. It attaches the bundle to the release as a zip, and the domain schema beside it.
- `knowledge-federation.yaml`, once `KNOWLEDGE_FEDERATION_ENABLED` is `true`. It rebuilds [the workspace](../datasets/workspace.md).

## What holds `main`

Configure required reviewers on the `release` Environment, under Settings → Environments, or every qualifying merge releases unattended. A branch rule that requires pull requests or signed commits would reject the release job's push to `main`.

`SECURITY.md` names three repository settings that hold `main` instead. Nothing in CI can assert them:

- required reviewers on the `release` Environment;
- a rule blocking deletion and force-pushes on `main`;
- secret scanning with push protection.
