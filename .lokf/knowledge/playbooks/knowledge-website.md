---
type: Playbook
id: https://w3id.org/ktl/federation/knowledge/playbooks/knowledge-website
title: The knowledge website
description: How the site at noelmcloughlin.github.io/ktl-federation is built from the bundle, the README, docs/ and the changelog, how to preview it, what to edit for each part, and why the federation workflow deploys it on this host, not the website workflow.
genre: how-to
resource: website/README.md
references:
  - https://w3id.org/ktl/federation/knowledge/datasets/workspace
sources:
  - resource: website/README.md
  - resource: website/site.toml
  - resource: .github/workflows/knowledge-website.yaml
  - resource: .github/workflows/knowledge-federation.yaml
  - resource: SECURITY.md
generated:
  by: process:ktl-librarian
  at: "2026-11-15T01:15:09Z"
status: draft
verified:
  - by: process:ktl-librarian
    at: "2026-10-29T11:44:32Z"
---

# Overview

The site is the Hugo project in `website/`, copied from the ktl-website templates. `website/site.toml` sets its address, `https://noelmcloughlin.github.io/ktl-federation/`. Every page comes from a file the repository already holds, so a change to the site is a change to that file.

## What each page comes from

- Each concept in `.lokf/knowledge/` becomes a page under `knowledge/`, with its trust label, its sources and its typed relations both ways.
- The four files `lokf export` writes are served under `knowledge/`, beside each concept's Markdown file and its JSON-LD. The bundle log is served as an Atom feed, `knowledge/log.xml`.
- The README becomes the home page, each page under `docs/` becomes a page under `docs/`, and `CHANGELOG.md` becomes a page per release under `changelog/`.
- The home page and each docs page are served as Markdown too, at the page's path with `.md` added.

The repository holds no LinkML schema project of its own, so the site's Schema part shows LOKF core, the schema the bundle is written in. `site.toml` leaves `browse` unset, so the site serves no data.

## Preview it

You need bash, git and [uv](https://docs.astral.sh/uv/).

```bash
cd website
scripts/build.sh          # dist/, with the search index, then checks every link between its pages
scripts/build.sh serve    # http://localhost:1313/ktl-federation/, rebuilt as you edit
```

Both run `scripts/prepare.sh` first. It runs `lokf export` from the sidecar's own environment in `.lokf/`, and writes the generated pages. Nothing it writes is committed. Hugo and Pagefind come from PyPI, at the versions `website/uv.lock` holds.

## What to edit

- A page's words: the file the page comes from. Change a concept through the librarian and the curator, like any other change to the bundle.
- The site's values: `site.toml`, which is this repository's own. A comment above each value says what it takes.
- The site's look: `assets/css/custom.css`, which is this repository's own and loads last. The colours and the trust tones are custom properties at the top of `assets/css/site.css`.

Every other file in `website/` is a copy of the ktl-website template, so change one of those in KTL, never here.

## Who deploys it

This host has one Pages deployer, the federation workflow, so it leaves `KNOWLEDGE_WEBSITE_ENABLED` unset.

- `knowledge-website.yaml` builds the site and checks every link: on a pull request that touches the site's sources, on a push to the default branch that does, every Monday, and by hand. Its `deploy` job runs only once `KNOWLEDGE_WEBSITE_ENABLED` is `true`, so here it deploys nothing.
- `knowledge-federation.yaml` builds the website on each release, beside [the workspace](../datasets/workspace.md). A push to the default branch rebuilds the website alone and reuses the newest released workspace. Its `publish` job deploys the result to Pages.

A workspace that holds internal metadata is uploaded to the release only, and never deployed to the site.
