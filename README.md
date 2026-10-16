# KTL Federation

The top domain of the [Knowledge Trust Ladder](https://github.com/noelmcloughlin/knowledge-trust-ladder) (KTL) federation. Its knowledge bundle is a thin [LOKF](https://lokf.nolan-nichols.com) bundle whose concepts are other repositories' knowledge bundles. Each member names one released zip of a bundle and that zip's checksum, and a person confirms that it belongs. Nothing is copied from a member. The workspace, the graph a reader queries, is built from the releases the members name, one named graph per bundle, and swapped in whole on each release of this domain.

The complete documentation is at [noelmcloughlin.github.io/ktl-federation](https://noelmcloughlin.github.io/ktl-federation/). [The architecture](docs/architecture.md) says what the domain holds, how it stays current and how the workspace is built. The design it runs is [the KTL context layer page](https://noelmcloughlin.github.io/knowledge-trust-ladder/docs/context-layer/).

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

[The federation policy](.lokf/knowledge/policies/federation.md) says what admits a bundle, and [the top domain](.lokf/knowledge/domains/top.md) names the gate policy. The workspace built from these members is served under [`/workspace/index.md`](https://noelmcloughlin.github.io/ktl-federation/workspace/index.md) once the first release is published.

## License

The repository is under the [Apache License 2.0](LICENSE). The knowledge bundle is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), as its `index.md` says. Contributions follow [CONTRIBUTING.md](CONTRIBUTING.md) and the [AI Covenant](AI_COVENANT.md).
