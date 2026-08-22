# Governed Runtime Responsibility and Component Allocation

**Status:** Architecture blueprint

**Activation:** `NOT_INCLUDED`

## Purpose

This blueprint allocates logical runtime responsibility across the ToadAid ecosystem without activating runtime behavior or transferring the semantic ownership of any canonical contract.

The canonical contracts define the laws for scope sovereignty, capability and authority, agent identity and admission, messaging and delivery, attestations and evidence, and delegated authority. This blueprint answers the next architectural question: which component should carry each runtime concern while no component becomes a universal sovereignty root, reasoning brain, memory store, executor, wallet, or administrator?

The central laws are:

> **Intelligence may propose. Governance decides. Execution remains bounded.**

> **Component responsibility never transfers human sovereignty.**

## Status and non-activation

This document describes desired architecture, not current implementation. It does not establish that the described component boundaries, integrations, community agents, remote protocols, signers, or economic services exist or are active.

No authority, capability, provider, transport, credential, signer, wallet, payment, publication, deployment, or onchain operation is activated by this blueprint.

## Why this blueprint exists

Canonical law intentionally preceded runtime allocation. That ordering prevents current process boundaries or repository layouts from silently defining ecosystem semantics.

The following concepts remain distinct:

```text
semantic ownership
!= runtime responsibility
!= process placement
!= storage ownership
```

For example, the Scope Sovereignty Contract owns `ScopeId` semantics. Mirror Core may evaluate authoritative scope state, Living Agent may persist scope-bound continuity, and Mirror Desktop Bridge may bind a local workspace to a project scope. None of those runtime responsibilities transfers semantic ownership from the Scope Sovereignty Contract.

Physical co-location is also not semantic collapse. A small deployment may host several logical services in one process or on one machine, while their inputs, authority, state, failure, and verification boundaries remain distinct.

## Canonical law dependencies

This blueprint composes, and does not redefine:

- the [Scope Sovereignty Contract](../contracts/scope-sovereignty-contract.md), owner of `PrincipalId`, `ScopeId`, membership, audience, Release, and scope sovereignty;
- the [Capability / Authority Boundary Contract](../contracts/capability-authority-boundary.md), owner of capability, authority, request, and effective-capability semantics;
- the [Agent Identity and Specialist Admission Contract](../contracts/agent-identity-and-specialist-admission-contract.md), owner of `AgentId`, bindings, admission, and specialist admission;
- the [Agent-to-Agent Messaging and Delivery Contract](../contracts/agent-to-agent-messaging-and-delivery-contract.md), owner of message and delivery semantics;
- the [Attestation and Evidence Exchange Contract](../contracts/attestation-and-evidence-exchange-contract.md), owner of attestation and evidence-exchange semantics;
- the [Delegated Authority and Capability Grant Contract](../contracts/delegated-authority-and-capability-grant-contract.md), owner of `GrantId`, delegated authority, target binding, validity, consumption, and revocation;
- the [Trusted Channel Separation Contract](../contracts/trusted-channel-separation-contract.md), [Derived Evidence Contract](../contracts/derived-evidence-contract.md), [Evidence and Activation Contract](../contracts/evidence-activation-contract.md), [Verification Applicability Contract](../contracts/verification-applicability-contract.md), and [Failure Outcome Taxonomy](../contracts/failure-outcome-taxonomy.md).

The [Governed Ecosystem Architecture](governed-ecosystem-architecture.md) and [Community Agent Fabric Blueprint](community-agent-fabric.md) provide composition context. This blueprint allocates runtime responsibilities; it does not become a second owner for `PrincipalId`, `ScopeId`, `AgentId`, `GrantId`, membership, admission, Release, capability, authority, messages, attestations, receipts, or failure outcomes.

## Foundational distinctions

```text
reasoning != authorization
governance != execution
transport != authority
memory != permission
specialist expertise != authority
identity != authority
admission != authority
message != grant
attestation != authority
grant != approval
credential != authority
wallet != Principal
provider session != identity
component responsibility != sovereignty
```

## Whole-system conceptual model

