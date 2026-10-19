**Position paper**
# Skin: Publishing for AI agents

The web was built around a simple assumption: information is published in a form that people can navigate and read. Websites combine information with its presentation through pages, navigation structures, and language-specific content. AI agents introduce a different kind of consumer, capable of interpreting semantic information and generating responses adapted to individual questions.

Today, agents primarily access information through mechanisms designed to retrieve and interpret existing web content. While these approaches are essential for using the enormous body of information already online, they also inherit the limitations of material originally organized for human consumption.

Skin explores a complementary publication model in which individuals and organizations publish structured semantic information directly for AI agents. Rather than defining how information should be presented, publishers maintain the facts they wish to make available, while consuming agents determine how to interpret and communicate them.

The proposal combines publisher-controlled profiles, atomic semantic facts, a shared schema, and direct retrieval. Its objective is not to replace websites or existing retrieval technologies, but to examine what becomes possible when information can be published for intelligent agents without first being organized into a human-facing interface.

## From websites to information sources

Publishing information online has traditionally meant building a website. Whether introducing a company, describing a product, or explaining a service, publishers organize information into pages, navigation structures, and often multiple language versions.

This organization is largely dictated by how people consume information. Visitors browse, follow links, read explanations, and gradually locate what interests them. Publishers must anticipate those journeys and provide an interface that accommodates them.

Even a relatively simple project can therefore require dozens of pages, navigation categories, and translations. Much of this work concerns not the information itself, but the different ways people might need to access it.

AI agents change that relationship. They can understand questions expressed in natural language, interpret semantic relationships, and construct responses suited to a particular context. Instead of following a publisher's predefined navigation, an agent can identify relevant information and present it directly to its user.

The publisher still needs to make the information available, but no longer necessarily needs to determine how every visitor will navigate or encounter it.

This leads to the question at the center of Skin:

**If LLMs can interpret information and generate its presentation, why must publishers first organize that information into websites designed for humans?**

Consider a small project that wants to explain what it does, who it serves, how it works, and how to get in touch. A conventional website might distribute those details across an introduction, an about page, several feature pages, and a contact section. The same information might then be translated into multiple languages.

An agent could instead retrieve the underlying information and answer questions about the project directly, without requiring the publisher to anticipate the questions or maintain the pages through which visitors would traditionally find their answers.

Skin proposes treating this underlying information as the publication itself.

A Skin profile is an information source intended for AI agents. Its publisher maintains what is available, while consuming agents decide how to use and communicate it. A profile can exist independently of a website, and the same information can support different agents, interfaces, languages, and use cases.

This is not an attempt to make websites easier to crawl. It is an exploration of how information might be published if a human-facing website were never required in the first place.

## Publishing facts instead of pages

Human-oriented publications typically communicate through prose. A company's website may combine factual statements with explanations, storytelling, promotional language, and visual presentation. This works well for people, but requires AI agents to identify relevant facts within material that was not necessarily written for machine interpretation.

A company might describe itself as a team of passionate innovators delivering cutting-edge solutions. Such language may communicate enthusiasm, but it offers little precise information about the company's actual capabilities.

Skin approaches publication differently, representing information as atomic semantic facts rather than presentation-oriented prose.

The following fragment illustrates how Skin's prototype represents information about the service itself:

```json
{
  "profile": {
    "name": "Skin",
    "type": "service",
    "facts": [
      {
        "type": "capability",
        "subject": "AI agents",
        "value": "retrieve published facts",
        "from": "Skin",
        "insteadOf": "scraped information"
      },
      {
        "type": "authoring",
        "input": "natural language conversation",
        "output": "machine-readable index",
        "consumer": "AI agents"
      }
    ]
  }
}
```

The fragment describes two aspects of Skin: how agents can retrieve published information and how that information can be authored. Each fact uses properties appropriate to its meaning, while the shared structure allows an agent to interpret them within the same profile.

The representation describes information without prescribing how an agent should present it. An agent could use these facts to answer questions about Skin, generate a description of its capabilities, or incorporate them into a broader explanation.

Atomicity does not mean reducing every statement to a simplistic three-part relationship. Useful information frequently includes qualifications that are essential to its meaning. A service may be available only in certain countries, a price may depend on specific conditions, or an offer may have a defined validity period. A semantic representation must be able to preserve such context and the relationships between facts, rather than fragmenting them into disconnected statements.

These qualifications belong to the publisher. Skin should allow conditions, scope, and validity periods to be expressed when relevant, without requiring them for every fact or deciding when published information has become obsolete.

The objective is not to eliminate interpretation, which remains necessary even with structured information. It is to reduce the need for agents to extract factual meaning from prose whose primary purpose was human presentation.

