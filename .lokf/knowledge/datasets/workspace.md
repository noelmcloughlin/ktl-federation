---
type: Dataset
id: https://w3id.org/ktl/federation/knowledge/datasets/workspace
genre: reference
title: The KTL federation workspace
description: The graph each release of this domain builds from its members, one named graph per bundle plus a graph for the lock. It names the build's checks, what the release's workspace zip and the site's /workspace/ folder hold, the stored queries, and the serve, mcp and Oxigraph ways to read it.
resource: https://w3id.org/ktl/federation/workspace/index.md
relatedTo:
  - https://w3id.org/ktl/federation/knowledge/domains/ktl-federation
sources:
  - resource: docs/architecture.md
  - resource: https://w3id.org/ktl/federation/workspace/index.md
  - resource: .github/workflows/knowledge-federation.yaml
generated:
  by: process:ktl-librarian
  at: "2026-10-26T18:19:07Z"
status: draft
verified:
  - by: process:ktl-librarian
    at: "2026-10-29T11:44:32Z"
---

# Overview

The workspace is the graph built from this domain's members, one named graph per bundle. It is the domain's context layer, which readers query. A job that runs no agent builds it on each release of this domain: the release job dispatches `knowledge-federation.yaml`, which runs `.lokf/scripts/knowledge-federate.py build` from the tag.

A member's new release changes nothing in the workspace until a person confirms the member concept that names it. Until then, the build keeps the release a person last confirmed, leaves out a new member, and lists both as waiting in the workspace index.

## How it is built

In order, as [How the workspace stays current](https://w3id.org/ktl/docs/federation/#how-the-workspace-stays-current) describes, the build:

1. resolves the members into a lock, one entry per release with its URL, checksum, tier and the domains that named it, following each member that is a domain;
2. verifies each zip against its checksum and its build attestation, refusing a zip with a symbolic link or a path outside its root;
3. checks that each bundle's `index.md` names the namespace its member concept declares, then registers and exports it with the `lokf` toolkit;
4. loads each bundle's graph into a named graph whose IRI is its namespace, with one more graph holding the lock as DCAT and VoID;
5. gates every typed relation whose target lies outside the asserting bundle against the registry, as the domain's `unowned_targets` says;
6. swaps the result in whole, so a failed build leaves the previous workspace in place.

## What a release carries

The release carries the workspace as `workspace-<tag>.zip`. The site serves it under `/workspace/`, starting at [`index.md`](https://w3id.org/ktl/federation/workspace/index.md). That index lists each member's version, namespace, the domain that named it, licence and health line at the release. Then come the lock, the registry, `graph.nq`, each bundle's exports, the gate report and the stored queries:

- `labels.rq` computes every trust label at the moment it runs;
- `moved.rq` lists the members edited since the domain's last confirmation;
- `unowned.rq` is the gate.

No label is stored.

## Reading it

`knowledge-federate.py` builds and reads the workspace locally, from the repository's root:

```bash
cd .lokf && just lokf-install && cd ..
uv run --project .lokf .lokf/scripts/knowledge-federate.py build --tag v0.1.0 --release-base https://github.com/noelmcloughlin/ktl-federation/releases/tag
uv run --project .lokf .lokf/scripts/knowledge-federate.py query snapshot/queries/labels.rq
uv run --project .lokf .lokf/scripts/knowledge-federate.py serve
uv run --project .lokf .lokf/scripts/knowledge-federate.py mcp
```

- `serve` is the toolkit's SPARQL endpoint and graph page over the union of the graphs.
- `mcp` is the `lokf-registry` Model Context Protocol (MCP) server that section 11.4 of the LOKF specification describes. It takes the workspace index as its instructions, so an agent reads the index first. An agent registers it as a stdio server: that command, run from this repository.
- Each one takes `--snapshot <folder>`, so it reads an unpacked `workspace-<tag>.zip` too.

This host serves the static workspace and hosts no endpoint. A team that wants one serves `graph.nq` read-only from the Oxigraph server image in a container, as the curator's [domain bundle page](https://w3id.org/ktl/knowledge/playbooks/domain-bundle#reading-the-workspace) shows. Per-query permissions stay with the store's access control.

## What remains a design

Fetching a member from a private repository remains a design, which section 11.5 of the LOKF specification leaves to a later version.
