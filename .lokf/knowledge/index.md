---
lokf_version: "0.2"
okf_version: "0.2"
base_iri: https://w3id.org/ktl/federation/knowledge/
context: https://w3id.org/lokf/context.jsonld
title: KTL Federation Knowledge Bundle
description: "The domain of the Knowledge Trust Ladder federation: the knowledge bundles it federates, each named by its released zip and confirmed by a person, and the workspace built from them."
license: https://creativecommons.org/licenses/by/4.0/
publisher:
  type: Person
  id: https://w3id.org/ktl/federation/knowledge/person/noel-mcloughlin
  name: Noel McLoughlin
---

# KTL Federation Knowledge Bundle

This bundle is the domain of the Knowledge Trust Ladder (KTL) federation. Its concepts are the knowledge bundles the federation admits, each named by one released zip and that zip's checksum; the domain that admits them; and the policy that says what admission requires and what the build does with a link no member owns. A person confirms each membership. The workspace, the graph a reader queries, is built from the releases these concepts name, never from a copy of them. The design is on [the KTL context layer page](https://noelmcloughlin.github.io/knowledge-trust-ladder/docs/context-layer/).

# Domains

* [The KTL federation domain](domains/ktl-federation.md) - The domain of the KTL federation. Its builds start here, and another domain may name it as a member. It admits knowledge bundles by release, and its gate policy fails the build on a link no member owns.

# Policies

* [Federation policy](policies/federation.md) - What admits a knowledge bundle to this domain, what a member adds, which release a member names, what a person's confirmation attests, and who arbitrates a claim across bundles. It also says what the build does with a target that names no member's concept or a bundle two domains name.

# Members

* [Knowledge Trust Ladder knowledge bundle](members/knowledge-trust-ladder.md) - The bundle of the knowledge-trust-ladder repository, which publishes the KTL skills, as released at v0.55.1 on 2026-10-22.
* [AI-LinkMO knowledge bundle](members/ai-linkmo.md) - The bundle of the ai-linkmo repository, a reference implementation of operational AI governance over open AI-governance data, as released at v0.4.10 on 2026-10-19.
* [gist knowledge bundle](members/gist.md) - The bundle of the lmodel/gist repository, a LinkML rendering of Semantic Arts' gist upper ontology, as released at v0.3.13 on 2026-10-23 under the name gist-linkml.
* [KTL Curator knowledge bundle](members/obsidian-ktl-curator.md) - The bundle of the noelmcloughlin/obsidian-ktl-curator repository as released at 1.6.9 on 2026-10-26.
* [KTL Registrar knowledge bundle](members/obsidian-ktl-registrar.md) - The bundle of the noelmcloughlin/obsidian-ktl-registrar repository as released at 1.7.10 on 2026-10-26.
* [linkml-sidecar Knowledge Bundle](members/linkml-sidecar.md) - The bundle of the noelmcloughlin/linkml-sidecar repository as released at v0.3.2 on 2026-10-26.

# Playbooks

* [Confirming a member change](playbooks/confirming-a-member-change.md) - How a person confirms a member's move to a new release, or a new member, with ktl-curator or the KTL Curator plugin. It names what you need, the steps on the change's branch, the checks to run before the merge, and how to draft a new member with the members script.
* [Knowledge sources](playbooks/knowledge-sources.md) - Map of the repository paths and outside pages this domain bundle is derived from, the concepts each yields, the files left out on purpose, and how to re-check each on a later refresh.
* [Contributing to this domain](playbooks/contributing.md) - How to set up a clone, what to check before a pull request to this domain, and the rules for AI-assisted changes. It names the gate's two checks, the lint CI runs, the sidecar copies never edited here, and the changelog entry a change in behaviour needs.
* [Releasing this domain](playbooks/releasing.md) - How a merge to main releases this domain and rebuilds the workspace. It names the commit types that release, the changelog rule, the release job's Environment, the two workflows the release dispatches, and the repository settings that hold main.
* [The knowledge website](playbooks/knowledge-website.md) - How the site at noelmcloughlin.github.io/ktl-federation is built from the bundle, the README, docs/ and the changelog, how to preview it, what to edit for each part, and why the federation workflow deploys it on this host, not the website workflow.

# Datasets

* [The KTL federation workspace](datasets/workspace.md) - The graph each release of this domain builds from its members, one named graph per bundle plus a graph for the lock. It names the build's checks, what the release's workspace zip and the site's /workspace/ folder hold, the stored queries, and the serve, mcp and Oxigraph ways to read it.

# References

* [The domain schema](references/domain-schema.md) - The LinkML schema in .lokf/domain.yaml that adds Domain, MemberBundle, MemberDomain and ReleaseDistribution over LOKF core, so lokf validate checks a member's namespace, release and checksum. Its namespace is KTL's, and a host that needs more classes imports it.
