# Agent Identity and Specialist Admission Contract

## Purpose

This contract is the canonical cross-ecosystem owner for AgentId, agent identity, principal-agent binding, scope-agent binding, admitted actors, specialist admission, remote-agent admission, community-agent admission, the admission decision, admission revocation, and identity evidence versus authority.

It defines who an agent is within ToadAid and what must be true before that identity may be considered for separately governed capabilities. It does not implement messaging, A2A, MCP, x402, wallets, attestations, ERC-8004 registration, Base integration, or a community-agent runtime.

## Core definitions

### PrincipalId

PrincipalId is owned by the Scope Sovereignty Contract. This contract does not redefine principal sovereignty semantics.

### AgentId

An AgentId is a stable ToadAid identifier for one admitted agent identity. It is distinct from PrincipalId, ScopeId, provider or session identifier, wallet address, ERC-8004 identity, A2A AgentCard URL, MCP server identity, and repository identity.

External identities may be recorded as evidence or bindings. None automatically establishes a ToadAid AgentId.

### Agent binding

An agent binding is an explicit relationship describing the principal, scope, governance subject, deployment, or other later-defined authority context that governs an agent.

An AgentId is not automatically a sovereign principal, and an agent is not automatically equivalent to its owner.

### Admitted actor

An admitted actor is an identity that has passed the applicable ToadAid admission decision and may be considered for separately governed capabilities under stated constraints.

~~~
admission != membership
admission != capability
admission != authority
~~~

Admission establishes recognition and eligibility only.

### Admission decision

An admission decision is an explicit recorded decision by the applicable human governing authority that a specific agent identity is recognized for a stated profile and scope relationship. It is made by a human principal, or by a scope-governance subject that the scope's governance explicitly empowers to admit. An agent, a specialist, a community agent, a message, an attestation, a provider, a discovery mechanism, an external registry, or an automated rule cannot make or exercise it.

Admission evidence may inform the decision but never constitutes it. A decision must be attributable to the authority that made it, and it may produce a receipt or evidence.

~~~
admission evidence != admission decision
admission decision != membership
admission decision != authority
~~~

### Specialist

A specialist is an admitted agent with a declared bounded domain and capability surface.

### Remote external agent

A remote external agent is controlled outside the local ToadAid trust boundary and discovered through A2A, direct integration, registry, onchain identity, or another transport. Its external identity evidence does not create local admission.

## Initial conceptual profiles

These profiles are not scope types and grant no authority.

### PERSONAL AGENT

A personal agent is associated with one principal's personal context. This contract permits an explicit stable agent identity where required, but does not decide whether every personal agent has a permanent independent AgentId rather than a principal-bound runtime identity.

### COMMUNITY AGENT

A community agent is an admitted agent serving one explicit shared/community scope. It inherits no private-member memory.

### PROJECT AGENT

A project agent is an admitted agent serving one explicit project scope. Project membership does not become repository mutation authority.

### SPECIALIST AGENT

A specialist agent has a bounded domain capability surface. Code, lore, Zora/onchain, market, and future payment/signing specialists are examples only.

### REMOTE EXTERNAL AGENT

A remote external agent is controlled outside the local trust boundary. Its identity and advertised capability are evidence only.

## Identity laws

1. **Principal is not agent.** A human principal and an agent identity are separate concepts. An agent cannot silently absorb the sovereignty of its principal.
2. **Agent identity is not authority.** Knowing who an agent is does not authorize it to act.
3. **Authentication is not authorization.** A valid signature may prove control of an identifier; it does not prove membership, capability, delivery rights, payment authority, acceptance, or administrator rights.
4. **External identity is evidence.** An A2A AgentCard, cryptographic signature, MCP/service identity, wallet address, ERC-8004 identity, DNS/domain binding, provider identity, or deployment identity may provide evidence only.
5. **Provider session is not agent.** ChatGPT, Codex, Claude, API, local-model, and other reasoning sessions do not automatically create an AgentId.
6. **Transport is not agent.** A2A, MCP, HTTP, STDIO, WebSocket, Telegram, Slack, Discord, or another transport does not define agent identity or authority.
7. **Wallet is not agent.** Wallet or account ownership does not establish ToadAid principal, AgentId, scope membership, signer authority, or economic authority.
8. **Onchain identity is not local authority.** ERC-8004 or another onchain identity may be portable identity evidence only.

