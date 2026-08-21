# Scope Sovereignty Contract

## Purpose

This contract is the canonical cross-ecosystem owner for principal and scope sovereignty vocabulary. It defines what a scope means and the laws that every future implementation must preserve.

It does not assign scope-state ownership to Mirror Core, Living Agent, Mirror Desktop Bridge, ToadAid MCP, ToadAid Coder, or any specialist. It defines no storage schema, runtime API, transport, deployment, or implementation owner.

## Core definitions

### Principal

A **principal** is the explicitly identified human or other separately admitted actor to which a ToadAid identity, membership, grant, delivery, or receipt may bind.

A provider, model, browser, device, session, room, repository, wallet, or conversation is not automatically a principal.

### Scope

A **scope** is an explicit bounded domain of ownership, membership, data handling, capability admission, delivery, and future authority evaluation.

A scope is not created by implication from physical presence, a provider session, a channel, a repository checkout, a credential, or a model conversation.

### Scope identity

Every scope must have a stable ScopeId distinct from display names, provider-specific identifiers, room names, repository URLs, wallet addresses, and mutable membership lists. Implementations must preserve enough provenance to determine what scope a consequential request, release, grant, delivery, or receipt concerns.

### Scope type

This contract defines exactly four initial architectural scope types:

~~~
personal
shared
project
public
~~~

No additional scope type is defined by this contract.

### Scope owner

A scope owner is the principal or separately defined governance subject accountable for creating or governing that scope under later policy. Ownership is not equivalent to blanket access to every other scope, standing authority, provider identity, or possession of a credential.

The exact ownership and role model is deliberately unresolved.

### Membership

Membership is an explicit relationship between a PrincipalId and a ScopeId. A later implementation may define roles or classes, but it must preserve active and revoked membership state.

Membership is not created merely by presence in a room, Telegram group, Discord, Slack channel, GitHub organization, repository, provider account, or model conversation.

### Audience

An audience is the authorized recipient set for a delivery or release. Initial architectural audience forms are:

- one exact principal;
- the exact active membership of one scope;
- a deliberate public audience.

An audience is not inferred by a model's preference, a channel's visibility, or a recipient suggestion.

## Scope classes

### PERSONAL

A personal scope is controlled for one principal and is private by default.

- Personal memory, files, credentials, history, and receipts do not become shared because the principal joins another scope.
- Membership in shared, project, or community scope grants no visibility into personal state.
- A personal scope does not imply standing authority outside that scope.

### SHARED

A shared scope is an explicitly joined collaborative scope.

- Membership is explicit.
- Removing membership revokes future shared access and authority.
- Shared state does not imply access to any member's personal state.
- Shared membership does not itself grant a capability, credential view, delivery right, repository mutation right, or administrator role.

### PROJECT

A project scope is bounded collaborative state associated with an explicitly defined project.

- Project membership and workspace or repository binding are separate concepts.
- Repository access alone does not silently create project membership.
- Project membership alone does not grant arbitrary repository mutation authority.
- A project scope does not silently import personal or shared data.

### PUBLIC

A public scope contains deliberately released information or capability.

- Public state must arise from an explicit publication or release act.
- Public visibility does not make all underlying source-scope data public.
- Public material remains subject to the policy, receipt, and revocation semantics applicable to the release.

## Scope-owned data and boundaries

### Memory ownership

Memory may inform reasoning. Memory never grants permission.

Memory has a scope owner and does not become accessible across scopes because the same principal, provider, agent, repository, or conversation appears in both. A future implementation must model any personal-to-shared, personal-to-project, shared-to-public, project-to-public, or other crossing as an explicit release.

### File and workspace ownership

Files and workspaces may be associated with a scope only through explicit binding. Filesystem presence, repository access, checkout location, provider access, or a model's knowledge of a path does not by itself create scope membership, ownership, or mutation authority.

### Skill ownership

Skills describe procedure, not authority. Possessing, receiving, importing, or sharing a skill does not grant the capability, credential, scope access, or authority needed to execute it.

A future skill-ownership or sharing mechanism must separately state its scope, audience, provenance, and grant requirements.

### Capability grants

A capability grant is a separately admitted authority relationship. It is not created by memory, skill possession, membership, provider choice, provider session, repository access, or a prior receipt.

A future grant must bind at least:

~~~
scope
principal or admitted actor
capability
expiry
revocation state
one-use or standing classification
restart and recovery semantics
~~~

Effective capability remains governed by the canonical Capability / Authority Boundary Contract.

### Credential view or lease

Credentials are not ambient scope data. A credential view or lease must be separately admitted, narrowly scoped, and revocable.

Credential-purpose prose cannot substitute for mechanical capability enforcement. A scoped credential is not safe merely because a model, provider, sandbox, or specialist is told its intended purpose.

### Scheduled duty

A scheduled duty is a future bounded obligation associated with an explicitly identified scope. Scheduling does not create standing authority, override revocation, bypass emergency stop, expand audience, or permit delivery without current policy.

### Delivery

Delivery is audience-bound. A model deciding who should receive something does not authorize delivery.

