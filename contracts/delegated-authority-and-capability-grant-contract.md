# Delegated Authority and Capability Grant Contract

## Purpose

This contract defines the canonical mechanics by which a sovereign Principal or other separately authorized governance subject may delegate a bounded capability to an admitted actor without transferring sovereignty or creating ambient authority.

It is the detailed canonical owner for GrantId, Delegation, Delegator, Grantee, delegated authority, grant envelopes and classes, capability and target binding, constraint binding, approval dependency, validity intervals, one-use consumption, standing-grant limits, revocation, restart and recovery behavior, grant applicability, non-transferability, narrowing, evaluation, and grant evidence or receipt references.

This contract refines the basic capability-grant relationship defined by the Scope Sovereignty Contract. It does not redefine PrincipalId, AgentId, ScopeId, membership, admission, Release, capability semantics or taxonomy, receipt semantics, attestation semantics, ERC-8004 identity, wallets or signers, or runtime policy implementation.

This is architecture only. It does not implement a runtime authorization engine, wallet signer, payment system, credential store, capability-token format, smart contract, ERC-8004 registry integration, MCP authorization server, A2A authorization runtime, or community runtime.

## Core law

> **Delegation grants bounded authority. It never transfers sovereignty.**

Delegation may permit an exact actor to exercise an exact capability against an exact target under current constraints. It does not make the actor the Principal, scope owner, administrator, credential owner, wallet owner, signer, or source of future authority.

## Foundational distinctions

The following distinctions are mandatory:

```text
delegation != sovereignty transfer
grant != identity
grant != membership
grant != admission
grant != technical capability
grant != unrestricted authority
grant != credential
grant != wallet ownership
grant != signer ownership
grant != approval for unrelated actions
grant != future authority after expiry
grant != authority after revocation
grant != proof of execution
grant != receipt
request != grant
message != grant
attestation != grant
reputation != grant
payment != grant
NFT ownership != grant
ERC-8004 identity != grant
provider permission request != grant
technical capability != authority
```

## Canonical dependencies and ownership boundary

This contract depends on and preserves:

- [`scope-sovereignty-contract.md`](scope-sovereignty-contract.md), which owns PrincipalId, ScopeId, scope types, membership, audience, Release, scope sovereignty, the basic capability-grant relationship, temporary-authority restart law, revocation principles, and e-stop law;
- [`agent-identity-and-specialist-admission-contract.md`](agent-identity-and-specialist-admission-contract.md), which owns AgentId, agent and scope bindings, admission, specialist admission, remote-agent admission, and admission revocation;
- [`capability-authority-boundary.md`](capability-authority-boundary.md), which owns capability, authority, request, and effective-capability semantics;
- [`agent-to-agent-messaging-and-delivery-contract.md`](agent-to-agent-messaging-and-delivery-contract.md), which owns message and delivery semantics;
- [`attestation-and-evidence-exchange-contract.md`](attestation-and-evidence-exchange-contract.md), which owns attestation and evidence-exchange semantics;
- [`trusted-channel-separation-contract.md`](trusted-channel-separation-contract.md), [`derived-evidence-contract.md`](derived-evidence-contract.md), [`evidence-activation-contract.md`](evidence-activation-contract.md), [`verification-applicability-contract.md`](verification-applicability-contract.md), and [`failure-outcome-taxonomy.md`](failure-outcome-taxonomy.md).

The [`../blueprints/community-agent-fabric.md`](../blueprints/community-agent-fabric.md) supplies composition context only. It does not own grant mechanics.

## Core model

The governed path is:

```text
Principal or separately authorized governance subject
    ↓ explicit delegation decision
Grant
    ↓ exact admitted actor
    ↓ exact scope + capability + target + constraints
current policy + current state + approval if required
    ↓
bounded consequence
```

The invalid path is:

```text
Principal
    ↓ "you may do anything for me"
agent becomes Principal
```

An indefinite or vague expression of trust is not a valid substitute for a bounded Grant.

## Core definitions

### Delegation

