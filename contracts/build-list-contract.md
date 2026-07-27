# BUILD_LIST Contract

## Purpose

`BUILD_LIST.md` is the bridge between architectural intent and bounded implementation.

It is not merely a checklist and it is not a license for a coding provider to improvise beyond scope.

The canonical architecture lives here in `ToadAid/toadaid-architecture`. Active build lists normally live in the implementation repository they govern.

## Required properties of a bounded build item

A meaningful build item should identify:

```text
ID
Goal
Architectural basis
Dependencies
Base / starting state
Exact or bounded scope
Allowed surfaces
Forbidden surfaces
Authority ceiling
Required implementation
Required tests
Required evidence
Failure conditions
Acceptance conditions
Activation inclusion/exclusion
```

Not every low-risk item requires a verbose rendering of every field, but the semantics must remain recoverable.

## Example

```text
P3 — Read-Only Deployment Inspector

Goal:
  Add deterministic deployment inspection.

Architectural basis:
  governed-ecosystem-architecture
  capability-authority-boundary

Authority ceiling:
  READ_ONLY

Allowed:
  deployment metadata reads
  approved repository reads

Forbidden:
  deployment mutation
  credential access
  arbitrary external execution

Required proof:
  deterministic unit tests
  confinement tests
  false-capability adversarial test

Completion:
  implementation + tests + evidence

Activation:
  NOT_INCLUDED
```

## Provider behavior

A coding provider may propose an architectural revision when the cut is impossible or unsound.

It must not silently:

- widen file scope;
- widen tool scope;
- widen authority;
- add provider fallback;
- add retries beyond budget;
- reinterpret denied capability as implementation freedom;
- treat passing tests as activation.

## Completion

A BUILD_LIST item is complete only when its declared acceptance contract is satisfied.

Provider end-of-turn, a plausible explanation, or the existence of source changes is not sufficient unless the contract explicitly says so.

## Revision

If the work must change materially, revise the intended work deliberately. Preserve history rather than mutating the meaning of an already-proven cut after the fact.
