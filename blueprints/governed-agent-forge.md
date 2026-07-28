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
TYPED / STRUCTURAL VERIFICATION
  ↓
PRODUCTION WIRING VERIFICATION
  ↓
ADVERSARIAL / LIVE VERIFICATION
  ↓
CANDIDATE SPECIALIST
  ║
  ║ AUTHORITY WALL
  ║
  ↓
INDEPENDENT ACTIVATION VERIFICATION
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
source_verified
live_verified
activation_pending
active
degraded
paused
invalidated
replacement_required
revoked
retired
```

Transitions that increase effective authority require appropriate governance.

`invalidated` is distinct from `failed`. A prior proof may remain truthful for its earlier subject while no longer applying to the current one.

## Failure and invalidation paths

The forge must make safe non-happy paths visible.

Conceptually:

```text
candidate
  ├─ insufficient_evidence → blocked
  ├─ verification_failed → needs_revision / retired
  └─ live_verified
        ├─ subject_changed → invalidated → replacement_required
        ├─ activation_denied → paused / candidate
        └─ active
              ├─ degraded → paused
              ├─ authority_revoked → revoked
              └─ retired
```

Valid transitions also include operator cancellation, provider failure, tool unavailability, and refusal.

Failure must never silently widen authority, add retries, switch providers, broaden workspace scope, or transfer proof to a changed subject.

## Required artifacts

Before build:

- specialist identity and purpose;
- canonical blueprint;
- capability manifest;
- explicit denial manifest;
- threat model;
- memory/provenance model;
- trusted-channel map;
- evaluation contract;
- verification-subject definition;
- invalidation triggers;
- bounded BUILD_LIST.

During build:

- source changes;
- tests;
- deterministic verification output;
- production-wiring verification;
- provider-neutral evidence;
- authority-relevant receipts;
- proof-subject identities and applicability results.

Before activation:

- completed verification contract;
- adversarial confinement results where applicable;
- production-path binding;
- current proof applicability;
- independent verification;
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

A capability manifest must travel through trusted runtime configuration or another channel appropriate to its trust semantics. Delivering it as ordinary task text does not establish authority.

## Blueprint approval versus activation approval

These are separate decisions.

Blueprint approval means:

> The architecture is acceptable to build as a candidate.

Activation approval means:

> The verified candidate may receive specified effective capabilities in a specified runtime context.

Neither decision implies the other.

## Trusted-channel separation

The forge must preserve structural separation between:

```text
runtime configuration
operator / task input
conversation context
retrieved evidence
canonical memory
provider output
authority decisions
```

A provenance label in one undifferentiated prompt is not sufficient.

The blueprint must define who can write and read each channel, the transformations allowed between them, and how the production path preserves those distinctions.

## Verification layers

The forge distinguishes three complementary proof layers:

### Typed / structural verification

Proves properties such as:

- closed taxonomies;
- schema constraints;
- impossible invalid values where the typecheck gate is actually enforced;
- exact source structure;
- deterministic policy construction.

Typed law counts only when the production verification gate actually runs typechecking.

### Production wiring verification

Proves what the real adapter passes through:

- arguments;
- environment;
- PATH;
- working directory;
- trusted configuration channels;
- context packets;
- tool routing;
- retry and fallback controls;
- transport and receipt construction.

A safe ceremony beside an unsafe product path does not prove the product path.

### Adversarial / live verification

Proves what the external process or real effect did under the bounded proof conditions.

A live provider result, runtime observation, or external action receipt should not be treated as proof for an invocation or production path it did not exercise.

No proof layer may impersonate another.

## Derived evidence

Authority-relevant receipt fields must derive from canonical observations, classifiers, enforcement mechanisms, and performed comparisons.

The forge should prefer:

```text
observation
→ classifier
→ grounded claim constructor
→ receipt
```

over independently authored values and evidence-basis labels.

A schema-conformant receipt may still be false. The forge must test contradiction refusal and proof-binding comparisons.

## Verification applicability and invalidation

A verification binds a defined subject, which may include:

```text
source identity
executable/version
invocation policy
trusted-channel policy
environment policy
working-directory policy
runtime adapter / production path
schema version
capability manifest
authority surface
evaluation-contract version
```

When a bound subject changes:

```text
historical proof: preserved
current applicability: invalidated
replacement proof: required
```

The prior proof is not automatically wrong. It is not transferable to the changed subject.

Current proof status should be canonical data, not hand-maintained narrative.

## Independent verification

The same provider that implemented a candidate may contribute useful evaluation, but its own declaration of success is insufficient.

For authority-affecting activation, independent verification is required.

If independent verification is unavailable:

```text
activation denied
```

The blueprint author may define intended acceptance invariants, but should not be the sole reporter that the implementation satisfied them.

For higher-risk specialists, include adversarial cases such as:

- prompt injection;
- authority escalation requests;
- workspace escape;
- secret/credential access attempts;
- false capability claims;
- poisoned context;
- trusted-channel collapse;
- stale or inapplicable proof;
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

Generated receipts may report evidence. They cannot define the observations from which their own consequential claims are supposedly derived.

## Reuse over duplication

A new specialist should reuse shared ToadAid substrate wherever possible:

- Mirror memory and provenance;
- ToadAid MCP tools;
- ToadAid Coder build pathways;
- evidence and receipt formats;
- shared provider adapters;
- trusted-channel framework;
- confined process runner;
- proof registry and invalidation engine;
- derived-evidence constructors;
- hostile wiring fixtures;
- governance and runtime capability state;
- activation ceremony.

The forge should produce small specialists, not new monolithic agent platforms.

## Governance-cost amortization

The forge is viable only if governance cost per new specialist decreases as shared substrate matures.

NOMI-like failures should be paid for once, converted into reusable contracts and infrastructure, and inherited by future specialists.

A new specialist should primarily supply:

```text
identity
purpose
domain capability manifest
explicit denials
domain evidence adapters
domain acceptance tests
```

It should not rebuild confinement, channels, proof registries, receipt truth, or activation machinery from scratch.

Governance cost should be reviewed as an architectural metric. If every specialist requires another bespoke sequence of receipt and confinement repairs, the Forge has not yet achieved reusable substrate.

## Success criterion

The forge succeeds when Tobyworld can say:

> "We need this capability."

and the ecosystem can transform that need into a tested, inspectable, bounded candidate while preserving a hard separation between **building capability** and **granting authority**.

It succeeds sustainably when the next specialist inherits proven governance mechanisms instead of paying the full discovery cost again.
