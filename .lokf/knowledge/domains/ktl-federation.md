---
type: Domain
id: https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
genre: reference
title: The KTL federation domain
description: The domain of the KTL federation. Its builds start here, and another domain may name it as a member. It admits knowledge bundles by release, and its gate policy fails the build on a link no member owns.
resource: https://github.com/noelmcloughlin/ktl-federation
unowned_targets: fail
relatedTo:
  - https://w3id.org/ktl/federation/knowledge/policies/federation
generated:
  by: process:ktl-librarian
  at: "2026-10-29T11:44:32Z"
sources:
  - resource: docs/architecture.md
  - resource: .lokf/domain.yaml
  - resource: https://w3id.org/ktl/docs/federation
verified:
  - by: process:ktl-librarian
    at: "2026-10-29T11:52:21Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T11:43:05Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T17:21:47Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T23:56:15Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T17:07:54Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T17:15:22Z"
  - by: human:noelmcloughlin
    at: "2026-10-26T17:27:52Z"
stale_after: 2027-04-18
status: draft
---

# Overview

A domain is a named set of knowledge bundles with one accountable owner. This one is the domain of the Knowledge Trust Ladder (KTL) federation. This domain's builds start here, and another domain may name this bundle as a member in turn.

Every domain bounds a workspace of its own. The workspace is the graph built from the members' releases, with one named graph per bundle, named by that bundle's `base_iri`.

The members are the concepts under `members/`. Each is of type `MemberBundle` or `MemberDomain`, and each names one release by its zip and that zip's SHA-256 checksum. A file that fails a check stops the job, and the old snapshot stays. Nothing from a member is copied into this bundle, so a member's new release changes nothing here until a person confirms a member concept that names it.

When the owner confirms a member, the confirmation attests two things: that the member belongs under the admission rule in [the federation policy](../policies/federation.md), and that any claim this domain makes across bundles holds. This domain makes no cross-bundle claim yet.

This concept is a `Domain`, which carries `unowned_targets`, `max_depth`, `sensitivity` and `private_addresses`.

`unowned_targets` is the build's gate policy. With `fail`, the build stops and keeps the previous workspace when a typed relation in any member has a target that:

- no member owns; or
- lies in a member's namespace and names no concept of it.

With `report`, the build lists such a relation and goes on.

`max_depth` is how many tiers of members the build follows when a member is itself a domain. This domain sets none, so the build follows 3. This domain's own members are tier 1. A domain found at the last tier stops the build, and a domain may not name itself or a domain above it.

`sensitivity` is the most sensitive member the workspace may hold: public or internal. This domain sets none, so the workspace holds public members only. A person who confirms `internal` clears the workspace to aggregate internal bundles, as section 11.5 of the LOKF specification asks of a registry's owner.

`private_addresses` says whether the build may fetch a member from a private, loopback or link-local address. This domain sets none, so the build refuses. A person confirms `allow` for a forge on the host's own network.

## Open questions

- 2026-10-29, human:noelmcloughlin: refresh against sources.
