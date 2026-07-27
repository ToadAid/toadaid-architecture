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

## Mandatory read order for agents

Before planning ecosystem-level work, read:

1. [`AGENTS.md`](AGENTS.md)
2. [`ECOSYSTEM.md`](ECOSYSTEM.md)
3. [`GOVERNANCE.md`](GOVERNANCE.md)
4. [`blueprints/governed-ecosystem-architecture.md`](blueprints/governed-ecosystem-architecture.md)
5. the blueprint and contract relevant to the component being changed
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
│   └── evidence-activation-contract.md
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