```text
                     HUMAN PRINCIPAL
                           │
                           ▼
                  REASONING CLIENT
         cloud / local model / deterministic planner
              thinks · plans · proposes
                           │
                           ▼
                GOVERNED REQUEST EDGE
                           │
                           ▼
                MIRROR DESKTOP BRIDGE
               local consequence host
                           │
                           ▼
                      MIRROR CORE
             governance evaluation kernel
                           │
              ┌────────────┼────────────┐
              │            │            │
              ▼            ▼            ▼
          LIVING        CODER         TRADER
           AGENT       SPECIALIST     SPECIALIST
              │            │            │
              └────────────┼────────────┘
                           │
                           ▼
                    ZORA / FUTURE
                HIGH-CONSEQUENCE
                   SPECIALISTS
                           │
                           ▼
                 BOUNDED CONSEQUENCE
                           │
                           ▼
                  RECEIPT / EVIDENCE
```

This diagram is logical, not a required call graph. Specialist reasoning may occur before or during proposal refinement. Every consequential transition must still reach current governance and the applicable bounded consequence host. ToadAid MCP and future A2A mechanisms belong to transport and interoperability, never above governance as authority sources.

## Responsibility planes

### Intelligence Plane

Reasoning clients and specialists interpret intent, analyze domains, plan, propose, and construct candidate artifacts. They may request governed capabilities. They must not grant themselves authority or convert model output into a `Grant` or approval.

### Governance Plane

Mirror Core is the narrow governance kernel. It evaluates whether a requested consequence is currently eligible under canonical structured state and returns a canonical decision or outcome. Governance does not itself perform the consequence.

### Consequence Plane

Mirror Desktop Bridge and bounded execution adapters host local effects after applicable governance. They resolve exact targets, reverify current state immediately before effect, enforce bounds, reconcile uncertain effects, and capture evidence. Technical ability to execute is not an authority source.

### Continuity Plane

Living Agent and future scoped continuity services manage memory, time, retrieval, routines, and continuity. Their state may inform reasoning but cannot grant permission.

### Transport / Interoperability Plane

ToadAid MCP, future admitted A2A, HTTP, Streamable HTTP, STDIO, and other transports carry requests, artifacts, and evidence. Authentication, discovery, delivery, and tool presence do not create authority.

### Evidence Plane

Receipts, audit evidence, attestations, provenance, verification records, and reconciliation evidence describe what was requested, evaluated, or observed. Evidence remains distinct from authority, approval, acceptance, and future permission. This blueprint selects no universal evidence database or storage owner.

These planes must remain logically separable even where one process hosts more than one plane.

## Human Principal and reasoning clients

Reasoning clients include ChatGPT, Codex, Claude or other cloud clients, future local models, and deterministic planners where useful.

Their responsibilities may include:

- interpreting user intent;
- reasoning, analysis, planning, and drafting;
- proposing bounded actions and artifacts;
- asking for governed capabilities;
- presenting approval questions and understandable consequence summaries;
- consuming receipts and evidence.

They are interchangeable intelligence surfaces. They must not become the identity, admission, grant, policy, approval, or authority root.

```text
provider session != PrincipalId
provider session != AgentId
reasoning != authority
model output != Grant
tool request != approval
```

Changing provider must not widen scope, membership, admission, target, capability, Grant, approval, audience, or effective authority.

> **Use your AI normally. ToadAid governs consequences independently of which intelligence produced the request.**

## Mirror Core

Mirror Core is the narrow governance evaluation kernel.

Its primary responsibility is to evaluate current consequence eligibility from authoritative structured state. Depending on the request and applicable policy, it requires authoritative access to the relevant subset of:

- `PrincipalId` and `ScopeId`;
- `AgentId`, binding, and current admission state;
- requested capability and technical capability projection;
- `GrantId` and current Grant state where required;
- exact target binding and constraints;
- current policy and canonical current state;
- approval requirements and verified approval status;
- revocation, expiry, and `ONE_USE` consumption state;
- externally dominant e-stop state;
- relevant verification and applicability state.

Conceptually:

```text
request
  ↓ Principal
  ↓ Scope
  ↓ actor and admission
  ↓ capability
  ↓ Grant where required
  ↓ exact Target and constraints
  ↓ current policy and current state
  ↓ approval where required
  ↓ revocation / expiry / consumption
  ↓ e-stop
  ↓
canonical allow, deny, pause, or other applicable outcome
```

