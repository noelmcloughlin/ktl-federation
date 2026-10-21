# Confirming a member change

A member's new release changes nothing here until a person confirms the member concept that names it, and a new member joins only when a person confirms it. This page gives the steps. They work on GitHub, on another forge, and in a plain git clone. Where this page says pull request, GitLab says merge request.

## What you need

- ktl-curator in your agent, from the install lines in [CONTRIBUTING](../CONTRIBUTING.md#development-setup), or the KTL Curator plugin in Obsidian. In Obsidian, list `Domain`, `MemberBundle` and `MemberDomain` under *Settings → Type vocabulary → Known LOKF types* in both KTL Curator and KTL Registrar, the same list in each. They are the classes of this host's domain schema, `.lokf/domain.yaml`, which neither plugin can read because it sits outside the `knowledge_bundle` vault.
- Git set to sign your commits, and your public key in `.lokf/curators/` as `<login>.asc` (GPG) or `<login>.pub` (SSH), where `<login>` is your forge login. Add the key in a change of its own first: the provenance check refuses a change that adds a person's key together with that person's confirmation.
- [uv](https://docs.astral.sh/uv/) and [just](https://github.com/casey/just), for the checks.

ktl-curator records each answer under your forge login. [Its page in KTL's bundle](https://w3id.org/ktl/knowledge/playbooks/ktl-curator-skill) says where it reads that login on GitHub, GitLab and any other forge.

## Confirm the change

1. Fetch the branch that holds the change: `git fetch origin`, then `git switch <branch>`. On GitHub, `gh pr checkout <number>` does both; on GitLab, `glab mr checkout <number>` does.
2. Start your agent in this repository and run `/ktl-curator`. Ask it to record your answers on this branch, not in a new pull request. For each member it shows the release, the checksum and the attestation first, then what the concept claims. You answer each one: confirm, send back or later. In Obsidian, open `knowledge_bundle` as a vault and answer on the KTL Curator plugin's review card instead.
3. Add a line under `## [Unreleased]` in [CHANGELOG.md](../CHANGELOG.md) that names each member and its new version. The librarian cannot write to the changelog, and the release refuses an empty entry.
4. Commit your verdicts on their own, signed, and push to the same branch. Never amend them into the commit that changed the members: the gate fails a commit that records a confirmation and also changes what the concept says.
5. Check the branch before you merge. On GitHub, your push starts the registrar's gate and the federation `check` job. Neither runs before then, because GitHub starts no workflow for a pull request the librarian's job token opened. Anywhere else, run the same checks from the repository's root:

   ```bash
   (cd .lokf && just lokf-check-refs && bash scripts/knowledge-conventions.sh knowledge --since "$(git merge-base origin/main HEAD)")
   bash .lokf/scripts/knowledge-provenance.sh origin/main
   uv run --project .lokf .lokf/scripts/knowledge-federate.py build --verify-only
   ```

   The first line checks that every record is well formed, and that each commit recording a confirmation changes nothing else. Without `--since`, it skips the commit check. The second line checks that a key on file signed each confirmation. The third line fetches each member's zip and checks it against the checksum its concept names. It then runs the gate as the next release build would: a link into a namespace no member owns, or into a member no person has confirmed yet, fails here, before the merge. Its output names each member that build would leave out or build at an earlier release.

6. Merge so that the commit on `main` keeps the `chore(lokf)` subject. With a squash merge, keep the pull request's title. On this host the merge releases the domain, and the release rebuilds the workspace.

## Add a member

The members script reads releases from GitHub. For a bundle released there, draft its member concept on a new branch, open a pull request, and confirm it as above:

```bash
uv run --project .lokf .lokf/scripts/knowledge-federate.py members --add <owner>/<repo>
bash .lokf/scripts/knowledge-apply.sh
```

When the bundle is itself a domain, the script drafts a `MemberDomain`. Confirming it attests that the domain belongs and who answers for it, not what its members say.

The script leaves a member released outside GitHub as it is, so a person writes and moves that member concept by hand, from the worked example on the curator's [domain bundle page](https://w3id.org/ktl/knowledge/playbooks/domain-bundle#the-worked-example). The build fetches its zip from any `https` address and checks it against the `checksum`. It verifies a build attestation only for a GitHub release.
