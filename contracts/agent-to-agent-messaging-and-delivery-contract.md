# Agent-to-Agent Messaging and Delivery Contract

## Purpose

This contract is the canonical cross-ecosystem owner for AgentMessage, MessageId, sender identity, recipient identity and audience, source and destination scope, message provenance, delivery eligibility and decision, cross-scope messaging, expiry and replay, delivery evidence, and the transport-neutral messaging law.

It defines governed communication and delivery. It does not implement A2A, MCP messaging, networking, queues, rooms, public AgentCards, runtime delivery, wallets, payments, x402, attestations, ERC-8004, Base integration, or a community-agent runtime.

## Foundational distinctions

~~~
message != grant
message != capability
message != authority
message != human approval
message != task acceptance
message != attestation
message != receipt
delivery != consequence authorization
delivery != acceptance
sender identity != sender authority
authenticated message != authorized request
~~~

A message may request a capability. The request itself grants nothing.

## Core law

> **A message may inform. A message does not authorize a consequence.**

For example, a Living Agent message saying Tommy wants this posted may inform a Zora or publication specialist. It does not authorize public posting. The recipient must independently evaluate sender identity, source and destination scope, release state, current membership where relevant, requested capability, current policy, required approval, current target or state, and revocation/e-stop state.

## Core definitions

### MessageId

A MessageId is a stable identifier for one message or message record. It is distinct from AgentId, PrincipalId, ScopeId, transport request ID, provider-turn ID, wallet transaction ID, and receipt ID.

### AgentMessage

An AgentMessage is structured communication associated with an explicitly identified sender identity or identity evidence and a destination scope or audience. It may carry information, a proposal, a request, status, an artifact reference, an evidence reference, a receipt reference, or a reply/correlation reference. None implies authority.

### Sender

A sender is the claimed or verified sending agent, service, or external identity. Sender identity evidence remains separate from local admission and authority.

### Recipient

A recipient is an exact admitted agent, exact principal where separately supported, exact scope audience, or another later-defined destination. Recipient existence does not make delivery authorized.

### Source scope

The source scope is the scope from which message content is authorized to originate.

### Destination scope

The destination scope is the scope into which delivery is proposed.

### Audience

Audience is owned by the Scope Sovereignty Contract. This contract does not redefine its semantics.

### Delivery decision

A delivery decision is a current policy decision determining whether a specified message may be delivered to its specified destination or audience. Delivery authority is not inferred from the message itself.

## Architectural message envelope

The following is an architectural model, not implementation code or an A2A schema:

~~~
message_id
correlation_id or task_id where applicable
sender_agent_identity
sender_admission_reference where applicable
sender_principal_binding_reference where applicable
source_scope
destination_scope or audience
message_type
content_reference and/or digest
provenance
retention/disclosure class
cross_scope_release_reference where required
requested_capability, advisory only
artifact references
evidence references
attestation references, future/optional
receipt references
issued_at
expires_at where applicable
reply_to
transport identity/evidence
signature/authentication evidence where applicable
~~~

Not every field must be physically transmitted over every transport. Local policy and scope data should be referenced or minimized when broad transmission would leak private structure.

## Broad message classes

Implementations may use broad semantic classes such as INFORMATION, PROPOSAL, REQUEST, STATUS, ARTIFACT_REFERENCE, and EVIDENCE_REFERENCE.

This contract creates no exhaustive application taxonomy and no authority-bearing message type. There is no authorized-action, auto-approve, execute-without-policy, or equivalent class.

## Source-scope law

Every scope-relevant message must have a defensible source-scope relationship. Data does not become community, project, or public data merely because an agent puts it in a message.

~~~
PERSONAL
    ↓ explicit release
PROJECT
~~~

Copying is not release. Summarizing is not release. Embedding is not release. A model-generated paraphrase is not release. Personal information leaving a personal scope requires the applicable explicit cross-scope release required by the Scope Sovereignty Contract.

## Destination, audience, and personal privacy

Delivery must bind a current destination or audience:

~~~
presence != membership
membership != audience
audience != capability
capability != authority
~~~

A visible channel or room does not prove every participant is an authorized recipient, and a model-generated recipient list is not authoritative.

A personal agent participating in a shared, project, or community conversation must not expose its principal's personal memory, files, credentials, private receipts, conversation history, schedules, or unpublished artifacts unless they are separately released under current scope policy. Community membership is never a personal-memory read grant.

## Remote and external messages

Messages from remote external agents are untrusted external input unless a separately defined trusted channel establishes a specific authoritative claim. Authentication may prove sender control or identity evidence; it does not make content safe or authoritative.