Mirror Core uses the canonical Failure Outcome Taxonomy. A positive evaluation is bounded to its subject and current state; it is not a general capability token or future approval.

Mirror Core must not become a conversational UI, general reasoning model, personal memory system, code or market specialist, wallet, signer, exchange client, social publisher, generic shell, transport fabric, MCP server merely by definition, or credential vault merely by definition.

Mirror Core requires authoritative access to evaluation state. It need not physically store every canonical record, memory item, receipt, scope object, or Grant. Exact storage ownership remains separately decidable.

## Mirror Desktop Bridge

Mirror Desktop Bridge is the client-facing local enforcement edge and local governed consequence host.

Its responsibilities may include:

- supported local client connection, including STDIO MCP exposure where applicable;
- workspace identity and repository target resolution;
- capability projection and structured governance-input collection;
- approval ceremony hosting and presentation;
- exact-state re-verification immediately before a local consequence;
- bounded execution adapters, cancellation, and e-stop integration;
- refusal propagation and uncertain-effect reconciliation support;
- receipt and evidence capture and forwarding;
- provider-neutral doctor and preflight surfaces.

The Bridge must not manufacture Grants, reinterpret canonical policy, act as a universal reasoning brain, become personal memory or a wallet, infer `PrincipalId` from filesystem ownership, treat client permission dialogs as canonical authority, broaden a target, execute against stale exact-state binding, or route around Mirror Core merely because an operation is local.

OpenAI, ChatGPT, Codex, and other providers own their client experiences. The Bridge must use supported protocol seams such as MCP where applicable; it must not require forking, patching, injecting into, scraping, or relying on undocumented internals of third-party desktop clients.

> **Use your AI normally. Mirror makes local consequences safe.**

## Living Agent

Living Agent is the continuity and scoped-knowledge specialist.

Its responsibilities may include personal continuity, temporal awareness, routines, memory, scope-bound retrieval and files, separately admitted shared or project knowledge retrieval, local-model continuity, reminders, recurring cognitive work, and scheduled intentions or duties.

```text
memory != permission
retrieval != Release
schedule != standing authority
knowledge != capability
```

Living Agent must not decide consequence authority because memory records an earlier desire. A scheduled duty that reaches a consequential capability must become a fresh governed request at consequence time.

For example, checking and reasoning about project status each morning may be cognitive work. Pushing a branch, sending an external message, publishing, trading, signing, or deploying must cross the applicable governance and consequence boundary.

Personal state remains private by default. Joining a project or community does not cause personal-memory inheritance.

## ToadAid Coder

ToadAid Coder is the repository and code specialist.

Its responsibilities may include repository analysis, semantic and CodeGraph-assisted understanding, patch proposals, diff analysis, tests, builds, validation, pull-request construction proposals, CI interpretation, narrow repair proposals, and source-specific evidence.

```text
Coder can understand Repository R != Coder may mutate Repository R
Coder generated a patch != Coder may commit, push, or merge it
```

A governed repository flow is:

```text
User or Reasoning Client
    ↓
Coder analyzes and proposes
    ↓
Mirror governance
    ↓
exact repository / branch / HEAD / path binding
    ↓
approval where required
    ↓
Mirror Desktop Bridge executes a bounded operation
    ↓
receipt and evidence
```

Coder expertise does not create repository sovereignty or merge authority. This blueprint activates no Coder integration.

## ToadAid Trader

ToadAid Trader is a market-analysis and trade-intent specialist.

Its responsibilities may include market observation, quote and liquidity comparison, portfolio observation, signal generation, strategy evaluation, consensus packets, risk calculations, simulation, trade construction, slippage bounds, trade-intent proposals, expected-result calculations, and analytical reconciliation.

Trader must not inherently own funds, wallet sovereignty, private keys, seed phrases, unrestricted exchange credentials, unrestricted signer sessions, autonomous budget, or arbitrary trading authority.

A future conceptual flow is:

```text
market analysis
    ↓
TradeIntent
    ↓ exact asset / venue / amount / destination /
      slippage / expiry / constraints
    ↓
Mirror governance
    ↓ Grant + current state + approval
    ↓
separate signer and execution boundary
    ↓
effect
    ↓
reconciliation + receipt
```

This blueprint implements no trading and selects no exchange, wallet, signer, chain, or economic runtime.

## ToadAid Zora Agent

