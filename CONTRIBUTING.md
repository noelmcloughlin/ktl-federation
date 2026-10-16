# Contributing to ktl-federation

*This file is a checklist, not a design log. Each rule is a line or two that links to where its reasoning lives: a concept, a workflow header, or a page in the skills repository.*

Thanks for your interest in the Knowledge Trust Ladder (KTL) federation.

## What this repository is

The top domain of the KTL federation: a thin [LOKF](https://lokf.nolan-nichols.com) knowledge bundle whose concepts are the knowledge bundles the federation admits, each named by one released zip and its checksum, and the workspace built from those releases. The design is [the KTL context layer page](https://noelmcloughlin.github.io/knowledge-trust-ladder/docs/context-layer/).

| Path | Holds |
| --- | --- |
| `.lokf/knowledge/` | The domain bundle: `domains/`, `members/`, `policies/`. |
| `.lokf/domain.yaml` | The domain schema: `Domain`, `MemberBundle`, `ReleaseDistribution` over LOKF core. |
| `.lokf/scripts/`, `.github/workflows/` | Copies of the KTL sidecar's templates. Edit them upstream, never here. |
| `website/` | The site, from the ktl-website templates; `site.config.mjs` is this repository's own. |

## Development setup

[uv](https://docs.astral.sh/uv/) and [just](https://github.com/casey/just) are required; Node.js 24 for the website.

```bash
git clone https://github.com/noelmcloughlin/ktl-federation.git
cd ktl-federation/.lokf && just lokf-install && just lokf-check-refs
```

The agent skills that maintain the bundle come from [knowledge-trust-ladder](https://github.com/noelmcloughlin/knowledge-trust-ladder), **installed, never committed**:

```bash
npx skills add noelmcloughlin/knowledge-trust-ladder --skill ktl-curator --yes
```

## Before opening a pull request

- **A member names one release**, the newest that carries a `knowledge-*.zip`; its `checksum` is the digest in that release's `.sha256`. [The federation policy](.lokf/knowledge/policies/federation.md) says what admits a bundle.
- **A confirmation is a person's own act.** Record it with ktl-curator, in a signed commit; the registrar's `provenance` job backs each `human:` event with that person's signature or approval. No agent writes one.
- **Nothing is copied from a member.** The domain names releases; the workspace is built from them.
- **Run the gate's two checks**: `cd .lokf && just lokf-check-refs` and `bash scripts/knowledge-conventions.sh knowledge`.
- **Sidecar files are copies.** When the skills release moves, copy `.lokf/scripts/`, `.lokf/m365/` and the `knowledge-*.yaml` workflows from that release's templates in one pull request, and `.lokf/lokf.yaml` with them.
- **Lint as CI does**: markdownlint against `.markdownlint-cli2.jsonc`, lychee against `lychee.toml`, actionlint and ShellCheck over the workflows and scripts.
- **If your change alters behaviour**, add an entry under `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md).

## Code of conduct

Participation here is covered by the [Contributor Covenant](CODE_OF_CONDUCT.md).

## Using AI tools

AI assistance is welcome; [AI_COVENANT.md](AI_COVENANT.md) sets the rules, for people and the scheduled librarian alike. You are the author of what you submit.

## Releasing (maintainers)

- Write `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md) as you go; the release job refuses an empty one.
- A domain release is what rebuilds the workspace, so `.releaserc.json` releases a minor version for `chore(lokf)`, the type the librarian's pull requests carry, as well as for `feat:`, `fix:` and `security:`. A pull request that would release must carry a releasing type in its title, since a squash merge takes its subject from it.
- On merge, [`semantic-release.yml`](.github/workflows/semantic-release.yml) promotes the changelog, tags `vX.Y.Z`, publishes the GitHub Release, and dispatches `knowledge-release.yaml` for the tag once `KNOWLEDGE_RELEASE_ENABLED` is `true`.
- Below 1.0.0: the `v0.1.0` baseline tag sits on the first commit, so the first release is `0.2.0`; `.releaserc.json` maps a breaking change to `minor`.
- The release job runs behind the `release` GitHub Environment; configure required reviewers on it in Settings → Environments, or every qualifying merge releases unattended. A branch rule requiring pull requests or signed commits would reject the release job's own push to `main`; [SECURITY.md](SECURITY.md) says what holds `main` instead.

## License

By contributing, you agree that your contributions are licensed under the [Apache License 2.0](LICENSE). The knowledge bundle is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), as its `index.md` says.