### A shared schema

For independent publishers and agents to exchange information, a common structure is necessary. Skin therefore proposes an open schema defining shared fact types, properties, and relationships, while leaving semantic values open to interpretation by language models.

The distinction between structure and semantic values is central to the approach.

A schema can establish that properties such as subject, value, and from serve different roles within a fact without attempting to enumerate every possible subject, value, or source. The structural vocabulary provides consistency, while semantic values remain expressive enough to describe a broad range of activities and relationships.

This is a deliberate trade-off. Comprehensive ontologies can provide precise definitions and strong machine-readable semantics, but they also require extensive vocabularies that must evolve as new domains and concepts emerge.

Skin instead relies partly on the ability of language models to interpret natural-language semantic values within a consistent structure. It does not attempt to standardize every possible concept in advance.

That flexibility introduces uncertainty. Different models may interpret ambiguous values differently, and a shared schema cannot guarantee identical interpretations across consumers. The proposal is therefore not that structure eliminates ambiguity, but that a common structural vocabulary, combined with modern language models, may offer a useful balance between interoperability and expressiveness.

## What changes for publishers

Separating information from presentation changes more than the format in which information is stored. It also changes how publishers control, maintain, and distribute it.

Four properties define the intended publication model.

### Authored

A Skin profile is created and maintained by an authorized publisher. Ownership verification is a prerequisite for creating and publishing a profile, preventing third parties from claiming identities they do not control.

For a domain-associated entity, this means demonstrating control of the corresponding domain. Domain ownership, however, does not imply operating a website: a publisher can control a domain without hosting pages, applications, or other public infrastructure.

Verification establishes authority to publish on behalf of an identity, not the factual accuracy of everything published. A verified company may still publish incomplete, misleading, or incorrect information, just as it can on its own website.

The important distinction is that agents can identify information explicitly published by an entity, rather than relying exclusively on descriptions assembled from external sources.

### Real-time

Web publication and automated retrieval do not necessarily happen at the same time. A publisher may update a page immediately, while crawlers, search indexes, and other intermediate systems continue exposing older versions.

Skin allows publishers to update their information directly at its source, making those changes available without waiting for a crawling or indexing cycle.

This does not guarantee that every agent will immediately consume the latest information. Agents may cache responses or rely on previously retrieved data. Nor does Skin determine whether information is outdated: maintaining published facts remains the publisher's responsibility.

Real-time refers to the availability of changes at the source, not a guarantee that every consumer always holds the latest version.

### No infrastructure

Publishing information for AI agents should not require building and operating a website.

A hosted Skin service can provide the authoring interface, storage, and retrieval mechanisms on behalf of publishers. Individuals and organizations can therefore maintain profiles without deploying servers, developing applications, or implementing their own APIs.

The underlying architecture is intended to remain open, allowing independent implementations and self-hosted services to publish compatible information. The convenience of hosted infrastructure should not become a requirement to use a particular provider.

### Multi-language

Traditional multilingual websites often maintain separate versions of the same information. Each translation must be created, updated, and kept consistent with the others.

Skin proposes publishing semantic facts rather than maintaining language-specific presentations. A consuming agent can interpret those facts and formulate responses in the language appropriate to its user.

This does not guarantee perfect translation or identical wording across languages. Specialized terminology, cultural context, and ambiguous concepts may require additional information, while publishers relinquish some control over the exact language generated by consuming agents.

Nevertheless, the publisher can maintain a shared semantic source rather than repeatedly translating complete pages or predefined answers.

These four properties—**Authored, Real-time, No-infra, and Multi-language**—follow from a common principle: the publisher maintains information, while consuming agents take responsibility for its presentation.

## The role of the existing web

AI agents already retrieve and interpret information from websites, documents, databases, and other sources. Crawling, indexing, and retrieval-augmented generation make an enormous body of existing material accessible to intelligent systems.

These techniques are indispensable, but they also face limitations inherent in adapting human-oriented publications for automated consumption.

Information may be distributed across several pages, mixed with promotional language, or expressed differently in multiple places. Agents must determine which statements are relevant, whether they refer to the same entity, and how to reconcile incomplete or conflicting descriptions. Updates may take time to reach indexes, while extracted content can lose qualifications or context that were clear in its original presentation.

Structured-data conventions and retrieval techniques help address these difficulties, but they do not remove the distinction between publishing information for people and retrieving it for machines.

Skin starts from the other end of that process.

Rather than asking how an agent can reconstruct information from an existing website, it asks how a publisher can make that information available directly to agents.

This does not require the publisher to operate a website at all. A Skin profile may be the only information source an individual or organization chooses to maintain for agent consumption.