ToadAid Zora Agent is an isolated high-consequence specialist for later-admitted external, public, or onchain capabilities.

Possible responsibilities include constructing bounded publication or onchain intent, validating an exact target and payload, domain-specific reasoning, preparing evidence for human decision, and domain-specific reconciliation where later activated.

```text
Zora AgentId != signer authority
Zora admission != publishing authority
Zora capability != wallet authority
model proposal != transaction approval
```

A future signing path preserves:

```text
MODEL
  ↓ bounded intent
MIRROR
  ↓ governance
SEPARATE SIGNER / CUSTODY BOUNDARY
  ↓ exact authorized transaction only
```

Raw private keys and seed phrases must not enter reasoning context. This blueprint activates no wallet, signing, posting, minting, Base interaction, or Zora API execution.

## ToadAid MCP

ToadAid MCP is the protocol, service, and transport capability fabric.

Its responsibilities may include MCP tool and resource schemas, authenticated ingress, bounded HTTP or HTTPS ingress where admitted, Streamable HTTP, STDIO, protocol lifecycle, client compatibility, routing metadata, capability discovery, remote transport, and carriage of structured Principal, Scope, Agent, request, and evidence references where later defined.

> **MCP carries the request. Mirror governs the consequence.**

MCP must not become a Principal, `AgentId`, Grant issuer, authority root, reasoning brain, wallet, memory owner by implication, universal e-stop owner, or universal orchestration brain.

Tool discovery, tool availability, permission to invoke, invocation, consequence authorization, and successful effect remain distinct.

## Community and project agent runtime

The future community and project agent runtime is a composition layer for explicit collaborative scopes.

It may coordinate shared or project state, scope-owned memory, tasks, messages, admitted specialists, releases, attestations, evidence, and scheduled work.

It must not become the union of members' personal memory, a universal administrator or signer, an automatic repository owner, an automatic wallet owner, or an authority aggregate inherited from members.

```text
room presence != membership
membership != admission
admission != Grant
project membership != repository mutation authority
community membership != personal-memory access
```

## Future credential and signer boundary

Credentials and signers should remain a separately governed narrow responsibility rather than being placed in Mirror Core, Bridge, Living Agent, Coder, Trader, Zora, or MCP merely for convenience.

```text
credential != Grant
credential lease != authority
private key != PrincipalId
signer possession != approval
wallet ownership != AgentId
```

A future service may perform narrow secret or signature use against an exact, already governed envelope. It must not receive unrestricted authority or expose raw secrets to reasoning models. The credential broker, vault, signer, custody model, process, repository, and protocol remain deferred.

## Provider neutrality

Changing among ChatGPT, Codex, Claude, another cloud model, a local model, or a deterministic service must not change `PrincipalId`, `ScopeId`, `AgentId`, `GrantId`, membership, admission, target binding, authority, approval requirements, revocation, or e-stop.

> **Brains can be interchangeable. Agent identity and authority are not.**

Provider or harness configuration may constrain what a model can represent or how it behaves. It cannot become canonical ToadAid identity or authority. Where a provider surface conflicts with required trusted framing and precedence cannot be established, the system must use the applicable fail-closed canonical outcome rather than pretend the provider was reconfigured.

## No giant orchestrator

ToadAid rejects an architecture in which one component silently owns:

```text
reasoning + memory + identity + scope + Grants + transport
+ credentials + execution + wallets + evidence + administration
```

No early deployment convenience may turn one service into a sovereignty root. One machine may host many services; logical responsibilities and trust boundaries remain distinct.

## Initial repository responsibility map

| Component | Primary responsibility | Must not own by implication |
|---|---|---|
| Reasoning Client | Reasoning, planning, proposals, and UI | Authority, canonical identity, or consequence permission |
| Mirror Core | Current governance evaluation | Reasoning brain, wallet, personal memory, or transport monopoly |
| Mirror Desktop Bridge | Local consequence enforcement edge | Sovereignty, ambient shell authority, or personal memory |
| Living Agent | Continuity, memory, time, and scoped knowledge | Permission, wallet authority, or repository authority |
| ToadAid Coder | Code and repository expertise | Repository sovereignty or merge authority |
| ToadAid Trader | Market expertise and trade intent | Funds, signer, or autonomous trading authority |
| ToadAid Zora Agent | High-consequence domain expertise | Signer sovereignty or automatic public/onchain authority |
| ToadAid MCP | Protocol and transport | Grant issuance, authority root, or reasoning brain |
| Community / Project Agent | Collaborative scope coordination | Personal-member sovereignty or private memory |
| Future credential / signer service | Narrow secret or signature use | `PrincipalId`, approval, or unrestricted authority |

