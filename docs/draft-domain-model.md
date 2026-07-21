# Draft Domain Model

**Status:** Candidate conceptual domain model; not an authoritative interpretation, approved calculation rule, normalized persistence schema, or implemented API

**Purpose:** Define a shared conceptual vocabulary without silently resolving the project's open methodological, temporal, ownership, currency, privacy, or security questions.

**Review posture:** Candidate planning material. The record names, attributes, relationships, and lifecycle proposals remain subject to source review, fictional acceptance testing, consultation, privacy design, and revision.

This document does not require one table, aggregate root, service, or interface for every concept it names. The `Event` terminology used in the existing RFC describes semantic history; it does not select event-sourced persistence.

## 1. Modeling posture

The model should preserve reasoning, provenance, and uncertainty rather than reduce the domain to one calculated balance.

Its central distinctions are:

- Authoritative constraints are not user-configurable preferences.
- Recorded financial facts are not interpretations.
- Individual judgments are not source rules.
- Bookkeeping lenses organize the same history; they do not create facts.
- Operating assumptions are technical choices needed for reproducibility.
- Experimental hypotheses are opt-in research transformations.
- Voluntary practice remains separate from obligatory assessment.
- Assessment, obligation, payment, treatment, and allocation are different records.
- Drafts and previews do not change committed history.
- Amendments supersede earlier committed assertions instead of rewriting them.
- Holdings, balances, statuses, comparisons, and reports are derived projections.
- Full privacy deletion is distinct from correction or amendment.

Ordinary relational storage with typed records, immutable committed revisions, explicit relationships, and rebuildable projections is a plausible future fit. It is not selected by this document.

The model should not begin with a generic entity-attribute-value store, a universal `method_option` table, or a generic `FinancialEvent(type, json)` representation that collapses facts and interpretations.

## 2. Separate conceptual axes

The project currently uses several related but non-interchangeable classifications. They should remain distinct until a reviewed vocabulary is established.

| Axis | Examples | Must remain separate from |
| --- | --- | --- |
| Source or evidence basis | Explicit text, authoritative synthesis, worked example, historical inference | The computational role assigned to a proposition |
| Computational role | Constraint, derived rule, judgment, lens, operating assumption, hypothesis, voluntary practice | Current research posture |
| Current posture | Provisional, experimental, legacy, set aside, open | Human-review state or official approval |
| Fact provenance | Observed, documented, user asserted, imported, estimated, reconstructed, unknown | Rule authority |
| Record lifecycle | Draft, preview, committed revision, amendment, deletion | Financial or spiritual meaning |
| Economic time | Occurrence date or valid interval | Date the record became known or stored |
| Economic ownership | Legal or beneficial share | Control, use, payment source, or application access |
| Currency context | Recorded, primary, obligation, payment, or reporting currency | Language, locale, residence, or nationality |

Every displayed calculation should trace the applicable values across these axes. One broad `EpistemicStatus` field should not substitute for separate domain meanings.

## 3. Candidate value concepts

### 3.1 Identity and references

- `RecordId` identifies a stable conceptual record.
- `RevisionRef` identifies the exact committed revision used elsewhere.
- `EvidenceRef` points to source, receipt, import, consultation, or supporting material without copying its meaning into every record.
- `InputManifest` identifies the exact fact, decision, ownership, rate, and methodology revisions consumed by a committed calculation.

### 3.2 Money, quantities, and precision

- `Money` contains an exact decimal amount and currency-unit reference.
- `CurrencyUnit` identifies a current or historical currency without deriving it from locale.
- `Quantity` contains an exact amount and unit.
- `GoldWeightDefinition` preserves the source-defined relationship used in the threshold calculation.
- `PrecisionPolicy` identifies intermediate arithmetic, calculation scale, currency rounding, and display precision.

Binary floating-point values should not represent money, rates, weights, shares, or percentages.

The source relationship `19 × 19 ÷ 24 × 4.6 = 69.1916… grams` is the calculation basis for the threshold weight; approximately `69.2 g` is a display value.

### 3.3 Time and supersession

