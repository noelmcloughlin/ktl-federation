---
type: Policy
id: https://w3id.org/ktl/federation/knowledge/policies/federation
genre: reference
title: Federation policy
description: What admits a knowledge bundle to this domain, what a member adds, which release a member names, and what the build does with a target no member owns or a bundle two domains name.
resource: https://w3id.org/ktl/docs/federation
generated:
  by: process:ktl-librarian
  at: "2026-10-18T12:00:24Z"
sources:
  - resource: https://w3id.org/ktl/docs/federation
  - resource: https://w3id.org/ktl/knowledge/playbooks/domain-bundle
  - resource: https://w3id.org/ktl/docs/context-layer
verified:
  - by: process:ktl-librarian
    at: "2026-10-18T11:10:08Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T11:43:47Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T13:26:20Z"
status: draft
stale_after: 2027-04-18
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

## What a member adds

A bundle that meets the admission rule may join. Value is a stricter test: readers query across the member, or other members link into it. A domain whose members never link to one another has proved its mechanism, not its worth.

## The gate

The build resolves every typed relation whose target lies outside the asserting bundle's namespace against the federation's registry. The top domain's `unowned_targets` says what happens to a target no member owns: `fail` stops the build and keeps the previous workspace, and `report` lists it and goes on. This domain sets `fail`.

## The diamond rule

A member may be a domain in turn, and the build then follows that domain's members into the same workspace. So two domains in one workspace may name the same bundle. When both name the same release, the bundle joins the workspace once, and the lock records both domains. When they name different releases, the build stops, because one named graph holds one release. The two owners then agree on one release. A shared model, such as the gist upper ontology, is the ordinary case: every domain whose members link to its terms names it.

## What a confirmation means

A person's confirmation of a member concept attests that the member belongs under the admission rule and that the domain's cross-bundle claims hold. It does not vouch for the member's own concepts. Each member keeps its own trust labels, computed from its events when the workspace is read.

## Open questions

- 2026-10-18, human:noelmcloughlin: it has an old sentence at line 50