This map assigns logical direction. It does not assert current implementation completeness or select final repository ownership for unresolved services.

## Data ownership and authority

Data access, persistence, and authority remain separate:

- Living Agent may persist memory without controlling authority.
- Mirror Core may evaluate scope state without owning all scope data.
- Bridge may access a workspace without owning the project.
- Coder may inspect a repository without owning mutation rights.
- Trader may inspect portfolio information without owning funds.
- Zora may construct a transaction without signing authority.
- MCP may carry a request without authorizing it.

Storage ownership never becomes semantic ownership or sovereignty by implication.

## Inputs, channels, and trust boundaries

The fabric accepts intent, canonical governance state, continuity context, specialist analysis, external messages or evidence, approvals, and runtime observations through distinct structural channels.

| Channel | Writers | Readers | May establish | Must not establish |
|---|---|---|---|---|
| Operator/task input | Human-facing client | Reasoning client; governed request edge | Requested intent and supplied content | Identity, Grant, approval, or policy state by prose alone |
| Trusted identity/scope/admission state | Canonical governed state owners | Mirror Core; bounded enforcement edge as needed | Current identity, binding, scope, and admission claims for which the path is authoritative | New facts outside its semantic class |
| Trusted Grant/policy/e-stop state | Canonical governance path | Mirror Core; Bridge for enforcement projections | Current Grant, policy, revocation, consumption, and e-stop state where precedence is verified | Reasoning conclusions or arbitrary target substitution |
| Approval decision channel | Authorized governance surface | Mirror Core and bounded consequence host | Bounded approval status for the exact action class | General standing authority or private approval text disclosure |
| Continuity/memory channel | Scope-governed continuity mechanisms | Living Agent and admitted readers | Scoped historical or continuity context | Permission, Release, or current policy |
| Retrieved/external evidence | Bounded evidence adapters, remote peers | Specialists and verifiers | Provenanced candidate evidence | Trusted configuration, Grant, or approval |
| Provider/specialist output | Reasoning providers and admitted specialists | Request edge, humans, other admitted agents | Advisory analysis, proposal, or artifact | Canonical state, proof status, or authority |
| Runtime observation/reconciliation | Bounded adapters and effect observers | Evidence plane, Core, Bridge | Observed result under its declared evidence basis | Future authority |

Ordinary prompt text, retrieved documents, model output, messages, attestations, READMEs, and tool descriptions are never active Grants. Channel authority depends on the production receiver and verified precedence, not a provenance label. Unknown or conflicting precedence fails closed with canonical outcomes such as `unknown_channel_precedence`, `unsupported_trusted_framing`, or `provider_incompatible` where their defined meanings apply.

Permitted transformations include operator intent into a proposal, canonical state into a sanitized capability projection, scope-authorized evidence into a narrow derived claim, and observed effects into grounded receipts. Each transformation preserves provenance and cannot widen scope or authority.

Forbidden crossings include provider output into policy state, memory into permission, retrieved evidence into approval, message prose into Grant state, private scope material into shared/public context without Release, and receipt data into reusable authority.

## Outputs and authority ceiling

Advisory outputs include plans, analyses, proposed artifacts, messages, attestations, validation findings, trade or publication intents, and requests. State-changing outputs are limited to consequences separately admitted by current governance and executed through a bounded consequence host.

Every state-changing output requires the applicable provenance, current-state binding, policy decision, effect observation, reconciliation status, and receipt. This blueprint grants no component authority to activate itself, widen its capability surface, select a new target, delegate onward, expose private data, use credentials, or cause external effects.

## Local interactive flow

```text
Human Principal
    ↓
Reasoning Client
    ↓ request / proposal
Mirror Desktop Bridge
    ↓ structured governed request
Mirror Core governance evaluation
    ↓
specialist reasoning where needed
    ↓ updated exact consequence proposal
current governance re-evaluation where required
    ↓
human approval where required
    ↓
Mirror Desktop Bridge exact-state reverify
    ↓
bounded consequence
    ↓
receipt / evidence
```