- `Instant` records a timestamp with explicit time-zone meaning.
- `LocalDate` records a civil date when an instant is unavailable or inappropriate.
- `ValidInterval` records when ownership, a decision, or another assertion applies economically.
- `RecordedAt` records when the system learned or committed an assertion.
- `SupersessionRef` links a later assertion to the committed assertion it replaces.

### 3.4 Provenance and uncertainty

`Provenance` may record origin, recorder, capture method, evidence references, and capture time.

Candidate certainty kinds include observed, documented, user asserted, imported, estimated, reconstructed, historically inferred, and unknown.

An estimate may include a range, candidate dates, method, and confidence category. Missing, unresolved, estimated, and exact values should not become indistinguishable nulls.

## 4. Candidate domain vocabulary

The following are conceptual records or projections, not a proposed table list.

| Area | Candidate concepts | Responsibility |
| --- | --- | --- |
| Knowledge | `SourceRecord`, `SourcePassage`, `PropositionVersion`, `RuleVersion`, `RuleSetVersion`, `ReviewAssertion` | Preserve citations, proposition meaning, version, rationale, and review evidence |
| Methodology | `BookkeepingLensVersion`, `OperatingAssumptionVersion`, `MethodologyProfileRevision` | Describe a versioned composition of a known bookkeeping lens and operating assumptions for canonical evaluation |
| Research | `ExperimentalHypothesisVersion`, `ResearchComparison` | Preserve opt-in transformations and comparisons outside the committable assessment path |
| Scenario/workspace | `Scenario`, future `Workspace`, `Participant`, `AssessmentScope`, `ScopeMembershipInterval` | Bound fictional or private histories and assessment arrangements |
| Financial history | `FinancialEvent`, `EventLeg`, `OpeningStateClaim`, `PropertySubject`, `ValuationClaim` | Preserve native facts, movement, opening assertions, asset identity where useful, and valuation evidence |
| Decisions | `DecisionRecord`, `ClassificationDecision`, `PrimaryCurrencyDecision` | Preserve effective-dated personal judgment, intent, or operating choice |
| Ownership/context | `OwnershipInterval`, `ControlOrUseInterval`, `ResidenceContextInterval` | Preserve ownership and contextual changes without inferring one from another |
| Rates | `RateSnapshot`, `RateApplication`, `ThresholdValuation` | Preserve market evidence and each documented use |
| Assessment | `Assessment`, `AssessmentRevision`, `AssessmentBasisLine`, `CalculationTrace` | Preserve a reproducible historical calculation assertion |
| Settlement | `Obligation`, `PaymentEvent`, `IntentAtRemittance`, `LaterTreatmentDecision`, `PaymentAllocation`, `AllocationReversal` | Preserve face amount, remittance fact, intent, later understanding, and deliberate credit |
| Working state | `ScenarioDraft`, `PreviewRun`, `AmendmentPreview` | Support freely mutable exploration without changing committed history |
| Projections | `Holding`, balances, reconciliation categories, converted views, comparisons, diagnostics | Present rebuildable current or comparative views |

`ReviewAssertion` records review of an exact version. Human review does not create official approval, authoritative status, or approval of later revisions.

A committed assessment references the application-supplied canonical specification/kernel version and one `MethodologyProfileRevision` identifying a known bookkeeping lens and explicit operating-assumption versions. A profile revision cannot include an experimental hypothesis.

Experimental hypotheses belong only to `ResearchComparison` records and cannot create or modify an `Assessment`, `Obligation`, allocation, or canonical persisted result. A profile revision must not disable source-constrained behavior or make voluntary practice part of obligatory principal.

## 5. Scenarios, participants, and ownership

`Scenario` is the Phase 1 root for an authored fictional history. A future `Workspace` is a privacy boundary for private history and requires separately reviewed authorization, encryption, recovery, export, and deletion behavior.

`Participant` represents a person described by the history.

`AssessmentScope` represents an individual or joint arrangement used by a methodology. It is not an owner, household identity, login role, or permission group.

`ScopeMembershipInterval` links participants to an assessment scope over an explicit valid interval. A newly chosen methodology applies prospectively; any historical reconstruction is separately labeled, provenance-bearing, and remains subject to specification review.

