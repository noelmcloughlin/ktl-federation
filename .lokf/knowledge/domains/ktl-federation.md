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
  by: human:noelmcloughlin
  at: "2026-10-18T17:21:47Z"
sources:
  - resource: docs/architecture.md
  - resource: .lokf/domain.yaml
  - resource: https://w3id.org/ktl/docs/federation
verified:
  - by: process:ktl-librarian
    at: "2026-10-18T11:10:08Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T11:43:05Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T17:21:47Z"
  - by: human:noelmcloughlin
    at: "2026-10-18T23:56:15Z"
stale_after: 2027-04-18
---

# Overview

A domain is a named set of knowledge bundles with one accountable owner. This one is the domain of the Knowledge Trust Ladder (KTL) federation. Every domain bounds a workspace of its own: the graph built from its members' releases, one named graph per bundle, named by that bundle's `base_iri`. This domain's builds start here, and another domain may name this bundle as a member in turn. Its members are the concepts under `members/`, each of type `MemberBundle` or `MemberDomain`, and each names one release by its zip and that zip's checksum. Nothing is copied into this bundle from a member, so a member's new release changes nothing here until a person confirms a member concept that names it.

The owner's confirmation of a member attests two things: that the member belongs under the admission rule in [the federation policy](../policies/federation.md), and that any claim this domain makes across bundles holds. This release makes no cross-bundle claim.

`unowned_targets` is the build's gate policy. With `fail`, a typed relation in any member whose target lies in no member's namespace stops the build and keeps the previous workspace. With `report`, the build lists it and goes on.

It sets no `max_depth`, so the build follows member domains three tiers deep, and this domain's own members are tier 1.
