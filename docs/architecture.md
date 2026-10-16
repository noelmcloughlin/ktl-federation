# Architecture

This page says what the KTL Federation repository holds, how its domain stays current, and how the workspace is built from the members. It is for anyone deciding whether to join a bundle to the federation, and for anyone who keeps this domain.

## Where the design comes from

The design is [the KTL context layer page](https://noelmcloughlin.github.io/knowledge-trust-ladder/docs/context-layer/), which places Knowledge Trust Ladder in the industry's talk of a context layer, says why one bundle is already one repository's layer, and sets out how many bundles federate into one. This repository is that design run for real, with KTL's own bundle, the bundle of its reference host ai-linkmo, and the bundle of lmodel's gist as the first members. Section 11 of [the LOKF specification](https://lokf.nolan-nichols.com/specification/), "Federation: registries of bundles", supplies the registry and the routing; the domain, its schema and the confirmation of membership are what this repository adds.

## The domain

The bundle under `.lokf/knowledge/` is a domain: a thin LOKF bundle whose concepts are other repositories' bundles. Its `base_iri` is `https://w3id.org/ktl/federation/knowledge/`, beside KTL's own namespace and never above it, since the registry routes an IRI to its owner by the longest matching namespace. `https://w3id.org/ktl/federation/` itself is the site, with the workspace under it.

- `domains/top.md` is the top domain. It names the gate policy: a typed relation whose target lies in no member's namespace fails the build.
- `members/` holds one `MemberBundle` concept per member. Each names the member's namespace, one release, the release zip as its distribution, and that zip's SHA-256 digest. A member names the newest release that carries a bundle zip, not the newest release.
- `policies/federation.md` is the admission rule: a member is released with the KTL sidecar's release workflow, validates on LOKF core or on a schema it publishes, has a stable namespace under an authority its publisher controls, and has one accountable owner.

A person's confirmation of a member attests two things only: that the member belongs, and that the domain's cross-bundle claims hold. It is the curator's ordinary confirm, recorded as a `verified` event in that person's name and backed by a signed commit, which the registrar's `provenance` job checks. The first wave carries no cross-bundle claim.

`.lokf/domain.yaml` is the domain schema. It declares `Domain`, `MemberBundle` and `ReleaseDistribution` over LOKF core, so `lokf validate` checks a member's namespace, release and checksum. The schema's namespace is KTL's, so every domain host shares one meaning for those classes; a host that needs more extends it with a schema that imports this one.

## What is here

| Path | Holds |
| --- | --- |
| `.lokf/knowledge/` | The domain bundle, and the `index.md` a reader opens first. |
| `.lokf/domain.yaml` | The domain schema, named by the `schema :=` line of `.lokf/justfile`. |
| `.lokf/scripts/`, `.github/workflows/` | The KTL sidecar's registrar gate, librarian wrapper, release workflow and federation workflow, as copies of its templates. |
| `.lokf/curators/` | The public keys the provenance check verifies a curator's signed commit against. |
| `website/` | The site, from the ktl-website templates: a page per concept with its trust label, the bundle's health, and the four `lokf export` files under `/knowledge/`. |
| `knowledge_bundle` | A link to `.lokf/knowledge/`, the doorway for a file manager or Obsidian. |

## How it stays current

A member's new release changes nothing here until a person confirms a member concept that names it. The librarian for this bundle is a script, not a model: `knowledge-federate.py members`, run by the sidecar's librarian wrapper in place of an agent. It lists each member's releases, picks the newest that carries a bundle zip, verifies its checksum and attestation, and proposes the change as a pull request through the sidecar's own pen. Until that change is confirmed, the member reads as edited since a person last confirmed it, which is how the health line says which members have moved.

A bundle whose sources are release URLs is always quiet to the scheduled librarian, so the federation workflow dispatches the librarian once a week instead.

A merged member change is a release of this domain: the release rules treat `chore(lokf)` as a minor version. Each release carries the bundle as a zip with its checksum, and rebuilds the workspace.

## The workspace

`.lokf/scripts/knowledge-federate.py build`, from the KTL sidecar's federation templates, runs on each release of this domain through `knowledge-federation.yaml`. In order, it:

1. resolves the members into a lock of releases and digests, following a member that is itself a domain;
2. fetches every zip and verifies its checksum and build attestation, refusing a zip with a symbolic link or a path outside its root;
3. unpacks each bundle, checks that its declared namespace is the one the member names, and registers and exports it with the `lokf` toolkit;
4. loads each bundle's graph into a named graph whose IRI is its namespace, with one more graph holding the lock as DCAT and VoID;
5. gates every typed relation whose target lies outside the asserting bundle against the registry, under the top domain's policy;
6. swaps the result in whole, so a failed build leaves the previous workspace in place.

The release carries the workspace as `workspace-<tag>.zip`, and the site serves it under `/workspace/`: the index first, then the lock, the registry, `graph.nq`, each bundle's exports, the gate report, and stored queries that compute every trust label at the moment they run. No label is stored.

Run it locally:

```bash
cd .lokf && just lokf-install && cd ..
uv run --project .lokf .lokf/scripts/knowledge-federate.py build --tag v0.1.0 --release-base https://github.com/noelmcloughlin/ktl-federation/releases/tag
uv run --project .lokf .lokf/scripts/knowledge-federate.py query snapshot/queries/labels.rq
uv run --project .lokf .lokf/scripts/knowledge-federate.py serve
```

## What remains a design

The context layer page also describes an MCP server over the workspace, a hosted SPARQL endpoint, and a union graph page showing cross-bundle edges. None of these is built. The static workspace and the local `serve` subcommand are the read interface today.
