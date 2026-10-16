# Change Log

## 2026-10-16

* **Changed**: the bundle's `base_iri` moved from `https://w3id.org/ktl/federation/` to `https://w3id.org/ktl/federation/knowledge/`, the shape of the other KTL bundles' namespaces, so `https://w3id.org/ktl/federation/` is free for the site and the workspace; every id and relation target moved with it, and no concept's text changed.
* **Added**: the top domain, with `unowned_targets: fail`.
* **Added**: the federation policy: admission, the gate, and what a confirmation means.
* **Added**: member knowledge-trust-ladder at v0.43.0.
* **Added**: member ai-linkmo at v0.3.2.
* **Added**: member gist at v0.3.3, the first member from a second authority.
* **Initialization**: Scaffolded the LOKF bundle for KTL Federation with the domain schema `domain.yaml`, which declares `Domain`, `MemberBundle` and `ReleaseDistribution`.
