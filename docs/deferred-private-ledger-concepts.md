# Deferred Private-Ledger Concepts

**Status:** Deferred concept and question inventory; not part of the first explorer architecture, a normalized schema, an implementation backlog, or authorization to accept real financial data

**Purpose:** Preserve useful private-ledger concerns from earlier design work without treating them as entities, interfaces, cardinalities, lifecycle rules, or commitments for the public fictional explorer.

**Review posture:** Planning material for human review. A concept's presence here means only that it may deserve reconsideration if a concrete private-data use case is later scheduled.

## 1. Why these concepts are deferred

The first product direction is a public methodology explorer using curated fictional scenarios. Designing a comprehensive private-ledger model now would make unselected future use cases dictate the explorer's modules and vocabulary.

The explorer needs one structural constraint from this future possibility: it must not collect or durably store private financial histories by accident. It does not need a dormant private-ledger object model.

No implementation should create a type, table, service, or workflow merely because a term appears in this note. Concepts should move into the active architecture only after a selected vertical use case demonstrates the need and its source, product, privacy, and lifecycle behavior have been reviewed.

## 2. Concept clusters that may matter later

### Real financial history

A private ledger may eventually need to preserve native amounts and currencies, economic dates, provenance, ownership, classification judgments, valuation evidence, acquisition, expenses, transfers, gifts, losses, recoveries, and opening-state uncertainty.

Open questions include how much asset identity is useful, how aggregate and item-level records avoid double counting, and how incomplete history is represented without manufacturing certainty.

### Assessment and obligation history

A future use case may distinguish freely mutable drafts, calculation previews, committed historical assessments, resulting obligations, and later amendments. If so, corrections should not silently rewrite what was previously understood, and a changed assessment must account for dependent balances and reports.

Whether an externally calculated or reconstructed amount can become an allocatable obligation remains an open question. The explorer should not answer it by introducing a generic commit path.

### Remittance, intent, treatment, and allocation

Earlier work identified useful distinctions among a remittance fact, intent at remittance, later understanding, an obligation, and deliberate allocation. These distinctions may matter if a private ledger is scheduled, especially for settlement intent pending assessment, voluntary contributions, split treatment, cross-currency credit, reversals, and reconciliation.

They do not require the fictional explorer to implement payment persistence. A selected fictional scenario may illustrate the distinctions with transient values and structured explanation.

### Ownership and household transitions

Real-data support may need effective-dated ownership, individual or joint assessment arrangements, payment source distinct from obligation owner, and transitions involving marriage, separation, divorce, remarriage, gift, inheritance, death, or estate settlement.

These are sensitive use cases with unresolved source, product, jurisdictional, and privacy questions. They should not be reduced to a retrospective household toggle or anticipated through a large Phase 1 model.

### Revision, replay, and deletion

Reproducibility may eventually require exact inputs, calculation versions, applied rate evidence, precision conventions, and structured traces. A later system may also need amendments, supersession, export, correction, and deliberate full deletion.

Replay and append-only history do not override privacy deletion. Backup retention, shared-record authority, dependency invalidation, and exported copies require policy decisions before architecture can be selected.

### Source and content governance

The repository's human-review checklist records deliberate review of exact document scopes. It is not a runtime business entity, and human review does not create authority.

If a future product needs editorial authoring, versioned source propositions, translation governance, or publication workflow, those should begin with concrete editorial use cases. A static or build-time source catalog may be sufficient for the public explorer.

### Private access and agent diagnostics

A private ledger would require threat modeling, authentication, authorization, encryption, recovery, revocation, audit boundaries, export, deletion, operational-log limits, and permission-scoped diagnostics. Couple, adviser, or agent access must not be inferred from economic ownership or household relationships.

The explorer must not carry inactive private-access infrastructure in anticipation of those choices.

## 3. Re-entry gates

A deferred concept should enter the active architecture only when:

1. A concrete user-facing vertical use case has been selected.
2. Its authoritative constraints, individual judgments, derived rules, and open questions are distinguished.
3. Exact fictional examples and expected outcomes exist.
4. The minimum required records and lifecycle transitions can be named from those examples.
5. Privacy, security, recovery, export, correction, and deletion implications are reviewed when real data is involved.
6. The human-review ledger covers the affected source, design, and implementation scopes.
7. The change can be added without weakening the public explorer's structural prohibition on private-data storage.

Passing these gates does not require reuse of any term in this document. Implementers should prefer the vocabulary that emerges from the reviewed use case.

## 4. Decisions this note does not make

This inventory does not decide:

- A database, schema, aggregate, service, API, event model, or cardinality
- Whether committed records are immutable, event sourced, bitemporal, or revision based
- How prior assessed principal and carried remainder survive currency or methodology changes
- Whether an assessment produces one or several obligation components
- How allocations behave after an assessment amendment
- Which rate sources, valuation dates, gold instruments, FX conventions, or precision rules apply
- Whether voluntary contributions may later receive obligation credit
- How incomplete history, loss and recovery, or ownership transitions are normalized
- Who may amend or delete shared records
- Whether old executable calculation versions must remain runnable
- Whether the private ledger will be built at all

These remain study, consultation, product, privacy, and implementation questions. The [Draft Explorer Architecture](draft-explorer-architecture.md) deliberately proceeds without resolving them.
