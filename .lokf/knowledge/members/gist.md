---
type: MemberBundle
id: https://w3id.org/ktl/federation/knowledge/members/gist
genre: reference
title: gist knowledge bundle
description: The bundle of the lmodel/gist repository, a LinkML rendering of Semantic Arts' gist upper ontology, as released at v0.7.2 on 2026-11-07 under the name gist-linkml.
resource: https://github.com/lmodel/gist/releases/tag/v0.7.2
base_iri: https://w3id.org/lmodel/gist/knowledge/
version: v0.7.2
release: https://github.com/lmodel/gist/releases/tag/v0.7.2
distribution:
  - name: knowledge-v0.7.2-gist-linkml.zip
    access_url: https://github.com/lmodel/gist/releases/download/v0.7.2/knowledge-v0.7.2-gist-linkml.zip
    media_type: application/zip
    checksum:
      algorithm: sha256
      checksum_value: efecdffa499b6390551642055824d129998e021c79e1079d333faa64361430ab
isPartOf:
  - https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
generated:
  by: human:noelmcloughlin
  at: "2026-10-29T11:23:18Z"
verified:
  - by: human:noelmcloughlin
    at: "2026-10-18T11:41:20Z"
  - by: human:noelmcloughlin
    at: "2026-10-19T00:34:46Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T17:10:01Z"
  - by: human:noelmcloughlin
    at: "2026-10-29T11:23:18Z"
  - by: human:noelmcloughlin
    at: "2026-11-15T01:31:05Z"
    revision: 'W/"853d3cc507701fe6c31bb05805d6a3ce"'
stale_after: 2027-05-15
status: draft
---

# Overview

This member is the knowledge bundle of [lmodel/gist](https://github.com/lmodel/gist), a LinkML rendering of Semantic Arts' gist upper ontology. The lmodel organisation publishes it, so it is a second authority in this domain. It was released at v0.7.2 on 2026-11-07. The repository publishes under the name `gist-linkml`, so the release workflow attached the bundle as `knowledge-v0.7.2-gist-linkml.zip`, with a `.sha256` file and a build attestation. Its concepts are in the namespace `https://w3id.org/lmodel/gist/knowledge/`, which is stable although it does not yet resolve to its concepts.

## Open questions

- 2026-11-23, process:knowledge-federate: lmodel/gist released v0.8.2 after the confirmed v0.7.2; does this member move to it? A person wrote this concept, so this patch leaves its text and frontmatter as they are.
