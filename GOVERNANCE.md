# ToadAid Governance Doctrine

## Foundational law

> **Capability may be created. Authority may not be self-created.**

This is the central invariant of the ToadAid ecosystem.

## Required distinctions

The following concepts must remain distinct:

```text
creation                 ≠ activation
activation               ≠ authorization
capability               ≠ authority
request                  ≠ authority
proposal                 ≠ mutation
provider stop            ≠ ToadAid acceptance
acceptance               ≠ task completion
evidence                 ≠ authority
model claim              ≠ runtime truth
typed assertion          ≠ evidence
proof valid then         ≠ proof applicable now
provenance label         ≠ structural trusted channel
present trusted channel  ≠ authoritative trusted channel
process success          ≠ provider success
provider success         ≠ ToadAid workflow success
```

A system component may propose, implement, test, or prove a capability. None of those actions grants authority to use it.

## Effective capability

Conceptually:

```text
requested capability
        ∩
runtime availability
        ∩
policy
        ∩
operator authorization where required
        ↓
effective capability
```

If any required term is absent, the capability is not effectively authorized.

## Authority must remain external

Generated code must not be able to grant itself authority.

A generated statement such as:

```text
enableShell = true
walletSigningAllowed = true
mayPushToGitHub = true
```

has no authority merely because it exists in source.

Effective permissions must be established by trusted runtime or governance layers outside the code requesting those permissions.

## Mechanical governance

Doctrine should be implemented through mechanisms that make false assurance difficult to author.

The canonical mechanical contracts are:

- [`contracts/derived-evidence-contract.md`](contracts/derived-evidence-contract.md) — consequential evidence claims derive from canonical observations or enforcement mechanisms rather than authored answers;
- [`contracts/verification-applicability-contract.md`](contracts/verification-applicability-contract.md) — verification binds a defined subject and loses current applicability when that subject changes;
- [`contracts/trusted-channel-separation-contract.md`](contracts/trusted-channel-separation-contract.md) — different trust semantics require structurally distinct channels, and trusted framing must be authoritative for the semantic class it claims to establish;
- [`contracts/failure-outcome-taxonomy.md`](contracts/failure-outcome-taxonomy.md) — cross-ecosystem failure, invalidation, incompatibility, and stop-state names have one canonical meaning.

Three complementary proof layers remain distinct:

```text
typed / structural proof
production wiring proof
live / adversarial proof
```

Typed law constrains representable values. Wiring proof checks the production adapter and runtime path. Live proof checks the external process or real effect. None may impersonate another.

## Normative ownership

`GOVERNANCE.md` owns ecosystem-level doctrine.

Shared contracts own the detailed mechanical semantics within that doctrine. Blueprints, READMEs, maps, reports, and implementation repositories may summarize those laws, but should link to the canonical contract rather than independently redefine a competing taxonomy or lifecycle.

If a lower-level contract conflicts with this governance doctrine, surface the conflict for deliberate architectural review. Do not silently choose whichever wording is more convenient.

## Failure semantics

Failure must not silently widen authority.

The canonical cross-ecosystem outcome vocabulary is defined in [`contracts/failure-outcome-taxonomy.md`](contracts/failure-outcome-taxonomy.md).

Examples include:

```text
blocked
refused
needs_revision
insufficient_evidence
tool_unavailable
provider_failed
provider_incompatible
unsupported_trusted_framing
unknown_channel_precedence
authority_denied
verification_failed
verification_invalidated
proof_inapplicable
proof_expired
replacement_required
activation_denied
operator_cancelled
paused
degraded
revoked
retired
```

Invalid recovery includes silently:

- widening filesystem scope;
- enabling network access;
- adding retries beyond budget;
- switching providers when fallback is forbidden;
- acquiring credentials;
- enabling shell access;
- bypassing approval;
- treating provider completion as acceptance;
- transferring proof status to a changed subject;
- moving trusted configuration into ordinary user input;
- treating a present but non-authoritative channel as successful trusted framing;
- rewriting historical failure as success.

A failed bounded run is preferable to a successful unauthorized one.

## Bounded work

Agent work should have explicit bounds appropriate to risk:

- turn limits;
- model-call limits;
- retry budgets;
- tool-call budgets;
- workspace boundaries;
- filesystem boundaries;
- time limits;
- cost limits;
- network boundaries;
- provider fallback policy.

Loops should have deterministic stopping conditions whenever practical.

## Human governance

Meaningful approval boundaries should be understandable to the operator. Avoid approval theater and low-value prompts.

Human sovereignty should be strongest where effects are consequential or difficult to reverse.

For authority-affecting activation, independent verification is required.

If independent verification is unavailable, activation must remain denied rather than treating implementer self-report as sufficient.

## Evidence doctrine

Runtime-observed state, deterministic tests, source inspection, structured tool results, provenance records, wiring verification, adversarial evaluation, and independent verification are stronger evidence than provider self-report.

A model saying "done" is not proof that the intended work is complete.

A receipt that conforms to a schema is not necessarily truthful. Consequential claims should identify how they were derived and what subject they apply to.

A cached, rendered, mirrored, raw, indexed, or otherwise projected view of canonical state proves what was retrieved from that projection. It does not by itself prove that the projection is current. Consequential claims about repository or governance state should bind an explicit source, ref or revision, and freshness basis where those distinctions matter.

## Provider neutrality

No provider is sovereign.

Codex, Grok, Claude, local models, and future providers may perform reasoning roles, but policy, authority, and system truth must remain anchored outside provider assertions.

## Governance review trigger

Any change that would:

- broaden an authority class;
- allow generated code to influence its own permissions;
- merge proposal and mutation;
- merge evidence and activation;
- remove an operator boundary;
- make provider claims authoritative;
- introduce automatic recursive activation;
- collapse distinct trust channels;
- treat a non-authoritative channel as authoritative trusted framing;
- transfer verification to a changed subject without replacement proof;
- remove independent verification from an authority-affecting activation;

requires explicit architectural review rather than routine implementation.