`OwnershipInterval` links a property subject to a participant and share over a valid interval. Legal ownership, beneficial ownership, control, and use may require separate assertions.

Marriage, separation, divorce, remarriage, gift, inheritance, and death create transition records and effective intervals. They do not retroactively rewrite ownership, assessment scopes, obligations, or allocations.

Payment source and obligation owner remain separate even when shared accounts or spouses provide funds. Application access remains separate from all economic ownership and household relationships.

## 6. Financial history and holdings

`FinancialEvent` records an economic occurrence such as acquisition, income, expense, transfer, gift, inheritance, disposal, realized gain, loss, recovery, or correction.

Some event labels may themselves depend on judgment. The calculation should retain the underlying amount, currency, parties, date, and provenance rather than rely on a type label alone.

An event may contain `EventLeg` records. Internal transfers should have offsetting effects so movement within the same owner and assessment scope does not manufacture wealth.

`OpeningStateClaim` represents a documented opening position, estimated range, legacy reconstruction, or prospective-only starting point. It must not silently assert complete history or prior clearance.

`PropertySubject` optionally identifies a material asset, liability, account position, or aggregate category. Item-level identity is not required for every ordinary possession.

`ValuationClaim` records amount, currency, valuation date, method, evidence, and uncertainty separately from purchase cost.

`ClassificationDecision` records `subject`, `exempt`, or `unresolved`, with valid time and optional rationale. It is a person's recorded judgment in context, not an institutional ruling.

An aggregate category and its components must not both contribute to one calculation unless their relationship explicitly prevents double counting.

`Holding` is a current projection derived from events, ownership, valuation, and classification history. It is not the primary financial history.

## 7. Assessment

`Assessment` is a stable conceptual identity with one or more immutable committed `AssessmentRevision` records.

A revision should retain or reference:

- Assessment date and effective financial period
- Assessment scope
- Exact input revisions
- Native-currency financial facts
- Applicable classification and judgment revisions
- Prior assessed-principal and loss-recovery inputs
- Carried sub-unit remainder
- Rule-set, kernel, lens, and methodology versions
- Rate applications
- Precision policy
- Threshold value
- Completed unit count
- Obligatory principal
- Resulting obligation amount and currency
- Reproducible calculation trace

An `AssessmentBasisLine` may explain how an input contributed to or was excluded from the assessment.

“Threshold-bearing value,” if adopted as terminology, is an assessment-context result. It is not an intrinsic flag or amount on a financial event, holding, participant, or property record.

The local-currency value of one threshold unit, the value entering a threshold comparison, obligatory principal, and carried remainder are different values.

An amendment creates a new revision linked to the earlier revision. It distinguishes fact correction, judgment reconsideration, and newly available information, and records both effective and recorded time.

Before commitment, an amendment preview should identify affected obligations, allocations, carried state, and reports.

## 8. Obligation, remittance, treatment, and allocation

`Obligation` records the face amount, currency, owner, and its provenance-bearing basis. The canonical case originates from a committed assessment revision. Whether and how a previously calculated external obligation or historical reconstruction may be confirmed as an allocatable obligation remains open; a raw claim or preview cannot receive allocations.

A threshold comparison that does not complete an initial or further unit creates no new obligation. It does not reduce or extinguish an earlier obligation. Any voluntary remittance remains a separate `PaymentEvent` and does not create an obligation.

Whether one assessment may produce multiple obligation components remains open.

`PaymentEvent` records the remittance fact: payment date, native amount and currency, source of funds, optional receipt reference, provenance, and uncertainty.

`IntentAtRemittance` preserves what the person understood or intended when making the payment. Candidate states are:

- Settlement of an already calculated obligation
- Settlement intent pending assessment
- Voluntary contribution
- Unresolved

Absence of a recorded assessment does not default a payment to voluntary. Settlement intent does not manufacture an obligation.

For a voluntary contribution, possible future-credit intent remains separately recorded as explicitly excluded, preserved for possible later allocation, or unresolved. Preserved intent does not establish eligibility.

`LaterTreatmentDecision` records a later understanding without rewriting intent at remittance.

