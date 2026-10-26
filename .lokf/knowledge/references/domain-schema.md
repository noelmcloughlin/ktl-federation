---
type: Reference
id: https://w3id.org/ktl/federation/knowledge/references/domain-schema
genre: reference
title: The domain schema
description: The LinkML schema in .lokf/domain.yaml that adds Domain, MemberBundle, MemberDomain and ReleaseDistribution over LOKF core, so lokf validate checks a member's namespace, release and checksum. Its namespace is KTL's, and a host that needs more classes imports it.
resource: .lokf/domain.yaml
relatedTo:
  - https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
sources:
  - resource: .lokf/domain.yaml
  - resource: docs/architecture.md
generated:
  by: process:ktl-librarian
  at: "2026-10-26T18:11:40Z"
status: draft
---

# Overview

`.lokf/domain.yaml` is this host's domain schema, a LinkML file that `lokf validate` reads beside LOKF core. The `schema := "domain.yaml"` line of `.lokf/justfile` names it. ktl-sidecar lays it down on a host whose bundle is a domain, beside a pinned copy of `lokf.yaml`.

## The four classes

- `Domain` is a `Dataset` that is a `dcat:Catalog` of bundles. It carries `unowned_targets`, `max_depth`, `sensitivity` and `private_addresses`, the settings the federation build reads. [The domain concept](../domains/ktl-federation.md) says what each one means and what this domain sets.
- `MemberBundle` is a `Dataset` that names one released bundle. It requires a `base_iri` and a `distribution`, and carries the `release` page and a `sensitivity`.
- `MemberDomain` is a `MemberBundle` whose bundle is itself a domain, so a `dcat:Catalog` in turn.
- `ReleaseDistribution` is LOKF's `Distribution` plus the required `checksum` of the file it names: `sha256:` and 64 lowercase hexadecimal digits.

So `lokf validate` checks a member's namespace, release and checksum.

## Its namespace

The schema's namespace is KTL's, `https://w3id.org/ktl/schema/domain`, so every domain host shares one meaning for these classes. A host that needs more writes a schema of its own that imports this one.

Neither Obsidian plugin can read the file, because it sits outside the `knowledge_bundle` vault. The curator's [domain bundle page](https://w3id.org/ktl/knowledge/playbooks/domain-bundle#the-four-concept-types) in KTL's bundle describes each class.
