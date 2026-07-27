# Governed Agent Forge Blueprint

## Purpose

The Governed Agent Forge is the future ToadAid capability for turning an identified ecosystem need into a bounded specialist without allowing the creator, coding provider, or generated specialist to manufacture its own authority.

The forge is not an autonomous spawning system.

It is a governed construction pipeline.

## Core lifecycle

```text
NEED
  ↓
MIRROR ARCHITECTURE
  ↓
BLUEPRINT
  ↓
BUILD_LIST CUTS
  ↓
DIRECTION ACCEPTANCE
  ↓
TOADAID CODER
  ↓
CODEX / GROK
  ↓
TOADAID MCP
  ↓
SOURCE + TESTS + DOCTRINE
  ↓
DETERMINISTIC VERIFICATION
  ↓
ADVERSARIAL VERIFICATION
  ↓
CANDIDATE SPECIALIST
  ║
  ║ AUTHORITY WALL
  ║
  ↓
SEPARATE ACTIVATION DECISION
  ↓
BOUNDED SPECIALIST
```

## Required states

A specialist should progress through explicit states rather than one ambiguous `ready` flag.

Suggested conceptual states:

```text
idea
blueprinted
accepted_for_build
building
candidate
verified
activation_pending
active
paused
revoked
retired
```

Transitions that increase effective authority require appropriate governance.

## Required artifacts

Before build:

- specialist identity and purpose;
- canonical blueprint;
- capability manifest;
- explicit denial manifest;
- threat model;
- memory/provenance model;
- evaluation contract;
- bounded BUILD_LIST.

During build:

- source changes;
- tests;
- deterministic verification output;
- provider-neutral evidence;
- authority-relevant receipts.

Before activation:

- completed verification contract;
- adversarial confinement results;
- effective capability projection;
- explicit activation decision.

## Capability manifest

A specialist must not infer its own permissions from its purpose.

Example:

```text
specialist: lore-steward

requested:
  corpus.read
  corpus.search
  evidence.write

denied:
  shell.execute
  repository.write
  github.push
  wallet.sign
  social.publish
```

The runtime computes effective capability from trusted policy and authorization. The manifest is a request/contract, not a grant.

## Blueprint approval versus activation approval

These are separate decisions.

Blueprint approval means:

> The architecture is acceptable to build as a candidate.

Activation approval means:

> The verified candidate may receive specified effective capabilities in a specified runtime context.

Neither decision implies the other.

## Independent verification

The same provider that implemented a candidate may contribute useful evaluation, but its own declaration of success is insufficient.

Where practical, verification should include deterministic checks and independent inspection.

For higher-risk specialists, include adversarial cases such as:

- prompt injection;
- authority escalation requests;
- workspace escape;
- secret/credential access attempts;
- false capability claims;
- poisoned context;
- unavailable-tool behavior;
- provider fallback behavior;
- retry-budget exhaustion;
- attempts to modify policy or activation state.

## Authority monotonicity

A forge step may reduce requested authority or keep it unchanged.

It must not silently broaden authority.

If implementation discovers a genuine need for a broader capability, the correct result is a revised blueprint or explicit governance review.

## No self-approval

A model or specialist may recommend its own activation. It cannot authorize it.

Generated tests may prove behavior. They cannot grant activation.

Generated configuration may request tools. It cannot grant tools.

## Reuse over duplication

A new specialist should reuse shared ToadAid substrate wherever possible:

- Mirror memory and provenance;
- ToadAid MCP tools;
- ToadAid Coder build pathways;
- evidence and receipt formats;
- shared provider adapters;
- governance and runtime capability state.

The forge should produce small specialists, not new monolithic agent platforms.

## Success criterion

The forge succeeds when Tobyworld can say:

> "We need this capability."

and the ecosystem can transform that need into a tested, inspectable, bounded candidate while preserving a hard separation between **building capability** and **granting authority**.
