# Architecture Decision Records

Use this directory for decisions that materially change cross-ecosystem architecture or governance.

## When an ADR is warranted

Examples:

- broadening or redefining an authority class;
- introducing a new cross-repository substrate;
- changing the role boundary between Mirror, ToadAid Coder, ToadAid MCP, and governance;
- changing Agent Forge activation semantics;
- replacing a canonical contract;
- deliberately departing from a foundational doctrine.

Routine implementation choices generally belong in the implementation repository instead.

## Suggested format

```text
# ADR-NNN: Title

Status: proposed | accepted | superseded | rejected
Date: YYYY-MM-DD

## Context

## Decision

## Consequences

## Governance impact

## Migration / compatibility

## Supersedes / superseded by
```

## Rule

Architecture may evolve deliberately.

It must not drift accidentally.
