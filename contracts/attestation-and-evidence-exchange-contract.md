# Attestation and Evidence Exchange Contract

## Purpose

This contract is the canonical cross-ecosystem owner for AttestationId, Claim, issuer and subject binding, evidence basis, attestation provenance, verification, validity, supersession and revocation, disclosure, scope-bound attestation exchange, and external attestation interoperability.

It layers on the existing canonical evidence and receipt contracts. It does not replace or redefine their semantics, evidence authority, receipt formats, or lifecycles.

This contract defines architecture only. It does not implement signing, cryptographic key management, EIP-712 typed data, Ethereum Attestation Service (EAS), ERC-8004 registration or validation, onchain anchoring, Base integration, A2A or MCP runtime, x402, payment, wallets, community-agent runtime, or public attestation infrastructure.

## Foundational distinctions

The following concepts must remain distinct:

```text
observation != evidence
evidence != receipt
receipt != attestation
attestation != verification
verification != validation
validation != reputation
reputation != authorization
attestation != authority
receipt != authority
signature != authority
onchain record != authority
payment settlement != task acceptance
task completion evidence != acceptance
acceptance != future authority
```

A valid statement may prove that something occurred or was claimed. It does not authorize another consequence.

## Core law

> **Attestation is evidence. Evidence is not authority.**

An attestation may establish that an admitted actor claims:

- "I observed X."
- "I performed Y."
- "Artifact Z has digest D."
- "Validation V produced result R."
- "Payment P settled."
- "Receipt Q corresponds to action A."

The attestation itself must not establish permission to act, current capability, human approval, membership, delivery authority, payment authority, signer authority, repository authority, administrator authority, task acceptance, or future authority.

## Core definitions

### Observation

An observation is a statement or recorded perception produced by an actor or system about an event, state, result, artifact, or condition.

An observation may be wrong. An observation alone is not canonical evidence unless the applicable evidence contract admits it.

### Evidence

Evidence semantics remain owned by the existing canonical evidence contracts, including the Derived Evidence Contract and Evidence and Activation Contract. This contract does not redefine evidence authority.

Evidence may support a claim. Evidence remains distinct from the claim, an attestation containing the claim, and any policy conclusion drawn from it.

### Receipt

Existing canonical receipt semantics remain authoritative. A receipt records evidence of a governed lifecycle or action under the applicable canonical receipt law.

A receipt may be referenced by an attestation. An attestation does not replace, mutate, or silently strengthen a receipt.

### AttestationId

An AttestationId is a stable identifier for one attestation record. It must be distinct from:

- AgentId;
- PrincipalId;
- ScopeId;
- MessageId;
- ReceiptId or another receipt reference;
- transaction hash;
- ERC-8004 identity;
- EAS attestation identifier;
- provider-turn identifier.

The exact AttestationId format is deferred.

### Claim

A Claim is a precisely scoped proposition asserted by an issuer. It must be narrow enough to verify or dispute.

Appropriate examples include:

- "Artifact digest is D."
- "Validation command V completed with result R."
- "Settlement evidence references transaction T."

An ambient statement such as "This agent is trustworthy" is not a sufficiently precise claim for this contract.

### Issuer

The issuer is the admitted actor, principal, service, or external identity asserting the claim.

```text
issuer identity != issuer authority
```

Issuer authentication or admission may inform evaluation. Neither makes the claim authoritative or grants the issuer authority over its subject.

### Subject

The subject is the explicitly identified entity, artifact, action, receipt, agent, project, or other thing that the claim concerns.

Subject identification does not imply ownership, control, membership, or authority.

### Evidence basis

The evidence basis is the exact evidence or evidence references supporting the claim. It must preserve the derivation and applicability rules of the canonical evidence contracts.

Missing evidence basis cannot be replaced by issuer confidence, a signature, a provider statement, or an external registry entry.

### Disclosure class

The disclosure class identifies the allowed scope and audience exposure for an attestation and its supporting references. It does not itself perform or authorize a cross-scope release.

### Verification