## Specialist admission record

A future Specialist Admission Record or Manifest is an architectural concept, not a storage schema or grant. At minimum it must describe:

~~~
agent identity
agent profile
declared domain
governing principal or scope binding where applicable
allowed scope relationships
declared capability inventory
explicit denials
provider and harness assumptions
transport exposure
credential and secret policy
target and workspace constraints where applicable
required approval class and exact-state checks where applicable
e-stop behavior
revocation behavior
restart and recovery behavior
refusal behavior
reconciliation requirements
receipt and evidence requirements
admission version, digest, or equivalent integrity reference
~~~

The inventory states what a specialist is designed to support. It is not a grant; current effective capability still comes from separate governance.

## Specialist authority law

> **Declared capability is not granted capability.**

A Zora specialist may support public posting without currently being authorized to post. A Coder specialist may support repository patching without authority in every workspace. A payment specialist may support payment execution without wallet or payment authority.

## No authority inheritance

An agent must not automatically inherit authority from its principal, another agent, another specialist, room/project/shared membership, repository access, wallet ownership, token/NFT/Lore Land ownership, provider session, prior receipt/action, A2A message, MCP discovery, attestation, ERC-8004 reputation, or ERC-8004 validation.

## Remote-agent admission

A future local admission sequence is:

~~~
external identity evidence
→ verification
→ local AgentId and binding decision
→ explicit scope relationship where admitted
→ capability eligibility
→ separate current capability authorization
~~~

Remote external agents default to **no local direct authority**. They may send candidate messages, advertise capabilities, provide artifacts, provide identity/trust evidence, and request interaction. They do not automatically gain filesystem/repository access, MCP execution, wallet access, local secrets, scope membership, or delivery authority.

## Admission decisions for community and remote-external agents

The remote-agent admission sequence above is unchanged. This section states the admission decision law that sequence composes, for the two profiles a shared/community fabric depends on. It defines neither runtime, membership, nor authority.

### Who may admit

The admission decision for a community agent or a remote external agent is made by the human governing authority of the relevant scope, or by a scope-governance subject that the scope's governance explicitly empowers to admit. Admission authority is scope-governed and human-sovereign. No agent, specialist, community agent, provider, transport, message, attestation, reputation signal, or automated rule may hold or exercise it, and hosting or receiving capability never creates it.

### Admission evidence

Admission evidence is external identity evidence as defined by the identity laws: an A2A AgentCard, cryptographic signature, MCP or service identity, wallet address, ERC-8004 identity, DNS/domain binding, provider identity, or deployment identity. Verification of evidence and the admission decision remain separate steps; no verification result, authenticated channel, onchain validation, or volume of contact auto-produces a decision. Evidence freshness and re-verification cadence remain deferred.

### Admission record

An Admission Record is an architectural concept, not a storage schema or authority artifact. A community-agent or remote-external-agent admission record must, at minimum, describe:

~~~
agent identity
agent profile
governing scope relationship
admitting authority reference
admission evidence references and their verification basis
constraint classes the admission carries
e-stop and revocation behavior that applies
admission version, digest, or equivalent integrity reference
~~~

The specialist admission record above remains the maximal record shape for specialists; the admission record here is the same architectural concept narrowed to what these profiles require. Neither record is a grant, and neither is a storage schema.

### Admission is not joining

