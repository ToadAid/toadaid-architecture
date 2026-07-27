# Instructions for ToadAid Agents

This repository is the canonical cross-ecosystem architecture source for ToadAid.

These instructions apply to coding agents, planning agents, reviewers, specialists, and future automated contributors operating on ToadAid architecture or implementation derived from it.

## Required orientation

Before proposing ecosystem-level work:

1. Read `README.md`.
2. Read `ECOSYSTEM.md`.
3. Read `GOVERNANCE.md`.
4. Read `blueprints/governed-ecosystem-architecture.md`.
5. Read every blueprint and contract directly relevant to the intended work.
6. Then read the target implementation repository's local instructions, current architecture, and `BUILD_LIST.md`.

Do not infer ecosystem intent solely from current code.

## Non-drift rules

1. **Do not optimize away governance boundaries.** Convenience is not justification for collapsing proposal, mutation, evidence, activation, or authority into one step.
2. **Capability is not authority.** Creating or proving a capability never grants permission to use it.
3. **Requests are not grants.** A provider permission request is evidence that a capability was requested, not evidence that it was authorized.
4. **Provider completion is not ToadAid completion.** A model ending its turn does not establish system acceptance or task completion.
5. **Evidence is not authority.** Passing tests proves behavior under tested conditions; it does not authorize activation.
6. **Generated source cannot grant runtime authority.** Permission must come from trusted policy/runtime controls outside the generated code.
7. **Do not silently widen scope.** If intended work cannot be completed under its declared authority ceiling or file/tool scope, stop and surface the conflict.
8. **Do not silently rewrite doctrine to match implementation.** If implementation conflicts with canonical architecture, report the conflict for deliberate architectural review.
9. **Prefer shared governed substrate over duplicated agent infrastructure.** New specialists should reuse Mirror, ToadAid Coder, ToadAid MCP, evidence, and governance layers where appropriate.
10. **Providers are replaceable reasoning engines.** Do not make provider-specific behavior the root of system truth.

## Planning rule

A valid implementation plan should identify:

- architectural basis;
- goal and non-goals;
- exact scope;
- dependencies;
- authority ceiling;
- allowed and forbidden capabilities;
- required tests and evaluations;
- evidence required for completion;
- whether activation is explicitly included or explicitly excluded.

If those cannot be determined, planning is incomplete.

## Mutation rule

Before a consequential mutation, preserve the distinction:

```text
intent → proposal → authorization → mutation → verification → evidence → acceptance
```

Do not collapse the chain merely because a provider can technically perform several steps at once.

## Conflict rule

When canonical architecture, a component blueprint, local repository instructions, or runtime policy appear to conflict:

- obey higher-priority safety and runtime controls;
- do not guess which architectural statement should be discarded;
- identify the conflicting statements;
- state what work is blocked;
- request deliberate reconciliation.

## Core memory

Remember this sentence:

> **Mirror determines what to propose. Coding intelligence determines how to implement. Governance determines what may occur.**

And this law:

> **Build capability. Never manufacture authority.**