Delegation is an explicit governance act that creates or deliberately modifies a bounded Grant.

Delegation must itself arise from valid authority. An actor cannot delegate authority it does not possess or is not permitted to delegate. Delegation does not transfer the Delegator's identity, membership, sovereignty, or full authority surface.

### GrantId

A GrantId is a stable identifier for one delegated-authority record. It must remain distinct from:

- PrincipalId;
- AgentId;
- ScopeId;
- MessageId;
- AttestationId;
- ReceiptId or another receipt reference;
- transaction hash;
- wallet address;
- ERC-8004 Agent ID;
- provider-session identifier;
- capability name.

The exact GrantId format and serialization are deferred.

### Delegator

The Delegator is the Principal or separately authorized governance subject that creates the Grant.

Delegator identity alone is insufficient. The Delegator must have current authority to delegate the exact authority in question, within the exact scope and target, and must not exceed any non-delegable or narrower upstream limits.

### Grantee

The Grantee is the exact admitted actor receiving bounded authority.

Possible future Grantee categories include:

- an exact Principal identified by PrincipalId;
- an admitted agent identified by AgentId;
- an admitted specialist;
- a later-defined governed service identity where separately admitted.

A display name, provider session, wallet, room, transport, AgentCard, repository identity, or external registry record must not act as the authoritative Grantee identity.

### Capability

Capability retains the meaning defined by the Capability / Authority Boundary Contract. This contract does not redefine capability or create a capability taxonomy.

Binding a capability in a Grant identifies what authority may be evaluated. It does not prove technical availability or make the capability effectively authorized outside the remaining Grant and policy conditions.

### Target

The Target is the exact object or bounded set against which the delegated capability may be exercised.

Examples include one exact repository, workspace, branch, deployment target, publication identity, service endpoint, or later-defined payment target.

Ambient targets such as “all repositories,” “anything useful,” “any wallet,” or “all project resources” are invalid unless a later governance contract explicitly admits the scope and it remains bounded, reviewable, and within the Delegator's delegable authority.

### Constraints

Constraints are conditions narrowing use of the capability. They may include allowed operations, explicit denials, path or branch limits, audience limits, amount or budget limits, frequency limits, destination limits, a validity interval, approval dependencies, and current-state requirements.

Constraints narrow a Grant. They do not create capability, authority outside the Grant, credential access, or approval for another action.

### Grant class

This contract distinguishes two conceptual Grant classes:

```text
ONE_USE
STANDING
```

Exact runtime representation is deferred. A STANDING Grant is neither permanent nor unrestricted.

### Grant state

A future implementation must distinguish lifecycle conditions such as:

```text
candidate
active
consumed
expired
revoked
paused where applicable
invalidated or inapplicable where canonical taxonomy applies
```

These are conceptual lifecycle conditions, not an executable state machine. Cross-ecosystem failure, pause, revocation, invalidation, and applicability outcomes retain the canonical meanings in the Failure Outcome Taxonomy and Verification Applicability Contract.

## Authority conservation law

A Delegator cannot grant more authority than the Delegator is permitted to delegate.

```text
delegated_authority
    ⊆
delegator_delegable_authority
```

A Grant must not widen merely because:

- the Grantee technically supports more;
- a provider requests more;
- a task becomes difficult;
- another transport is used;
- a specialist advertises broader capability;
- a message claims additional permission;
- an attestation says the actor is trusted;
- a wallet has funds;
- an NFT is held;
- ERC-8004 reputation is high.

There is no authority amplification. A governance subject with broad administrative capability still cannot delegate an authority that its own current policy marks non-delegable or outside its scope.

## Non-transferability and subdelegation

> **A Grant is non-transferable unless a later explicit governance contract separately authorizes delegation-onward.**

A Grantee may not automatically transfer or onward-delegate a Grant to another agent, specialist, sub-agent, provider, tool, MCP server, A2A peer, Principal, or service.

Agent-created source, messages, prompts, attestations, plans, sub-agent creation, or tool configuration cannot manufacture a downstream Grant.

