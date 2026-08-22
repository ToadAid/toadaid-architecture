# ToadAid Ecosystem

## Purpose

ToadAid is a governed ecosystem, not a single agent and not an autonomous-agent swarm.

Its long-term purpose is to let the system safely grow new capabilities through an explicit lifecycle:

```text
understand
   ↓
blueprint
   ↓
bind intended work
   ↓
forge
   ↓
verify source and wiring
   ↓
prove live behavior
   ↓
review applicability
   ↓
activate when explicitly authorized
   ↓
learn and continue
```

The capability loop may continue. The authority loop must not close automatically.

## Major roles

### Mirror — continuity and architecture

Mirror is the governed intelligence substrate that understands ecosystem context and intended direction.

Mirror should increasingly be able to:

- consult governed memory and current system state;
- recognize missing capabilities;
- draft architecture and specialist blueprints;
- define capability requirements and explicit denials;
- define threat models and evaluation contracts;
- draft bounded `BUILD_LIST` items;
- propose improvements for human review.

Mirror does not gain authority merely because it designed a capability.

### ToadAid Coder — the forge

ToadAid Coder accepts bounded intended work and turns it into reviewable implementation.

It coordinates governed coding harnesses such as:

- Codex App Server;
- Grok ACP;
- future compatible coding providers.

ToadAid Coder owns the construction lifecycle, not the authority root.

### ToadAid MCP — the governed tool plane

ToadAid MCP supplies shared capabilities needed by coding agents and specialists.

The desired direction is semantic, bounded tooling rather than universal unrestricted shell access. Examples include:

```text
repo.inspect
repo.search
repo.read
workspace.diff
test.run
build.run
typecheck.run
git.status
git.diff
github.pr.create
github.checks.inspect
evidence.record
receipt.render
```

Capabilities may have different authority classes: read-only, proposal-only, authorized mutation, operator-only, or denied.

### Governance — MAY

Governance decides whether consequential operations are permitted.

A useful separation is:

```text
Mirror:         WHY / WHAT
Coding models:  HOW
Governance:     MAY
```

No reasoning provider owns `MAY`.

### Humans — sovereignty

Human control should remain meaningful and legible.

The goal is not to require approval for every low-level deterministic action. The goal is to preserve clear human control at consequential boundaries such as:

- accepting a blueprint;
- accepting a bounded build cut;
- authorizing a mutation;
- activating a new capability;
- signing a wallet action;
- publishing externally;
- merging a reviewed result.

## Mechanical governance substrate

The ecosystem must reuse shared mechanisms beneath its doctrine.

These mechanisms include:

```text
trusted-channel framework
confined process runner
provider-neutral capability adapters
proof registry
verification invalidation engine
derived-evidence claim constructors
production wiring tests
hostile/adversarial fixtures
runtime capability projection
activation ceremony
```

The purpose is not to add ceremony to every specialist. It is to prevent every specialist from rediscovering the same failure modes.

Three laws apply across the ecosystem:

```text
A security-relevant evidence claim must be derived from its observation.
A proof must stop governing the runtime when its bound subject changes.
Inputs with different trust semantics must travel through different structural channels.
```

## Proof layers

The ecosystem distinguishes:

```text
typed law
wiring proof
live proof
```

Typed law constrains representable source and schemas.

Wiring proof verifies what production adapters actually pass through arguments, environment, paths, contexts, transports, signers, and tool routers.

Live proof verifies what an external process or real effect did under bounded conditions.

None may impersonate another.

## End-to-end intended flow

```text
Tobyworld need
      ↓
Mirror understands context
      ↓
Mirror drafts blueprint + channel map
      ↓
Mirror defines verification subject + invalidation triggers
      ↓
Mirror drafts bounded BUILD_LIST items
      ↓
human/governance accepts direction
      ↓
ToadAid Coder accepts one intended cut
      ↓
Codex / Grok reason about implementation
      ↓
ToadAid MCP exposes governed tools
      ↓
implementation is forged
      ↓
typecheck + deterministic evaluation
      ↓
production wiring verification
      ↓
adversarial / live evaluation
      ↓
independent verification
      ↓
proof applicability check
      ↓
evidence + receipts
      ↓
human review
      ↓
explicit activation if separately authorized
      ↓
new capability joins ecosystem
      ↓
Mirror understands the enlarged system
```

If the verified subject changes before activation or during operation:

```text
historical proof preserved
      ↓
current proof invalidated
      ↓
replacement proof required
      ↓
authority remains denied or paused
```

This is **governed ecosystem evolution**, not uncontrolled recursive self-improvement.

## Governance-cost objective

The ecosystem should not require every specialist to rebuild its own governance runtime.

As shared substrate matures, governance cost per new specialist should decrease.

A specialist should primarily provide its identity, purpose, domain capability manifest, explicit denials, domain evidence adapters, and domain acceptance tests.

Confinement, trusted channels, proof applicability, receipt truth, and activation machinery should increasingly be inherited from shared substrate.

## Community Agent Fabric direction

Future personal, shared/community, project, specialist, and remote agents may collaborate through explicit scopes, admission, governed messaging, evidence and attestation exchange, and separately governed consequences. The [`Community Agent Fabric Blueprint`](blueprints/community-agent-fabric.md) composes those boundaries without creating shared private memory, ambient authority, or an autonomous-agent swarm.

## Governed runtime responsibility direction

The [`Governed Runtime Responsibility and Component Allocation`](blueprints/governed-runtime-component-allocation.md) blueprint assigns logical runtime responsibilities without making process placement or storage ownership a sovereignty root:

| Component | Architectural responsibility |
|---|---|
| Reasoning clients | Interchangeable intelligence, planning, and proposals |
| Mirror Core | Current governance evaluation kernel |
| Mirror Desktop Bridge | Local governed consequence edge |
| Living Agent | Continuity and scoped knowledge |
| ToadAid Coder | Repository and code specialist |
| ToadAid Trader | Market analysis and trade-intent specialist |
| ToadAid Zora Agent | Isolated high-consequence specialist |
| ToadAid MCP | Protocol and transport capability fabric |
| Community/project runtime | Collaborative composition under explicit scope |

Intelligence may propose, governance decides, and execution remains bounded. This direction does not activate any runtime or turn ToadAid into an autonomous-agent swarm.

## Design objective

The ecosystem should survive changes in individual model providers, interfaces, and repositories.

A provider is an intelligence implementation. It is not the architecture, the evidence root, or the governance root.
