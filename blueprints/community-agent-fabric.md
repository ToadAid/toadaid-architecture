# Community Agent Fabric Blueprint

**Status:** Architectural blueprint / not runtime authority

**Activation:** `NOT_INCLUDED`

**Purpose:** Describe how independently governed human principals, scopes, personal agents, community and project agents, specialists, and remote agents may collaborate while preserving sovereignty, privacy, admission boundaries, and consequence governance.

## 1. Why the Community Agent Fabric exists

ToadAid may eventually support collaboration among humans and agents whose identities, knowledge, duties, and capabilities belong to different scopes. That collaboration must not create a shared brain, ambient authority, or a path by which one participant silently inherits another's memory, credentials, membership, capability, or sovereignty.

The architectural direction is:

> **Agents may collaborate. Humans remain sovereign.**

And:

> **Community coordination must not collapse personal sovereignty.**

The fabric is not a shared brain. It is a governed fabric in which independently scoped humans and agents may communicate, prove, coordinate, and eventually exchange value without silently inheriting one another's authority.

This blueprint describes desired future architecture. It does not claim that a Community Agent Fabric or its runtime components currently exist.

## 2. Canonical law dependencies

This blueprint composes, and does not redefine, these canonical contracts:

- [`../contracts/scope-sovereignty-contract.md`](../contracts/scope-sovereignty-contract.md) owns PrincipalId, ScopeId, personal/shared/project/public scopes, membership, audience, release, scope-owned data, and scope sovereignty.
- [`../contracts/agent-identity-and-specialist-admission-contract.md`](../contracts/agent-identity-and-specialist-admission-contract.md) owns AgentId, principal-agent and scope-agent bindings, admission, specialist admission, remote-agent admission, and admission revocation.
- [`../contracts/agent-to-agent-messaging-and-delivery-contract.md`](../contracts/agent-to-agent-messaging-and-delivery-contract.md) owns MessageId, AgentMessage, sender and recipient relationships, source and destination scope, delivery, provenance, expiry, and replay.
- [`../contracts/attestation-and-evidence-exchange-contract.md`](../contracts/attestation-and-evidence-exchange-contract.md) owns AttestationId, Claim, issuer and subject binding, evidence basis, verification, validity, disclosure, revocation, supersession, and attestation exchange.

The fabric must also preserve:

- [`../contracts/capability-authority-boundary.md`](../contracts/capability-authority-boundary.md);
- [`../contracts/trusted-channel-separation-contract.md`](../contracts/trusted-channel-separation-contract.md);
- [`../contracts/derived-evidence-contract.md`](../contracts/derived-evidence-contract.md);
- [`../contracts/evidence-activation-contract.md`](../contracts/evidence-activation-contract.md);
- [`../contracts/verification-applicability-contract.md`](../contracts/verification-applicability-contract.md);
- [`../contracts/failure-outcome-taxonomy.md`](../contracts/failure-outcome-taxonomy.md).

If future fabric design needs different mechanical vocabulary or lifecycle semantics, the owning contract must receive a deliberate contract cut. This blueprint must not become a second owner.

## 3. Status, authority ceiling, and non-activation

This is a docs-only architectural blueprint. It adds no runtime, provider activation, scope state, membership, admission, transport, capability, credential access, wallet, signer, payment, transaction, publication, or onchain authority.

```text
desired architecture != current implementation
blueprint acceptance != runtime activation
```

The authority ceiling of this blueprint is descriptive and proposal-only. Every future implementation and activation requires separately bounded work, verification, evidence, governance, and authorization.

## 4. Whole-system conceptual model

The fabric composes four distinct subjects and one governed transition:

```text
PRINCIPAL
    ↓ explicit scope relationships

SCOPE
personal | shared | project | public
    ↓ scope-owned data / audience / membership relationships

AGENT
explicit identity + binding + admission
    ↓ messages / attestations / capability requests

GOVERNANCE
current policy + current state + approval where required
    ↓

BOUNDED CONSEQUENCE
```

The following distinctions remain mandatory:

```text
PrincipalId != AgentId
ScopeId != AgentId
membership != admission
admission != capability
capability != current authority
message != grant
attestation != authority
reputation != authority
payment != authority
room presence != membership
wallet ownership != PrincipalId
NFT or Lore Land ownership != authority
```

A possible future topology is:

```text
Human A
  └─ Personal Scope A
       └─ Personal Agent A

Human B
  └─ Personal Scope B
       └─ Personal Agent B

Project Scope X
  ├─ explicit members
  ├─ project-owned memory and data
  ├─ Project Agent X
  └─ admitted specialists

Shared / Community Scope Y
  ├─ explicit members
  ├─ community-owned knowledge
  ├─ Community Agent Y
  └─ admitted specialists
```

Personal Scope A and Personal Scope B do not merge merely because their humans join Project Scope X or Shared Scope Y. A shared or project scope has its own governed state; it is not a union of member personal scopes.

The fabric is therefore a set of explicitly related sovereign scopes and admitted agents, not one global memory, super-agent, administrator, wallet-controlling model, provider, chain, MCP server, or A2A router.

## 5. Human principals and sovereignty

Human principals remain distinct from agents, providers, wallets, rooms, repositories, and external identities. An agent may support a principal without becoming that principal or absorbing the principal's sovereignty.

Human governance should remain meaningful and legible. An ordinary participant should eventually be able to understand:

- which scope an agent belongs to;
- what information it may see;
- what information it may release;
- which specialists it may request;
- what consequential action is proposed;
- whether approval is required;
- what authority expires;
- what was revoked;
- what evidence exists;
- what happened.

Ordinary control should not require users to understand hashes, provider sessions, raw capability tokens, protocol internals, or A2A and MCP mechanics. This is architectural user-experience direction, not a current interface claim.

## 6. Scope topology

The fabric uses only the scope types and relationships owned by the Scope Sovereignty Contract:

```text
personal
shared
project
public
```

Scope identity, ownership, membership, audience, delivery, release, grants, credential leases, scheduled duties, and revocation retain their canonical meanings.

Room presence does not create membership. Membership does not create admission or capability. Repository access does not create project membership. A wallet, token, NFT, provider session, or external registry does not create a scope or a principal.

## 7. Personal agents

A future personal agent may serve as a continuity agent for one principal's personal context where applicable.

It must preserve:

- personal scope is private by default;
- personal memory does not become shared or project memory;
- community or project membership does not expose personal memory;
- personal files remain personal unless explicitly released;
- credentials remain separately governed and are never ambient memory;
- schedules and duties do not create standing consequence authority;
- participation in a room does not widen disclosure or audience;
- model-context inclusion does not create a new scope or release.

A personal agent may propose a cross-scope release or consequence. It cannot infer release, consent, or authority from usefulness, conversation context, membership, or proximity to another scope.

This blueprint does not decide whether every personal agent is persistent, how its identity or memory is stored, or which runtime component hosts it.

## 8. Shared and community agents

A future community agent is an admitted agent serving one explicit shared scope. “Community” is an agent profile and collaboration purpose; it does not add a fifth scope type or redefine shared-scope law.

Under later separately authorized runtime architecture, a community agent may support bounded duties such as:

- answering from community-owned knowledge;
- coordinating community or project work;
- receiving and sending governed messages;
- exchanging evidence and attestations;
- maintaining approved community artifacts;
- routing candidate requests to admitted specialists;
- producing bounded summaries from community-owned material;
- verifying evidence under explicit methods;
- preparing approved public-release proposals;
- performing separately authorized scheduled duties.

A community agent must not automatically:

- read member personal memory or files;
- access member credentials;
- impersonate a member;
- inherit member capabilities;
- inherit universal administrator authority;
- sign wallet transactions;
- spend community or personal funds;
- publish publicly;
- mutate repositories;
- create membership;
- grant capabilities;
- self-approve;
- override revocation or e-stop.

Administration is not private omniscience. Any future exceptional administrative read remains subject to separate scope, authority, audience, audit, and human-governed policy.

## 9. Project agents

A future project agent is an admitted agent serving one explicit project scope.

A project scope may eventually own project memory, project files and workspace bindings, public or private project artifacts, project messages, project attestations, project specialist relationships, project duties, and project receipts or evidence.

The following separations remain mandatory:

```text
project membership != repository mutation authority
repository access != project membership
project agent != repository owner
project agent != wallet authority
project agent != human principal
```

Project-owned state must arise within the project scope or through an explicit admitted release. A project agent cannot silently import personal or shared data.

## 10. Specialists

Specialists remain separately admitted bounded agents under the Agent Identity and Specialist Admission Contract and the Governed Agent Forge Blueprint.

Possible future profiles include:

- code or construction specialist;
- Living or personal-continuity specialist;
- lore specialist;
- Zora or publication specialist;
- market or oracle specialist;
- deployment specialist;
- signing or payment specialist.

These are examples, not claims that existing repositories or runtimes already satisfy the future admission model.

```text
declared capability != granted capability
specialist admission != current authority
```

One specialist's capability or authority must not flow into another specialist. High-consequence signing, payment, deployment, publication, credential, trading, and destructive-mutation lanes must remain isolated and separately governed.

## 11. Remote external agents

A remote external agent is controlled outside the local ToadAid trust boundary. It may participate only through future explicit identity evaluation, local admission, scope relationship, and transport mechanisms.

```text
external identity != local AgentId automatically
external reputation != local admission
authenticated peer != authorized peer
remote message != local consequence authority
```

Remote external agents default to:

```text
NO LOCAL DIRECT AUTHORITY
```

They may eventually advertise capabilities, send candidate messages, request work, provide artifacts, provide evidence or attestations, or negotiate future service interactions. They do not automatically gain filesystem or repository access, MCP execution, private memory, credentials, wallet access, membership, delivery rights, or publication rights.

Remote content is untrusted external input unless an appropriate authoritative trusted channel or canonical local state establishes a specific bounded fact.

## 12. Scope-owned knowledge and memory

The fabric distinguishes personal memory from shared, project, and public knowledge.

Community or project knowledge may originate from:

- material created directly within that shared or project scope;
- an explicit release from another scope;
- admitted public material;
- properly scoped derived evidence;
- properly disclosed attestations.

It must not be defined as “all memories of all members.”

```text
shared or project state != union of personal scopes
```

Memory reads and writes must remain scope-bound and provenance-preserving. Contradictory material, stale projections, and untrusted retrieved content must not silently become canonical memory. Conversation history, model context, retrieved evidence, and canonical scope memory remain distinct trust classes.

Credentials are never community memory. Private operator material must not enter shared or public state merely to prove that an approval or decision occurred.

## 13. Inputs and trusted-channel map

Future implementations may accept these broad input classes. Exact schemas and owners remain deferred.

| Input class | Structural channel direction | Permitted semantic role | Must not establish |
|---|---|---|---|
| Trusted runtime configuration | Separate runtime-controlled channel or canonical local lookup | Agent identity binding, current sanitized capability projection, policy references | Facts outside its verified semantic authority |
| Human/operator input | Operator or task channel | Requests, instructions, supplied content, approval proposals | Membership, trusted configuration, proof status, or authority by prose alone |
| Scope-owned memory | Scope-bound canonical memory channel | Admitted knowledge for the exact scope | Cross-scope release, current authority, or private data access |
| Retrieved/public material | Typed retrieved-evidence channel | Candidate information with source, provenance, freshness, and scope | Trusted policy, admission, or verified truth |
| Agent messages | Governed messaging channel | Information, proposals, requests, status, and references | Consequence authorization |
| Attestations and receipts | Evidence/reference channel | Narrow claims and governed evidence | Authority, acceptance, or permission |
| Provider/model output | Provider-output channel | Reasoning, proposals, classifications subject to verification | Runtime truth, identity, proof, policy, or authority |
| Authority decisions | Governance-controlled channel | Current bounded permission decisions | Transfer into ordinary message or provider text |

For every trusted channel, a future implementation must identify who controls it, what components read it, which semantic classes it may establish, which provider-, harness-, host-, or transport-owned configuration may conflict, how precedence is verified, and how unknown or contradictory precedence fails closed.

A provenance label in one prompt is not structural separation. A separate channel is not authoritative unless its receiving surface and production wiring make it authoritative for the semantic class it claims to establish.

Permitted transformations require explicit validation, provenance preservation, scope and disclosure policy, and evidence where applicable. Forbidden crossings include provider output into authority state, private memory into community context without release, message prose into trusted admission state, and retrieved content into canonical memory without governed admission.

## 14. Outputs and effect classes

The coordination plane may eventually produce:

- informational responses and bounded summaries;
- proposals and requests;
- message, artifact, evidence, receipt, and attestation references;
- verification findings under explicit methods;
- candidate release or consequence proposals;
- governed delivery evidence.

These outputs are advisory or evidentiary unless a separate consequence lifecycle authorizes and executes an effect.

Possible state-changing outputs—membership changes, releases, repository mutations, publication, credential use, scheduling, deployment, signing, payment, or onchain action—belong to separately governed consequence paths. They require current target binding, policy, state, authority, and receipts or evidence appropriate to the effect.