For publishers with existing infrastructure, the two approaches can coexist. A website or content management system might update a Skin profile automatically, while existing content could help initialize a profile. The purpose is not to duplicate every web page in another format, but to maintain information that agents can consume independently of its human-facing presentation.

Discovery remains a separate but essential challenge. Agents must be able to identify relevant entities and locate their profiles, potentially through search engines, directories, references, or dedicated agent-accessible services. A profile that cannot be discovered has limited practical value, even if its information is well structured.

Separating discovery from publication does not make discovery unimportant. It allows different discovery mechanisms to evolve without requiring publishers to change how they express their information.

## Relationship to existing semantic technologies

Structured information is not a new idea. RDF, JSON-LD, Schema.org, and knowledge graphs already provide ways to describe entities, properties, and relationships in machine-readable forms.

Skin shares the underlying objective of making information easier for machines to interpret, but approaches the problem from a different publication perspective.

Schema.org, for example, provides a broad vocabulary that can describe information embedded in or associated with web resources. RDF offers a general model for representing relationships, while JSON-LD provides a way to express linked data using JSON.

These technologies can support rich semantic representations and may be useful within agent-oriented systems. Skin does not depend on claiming that they are inadequate or that structured data must be reinvented.

The distinction lies in the proposed combination of a publication model and an interpretation model.

First, the structured information is the publication itself, not necessarily an annotation of a human-facing resource. Second, the shared schema is intentionally leaving many semantic values to be interpreted by language models rather than defined through an extensive ontology. Third, the information is maintained directly by its authorized publisher and made available through a dedicated retrieval interface.

This choice sacrifices some of the determinism offered by more formally defined vocabularies in exchange for a simpler authoring model and greater flexibility across domains.

Whether that balance proves useful depends on how consistently agents interpret the information and how effectively publishers can express the facts they need. These are practical questions for implementation and evaluation, rather than assumptions that the proposal has already resolved.

## Authoring and consuming information

Although Skin uses structured representations, publishers should not need to understand schemas or write JSON manually.

Conversational authoring offers one possible interface. A publisher describes an organization, activity, product, or service through natural-language interaction, while an authoring system prepares structured facts for review and publication.

The publisher remains responsible for approving the information. The system assists in organizing it rather than independently deciding what the publisher should claim.

Other interfaces, including forms and authenticated APIs, can support the same architecture. Existing systems may publish updates automatically, allowing a Skin profile to reflect changes already made through a publisher's established workflows.

For consuming agents, the process is different. Once an agent has located a profile, it retrieves the relevant information and uses it to answer questions, compare entities, generate summaries, or support other tasks.

The publisher does not need to anticipate every possible question or maintain predefined answers. Different agents can use the same underlying facts in different contexts, constructing presentations appropriate to their users.

This separation is what allows information to remain useful beyond any particular website, interface, or conversational application.

## Open questions and limitations

Skin is an architectural proposal, not an established standard, and several questions remain open.

A semantic schema must be expressive enough to represent complex information without becoming an exhaustive ontology. Qualifications, relationships, and contextual dependencies need to survive interpretation, while different language models may produce different results from the same facts.

Ownership verification prevents unauthorized publication under another entity's identity, but it does not establish factual truth. Publishers remain responsible for the information they provide, and agents may still need to compare it with independent sources.

Direct publication improves the availability of updates at the source, but cannot dictate downstream caching behavior. Multilingual interpretation reduces the need for publisher-maintained translations without guaranteeing identical responses across languages.

Discovery and adoption are equally important. Publishers need reasons to maintain agent-oriented profiles, while agent developers need reliable ways to find and consume them. An open schema alone does not create an ecosystem.

These limitations do not invalidate the publication model, but they define questions that must be addressed as it develops.

The proposed schema and validation mechanisms are intended to be open and independently implementable, allowing different services and applications to participate without depending on a single hosted platform.

## Conclusion

The web established a publication model in which information and its presentation are closely connected. Publishers organize content into resources that people can navigate, while automated systems retrieve and interpret those resources as best they can.

AI agents introduce a different kind of consumer. They can interpret semantic information, respond to questions, and generate contextual presentations without requiring publishers to define every page, navigation path, or language-specific response.

Skin explores a complementary model built around that capability: publishers maintain structured information directly for agents, rather than first organizing it into interfaces designed for humans.

The proposal does not eliminate the need for websites, search, or existing retrieval technologies. It simply questions whether those mechanisms must always stand between a publisher and an intelligent consumer.

**If agents can determine how information should be presented, publishers may no longer need to define its presentation at all.**

Skin is an exploration of what becomes possible when that constraint is removed.

---

**Author:** Raphael Del Blanco  
**Published:** October 2026<br><br>
https://profiles.skin
