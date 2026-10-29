---
type: Policy
id: https://w3id.org/ktl/federation/knowledge/policies/federation
genre: reference
title: Federation policy
description: What admits a knowledge bundle to this domain, what a member adds, which release a member names, what a person's confirmation attests, and who arbitrates a claim across bundles. It also says what the build does with a target that names no member's concept or a bundle two domains name.
resource: https://w3id.org/ktl/docs/federation
generated:
  by: process:ktl-librarian
  at: "2026-10-29T11:44:32Z"
sources:
  - resource: https://w3id.org/ktl/docs/federation
  - resource: https://w3id.org/ktl/knowledge/playbooks/domain-bundle
  - resource: https://w3id.org/ktl/docs/context-layer
  - resource: docs/architecture.md
  - resource: .github/workflows/knowledge-release.yaml
verified:
  - by: process:ktl-librarian
    at: "2026-10-29T11:52:21Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T11:43:47Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T13:26:20Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T23:53:12Z"
stale_after: 2027-04-18
status: draft
---

# Overview

## Admission

A knowledge bundle joins this domain when all four hold:

- it is released with the KTL sidecar's release workflow, so each release carries the bundle as a zip with a checksum and, on a public repository, a build attestation;
- it validates against LOKF core, or against a schema it publishes with its releases;
- its `base_iri` is stable and lies under an authority its publisher controls;
- it has one accountable owner, who answers for what it claims.

The registry refuses a `base_iri` that nests inside another member's, so no two members' namespaces nest.

A member concept names one release, the newest that carries a zip. A release whose bundle and domain schema are both unchanged carries no zip.

## What a member adds

A bundle that meets the admission rule may join. Value is a stricter test: readers query across the member, or other members link into it. A federation whose members never link to one another has proved its mechanism, not its worth. No member of this domain links into another yet.

## The gate

The build resolves every typed relation whose target lies outside the asserting bundle's namespace against the federation's registry. Under the top domain's `unowned_targets`, `fail` stops the build on a target in no member's namespace, or on one in a member's namespace that names no concept of that member, and `report` lists it and goes on. A pull request's check runs the same gate, so such a link fails before the merge. This domain sets `fail`.

## The diamond rule

A member may be a domain in turn, and the build then follows that domain's members into the same workspace. So two domains in one workspace may name the same bundle. When both name the same release, the bundle joins the workspace once, and the lock records both domains. When they name different releases, the build stops, because one named graph holds one release. It stays stopped until the two owners agree on one release and both pin it. A shared model, such as the gist upper ontology, is the ordinary case: every sub-domain that links to its terms names it.

## What a confirmation means

A person's confirmation of a member concept attests that the member belongs under the admission rule and that the domain's cross-bundle claims hold. For a `MemberDomain`, it attests that the domain belongs and who answers for it, not what that domain's members say. It does not vouch for the member's own concepts. Each member keeps its own trust labels, computed from its events when the workspace is read.

A confirmation is the curator's ordinary confirm, recorded as a `verified` event in that person's name and backed by a signed commit, which the registrar's `provenance` job checks.

## This domain's decisions

KTL's federation page lists the [decisions an adopter must make](https://w3id.org/ktl/docs/federation/#decisions-an-adopter-must-make). Beside the admission rule and the value test above, this domain's answers are:

- **Pin.** Each member concept names one release, and a person confirms each move. A domain that names this one adds a pin of its own. So a member's release reaches that domain's workspace only after a confirmation and a release here, then a confirmation and a release there.
- **Who arbitrates.** This domain's owner arbitrates a claim across bundles, by a confirmed concept in this bundle, never by a rewrite of a member. There is no cross-bundle claim yet.
- **Permissions.** Every member is a public repository. A bundle that must not be seen whole does not join.
