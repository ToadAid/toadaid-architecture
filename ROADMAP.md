# ToadAid Architecture Roadmap

This is a **directional architecture roadmap**, not a live implementation-status ledger. Individual repositories own their current build state.

## Phase A — Canonical intent

Establish one public source of truth for:

- ecosystem architecture;
- governance laws;
- blueprint semantics;
- BUILD_LIST semantics;
- capability and authority boundaries;
- evidence and activation boundaries;
- architecture decision records.

## Phase B — Shared governed substrate

Mature Mirror Core and related shared substrate so specialists can reuse:

- governed memory;
- provenance;
- runtime capability state;
- shared policy concepts;
- specialist registration and lifecycle semantics.

## Phase C — Governed tool plane

Mature ToadAid MCP into a reusable capability plane for coding and specialist work.

Goals:

- semantic bounded tools where practical;
- explicit capability classes;
- runtime-observed authority state;
- receipts and evidence;
- no requirement for every specialist to reinvent filesystem, GitHub, shell, or approval infrastructure.

## Phase D — ToadAid Coder as forge

Complete the governed coding forge around provider-neutral contracts.

Key provider harnesses may include Codex App Server and Grok ACP, while keeping providers replaceable.

The forge should support:

- inspection;
- planning;
- proposal;
- authorization boundaries;
- bounded mutation;
- verification;
- evidence;
- completion classification.

## Phase E — Mirror architectural authoring

Enable Mirror to reliably draft:

- ecosystem-compatible blueprints;
- capability manifests;
- threat models;
- evaluation contracts;
- bounded BUILD_LIST cuts.

This phase should not grant Mirror automatic implementation or activation authority.

## Phase F — Governed Agent Forge

Connect the architecture loop:

```text
Mirror blueprint
      ↓
accepted BUILD_LIST
      ↓
ToadAid Coder
      ↓
Codex / Grok
      ↓
ToadAid MCP
      ↓
candidate specialist
      ↓
verification + adversarial proof
      ↓
separate activation decision
```

The product of the forge is inert until activation is explicitly authorized.

## Phase G — Ecosystem evolution

Allow Tobyworld to grow a family of small, bounded specialists sharing the same governed substrate rather than becoming a collection of disconnected autonomous frameworks.

The long-term measure of success is not the number of agents created. It is the ecosystem's ability to add useful capability **without losing provenance, observability, maintainability, or human sovereignty**.

## Future governed runtime implementation waves

The [`Governed Runtime Responsibility and Component Allocation`](blueprints/governed-runtime-component-allocation.md) defines an architecture-level sequence for later bounded implementation cuts. It does not authorize or claim completion of any wave:

1. project canonical governance into a minimal Mirror Core evaluation kernel;
2. make Mirror Desktop Bridge consume governance at the local consequence edge;
3. project scope sovereignty into Living Agent continuity and retrieval;
4. admit ToadAid Coder as a bounded repository specialist;
5. admit ToadAid Trader first as an analysis and trade-intent specialist;
6. project ToadAid Zora Agent through isolated high-consequence boundaries;
7. carry identity, scope, request, and evidence semantics through ToadAid MCP without making it the authority owner;
8. compose community and project runtime under explicit scope, admission, Release, and Grant law;
9. consider external interoperability only after local sovereignty survives implementation.

Every wave requires its own implementation scope, verification, and separate activation decision.