Not every cognitive specialist call requires consequence approval. ToadAid governs consequences, not thoughts. Any proposal change that affects target, capability, constraints, current state, or approval subject requires the applicable re-evaluation before effect.

## Remote and MCP flow

```text
Reasoning Client or Remote Agent
    ↓
ToadAid MCP
    ↓ authenticated request/evidence transport
local identity, admission, scope, and Grant evaluation
    ↓
Mirror governance
    ↓
bounded consequence host
    ↓
receipt
```

```text
authenticated transport != authority
remote agent != local direct authority
MCP discovery != Grant
A2A message != Grant
```

Revocation and e-stop apply across MCP, A2A, direct, local, and future transport routes. Switching transport cannot restore authority.

## Scheduled and background flow

```text
Living Agent or Scheduler
    ↓ scheduled duty fires
bounded request
    ↓
current Principal / Scope / Agent / Grant state
    ↓
Mirror governance
    ↓
approval where required
    ↓
bounded consequence
```

Scheduling must not freeze the authority state that existed when the schedule was created. Current authority is re-evaluated at consequence time.

```text
schedule != standing authority
old approval != future approval
restart != authority restoration
```

## Specialist-to-specialist flow

Agents may exchange messages, tasks, artifacts, evidence, attestations, and capability requests. The receiving specialist independently evaluates its own admission, scope, Grant, target, constraints, current policy, approval, revocation, and e-stop state.

```text
Specialist A message != authority for Specialist B
Specialist A Grant != Specialist B Grant
parent agent authority != child specialist authority
```

## Current-state, revocation, recovery, and e-stop

Consequential evaluation binds canonical current state, not cached projections, provider assertions, or old receipts. Mirror Core evaluates current eligibility; the consequence host reverifies the exact mutable target immediately before effect where applicable.

Revocation remains dominant across providers, transports, and process boundaries. E-stop remains externally dominant and cannot be routed around by changing client, specialist, MCP route, A2A route, or local process.

Temporary authority does not silently survive restart. Restart and recovery must reload canonical revocation and e-stop state and re-establish current applicability. Clearing e-stop must not automatically replay queued effects.

For `ONE_USE` Grants, the Delegated Authority Contract remains canonical: uncertain external effect requires reconciliation first and never blind replay. The Bridge and bounded adapters support effect observation; Core evaluates the resulting canonical consumption and applicability state. Neither component may infer success or safe retry from provider completion.

```text
Grant != approval
```

Per-action approval remains independently evaluated wherever current policy requires it.

## Receipts and evidence

Every consequential implementation should eventually preserve enough evidence to determine:

- Principal, Scope, and Agent or specialist;
- requested capability and `GrantId` where applicable;
- exact Target and constraints;
- current-state and policy binding;
- approval status where applicable;
- revocation, expiry, consumption, and e-stop evaluation;
- effect or result and reconciliation status;
- relevant source provenance and proof applicability.

Evidence claims must derive from observations, classifiers, comparisons, or enforcement mechanisms. Receipts are evidence, not Grants, approval, acceptance, or future authority. This blueprint selects no universal receipt database.

## Failure and refusal

All components use the [Failure Outcome Taxonomy](../contracts/failure-outcome-taxonomy.md). They may define narrower local subtypes only when mapped to the canonical vocabulary without changing its meaning.

Missing authority, missing evidence, invalidated proof, incompatible trusted framing, provider failure, refusal, pause, and e-stop conditions must remain truthful and non-escalating. Boundary failure must not widen authority, switch providers or transports to escape policy, leak private data, use stale Grant state, blindly retry, substitute another specialist, or change the target.

## Verification and production path

This blueprint does not call an implementation verified. Each implementation wave must define its own evaluation contract and verification subject.

At minimum, verification distinguishes:

- typed or structural proof that interfaces and closed state representations preserve canonical distinctions;
- production wiring proof that the real adapters carry trusted state, requests, decisions, effects, and receipts through the intended channels;
- live or adversarial proof for real provider, process, transport, signer, or external-effect boundaries where activation requires it.