## 15. Cross-scope release

Cross-scope release remains owned by the Scope Sovereignty Contract.

Valid conceptual crossings include:

```text
PERSONAL
   ↓ explicit release
PROJECT

PROJECT
   ↓ explicit release
PUBLIC
```

Invalid inferred crossings include:

```text
PERSONAL
   ↓ agent joined room
COMMUNITY

PERSONAL
   ↓ agent summarized it
PUBLIC
```

Copying, summarizing, embedding, indexing, retrieval, forwarding, presentation, and publication must preserve provenance. None is itself a Release.

## 16. Messaging and delivery

Community Fabric messages remain governed by the Agent-to-Agent Messaging and Delivery Contract. They may eventually carry information, proposals, requests, status, artifact references, evidence references, or attestation references.

> **A message may inform. A message does not authorize a consequence.**

A community or project agent may forward a candidate request to a specialist. The specialist and the governing runtime must still evaluate the relevant identity and admission, source and destination scope, requested capability, current policy, current target and state, approval, expiry, revocation, and e-stop conditions.

Delivery does not validate content, accept a task, invoke a tool, authorize payment, or authorize another consequence.

## 17. Attestations, evidence, validation, and reputation

Attestation exchange remains governed by the Attestation and Evidence Exchange Contract. Agents may eventually communicate narrow evidence claims about artifact digests, validation results, contributions, project completion, public lore provenance, or settlement evidence.

```text
attestation != authority
verification != authorization
reputation != authority
settlement != acceptance
```

Community validation or reputation may inform later reasoning or policy. It must never become an ambient permission, membership, admission, approval, or authority system. Supporting private evidence bodies and private operator material must not be published merely to make a claim portable.

## 18. Coordination plane and consequence plane

The fabric distinguishes a community coordination plane from a governed consequence plane.

```text
COMMUNITY COORDINATION PLANE
identity
membership
messages
knowledge
artifacts
attestations
requests

        ↓ proposal or request only

GOVERNED CONSEQUENCE PLANE
capability admission
exact target binding
current policy
current state
approval where required
revocation and e-stop
bounded execution
receipts and evidence
```

The coordination plane does not own `MAY`. Neither a community agent, A2A, MCP, a provider, a room, nor an attestation may collapse the two planes.

Exact implementation ownership of the consequence plane remains unresolved.

## 19. Requested future capabilities

This blueprint identifies future capability areas for later bounded design, not grants:

- independently owned personal-agent continuity;
- shared and project scope knowledge access;
- scope-bound messaging and delivery;
- evidence and attestation exchange;
- specialist discovery and candidate request routing;
- governed knowledge sharing and public-release proposals;
- project-to-project collaboration;
- scheduled scope-bound duties;
- optional remote-agent discovery and interaction;
- optional economic service exchange;
- optional external or onchain identity and evidence interoperability;
- conceptual Lore Land and project association.

Every consequence remains governed. A future capability manifest must state exact targets, effects, denials, expiry, revocation, restart behavior, and evidence requirements.

## 20. Community and project collaboration flows

A future collaboration may remain entirely informational:

```text
Project Agent A
    ↓ governed message
Project Agent B
    ↓ scoped response or evidence reference
Project Agent A
```

Possible requests include verifying lore, reviewing an artifact, providing a build service, producing an attestation, proposing collaboration, or requesting a future paid service.

Neither project inherits the other's members, personal memories, credentials, repository rights, wallet authority, or standing capabilities. Collaboration must be explicit, audience-bound, provenance-preserving, and scoped.

A consequence-producing collaboration requires a separate path:

```text
governed message or proposal
    ↓ identity, admission, and scope evaluation
candidate capability request
    ↓ current policy, target, state, and approval
bounded execution by an eligible runtime
    ↓
derived evidence and receipt
    ↓
separate acceptance where applicable
```

## 21. Optional A2A and MCP interoperability

A2A remains optional future peer-agent interoperability. A possible relationship is:

```text
Personal Agent A
    ↕
Project Agent X
    ↕
Community Agent Y
    ↕
Remote admitted Agent Z
```

But:

```text
A2A connectivity != membership
A2A discovery != admission
A2A task != accepted ToadAid task
A2A message != authority
A2A authentication != authorization
```

This blueprint defines no AgentCard schema and activates no A2A runtime.

