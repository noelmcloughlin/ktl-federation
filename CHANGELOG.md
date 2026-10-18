# Changelog

All notable changes to this repository are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this repository adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

The `v0.1.0` tag is a baseline, not a release: it marks where versioning starts, so the first release was `0.2.0` rather than `1.0.0`. A domain release is what rebuilds the workspace, so a merged change to a member concept releases a minor version. See [CONTRIBUTING.md](CONTRIBUTING.md#releasing-maintainers).

## [Unreleased]

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