If a future subdelegation model is admitted, it must be explicit, no broader than the original Grant, provenance-preserving, expiry-preserving, revocation-preserving, e-stop-bound, and unable to extend the original Grant's lifetime, target, audience, capability, or constraints.

Subdelegation mechanics are deferred.

## Architectural Grant envelope

The following is an architectural model, not implementation code, a schema, a capability token, or a required public representation:

```text
grant_id
delegator identity or reference
grantee identity or reference
scope_id
capability
target binding
allowed operations
explicit denials
grant class
  one_use | standing
issued_at
valid_from where applicable
expires_at
revocation state or reference
consumption state or reference where applicable
approval requirements
current-state requirements
budget, quantity, or rate constraints where applicable
credential or signer dependency reference where applicable
restart and recovery policy
e-stop applicability
policy version or reference
evidence and receipt references
supersession or replacement reference where applicable
```

Not every field belongs in every transport or public representation. Rendering a Grant must not disclose credentials, keys, private approval text, private evidence bodies, hidden policy, or sensitive topology.

## Scope binding

Every Grant must bind an explicit ScopeId under the Scope Sovereignty Contract.

A Grant does not create a scope, create membership, change scope ownership, widen an audience, or perform Release.

For example:

```text
Grantee:
Project Agent X

scope:
Project Scope X

capability:
repo.review

target:
Repository R
```

This does not imply membership in another project, access to personal memory, access to every repository, public-publication rights, or wallet authority.

Copying a Grant into another scope does not make it applicable there. Cross-scope data movement and Release remain separately governed.

## Identity binding

A Grant must bind the canonical local actor identity required by applicable ToadAid policy.

```text
PrincipalId != AgentId
AgentId != ERC-8004 Agent ID automatically
wallet != Principal
provider session != AgentId
```

Admission and identity binding are prerequisites where applicable; they do not themselves create a Grant.

## Base ERC-8004 user-account identity direction

For future user accounts that adopt Base ERC-8004 interoperability, a Base ERC-8004 Agent ID is intended to serve as the account-specific external or onchain identity anchor for the user's agent.

That direction does not change current canonical law:

```text
Base ERC-8004 Agent ID != PrincipalId
Base ERC-8004 Agent ID != local AgentId automatically
Base ERC-8004 Agent ID != GrantId
Base ERC-8004 identity != authority
Base ERC-8004 identity != delegated capability
```

The safe conceptual relationship is:

```text
Human User
    ↓
PrincipalId
    ↓ explicit principal-agent relationship
local admitted AgentId
    ↔ verified Base ERC-8004 Agent ID binding
```

The local AgentId and external Base ERC-8004 identity remain distinct. Their binding must be explicit, separately governed, verifiable, revocable or replaceable where later policy requires, and insufficient by itself to establish a Grant.

The exact local AgentId to Base ERC-8004 Agent ID mapping is deferred to a dedicated identity-mapping architecture cut. This contract defines no registry address, chain contract, token or NFT semantics, smart-contract schema, registration flow, wallet binding, key ownership, or Base transaction flow. It authorizes no chain activity.

## ONE_USE Grants

A ONE_USE Grant is intended to be consumed by one successful governed authority exercise under its exact scope, capability, target, constraints, policy, current state, and approval requirements.

The following do not automatically establish consumption:

```text
request
attempt
provider completion
message delivery
receipt generation
```

A request or refused action consumes nothing merely by being requested. An attempt that fails before any effect must not be reported as a successful consumption. Conversely, an uncertain external effect must not be assumed absent merely because a response was lost.

Every future runtime must define unambiguous reconciliation semantics for success, refusal, failure before effect, uncertain external effect, crash during effect, lost response, and duplicate delivery.

For an uncertain external consequence:

```text
reconcile first
never assume safe replay
```

Until reconciliation establishes the applicable state, the Grant must not authorize blind retry. Consumption state must derive from canonical effect observation or reconciliation evidence rather than provider narrative or a convenient literal.