`PaymentAllocation` deliberately links part of one payment to one obligation. Payments and obligations have a many-to-many relationship through allocations.

An allocation across currencies records both the payment-currency amount consumed and obligation-currency amount credited. It references the conversion evidence, purpose, precision, and rounding difference.

`AllocationReversal` negates an earlier allocation under ordinary correction rather than deleting it silently.

Payment availability and obligation balance should be derived from allocations and reversals. An assessment may suggest a compatible payment but never allocate it automatically.

## 9. Candidate relationships and lifecycle ownership

| Relationship | Candidate cardinality or rule |
| --- | --- |
| Scenario or workspace to participant | One to many |
| Participant to assessment scope | Many to many through effective-dated membership |
| Property subject to participant | Many to many through ownership intervals |
| Source passage to proposition version | Many to many |
| Methodology profile revision to bookkeeping lens and operating assumptions | One known lens plus explicit operating-assumption-version references |
| Assessment to committed revision | One to many over time |
| Assessment revision to input revision | Many through an input manifest |
| Assessment revision to rate application | Zero to many |
| Canonical assessment revision to obligation | Currently zero or one; component obligations and any reviewed external-confirmation path remain open |
| Payment to obligation | Many to many through allocation |
| Rate snapshot to rate application | One to many |
| Committed revision to operative successor | Zero or one unless explicit branching is designed |

Financial events own recorded native facts. Decision records own judgments and classifications. Assessment revisions own historical calculation results. Obligations own face amount and owner. Payments own remittance facts and original intent. Allocations own obligation credit. Reports and projections own no historical truth.

Candidate lifecycle behavior is:

| Record kind | Lifecycle |
| --- | --- |
| Draft | Mutable, undoable, and freely deletable |
| Preview | Derived and non-committing |
| Versioned source, rule, or methodology record | Immutable; later version supersedes |
| Committed financial assertion | Immutable in ordinary use; correction adds a superseding assertion |
| Decision | Effective-dated; reconsideration adds a new decision |
| Rate snapshot | Immutable observation |
| Committed assessment | Immutable; amendment adds a revision |
| Payment | Original remittance fact and intent preserved; correction supersedes explicitly |
| Allocation | Reversal and replacement rather than silent mutation |
| Projection or cache | Rebuildable and replaceable |
| Full deletion | Explicit privacy action outside ordinary supersession |

## 10. Currency, rate evidence, and time

Every native financial amount remains recorded and displayed in its recorded currency by default. A converted amount is a labeled derivative and does not replace the native fact.

`RateSnapshot` should preserve base and quote units, exact rate and direction, provider or source, instrument and market convention, effective market time, retrieval time, contemporaneous-versus-retrospective provenance, evidence, and uncertainty.

`RateApplication` records why and how a snapshot was used. Candidate purposes include assessment valuation, payment conversion, period-end reconciliation, converted reporting, and experimental current-gold translation.

A rate used for one purpose must not silently replace a rate used for another. Gold used to calibrate the threshold remains distinct from physical gold owned as property.

A change in display currency, residence, locale, or primary currency is not an acquisition event. Unrealized reporting-currency movement must not silently become income, acquisition, or realized gain.

The model should preserve both economic valid time and record/knowledge time. A calculation run should identify both the date or period being evaluated and the record revisions known to that run.

This supports two different questions:

- What is now understood about an earlier date?
- What did the record show at a particular time about that earlier date?

The proposal does not select a bitemporal database. Explicit date fields and revision references may be sufficient.

## 11. Derived projections and non-fields

Candidate rebuildable projections include current holdings and ownership, current classification view, carried principal and remainder, obligation balance, payment availability, reconciliation categories, converted views, current-gold comparisons, bookkeeping-lens comparisons, and diagnostic explanations.

A committed assessment retains its historical result and trace even when projections are rebuilt.

The following should not become authoritative mutable fields:

- `holding.purified`, `holding.paid`, or `holding.already_assessed`
- `participant.above_threshold` or `scope.threshold_status`
- `holding.assessable_value` outside an assessment context
- `event.threshold_bearing`
- Mutable `payment.is_voluntary` or `payment.is_applied`
- Mutable `obligation.is_paid`
- `obligation.current_gold_units`
- A retrospective `workspace.joint_method` toggle
- A native-currency balance treated as a separate obligation
- Reporting-currency movement recorded as acquisition
- Possible-future-credit intent treated as eligibility