Remote messages may contain prompt injection, malicious instructions, false authority claims, malicious artifact references, deceptive payment requests, stale scope claims, or replayed requests. A recipient must not execute a consequence merely because a message is authenticated.

## Trusted-channel relationship

This contract preserves the Trusted Channel Separation Contract. Metadata embedded in ordinary message content is not trusted authority.

If a future delivery carries authoritative framing such as verified source scope, release decision, admission status, or policy result, that framing must travel through a structurally appropriate trusted channel or canonical local lookup. This contract creates no competing trusted-channel taxonomy.

## Requested capability

A message may carry advisory intent such as repository patching, public posting, or future payment execution. The field creates no capability, admission, approval, target authority, signer authority, or current execution authority.

## Delivery and consequence lifecycles

A future delivery lifecycle is:

~~~
message candidate
    ↓
sender identity/admission evaluation
    ↓
source-scope validation
    ↓
cross-scope release check where required
    ↓
destination/audience resolution
    ↓
current membership/revocation policy
    ↓
delivery-policy decision
    ↓
delivery
    ↓
delivery evidence/receipt where required
~~~

Any requested consequence is separate:

~~~
delivered request
    ↓
recipient reasoning
    ↓
capability proposal
    ↓
governance
    ↓
current-state verification
    ↓
separate authorization
    ↓
consequence
~~~

The two lifecycles must not collapse.

## Expiry, replay, revocation, and e-stop

A consequential request message must not be reusable indefinitely merely because it was once valid. A future mechanism may use expiry, nonce, correlation identity, consumed-request marker, message digest, or current-state binding; the implementation is deferred.

A replayed message does not recreate membership, admission, approval, capability, payment authority, or publication authority.

If an agent, membership, release, delivery right, or relevant capability is revoked before delivery or consequence, future effect must be denied or refused under applicable canonical policy. Revocation applies across transports: switching from A2A to MCP or direct transport must not restore delivery or authority.

Dominant e-stop applies independently of transport. Queued, delayed, streamed, retried, or already-received messages cannot override an active e-stop for a governed consequence. This contract defines no automatic replay after e-stop clears.

## Delivery evidence, retention, and disclosure

A delivery receipt or evidence record may prove that a message was accepted for delivery, refused, destination-resolved, delivered, or failed. It does not prove recipient agreement, task acceptance, capability authorization, action, payment, or result correctness. Existing evidence and failure vocabulary remains canonical.

Messages remain subject to source scope, destination scope, release policy, audience, retention policy, and later-defined deletion/export policy. Delivery does not grant indefinite retention. Forwarding does not erase source provenance. Indexing does not widen audience. Model-context inclusion does not change scope ownership.

## Room and community model

A future room may contain humans, personal agents, project agents, community agents, specialists, and remote admitted agents. It is not a governance root:

~~~
room presence != ToadAid membership
membership != audience
audience != capability
capability != current authority
~~~

## Transport neutrality and interoperability

This contract remains valid over local in-process delivery, MCP-related adapters where appropriate, A2A, HTTP, WebSocket, queues, Slack, Telegram, Discord, and future transports. A transport change must not widen authority.

A2A is an optional future interoperability seam. AgentCard, Message, Task, Artifact, and task-lifecycle concepts may be external mappings only:

~~~
A2A Message != ToadAid authority
A2A Task != ToadAid accepted task
A2A authentication != ToadAid authorization
A2A Artifact != automatically admitted scope data
A2A status != ToadAid completion
~~~

MCP remains tool/resource capability exposure, while A2A concerns peer-agent collaboration. Delivering a message must not automatically invoke an MCP tool, and MCP must not become an agent-chat authority protocol.

Messages may later reference attestations, but attestation remains evidence rather than authority. A message may later carry service terms, payment-requirement references, or payment-receipt references, but none grants payment authority. A message requesting public publication is a proposal only; delivery to a publication specialist does not authorize publication.

## Non-claims and deferred decisions

This contract explicitly defers:

- exact serialization, encryption, and signature formats;
- A2A runtime and AgentCard mapping;
- networking, public endpoints, queues, and persistence;
- replay-protection implementation;
- room and Slack/Telegram/Discord implementation;
- message database/storage ownership and routing owner;
- whether Core, MCP, Bridge, or Living hosts delivery state;
- attestation schema;
- payment/x402 fields and wallet/signing;
- ERC-8004, Base, and Lore Land mapping;
- community-agent runtime.

The governing sentence is:

> **Delivery may carry governed information to an eligible audience. It never converts a message, identity, or request into authority to cause a consequence.**