Exact consumption transactions, idempotency mechanisms, and reconciliation implementation are deferred.

## STANDING Grants

A STANDING Grant permits repeated authority evaluation only within bounded conditions.

Every STANDING Grant must continue to bind:

- exact Grantee;
- ScopeId;
- capability;
- Target;
- allowed operations and explicit denials;
- validity interval;
- revocation state;
- restart behavior;
- e-stop applicability;
- current policy and state.

STANDING must not mean universal, permanent, inheritable, transferable, provider-controlled, approval-free by default, target-free, or revocation-free.

A STANDING Grant may still require separate per-action human or governance approval for high-consequence effects. Each action must remain within any rate, quantity, aggregate, audience, and target constraints.

## Grant and approval separation

```text
grant != approval
```

A Grant establishes eligibility for current bounded delegated-authority evaluation. A particular action may still require separate human or governance approval.

For example:

```text
Grant:
Project Agent X may prepare release candidates for Repository R.

Action:
merge pull request 123
```

The action may still require explicit human approval under current policy.

Grant issuance and action approval must not collapse unless a later policy explicitly defines a bounded action class for which issuance itself satisfies the approval requirement. That policy must remain exact, current, reviewable, and within the Delegator's delegable authority.

Approval for one action does not approve unrelated actions.

## Effective authority evaluation

Effective authority composes the Capability / Authority Boundary Contract and the other canonical dependencies:

```text
requested capability
    ∩ technically available capability
    ∩ valid Grantee admission
    ∩ valid ScopeId
    ∩ active and applicable Grant
    ∩ exact Target match
    ∩ Grant constraints
    ∩ current policy
    ∩ current state
    ∩ required approval
    ∩ not revoked
    ∩ not expired
    ∩ not consumed where ONE_USE
    ∩ e-stop clear
    ↓
effective authority
```

This is conceptual architecture, not executable policy code. A Grant is necessary only where the applicable policy requires delegated authority, and it is never sufficient when another required term is absent.

## Grant applicability and current state

A Grant applies only to the actor, scope, capability, Target, constraints, policy, validity interval, and other subject conditions it binds.

Future evaluation must compare canonical current state against the Grant rather than rely on a cached projection, provider statement, message, copied identifier, or prior successful action.

Changes to the Grantee's admission, Scope relationship, Target state, policy version, capability surface, approval requirement, revocation state, credential or signer dependency, or other bound condition may make the Grant inapplicable or require replacement verification. Historical evidence remains historical and must not be presented as current authority.

## Narrowing and widening

A Grant may be narrowed through deliberate governance. Narrowing may create a smaller Target, fewer operations, shorter expiry, lower budget, stricter approval, reduced audience, or other tighter constraints.

Narrowing must not silently become widening. A widened Grant is a new authority-increasing governance decision and requires the applicable explicit authorization, current-state evaluation, and evidence.

Supersession or replacement must preserve provenance and history. A replacement Grant does not inherit applicability merely because it references an older one.

## Validity and expiry

A Grant may have an issued time, a later valid-from time, and an explicit expiry. Exact clock and freshness implementation is deferred.

Expiry affects future authority. Historical evidence remains historical.

```text
expired Grant != active authority
```

An old receipt, signature, attestation, cached policy result, provider session, message, or earlier action cannot restore an expired Grant.

## Revocation

Revocation must dominate future use. It affects future delegated authority without erasing legitimate historical evidence.

Changing transport or execution context must not restore a revoked Grant:

```text
MCP → A2A
A2A → direct
provider A → provider B
desktop → server
agent route A → agent route B
```

Stale caches, old receipts, messages, attestations, signatures, provider state, or alternate routes cannot reverse revocation. A later new Grant requires a new explicit delegation decision; it is not a revival by implication.

## Restart, crash, and recovery

This contract preserves the Scope Sovereignty law:

> **Temporary authority does not silently survive restart.**

Every future Grant implementation must define:

- whether a particular Grant survives restart;
- how current validity and applicability are re-established;
- how ONE_USE consumption is reconciled;
- how uncertain effects are reconciled;
- how revocation is reloaded from canonical state;
- how e-stop state is re-established;
- how stale caches and queued requests are rejected or reconciled.

The default is to not infer continued temporary authority merely because a process restarted. Crash recovery must not widen scope, capability, Target, constraints, validity, approval, retries, or effective authority.

## Externally dominant e-stop

The externally governed e-stop overrides active Grants.

Grant presence, Grant class, provider choice, transport, runtime, message delivery, or prior approval cannot bypass the applicable e-stop. ONE_USE and STANDING Grants are equally subordinate to it.

Clearing an e-stop does not automatically replay queued consequences or restore a Grant that independently expired, was consumed, was revoked, or became inapplicable.

## Target binding

Target matching must be exact enough to prevent ambient widening.

A repository Target may bind:

```text
repository owner and name
branch where applicable
path class where applicable
operation class
```

A publication Target may bind:

```text
account or service identity
audience
content or effect class
```

A future payment Target may bind:

```text
payer identity
payee or destination
asset
amount ceiling
purpose
expiry
```

The last model is conceptual only. This contract defines no payment semantics or payment authority.

## Budget and quantity bounds

The architectural envelope may support a future monetary ceiling, quantity ceiling, rate ceiling, action count, per-action maximum, or aggregate maximum.

```text
budget != wallet authority
budget != signer authority
budget != approval
budget != automatic spend
```

Limits only narrow an otherwise valid evaluation. They do not authorize funds, credentials, a signer, a payment, or a retry. Exact economic policy and budget accounting are deferred.

## Credential and signer relationship

A Grant may reference a separately governed credential, credential lease, or signer dependency.

```text
grant != credential
grant != credential lease
grant != private key
grant != wallet session
grant != signer ownership
```

A reasoning model must not require or receive raw private keys, seed phrases, or unrestricted signer sessions merely because a Grant exists.

Credential, lease, signer, wallet, and custody implementations remain deferred. A Grant reference to such a dependency is not proof that it is available or authorized.

## Messaging relationship

Messages may request delegated authority or reference a Grant.

```text
message != grant
```

For example:

```text
Agent A:
"Please let me publish artifact X."
```

This is a request. It is not a Grant. Message delivery, authentication, or text claiming broad user approval cannot create or widen delegated authority.

Authoritative Grant state must come from canonical trusted state through an authoritative structural channel, not ordinary message prose.

## Attestation, evidence, and receipt relationship

Attestations may provide evidence that a Grant was issued or revoked, an action occurred, or a particular state was observed.

```text
attestation != grant
receipt != grant
receipt != future authority
evidence != authority
```

A Grant may reference receipts or evidence without those artifacts becoming the Grant. Receipt and attestation semantics remain owned by their canonical contracts.

Grant evidence claims must be derived from canonical Grant observations, comparisons, and enforcement mechanisms. A rendered, cached, indexed, or summarized Grant view is a projection, not automatically canonical current Grant state.

## Reputation

High reputation must not increase delegated authority.

```text
reputation != grant
reputation != capability
reputation != approval
reputation != authority
```

This includes future ERC-8004 reputation. Reputation may inform later policy only within separately defined bounds; it cannot create, widen, renew, transfer, or restore a Grant.

## NFT and Lore Land relationship

NFT or Lore Land ownership may inform future identity or project association through separate contracts. It does not create delegated authority.

```text
Lore Land ownership != grant
Lore Land ownership != repository authority
Lore Land ownership != wallet authority
Lore Land ownership != administrator authority
```

Actual mapping remains deferred.

## Remote external agents

Remote external agents remain:

```text
NO LOCAL DIRECT AUTHORITY
```

For a remote agent to become eligible for a bounded consequence, its identity must be evaluated, it must be locally admitted, the relevant scope relationship and explicit Grant must exist, current policy and Target or current-state checks must pass, and required approval must exist.

