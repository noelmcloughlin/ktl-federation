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

* [Federation policy](policies/federation.md) - What admits a knowledge bundle to this domain, what a member adds, which release a member names, and what the build does with a target no member owns or a bundle two domains name.

# Members

* [Knowledge Trust Ladder knowledge bundle](members/knowledge-trust-ladder.md) - The bundle of the knowledge-trust-ladder repository, which publishes the KTL skills, as released at v0.50.1 on 2026-10-18.
* [AI-LinkMO knowledge bundle](members/ai-linkmo.md) - The bundle of the ai-linkmo repository, a reference implementation of operational AI governance over open AI-governance data, as released at v0.4.9 on 2026-10-17.
* [gist knowledge bundle](members/gist.md) - The bundle of the lmodel/gist repository, a LinkML rendering of Semantic Arts' gist upper ontology, as released at v0.3.7 on 2026-10-17 under the name gist-linkml.
* [KTL Curator knowledge bundle](members/obsidian-ktl-curator.md) - The bundle of the noelmcloughlin/obsidian-ktl-curator repository as released at 1.6.4 on 2026-10-17.
* [KTL Registrar knowledge bundle](members/obsidian-ktl-registrar.md) - The bundle of the noelmcloughlin/obsidian-ktl-registrar repository as released at 1.7.5 on 2026-10-17.
