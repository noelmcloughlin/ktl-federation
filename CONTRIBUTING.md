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
gh skill install noelmcloughlin/knowledge-trust-ladder ktl-curator --scope user --agent <yours>
npx skills add noelmcloughlin/knowledge-trust-ladder --skill ktl-curator --yes
```

Either line works; `npx` can fail behind a company proxy or an internal npm registry, and the [install page](https://w3id.org/ktl/docs/install/) has every route.

## Before opening a pull request

- **A member names one release**, the newest that carries a `knowledge-*.zip`; its `checksum` is the digest in that release's `.sha256`. [The federation policy](.lokf/knowledge/policies/federation.md) says what admits a bundle.
- **A confirmation is a person's own act.** Record it with ktl-curator, in a signed commit; the registrar's `provenance` job backs each `human:` event with that person's signature or approval. No agent writes one.
- **Nothing is copied from a member.** The domain names releases; the workspace is built from them.
- **Run the gate's two checks**: `cd .lokf && just lokf-check-refs` and `bash scripts/knowledge-conventions.sh knowledge`.
- **Sidecar files are copies.** Each week `knowledge-sync.yaml` checks the newest skills release and, when this host is behind, opens one pull request that copies its templates over `.lokf/scripts/`, `.lokf/m365/` and the `knowledge-*.yaml` workflows. Change them in Knowledge Trust Ladder, never here. The sync leaves `.lokf/lokf.yaml` alone: when the `lokf` toolkit's version moves, copy it again from the installed package in the same pull request.
- **Lint as CI does**: markdownlint against `.markdownlint-cli2.jsonc`, lychee against `lychee.toml`, actionlint and ShellCheck over the workflows and scripts.
- **If your change alters behaviour**, add an entry under `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md).

## Confirming a member change (maintainers)

The librarian opens a pull request when a member releases a newer bundle, and `members --add` drafts a new member the same way. Neither counts until a person confirms it:

1. Check out the pull request: `gh pr checkout <number>`.
2. Start your agent in this repository and run `/ktl-curator`. Ask it to record your answers on this branch, not in a new pull request. For each member it shows the release, the checksum and the attestation before what the concept claims, and you answer each one: confirm, send back or later. Without an agent, open `knowledge_bundle` as an Obsidian vault and confirm each member with the KTL Curator plugin.
3. Add a line under `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md) naming each member and its new version. The librarian writes only inside the bundle, and the release refuses an empty entry.
4. Commit, signed, and push to the same branch. GitHub runs no checks on a pull request the librarian's token opened, so your push is what starts the registrar's gate and the federation `check` job.
5. When both pass, squash-merge and keep the `chore(lokf)` title. The merge releases the domain and rebuilds the workspace.

To propose a new member, run these on a branch, then open a pull request and confirm it as above:

```bash
uv run --project .lokf .lokf/scripts/knowledge-federate.py members --add <owner>/<repo>
bash .lokf/scripts/knowledge-apply.sh
```

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