A2A discovery, AgentCard capability advertisement, authentication, reputation, attestation, or remote message is not a Grant.

## Community and project agents

Community and project agents receive no ambient authority merely because they serve a scope.

```text
Community Agent + community membership != administrator authority
Project Agent + project association != repository mutation authority
```

A separate applicable Grant remains required whenever delegated authority is required by policy.

## Delegation by agents

By default, agents may not self-author or onward-delegate authority merely because they hold a Grant.

Source code, prompts, messages, attestations, plans, provider calls, sub-agent creation, and tool configuration produced by an agent cannot create a broader or downstream Grant.

Any future permission for an agent to act as Delegator must itself be separately explicit, bind what authority is delegable, remain within authority conservation, and not imply general subdelegation. Subdelegation remains deferred.

## Provider and client neutrality

Changing ChatGPT, Codex, another cloud model, a local model, or a deterministic service must not widen a Grant.

A provider session is not Grantee identity. A provider permission interface event is a request or provider-level event, not canonical Grant state, unless a later explicit trusted integration maps a verified decision through authoritative policy.

Provider persuasion, fallback, or self-reported necessity cannot alter Scope, capability, Target, constraints, validity, approval, or revocation.

## Trusted-channel requirement

Authority-bearing Grant state must travel through an authoritative structural channel or canonical runtime state appropriate to that semantic class.

Ordinary prompt text, retrieved documents, messages, agent output, attestation prose, READMEs, and tool descriptions must not be treated as active Grants.

A separate channel is insufficient unless the receiver gives it authority for Grant state under a verified precedence model. Unknown or conflicting precedence must fail closed using the canonical outcomes.

## Grant evidence and receipts

Future evidence should preserve enough provenance to determine:

- which Grant and revision was evaluated;
- who delegated to which exact Grantee;
- which Scope, capability, Target, and constraints were bound;
- which policy, state, approval, validity, consumption, revocation, and e-stop checks occurred;
- what authority exercise was requested;
- what effect was observed or remained uncertain;
- which evidence basis supports the result;
- whether the Grant remained applicable.

Receipts are evidence, not Grants or future authority. A receipt should not expose private approval text, credentials, private evidence bodies, or sensitive runtime topology merely to prove that a check occurred.

Historical evidence must remain preserved when a Grant expires, is consumed, revoked, superseded, or becomes inapplicable. History cannot recreate future authority.

## Failure and refusal

Grant evaluation must use the canonical Failure Outcome Taxonomy where its outcomes apply.

Examples include:

- no matching applicable Grant: `authority_denied` where the requested consequence is not authorized;
- missing evidence for a required Grant or state claim: `insufficient_evidence`;
- expired proof supporting an applicability requirement: `proof_expired` where the canonical meaning applies;
- stale or changed verification subject: `verification_invalidated`, followed by `replacement_required` where required;
- active e-stop or intentional halt: `paused` or another appropriate canonical stop outcome;
- incompatible trusted Grant channel: `unsupported_trusted_framing`, `unknown_channel_precedence`, or `provider_incompatible` as canonically defined.

This contract does not create a parallel failure taxonomy. Failure must not widen or generate a Grant, switch providers to escape policy, retry beyond an authorized budget, change Target, or resurrect expired, consumed, revoked, or inapplicable authority.

## Threat model

Each threat is governed by existing canonical law plus the bounded mechanics in this contract:

