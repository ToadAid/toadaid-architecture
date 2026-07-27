# ToadAid Repository Map

This map records architectural roles, not ownership of every implementation detail. Update it deliberately as repositories evolve.

## Canonical architecture

### `ToadAid/toadaid-architecture`

Role: cross-ecosystem constitution, architecture, governance, contracts, blueprints, and maps.

It should not become a live implementation monorepo.

## Core substrate

### `ToadAid/mirror-core`

Role: shared governed Mirror substrate, continuity, memory/provenance semantics, specialist foundations, and other reusable core contracts.

## User/operator surface

### `ToadAid/mirror-desktop`

Role: desktop experience through which humans understand and operate Mirror and its governed capabilities.

### `ToadAid/mirror-desktop-bridge`

Role: governed bridge between desktop/assistant surfaces and local repository/runtime capabilities, including MCP-facing capability exposure where appropriate.

## Construction forge

### `ToadAid/coder`

Role: ToadAid Coder — governed software-construction system.

Expected provider harnesses include Codex App Server and Grok ACP behind ToadAid-owned lifecycle, authority, evidence, and completion semantics.

## Adjacent governed agents

Other ToadAid agent repositories may implement specialized roles. They should reference this canonical architecture when their behavior participates in the shared ecosystem.

## Relationship

```text
                  toadaid-architecture
                        doctrine
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
     mirror-core        coder        desktop / bridge
          │                │                │
          └────────────┬───┴───────┬────────┘
                       ▼           ▼
                 shared runtime   MCP tools
                       │           │
                       └─────┬─────┘
                             ▼
                       specialists
```

## Non-drift rule

Implementation repositories may specialize this architecture but should not independently redefine ecosystem-wide laws.

When a local need implies an ecosystem-level architectural change, record that change here through deliberate review, then update dependent repositories.
