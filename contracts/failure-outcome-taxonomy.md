# Failure Outcome Taxonomy

## Purpose

ToadAid components need one shared vocabulary for truthful failure, refusal, invalidation, incompatibility, and operator-controlled stopping states.

This contract is the canonical cross-ecosystem source for those outcome names. Higher-level documents may summarize the taxonomy, but they should not create overlapping synonyms for the same state without deliberate architectural review.

## Core law

> **Failure must remain truthful, bounded, and non-escalating.**

A failure outcome describes what happened or what is currently required. It does not grant authority, increase scope, add retries, or authorize fallback.

## Canonical outcomes

### Work and evidence

- `blocked` — work cannot proceed under the current declared bounds or prerequisites.
- `refused` — the requested operation was explicitly refused by policy, runtime, provider, or operator.
- `needs_revision` — the intended work or blueprint must change before another bounded attempt is valid.
- `insufficient_evidence` — available evidence cannot support the consequential claim or transition.
- `tool_unavailable` — a required governed capability is unavailable in the current runtime.
- `provider_failed` — the selected provider failed to produce the required provider-level result.
- `provider_incompatible` — the selected provider or harness cannot satisfy a required structural or semantic runtime contract.
- `operator_cancelled` — the operator deliberately stopped the bounded work.

### Verification and proof

- `verification_failed` — the tested subject failed the declared verification contract.
- `verification_invalidated` — an earlier verification may remain historically true but no longer applies to the current subject.
- `replacement_required` — a changed or invalidated subject requires a new governed verification before the dependent transition can proceed.
- `proof_inapplicable` — a proof exists but does not bind the subject or production path currently under consideration.
- `proof_expired` — a proof is outside a declared freshness or validity interval and may not govern the current transition.

### Trusted-channel and framing

- `unsupported_trusted_framing` — a structurally separate trusted channel exists, but the receiving provider, harness, host, or transport does not make it authoritative for the semantic class it is meant to establish.
- `unknown_channel_precedence` — the system cannot establish which controlling configuration wins for a relevant semantic class.

### Authority and activation

- `authority_denied` — the requested consequential capability is not authorized in the current runtime context.
- `activation_denied` — the candidate may not cross the activation boundary under the current evidence, policy, or authorization state.
- `paused` — an active or candidate runtime is intentionally prevented from continuing consequential operation until a governed condition changes.
- `degraded` — the runtime remains available only with a reduced or explicitly limited capability projection.
- `revoked` — previously effective authority or activation has been withdrawn.
- `retired` — the component or specialist is intentionally removed from active use.

## Distinctions

The following distinctions are mandatory:

```text
verification_failed      != verification_invalidated
verification_invalidated != replacement_required
provider_failed          != provider_incompatible
refused                  != authority_denied
blocked                  != activation_denied
degraded                 != revoked
historical proof         != current applicability
```

`unsupported_trusted_framing` is not a provider failure merely because it is discovered during provider use. It means the production surface cannot establish the intended trusted semantic framing under the verified precedence model.

## Recovery rules

A failure outcome may lead to another bounded state only through an explicitly valid transition.

Examples:

```text
verification_invalidated
→ replacement_required
→ new bounded verification
```

```text
provider_incompatible
→ provider remains unusable for that contract
→ architecture or provider-surface decision required
```

```text
unsupported_trusted_framing
→ do not claim trusted framing
→ use runtime-owned presentation or a compatible authoritative channel
```

Invalid recovery includes silently:

- widening filesystem, network, repository, wallet, publishing, or deployment scope;
- adding retries beyond the approved budget;
- switching providers when fallback is forbidden;
- translating an unknown or inapplicable proof into success;
- treating a provider self-description as runtime capability truth;
- treating a present but non-authoritative channel as trusted framing;
- converting historical success into current applicability without a performed binding comparison.

## Local extensions

An implementation repository may define narrower local subtypes where useful, but it should map them to this canonical taxonomy for cross-ecosystem reporting.

A local name must not silently change the meaning of a canonical outcome.

## Relationship to state machines

These outcome names do not require every repository to implement one identical state machine.

Blueprints should use the subset relevant to their lifecycle while preserving the canonical meanings. Authority-increasing transitions still require the governance rules defined elsewhere.

## Governing sentence

> **Safe systems need a common language for stopping, not only a common language for succeeding.**