No layer substitutes for another. The verification subject must bind the relevant source and executable identity, policy and channel configuration, provider or harness precedence assumptions, environment and working-directory policy, adapter path, schema version, capability and authority surface, and evaluation-contract version.

Changes to Core decision wiring, Bridge enforcement paths, specialist adapters, target resolution, trusted channels, policy, capability surfaces, credential/signer boundaries, or receipt derivation invalidate the affected proof layer and require replacement proof. Historical proof remains historical.

The production path under test is the actual path carrying authority-relevant behavior:

```text
operator or remote input
→ structural request adapter
→ authoritative state lookup and Mirror Core evaluation
→ bounded specialist / consequence adapter
→ exact-state reverify
→ effect observation or refusal
→ reconciliation
→ derived receipt
```

A safer standalone ceremony beside an unverified product path is insufficient. Where activation would create consequential effective capability, independently inspect the applicable proof before a separate activation decision. If independent applicable verification is unavailable, activation remains `activation_denied`.

## QM reference harvest

QM is a reference implementation and product-pattern source, not a dependency, authority model, or required topology.

Useful patterns to keep or adapt include:

- a headless core with optional product surfaces;
- provider and harness neutrality;
- per-scope workspace isolation and scoped memory;
- resource grants and durable sessions;
- cron or job queues and shared skills;
- credential and keychain separation;
- portal-only high-risk governance decisions and clear approval UX;
- refusal to trust a model or sandbox to authorize itself;
- plugin-based product surfaces.

ToadAid adaptations are mandatory:

| Reference pattern | ToadAid adaptation |
|---|---|
| Scoped memory | Explicit Scope ownership and Release |
| Skills | Procedure only; separate capability and Grant |
| ACL or resource grants | Subordinate resource mechanism under generalized Grant law |
| Cron | Scheduled duty with current authority re-evaluation |
| Credentials | Separate narrow credential lease plus consequence governance |
| Shared agents | Community/project agent without personal-memory inheritance |
| Provider swapping | No identity or authority change |

ToadAid rejects as canonical assumptions administrator private omniscience, browser or provider paths that bypass governance, ambient plaintext credentials as sufficient security, credential-purpose prose as authorization, transport bypass around effect gates, incomplete kill or e-stop semantics, room presence as membership, and provider session as identity.

## Implementation waves

These waves are architecture-level sequencing only. Each requires a later bounded implementation cut and separate activation decision.

### Wave 1 — Mirror Core

Project canonical governance contracts into a minimal kernel for Principal and Scope references, Agent admission references, Grant evaluation, exact target matching, current policy and state, approval dependency, revocation, expiry, `ONE_USE` state, e-stop, and canonical outcomes. Avoid broad execution.

### Wave 2 — Mirror Desktop Bridge

Consume Mirror governance at the local consequence edge: workspace binding, supported client integration, capability projection, approval ceremony, exact-state reverify, bounded adapters, receipts, doctor surfaces, and e-stop.

### Wave 3 — Living Agent

Project scope sovereignty into memory, temporal awareness, routines, scheduled duties, personal/shared/project retrieval, and Release boundaries. Memory supplies no authority.

### Wave 4 — ToadAid Coder

Admit Coder as a repository specialist with exact targets, proposal/execution separation, governed mutation, build and CI evidence, and receipts.

### Wave 5 — ToadAid Trader

Admit Trader first as an analysis and trade-intent specialist. Economic authority requires separate contracts and activation.

### Wave 6 — ToadAid Zora Agent

Project high-consequence specialist admission and exact action envelopes while preserving separate signer and human-approval boundaries.

### Wave 7 — ToadAid MCP

Carry identity, scope, request, decision-reference, and evidence semantics across supported transports without becoming the authorization owner.

### Wave 8 — Community and project runtime

Compose personal, shared, project, and specialist agents under explicit scope, membership, Release, admission, and Grant law.

### Wave 9 — External interoperability

Only after local sovereignty survives implementation, consider A2A, ERC-8004 identity mapping, x402 or payments, Base or EAS, Lore Land project mapping, and federation. None is activated here.

## Threat model

