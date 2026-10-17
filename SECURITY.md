# Security Policy

*This file is a policy, not a threat model. It says how to report, what executes here, and what holds each surface. Each is a line or two that links to where the reasoning lives: a workflow header, or the shared [threat model](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/main/docs/threat-model.md).*

## Reporting a vulnerability

Use GitHub's [private vulnerability reporting](https://github.com/noelmcloughlin/ktl-federation/security/advisories/new), not a public issue or a pull request. Say which file is affected, how it is exploitable, and whether it reaches a reader of the workspace or only this repository's automation. One person maintains this repository: expect a first reply in days, not hours, and no bounty.

## Supported versions

Only the latest release receives fixes; a security fix is released as a patch release and is noted in [CHANGELOG.md](CHANGELOG.md).

## What this repository ships

A knowledge bundle of Markdown files, a LinkML schema, and the workspace built from other repositories' released bundles. The workspace build downloads only the zips the member concepts name, checks each against the checksum a person confirmed, verifies its build attestation where the forge recorded one. It refuses a zip that holds a symlink or a path outside its root. A member's release is read, never run.

## What executes here

| Surface | What holds it |
| --- | --- |
| `knowledge-registrar.yaml` on any pull request that touches `.lokf/`: the validator, the conventions and the provenance gate | Read-only jobs with `persist-credentials: false`; `uv sync --locked` installs only what `.lokf/uv.lock` pins. A `human:` confirmation must be backed by that person's signature or approval. [Human attribution](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/main/docs/threat-model.md#human-attribution-human-is-a-claim-not-a-credential). |
| `knowledge-librarian.yaml` and `.lokf/scripts/`, copies of the `ktl-sidecar` template | Here the agent is a script that reads members' releases; it runs in a job that never meets a write token, and the `publish` job confines the patch to the bundle and refuses a `human:` claim. A person merges the pull request. Inert until `KNOWLEDGE_LIBRARIAN_ENABLED` is `true`. |
| `knowledge-release.yaml`, which attaches the bundle to a release | Inert until dispatched or `KNOWLEDGE_RELEASE_ENABLED` is `true`; only its `attach` job, which runs no third-party packages, can write. |
| `knowledge-website.yaml`, which builds the site | Builds on every pull request under a read token; deploys nothing, since the federation build is this repository's one Pages deployer. |
| `semantic-release.yml`, which pushes a changelog commit and tag to `main` | Runs only on a push to `main`, in the `release` Environment, installing its pinned tools with `--ignore-scripts`. [Repository hardening](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/main/docs/threat-model.md#repository-hardening). |
| `README.md`, `llms.txt` and the bundle, read by agents | Content, never instructions. A member concept names a release; it carries no text from the member. |

Every workflow declares `permissions: {}` at the top, pins its actions to commit SHAs that Dependabot keeps current, and runs harden-runner in audit mode. Three things are repository settings, not files: required reviewers on the `release` Environment, a rule blocking deletion and force-pushes on `main`, and secret scanning with push protection. Nothing in CI can assert them, so keeping them on is the maintainer's job.

## Not covered

- What a member's own bundle claims. Each member keeps its own gate and its own labels; report a problem in one to its repository.
- The LOKF toolkit: report it to [lokf](https://github.com/nicholsn/lokf/security).
- A compromised runner, upstream action or agent harness: this is a baseline, not a sandbox.
