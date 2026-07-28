# Evidence and Activation Contract

## Purpose

ToadAid separates evidence of behavior from authority to activate behavior.

## Evidence classes

Useful evidence may include:

- deterministic test output;
- typecheck/build/lint output;
- runtime-observed capability state;
- source inspection;
- structured MCP/tool results;
- provenance records;
- sanitized receipts;
- production wiring verification;
- independent provider review;
- adversarial evaluation results;
- Git/GitHub state.

Model self-report may be useful context but should not be the only basis for consequential claims that can be observed independently.

## Derived evidence

Security-relevant receipt fields should be derived from the observation, classifier, comparison, or enforcement mechanism they describe.

A typed literal such as `observed` or `zero` is not itself evidence. A cached or rendered projection is not automatically evidence of current canonical state.

When a fact is unknown or not observable, the receipt must preserve that uncertainty rather than serialize an optimistic zero.

A proof-binding claim must record that an expected subject and actual subject were compared. A proof identifier copied into a receipt is not a performed binding.

The canonical mechanism is defined in [`derived-evidence-contract.md`](derived-evidence-contract.md).

## Completion evidence

Completion evidence answers questions such as:

- Was the intended source change made?
- Did the declared tests run?
- Did they pass?
- Did protected surfaces remain unchanged?
- Did the production-equivalent wiring use the declared boundary?
- Did the runtime remain within the declared authority ceiling?
- Was the applicable verification layer bound to the subject currently running?

Completion evidence does **not** answer:

- Should this capability be activated?
- Should this specialist receive broader authority?
- Should a wallet action be signed?
- Should content be published?

## Proof layers

Where consequential behavior crosses a real runtime boundary, verification should distinguish:

```text
typed / structural proof
wiring proof
live / adversarial proof
```

Typed proof constrains source and schemas.

Wiring proof establishes what the production adapter actually passes through arguments, environment, context, transport, tool routing, or signer boundaries.

Live proof establishes what the real external process or effect did under the bounded proof conditions.

None may impersonate another.

For lifecycle purposes, these layers may establish `source_verified`, `wiring_verified`, and `live_verified` respectively where the evaluation contract requires them.

The canonical proof lifecycle is defined in [`verification-applicability-contract.md`](verification-applicability-contract.md).

## Verification applicability

A verification applies only to the subject and proof layer it actually bound.

If a bound subject changes, preserve the historical result, mark current applicability `verification_invalidated`, and require the appropriate replacement proof.

`verification_invalidated` is not `verification_failed`.

A source proof cannot satisfy a wiring requirement. A wiring proof cannot satisfy a live requirement.

See [`verification-applicability-contract.md`](verification-applicability-contract.md).

## Activation

Activation is a separate state transition.

Conceptually:

```text
candidate
  ↓
required applicable verification layers
  ↓
verified candidate
  ║
  ║ separate governance boundary
  ║
  ↓
activated with explicit effective capabilities
```

At an authority-affecting activation boundary, verification must be current, applicable to the production subject, and independently inspected.

If applicable independent verification is unavailable:

```text
activation_denied
```

## Provider completion

A provider terminal event or `end_turn` is evidence about provider session state. It is not automatically evidence of:

- ToadAid acceptance;
- ToadAid task completion;
- successful verification;
- conversational answer completeness;
- authority grant;
- activation.

A successful OS process and a provider-reported success value may still produce an incomplete or failed ToadAid turn.

## Failure

Use the canonical outcome meanings in [`failure-outcome-taxonomy.md`](failure-outcome-taxonomy.md).

If required evidence is unavailable, stale, invalidated, inapplicable, or based on unsupported trusted framing, the correct result is the corresponding truthful fail-closed outcome such as `insufficient_evidence`, `verification_invalidated`, `proof_inapplicable`, `replacement_required`, or `unsupported_trusted_framing`—not optimistic completion.

## Receipts

Receipts should distinguish what was observed, what was structurally enforced, what was requested, what was inferred, what was historical, and what was not observable whenever those distinctions matter to authority or safety.

A receipt should also identify the subject, proof layer, and proof applicability relevant to consequential claims.

Historical receipts must not be silently rewritten when later evidence exposes an unsupported claim. Preserve the original receipt and append a corrective or superseding record.