Verification is a bounded evaluation of whether a claim and its evidence satisfy an explicitly identified verification method. Verification must identify what was verified, by which method, against which evidence basis, at what time, and with what applicability.

Verification does not grant permission.

### Validation

Validation is a domain-specific evaluation or result under an explicitly identified validation method. "Validated" does not mean universally trusted, accepted, authorized, or currently applicable.

### Reputation evidence

Reputation evidence is historical feedback or accumulated claims that may inform reasoning or policy. Reputation never grants authority by itself.

## Claim precision law

Attestations assert narrow facts, not ambient trust. Claim scope and policy conclusion are separate.

Prefer:

```text
"Tests A/B/C passed at commit H."
```

over:

```text
"Agent X is safe."
```

Prefer:

```text
"Artifact digest = D."
```

over:

```text
"Artifact is legitimate."
```

Prefer:

```text
"Payment settlement was observed at transaction T."
```

over:

```text
"Service is accepted."
```

A policy may consider a precise claim alongside current trusted state. The attestation must not pre-author the policy conclusion.

## Architectural attestation envelope

The following is an architectural model, not implementation code, a serialization schema, or a public representation:

```text
attestation_id
issuer_identity
issuer_admission_reference where applicable
issuer_principal_binding_reference where applicable
subject_identity or reference
claim_type
claim_schema and version
claim content or claim digest/reference
source_scope
disclosure and audience classification
evidence references
receipt references
message, task, and correlation references where applicable
verification method or reference where applicable
issued_at
expires_at where applicable
supersedes reference where applicable
revocation reference or state where applicable
signature or authentication evidence where applicable
optional external registry reference
optional onchain anchor reference
```

Not every field belongs in every transport or public representation. A portable attestation must not disclose private scope structure, private evidence bodies, credentials, hidden topology, or private operator material merely to reproduce the full architectural envelope.

## Provenance law

Every attestation must preserve enough provenance to determine:

- who or what issued it;
- what subject it concerns;
- what claim was made;
- what evidence basis was relied upon;
- which scope the claim arose from;
- when it was issued;
- whether it is current, expired, superseded, revoked, invalidated, or no longer applicable;
- what disclosure policy applies.

Copying an attestation must not erase provenance. Summarizing it must not silently strengthen its claim. Reformatting must not transform:

```text
issuer claims X
```

into:

```text
X is canonically true
```

## Scope and disclosure law

Attestation exchange is scope-bound. Personal evidence does not become shared, project, or public evidence merely because an agent creates an attestation from it.

The required pattern is:

```text
PERSONAL EVIDENCE
        ↓
explicit permitted claim and release
        ↓
PROJECT ATTESTATION
```

The following is invalid:

```text
PERSONAL EVIDENCE
        ↓
agent summarizes it
        ↓
PUBLIC ATTESTATION
```

Cross-scope exchange must satisfy the Scope Sovereignty Contract, including explicit release, provenance preservation, destination scope or audience, and current policy. A public attestation must not require publication of the private evidence body.

Where the applicable policy permits, disclose the narrow claim, digest or reference, and verification result rather than private source material.

## Private operator material

Private human or operator messages, confirmations, cognition proofs, approval text, or advisory content must not be reproduced, paraphrased, summarized, hashed, embedded, signed, committed, or published merely to produce an attestation.

A future attestation may state only an approved value-free fact such as:

```text
required human-decision evidence is present
```

and only when the applicable canonical proof contract permits that statement. The private confirmation itself must never be included.

## Attestation and receipt separation

A receipt records evidence of a governed lifecycle or action under canonical receipt law. An attestation asserts a scoped claim that may reference one or more receipts or evidence items.

For example:

```text
Receipt:
validation command completed with recorded result.

Attestation:
"At commit H, validation suite V passed according to receipt R."
```

The attestation does not replace or mutate receipt R. Receipt R may remain valid while an attestation about it becomes superseded, revoked, expired, invalidated, or inapplicable for another reason.

## Attestation and message separation

A message may carry or reference an attestation. Message delivery does not validate the attestation. An authenticated message carrying an attestation does not make the attestation authoritative.