MCP remains tool and resource capability exposure. Supported clients or agents may eventually use it to request bounded capabilities. A2A concerns peer-agent communication and collaboration; MCP concerns tool and resource exposure. Neither protocol creates authority.

ToadAid MCP is neither removed from the possible design nor made a mandatory chokepoint for every community interaction. Exact A2A, MCP, and direct-transport routing remains deferred.

## 22. Optional economic and onchain interoperability

The fabric may eventually support agent-to-agent economic interactions, including service quotation, payment requirements, payment-authorization proposals, settlement evidence, service delivery, and acceptance. These remain separate:

```text
service request != payment authority
payment requirement != approval
payment authorization != wallet ownership
payment settlement != service delivery
service delivery != acceptance
acceptance != future authority
```

x402 is optional future transport or payment interoperability. This blueprint defines no x402 mechanics, payment budgets, wallet, signer, retry behavior, or payment runtime.

For future economic and other high-consequence lanes, signing authority must remain separately governed. The architecture should not require exposing raw private keys, seed phrases, or unrestricted signer sessions to reasoning models. Signer implementation and wallet custody remain unresolved, and no payment or signer authority is created here.

ERC-8004 may later supply portable external identity, validation, or reputation evidence:

```text
ERC-8004 identity != PrincipalId
ERC-8004 identity != local AgentId automatically
ERC-8004 validation != task acceptance
ERC-8004 reputation != authority
ERC-8004 registry presence != admission
```

EAS and onchain anchoring remain optional evidence interoperability. No registry, EAS, Base, signing, payment, wallet, or chain activity is included.

## 23. Lore Land and project future model

A Lore Land may someday be deliberately associated with a project scope through separate governed decisions:

```text
Lore Land ownership evidence
        ↓
separate Principal binding decision
        ↓
separate project-scope relationship
        ↓
separate membership
        ↓
separate specialist and capability admission
        ↓
separate consequence governance
```

The invalid path is:

```text
Lore Land NFT ownership
        ↓
automatic repository, wallet, administrator, or personal-memory authority
```

A possible future project shape is:

```text
Lore Land N
   └─ Project Scope N
        ├─ explicit human members
        ├─ project-owned lore and data
        ├─ project agent
        ├─ admitted specialists
        ├─ attestations and evidence
        └─ collaborations with other project scopes
```

This is conceptual only. Lore Land identity, ownership, principal binding, project mapping, token or NFT membership, and runtime mechanics remain deferred.

## 24. Federation-friendly direction

The fabric should be federation-friendly: different principals, projects, and communities should be able to operate independently and later interoperate through governed protocols.

It must not require one central ToadAid server, global community database, universal administrator, global agent, global wallet, reasoning provider, or chain.

This is a federation-friendly architectural direction, not implemented federation. Deployment topology, discovery, routing, storage ownership, and federation protocol remain unresolved.

## 25. Human-facing governance, joining, and leaving

Join and leave behavior composes canonical scope law rather than redefining membership:

```text
join
  → explicit membership according to scope governance

leave or revocation
  → future access and authority removed according to canonical law
```

Leaving a shared or project scope must not erase legitimate historical evidence, preserve hidden future access, preserve ambient credentials, silently retain future delivery rights, or silently retain future capabilities.

Exact retention, deletion, and export semantics remain future governance work.

## 26. Revocation and externally dominant e-stop

Revocation affects future admission, membership, access, delivery, or authority according to the owning canonical contract. A stale grant, message, attestation, credential, or prior action cannot recreate what was revoked.

The externally governed e-stop remains dominant across community interactions. Changing provider, transport, room, agent, MCP route, A2A route, or direct route must not silently bypass it.

Queued, delayed, retried, or already-received work does not gain authority while the applicable e-stop is active. This blueprint defines no automatic replay after an e-stop clears.

## 27. Provider and client neutrality

The fabric must remain valid with ChatGPT or Codex, other cloud reasoning models, local models, future providers, and non-model deterministic services.

Changing providers must not widen scope, membership, admission, capability, authority, audience, or disclosure. A provider session is not a principal, AgentId, governance root, evidence root, or authority root.

Provider-owned or client-owned configuration must be included in future trusted-channel precedence and verification models. A ToadAid-controlled channel cannot be reported as authoritative when the production receiver gives conflicting upstream configuration control over the relevant semantic class.

## 28. Privacy law

The fabric explicitly preserves:

