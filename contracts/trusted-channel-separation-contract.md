# Trusted Channel Separation Contract

## Purpose

ToadAid systems receive information with different trust semantics.

Runtime configuration, operator input, conversation history, retrieved evidence, memory, provider output, and authority decisions must not become interchangeable merely because they can all be serialized as text.

This contract defines the structural separation required between those channels.

## Core law

> **Inputs with different trust semantics must travel through different structural channels.**

A provenance label inside one undifferentiated prompt is not equivalent to trusted-channel separation.

A structurally separate channel is also not sufficient merely because the runtime can write to it. For a channel to establish trusted configuration for a semantic class, the receiving provider or runtime must treat that channel as authoritative relative to conflicting provider-owned or harness-owned configuration.

If an upstream provider surface injects a higher-priority or otherwise controlling identity, capability description, tool manifest, or policy that conflicts with ToadAid's intended trusted configuration, then the ToadAid channel is not authoritative for that semantic class. The system must mark the framing unsupported, choose a compatible provider surface, or move the user-facing interpretation outside that provider surface. It must not claim successful trusted configuration merely because the channel was separate and uncontaminated.

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

Trusted configuration can establish runtime framing only where the receiving surface gives that channel sufficient authority for the intended semantic class. It does not establish that every framed claim is externally true, and it must not be treated as authoritative when a provider-owned harness supplies conflicting higher-priority framing that ToadAid cannot override or independently reconcile.

## Channel authority and precedence

A channel map must describe not only separation, but also **authority and precedence**.

For each trusted channel, identify:

```text
who controls the channel
what semantic classes it may establish
what upstream configuration the receiver already has
whether conflicting upstream configuration can override it
how precedence is verified
what happens when precedence is unknown or contradictory
```

A channel is authoritative for a semantic class only when the production receiver contract and verification establish that the channel can actually govern that class.

Examples:

- a runtime-owned capability projection may be authoritative for NOMI's capability truth even when a provider self-describes broader native capabilities, if the product renders NOMI capability truth outside the provider's self-description and the runtime enforces the denial;
- a provider-specific appended system prompt is not authoritative for user-facing agent identity if the provider harness has an earlier controlling system identity that the model continues to treat as its own;
- a capability manifest delivered through a trusted field is still only a request if the runtime authority layer, rather than that field, determines effective capability.

When authoritative delivery cannot be established, use the canonical fail-closed outcomes appropriate to the evidence:

```text
unsupported_trusted_framing
unknown_channel_precedence
provider_incompatible
insufficient_evidence
```

Do not report successful configuration.

The canonical meanings of these outcomes are defined in [`failure-outcome-taxonomy.md`](failure-outcome-taxonomy.md).

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

Provider self-description is also not runtime capability truth. However, if the provider's own controlling configuration materially determines what identity or capability framing it will emit, ToadAid must account for that behavior in the channel-authority model rather than pretending a lower-precedence trusted field overrode it.

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
- provider adapters that cannot independently discover repository or workspace context;
- explicit modeling of provider-owned or harness-owned configuration that precedes or constrains ToadAid-controlled channels.

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

```text
separate trusted channel exists
        ↓
provider-owned higher-priority configuration conflicts
        ↓
runtime still claims trusted framing succeeded
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
- which semantic classes each trusted channel is authoritative for;
- provider- or harness-owned configuration that can conflict with it;
- precedence and conflict-resolution rules;
- permitted transformations;
- forbidden crossings;
- how channel integrity and channel authority are tested at the production path.

## Required verification

Implementations of this contract should test:

- user input cannot modify trusted configuration;
- retrieved evidence cannot grant authority;
- provider output cannot become proof status;
- contaminated history cannot enter trusted memory through summarization;
- runtime identity is absent from ordinary task input when a trusted configuration channel exists;
- unknown provenance and unknown channels fail closed;
- the production adapter preserves the intended channel separation;
- channel-specific digests change independently where appropriate;
- trusted configuration is actually authoritative for the semantic class it claims to establish;
- conflicting provider- or harness-owned higher-priority configuration is detected rather than ignored;
- a present but non-authoritative trusted channel cannot satisfy compliance;
- unknown channel precedence yields `unknown_channel_precedence` rather than successful trusted framing;
- an incompatible provider/harness yields `provider_incompatible` rather than a weaker provider-success claim;
- unsupported semantic authority yields `unsupported_trusted_framing` rather than successful configuration.

The governing sentence is:

> **Trust is not a label attached to text. Trust is a property of the path by which the text entered the system—and of whether that path is authoritative for the claim it is meant to establish.**