An admission decision is not a join. Joining composes canonical scope law: a human joins a scope through explicit membership according to that scope's governance, and an agent is admitted through an admission decision. Neither produces the other, and neither substitutes for the other.

~~~
admission != join
admission of an agent != the principal's membership
a principal's membership != admission of the principal's agent
~~~

### Community agent admission

A community-agent admission binds one admitted agent identity to one explicit shared scope under that scope's governance. It establishes recognition for that scope only; serving a further community scope requires its own admission decision for that scope, whether recorded separately or as an explicitly stated scope set in one decision.

A community-agent admission must never be recorded, held, or interpreted as establishing any of: reading member personal memory or files; accessing member credentials; impersonating a member; inheriting member capabilities; holding universal administrator authority; signing wallet transactions; spending community or personal funds; publishing publicly; mutating repositories; creating membership; granting capabilities; self-approving; or overriding revocation or e-stop. These are constraint classes carried by the admission record, and each belongs to a separately governed authority path.

### Remote external agent admission

A remote-external-agent admission is a recognition that one external agent identity, after identity evaluation and verification, is locally admitted for a stated scope relationship. It rests on external identity evidence only. External reputation, ERC-8004 validation, an authenticated channel, or persistence of contact is never sufficient admission evidence.

It does not disturb the default above: a remote external agent defaults to **no local direct authority** before, during, and after admission unless the full bounded-consequence sequence is separately satisfied.

~~~
external identity != local AgentId automatically
external reputation != local admission
authenticated peer != admitted peer
admitted remote peer != authorized peer
admission != standing intake acceptance
~~~

### Profile interlock

A remote external agent that passes an admission decision into a shared/community scope relationship becomes a community-agent profile instance: a remote-origin agent serving one explicit shared scope under this contract's community-agent law. The interlock replaces nothing. The agent's remote origin still governs its evidence and verification posture, its messages still begin as untrusted external content, and it retains no local direct authority.

If an admitted remote-origin community agent is ever to reach a bounded consequence, every step of the delegated-authority sequence remains required: identity evaluated, locally admitted, the relevant scope relationship and an explicit Grant existing, current policy and target or current-state checks passing, and required approval present. Admission satisfies the locally-admitted step only.

### Admission and standing intake

Admission is a precondition for standing message intake from a sender outside the local trust boundary. A sender with no admission under this contract has no standing intake path; an implementation must refuse to hold an intake channel open to it, and it must treat that refusal as the default rather than a configurable choice.

Admission is a precondition, not an acceptance. Messages from an admitted sender remain untrusted external content governed by the messaging and trusted-channel contracts, may establish no authority, and must be independently evaluated by the recipient. This contract defines no intake channel classes, transports, or delivery semantics; those remain owned downstream. Refusal of an unadmitted sender uses the canonical failure-outcome vocabulary and no local synonym.

### Composition with leave, revocation, and e-stop

Leaving a scope removes an agent's admission-derived standing in that scope together with its membership-derived access, according to canonical scope law. Retention, deletion, and export semantics are owned by the scope sovereignty contract and are not redefined here.

Revocation composes across owners. Revoking admission removes future admission-based recognition and eligibility across transports, as stated in the revocation law of this contract. Membership removal, Grant revocation, and delivery revocation are separately owned by the scope sovereignty, delegated authority, and messaging contracts. Revoking one does not silently revive another, and no stale membership, grant, message, attestation, credential, or prior action can recreate revoked admission.

An external dominant e-stop applies across community interactions and transports. Admission cannot be used to override or route around an active e-stop, and queued or already-received work gains no authority while it is active.

## Revocation and emergency stop

Admission is revocable independently of provider session, transport, external registry, wallet, AgentCard, or ERC-8004 identity. Revocation affects future local authority and applies across transports; an agent may not continue through a different transport after one route is revoked.

An external dominant e-stop applies to admitted agents and specialists. An agent cannot override or route around it through A2A, MCP, direct transport, or provider switching. Historical evidence remains historical evidence only.

