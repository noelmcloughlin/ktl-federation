---
type: Policy
id: https://w3id.org/ktl/federation/knowledge/policies/federation
genre: reference
title: Federation policy
description: What admits a knowledge bundle to this domain, which release a member names, and what the workspace build does with a cross-bundle target no member owns.
resource: https://w3id.org/ktl/docs/federation
generated:
  by: process:ktl-librarian
  at: "2026-10-18T11:10:08Z"
status: draft
sources:
  - resource: https://w3id.org/ktl/docs/federation
  - resource: https://w3id.org/ktl/knowledge/playbooks/domain-bundle
  - resource: https://w3id.org/ktl/docs/context-layer
verified:
  - by: process:ktl-librarian
    at: "2026-10-18T11:10:08Z"
---

# Overview

## Admission

A knowledge bundle joins this domain when all four hold:

- it is released with the KTL sidecar's release workflow, so each release carries the bundle as a zip with a checksum and, on a public repository, a build attestation;
- it validates against LOKF core, or against a schema it publishes with its releases;
- its `base_iri` is stable and lies under an authority its publisher controls;
- it has one accountable owner, who answers for what it claims.

The registry refuses a `base_iri` that nests inside another member's, so no two members' namespaces nest.

A member concept names one release, the newest that carries a zip. A release whose bundle did not change carries no zip.

## The gate

The build resolves every typed relation whose target lies outside the asserting bundle's namespace against the federation's registry. The top domain's `unowned_targets` says what happens to a target no member owns: `fail` stops the build and keeps the previous workspace, and `report` lists it and goes on. This domain sets `fail`.

## What a confirmation means

A person's confirmation of a member concept attests that the member belongs under the admission rule and that the domain's cross-bundle claims hold. It does not vouch for the member's own concepts. Each member keeps its own trust labels, computed from its events when the workspace is read.