A recipient must evaluate the relevant subset of:

- issuer identity;
- issuer admission;
- source scope and disclosure;
- evidence basis;
- verification applicability;
- expiry;
- revocation and supersession;
- domain policy.

Authoritative local facts such as issuer admission, scope relationship, release status, and verification result must come from appropriate trusted channels or canonical local state, not self-asserted attestation prose.

## Verification

Verification is bounded to the attestation or claim, method, evidence basis, verifier identity where applicable, evaluation time, result, and applicability.

A result may be `verified`, `not verified`, or `inconclusive` as a domain verification finding. When the evaluation concerns cross-ecosystem failure, invalidation, expiry, or applicability, it must use the existing canonical Failure Outcome Taxonomy rather than invent a competing outcome. Applicable examples include `insufficient_evidence`, `verification_failed`, `verification_invalidated`, `proof_inapplicable`, `proof_expired`, and `replacement_required`.

A verified attestation remains evidence. It does not become authorization, acceptance, capability, or authority.

## Validity, expiry, and applicability

An attestation may be current, expired, superseded, revoked, invalidated, or no longer applicable. Exact runtime representation is deferred.

Historical truth and current applicability must remain distinct. For example:

```text
"Wallet W owned token N at time T"
```

may be historically true. It does not imply:

```text
"Wallet W owns token N now."
```

Current evaluation must preserve the Verification Applicability Contract. A claim that was valid for an earlier subject, policy, scope, or production path cannot silently govern a changed one.

## Revocation and supersession

Revocation means that the issuer or applicable governance marks an attestation as no longer suitable for future reliance under the applicable policy.

Supersession means that a later attestation replaces or updates an earlier claim without erasing its history.

Neither revocation nor supersession rewrites history. Historical evidence remains historical. A revoked or superseded attestation cannot silently recreate authority, admission, membership, approval, acceptance, or capability.

## Replay and staleness

An old attestation must not be replayed as current merely because its signature remains cryptographically valid.

Future evaluation must consider the relevant subset of:

- expiry;
- current scope and disclosure policy;
- current issuer admission;
- revocation;
- supersession;
- verification applicability;
- current subject state.

```text
cryptographic validity != current applicability
```

## Agent-to-agent exchange

Future agents may exchange attestation references through the canonical Agent-to-Agent Messaging and Delivery Contract.

For example:

```text
Project Agent A:
"Artifact X is complete; attestation A references receipt R."
```

Project Agent B may inspect or verify that evidence. However:

```text
receiving attestation A != accepting artifact X
accepting artifact X != granting Agent A future authority
```

Transport authentication, message delivery, or successful exchange does not validate the claim or authorize its consequence.

## Community and project attestations

Future community or project agents may maintain community-owned attestations for public lore verification, project build completion, published artifact digests, shared validation results, contribution evidence, or approved public provenance.

They must not publish personal memories, private credentials, private approval text, private receipt bodies, private operator messages, or hidden security topology merely for verifiability.

Community ownership of an attestation does not establish authority over its subject or over a member's personal scope.

## Reputation

Reputation may be derived from historical attestations or feedback. This contract defines no reputation scoring algorithm.

```text
reputation != admission
reputation != capability
reputation != authority
reputation != approval
```

A high reputation score cannot bypass current scope policy, human approval, exact-state verification, e-stop, expiry, invalidation, or revocation.

## Optional cryptographic and external interoperability

### EIP-712

EIP-712 may be a future optional structured-signing mechanism.

```text
EIP-712 signature = possible cryptographic evidence
EIP-712 signature != ToadAid authorization
```

This contract defines no typed-data schema and authorizes no signing.

### Ethereum Attestation Service

EAS may be optional external interoperability. It is not required, canonical ToadAid storage, identity authority, or authorization authority.

This contract defines no EAS schema, deployment, or use.

### ERC-8004

ERC-8004 identity, validation, or reputation may be optional external evidence.

