# ADR-0001: Assign the Lane 3 trusted connection-provider to Mirror Desktop Bridge

Status: accepted
Date: 2026-10-18

## Context

ToadAid Pond (`ToadAid/toadaid-app`) presents the governed front door for the toadgang
community's agents. Its docking path has three lanes:

- Lane 1 (identity-evidence presentation) and Lane 2 (admission-evidence presentation) are
  complete and merged in Pond.
- Lane 3 — the trusted connection-provider that holds a real intake boundary for admitted
  senders only and feeds real projections into Pond's exact-shape seam — cannot start,
  because canonical law defers the provider's assignment.

Four canonical deferrals block Lane 3 (all at this repository's main `53de869`):

1. Final repository ownership for unresolved runtime services —
   `blueprints/governed-runtime-component-allocation.md` (L459, L777).
2. Delivery-state host — `contracts/agent-to-agent-messaging-and-delivery-contract.md`
   (L246: "whether Core, MCP, Bridge, or Living hosts delivery state").
3. Intake vocabulary, transports, and runtime —
   `contracts/agent-identity-and-specialist-admission-contract.md` (L279: "intake class
   vocabularies and transports, any intake runtime, and any sender-admission interface").
4. First-slice transport and channel-map authorship — `blueprints/community-agent-fabric.md`
   §13 (L296), §21 (L465), §36 (L761).

`blueprints/community-agent-fabric.md` §36 (L761) states these deferrals "require later
implementation architecture cuts." This ADR is that cut for the provider boundary only.

The Pond Lane 3 plan (`ToadAid/toadaid-app` PR #100, docs-only) mapped these deferrals and
proposed Mirror Desktop Bridge as the host; the human principal has reviewed and approved
that hypothesis. This ADR records the decision canonically so implementation may proceed in
Bridge and then in Pond, without any repository silently taking the assignment.

## Decision

### D1 — Assignment: Mirror Desktop Bridge hosts the provider

Mirror Desktop Bridge hosts the trusted connection-provider — the boundary that holds
admitted-agent intake, runs the delivery lifecycle, and feeds host-neutral projections into
Pond's exact-shape seam. This resolves "final repository ownership for unresolved runtime
services" for this one service only.

Grounding:

- `maps/repository-map.md` L25–27: Bridge is the "governed bridge between desktop/assistant
  surfaces and local repository/runtime capabilities, including MCP-facing capability
  exposure where appropriate."
- `blueprints/governed-runtime-component-allocation.md` Wave 2 (L691) and L258: Bridge is
  the "client-facing local enforcement edge and local governed consequence host" — the local
  trusted-channel boundary host.

Not assigned here: the admission-decision backend, membership/scope storage, routing, or the
governance kernel (Mirror Core remains the Wave-1 governance kernel). The provider checks
admission records; it does not produce them.

### D2 — Delivery-state runtime responsibility: Bridge; semantic ownership: messaging contract

Runtime responsibility for in-flight delivery state — the delivery lifecycle at
`contracts/agent-to-agent-messaging-and-delivery-contract.md` L149–189 (message candidate →
sender identity/admission evaluation → source-scope validation → cross-scope release check →
destination/audience resolution → current membership/revocation policy → delivery-policy
decision → delivery → delivery evidence) — sits with the provider (Bridge) as the local
intake/delivery edge. Semantic ownership of the delivery lifecycle and `MessageId` stays with
the messaging contract.

Grounding: `blueprints/governed-runtime-component-allocation.md` L31–36 — semantic ownership,
runtime responsibility, process placement, and storage ownership remain distinct; the example
at L38 (Scope Sovereignty owns `ScopeId` semantics while components evaluate/persist/bind
state) is the model.

### D3 — First-slice intake transport: local STDIO/MCP exposure, not A2A

The first-slice intake transport is a local trusted channel — Bridge's Wave-2 "supported local
client connection, including STDIO MCP exposure where applicable"
(`governed-runtime-component-allocation.md` L262) — carrying tool/resource capability
exposure. A2A peer-agent messaging is deferred to Wave 9
(`governed-runtime-component-allocation.md` L719, "External interoperability"), gated on local
sovereignty surviving implementation.

Grounding: `contracts/agent-to-agent-messaging-and-delivery-contract.md` L232 — "Delivering a
message must not automatically invoke an MCP tool, and MCP must not become an agent-chat
authority protocol"; `blueprints/community-agent-fabric.md` §21 (L465) — A2A is optional future
peer-agent interoperability, MCP is tool/resource exposure, neither creates authority.

### D4 — Channel-map authorship: Bridge, conforming to trusted-channel law

Bridge authors the provider's channel map as its first deliverable. The map must conform to:

- `contracts/trusted-channel-separation-contract.md` §Blueprint requirement (L231) and
  §Channel authority and precedence (L51, L58): who controls each channel, what semantic
  classes it may establish, what upstream configuration can conflict, how precedence is
  verified, and how unknown or contradictory precedence fails closed;
- `blueprints/community-agent-fabric.md` §13 (L296) reference table;
- `blueprints/governed-runtime-component-allocation.md` "Inputs, channels, and trust
  boundaries" (L475).

Unknown or conflicting precedence fails closed to the canonical outcomes
`unsupported_trusted_framing`, `unknown_channel_precedence`, and `provider_incompatible`
(`contracts/trusted-channel-separation-contract.md` L74–85).

## Consequences

- Lane 3 is unblocked in order: Bridge may plan and implement the provider boundary, then Pond
  may plan L3-P1 (admission-posture presentation from real projections), L3-P2 (D-P16
  live-inbound extension), and L3-P3 (D-P21 reply cause-swap).
- No runtime, code, schema, transport, credential, or activation is created or authorized by
  this ADR. Activation remains `NOT_INCLUDED` for every downstream step.
- The provider stays provider-neutral, and Pond stays projection-consuming and does not
  hardcode Bridge (`blueprints/community-agent-fabric.md` §27; Pond's D-P25
  `providerBoundaryPosture`).

## Governance impact

- Resolves a deferred-decision subset; introduces no new authority class, removes no operator
  boundary, and collapses no distinct trust channel.
- No provider, harness, or model output becomes authoritative for identity, admission, grant,
  policy, or authority state (`blueprints/governed-runtime-component-allocation.md` L431).
- The human principal's review of the Bridge hypothesis is recorded here; this ADR was
  accepted by the human principal on 2026-10-18.

## Migration / compatibility

- This ADR resolves the following deferral lines without editing them: messaging L246
  (delivery-state host), admission L279 (intake vocabularies/transports/runtime and
  sender-admission interface), allocation L777 ("final repository ownership for unresolved
  runtime services" — narrowed to this one service), and fabric §36 (L761 — narrowed to the
  provider boundary).
- Downstream repositories (Mirror Desktop Bridge, ToadAid Pond) cite this ADR when they
  implement the provider and its consumers.
- Remaining Social Control Plane ownership (membership/scope storage, rooms, routing,
  discovery, AgentCard serving) stays deferred per fabric §36.

## Supersedes / superseded by

- None — this is the first ADR in this repository.

---

activation: NOT_INCLUDED
