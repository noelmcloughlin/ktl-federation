# Change Log

## 2026-10-29

* **Changed**: The domain schema names five classes, since `.lokf/domain.yaml` adds `ReleaseChecksum`, LOKF core's checksum with sha256 as its only algorithm, in place of the `sha256:<hex>` string.
* **Changed**: The KTL federation domain, refreshed against its sources as a person asked: a member's checksum is its zip's SHA-256 checksum, and KTL's federation page adds that a domain at the last tier stops the build and that a domain may not name itself or one above it. Edited since a person confirmed it; the label says so until the curator looks again.
* **Changed**: Federation policy, reviewed against its sources as a person asked: a release carries no zip only when both its bundle and its domain schema are unchanged, as the release workflow says since v0.59.0; no member links into another yet; there is no cross-bundle claim yet; and the diamond rule's wording follows KTL's federation page. Edited since a person confirmed it; the label says so until the curator looks again.
* **Curation**: human:noelmcloughlin sent 1 concept back (the domain, to refresh against its sources, with its text released to the librarian) and left 1 for later (the federation policy, still a draft).
* **Curation**: human:noelmcloughlin confirmed 4 concepts (the AI-LinkMO, linkml-sidecar, KTL Curator and KTL Registrar members, whose checksums the pen moved to LOKF core's `Checksum` form with the same digests).
* **Curation**: human:noelmcloughlin corrected 2 concepts (the gist and Knowledge Trust Ladder members, whose checksums now take LOKF core's `Checksum` form with the same digests), and the corrections confirm both.
* **Changed**: AI-LinkMO knowledge bundle names its checksum as LOKF core's `Checksum`; the digest is the same. Edited since a person confirmed it; the label says so until the curator looks again.
* **Changed**: linkml-sidecar Knowledge Bundle names its checksum as LOKF core's `Checksum`; the digest is the same. Edited since a person confirmed it; the label says so until the curator looks again.
* **Changed**: KTL Curator knowledge bundle names its checksum as LOKF core's `Checksum`; the digest is the same. Edited since a person confirmed it; the label says so until the curator looks again.
* **Changed**: KTL Registrar knowledge bundle names its checksum as LOKF core's `Checksum`; the digest is the same. Edited since a person confirmed it; the label says so until the curator looks again.

## 2026-10-27

* **Curation**: human:noelmcloughlin corrected 1 concept (the domain, without a new confirmation) and sent 1 back (the federation policy, to review against its sources).

## 2026-10-26

* **Curation**: human:noelmcloughlin confirmed 3 concepts (the linkml-sidecar, KTL Curator and KTL Registrar members, at v0.3.2, 1.6.9 and 1.7.10) and corrected 1 (the Knowledge Trust Ladder member, moved to v0.56.1), each against its release, checksum and attestation, and cleared their federate questions.
* **Prose**: reworded 4 concept bodies in plain English. No fact, link, number or frontmatter changed.
* **Added**: the knowledge sources map, which names every top-level path and the outside pages this bundle rests on, the concept each yields, and the files left out on purpose.
* **Added**: the contributing playbook, from `CONTRIBUTING.md`, the pull request template, the lint workflow and the AI covenant.
* **Added**: the releasing playbook, from `semantic-release.yml`, `.releaserc.json`, the changelog script, `knowledge-release.yaml`, `CONTRIBUTING.md` and `SECURITY.md`.
* **Added**: the knowledge website playbook, from `website/README.md`, `site.config.mjs`, the website and federation workflows, and `SECURITY.md`.
* **Changed**: the workspace concept cites `.github/workflows/knowledge-federation.yaml`, so a change to the build's workflow puts it on the work list. No claim changed.
* **Added**: Confirming a member change, from `docs/curation.md`, with where a member change comes from as `docs/architecture.md` says. No concept covered `docs/curation.md` before.
* **Added**: The KTL federation workspace, from `docs/architecture.md`: how each release builds it, what the release and the site carry, and how to read it.
* **Added**: The domain schema, from `.lokf/domain.yaml` and `docs/architecture.md`: the four classes it adds over LOKF core, and how a host extends it.
* **Changed**: Federation policy: it now gives this domain's decisions on pinning, arbitration and permissions, what confirming a `MemberDomain` attests, and that a confirmation is a signed `verified` event, as `docs/architecture.md` says, and cites that page. Edited since a person confirmed it; the label says so until the curator looks again.
* **Changed**: Federation policy: the gate now also stops on a target in a member's namespace that names no concept there, and runs on pull requests, as KTL's docs/federation.md and domain-bundle playbook say since 2026-10-19; neither says the gate keeps the previous workspace, so that clause is gone. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.56.1 after the confirmed v0.55.1; does this member move to it? A person wrote this concept, so this patch leaves its text and frontmatter as they are.
* **Changed**: linkml-sidecar Knowledge Bundle moved from v0.2.0 to v0.3.2, and its namespace from `https://noelmcloughlin.github.io/linkml-sidecar/knowledge/` to `https://w3id.org/ktl/linkml-sidecar/knowledge/`; the release carries `knowledge-v0.3.2-linkml-sidecar.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: linkml-sidecar Knowledge Bundle: noelmcloughlin/linkml-sidecar released v0.3.2 after the confirmed v0.2.0; does this member move to it?
* **Changed**: KTL Curator knowledge bundle moved from 1.6.4 to 1.6.9; the release carries `knowledge-1.6.9-obsidian-ktl-curator.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: KTL Curator knowledge bundle: noelmcloughlin/obsidian-ktl-curator released 1.6.9 after the confirmed 1.6.4; does this member move to it?
* **Changed**: KTL Registrar knowledge bundle moved from 1.7.5 to 1.7.10; the release carries `knowledge-1.7.10-obsidian-ktl-registrar.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: KTL Registrar knowledge bundle: noelmcloughlin/obsidian-ktl-registrar released 1.7.10 after the confirmed 1.7.5; does this member move to it?
* **Curation**: human:noelmcloughlin corrected the domain at `domains/ktl-federation` with plain-English wording: the overview is split into three paragraphs, the `fail` conditions are a list, and each setting is defined before what this domain sets. It now says the domain makes no cross-bundle claim yet, as `docs/architecture.md` does. No fact, link or number changed.
* **Curation**: human:noelmcloughlin corrected 3 concepts and confirmed 1. The domain now gives the wider `fail` rule, `max_depth`, `sensitivity` and `private_addresses` in `.lokf/domain.yaml`'s words. The gist and Knowledge Trust Ladder members now give their release dates as 2026-10-23 and 2026-10-22. The linkml-sidecar member is confirmed at v0.2.0. All three member questions are cleared, and the review dates are kept. The same correction came up twice: the librarian moved a member's version but kept the old release date, so its federate step should take the date from the release.
* **Changed**: gist knowledge bundle moved from v0.3.10 to v0.3.13; the release carries `knowledge-v0.3.13-gist-linkml.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: gist knowledge bundle: lmodel/gist released v0.3.13 after the confirmed v0.3.10; does this member move to it?
* **Changed**: Knowledge Trust Ladder knowledge bundle moved from v0.55.0 to v0.55.1; the release carries `knowledge-v0.55.1-knowledge-trust-ladder.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.55.1 after the confirmed v0.55.0; does this member move to it?
* **Changed**: linkml-sidecar Knowledge Bundle moved from v0.0.1 to v0.2.0; the release carries `knowledge-v0.2.0-linkml-sidecar.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: linkml-sidecar Knowledge Bundle: noelmcloughlin/linkml-sidecar released v0.2.0 after the confirmed v0.0.1; does this member move to it?

## 2026-10-21

* **Curation**: human:noelmcloughlin confirmed 2 concepts: the new linkml-sidecar member at v0.0.1, admitted under the admission rule with the review date 2027-04-21, and the Knowledge Trust Ladder member's move to v0.55.0, keeping its review date 2027-04-18, after checking each release's checksum, attestation and namespace, and cleared each one's question. Nothing was sent back or retired.
* **Changed**: Knowledge Trust Ladder knowledge bundle moved from v0.52.0 to v0.55.0; the release carries `knowledge-v0.55.0-knowledge-trust-ladder.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.55.0 after the confirmed v0.52.0; does this member move to it?
* **Added**: linkml-sidecar Knowledge Bundle, noelmcloughlin/linkml-sidecar at v0.0.1; a person confirms the member to admit it.
* **Open question**: linkml-sidecar Knowledge Bundle: noelmcloughlin/linkml-sidecar is proposed as a member at v0.0.1; does it belong under the admission rule?

## 2026-10-19

* **Curation**: human:noelmcloughlin confirmed 3 concepts: the Knowledge Trust Ladder member at v0.52.0, the AI-LinkMO member at v0.4.10 and the gist member at v0.3.10, after checking each release's checksum, attestation and namespace, keeping each review date 2027-04-18, and cleared each one's question about the move. Nothing was sent back or retired.
* **Changed**: AI-LinkMO knowledge bundle moved from v0.4.9 to v0.4.10; the release carries `knowledge-v0.4.10-ai-linkmo.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: AI-LinkMO knowledge bundle: noelmcloughlin/ai-linkmo released v0.4.10 after the confirmed v0.4.9; does this member move to it?
* **Changed**: gist knowledge bundle moved from v0.3.7 to v0.3.10; the release carries `knowledge-v0.3.10-gist-linkml.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: gist knowledge bundle: lmodel/gist released v0.3.10 after the confirmed v0.3.7; does this member move to it?
* **Changed**: Knowledge Trust Ladder knowledge bundle moved from v0.50.1 to v0.52.0; the release carries `knowledge-v0.52.0-knowledge-trust-ladder.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.52.0 after the confirmed v0.50.1; does this member move to it?

## 2026-10-18

* **Curation**: human:noelmcloughlin confirmed 1 concept: the domain at `domains/ktl-federation`, against `.lokf/domain.yaml` after the v0.52.0 sync added a comment about a member domain's workspace, keeping the review date 2027-04-18. Nothing was sent back or retired.
* **Curation**: human:noelmcloughlin confirmed 1 concept: the federation policy, after its diamond rule was brought in line with KTL's federation page, keeping the review date 2027-04-18, and cleared the note they left on the old sentence. Nothing was sent back or retired.
* **Changed**: the federation policy's diamond rule says the build stays stopped until the two owners agree on one release and both pin it, as KTL's federation page now says. This answers the note a person left on the old sentence. Edited since a person confirmed it; the label says so until the curator looks again.
* **Curation**: human:noelmcloughlin sent back 1 concept: the federation policy, whose diamond rule still says the two owners "then agree" where KTL's federation page now says the build stays stopped until they agree and both pin one release. Nothing was confirmed or retired.
* **Curation**: human:noelmcloughlin confirmed 1 concept: the Knowledge Trust Ladder member at v0.50.1, after checking the release's checksum, attestation and namespace, keeping the review date 2027-04-18, and cleared its question about the move. Nothing was sent back or retired.
* **Changed**: Knowledge Trust Ladder knowledge bundle moved from v0.49.0 to v0.50.1; the release carries `knowledge-v0.50.1-knowledge-trust-ladder.zip`. Edited since a person confirmed it; the label says so until the curator looks again.
* **Open question**: Knowledge Trust Ladder knowledge bundle: noelmcloughlin/knowledge-trust-ladder released v0.50.1 after the confirmed v0.49.0; does this member move to it?
* **Curation**: human:noelmcloughlin corrected 1 concept now: the domain at `domains/ktl-federation` says its members may be of type `MemberBundle` or `MemberDomain`, as `docs/architecture.md` says, and was confirmed against that page's later edits, keeping the review date 2027-04-18. Nothing was sent back or retired.
* **Curation**: human:noelmcloughlin confirmed 3 concepts: the federation policy again, after its edit added the value test and the diamond rule, and the two new members, KTL Curator at 1.6.4 and KTL Registrar at 1.7.5, each checked against the four admission conditions and given the review date 2027-04-18. Their two admission questions are cleared. Nothing was sent back or retired.
* **Prose**: reworded 2 concept bodies in plain English. No fact, link, number or frontmatter changed.
* **Changed**: the federation policy states the value test and the diamond rule, as KTL's federation page and the domain bundle playbook give them, and its description names both. No admission condition changed. Edited since a person confirmed it; the label says so until the curator looks again.
* **Added**: KTL Curator knowledge bundle, noelmcloughlin/obsidian-ktl-curator at 1.6.4; a person confirms the member to admit it.
* **Open question**: KTL Curator knowledge bundle: noelmcloughlin/obsidian-ktl-curator is proposed as a member at 1.6.4; does it belong under the admission rule?
* **Added**: KTL Registrar knowledge bundle, noelmcloughlin/obsidian-ktl-registrar at 1.7.5; a person confirms the member to admit it.
* **Open question**: KTL Registrar knowledge bundle: noelmcloughlin/obsidian-ktl-registrar is proposed as a member at 1.7.5; does it belong under the admission rule?
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
