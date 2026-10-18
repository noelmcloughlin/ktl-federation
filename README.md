# KTL Federation

A museum that borrows for an exhibition never owns what it shows: each loan is named exactly, its condition recorded, and the lender's name kept on the label. KTL Federation does the same for knowledge bundles.

[Knowledge Trust Ladder](https://w3id.org/ktl/) (KTL) keeps a repository's checked knowledge as a bundle: the repository's context layer, with trust in every claim left visible. [The design](https://w3id.org/ktl/docs/context-layer/) goes beyond one repository: a federation of many bundles, each kept and trusted where it lives, read as one graph. This repository is the domain of one such federation.

The [domain](https://w3id.org/ktl/federation/knowledge/) is a thin [LOKF](https://lokf.nolan-nichols.com) bundle whose concepts are other repositories' bundles. Each member concept is the loan agreement: it names one released zip and its checksum, and a person confirms that the bundle belongs. The workspace and graph that a reader queries are built from member releases, with one named graph per bundle and every claim visible. The documentation is at [w3id.org/ktl/federation](https://w3id.org/ktl/federation/). The [architecture](https://w3id.org/ktl/federation/docs/architecture/) says what the domain holds, how it stays current and how the workspace is built.

> **Only want to ask?** Install `ktl-docent` into any agent you use, by a route from [the install page](https://w3id.org/ktl/docs/install/), and ask it about this federation. It answers from the bundle and says how far each answer has been checked.
>
> **Agents:** if `.lokf/knowledge/index.md` exists, read it first. `llms.txt` says how to weigh it.

## Members

| Member | Its bundle | Its member concept here |
| --- | --- | --- |
| KTL, which publishes the skills | [w3id.org/ktl/knowledge](https://w3id.org/ktl/knowledge/) | [members/knowledge-trust-ladder](https://w3id.org/ktl/federation/knowledge/members/knowledge-trust-ladder) |
| AI-LinkMO, a reference implementation of operational AI governance | [its knowledge pages](https://noelmcloughlin.github.io/ai-linkmo/knowledge/) | [members/ai-linkmo](https://w3id.org/ktl/federation/knowledge/members/ai-linkmo) |
| gist, a LinkML rendering of Semantic Arts' gist upper ontology, from lmodel | [w3id.org/lmodel/gist/knowledge](https://w3id.org/lmodel/gist/knowledge/) | [members/gist](https://w3id.org/ktl/federation/knowledge/members/gist) |

Each member concept names its release and checksum, and [the workspace index](https://w3id.org/ktl/federation/workspace/index.md) lists every member's release and health line. [The federation policy](https://w3id.org/ktl/federation/knowledge/policies/federation) says what admits a bundle and what the build does with a link no member owns.

## License

The repository is under the [Apache License 2.0](LICENSE), and the knowledge bundle under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Contributions follow [CONTRIBUTING.md](CONTRIBUTING.md) and the [AI Covenant](AI_COVENANT.md).
