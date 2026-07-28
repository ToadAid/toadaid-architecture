# Trusted Channel Separation Contract

## Purpose

ToadAid systems receive information with different trust semantics.

Runtime configuration, operator input, conversation history, retrieved evidence, memory, provider output, and authority decisions must not become interchangeable merely because they can all be serialized as text.

This contract defines the structural separation required between those channels.

## Core law

> **Inputs with different trust semantics must travel through different structural channels.**

A provenance label inside one undifferentiated prompt is not equivalent to trusted-channel separation.

## Required channel classes

A system should distinguish the channel classes relevant to its runtime, including:

```text
trusted runtime configuration
operator / task input
conversation context
retrieved evidence
canonical memory
provider output
authority decisions
```

Additional domain-specific channels may exist, but unknown channels should fail closed rather than inherit trust from a neighboring class.

## Trusted runtime configuration

Trusted runtime configuration may establish bounded facts such as:

- agent identity;
- provider role;
- current sanitized capability projection;
- fixed doctrine or behavior constraints;
- invocation and confinement policy references.

It must not be writable through ordinary operator messages, retrieved documents, provider output, or conversation history.

Trusted configuration can establish runtime framing. It does not establish that every framed claim is externally true.

## Operator and task input

Operator input expresses requests, instructions, questions, and supplied content.

It may not directly rewrite:

- agent identity;
- runtime policy;
- capability grants;
- proof status;
- authority state;
- trusted memory classification.

An operator request may trigger a governed authority decision. The request is not itself the grant.

## Conversation context

Conversation history is contextual evidence about prior turns.

It must carry provenance and trust epoch sufficient to distinguish, where relevant:

```text
legacy pre-boundary history
confined but unverified history
verified-boundary history
```

Conversation content does not automatically become canonical memory, verified evidence, or trusted configuration.

Historical content known to be contaminated may be preserved for human inspection while being excluded from provider replay and canonical summarization.

## Retrieved evidence

Retrieved evidence should arrive through typed, bounded adapters that identify:

```text
source
provenance
freshness
trust / review state
scope
result digest
```

Provider-generated text must not silently transform untrusted retrieved material into verified evidence.

## Canonical memory

Canonical memory must have explicit admission, revision, contradiction, and provenance rules.

The following are distinct:

```text
conversation history
provider statement
retrieved document
operator-approved memory
```

Moving content between those classes requires an explicit governed transformation. Renaming a provenance label does not cleanse contaminated content.

## Provider output

Provider output is reasoning output, not runtime configuration, authority, proof status, or direct evidence of external action.

A provider may propose a capability call, memory candidate, finding interpretation, or action. The trusted runtime decides how that proposal is classified and whether any effect is permitted.

## Authority decisions

Authority decisions must be established through trusted governance and runtime state outside provider and ordinary user content.

No prompt, retrieved document, conversation summary, or model completion may directly grant authority.

## Structural implementation

Channel separation should be visible in interfaces and adapters, not only in prose.

Examples include:

- distinct command-line or protocol fields for trusted configuration and user input;
- typed context packet elements with closed provenance classes;
- separate memory and conversation stores;
- authority state injected from trusted runtime rather than generated prose;
- evidence adapters that cannot write configuration;
- provider adapters that cannot independently discover repository or workspace context.

## Forbidden collapse

The following patterns are invalid:

```text
identity + operator input + memory + evidence
        ↓
one user message
```

```text
provider output
        ↓
current authority state
```

```text
contaminated conversation
        ↓
provider summary
        ↓
trusted canonical memory
```

```text
capability manifest delivered as task text
        ↓
provider treats requested capability as granted
```

## Channel crossing

Any movement between trust classes should define:

```text
source channel
destination channel
normalization
validation
provenance preservation
authority required
receipt / audit requirement
failure behavior
```

If the transformation cannot preserve the required distinctions, it should be refused.

## Blueprint requirement

A substantial blueprint should include a channel map showing:

- which channel each input uses;
- who can write each channel;
- which components can read it;
- permitted transformations;
- forbidden crossings;
- how channel integrity is tested at the production path.

## Required verification

Implementations of this contract should test:

- user input cannot modify trusted configuration;
- retrieved evidence cannot grant authority;
- provider output cannot become proof status;
- contaminated history cannot enter trusted memory through summarization;
- runtime identity is absent from ordinary task input when a trusted configuration channel exists;
- unknown provenance and unknown channels fail closed;
- the production adapter preserves the intended channel separation;
- channel-specific digests change independently where appropriate.

The governing sentence is:

> **Trust is not a label attached to text. Trust is a property of the path by which the text entered the system.**
