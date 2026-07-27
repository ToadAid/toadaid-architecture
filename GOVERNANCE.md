# ToadAid Governance Doctrine

## Foundational law

> **Capability may be created. Authority may not be self-created.**

This is the central invariant of the ToadAid ecosystem.

## Required distinctions

The following concepts must remain distinct:

```text
creation        ≠ activation
activation      ≠ authorization
capability      ≠ authority
request         ≠ authority
proposal        ≠ mutation
provider stop   ≠ ToadAid acceptance
acceptance      ≠ task completion
evidence        ≠ authority
model claim     ≠ runtime truth
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

## Failure semantics

Failure must not silently widen authority.

Valid outcomes include:

- `blocked`;
- `refused`;
- `needs_revision`;
- `insufficient_evidence`;
- `tool_unavailable`;
- `provider_failed`;
- `authority_denied`;
- `verification_failed`.

Invalid recovery includes silently:

- widening filesystem scope;
- enabling network access;
- adding retries beyond budget;
- switching providers when fallback is forbidden;
- acquiring credentials;
- enabling shell access;
- bypassing approval;
- treating provider completion as acceptance.

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

## Evidence doctrine

Runtime-observed state, deterministic tests, source inspection, structured tool results, provenance records, and independent verification are stronger evidence than provider self-report.

A model saying "done" is not proof that the intended work is complete.

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

requires explicit architectural review rather than routine implementation.
