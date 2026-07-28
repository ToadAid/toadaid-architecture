# Derived Evidence Contract

## Purpose

ToadAid receipts and status projections must report what the system can actually ground, not what an implementation author intended to be true.

This contract defines the mechanical relationship between an observation or enforcement mechanism and the evidence claim derived from it.

## Core law

> **A security-relevant evidence claim must be derived from the observation or enforcement mechanism it describes.**

A claim basis such as `observed`, `structurally_enforced`, or `source_verified` is not authoritative merely because a developer wrote that label into source.

## Required derivation path

The intended path is:

```text
observation or enforcement mechanism
        ↓
canonical classifier
        ↓
grounded claim constructor
        ↓
receipt / status projection
```

The following path is invalid:

```text
developer-authored value
+
developer-authored evidence basis
        ↓
receipt
```

A type-safe literal can still be false. Type correctness does not establish runtime truth.

## Evidence bases

Implementations may use a closed evidence-basis taxonomy appropriate to their runtime. Common classes include:

```text
observed
structurally_enforced
source_verified
provider_flag_requested
historical
inferred
not_observable
unknown
```

The value and its basis must be compatible.

Examples:

```text
attempt count = 1
basis = observed
```

```text
retry maximum = 0
basis = structurally_enforced
```

```text
web search disabled
basis = provider_flag_requested
```

```text
arbitrary external actions = unknown
basis = not_observable
```

Invalid examples include:

```text
tool calls = 0
basis = not_observable
```

```text
repository access = denied
basis = observed
```

when only source policy, rather than runtime behavior, was inspected.

## Single-source requirement

Where a canonical classifier or observation already exists, downstream receipts must consume that result.

They must not independently recreate the same conclusion from literals, comments, duplicate conditionals, or hand-maintained narrative.

Conceptually:

```text
provider transcript
        ↓
tool-attempt classifier
        ├── runtime rendering
        ├── receipt field
        └── proof report
```

All projections should derive from the same classifier result.

This rule also applies to shared architecture vocabularies. When a canonical contract owns a taxonomy or lifecycle, higher-level summaries should link to that contract instead of inventing a second independently maintained definition.

## Contradiction refusal

A grounded claim constructor should fail closed when:

- the value contradicts the observation;
- the basis cannot support the value;
- `unknown` or `not_observable` is serialized as a numeric zero;
- `not_authorized` is presented as though it were an observed runtime outcome;
- a proof binding is asserted without a performed comparison;
- a mutable proof status is copied from stale prose rather than canonical proof state.

## Proof bindings

A receipt claim that says it is bound to a proof must record enough information to establish that the comparison occurred.

At minimum:

```text
expected proof identity
actual subject identity
comparison performed
comparison result
```

A string such as:

```text
bound_to: cut-19-r6
```

is not itself evidence of a binding.

## Canonical state and projections

A rendered, cached, mirrored, indexed, raw, summarized, or API-projected view of canonical state is a projection.

A projection proves what was returned by that projection at the time and under the addressing information actually used. It does not automatically prove that the projection is current, complete, or bound to the canonical revision being discussed.

For consequential claims about repository, governance, proof, deployment, or authority state, evidence should bind the relevant subset of:

```text
canonical source or repository
branch / ref / object identity
commit, digest, or revision where available
retrieval time or freshness basis
projection mechanism
comparison against expected current state where required
```

The intended pattern is:

```text
canonical source identity
        ↓
explicit ref / revision
        ↓
direct current read or freshness check
        ↓
derived claim
```

The following is insufficient for a consequential current-state claim:

```text
cached or projected document
        ↓
assume current
        ↓
confident finding
```

When two projections disagree, do not choose the convenient one. Resolve the canonical source identity and freshness before asserting current truth.

## Projection rule

Reports, shutdown summaries, Telegram messages, dashboards, raw-content endpoints, generated indexes, and human-readable receipts are projections of canonical evidence or state.

A rendering defect should be repaired by re-rendering the preserved evidence where possible. It should not trigger another provider or external action merely to regenerate prose.

A stale projection should be refreshed or rebound to the intended canonical revision. It should not be treated as evidence that canonical state is missing or contradictory until the source/ref/freshness question is resolved.

## Historical correction

False or insufficient historical receipt claims must not be silently rewritten or deleted.

The correct repair is:

```text
historical receipt: preserved
unsupported claim: withdrawn or superseded
corrective record: appended
cryptographic identity: preserved
```

A historical receipt remains evidence of what the software recorded at issuance. It is not automatically evidence that every recorded claim was true.

## Required verification

Implementations of this contract should include tests that:

- deliberately contradict an observation and a proposed claim;
- prove the grounded constructor refuses the mismatch;
- prove unknown facts cannot become observed zeros;
- prove a proof-binding claim fails when no comparison occurred;
- prove separate renderers derive from the same canonical observation;
- prove stale narrative cannot override canonical proof state;
- prove a stale or mismatched projection cannot satisfy a current-state claim without a freshness or revision check;
- prove conflicting projections trigger canonical-source reconciliation rather than optimistic selection.

## Relationship to authority

Evidence does not grant authority.

Accurate evidence allows governance to decide from truthful state. It does not collapse evidence, approval, activation, or authorization into one step.

The governing sentence is:

> **Doctrine states what evidence should mean. Derivation prevents an implementation from authoring the answer. A projection of canonical state is not canonical state itself.**
