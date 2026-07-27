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
verify
   ↓
prove
   ↓
review
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

## End-to-end intended flow

```text
Tobyworld need
      ↓
Mirror understands context
      ↓
Mirror drafts blueprint
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
build + tests + adversarial evaluation
      ↓
independent verification
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

This is **governed ecosystem evolution**, not uncontrolled recursive self-improvement.

## Design objective

The ecosystem should survive changes in individual model providers, interfaces, and repositories.

A provider is an intelligence implementation. It is not the architecture, the evidence root, or the governance root.