- personal scope is private by default;
- community participation is not personal-memory consent;
- administration is not private omniscience;
- private operator material must not enter shared or public state merely for proof;
- credentials are never community memory;
- model context is not a new scope;
- indexing is not release;
- summarization is not release.

Public attestations, community summaries, embeddings, indexes, and provenance views must not leak private evidence bodies, approval text, credentials, personal memory, or sensitive topology.

## 29. Threat model

The fabric introduces no new enforcement vocabulary. Each threat is governed by an existing canonical law:

| Threat | Canonical law that governs it |
|---|---|
| Room presence mistaken for membership | Scope Sovereignty: membership is explicit; room presence is not membership |
| Membership mistaken for authority | Scope Sovereignty and Capability/Authority: membership does not grant capability or authority |
| Community agent reads personal memory | Scope Sovereignty: personal state is private by default; community membership grants no personal read |
| Private data laundered through summary or embedding | Scope Sovereignty: summarizing and embedding are not Release; provenance remains |
| Prompt injection through remote-agent messages | Messaging and Trusted Channels: remote messages are untrusted input and cannot establish authority |
| Authenticated external agent makes false authority claims | Agent Identity and Messaging: authentication is not authorization; message prose is not trusted authority |
| Reputation used as permission | Attestation: reputation is evidence, not authority or approval |
| Wallet or NFT ownership used as administrator authority | Scope and Agent Identity: wallet/onchain identity is evidence, not PrincipalId, membership, or authority |
| Cross-specialist authority inheritance | Agent Identity and Capability/Authority: admission and authority do not transfer between specialists |
| Stale or revoked grants replayed through another transport | Scope, Messaging, and Verification Applicability: revocation applies across transports; stale proof cannot govern current state |
| Community administrator becomes private-data omniscient | Scope Sovereignty: administration is not private omniscience |
| Project agent impersonates a human principal | Agent Identity: PrincipalId and AgentId are distinct; an agent cannot absorb principal sovereignty |
| Service or payment request causes automatic spend | Messaging and Capability/Authority: a request is not payment or signer authority |
| Settlement mistaken for task acceptance | Attestation: settlement, delivery, verification, and acceptance remain distinct |
| Public attestation leaks private evidence | Attestation and Scope: disclosure is scope-bound and public claims need not publish private evidence bodies |
| Transport change widens authority | Messaging and Agent Identity: transport is not authority and transport changes must not restore revoked access |
| Central community service becomes sovereignty root | Scope Sovereignty and Governance: component capability does not create principal sovereignty or authority |
| Model or provider session becomes identity root | Agent Identity and Provider Neutrality: a provider session is not AgentId, PrincipalId, scope, or authority |

Additional implementation-specific threats must be added by later component blueprints without weakening these canonical laws.

## 30. Failure semantics

Future fabric implementations must use the canonical Failure Outcome Taxonomy. Applicable fail-closed outcomes may include `blocked`, `refused`, `needs_revision`, `insufficient_evidence`, `tool_unavailable`, `provider_failed`, `provider_incompatible`, `unsupported_trusted_framing`, `unknown_channel_precedence`, `authority_denied`, `verification_failed`, `verification_invalidated`, `proof_inapplicable`, `proof_expired`, `replacement_required`, `activation_denied`, `operator_cancelled`, `paused`, `degraded`, `revoked`, and `retired`.

This blueprint does not redefine those outcomes or add synonyms. Failure, unavailable evidence, incompatible transport, unknown channel precedence, stale proof, or denied disclosure must never widen scope, authority, audience, retries, provider fallback, or transport access.

## 31. Future production path

Exact production paths and component owners remain deferred. A future consequence-capable implementation must nevertheless preserve this abstract path:

```text
operator, scope-owned input, or governed message
    ↓ structurally separated intake and provenance
identity, admission, source-scope, release, and audience evaluation
    ↓
candidate proposal or capability request
    ↓ current target, policy, state, approval, revocation, and e-stop
bounded capability adapter or specialist
    ↓
normalized result
    ↓
derived evidence, receipt, and applicability record
    ↓
separate acceptance where applicable
```

A future component blueprint must bind this to its real production-equivalent adapters, transports, process or tool routers, and any signer boundary. A safer parallel ceremony cannot prove an unverified product path.

## 32. Evaluation contract and independent verification

No runtime can be called conformant to this blueprint solely because schemas exist or a provider reports success.

Future verification must distinguish:

### Typed or structural verification

