---
type: Domain
id: https://w3id.org/ktl/federation/domains/top
genre: reference
title: The top domain
description: The domain that bounds the KTL federation's workspace. It admits knowledge bundles by release, and its gate policy fails the build on a link no member owns.
resource: https://github.com/noelmcloughlin/ktl-federation
unowned_targets: fail
relatedTo:
- https://w3id.org/ktl/federation/policies/federation
generated:
  by: process:knowledge-federate
  at: "2026-10-16T10:00:29Z"
status: draft
---

# Overview

A domain is a named set of knowledge bundles with one accountable owner. This one is the top domain of the Knowledge Trust Ladder (KTL) federation, and it bounds the workspace: the graph built from its members' releases, one named graph per bundle, named by that bundle's `base_iri`. Its members are the concepts under `members/`, each of type `MemberBundle`, and each names one release by its zip and that zip's checksum. Nothing is copied into this bundle from a member, so a member's new release changes nothing here until a person confirms a member concept that names it.

The owner's confirmation of a member attests two things: that the member belongs under the admission rule in [the federation policy](../policies/federation.md), and that any claim this domain makes across bundles holds. This release makes no cross-bundle claim.

`unowned_targets` is the build's gate policy. With `fail`, a typed relation in any member whose target lies in no member's namespace stops the build and keeps the previous workspace. With `report`, the build lists it and goes on.