| Threat | Canonical and allocation defense |
|---|---|
| Reasoning client claims authority | Capability/Authority and trusted channels: model output is advisory; Core reads authoritative state |
| Mirror Core becomes a universal monolith | Responsibility planes: Core evaluates governance and does not inherit reasoning, memory, transport, credential, or execution ownership |
| Bridge creates authority because it can execute | Capability/Authority: technical capability is not authority; Bridge consumes Core decisions and reverifies bounds |
| Living Agent memory is treated as permission | Scope Sovereignty: memory never grants permission; current consequence evaluation is separate |
| Scheduled duty preserves stale authority | Scope and Grant law: current authority is re-evaluated at consequence time |
| Coder treats patch generation as repository authorization | Agent admission and Grant law: expertise and artifacts do not create target authority |
| Trader receives ambient wallet credentials | Scope and credential separation: credentials are narrow dependencies, never ambient memory or authority |
| Zora receives unrestricted signer authority | Specialist isolation and Grant law: bounded intent crosses a separate signer/custody boundary |
| MCP tool discovery becomes permission | Capability/Authority: discovery, availability, invocation, and authorization are distinct |
| Remote agent bypasses local admission | Agent Identity: remote agents default to no local direct authority |
| Provider switch widens authority | Provider neutrality: authoritative identity, Grant, policy, revocation, and e-stop state remain unchanged |
| Project agent reads personal member memory | Scope Sovereignty and Release: community membership is not personal-memory consent |
| Community membership becomes administrator authority | Scope and Grant law: membership, admission, and authority remain distinct |
| One specialist delegates to another implicitly | Grant non-transferability: each specialist requires its own applicable authority |
| Process co-location collapses trust boundaries | Trusted channels and logical planes remain structurally distinct despite shared hosting |
| Exact-state reverify is omitted | Verification applicability and Bridge responsibility require current target binding immediately before consequence |
| E-stop applies to only one transport | Scope and Grant law: e-stop and revocation dominate across all routes |
| Credentials become reasoning context | Credential boundary: raw secrets are excluded from model context and narrow use remains separately governed |
| Receipt becomes reusable authority | Evidence law: receipts preserve history and never create a Grant or future authority |
| Runtime storage owner is mistaken for semantic owner | Canonical dependency boundary: persistence responsibility cannot redefine contract-owned semantics |

Prompt injection, poisoned context, false capability claims, and non-authoritative trusted framing are handled as instances of untrusted input and channel separation: remote, retrieved, remembered, or provider-authored content cannot write canonical identity, policy, Grant, approval, or proof state.

## Explicit non-claims and denials

This blueprint does not:

- activate Mirror Core or modify Mirror Desktop Bridge;
- modify Living Agent, Coder, Trader, Zora Agent, or ToadAid MCP;
- implement a community or project runtime;
- select a database, event bus, RPC framework, exact API, or exact schema;
- create a wallet, connect a signer, activate credentials, or expose secrets;
- perform trading, payment, x402, public publication, repository mutation, deployment, or social action;
- enable A2A, register ERC-8004 identities, perform Base transactions, use EAS, or map Lore Land ownership to authority;
- grant provider, model, specialist, administrator, component, or storage owner new authority.

## Deferred decisions

Unless already owned by a canonical contract, this blueprint defers:

- exact process topology and microservice-versus-monolith packaging;
- exact storage ownership and database selection;
- event bus, IPC, RPC, and exact Mirror Core API;
- exact Bridge/Core protocol and specialist adapter format;
- remote federation, cloud deployment, and public networking;
- credential broker, signer, custody, and wallet implementation;
- economic policy, payment budgets, and x402;
- onchain identity and ERC-8004 registry mapping;
- Lore Land mapping, A2A runtime, and EAS runtime;
- admin and community user interfaces;
- final repository ownership for unresolved runtime services.

Logical responsibility allocation is the purpose of this cut. Physical implementation, verification, and activation come later.

## Governing principles

1. Intelligence may propose. Governance decides. Execution remains bounded.
2. Component responsibility never transfers human sovereignty.
3. Semantic ownership, runtime responsibility, process placement, and storage ownership remain distinct.
4. Govern consequences, not thoughts.
5. Current authority is evaluated at consequence time.
6. Transport changes neither identity nor authority.
7. Memory, evidence, credentials, and technical capability are not permission.
8. No component becomes a giant orchestrator by convenience or co-location.
9. Every consequential path remains bounded, observable, reconcilable, and subject to externally dominant e-stop.
10. Activation is not included.
