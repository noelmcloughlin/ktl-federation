# Contributing to ktl-federation

*This file is a checklist, not a design log. Each rule is a line or two that links to where its reasoning lives: a concept, a workflow header, or a page in the skills repository.*

Thanks for your interest in the Knowledge Trust Ladder (KTL) federation.

## What this repository is

This repository is the domain of the KTL federation: a thin [LOKF](https://lokf.nolan-nichols.com) knowledge bundle whose concepts are the knowledge bundles the federation admits, each named by one released zip and its checksum. The workspace is built from those releases. The design is KTL's [context layer](https://w3id.org/ktl/docs/context-layer/) and [federation](https://w3id.org/ktl/docs/federation/) pages.

| Path | Holds |
| --- | --- |
| `.lokf/knowledge/` | The domain bundle: `domains/`, `members/`, `policies/`. |
| `.lokf/domain.yaml` | The domain schema: `Domain`, `MemberBundle`, `MemberDomain`, `ReleaseDistribution` over LOKF core. |
| `.lokf/scripts/`, `.github/workflows/` | Copies of the KTL sidecar's templates. Edit them upstream, never here. |
| `website/` | The site, from the ktl-website templates; `site.config.mjs` is this repository's own. |

## Development setup

You need [uv](https://docs.astral.sh/uv/) and [just](https://github.com/casey/just), and Node.js 24 for the website.

```bash
git clone https://github.com/noelmcloughlin/ktl-federation.git
cd ktl-federation/.lokf && just lokf-install && just lokf-check-refs
```

The agent skills that maintain the bundle come from [knowledge-trust-ladder](https://github.com/noelmcloughlin/knowledge-trust-ladder), **installed, never committed**:

```bash
npx skills add noelmcloughlin/knowledge-trust-ladder --skill ktl-curator --yes
```

Where a company proxy or an internal npm registry blocks `npx`, the GitHub CLI installs it instead: `gh skill install noelmcloughlin/knowledge-trust-ladder ktl-curator --scope user --agent <yours>`. The [install page](https://w3id.org/ktl/docs/install/) has every route.

## Before opening a pull request

- **A member names one release**, the newest that carries a `knowledge-*.zip`. Its `checksum` is the digest in that release's `.sha256`. [The federation policy](.lokf/knowledge/policies/federation.md) says what admits a bundle.
- **A confirmation is a person's own act.** Record it with ktl-curator, in a signed commit. The registrar's `provenance` job backs each `human:` event with that person's signature or approval, and off GitHub `knowledge-provenance.sh` checks the signature against `.lokf/curators/`. No agent writes a confirmation. [Confirming a member change](docs/curation.md) gives the steps on any forge.
- **Nothing is copied from a member.** The domain names releases, and the workspace is built from them.
- **Run the gate's two checks**: `cd .lokf && just lokf-check-refs` and `bash scripts/knowledge-conventions.sh knowledge`.
- **Sidecar files are copies.** Each week `knowledge-sync.yaml` checks the newest skills release and, when this host is behind, opens one pull request that copies its templates over `.lokf/scripts/`, `.lokf/m365/` and the `knowledge-*.yaml` workflows. Change them in KTL, never here. The sync leaves `.lokf/lokf.yaml` alone: when the `lokf` toolkit's version changes, copy it again from the installed package in the same pull request.
- **Lint as CI does**: [`lint-and-docs.yaml`](.github/workflows/lint-and-docs.yaml) runs markdownlint against `.markdownlint-cli2.jsonc`, lychee against `lychee.toml` and codespell over every `*.md`, and actionlint and ShellCheck over the workflows and scripts.
- **If your change alters behaviour**, add an entry under `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md).

## Code of conduct

Participation here is covered by the [Contributor Covenant](CODE_OF_CONDUCT.md).

## Using AI tools

AI assistance is welcome. [AI_COVENANT.md](AI_COVENANT.md) sets the rules, for people and the scheduled librarian alike. You are the author of what you submit.

## Releasing (maintainers)

- Write `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md) as you go. The release job refuses an empty one.
- `.releaserc.json` releases a minor version for `chore(lokf)`, the type the librarian's pull requests carry, as well as for `feat:`, `fix:` and `security:`, because a domain release is what rebuilds the workspace. A pull request that would release must carry a releasing type in its title, since a squash merge takes its subject from it.
- On merge, [`semantic-release.yml`](.github/workflows/semantic-release.yml) promotes the changelog, tags `vX.Y.Z`, publishes the GitHub Release, and dispatches `knowledge-release.yaml` for the tag once `KNOWLEDGE_RELEASE_ENABLED` is `true`, and `knowledge-federation.yaml`, which rebuilds the workspace, once `KNOWLEDGE_FEDERATION_ENABLED` is `true`.
- Below 1.0.0: the `v0.1.0` baseline tag points at the first commit, so the first release is `0.2.0`. `.releaserc.json` maps a breaking change to `minor`.
- The release job runs in the `release` GitHub Environment. Configure required reviewers on it in Settings → Environments, or every qualifying merge releases unattended. A branch rule requiring pull requests or signed commits would reject the release job's push to `main`. [SECURITY.md](SECURITY.md) says what holds `main` instead.

## License

By contributing, you agree that your contributions are licensed under the [Apache License 2.0](LICENSE). The knowledge bundle is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), as its `index.md` says.
