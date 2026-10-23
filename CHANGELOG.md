# Changelog

All notable changes to this repository are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this repository adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

The `v0.1.0` tag is a baseline, not a release: it marks where versioning starts, so the first release was `0.2.0` rather than `1.0.0`. A domain release is what rebuilds the workspace, so a merged change to a member concept releases a minor version. See [CONTRIBUTING.md](CONTRIBUTING.md#releasing-maintainers).

## [Unreleased]

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.55.2](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.55.0...v0.55.2).** The release changed `.lokf/scripts/knowledge-preflight.sh`, `.lokf/scripts/knowledge-sync.sh`, `website/package-lock.json` and `website/package.json` here.

## [0.12.0] - 2026-10-21

### Added

- **The linkml-sidecar bundle is a member at its v0.0.1 release.** Its zip's checksum and attestation were verified, and a person confirmed it under the admission rule.

### Changed

- **The Knowledge Trust Ladder member names its v0.55.0 bundle release.** The zip's checksum and attestation were verified, and a person confirmed the move.

## [0.11.1] - 2026-10-21

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.55.0](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.53.0...v0.55.0).** The release changed `.github/workflows/knowledge-registrar.yaml`, `.github/workflows/knowledge-release.yaml`, `.github/workflows/knowledge-federation.yaml`, `.github/workflows/knowledge-sync.yaml`, `.lokf/scripts/knowledge-librarian.sh`, `.lokf/scripts/knowledge-conventions.sh`, `.lokf/scripts/knowledge-conventions.py`, `.lokf/scripts/knowledge-preflight.sh`, `.lokf/scripts/knowledge-provenance.sh`, `.lokf/scripts/knowledge-feedback.sh`, `.lokf/scripts/knowledge-apply.sh`, `.lokf/scripts/knowledge-apply.py`, `.lokf/scripts/knowledge-report.sh`, `.lokf/scripts/knowledge-federate.py`, `.lokf/scripts/knowledge-sync.sh`, `.lokf/domain.yaml`, `.lokf/.gitignore` and `.lokf/justfile` here.

## [0.11.0] - 2026-10-20

### Changed

- **The graph page's full screen keeps the graph at full height and stays on when the view changes,** and its filters show counts, *All* and *None*, and how many concepts are shown. The component is ahead of the skills pin until Knowledge Trust Ladder releases the same change.

## [0.10.1] - 2026-10-19

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.53.0](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.52.0...v0.53.0).** The release changed `.github/workflows/knowledge-librarian.yaml`, `.github/workflows/knowledge-federation.yaml`, `.github/workflows/knowledge-sync.yaml`, `.github/PULL_REQUEST_TEMPLATE/knowledge-sync.md`, `.lokf/scripts/knowledge-librarian.sh`, `.lokf/scripts/knowledge-apply.py`, `.lokf/scripts/knowledge-federate.py`, `.lokf/scripts/knowledge-sync.sh`, `.lokf/domain.yaml`, `.lokf/.gitignore`, `website/scripts/config.mjs`, `website/scripts/markdown-ktl.mjs`, `website/scripts/sync.mjs`, `website/src/components/KnowledgeGraph.astro`, `website/src/pages/graph.astro`, `.github/workflows/knowledge-website.yaml` and `website/scripts/raw-html.mjs` here.

## [0.10.0] - 2026-10-19

### Changed

- **The Knowledge Trust Ladder, AI-LinkMO and gist members name their v0.52.0, v0.4.10 and v0.3.10 bundle releases.** Each zip's checksum and attestation were verified, and a person confirmed each move.

## [0.9.0] - 2026-10-19

### Changed

- **The federation policy's diamond rule says the build stays stopped until both owners pin one release**, as KTL's federation page now says.

## [0.8.1] - 2026-10-18

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.52.0](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.50.1...v0.52.0).** The release changed `.github/workflows/knowledge-federation.yaml`, `.lokf/scripts/knowledge-conventions.sh`, `.lokf/scripts/knowledge-conventions.py`, `.lokf/scripts/knowledge-report.sh`, `.lokf/scripts/knowledge-federate.py` and `.lokf/domain.yaml` here.

## [0.8.0] - 2026-10-18

### Changed

- **The Knowledge Trust Ladder member names its v0.50.1 bundle release.** The zip's checksum and attestation were verified, and a person confirmed the move.

## [0.7.0] - 2026-10-18

### Changed

- **The domain concept says a member is a `MemberBundle` or a `MemberDomain`, as the architecture page does.** A person corrected it and confirmed it against that page's latest edits.

## [0.6.2] - 2026-10-18

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.50.1](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.48.0...v0.50.1).** The release changed `.lokf/scripts/knowledge-preflight.sh`, `.lokf/scripts/knowledge-report.sh` and `.lokf/scripts/knowledge-sync.sh` here.

