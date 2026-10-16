# KTL Federation

A museum that borrows for an exhibition never owns what it shows. Each piece arrives under a loan agreement that names it exactly, with a condition report that says what state it came in, and the lender's name stays on the label beside it. KTL Federation does the same for knowledge bundles.

[Knowledge Trust Ladder](https://w3id.org/ktl/) (KTL) keeps one repository's knowledge as a bundle, with the trust in every claim left visible. That bundle is the repository's context layer: the checked part of what it knows, which sits between its sources and whoever reads them, a person or an agent, and lasts from one task to the next. [The KTL context layer page](https://w3id.org/ktl/docs/context-layer/) designs the step beyond one repository, a federation in which many bundles, each kept and trusted where it lives, are read as one graph. [KTL's own bundle keeps a summary of that page](https://w3id.org/ktl/knowledge/explanation/context-layer), labelled with how far it has been checked. This repository is the design built: the first host of the federation's top domain.

The domain's own bundle is a thin [LOKF](https://lokf.nolan-nichols.com) bundle whose concepts are other repositories' bundles. Each member concept is the loan agreement: it names one released zip of a bundle and that zip's checksum, and a person confirms that the bundle belongs. Nothing is copied from a member, and each member keeps its own trust labels. The workspace is where the loans are shown together: the graph a reader queries, built from the releases the members name. It holds one named graph per bundle, so every claim still carries the name of the bundle that made it, and it is swapped in whole on each release of this domain.

The complete documentation is at [w3id.org/ktl/federation](https://w3id.org/ktl/federation/). [The architecture](https://w3id.org/ktl/federation/docs/architecture/) says what the domain holds, how it stays current and how the workspace is built.

> **Only want to ask?** Install the docent skill, `ktl-docent`, into any agent you already use, by whichever route [the install page](https://w3id.org/ktl/docs/install/) gives for your machine, and ask it about this federation. It answers from this repository's bundle and says how far each answer has been checked.
>
> **Agents:** if `.lokf/knowledge/index.md` exists, read it first. `llms.txt` says how to weigh it.

## Members

| Member | Its bundle | Its member concept here |
| --- | --- | --- |
| Knowledge Trust Ladder, the repository that publishes the KTL skills | [w3id.org/ktl/knowledge](https://w3id.org/ktl/knowledge/) | [members/knowledge-trust-ladder](https://w3id.org/ktl/federation/knowledge/members/knowledge-trust-ladder) |
| AI-LinkMO, a reference implementation of operational AI governance over open AI-governance data | [its knowledge pages](https://noelmcloughlin.github.io/ai-linkmo/knowledge/) | [members/ai-linkmo](https://w3id.org/ktl/federation/knowledge/members/ai-linkmo) |
| gist, a LinkML rendering of Semantic Arts' gist upper ontology, from the lmodel organisation | [w3id.org/lmodel/gist/knowledge](https://w3id.org/lmodel/gist/knowledge/) | [members/gist](https://w3id.org/ktl/federation/knowledge/members/gist) |

The member concept names the release the member is at and the checksum of its zip. [The workspace index](https://w3id.org/ktl/federation/workspace/index.md) lists each member's release and its health line at the last build. [The federation policy](https://w3id.org/ktl/federation/knowledge/policies/federation) says what admits a bundle, and [the top domain](https://w3id.org/ktl/federation/knowledge/domains/top) names the gate policy.

## License

The repository is under the [Apache License 2.0](LICENSE). The knowledge bundle is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), as its `index.md` says. Contributions follow [CONTRIBUTING.md](CONTRIBUTING.md) and the [AI Covenant](AI_COVENANT.md).
