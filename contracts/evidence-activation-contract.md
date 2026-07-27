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
- independent provider review;
- adversarial evaluation results;
- Git/GitHub state.

Model self-report may be useful context but should not be the only basis for consequential claims that can be observed independently.

## Completion evidence

Completion evidence answers questions such as:

- Was the intended source change made?
- Did the declared tests run?
- Did they pass?
- Did protected surfaces remain unchanged?
- Did the runtime remain within the declared authority ceiling?

Completion evidence does **not** answer:

- Should this capability be activated?
- Should this specialist receive broader authority?
- Should a wallet action be signed?
- Should content be published?

## Activation

Activation is a separate state transition.

Conceptually:

```text
candidate
  ↓
verification
  ↓
verified candidate
  ║
  ║ separate governance boundary
  ║
  ↓
activated with explicit effective capabilities
```

## Provider completion

A provider terminal event or `end_turn` is evidence about provider session state. It is not automatically evidence of:

- ToadAid acceptance;
- ToadAid task completion;
- successful verification;
- authority grant;
- activation.

## Failure

If required evidence is unavailable, the correct status is `insufficient_evidence` or another truthful failure state, not optimistic completion.

## Receipts

Receipts should distinguish what was observed, what was structurally enforced, what was requested, what was inferred, and what was not observable whenever those distinctions matter to authority or safety.
