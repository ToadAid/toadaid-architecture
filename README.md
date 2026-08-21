# ToadAid Architecture

**Canonical architecture, governance, blueprints, and system doctrine for the ToadAid ecosystem.**

This repository exists so that Mirror, ToadAid Coder, ToadAid MCP, coding providers, specialists, future agents, and human contributors can share one durable statement of system intent.

ToadAid is not being built as a collection of unrelated autonomous agents. It is being built as a **governed ecosystem capable of understanding needs, designing capabilities, constructing them, proving them, and incorporating them without allowing intelligence to manufacture its own authority.**

## The architectural compass

The ecosystem is organized around four questions:

- **Mirror — WHY and WHAT:** understand context, preserve continuity, identify needs, draft architecture, blueprints, and bounded intended work.
- **ToadAid Coder — HOW TO FORGE:** turn accepted intended work into bounded implementation through governed coding harnesses such as Codex App Server and Grok ACP.
- **ToadAid MCP — WITH WHICH TOOLS:** expose shared, governed capabilities so coding agents can finish authorized work without owning the machine.
- **Governance — MAY:** determine whether consequential capabilities or mutations are permitted. No reasoning model owns this decision.

The core law is:

> **Build capability. Never manufacture authority.**

The operating sequence is:

> **Mirror imagines. Mirror blueprints. BUILD_LIST binds intent. ToadAid Coder forges. Codex and Grok reason. ToadAid MCP equips. Runtime executes. Evidence proves. Governance decides. Humans authorize. The ecosystem grows.**

## Mechanical governance

Doctrine alone is not enough. Cross-ecosystem laws must be expressed through mechanisms that make false assurance difficult to author and easy to detect.

The architecture therefore defines canonical mechanical contracts for:

- **Derived evidence:** security-relevant claims must be derived from the observation or enforcement mechanism they describe.
- **Verification applicability:** proof binds a subject and proof layer; historical proof may remain true while current applicability is invalidated.
- **Trusted-channel separation:** information with different trust semantics must travel through different structural channels, and trusted framing must be authoritative for the semantic class it claims to establish.
- **Failure outcomes:** failure, invalidation, incompatibility, refusal, and stop states use one shared cross-ecosystem vocabulary.
- **Scope sovereignty:** principal and personal/shared/project/public scope vocabulary, membership, audience, and cross-scope release remain governed architectural boundaries.
- **Agent identity and specialist admission:** agent identity evidence, principal/scope bindings, and specialist eligibility remain distinct from authority.
- **Agent messaging and delivery:** sender/recipient relationships, source/destination scopes, provenance, and delivery remain distinct from consequence authorization.
- **Attestation and evidence exchange:** scoped claims, provenance, verification, disclosure, validity, and exchange remain evidence rather than authority.

The combined operating law is:

```text
Doctrine states the law.
Mechanism prevents the lie.
Wiring proves the mechanism is connected.
Live evidence proves the subject behaved.
Invalidation prevents an old proof from governing a changed system.
```

## Mandatory read order for agents

Before planning ecosystem-level work, read:

1. [`AGENTS.md`](AGENTS.md)
2. [`ECOSYSTEM.md`](ECOSYSTEM.md)
3. [`GOVERNANCE.md`](GOVERNANCE.md)
4. [`blueprints/governed-ecosystem-architecture.md`](blueprints/governed-ecosystem-architecture.md)
5. the blueprint and contracts relevant to the component being changed
6. the implementation repository's local instructions and `BUILD_LIST.md`

If implementation and canonical architecture conflict, **surface the conflict instead of silently changing architectural intent**.

## Canonical hierarchy

When documents disagree, do not guess. Surface the conflict. The intended hierarchy is:

```text
human-approved architecture change
        ↓
GOVERNANCE.md
        ↓
governed-ecosystem-architecture.md
        ↓
component blueprints
        ↓
shared contracts
        ↓
repository-local architecture / BUILD_LIST
        ↓
implementation
```

Existing code is evidence of what exists. It is not automatically evidence of what the architecture intends.

Within that hierarchy, each detailed mechanical contract is the canonical source for its own vocabulary and mechanism. Higher-level documents may summarize those laws, but should link rather than independently create a competing taxonomy or lifecycle.

## Canonical state and projections

A repository page, raw-content endpoint, generated index, cache, mirror, rendered receipt, or summary is a projection of state.

For consequential current-state claims, bind the relevant canonical repository or source, branch/ref, commit or digest where available, and a freshness basis. If projections disagree, resolve the canonical source before reporting a confident finding.

> **A projection of canonical state is not canonical state itself.**

## Repository structure

```text
toadaid-architecture/
├── README.md
├── AGENTS.md
├── ECOSYSTEM.md
├── GOVERNANCE.md
├── ROADMAP.md
├── LICENSE
├── blueprints/
│   ├── governed-ecosystem-architecture.md
│   └── governed-agent-forge.md
├── contracts/
│   ├── blueprint-contract.md
│   ├── build-list-contract.md
│   ├── capability-authority-boundary.md
│   ├── derived-evidence-contract.md
│   ├── evidence-activation-contract.md
│   ├── failure-outcome-taxonomy.md
│   ├── scope-sovereignty-contract.md
│   ├── agent-identity-and-specialist-admission-contract.md
│   ├── agent-to-agent-messaging-and-delivery-contract.md
│   ├── attestation-and-evidence-exchange-contract.md
│   ├── trusted-channel-separation-contract.md
│   └── verification-applicability-contract.md
├── maps/
│   └── repository-map.md
└── adr/
    └── README.md
```

Implementation repositories remain responsible for their own active execution state and `BUILD_LIST.md`. This repository defines the cross-ecosystem laws and contracts those build lists must preserve.

## What belongs here

- cross-repository architecture;
- governance doctrine;
- capability and authority contracts;
- blueprint format and Agent Forge doctrine;
- shared BUILD_LIST semantics;
- ecosystem maps;
- architecture decision records;
- long-term direction that must survive provider and implementation changes.

## What does not belong here

- API keys, tokens, wallet keys, credentials, or secrets;
- operator-specific private deployment data;
- undisclosed vulnerability details;
- routine implementation state belonging to an individual repository;
- provider-specific claims presented as ecosystem truth.

## License

Unless otherwise noted, documentation in this repository is licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**. See [`LICENSE`](LICENSE).

---

**Stand tall. Stand fast. Build with proof. Grow without surrendering sovereignty.**
