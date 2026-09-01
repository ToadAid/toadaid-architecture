# ToadAid Social Control Plane Map

**Status:** Architectural composition map / not runtime authority

**Activation:** `NOT_INCLUDED`

**Purpose:** Show how sovereign personal scopes, shared/project scopes, governed relationship state, agents, and isolated execution domains compose without collapsing personal memory, membership, capability, or consequence authority.

This map is a projection of existing ToadAid architectural law. It does not create new scope types, grant semantics, admission semantics, runtime authority, or implementation ownership.

## Canonical owners

This map composes, and does not redefine:

- [`../blueprints/community-agent-fabric.md`](../blueprints/community-agent-fabric.md) for the Community Agent Fabric composition model;
- [`../contracts/scope-sovereignty-contract.md`](../contracts/scope-sovereignty-contract.md) for principals, scopes, membership, audience, release, and scope sovereignty;
- [`../contracts/agent-identity-and-specialist-admission-contract.md`](../contracts/agent-identity-and-specialist-admission-contract.md) for agent identity, principal/scope binding, admission, and admission revocation;
- [`../contracts/delegated-authority-and-capability-grant-contract.md`](../contracts/delegated-authority-and-capability-grant-contract.md) for grants, delegation, expiry, consumption, revocation, and grant applicability;
- [`../contracts/agent-to-agent-messaging-and-delivery-contract.md`](../contracts/agent-to-agent-messaging-and-delivery-contract.md) for governed messaging and delivery;
- [`../contracts/attestation-and-evidence-exchange-contract.md`](../contracts/attestation-and-evidence-exchange-contract.md) for attestations and evidence exchange;
- [`../contracts/capability-authority-boundary.md`](../contracts/capability-authority-boundary.md) for the separation between capability and authority.

If this map conflicts with an owning contract, the owning contract remains canonical until deliberate architectural reconciliation.

## Community / organization composition

```text
                   COMMUNITY / ORGANIZATION
                           │
                  ┌────────▼────────┐
                  │ SOCIAL CONTROL  │
                  │     PLANE       │
                  │                 │
                  │ identity        │
                  │ membership      │
                  │ scopes          │
                  │ grants          │
                  │ delegation      │
                  │ revocation      │
                  │ audit           │
                  │ routing         │
                  └────────┬────────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
      Private LA       Private LA       Project Scope
    / personal scope  / personal scope    / shared domain
          │                │                │
       agents           agents           agents
       memory           memory        shared state
       tools            tools         scoped tools
          │                │                │
          └──────── isolated execution ─────┘
```

`Private LA` is shorthand for a future personal-agent continuity arrangement bound to one sovereign personal scope. It does not imply that every personal agent must use one specific process, container, VM, Gateway, or provider.

`Project Scope` means the canonical ToadAid project scope. A shared/community deployment uses the existing `shared` scope type rather than inventing a separate community scope type.

## What the Social Control Plane means

The Social Control Plane is the governed relationship layer through which a future community or organization can reason about and apply already-defined architectural relationships such as:

```text
principal identity
    ↓
scope identity
    ↓
membership and audience
    ↓
agent binding and admission
    ↓
message / request / attestation relationships
    ↓
grant or delegation relationships where separately valid
    ↓
revocation / expiry / applicability
    ↓
routing to the correct governed scope or execution domain
```

It is not a global shared brain and it is not an ambient administrator.

The Social Control Plane must not silently turn any of these facts into another:

```text
identity != membership
membership != admission
admission != capability
capability != authority
grant != execution
message != grant
attestation != authority
room presence != membership
shared context != personal memory
project membership != repository mutation authority
```

## Personal sovereignty

Joining a project or shared scope does not merge personal scopes.

```text
Personal Scope A ──┐
                   ├── explicit governed relationships ──► Project Scope X
Personal Scope B ──┘
```

The valid result is not:

```text
Project Scope X = Personal Scope A + Personal Scope B
```

Instead:

```text
Project Scope X
  ├─ owns its own membership state
  ├─ owns its own admitted shared/project knowledge
  ├─ owns its own project artifacts and relationships
  └─ receives personal information only through valid governed release
```

