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
wiring_verified
    ↓
live_verified
    ↓ subject changes
verification_invalidated
    ↓
replacement_required
    ↓ replacement proof
source_verified / wiring_verified / live_verified as required
```

`wiring_verified` means the production-equivalent adapter and boundary were verified for the bound subject. It does not imply that an external provider, network, signer, or real-world effect behaved successfully.

Not every proof requires every layer. The evaluation contract must state which layer is necessary for the claim being made. A source-only doctrine change, for example, may not require a live provider proof. A consequential provider or signer boundary normally requires production wiring verification before a live proof can establish the full claim.

Other truthful states may include:

```text
verification_failed
insufficient_evidence
proof_expired
revoked
not_applicable
```

Cross-ecosystem failure names use the canonical meanings in [`failure-outcome-taxonomy.md`](failure-outcome-taxonomy.md).

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

A change may invalidate only the proof layers whose subject includes that change. For example, a documentation-only edit need not invalidate a runtime confinement proof unless the bound subject or evaluation contract says it does. Conversely, a production adapter change must not inherit a prior `wiring_verified` or `live_verified` result merely because source types still compile.

## Historical preservation

Invalidation must not delete or relabel the earlier proof.

The correct record is:

```text
historical proof: preserved
historical result: unchanged
current applicability: verification_invalidated
replacement proof: required
```

`verification_invalidated` is distinct from `verification_failed`.

The earlier proof may remain completely true about the earlier subject.

## Proof registry

Consequential proof status should be represented as canonical data.

A proof registry should be able to answer:

```text
What subject was verified?
Which proof layer was established?
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
required proof layer
available applicable proof layer
```

Possible outcomes include:

```text
bound
not_bound
proof_missing
subject_changed
verification_invalidated
proof_inapplicable
proof_expired
insufficient_evidence
```

A hardcoded proof identifier is not a performed binding.

## Activation boundary

A candidate must not cross an authority-affecting activation boundary using an invalidated, expired, missing, or inapplicable verification.

Conceptually:

```text
candidate
  ∩ applicable required verification layers
  ∩ current capability projection
  ∩ explicit activation authorization
        ↓
activated bounded capability
```

If applicable verification is unavailable:

```text
activation_denied
```

## Production-path applicability

A ceremony or test proves only the path and policy it actually exercises.

A safe standalone runner beside an unsafe product path does not prove the product path.

When authority-relevant behavior crosses adapters, child processes, transports, signers, networks, or tool routers, the verification subject should include the production-equivalent path.

`source_verified` must not be presented as `wiring_verified`, and `wiring_verified` must not be presented as `live_verified`.

## Replacement proof

A replacement proof is a new governed verification for the changed subject.

It is not an automatic retry and does not inherit authority from the earlier proof.

The replacement proof should define:

- the changed subject identity;
- the reason replacement is required;
- the proof layer or layers that must be re-established;
- the exact new evidence budget;
- retry and fallback limits;
- acceptance and failure outcomes;
- how the new proof supersedes applicability without erasing history.

## Required verification

Implementations of this contract should test:

- unchanged subject remains bound;
- each bound subject change invalidates the applicable affected layer;
- source verification cannot satisfy a wiring requirement;
- wiring verification cannot satisfy a live requirement;
- historical proof remains preserved;
- invalidated does not serialize as failed;
- stale narrative cannot restore applicability;
- a hardcoded proof ID cannot satisfy a binding comparison;
- production-path drift invalidates a ceremony-only or prior wiring proof;
- activation fails closed when the required proof layer is missing or inapplicable.

The governing sentence is:

> **Verification is a relationship between evidence, a proof layer, and a subject—not a permanent badge attached to a component.**
