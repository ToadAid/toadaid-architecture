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
- provenance requirements.

### Threat model

At minimum consider:

- prompt injection;
- authority escalation;
- workspace escape;
- credential exposure;
- false capability claims;
- poisoned context;
- provider failure.

### Failure semantics

Define safe outcomes for missing evidence, denied authority, unavailable tools, provider failure, and verification failure.

### Evaluation contract

Define what must be proven before the candidate can be called verified.

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
5. How will failure behave?
6. How will success be proven?
7. Does this blueprint authorize activation?

If those answers are unclear, the blueprint is incomplete.
