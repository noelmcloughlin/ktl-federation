---
type: MemberBundle
id: https://w3id.org/ktl/federation/knowledge/members/linkml-sidecar
genre: reference
title: schema-sidecar Knowledge Bundle
description: The bundle of the lmodel/schema-sidecar repository as released at v0.6.0 on 2026-11-15.
resource: https://github.com/lmodel/schema-sidecar/releases/tag/v0.6.0
base_iri: https://w3id.org/lmodel/schema-sidecar/knowledge/
version: v0.6.0
release: https://github.com/lmodel/schema-sidecar/releases/tag/v0.6.0
distribution:
  - name: knowledge-v0.6.0-schema-sidecar.zip
    access_url: https://github.com/lmodel/schema-sidecar/releases/download/v0.6.0/knowledge-v0.6.0-schema-sidecar.zip
    media_type: application/zip
    checksum:
      algorithm: sha256
      checksum_value: 7d9e4c7f8402de0af219bfee3784daa5f0cd37dd70e9a797db464b6790634f03
isPartOf:
  - https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
generated:
  by: process:knowledge-federate
  at: "2026-11-15T00:31:03Z"
verified:
  - by: human:noelmcloughlin
    at: "2026-10-21T23:19:11Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T17:13:13Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T18:29:04Z"
  - by: human:noelmcloughlin
    at: "2026-10-29T11:28:13Z"
    revision: W/"86d3df74bb848e94e2e134f7de08a0a3"
stale_after: 2027-04-26
status: draft
---

# Overview

This member is the knowledge bundle of [lmodel/schema-sidecar](https://github.com/lmodel/schema-sidecar). The description in its own index reads "Two Agent Skills that give a code repository a LinkML data model as a sidecar: linkml-sidecar installs a hidden .linkml/ project from linkml-project-copier without touching the host's build, and linkml-author turns its dummy schema into the real model and keeps it generated, documented and tested." It was released at v0.6.0 on 2026-11-15, and the release workflow attached the bundle as `knowledge-v0.6.0-schema-sidecar.zip`, with a `.sha256` file and a build attestation. Its concepts are in the namespace `https://w3id.org/lmodel/schema-sidecar/knowledge/`.

## Open questions

- 2026-11-02, process:knowledge-federate: noelmcloughlin/linkml-sidecar released v0.4.0 after the confirmed v0.3.2; does this member move to it?
- 2026-11-09, process:knowledge-federate: noelmcloughlin/linkml-sidecar released v0.5.1 after v0.4.0; does this member move to it?
- 2026-11-15, process:knowledge-federate: lmodel/schema-sidecar released v0.6.0 after v0.5.1; does this member move to it? Its namespace moves from <https://w3id.org/ktl/linkml-sidecar/knowledge/> to <https://w3id.org/lmodel/schema-sidecar/knowledge/>, so each of its concepts has a new IRI, and the gate counts a link into the old one as unowned. Before confirming, check that the new namespace belongs to this member.