Current classification, payment availability, obligation balance, and settlement state may be cached only as derived projections with identifiable source records.

A current-gold translation must not become prior assessed principal or enter the canonical obligation calculation. Payment-date gold must not become an observed assessment-unit count.

## 12. Phase boundary

| Phase 1 fictional explorer | Future private ledger |
| --- | --- |
| Authored fictional scenarios | Real private workspaces |
| Fictional participants and ownership transitions | Personal identity and ownership history |
| Versioned rule and methodology catalog | Effective-dated personal methodology profiles |
| Session drafts and previews | Committed facts, decisions, and amendments |
| Fictional assessments, obligations, payments, and allocations | Actual financial and remittance history |
| Comparison runs and source overlays | Incomplete-history reconstruction |
| Explicit fictional exports | User-controlled export and deletion |
| No receipt uploads or personal notes | Optional evidence attachments |
| No durable household-financial input | Encrypted private storage |
| No couple or adviser permissions | Reviewed access and revocation model |
| No agent access to private facts | Explicit permission-scoped diagnostics after security review |

Phase 1 may reuse conceptual vocabulary without reusing the eventual private persistence architecture.

## 13. Privacy and deletion

A future private ledger must not accept real data before threat modeling, encryption, recovery, authorization, export, deletion, and security review are complete.

Ordinary append-only semantics do not override an explicit full-deletion action. Deletion removes, invalidates, or recalculates dependent assessments, obligations, allocations, projections, caches, indexes, and diagnostics so they do not remain apparently valid without their basis.

Operational logs should use opaque identifiers and avoid amounts, rationales, receipt content, and other financial payloads.

Backup retention, cryptographic erasure, shared-record authority, and previously exported copies require explicit policy decisions. An amendment must not be presented as a substitute for full deletion.

## 14. Language and text design note

Multi-language support is a possible future capability, not a current language list, localization framework, translation-storage design, or delivery commitment.

Source quotations should preserve their original text, language tag when known, exact passage reference, and provenance. A future translation representation should remain linked to—not overwrite—the cited source and should identify its language and whether it is official, published, project-authored, or user-supplied when known.

User-entered rationales, notes, and descriptions remain original records and should not be presumed translatable. Sending private text to an external translation service would require separate explicit user action and privacy review.

Language and locale must not determine currency, rate convention, residence, ownership, methodology, or calculation behavior. No dedicated translation record or localization storage is required by the present conceptual model.

## 15. Highest-priority open questions

1. What historical state remains invariant after assessment: native principal, property provenance, completed units, or a linked combination?
2. What exact formula carries prior assessed principal and sub-unit remainder when threshold values or primary currencies change?
3. Does one assessment produce at most one obligation, and how should obligation revisions behave after amendment?
4. May any reviewed external-confirmation path originate an allocatable obligation without a canonical assessment revision and, if so, with what provenance?
5. What happens to existing allocations when an amended assessment changes or removes an obligation?
6. Which valuation date, gold instrument, market convention, and FX source govern an assessment?
7. What constitutes realized foreign-exchange gain, and how are redenomination, multiple lawful rates, or currency collapse represented?
8. Can voluntary contributions ever receive later obligation credit, and what source or explicitly labeled treatment establishes eligibility?
9. May a remittance have split intent at entry, or may only later treatment and allocation divide it?
10. How should incomplete history initialize prior assessed principal, units, ownership, and uncertainty?
11. Should loss and recovery be tracked at aggregate level, asset level, or through linked views of both?
12. How should joint and individual histories transition through marriage, divorce, remarriage, inheritance, death, and estate settlement?
13. Which review state and fictional acceptance results are required before a rule-set version becomes eligible for implementation?
14. Who may amend or delete shared private records, and what dependent or exported data remains outside that action?
15. Which multilingual content-governance and review process would be required before supporting any language?

This candidate model remains a vocabulary for review, not a database design or statement that the open questions have been settled.
