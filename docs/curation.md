# Confirming a member change

A member's new release, or a new member, joins the workspace when the pull request that names it merges, since the build takes every member concept on the default branch. A person's confirmation records that the member belongs, and the health line shows each member no person has confirmed since it moved. This page gives the steps. They work on GitHub, on another forge, and in a plain git clone. Where this page says pull request, GitLab says merge request.

## What you need

- ktl-curator in your agent, from the install lines in [CONTRIBUTING](../CONTRIBUTING.md#development-setup), or the KTL Curator plugin in Obsidian.
- Git set to sign your commits, and your public key in `.lokf/curators/` as `<login>.asc` (GPG) or `<login>.pub` (SSH), where `<login>` is your forge login. Add the key in a change of its own first: the provenance check refuses a change that adds a person's key together with that person's confirmation.
- [uv](https://docs.astral.sh/uv/) and [just](https://github.com/casey/just), for the checks.

ktl-curator records each answer under your forge login. [Its page in KTL's bundle](https://w3id.org/ktl/knowledge/playbooks/ktl-curator-skill) says where it reads that login on GitHub, GitLab and any other forge.

## Confirm the change

1. Fetch the branch that holds the change: `git fetch origin`, then `git switch <branch>`. On GitHub, `gh pr checkout <number>` does both; on GitLab, `glab mr checkout <number>` does.
2. Start your agent in this repository and run `/ktl-curator`. Ask it to record your answers on this branch, not in a new pull request. For each member it shows the release, the checksum and the attestation first, then what the concept claims. You answer each one: confirm, send back or later. In Obsidian, open `knowledge_bundle` as a vault and answer on the KTL Curator plugin's review card instead.
3. Add a line under `## [Unreleased]` in [CHANGELOG.md](../CHANGELOG.md) that names each member and its new version. The librarian cannot write to the changelog, and the release refuses an empty entry.
4. Commit, signed, and push to the same branch.
5. Check the branch before you merge. On GitHub, your push starts the registrar's gate and the federation `check` job. Neither runs before then, because GitHub starts no workflow for a pull request the librarian's job token opened. Anywhere else, run the same checks from the repository's root:

   ```bash
   (cd .lokf && just lokf-check-refs && bash scripts/knowledge-conventions.sh knowledge)
   bash .lokf/scripts/knowledge-provenance.sh origin/main
   uv run --project .lokf .lokf/scripts/knowledge-federate.py build --verify-only
   ```

   The first line checks that every record is well formed. The second checks that a key on file signed each confirmation. The third fetches each member's zip and checks it against the checksum its concept names.

6. Merge so that the commit on `main` keeps the `chore(lokf)` subject. With a squash merge, keep the pull request's title. On this host the merge releases the domain, and the release rebuilds the workspace.

## Add a member

The members script reads releases from GitHub. For a bundle released there, draft its member concept on a new branch, open a pull request, and confirm it as above:

```bash
uv run --project .lokf .lokf/scripts/knowledge-federate.py members --add <owner>/<repo>
bash .lokf/scripts/knowledge-apply.sh
```

When the bundle is itself a domain, the script drafts a `MemberDomain`. Confirming it attests that the domain belongs and who answers for it, not what its members say.

The script leaves a member released anywhere else as it is, so a person writes and moves that member concept by hand, from the worked example on the curator's [domain bundle page](https://w3id.org/ktl/knowledge/playbooks/domain-bundle#the-worked-example). The build fetches its zip from any `https` address and checks it against the `checksum`. It verifies a build attestation only for a GitHub release.