## Identity rotation and replacement

A future rotation requires old identity, replacement identity, explicit binding update, revocation or supersession, historical-receipt preservation, and no automatic transfer of capability. This contract defines no cryptographic key format.

## Public discovery and service identity

Public discovery is a projection, not canonical authority. A future AgentCard or public record may disclose only explicitly released information and must not expose private scopes, membership lists by default, personal memory, credentials, internal topology, hidden capabilities, unrestricted target paths, or private receipt bodies.

A tool or MCP server may have service identity and expose capabilities without being an autonomous agent. Agent, service, tool, provider, and principal remain distinct identity classes.

## High-consequence specialists

Wallet/signing, payments, trading, public publishing, social posting, deployment, credential use, and destructive mutation remain stricter specialist lanes. Admission alone never activates them; each requires separate domain policy and explicit later authority contracts.

## Receipts and evidence

An admission decision may produce a receipt or evidence. It proves that the decision occurred, not standing authority, a capability token, future approval, or that later behavior is safe. Identity evidence and action evidence remain distinct.

## Relationship to scope sovereignty

~~~
PrincipalId != AgentId
ScopeId != AgentId
membership != admission
admission != join
admission != capability
capability != current authority
message != grant
receipt != authority
attestation != authority
payment != authority
~~~

Agent-to-agent communication is a later contract.

## External interop non-claims and deferred decisions

A2A, MCP, ERC-8004, cryptographic signatures, and wallet/account identifiers are possible external identity/interoperability evidence only. This contract does not approve or activate A2A runtime, public AgentCards, MCP runtime/service, ERC-8004 registration, wallet connection, x402, AgentKit, Payments MCP, EAS, signing, payment, Base interaction, or Lore Land authority.

It explicitly defers permanent personal-agent identity, AgentId format, key type, PKI, DID, ERC-8004/A2A mapping, persistence backend, discovery/public directory, role/admin taxonomy, wallet/Lore Land association, payment/signer policy, A2A message format, and attestation format.

This cut adds no admission runtime, no membership state, no intake channel class, no transport, and no admission authority, and it narrows no existing vocabulary. Every admission decision and every implementation of the admission decision law requires separately bounded, human-approved work, verification, evidence, governance, and authorization.

~~~
activation: NOT_INCLUDED
~~~

It also defers admission-implementation backends, evidence re-verification cadence, admission receipt format, intake class vocabularies and transports, any intake runtime, and any sender-admission interface.

## Canonical dependencies and ownership boundary

This contract depends on and preserves:

- [`scope-sovereignty-contract.md`](scope-sovereignty-contract.md), which owns PrincipalId, ScopeId, scope types, membership, audience, cross-scope release, and join/leave semantics. This contract's admission law composes with membership and never redefines it.
- [`delegated-authority-and-capability-grant-contract.md`](delegated-authority-and-capability-grant-contract.md), which owns GrantId and the bounded-consequence sequence for remote agents.
- [`agent-to-agent-messaging-and-delivery-contract.md`](agent-to-agent-messaging-and-delivery-contract.md), which owns sender identity, delivery, and untrusted remote-message content.
- [`trusted-channel-separation-contract.md`](trusted-channel-separation-contract.md), which owns channel separation.
- [`attestation-and-evidence-exchange-contract.md`](attestation-and-evidence-exchange-contract.md), [`capability-authority-boundary.md`](capability-authority-boundary.md), and [`failure-outcome-taxonomy.md`](failure-outcome-taxonomy.md).

The [`../blueprints/community-agent-fabric.md`](../blueprints/community-agent-fabric.md) supplies composition context for these sections only. It does not own admission mechanics, and this contract does not become a second owner of messaging, delivery, scope, or Grant law.

The governing sentence is:

> **An agent identity establishes neither sovereignty nor authority; it is a governed subject that must be explicitly admitted before separately governed capability can be considered.**
