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

### Derived evidence

Security-relevant evidence claims must derive from the observation or enforcement mechanism they describe.

The intended path is:

```text
observation / enforcement
        ↓
canonical classifier
        ↓
grounded claim
        ↓
receipt or status projection
```

A developer-authored value plus a developer-authored evidence basis is not proof merely because both satisfy a type.

### Verification applicability

A verification binds a defined subject.

If that subject changes, the earlier proof remains historical evidence but loses current applicability until an appropriate replacement proof succeeds.

```text
historical proof: preserved
current applicability: invalidated
replacement proof: required
```

### Trusted-channel separation

Information with different trust semantics must travel through different structural channels.

Trusted runtime configuration, operator input, conversation context, retrieved evidence, canonical memory, provider output, and authority decisions must not collapse into one undifferentiated text stream.

A provenance label is useful, but it does not by itself establish a trusted channel.

### Proof layers

The following layers are complementary:

```text
typed law
wiring proof
live proof
```

Typed law constrains representable values. Wiring proof checks the production adapter and runtime path. Live proof checks the external process or real effect.

None may impersonate another.

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
- `verification_failed`;
- `verification_invalidated`;
- `replacement_required`;
- `activation_denied`;
- `operator_cancelled`.

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
- transfer verification to a changed subject without replacement proof;
- remove independent verification from an authority-affecting activation;

requires explicit architectural review rather than routine implementation.