Personal memory, files, credentials, and authority remain outside the project scope unless the applicable canonical contract permits an exact, explicit crossing.

## Coordination is not consequence authority

The Social Control Plane belongs conceptually to the Community Agent Fabric coordination layer. It does not own `MAY` for consequential effects.

```text
SOCIAL / COMMUNITY COORDINATION
identity
membership
scopes
routing
messages
requests
attestations
grant references
revocation state

        ↓ proposal / exact governed relationship only

GOVERNED CONSEQUENCE PLANE
current capability admission
exact target binding
current policy
current state
current applicable authority
approval where required
revocation / expiry / e-stop
bounded execution
receipts / evidence
```

A valid grant may be represented or routed through the social layer, but grant mechanics and applicability remain owned by the delegated-authority contract. The presence of a grant reference does not itself execute an effect.

## Isolation domains

The lower execution layer may eventually use processes, sandboxes, containers, VMs, remote workers, separate hosts, or another proven isolation mechanism. This map intentionally does not choose one.

The invariant is architectural rather than vendor-specific:

```text
scope relationship
    !=
shared runtime trust
```

Two principals may belong to the same project while their personal-agent execution, memory, credentials, and private state remain independently isolated.

A project or community agent may have its own execution domain and shared-scope state without inheriting the private execution domain or memory of its members.

## Routing model

Routing must preserve the source principal, source scope, destination scope, agent identity, and applicable policy boundaries rather than flattening all activity into one undifferentiated agent session.

Conceptually:

```text
Human / Personal Agent
        │
        │ request, message, release proposal, or governed delegation
        ▼
Social Control Plane
        │
        ├──► same personal scope
        ├──► explicit project/shared scope
        ├──► admitted specialist
        └──► governed consequence path
```

Routing is not authorization. A correctly routed request may still be refused because membership, admission, release, grant applicability, target binding, approval, or another governing condition is absent or stale.

## Revocation model

Revocation must be able to narrow future access and authority without rewriting history.

Examples include:

```text
membership revoked
    → future membership-dependent access no longer applies

agent admission revoked
    → future admission-dependent participation no longer applies

grant revoked / expired / consumed
    → future grant-dependent consequence authority no longer applies
```

Historical messages, receipts, attestations, and audit evidence remain historical facts subject to their own retention rules. They must not be mistaken for current access or current authority.

## External convergence note: OpenClaw

OpenClaw is a useful non-authoritative reference point because its 2026 team architecture independently exposes several lower-layer primitives that ToadAid already treats as architectural subjects: person identity, roles, session ownership and participation, multiple agents, sandbox requirements, and isolated per-tenant Gateway cells.

OpenClaw's own documentation states that one Gateway remains one trusted operator domain and that mutually untrusted tenants require separate Gateway cells. Its experimental Fleet layer explicitly leaves multi-machine identity-governed fleet control to a separate control-plane layer.

This convergence is evidence that the problem class is real; it is not ToadAid architectural authority, a dependency choice, or permission to copy OpenClaw semantics into canonical ToadAid contracts.

References:

- <https://github.com/openclaw/openclaw>
- <https://docs.openclaw.ai/start/teams>
- <https://docs.openclaw.ai/gateway/multi-tenant-hosting>

## Non-goals

This map does not choose or activate:

- a Community Agent Fabric runtime;
- a social-control-plane implementation repository;
- an identity provider;
- a database or transport;
- OpenClaw or another agent runtime as a dependency;
- a container, VM, or cloud-worker implementation;
- credentials, wallets, signing, publication, repository mutation, payments, or onchain effects;
- automatic authority from membership, reputation, tokens, NFTs, rooms, messages, or model output.

## Core law

```text
sovereign principals
    + explicit scopes
    + explicit relationships
    + bounded agents
    + isolated execution
    + revocable authority
    != shared sovereignty
```

The intended outcome is collaboration without ownership collapse:

> **Agents may collaborate. Humans remain sovereign. Shared scopes own only what is explicitly theirs.**
