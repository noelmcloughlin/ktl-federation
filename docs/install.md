# Install

This page is for anyone who confirms a member change or admits a new member. [Confirming a member change](curation.md) has the steps that follow it.

## Quick start

You need [uv](https://docs.astral.sh/uv/) and [just](https://github.com/casey/just) for the checks, and git set to sign your commits.

1. Clone the repository and install the bundle's tools:

   ```bash
   git clone https://github.com/noelmcloughlin/ktl-federation.git
   cd ktl-federation/.lokf && just lokf-install && just lokf-check-refs
   ```

2. Install ktl-curator into your agent. It installs for GitHub Copilot unless you add `--agent claude-code` or `--agent codex`. [KTL's install page](https://w3id.org/ktl/docs/install/) has every other route.

   ```bash
   uvx ktl skills install --scope user --skill ktl-curator
   ```

3. Add your public key to `.lokf/curators/` as `<login>.asc` (GPG) or `<login>.pub` (SSH), where `<login>` is your forge login. Add it in a change of its own first: the provenance check refuses a change that adds a person's key together with that person's confirmation.

ktl-curator records each answer under your forge login. [Its page in KTL's bundle](https://w3id.org/ktl/knowledge/playbooks/ktl-curator-skill) says where it reads that login on GitHub, GitLab and any other forge.

## In Obsidian

The KTL Curator plugin does ktl-curator's work in Obsidian. List `Domain`, `MemberBundle` and `MemberDomain` under *Settings → Type vocabulary → Known LOKF types* in both KTL Curator and KTL Registrar, the same list in each. They are the classes of this host's domain schema, `.lokf/schema/domain.yaml`, which neither plugin can read because it sits outside the `knowledge_bundle` vault.
