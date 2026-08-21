# Agent Identity and Specialist Admission Contract

## Purpose

This contract is the canonical cross-ecosystem owner for AgentId, agent identity, principal-agent binding, scope-agent binding, admitted actors, specialist admission, remote-agent admission, admission revocation, and identity evidence versus authority.

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

The governing sentence is:

> **An agent identity establishes neither sovereignty nor authority; it is a governed subject that must be explicitly admitted before separately governed capability can be considered.**
