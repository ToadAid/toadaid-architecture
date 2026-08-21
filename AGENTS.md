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
7. **Evidence claims must be derived.** Do not author security-relevant values or evidence bases as convenient literals when a canonical observation, classifier, or enforcement mechanism exists.
8. **Proof applicability is not permanent.** Preserve historical proof, but invalidate its current applicability when the bound subject or production path changes.
9. **Different trust classes require different channels.** A provenance label inside one undifferentiated prompt is not structural trusted-channel separation.
10. **A separate trusted channel is not automatically authoritative.** Verify precedence and receiving-surface semantics for the claim the channel is meant to establish.
11. **Typed law, wiring proof, and live proof are distinct.** None may be presented as evidence for a layer it did not exercise.
12. **Use canonical outcome names.** Do not invent local synonyms for cross-ecosystem failure, invalidation, incompatibility, or stop states when the canonical taxonomy already covers them.
13. **A projection is not canonical current state.** Bind consequential current-state claims to an explicit source/ref/revision and freshness basis rather than trusting a cache, raw view, mirror, index, or rendered summary blindly.
14. **Do not silently widen scope.** If intended work cannot be completed under its declared authority ceiling or file/tool scope, stop and surface the conflict.
15. **Do not silently rewrite doctrine to match implementation.** If implementation conflicts with canonical architecture, report the conflict for deliberate architectural review.
16. **Prefer shared governed substrate over duplicated agent infrastructure.** New specialists should reuse Mirror, ToadAid Coder, ToadAid MCP, evidence, and governance layers where appropriate.
17. **Providers are replaceable reasoning engines.** Do not make provider-specific behavior the root of system truth.

## Canonical contract ownership

Detailed mechanical vocabularies and lifecycles should have one canonical contract owner.

Current canonical owners include:

```text
derived evidence / projection truth
  → contracts/derived-evidence-contract.md

proof layers / applicability / invalidation
  → contracts/verification-applicability-contract.md

trusted channels / authority / precedence
  → contracts/trusted-channel-separation-contract.md

failure / invalidation / incompatibility outcomes
  → contracts/failure-outcome-taxonomy.md

principal / personal/shared/project/public scope /
membership / audience / cross-scope release / scope sovereignty
  → contracts/scope-sovereignty-contract.md

agent identity / AgentId / principal-agent binding /
specialist admission / remote-agent admission / admission revocation
  → contracts/agent-identity-and-specialist-admission-contract.md

agent-to-agent messaging / MessageId / sender-recipient binding /
source/destination scope / delivery / message provenance / replay
  → contracts/agent-to-agent-messaging-and-delivery-contract.md

attestation / AttestationId / claim / issuer-subject binding /
evidence basis / verification / revocation / supersession /
attestation exchange
  → contracts/attestation-and-evidence-exchange-contract.md
```

Higher-level documents may summarize these rules. If summaries diverge, do not silently choose one; reconcile against `GOVERNANCE.md` and the canonical contract.

## Planning rule

A valid implementation plan should identify:

- architectural basis;
- goal and non-goals;
- exact scope;
- dependencies;
- authority ceiling;
- allowed and forbidden capabilities;
- input trust classes and structural channel map;
- channel authority and precedence assumptions where trusted framing matters;
- production paths carrying authority-relevant behavior;
- verification subject, required proof layers, and invalidation triggers;
- required typed, wiring, and live tests where relevant;
- evidence required for completion;
- whether activation is explicitly included or explicitly excluded.

If those cannot be determined, planning is incomplete.

## Current-state reading rule

When a consequential conclusion depends on current repository, governance, proof, deployment, or authority state:

```text
identify canonical source
→ bind branch/ref/revision
→ perform current read or freshness check
→ compare expected and actual state where required
→ then state the conclusion
```

If two projections disagree, report the inconsistency and resolve canonical state before making a confident finding.

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