- closed identity, scope, message, evidence, and capability representations preserve canonical distinctions;
- private and shared trust classes cannot be accidentally represented as one ambient context;
- requested capabilities and denials remain explicit;
- authority-bearing states cannot be authored by ordinary content.

### Production wiring verification

- production adapters preserve channel separation and authoritative precedence;
- scope and audience bindings survive routing;
- cross-scope data cannot bypass Release through summary, embedding, indexing, forwarding, or model context;
- A2A, MCP, direct transport, queues, and provider changes do not bypass admission, policy, revocation, or e-stop;
- capability requests reach the governed consequence path rather than direct effects;
- credential and future signer boundaries remain outside reasoning-model control.

### Live or adversarial verification

- hostile remote messages and prompt injection cannot create authority;
- room presence, membership, reputation, wallet ownership, or NFT ownership cannot create grants;
- personal memory is not exposed to community or project agents without explicit release;
- replayed or stale grants fail closed across alternate transports;
- payment requests cannot trigger automatic spending;
- public claims do not disclose private evidence or operator material;
- provider switching does not widen scope or effective capability.

For any authority-affecting activation, independent verification must bind the real production path. If applicable independent verification is unavailable, activation remains `activation_denied`.

## 33. Verification subject and invalidation

Future proof must bind the relevant subset of:

```text
source and executable identity
scope, identity, membership, and admission policy versions
message, attestation, and release schema versions
trusted-channel policy and receiver precedence
capability and denial manifests
credential and signer boundary policy where applicable
environment and working-directory policy
transport and routing adapters
production consequence path
authority surface
evaluation-contract version
```

Changes to a bound subject invalidate only the affected proof layers, preserve historical evidence, and require replacement proof under the Verification Applicability Contract. A provider, transport, routing, scope-policy, membership-policy, admission-policy, disclosure, signer-boundary, capability, or production-path change must not inherit prior applicability without a performed binding comparison.

## 34. Explicit denials

This blueprint does not target or authorize:

- hive-mind memory;
- a universal super-agent;
- ambient cross-scope context;
- a model-controlled wallet;
- an autonomous treasury;
- reputation-based permission;
- NFT-based administrator authority;
- room-based authority;
- provider-based identity;
- mandatory public exposure;
- a mandatory MCP chokepoint;
- a mandatory A2A network;
- a central administrator with automatic personal-data access;
- automatic payment retry;
- automatic publication;
- autonomous creation of new authority;
- runtime, provider, MCP, A2A, signer, wallet, payment, chain, social, trading, deployment, or community-agent activation.

Silence about a capability is not permission.

## 35. Public architecture boundary

This public blueprint may describe laws, topology, abstract roles, threat classes, interoperability direction, and conceptual future flows.

It must not publish credentials, keys, wallet secrets, private evidence, private operator messages, private proof contents, sensitive current runtime topology, exploitable private implementation details, or personal user data.

> **Open law. Private sovereignty.**

## 36. Deferred decisions and implementation ownership

This blueprint explicitly defers:

- runtime implementation;
- exact component ownership;
- scope storage backend;
- membership backend;
- identity backend;
- message routing owner;
- room implementation;
- federation protocol;
- public discovery;
- A2A AgentCard schema and runtime;
- MCP routing topology;
- community UI;
- administrator role taxonomy beyond canonical scope law;
- retention, deletion, and export mechanics;
- credential lease implementation;
- signer and wallet implementation;
- x402 runtime;
- payment budgets;
- Base integration;
- ERC-8004 runtime mapping;
- EAS runtime;
- onchain anchoring;
- Lore Land binding mechanics;
- token or NFT membership;
- reputation scoring;
- scheduled-duty runtime;
- specialist runtime admission implementation.

This cut does not decide whether canonical community state belongs in Mirror Core, Mirror Desktop Bridge, ToadAid MCP, Living Agent, ToadAid Coder, a new service, a database, a local daemon, or a remote service.

It does not decide which repository owns membership runtime, scope storage, routing, rooms, public discovery, AgentCard serving, attestation storage, credential leasing, community UI, or payment runtime. Those require later implementation architecture cuts.

## 37. Governing principles

> **Agents may collaborate. Humans remain sovereign.**

> **Community coordination must not collapse personal sovereignty.**

> **A message may inform. A message does not authorize a consequence.**

> **Attestation is evidence. Evidence is not authority.**

And the ecosystem law remains:

> **Build capability. Never manufacture authority.**
