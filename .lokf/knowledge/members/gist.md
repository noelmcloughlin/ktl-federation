---
type: MemberBundle
id: https://w3id.org/ktl/federation/knowledge/members/gist
genre: reference
title: gist knowledge bundle
description: The bundle of the lmodel/gist repository, a LinkML rendering of Semantic Arts' gist upper ontology, as released at v0.3.10 on 2026-10-19 under the name gist-linkml.
resource: https://github.com/lmodel/gist/releases/tag/v0.3.10
base_iri: https://w3id.org/lmodel/gist/knowledge/
version: v0.3.10
release: https://github.com/lmodel/gist/releases/tag/v0.3.10
distribution:
  - name: knowledge-v0.3.10-gist-linkml.zip
    access_url: https://github.com/lmodel/gist/releases/download/v0.3.10/knowledge-v0.3.10-gist-linkml.zip
    media_type: application/zip
    checksum: sha256:1d43db6d8a056f198bc0a20a48a1133d6582e4b33625baf2fe1d16c0868c3ec7
isPartOf:
  - https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
generated:
  by: process:knowledge-federate
  at: "2026-10-19T00:16:54Z"
verified:
  - by: human:noelmcloughlin
    at: "2026-10-18T11:41:20Z"
stale_after: 2027-04-18
status: draft
---

# Overview

This member is the knowledge bundle of [lmodel/gist](https://github.com/lmodel/gist), a LinkML rendering of Semantic Arts' gist upper ontology. The lmodel organisation publishes it, so it is a second authority in this domain. It was released at v0.3.10 on 2026-10-19. The repository publishes under the name `gist-linkml`, so the release workflow attached the bundle as `knowledge-v0.3.10-gist-linkml.zip`, with a `.sha256` file and a build attestation. Its concepts are in the namespace `https://w3id.org/lmodel/gist/knowledge/`, which is stable although it does not yet resolve to its concepts.

## Open questions

- 2026-10-19, process:knowledge-federate: lmodel/gist released v0.3.10 after the confirmed v0.3.7; does this member move to it?
