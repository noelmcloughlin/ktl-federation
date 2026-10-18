# Change Log

## 2026-10-18

* **Curation**: human:noelmcloughlin confirmed 5 concepts: the domain at `domains/ktl-federation`, the federation policy, and the three members at their new releases (AI-LinkMO v0.4.9, gist v0.3.7, Knowledge Trust Ladder v0.49.0), each with the review date 2027-04-18. The three move questions are cleared.
* **Changed**: the federation policy now cites KTL's federation page, which states the admission rule and the gate since the context layer page was split, and lists the domain bundle playbook as a source. No rule changed.
* **Changed**: the domain concept cites `docs/architecture.md` and `.lokf/domain.yaml`, so a change to either now puts it on the work list, and says that with no `max_depth` set the build follows member domains three tiers deep.
* **Changed**: AI-LinkMO knowledge bundle moved from v0.3.2 to v0.4.9; the release carries `knowledge-v0.4.9-ai-linkmo.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: AI-LinkMO knowledge bundle: noelmcloughlin/ai-linkmo released v0.4.9 after v0.3.2; does this member move to it?
* **Changed**: gist knowledge bundle moved from v0.3.3 to v0.3.7; the release carries `knowledge-v0.3.7-gist-linkml.zip`.
* **Open question**: gist knowledge bundle: lmodel/gist released v0.3.7 after v0.3.3; does this member move to it?
* **Changed**: Knowledge Trust Ladder knowledge bundle moved from v0.43.0 to v0.49.0; the release carries `knowledge-v0.49.0-knowledge-trust-ladder.zip`.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.49.0 after v0.43.0; does this member move to it?
* **Changed**: the domain concept moved from `domains/top` to `domains/ktl-federation`, titled "The KTL federation domain". A domain concept is named for the domain, never for its position, as KTL's federation figures now name each domain. The confirmation of 2026-10-16 was given to `domains/top` and does not move with it, so the domain waits for a confirmation of its own. The three members' `isPartOf` names the new id, so `members/ai-linkmo.md` reads as edited since a person confirmed it until the curator looks again.

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
