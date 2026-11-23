---
type: MemberBundle
id: https://w3id.org/ktl/federation/knowledge/members/linkml-sidecar
genre: reference
title: schema-sidecar Knowledge Bundle
description: The bundle of the lmodel/schema-sidecar repository as released at v0.7.0 on 2026-11-16.
resource: https://github.com/lmodel/schema-sidecar/releases/tag/v0.7.0
base_iri: https://w3id.org/lmodel/schema-sidecar/knowledge/
version: v0.7.0
release: https://github.com/lmodel/schema-sidecar/releases/tag/v0.7.0
distribution:
  - name: knowledge-v0.7.0-schema-sidecar.zip
    access_url: https://github.com/lmodel/schema-sidecar/releases/download/v0.7.0/knowledge-v0.7.0-schema-sidecar.zip
    media_type: application/zip
    checksum:
      algorithm: sha256
      checksum_value: a59f2bf0791edf1755cf21b7b8e7caa408c75a125157555b744a94b5f34b3eb0
isPartOf:
  - https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
generated:
  by: process:knowledge-federate
  at: "2026-11-23T15:48:37Z"
verified:
  - by: human:noelmcloughlin
    at: "2026-10-21T23:19:11Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T17:13:13Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T18:29:04Z"
  - by: human:noelmcloughlin
    at: "2026-10-29T11:28:13Z"
    revision: 'W/"86d3df74bb848e94e2e134f7de08a0a3"'
  - by: human:noelmcloughlin
    at: "2026-11-18T22:55:23Z"
    revision: 'W/"3c5e9a92c28460c3b16cece7faa1ac1e"'
stale_after: 2027-05-18
status: draft
---

# Overview

This member is the knowledge bundle of [lmodel/schema-sidecar](https://github.com/lmodel/schema-sidecar). The description in its own index reads "Two Agent Skills that give a code repository a LinkML data model as a sidecar: linkml-sidecar installs a hidden .linkml/ project from linkml-project-copier without touching the host's build, and linkml-author turns its dummy schema into the real model and keeps it generated, documented and tested." It was released at v0.7.0 on 2026-11-16, and the release workflow attached the bundle as `knowledge-v0.7.0-schema-sidecar.zip`, with a `.sha256` file and a build attestation. Its concepts are in the namespace `https://w3id.org/lmodel/schema-sidecar/knowledge/`.

## Open questions

- 2026-11-23, process:knowledge-federate: lmodel/schema-sidecar released v0.7.0 after the confirmed v0.6.0; does this member move to it?