## [0.6.1] - 2026-10-18

### Fixed

- **The build takes each member as a person last confirmed it.** It built every member concept at the tag, as the 0.6.0 pages said, so a merged move or a new member joined the workspace before anyone confirmed it. A moved member is now built at its confirmed release while that confirmation stands, and a new one waits outside until confirmed. The domain's own gate policy and depth count only as confirmed too, and the pages and the figure say so again.

## [0.6.0] - 2026-10-18

### Fixed

- **The pages say when a member joins the workspace.** The architecture and curation pages and the figure said a release changes nothing until a person confirms it. The build takes every member concept on the default branch, so a release joins when its pull request merges, and the confirmation records that it belongs.

## [0.5.0] - 2026-10-18

### Added

- **KTL Curator 1.6.4 and KTL Registrar 1.7.5 join the domain as members.** Each zip's checksum and attestation were verified, and a person's confirmation admits each one.

### Changed

- **The federation policy states the value test and the diamond rule.** No admission condition changed.

## [0.4.0] - 2026-10-18

### Changed

- **The members name their newest bundle releases: Knowledge Trust Ladder v0.49.0, AI-LinkMO v0.4.9 and gist v0.3.7.** Each zip's checksum and attestation were verified, and each move waits for a person's confirmation.

## [0.3.0] - 2026-10-18

### Changed

- **The domain concept is `domains/ktl-federation`, named for the domain rather than its position.** The workspace index and every member's `isPartOf` name the new id, and the domain waits for a confirmation of its own.

## [0.2.6] - 2026-10-18

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.48.0](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.47.0...v0.48.0).** The release changed `.github/workflows/knowledge-registrar.yaml`, `.github/workflows/knowledge-federation.yaml`, `.github/PULL_REQUEST_TEMPLATE/knowledge-sync.md`, `.lokf/scripts/knowledge-report.sh`, `.lokf/scripts/knowledge-federate.py` and `.lokf/domain.yaml` here.

## [0.2.5] - 2026-10-17

### Security

- **The sidecar copies and the skills pin are at Knowledge Trust Ladder [v0.47.0](https://github.com/noelmcloughlin/knowledge-trust-ladder/compare/v0.46.0...v0.47.0).** The release changed `.lokf/scripts/knowledge-preflight.sh`, `.lokf/scripts/knowledge-federate.py`, `.github/workflows/knowledge-sync.yaml`, `.github/PULL_REQUEST_TEMPLATE/knowledge-sync.md` and `.lokf/scripts/knowledge-sync.sh` here.

## [0.2.4] - 2026-10-17

### Security

- **The sidecar copies and the skills pin match `v0.46.0`.** The release changed `.github/workflows/knowledge-release.yaml`, `.lokf/scripts/knowledge-federate.py`, `website/package-lock.json` and `website/package.json` here; its [changelog](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/v0.46.0/CHANGELOG.md) says how.

## [0.2.3] - 2026-10-17

### Security

- **The sidecar copies and the skills pin match `v0.45.1`.** The release changed `.lokf/scripts/knowledge-apply.py` and `.lokf/scripts/knowledge-federate.py` here; its [changelog](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/v0.45.1/CHANGELOG.md) says how.

## [0.2.2] - 2026-10-16

### Security

- **The sidecar copies and the skills pin match `v0.45.0`.** The release changed `.lokf/scripts/knowledge-report.sh`, `.lokf/m365/ktl-docent-m365.md`, `website/scripts/sync.mjs`, `website/src/components/ConceptCard.astro`, `website/src/content.config.ts` and `website/src/styles/catalogue.css` here; its [changelog](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/v0.47.0/CHANGELOG.md) says how.

## [0.2.1] - 2026-10-16

### Security

- **The skills pin matches `v0.44.0`.** The sidecar copies were already current, and the justfile keeps this host's domain schema.

## [0.2.0] - 2026-10-16

### Added

- The top domain of the Knowledge Trust Ladder federation, as a LOKF knowledge bundle under `.lokf/` with the namespace `https://w3id.org/ktl/federation/knowledge/`: the domain, its federation policy, and three members named by their released zips, knowledge-trust-ladder v0.43.0, ai-linkmo v0.3.2 and gist v0.3.3.
- The domain schema `.lokf/domain.yaml`, which declares `Domain`, `MemberBundle` and `ReleaseDistribution` over LOKF core, so `lokf validate` checks a member's namespace, release and checksum.
- The KTL sidecar, its registrar, librarian and release workflows, and the website.
- The federation build and its workflow, `knowledge-federation.yaml`, from the sidecar's templates: on each release the workspace is built from the members' zips, attached to the release as `workspace-<tag>.zip`, and served with the site under `/workspace/`.
- `docs/architecture.md`, the design of the domain and the workspace, with the README as its doorway.