| Threat | Canonical defense |
|---|---|
| Agent self-grants authority | Governance and Capability/Authority: generated content cannot create effective authority; Grant state requires authoritative governance |
| Grantee passes Grant to a sub-agent | Non-transferability: onward delegation is denied by default and subdelegation is deferred |
| Stale Grant replay | Validity and applicability: current canonical comparison is required; historical state is not current authority |
| Expired Grant cached as active | Expiry and Derived Evidence: cached projection cannot override canonical validity |
| Revoked Grant restored through alternate transport | Scope revocation and Messaging: revocation applies across transports and routes |
| ONE_USE Grant replay after uncertain effect | Consumption reconciliation: reconcile canonical effect state before any retry; no blind replay |
| Restart resurrects temporary authority | Scope Sovereignty: temporary authority does not silently survive restart |
| Broad Target interpreted from vague prose | Exact Target and constraint binding: ambient targets and ordinary prose cannot widen the envelope |
| Wildcard repository or wallet authority | Authority conservation and Target binding: broad targets require explicit later governance and remain bounded |
| Provider permission event mistaken for Grant | Capability/Authority: a permission request is evidence of request, not a Grant |
| Message text mistaken for Grant | Messaging: message is not Grant; authoritative state uses a trusted channel |
| Attestation or reputation mistaken for Grant | Attestation: evidence and reputation are not authority or Grants |
| NFT, wallet, or ERC-8004 identity mistaken for authority | Scope and Agent Identity: external identity or ownership is evidence, not PrincipalId, admission, or Grant |
| Membership or admission mistaken for Grant | Scope and Agent Identity: membership and admission remain distinct from capability and authority |
| Technical capability mistaken for authority | Capability/Authority: `can_do(X)` does not imply `may_do(X)` |
| STANDING Grant becomes permanent ambient permission | Standing limits: exact bounds, expiry, revocation, current policy, state, approval, and e-stop remain required |
| Approval requirement dropped because Grant exists | Grant/approval separation: per-action approval remains separately evaluated where policy requires |
| Credential lease confused with Grant | Scope and credential separation: a credential lease and a Grant are distinct governed relationships |
| Grant amount ceiling confused with wallet authority | Budget bounds: a limit narrows evaluation and does not create wallet, signer, or spend authority |
| Grant copied across scopes | Scope binding: a Grant binds one ScopeId; copying does not change applicability or perform Release |
| Agent attempts authority amplification | Authority conservation: delegated authority cannot exceed delegable authority or widen through generated content |
| Old receipt restores authority | Evidence law: receipts are historical evidence, not Grants or future authority |
| Provider or session change widens effective authority | Provider neutrality and applicability: provider session is not identity and routing changes cannot widen a Grant |
| Administrator delegates outside its bounds | Authority conservation: Delegator identity or role is insufficient without exact delegable authority |

## Public and private boundary

A public Grant representation must not require disclosure of private user messages, private approval text, private cognition proofs, credentials, keys, private evidence bodies, hidden policy, or sensitive runtime topology.

Only deliberately released fields may be exposed, and their publication does not widen the Grant or its audience.

> **Open law. Private sovereignty.**

## Explicit denials

This contract does not authorize:

- implementation of Grants or a runtime policy engine;
- bearer capability tokens;
- OAuth, JWT, or macaroons;
- smart-contract permissions;
- wallet connection or signer activation;
- payment or x402;
- ERC-8004 registration or ERC-8004 Grant semantics;
- Base transactions;
- EAS;
- NFT or Lore Land authority;
- MCP or A2A authorization runtime;
- public posting;
- repository mutation;
- deployment;
- trading or social action.

No authority is activated by this documentation cut.

## Deferred decisions

This contract explicitly defers:

- exact GrantId format;
- serialization;
- storage backend and persistence;
- runtime owner;
- policy-engine owner;
- Grant API;
- cryptographic representation;
- signed-Grant format;
- bearer or non-bearer representation;
- subdelegation;
- exact STANDING-Grant lifecycle;
- exact ONE_USE consumption transaction;
- crash-reconciliation implementation;
- clock and freshness mechanism;
- Grant caching;
- distributed revocation;
- federation;
- credential-lease runtime;
- signer and wallet implementation;
- payment budgets and runtime;
- x402 integration;
- ERC-8004 identity mapping;
- Base registry and contract mapping;
- onchain Grant representation;
- EAS integration;
- Lore Land Grant relationships;
- user interface and user experience;
- administrator role taxonomy;
- MCP and A2A integration;
- repository and runtime ownership.

The governing sentence is:

> **Delegation grants bounded authority. It never transfers sovereignty.**