```text
ERC-8004 identity != PrincipalId
ERC-8004 validation != acceptance
ERC-8004 reputation != authority
ERC-8004 registry record != local admission
```

This contract authorizes no registration, validation transaction, or other chain activity.

### Onchain anchoring

A future attestation or receipt digest may optionally be anchored onchain. Such an anchor may provide limited evidence of existence by a certain point, association with a submitted digest, or a public provenance reference.

It does not prove correctness, authorization, acceptance, current validity, or private evidence contents. Mandatory onchain anchoring is deferred.

## Payment and x402 relationship

Payment settlement may become evidence referenced by an attestation. A narrow claim may state:

```text
"Payment P settled according to settlement evidence S."
```

But:

```text
settlement != service delivery
settlement != task acceptance
settlement != quality verification
settlement != future payment authority
```

This contract defines no x402 mechanics, payment runtime, wallet, signer, or transaction authority.

## Lore Land and onchain ownership example

An attestation may narrowly assert:

```text
"Wallet W was observed as owner of Lore Land N at block or time B."
```

That is historical onchain evidence. It does not itself establish PrincipalId binding, current project membership, repository authority, community administration, wallet or signing authority, or future ownership.

Actual Lore Land and project mapping is deferred to a later domain cut.

## Trusted-channel relationship

This contract preserves the Trusted Channel Separation Contract. Attestation content carried in ordinary message text must not masquerade as trusted local policy metadata.

Where a local verifier establishes issuer admission, scope relationship, release status, or verification result, those facts must come from an appropriate authoritative trusted channel or canonical local state. A structurally separate but non-authoritative channel cannot establish them.

## Derived evidence relationship

An attestation derived from evidence must:

- identify its source evidence;
- preserve provenance;
- not silently broaden the source meaning;
- not erase invalidation or applicability conditions;
- not turn derived content into new authority.

A summary, projection, digest, or external registry record remains derived evidence. It is not canonical current state merely because it is portable or cryptographically authenticated.

## Failure and refusal

Attestation handling must use the canonical Failure Outcome Taxonomy where its outcomes apply.

Examples include:

- missing evidence basis: `insufficient_evidence`;
- unverifiable issuer: `insufficient_evidence` or a narrower local subtype mapped to it;
- expired proof or attestation evidence: `proof_expired` where the canonical meaning applies;
- invalid signature or evidence: `verification_failed` where a declared verification contract was tested and failed;
- denied scope disclosure: `refused` or `authority_denied` according to the canonical distinction;
- inconclusive verification: `insufficient_evidence` when the intended claim cannot be supported;
- invalidated current applicability: `verification_invalidated`, followed by `replacement_required` where replacement proof is required.

Revoked and superseded are lifecycle facts under this contract. `revoked` retains its canonical authority meaning when an authority or activation is withdrawn; an attestation's revocation must not invent a competing authority outcome.

Failure must not widen disclosure, add authority, bypass current policy, trigger an unapproved retry, or strengthen the claim.

## Public architecture boundary

This public contract may describe laws, abstract fields, interoperability relationships, and threat principles. It must not contain credentials, private keys, operational wallet addresses, private evidence, private proof material, sensitive runtime topology, exploit details, or private user information.

> **Open law. Private sovereignty.**

## Non-claims and deferred decisions

This contract explicitly defers:

- exact AttestationId format;
- serialization;
- signature format;
- cryptographic key type;
- signer ownership;
- EIP-712 schema;
- EAS schema and usage;
- ERC-8004 runtime mapping;
- reputation algorithm;
- onchain anchoring;
- public registry;
- attestation persistence backend;
- attestation storage owner;
- attestation routing owner;
- verification runtime owner;
- whether Core, MCP, Bridge, or Living hosts attestation state;
- payment and x402 integration;
- wallet and signer implementation;
- Base integration;
- Lore Land and project mapping;
- community-agent runtime.

No signing, wallet operation, payment, transaction, onchain publication, runtime activation, A2A activation, MCP activation, or authority grant is included in this architecture cut.

The governing sentence is:

> **Attestation is evidence. Evidence is not authority.**
