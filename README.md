# KTL Federation

The top domain of the [Knowledge Trust Ladder](https://github.com/noelmcloughlin/knowledge-trust-ladder) (KTL) federation. Its knowledge bundle, under `.lokf/knowledge/`, is a thin [LOKF](https://lokf.nolan-nichols.com) bundle whose concepts are other repositories' knowledge bundles: each member names one released zip of a bundle and that zip's checksum, and a person confirms that it belongs. Nothing is copied from a member. The workspace, the graph a reader queries, is built from the releases the members name, one named graph per bundle, and swapped in whole on each release of this domain.

The design is [the KTL context layer page](https://noelmcloughlin.github.io/knowledge-trust-ladder/docs/context-layer/), which places KTL in the industry's talk of a context layer, says why one bundle is already one repository's layer, and sets out how many bundles federate into one. This repository is that design run for real, with KTL's own bundle, the bundle of its reference host ai-linkmo, and the bundle of lmodel's gist as the first members. The LOKF specification's section 11, "Federation: registries of bundles", supplies the registry and the routing; the domain, its schema and the confirmation of membership are what this repository adds.

> **Two ways in.** This README is one; the other is a docent, a museum's name
> for a guide. Install
> [`ktl-docent`](https://github.com/noelmcloughlin/knowledge-trust-ladder) into
> whatever agent you already use
> (`npx skills add noelmcloughlin/knowledge-trust-ladder --skill ktl-docent --global --yes`)
> and ask it anything about this project. It answers from `.lokf/knowledge/`,
> the checked part of what the project knows, and says how far each answer has
> been trusted (still a draft, checked by automation only, or confirmed by a
> named person). It opens the source for exact values, and records what it
> could not answer so the gap gets filled. The same docent serves a person at a
> prompt, an agent reading this file, or a chatbot that can load a skill.
> **Agents:** if `.lokf/knowledge/index.md` exists, read it first. `llms.txt`
> says how to weigh it.

## Members

| Bundle | Release named | Namespace |
| --- | --- | --- |
| [knowledge-trust-ladder](.lokf/knowledge/members/knowledge-trust-ladder.md) | v0.43.0 | `https://w3id.org/ktl/knowledge/` |
| [ai-linkmo](.lokf/knowledge/members/ai-linkmo.md) | v0.3.2 | `https://noelmcloughlin.github.io/ai-linkmo/knowledge/` |
| [gist](.lokf/knowledge/members/gist.md) | v0.3.3 | `https://w3id.org/lmodel/gist/knowledge/` |

[The federation policy](.lokf/knowledge/policies/federation.md) says what admits a bundle: released with the KTL sidecar's release workflow, valid on LOKF core or on a schema it publishes, a stable namespace under an authority its publisher controls, and one accountable owner. [The top domain](.lokf/knowledge/domains/top.md) names the gate policy: a typed relation whose target lies in no member's namespace fails the build.

## What is here

| Path | Holds |
| --- | --- |
| `.lokf/knowledge/` | The domain bundle: `domains/top.md`, `members/`, `policies/federation.md`, and the `index.md` a reader opens first. |
| `.lokf/domain.yaml` | The domain schema. It declares `Domain`, `MemberBundle` and `ReleaseDistribution` over LOKF core, so `lokf validate` checks a member's namespace, release and checksum. |
| `.lokf/scripts/`, `.github/workflows/` | The KTL sidecar's registrar gate, librarian wrapper and release workflow, as copies of its templates. |
| `website/` | The site, from the ktl-website templates: a page per concept with its trust label, the bundle's health, and the four `lokf export` files under `/knowledge/`. |
| `knowledge_bundle` | A link to `.lokf/knowledge/`, the doorway for a file manager or Obsidian. |

## How it stays current

A member's new release changes nothing here until a person confirms a member concept that names it. The librarian for this bundle is a script, not a model: it lists each member's releases, picks the newest that carries a bundle zip, verifies its checksum and attestation, and proposes the change as a pull request through the sidecar's own pen. Until it is confirmed, the member reads as edited since a person last confirmed it, which is how the health line says which members have moved.

The workspace build, laid down by the KTL sidecar's federation templates, runs on each release of this domain: it resolves the members into a lock, verifies every zip, registers and exports each bundle with the `lokf` toolkit, loads one named graph per bundle, gates cross-bundle links, and swaps the result in whole. That build is the next step; this repository holds the domain it will read.

## License

The repository is under the [Apache License 2.0](LICENSE). The knowledge bundle is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), as its `index.md` says. Contributions follow [CONTRIBUTING.md](CONTRIBUTING.md) and the [AI Covenant](AI_COVENANT.md).
