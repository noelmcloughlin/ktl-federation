# Architecture

This page says what this repository holds, how its domain stays current, and how the workspace is built from the members. It is for anyone deciding whether to join a bundle to the Knowledge Trust Ladder (KTL) federation, and for anyone who keeps its domain.

## Where the design comes from

KTL sets out the design on two pages. [The curated context layer](https://w3id.org/ktl/docs/context-layer/) says what a context layer is, why one bundle is already one repository's layer, and why KTL federates bundles through domains. [A federation of bundles](https://w3id.org/ktl/docs/federation/) says how a domain names bundles and other domains, how the workspace is built and kept current, and what an adopter decides. Section 11 of [the LOKF specification](https://lokf.nolan-nichols.com/specification/), "Federation: registries of bundles", supplies the registry and the routing.

This repository is the first domain host. Its first members are KTL's bundle, the bundle of its reference host ai-linkmo, and the bundle of lmodel's gist.

The figure reads from the bottom up. Each member releases its bundle from its own repository. This domain names one release of each, and its builds turn those releases into the workspace, the domain's context layer, which readers query.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../.assets/ktl-federation-context-layer-dark.svg">
    <img src="../.assets/ktl-federation-context-layer.svg" alt="Drawn bottom to top: three member bundles, Knowledge Trust Ladder, AI-LinkMO and gist, each on its own trust ladder and released to GitHub Releases as a zip with its checksum and attestation; the domain, this repository's bundle, whose members/ concepts name one release each, whose domains/ktl-federation is where the build starts, and whose policies/federation is the admission rule; the workspace, one named graph per member, built on each release of the domain; and, at the top, the readers." width="720" />
  </picture>
</p>

## The domain

A domain is a named set of bundles with one accountable owner, kept as a thin LOKF bundle in a repository of its own. The bundle under `.lokf/knowledge/` is the domain of the KTL federation. Every domain bounds a workspace of its own. This domain's builds start here, so it is the top domain of the workspace they build. Another domain may still name it as a member.

- `domains/ktl-federation.md` is the domain concept. Its `unowned_targets` is `fail`: a typed relation whose target lies in no member's namespace stops the build. It sets no `max_depth`, so the build follows member domains three tiers deep.
- `members/` holds one concept per member: a `MemberBundle`, or a `MemberDomain` when the member's bundle is itself a domain. Each names the member's namespace, one release, the release zip as its distribution with that zip's SHA-256 digest, and the schema released beside the zip when the member publishes one. A member names the newest release that carries a bundle zip, not the newest release.
- `policies/federation.md` is the admission rule: a member is released with the KTL sidecar's release workflow, validates on LOKF core or on a schema it publishes, has a stable namespace under an authority its publisher controls, and has one accountable owner.

A person's confirmation of a member attests two things only: that the member belongs, and that the domain's cross-bundle claims hold. For a `MemberDomain`, it attests that the domain belongs and who answers for it, not what that domain's members say. It is the curator's ordinary confirm, recorded as a `verified` event in that person's name and backed by a signed commit, which the registrar's `provenance` job checks.

The domain's `base_iri` is `https://w3id.org/ktl/federation/knowledge/`. It sits beside KTL's own namespace, never above it, since the registry refuses a `base_iri` nested inside another and routes an IRI to its owner by the longest matching namespace. `https://w3id.org/ktl/federation/` itself is the site, with the workspace under it.

`.lokf/domain.yaml` is the domain schema. It declares four classes over LOKF core: `Domain`, which carries `unowned_targets` and `max_depth`; `MemberBundle`; `MemberDomain`; and `ReleaseDistribution`, which carries the zip's checksum. So `lokf validate` checks a member's namespace, release and checksum. The schema's namespace is KTL's, so every domain host shares one meaning for those classes. A host that needs more extends it with a schema that imports this one. The curator's [domain bundle page](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/main/skills/ktl-curator/references/domain-bundle.md) describes each class.

## What is here

| Path | Holds |
| --- | --- |
| `.lokf/knowledge/` | The domain bundle, and the `index.md` a reader opens first. |
| `.lokf/domain.yaml` | The domain schema, named by the `schema :=` line of `.lokf/justfile`. |
| `.lokf/scripts/`, `.github/workflows/` | The KTL sidecar's registrar gate, librarian wrapper, and its release, federation and sync workflows, as copies of its templates. `knowledge-sync.yaml` moves them to KTL's newest release. |
| `.lokf/curators/` | The public keys the provenance check verifies a curator's signed commit against. |
| `website/` | The site, from the ktl-website templates: a page per concept with its trust label, the bundle's health, and the four `lokf export` files under `/knowledge/`. |
| `knowledge_bundle` | A link to `.lokf/knowledge/`, the doorway for a file manager or Obsidian. |

## How it stays current

A member's new release changes nothing here until a person confirms a member concept that names it. The librarian for this bundle is a script, not a model: `knowledge-federate.py members`, run by the sidecar's librarian wrapper in place of an agent. It lists each member's releases, picks the newest that carries a bundle zip, verifies its checksum and attestation, and proposes the change as a pull request through the sidecar's pen. Until a person confirms that change, the member reads as edited since a person last confirmed it, so the health line shows which members have moved. `members --add <owner>/<repo>` drafts a new member the same way, as a `MemberDomain` when its release is a domain. [Confirming a member change](curation.md) gives the steps for both.

The scheduled librarian always reads a bundle whose sources are release URLs as quiet, with nothing to do. So the federation workflow dispatches the librarian once a week instead.

A merged member change is a release of this domain: the release rules treat `chore(lokf)` as a minor version. Each release carries the bundle as a zip with its checksum, and rebuilds the workspace.

## The workspace

The workspace is the graph built from this domain's members, one named graph per bundle. A job that runs no agent builds it on each release of this domain: the release job dispatches `knowledge-federation.yaml`, which runs `.lokf/scripts/knowledge-federate.py build` from the tag. In order, as [How the workspace stays current](https://w3id.org/ktl/docs/federation/#how-the-workspace-stays-current) describes, the build:

1. resolves the members into a lock, one entry per release with its URL, checksum, tier and the domains that named it, following each member that is a domain;
2. verifies each zip against its checksum and its build attestation, refusing a zip with a symbolic link or a path outside its root;
3. checks that each bundle's `index.md` names the namespace its member concept declares, then registers and exports it with the `lokf` toolkit;
4. loads each bundle's graph into a named graph whose IRI is its namespace, with one more graph holding the lock as DCAT and VoID;
5. gates every typed relation whose target lies outside the asserting bundle against the registry, as the domain's `unowned_targets` says;
6. swaps the result in whole, so a failed build leaves the previous workspace in place.

The release carries the workspace as `workspace-<tag>.zip`. The site serves it under `/workspace/`, starting at `index.md`, which lists each member's version, namespace, the domain that named it, licence and health line at the release. Then come the lock, the registry, `graph.nq`, each bundle's exports, the gate report and the stored queries. `labels.rq` computes every trust label at the moment it runs, `moved.rq` lists the members edited since the domain's last confirmation, and `unowned.rq` is the gate. No label is stored.

## Reading the workspace

Build and read it locally:

```bash
cd .lokf && just lokf-install && cd ..
uv run --project .lokf .lokf/scripts/knowledge-federate.py build --tag v0.1.0 --release-base https://github.com/noelmcloughlin/ktl-federation/releases/tag
uv run --project .lokf .lokf/scripts/knowledge-federate.py query snapshot/queries/labels.rq
uv run --project .lokf .lokf/scripts/knowledge-federate.py serve
uv run --project .lokf .lokf/scripts/knowledge-federate.py mcp
```

`serve` is the toolkit's SPARQL endpoint and graph page over the union of the graphs. `mcp` is the `lokf-registry` Model Context Protocol (MCP) server that section 11.4 of the LOKF specification describes, with the workspace index as its instructions, so an agent reads the index first. Register it with your agent as a stdio server: that command, run from this repository. Each one takes `--snapshot <folder>`, so it reads an unpacked `workspace-<tag>.zip` too. For a team, the Oxigraph server image serves `graph.nq` read-only from a container, as the curator's [domain bundle page](https://github.com/noelmcloughlin/knowledge-trust-ladder/blob/main/skills/ktl-curator/references/domain-bundle.md#reading-the-workspace) shows.

## What remains a design

This host serves the static workspace and hosts no endpoint. A team that wants one runs the container. Three parts remain designs: loading a member's graph on first use, harvesting remote artifacts under the `sensitivity` gate of section 11.5, and per-query permissions, which stay with the store's access control. [What exists, and what remains a design](https://w3id.org/ktl/docs/federation/#what-exists-and-what-remains-a-design) lists each part and where it lives.

## Decisions this domain has made

KTL's federation page lists the [decisions an adopter must make](https://w3id.org/ktl/docs/federation/#decisions-an-adopter-must-make). This domain's answers:

- **Pin.** Each member concept names one release, and a person confirms each move. A domain that names this one adds a pin of its own, so a member's release reaches that domain's workspace only after a confirmation and a release here, then a confirmation and a release there.
- **Who arbitrates.** This domain's owner, by a confirmed concept in this bundle, never by a rewrite of a member. There is no cross-bundle claim yet.
- **What a member adds.** Members are admitted on the policy's four tests. The stricter value test asks that readers query across a member or that other members link into it. No member links into another yet, so this federation has proved its mechanism, not yet its worth.
- **Permissions.** Every member is a public repository. A bundle that must not be seen whole does not join.
