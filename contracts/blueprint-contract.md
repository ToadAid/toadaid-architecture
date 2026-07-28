# Blueprint Contract

A ToadAid blueprint is a durable statement of intended capability. It should be understandable by humans and future agents without requiring the authoring conversation.

## Required fields

Every substantial component or specialist blueprint should define:

### Identity

- name;
- purpose;
- why the capability belongs in the ecosystem.

### Architectural basis

- canonical doctrine it depends on;
- existing substrate it reuses;
- neighboring components it interacts with.

### Inputs

- accepted input classes;
- provenance expectations;
- trust boundaries;
- untrusted content handling.

### Channel map

For inputs with different trust semantics, define:

- the structural channel each input uses;
- who may write each channel;
- which components may read it;
- which semantic classes each trusted channel is intended to establish;
- provider-, harness-, host-, or transport-owned configuration that can precede or conflict with it;
- precedence rules and how authoritative delivery is verified;
- permitted transformations between channels;
- forbidden channel crossings;
- how production wiring preserves the separation.

A provenance label inside one undifferentiated prompt is not sufficient channel separation.

A separate channel is not automatically authoritative. If the receiving provider or harness has conflicting controlling configuration that ToadAid cannot override or reconcile, the blueprint must state that limitation and fail closed for the affected semantic class rather than claiming successful trusted framing.

### Outputs

- output classes;
- whether outputs are advisory or state-changing;
- provenance/receipt requirements.

### Requested capabilities

List capabilities required to fulfill the purpose.

### Explicit denials

List consequential capabilities that are intentionally out of scope.

Silence should not be treated as permission.

### Memory model

- read rules;
- write rules;
- revision rules;
- contradiction behavior;
- provenance requirements;
- trust epochs or quarantine behavior where historical context may be contaminated;
- transformations between conversation, retrieved evidence, and canonical memory.

### Threat model

At minimum consider:

- prompt injection;
- authority escalation;
- workspace escape;
- credential exposure;
- false capability claims;
- poisoned context;
- trusted-channel collapse;
- non-authoritative trusted-channel delivery;
- stale or inapplicable proof;
- provider failure.

### Failure semantics

Define safe outcomes for missing evidence, denied authority, unavailable tools, provider failure, verification failure, proof invalidation, activation denial, and trusted-channel incompatibility.

### Evaluation contract

Define what must be proven before the candidate can be called verified.

The evaluation contract should distinguish:

```text
typed / structural verification
production wiring verification
live or adversarial verification
```

None should be presented as a substitute for another.

Where trusted configuration is required, verification must test both structural separation and authoritative delivery. Presence, provenance, and digest separation alone are not sufficient evidence that the receiving surface actually honors the channel for the intended semantic class.

### Verification subject

Identify the relevant subject that verification binds, such as:

- source identity;
- executable/version;
- invocation and confinement policy;
- trusted-channel policy;
- provider/harness configuration assumptions and precedence;
- environment and working-directory policy;
- runtime adapter / production path;
- schema version;
- capability and authority surface;
- evaluation-contract version.

Define which changes invalidate applicability and require replacement proof.

### Production path

Identify the exact runtime path that carries authority-relevant behavior.

For example:

```text
operator input
→ runtime validation
→ context / capability adapter
→ child process or tool router
→ normalized result
→ receipt
```

State how verification exercises that production-equivalent path rather than a safer parallel ceremony or test-only implementation.

For provider-facing configuration, include any upstream provider or harness system context that can constrain, override, or contradict ToadAid-controlled channels. A blueprint must not model a provider surface as a blank slate when the production harness is not one.

### Independent verification

If activation would grant consequential effective capability, define an independent verification path.

If independent verification is unavailable, activation must remain denied.

### Activation statement

State one of:

```text
activation: NOT_INCLUDED
activation: SEPARATE_DECISION_REQUIRED
activation: <explicit bounded activation scope>
```

Never leave activation implicit.

## Blueprint quality test

A future agent unfamiliar with the authoring conversation should be able to answer:

1. What is being built?
2. Why does it exist?
3. What may it read or affect?
4. What must it never do?
5. Which trust classes enter through which structural channels?
6. Which trusted channels are actually authoritative for which semantic classes, and what upstream configuration can conflict with them?
7. Which exact production path carries consequential behavior?
8. How will failure behave?
9. How will success be proven at the typed, wiring, and live layers?
10. What exact subject does the proof bind, and what invalidates it?
11. Does this blueprint authorize activation?

If those answers are unclear, the blueprint is incomplete.