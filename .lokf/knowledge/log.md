# Change Log

## 2026-10-17

* **Changed**: the domain concept is named for the domain, not for its position. Its title is "The KTL federation domain", and its text says that the top is relative: every domain bounds a workspace of its own, and this one may be a member of another. Edited since a person confirmed it; the label says so until the curator looks again.
* **Changed**: AI-LinkMO knowledge bundle moved from v0.3.2 to v0.4.7; the release carries `knowledge-v0.4.7-ai-linkmo.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: AI-LinkMO knowledge bundle: noelmcloughlin/ai-linkmo released v0.4.7 after the confirmed v0.3.2; does this member move to it?
* **Changed**: gist knowledge bundle moved from v0.3.3 to v0.3.7; the release carries `knowledge-v0.3.7-gist-linkml.zip`.
* **Open question**: gist knowledge bundle: lmodel/gist released v0.3.7 after v0.3.3; does this member move to it?
* **Changed**: Knowledge Trust Ladder knowledge bundle moved from v0.43.0 to v0.45.1; the release carries `knowledge-v0.45.1-knowledge-trust-ladder.zip`.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.45.1 after v0.43.0; does this member move to it?

## 2026-10-16

* **Prose**: reworded 3 concept bodies in plain English. No fact, link, number or frontmatter changed.
* **Changed**: the federation policy now names the registry, which refuses a nested `base_iri`, as what keeps members' namespaces apart. The context layer page and the lokf registry say so, and neither credits a publisher's control of its authority with it.
* **Curation**: human:noelmcloughlin reviewed 3 of 5 concepts: 2 confirmed (the top domain, re-check due 2026-11-16, and member ai-linkmo), 1 marked for later (the federation policy), 0 sent back, 0 corrected, 0 retired.
* **Changed**: the bundle's `base_iri` moved from `https://w3id.org/ktl/federation/` to `https://w3id.org/ktl/federation/knowledge/`, the shape of the other KTL bundles' namespaces, so `https://w3id.org/ktl/federation/` is free for the site and the workspace; every id and relation target moved with it, and no concept's text changed.
* **Added**: the top domain, with `unowned_targets: fail`.
* **Added**: the federation policy: admission, the gate, and what a confirmation means.
* **Added**: member knowledge-trust-ladder at v0.43.0.
* **Added**: member ai-linkmo at v0.3.2.
* **Added**: member gist at v0.3.3, the first member from a second authority.
* **Initialization**: Scaffolded the LOKF bundle for KTL Federation with the domain schema `domain.yaml`, which declares `Domain`, `MemberBundle` and `ReleaseDistribution`.
