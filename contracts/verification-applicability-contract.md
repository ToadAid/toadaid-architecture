# Verification Applicability Contract

## Purpose

A verification proves a defined subject under defined conditions.

It does not remain automatically applicable after the subject, policy, executable, environment, schema, capability surface, or acceptance contract changes.

This contract preserves historical proof while preventing stale proof from governing a changed runtime.

## Core law

> **Proof valid then does not imply proof applicable now.**

A changed subject does not make the earlier proof dishonest. It makes the earlier proof inapplicable to the new subject.

## Verification subject

Every consequential verification should bind the relevant subset of:

```text
source identity
executable identity and version
invocation policy
trusted-channel policy
environment policy
working-directory policy
schema version
capability manifest
authority surface
acceptance-proof version
runtime adapter / production path
```

The bound subset must be sufficient to identify what was actually verified.

Dynamic turn input, conversation text, or other per-run material should be recorded separately from stable policy identity where appropriate.

## Conceptual lifecycle

```text
unverified
    ↓
source_verified
    ↓
live_verified
    ↓ subject changes
invalidated
    ↓
replacement_required
    ↓ replacement proof
live_verified
```

Other truthful states may include:

```text
verification_failed
insufficient_evidence
expired
revoked
not_applicable
```

## Invalidation triggers

A verification must be reconsidered when a bound subject changes, including changes to:

- source revision or protected implementation;
- executable version or build identity;
- fixed invocation arguments;
- confinement or tool policy;
- trusted configuration channels;
- environment allowlist or PATH policy;
- working-directory isolation;
- provider adapter or production wiring;
- receipt or evidence schema when the proof depends on it;
- capability manifest or denial manifest;
- effective authority surface;
- acceptance or adversarial evaluation contract.

The invalidation engine should compare canonical subject identities rather than rely on hand-maintained prose.

## Historical preservation

Invalidation must not delete or relabel the earlier proof.

The correct record is:

```text
historical proof: preserved
historical result: unchanged
current applicability: invalidated
replacement proof: required
```

`invalidated` is distinct from `failed`.

The earlier proof may remain completely true about the earlier subject.

## Proof registry

Consequential proof status should be represented as canonical data.

A proof registry should be able to answer:

```text
What subject was verified?
Which evidence established it?
When was it verified?
Is the proof applicable to the current subject?
If not, what changed?
What replacement proof is required?
```

Human-readable notes may explain status, but they must not be the source of current applicability truth.

## Binding comparison

A runtime claiming a proof binding must perform and record a comparison between:

```text
expected proof subject identity
actual current subject identity
```

Possible outcomes include:

```text
bound
not_bound
proof_missing
subject_changed
proof_invalidated
insufficient_evidence
```

A hardcoded proof identifier is not a performed binding.

## Activation boundary

A candidate must not cross an authority-affecting activation boundary using an invalidated, expired, missing, or inapplicable verification.

Conceptually:

```text
candidate
  ∩ applicable verification
  ∩ current capability projection
  ∩ explicit activation authorization
        ↓
activated bounded capability
```

If applicable verification is unavailable:

```text
activation denied
```

## Production-path applicability

A ceremony or test proves only the path and policy it actually exercises.

A safe standalone runner beside an unsafe product path does not prove the product path.

When authority-relevant behavior crosses adapters, child processes, transports, signers, networks, or tool routers, the verification subject should include the production-equivalent path.

## Replacement proof

A replacement proof is a new governed verification for the changed subject.

It is not an automatic retry and does not inherit authority from the earlier proof.

The replacement proof should define:

- the changed subject identity;
- the reason replacement is required;
- the exact new evidence budget;
- retry and fallback limits;
- acceptance and failure outcomes;
- how the new proof supersedes applicability without erasing history.

## Required verification

Implementations of this contract should test:

- unchanged subject remains bound;
- each bound subject change invalidates applicability;
- historical proof remains preserved;
- invalidated does not serialize as failed;
- stale narrative cannot restore applicability;
- a hardcoded proof ID cannot satisfy a binding comparison;
- production-path drift invalidates a ceremony-only proof;
- activation fails closed when proof is missing or inapplicable.

The governing sentence is:

> **Verification is a relationship between evidence and a subject, not a permanent badge attached to a component.**
