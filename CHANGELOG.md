# Changelog

All notable changes to this repository are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this repository adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

The `v0.1.0` tag is a baseline, not a release: it marks where versioning starts, so the first release was `0.2.0` rather than `1.0.0`. A domain release is what rebuilds the workspace, so a merged change to a member concept releases a minor version. See [CONTRIBUTING.md](CONTRIBUTING.md#releasing-maintainers).

## [Unreleased]

### Security

- **The sidecar copies and the skills pin match `v0.45.0`.** The release changed `.lokf/scripts/knowledge-report.sh`, `.lokf/m365/ktl-docent-m365.md`, `website/scripts/sync.mjs`, `website/src/components/ConceptCard.astro`, `website/src/content.config.ts` and `website/src/styles/catalogue.css` here; its [changelog](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/v0.45.0/CHANGELOG.md) says how.

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
