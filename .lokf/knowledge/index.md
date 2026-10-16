---
lokf_version: "0.2"
okf_version: "0.2"
base_iri: https://w3id.org/ktl/federation/knowledge/
context: https://w3id.org/lokf/context.jsonld
title: KTL Federation Knowledge Bundle
description: "The top domain of the Knowledge Trust Ladder federation: the knowledge bundles it federates, each named by its released zip and confirmed by a person, and the workspace built from them."
license: https://creativecommons.org/licenses/by/4.0/
publisher:
  type: Person
  id: https://w3id.org/ktl/federation/knowledge/person/noel-mcloughlin
  name: Noel McLoughlin
---

# KTL Federation Knowledge Bundle

This bundle is the top domain of the Knowledge Trust Ladder (KTL) federation. Its concepts are the knowledge bundles the federation admits, each named by one released zip and that zip's checksum; the domain that admits them; and the policy that says what admission requires and what the build does with a link no member owns. A person confirms each membership. The workspace, the graph a reader queries, is built from the releases these concepts name, never from a copy of them. The design is on [the KTL context layer page](https://noelmcloughlin.github.io/knowledge-trust-ladder/docs/context-layer/).

# Domains

* [The top domain](domains/top.md) - The domain that bounds the KTL federation's workspace. It admits knowledge bundles by release, and its gate policy fails the build on a link no member owns.

# Policies

* [Federation policy](policies/federation.md) - What admits a knowledge bundle to this domain, which release a member names, and what the workspace build does with a cross-bundle target no member owns.

# Members

* [Knowledge Trust Ladder knowledge bundle](members/knowledge-trust-ladder.md) - The bundle of the knowledge-trust-ladder repository, which publishes the KTL skills, as released at v0.43.0 on 2026-10-15.
* [AI-LinkMO knowledge bundle](members/ai-linkmo.md) - The bundle of the ai-linkmo repository, a reference implementation of operational AI governance over open AI-governance data, as released at v0.3.2 on 2026-10-14.
* [gist knowledge bundle](members/gist.md) - The bundle of the lmodel/gist repository, a LinkML rendering of Semantic Arts' gist upper ontology, as released at v0.3.3 on 2026-10-15 under the name gist-linkml.