A future delivery must bind source scope, destination audience, capability, current policy, and the applicable evidence or receipt requirements.

## Authority lifecycle

### Revocation

Removing membership or revoking a grant must prevent future access and action under that relationship. Historical evidence may remain preserved as history, but it cannot recreate membership, authority, capability, or access.

### Temporary authority

Temporary authority must not silently survive restart. Every future temporary grant must define explicit expiry, consumption where applicable, revocation, restart, crash, recovery, and reconciliation semantics. No implementation may assume durability by default.

### Emergency stop

An externally governed emergency stop is dominant over agent, provider, model, scheduled-duty, worker, or specialist desire to continue. An e-stop is not merely a conversational instruction or provider-side preference.

### Retention, deletion, and export

Retention, deletion, and export are scope-governance concerns. A future implementation must define them with explicit source scope, audience, authority, provenance, receipt/audit behavior, and cross-scope consequences.

No current storage, retention, deletion, or export mechanism is selected here.

## Scope crossing and publication

### Cross-scope release

Scope crossing is a trust boundary. Personal-to-shared, personal-to-project, shared-to-public, project-to-public, and every other scope crossing require an explicit release operation.

A future release record must bind:

~~~
source scope
destination scope or audience
data class
purpose metadata
policy decision
receipt or evidence reference
~~~

Crossing must preserve provenance. Copying, summarizing, embedding, indexing, retrieving, forwarding, or presenting data does not erase its source scope or turn a non-release into a release.

### Public publication

Public publication is a deliberate release to a public audience, not a consequence of a source being useful, visible to a model, available in a room, attached to a repository, or mentioned in a conversation.

## Receipt, audit, and administration

### Receipt and audit relationship

Receipts and audit records are evidence, not authority. A historical receipt cannot authorize a new action, restore membership, recreate a credential lease, or reverse revocation.

Receipts should preserve the relevant scope, principal or admitted actor, policy decision, and crossing or delivery provenance without becoming a broader disclosure mechanism.

### Administration

Administration is not private omniscience. ToadAid does not adopt a default assumption that organization administrators are standing readers of all personal content.

Any future exceptional administrative read requires separately defined authority, scope, audience, audit, and human-governed policy. This contract defines no administrator role taxonomy.

## Provider neutrality

ChatGPT, Codex, API-backed models, local models, provider sessions, harnesses, and future reasoning providers do not define principal, membership, ownership, scope, or authority.

Reasoning authority and execution authority are distinct. Changing provider must not widen a scope, capability, credential view, grant, or delivery audience.

## Required laws

The following laws are canonical:

1. Memory never grants permission.
2. Skills are procedure, not authority.
3. A provider session is not identity.
4. Reasoning authority is not execution authority.
5. Membership is explicit.
6. Personal state is private by default.
7. Release is explicit.
8. Revocation affects future authority.
9. Temporary authority does not silently survive restart.
10. E-stop is externally dominant.
11. Credentials are not ambient scope data.
12. Receipts are evidence, not authority.
13. Administration is not private omniscience.
14. Delivery is audience-bound.
15. Scope crossing is a trust boundary.

## Architectural type model

This is an architectural data model, not code, a storage schema, or a runtime API.

~~~
PrincipalId

ScopeId

ScopeType
  personal | shared | project | public

Membership
  principal
  scope
  role_or_class (later-defined)
  active_or_revoked state

Audience
  exact principal
  exact scope membership
  deliberate public audience

Grant
  scope
  principal or admitted actor
  capability
  expiry
  revocation
  one-use or standing classification
  restart semantics

Release
  source scope
  destination scope or audience
  data class
  purpose metadata
  policy decision
  receipt or evidence reference
~~~

## QM reference lessons

QM is a reference implementation and threat-model source, not a ToadAid dependency or authority model.

Useful questions include per-person and room scopes, scope-owned memory and files, skills and grants, durable sessions and sandboxes, scheduled work, audience-bound delivery, and provider-neutral harnesses.

ToadAid does not accept as sufficient authority controls: bypassable command policy, browser actions outside gates, plaintext credentials treated as safe merely because they are scoped, unenforced credential-purpose prose, incomplete audience-floor filtering, conditional egress claims, provider paths bypassing governance, incomplete kill controls, or standing administrator access to personal content.

## Non-claims and deferred decisions

This contract does not decide:

- whether Mirror Core stores scope state;
- whether Living Agent owns personal-scope storage;
- whether ToadAid MCP routes scope operations;
- whether Mirror Desktop Bridge binds project scope;
- whether scopes are database rows, files, contracts, or runtime objects;
- exact role taxonomy or administrator model;
- exact credential backend or identity provider;
- blockchain/onchain identity mapping, wallet ownership, or community token/NFT membership;
- UI, Slack, Telegram, Discord, server deployment, or public networking;
- runtime activation, MCP runtime changes, agent runtime changes, API/provider activation, credential handling, wallet/social/trading action, or implementation authority.

The governing sentence is:

> **A scope is a governed boundary of ownership and future authority, not a label inferred from a model, channel, repository, or credential.**
