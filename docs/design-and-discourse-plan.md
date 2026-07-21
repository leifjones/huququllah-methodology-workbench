# Design and Discourse Plan

**Status:** Pre-specification RFC

**Audience:** A general Bahá'í audience learning about the law in practice, reviewers familiar with the authoritative guidance, and future designers or implementers

**Product posture:** Independent learning project; not official guidance or a payment service

## 1. Desired contribution

The workbench should help people share *how they reasoned* without implying that every methodology has equal support or that one person's ledger settles another person's obligation. Its primary contribution is a common descriptive language connecting:

- Source principles
- Financial and ownership facts
- Individual judgments
- Bookkeeping choices
- Market-rate evidence
- Calculated assessments
- Later settlement payments
- Known uncertainty

The preferred discourse pattern is:

> Here are the facts I recorded, the sources I relied on, the judgments I made, the calculation lens I used, and the unresolved questions I encountered.

The system should make disagreement inspectable. A difference in results should be attributable to a source interpretation, classification, valuation date, missing event, ownership assumption, or explicit voluntary practice—not hidden inside a formula.

## 2. Non-negotiable posture

Every public artifact should communicate that:

- Huqúqu'lláh is a matter of individual conscience.
- This project is not institutionally endorsed and cannot determine another person's obligation.
- The authoritative texts take priority over software behavior.
- Threshold comparisons must concern assessable property or accumulation, not classify a person or couple as above or below the threshold.
- No one must disclose financial information to participate in the discourse.
- Reporting must preserve the distinction between voluntary contributions and obligatory amounts, and must not represent voluntary giving as an amount due. Aggregate remittance totals are permitted only when the report provides a clear breakdown of the obligatory and voluntary components.
- The project should direct questions requiring guidance to appointed representatives rather than inventing definitive rulings.

This posture follows the emphasis on conscience and freedom from individual solicitation in the [26 November 2000 message of the Universal House of Justice](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1).

## 3. Methodology taxonomy

The workbench must not place unlike concepts in a single menu of competing “methods.” Use the following taxonomy.

| Layer | Meaning | Examples | Software treatment |
| --- | --- | --- | --- |
| **Authoritative constraint** | A principle stated directly in the authoritative guidance | Initial 19-mithqál threshold; 19% rate; whole-unit treatment; once-only treatment of principal | Always visible; not silently configurable |
| **Bookkeeping lens** | A way to organize the same financial history | Accumulation-of-savings reconciliation; wealth-balance reconciliation; transaction/provenance ledger | May be compared; should reconcile or explain divergence |
| **Individual judgment** | A decision expressly or practically left to conscience | Which expenses are necessary; timing within permitted leeway; joint or individual handling by spouses | Recorded with effective date; rationale is optional |
| **Experimental hypothesis** | A proposed transformation not established as a rule | Translating historical units at today's gold price as a deductible indexed credit | Opt-in research view with warnings and counterexamples |
| **Voluntary practice** | Giving beyond what is presently obligatory | Contributing below the threshold; paying 19% of selected income regardless of threshold | Reported separately from obligation |
| **Software operating assumption** | A technical choice needed to calculate or display | Rate provider; time zone; decimal precision; converted reporting view | Versioned and reproducible; never described as source law |

An “income orientation” and a “wealth orientation” may be bookkeeping lenses over the same history rather than competing substantive laws. Complete, consistently classified data should either reconcile or reveal precisely why they do not.

Approaches that shaped the project but are no longer proposed as the ordinary path should not disappear from the discourse. Record their former purpose, current status, counterexamples, and conditions for reconsideration in [Considered Approaches and Current Posture](considered-approaches.md). “Set aside as a default” does not mean that a personal practice is forbidden or that a later understanding cannot restore it.

## 4. Source-grounded starting constraints

The calculation specification begins with these constraints:

1. Obligatory payment begins when assessable possessions reach the value of 19 mithqáls of gold. [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
2. For metric calculations, the project follows the weight relationship stated in a letter written on behalf of Shoghi Effendi: “One mithqál consists of nineteen nakhuds. The weight of twenty-four nakhuds equals four and three-fifths grammes. Calculations may be made on this basis.” [Application compilation, paragraph 52](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) This gives `19 × 19 ÷ 24 × 4.6 = 69.1916… grams` for the threshold, conventionally reported as approximately 69.2 grams. A generic or regional mithqál conversion must not replace this source-specified relationship.
3. The rate is 19%. [Q&A 89](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10)
4. Assessable value not already counted toward a completed threshold unit—including any carried remainder—accumulates toward the next 19-mithqál unit. Each further complete unit generates a new obligatory amount. A remainder smaller than one unit carries forward but does not by itself generate an obligatory amount. [Q&A 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10)
5. A given principal is subject once; realized profit or subsequent acquisitions become assessable when the prescribed amount is reached. [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
6. Applicable annual expenses, losses, debts, exemptions, ownership, and financial ability must be incorporated rather than appended after calculation. The [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) provides a concise synthesis.
7. If the value of a believer’s assessable property is less than the value of 19 mithqáls of gold, that accumulation does not generate an initial obligatory amount. The believer may nevertheless contribute voluntarily. See paragraph 63 in the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).

   **Derived design consequence:** When a remittance is identified as voluntary, the workbench must preserve that it was voluntary when made and must not report it as an amount then due. The absence of a recorded assessment does not by itself establish that a remittance was voluntary; see [Draft UX and Feature Proposals](draft-ux-and-feature-proposals.md#1-remittance-before-assessment).

A statement that no initial or new obligatory amount arises from a threshold comparison does not reduce or extinguish an obligation already established.

These constraints do not answer every bookkeeping or continuity question, but they prevent a methodology explorer from treating “19% of any selected income” as equivalent to the obligatory calculation.

## 5. Historical assessment units

### 5.1 Intended meaning

Gold can serve as the law-defined calibration for identifying a completed threshold unit at a historical assessment. It is not necessary to claim that gold preserves purchasing power or that every previously assessed currency amount should float with today's gold price.

For a particular assessment context `a`:

- `threshold_weight` is the source-defined weight of 19 Bahá’í mithqáls: `19 × 19 ÷ 24 × 4.6 = 69.1916… grams`, conventionally reported as approximately 69.2 grams of gold.
- `threshold_value(a)` is the supported local-currency value of that weight at the assessment date under a documented rate convention.
- `completed_units(a)` is the count of complete threshold units identified by the assessment after applicable deductions, losses, prior assessed principal, and carried sub-unit remainder have been handled under the selected specification.

The count is a historical result. Its inputs and methodology version must be immutable, even if later corrected through an explicit superseding event.

### 5.2 What the count does not establish

The historical count alone does not determine that:

- Previously assessed principal should be revalued continuously in gold
- Today's gold price defines a current deductible credit
- Payment-date gold can reconstruct assessment-date units
- A current-gold display is the authoritative amount of property already assessed

Those are separate claims requiring explicit status and testing.

### 5.3 Boundary on current-gold research comparisons

The experimental transformation is:

`current indexed view = historical completed units × current threshold value`

An earlier experiment proposed this transformation as a comparative lens. Treating it as a substantive credit against current wealth is stronger: it can shelter genuinely new acquisitions when gold rises or manufacture apparent new wealth when gold falls. The [worked counterexamples](open-questions-and-counterexamples.md#2-historical-state-question-and-indexed-credit-counterexamples) demonstrate both failures.

If explicitly enabled as a research comparison, the interface may show a separately labeled output alongside the ordinary assessment:

- **Current-gold translation under experimental hypothesis**

It must remain clearly experimental and must not overwrite a historical assessment, become the ordinary or recorded obligation, enter allocation, or be presented as deductible assessed principal outside the counterfactual view. The ordinary assessment view should not require this comparison.

## 6. Assessment, obligation, payment, and allocation

Assessment and settlement are different event families.

### Assessment event

An assessment records:

- Assessment date and effective financial period
- Participant or ownership scope
- Native-currency assessable amount
- Completed units and carried sub-unit remainder
- Gold and FX rate evidence used
- Applicable source rules
- Judgment and classification decisions
- Methodology and formula version
- Resulting obligation amount and currency

### Payment event

A payment records:

- Payment date
- Amount and currency remitted
- Intent at remittance: settlement of an identified obligation, settlement intent pending assessment, voluntary contribution, or unresolved
- For a voluntary contribution, future-credit intent: explicitly excluded, preserved for possible future allocation, or unresolved
- Later treatment decisions and allocations, without overwriting the original intent
- Payment channel or receipt reference, if the user elects to keep it
- Conversion evidence when paid in a currency different from the obligation
- Notes and provenance

A remittance may precede assessment. “Settlement intent pending assessment” preserves the person's intention without manufacturing an obligation or granting present obligation credit. A later assessment may support a deliberately confirmed allocation, but it must not trigger one automatically. Lack of a prior assessment must not default the remittance to voluntary. The proposed states, entry flow, later reconciliation, and reporting behavior are described in [Draft UX and Feature Proposals](draft-ux-and-feature-proposals.md#1-remittance-before-assessment).

A user-facing option such as “Do not count this toward any future amount due” may record an explicit exclusion. A separate option such as “Preserve this for possible allocation to a future obligation” records the person's intent and retains the candidate amount, but it does not by itself establish eligibility or reduce a later amount due. Leaving both options unset records unresolved intent. An actual future allocation requires a reviewed source-grounded or explicitly labeled methodological treatment and a deliberate allocation record.

### Assessment-payment allocation

An allocation links settlement value to an obligation. It permits:

- One assessment settled by installments
- One payment allocated across more than one assessment
- Partial settlement
- Later corrections or reversals without rewriting history
- An outstanding balance independent of current gold prices

A payment made after the price of gold has changed does not alter the assessment. Deriving units from `payment ÷ 19% ÷ payment-date threshold value` is invalid when the payment date differs from the assessment date.

Payment reporting should reconcile **total remitted** separately from **credit allocated toward obligations**. The explanation should identify obligatory allocations, voluntary amounts explicitly excluded from future credit, voluntary amounts preserved as candidates for possible later allocation, voluntary amounts whose intent is unresolved, unallocated settlement-intent amounts, corrections or reversals, and any documented currency conversion. No difference should appear as an unexplained residual.

### Incomplete historical records

If only a payment is known, the tool may store an **estimated assessment reconstruction**, but it must retain:

- The original known fact
- The estimation method
- Candidate assessment dates or rate ranges
- Confidence level
- Who entered the estimate and when
- A visible warning that the unit count was inferred, not observed

### Draft, preview, commit, amendment, and deletion

“Just show me what this would look like” is a drafting need, not necessarily a change to historical records. The workbench should distinguish:

- **Draft:** freely editable, undoable, and deletable working data with no required revision history
- **Preview:** calculated consequences of a draft without changing committed records
- **Committed assessment:** a reproducible dated snapshot of inputs, judgments, rates, and results
- **Amendment:** a correction or reconsideration that previews affected later records and, when confirmed, supersedes a committed version without erasing what it previously showed
- **Full deletion:** a separate user-controlled privacy action that removes the selected record and consistently deletes, invalidates, or recalculates dependent results

Ordinary undo may stop at the most recent commit boundary. An attempted in-place edit to an older committed assessment should normally redirect to an amendment flow that distinguishes correcting a fact, reconsidering a judgment, and applying newly available information. A rationale may be supplied, omitted, or marked unknown. Full deletion remains available as a deliberate operation rather than being disguised as an amendment.

## 7. Event and provenance model

Holdings snapshots are useful reconciliations but cannot explain how state changed. The conceptual model should include:

| Record | Purpose |
| --- | --- |
| `Workspace` | Private household or fictional public scenario |
| `Participant` | Person whose individual obligation or joint arrangement is being described |
| `FinancialEvent` | Acquisition, income, expense, transfer, gift, inheritance, disposal, gain, loss, recovery, or correction |
| `Holding` | Current derived position linked to the events that produced it |
| `ClassificationDecision` | Subject/exempt/unresolved status, optional rationale, source, confidence, and effective date |
| `OwnershipInterval` | Owner and share over an effective date range |
| `AssessmentEvent` | Reproducible historical assessment and completed units |
| `Obligation` | Amount arising from an assessment and its settlement status |
| `PaymentEvent` | Actual remittance fact, purpose, and voluntary-credit treatment |
| `PaymentAllocation` | Amount of a payment applied to an obligation |
| `ScenarioDraft` | Freely mutable working state used for previews before commitment |
| `Amendment` | A superseding correction or reconsideration linked to an earlier committed record |
| `RateSnapshot` | Gold or FX observation with provider, instrument, timestamp, unit, and retrieval evidence |
| `MethodologyProfile` | Versioned set of bookkeeping and operating choices |
| `DecisionRecord` | Personal judgment, optional reason and alternatives, and effective date |

Snapshots should reconcile to event history. They should not replace provenance.

### 7.1 Current holdings are not a purification inventory

A `Holding` is a current record of an owned position: its owner or ownership share, category, reported value, valuation evidence, and current classification decision. It does **not** need a row-level `paid`, `purified`, or “already assessed” flag.

The once-only principle is primarily represented by the history of `AssessmentEvent`, `Obligation`, `PaymentEvent`, and `PaymentAllocation` records, together with the carried assessed-principal baseline required by the selected calculation specification. This allows cash that was part of a settled prior assessment to be exchanged for an object without treating the object itself as the carrier of a permanent payment status. A holding's present classification is a separate question from whether an earlier obligation was settled.

Where a particular transfer, replacement, jointly owned item, gift, inheritance, or ownership change makes tracing helpful, the workbench may retain links between a holding and the events or assessments that explain it. Those links are optional explanatory provenance, not required data on every ordinary asset row.

### 7.2 Asset classification, current value, and materiality

The texts name the residence and needed household furnishings as exempt, while stating that the **value** of other forms of property reaches the threshold when it reaches the prescribed amount. See [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9) and [Q&A 42](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9). They do not supply an exhaustive asset catalog, a de-minimis dollar amount, or a formula for dividing a mixed or upgraded item into necessary and unnecessary components.

The workbench should therefore let a person record, for any material holding or group of holdings:

- A current classification: `subject`, `exempt`, or `unresolved`
- An optional rationale, effective date, and any source or consultation note the person elects to keep
- An optional reported current or reconciliation value with its evidence and date
- Whether the line is a single item or an aggregate category

This is a recordkeeping model, not a ruling engine. The current value of a holding is different from its original purchase price, and a decision to aggregate small possessions is a choice of data granularity, not an undocumented declaration that they are exempt.

Examples of the intended handling, not answers for another person:

- A material leisure boat is not a named exemption. The workbench can record it as a current owned asset and expose a person's `subject` or `unresolved` classification and any rationale they choose to record; it must not imply that its classification is an institutional determination.
- Ordinary small possessions, such as pens, need not appear as individual rows. A person may use an `ordinary personal goods` aggregate with a plainly labeled estimate if they wish to include that value. The aggregation must not silently double-count or conceal a value that the selected method treats as relevant.
- A vehicle is not a named exemption. Whether a particular vehicle—including whether a household needs one or more vehicles, or whether a particular configuration is needful—is an individual judgment. When a person records a vehicle as a distinct holding, the workbench should ordinarily retain its whole current value and any optional rationale. The source does not provide a component-splitting formula for, for example, treating $5,000 of desired features separately; a separate component treatment, if a person uses one, is an explicit individual bookkeeping choice rather than a derived rule.

## 8. Partial units and ordinary rounding

The whole-unit gate is a source constraint, not a cosmetic rounding preference. The specification must distinguish:

- A sub-unit assessable remainder carried toward a future complete unit
- Decimal rounding of a currency result
- Rate-source precision
- Timing discretion in settling an already identified obligation
- A voluntary contribution below the obligatory threshold

These must not be collapsed into a user setting called “rounding.”

## 9. Multi-currency strategy

### One explicit primary currency per methodology profile

The simplest methodology profile should identify one primary or functional currency for consolidated assessments. For most people this will ordinarily be the currency in which they live and conduct most of their financial life, but that is a bookkeeping and software choice rather than a currency prescribed by the authoritative guidance.

An assessment spanning other currencies may translate their dated native values into the primary currency using documented rates and purposes. Multiple native-currency subledgers may feed the same consolidated personal history; they must not silently become independent spiritual obligations or conceal that the person's combined assessable possessions complete a threshold unit.

A change of primary currency is prospective and effective-dated. It changes the consolidation convention without relabeling native facts, rewriting earlier assessments, or creating an acquisition event. The appropriate treatment of carried principal and sub-unit remainders at such a transition remains an open specification question.

### Preserve native facts

Every event retains its original amount and currency, and is displayed in that recorded currency by default. A converted reporting view is a labeled derivative, not a rewrite or relabeling of the original fact. Any converted amount must show its rate provenance and purpose, such as:

- Assessment valuation
- Payment conversion
- Period-end reconciliation
- Converted reporting view
- Experimental current-gold translation

For example, a recorded `€1,000` may be accompanied by `≈ $1,085 reporting value` using an explicitly identified `1 EUR = 1.085 USD` rate, source, date, and purpose. The converted value must not appear alone as though the event had been recorded in USD. Aggregates spanning currencies may use a reporting currency only when the conversion convention is visible and the underlying native amounts remain available.

### Avoid silent phantom gains

Converting all historical holdings at current FX can make exchange-rate movement appear to be new acquisition. The system must distinguish:

- Native-currency nominal change
- Realized exchange gain or loss
- Unrealized reporting-currency movement
- Transfer between the owner's own accounts
- Economic acquisition or disposal

Whether and when an FX movement becomes assessable requires a declared source synthesis or judgment. The software must not answer it accidentally through current-rate consolidation.

### Multiple regions and migration

A person may maintain native-currency subledgers feeding one consolidated personal history. Moving countries should normally be represented as a change in residence, functional currency, and reporting view—not as deletion or rebasing of the earlier ledger. Open questions include which rate and date govern cross-currency comparisons and how redenomination, capital controls, or multiple lawful market rates should be documented.

## 10. Ownership and household transitions

The obligation rests on individuals and on property recognized as their own, while spouses may choose to proceed jointly or individually. See paragraphs 59, 71, and 74 in the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).

Joint versus individual handling is therefore not merely a display toggle. The model must preserve:

- Legal and beneficial ownership over time
- Jointly owned shares
- Property controlled or used but not owned
- The owner of an obligation
- The source of a payment
- Gifts or transfers between spouses
- Pre-marital property and pre-existing assessment histories
- Effective dates for marriage, separation, divorce, remarriage, inheritance, and death

The workbench should not manufacture rulings for divorce or second marriages. It should preserve enough history for the person and a knowledgeable adviser to reason about the transition without double assessment or loss of provenance.

## 11. Public explorer and private ledger

### Public methodology explorer

The recommended first public-facing product is an interactive methodology explorer using fictional data. Videos, explainers, and other materials may accompany it, but the current product path does not assume that a static presentation will precede a usable interactive tool.

It supports:

- Guided entry and playback of fictional scenarios
- Side-by-side bookkeeping lenses
- Source and epistemic-status overlays
- Counterexample playback
- Methodology-statement generation
- Export of fictional calculation traces
- Discussion of unresolved questions without collection of personal wealth data

### Private financial ledger

Defer until the project specifies and reviews:

- Threat model and data minimization
- Encryption at rest and in transit
- Key recovery and device loss
- Couple and adviser permissions
- Export, deletion, correction, and audit history
- Logging that does not expose financial content
- A clear boundary excluding payment transmission and compliance monitoring

### Agent-readable diagnostics

A future private ledger may expose a permission-scoped, read-only diagnostic interface—potentially through MCP or an equivalent protocol—so a user can ask questions such as, “Why does my total remitted not equal the credit applied toward obligations?” The interface should return a structured reconciliation and point to the exact records and user-controlled treatments that explain the difference.

This possibility does not authorize agent access by default. It belongs after the privacy and security work for the private ledger and should require explicit user authorization, data minimization, clear workspace scope, revocable access, and no write capability unless separately designed and approved. The same explanation must remain available directly in the product so that an agent is helpful rather than required.

## 12. General-audience accessibility

The repository may preserve technical depth, but the videos, tools, examples, and explainers ultimately shared with others must be understandable to a general Bahá'í audience. They must not assume prior familiarity with accounting, software design, historical currencies, gold pricing, or the conversations that produced this RFC.

Public-facing materials should use progressive disclosure:

1. Begin with what Huqúqu'lláh is, its spiritual and social context, who may have an obligation, and the threshold.
2. Introduce gold as the law-defined threshold measure before discussing historical units or indexed-credit experiments.
3. Demonstrate one initial obligatory assessment in a familiar local currency.
4. Show a below-threshold voluntary contribution next, keeping required payment at zero and allowing its future-credit intent to be explicitly excluded, preserved for possible later allocation, or left unresolved without silently deciding eligibility.
5. Demonstrate the once-only principle across a later period, including genuine additional accumulation toward a further complete unit.
6. Add expenses, losses, delayed settlement, or carried remainders only after those basic examples are clear.
7. Place gold-price counterexamples, alternative carry-forward approaches, multi-currency histories, ownership transitions, provenance, and other experimental hypotheses in optional deeper layers.

Every public artifact should also:

- Define specialized terms at first use and pair them with ordinary-language explanations
- Distinguish “the guidance says,” “this person judged,” and “this experiment tests” without relying only on technical labels
- Prefer concrete examples and visible calculation traces over unexplained formulas
- Provide captions or transcripts for video, text alternatives for essential visuals, and layouts usable at common zoom and text sizes
- Avoid making fluency with financial terminology a condition of participating in the discourse
- Be tested with Bahá'ís who have not followed the project's development; confusion discovered in those sessions becomes design feedback

A public artifact is not ready merely because its calculation is correct. A person unfamiliar with this project should be able to explain, in their own words, why the threshold matters, why gold appears, which parts are authoritative, and which parts are experimental.

## 13. Experience principles

The interface should:

- Lead with study and scope, not an amount due
- Show why each asset or event was classified
- Distinguish fact, source rule, derivation, judgment, and hypothesis visually and in exports
- Permit “unresolved” rather than forcing a false binary decision
- Permit a remittance to be recorded before assessment without classifying it automatically as voluntary or as obligation credit
- Display each recorded amount in its recorded currency by default; preserve original values beside any converted reporting view
- Explain divergences between methods
- Explain differences among total remitted, obligation credit, voluntary excluded amounts, voluntary amounts preserved for possible allocation, unresolved amounts, unallocated amounts, reversals, and currency effects
- Make draft, preview, commit, amendment, undo, and full-deletion states understandable without accounting or software vocabulary
- Use calm, non-pressuring language
- Make voluntary amounts visibly separate from obligations
- Avoid rankings, streaks, reminders framed as delinquency, or social comparison

## 14. Phases

### Phase 0 — Source synthesis and specification

- Review the source-rule matrix
- Track deliberate human review in the [human review checklist](human-review-checklist.md)
- Resolve or explicitly defer open questions
- Normalize schemas and formulas
- Write fictional cases with expected outputs
- Review the historical-rate methodology
- Seek focused consultation on questions requiring guidance

### Phase 1 — Public methodology explorer

- Interactive fictional scenarios only
- Guided scenario entry and state-transition playback
- Source overlays and comparison views
- No personal financial storage
- Plain-language testing with members of the intended general Bahá'í audience

### Phase 2 — Calculation-specification prototype

- Implement only reviewed constraints and labeled hypotheses
- Validate all invariants
- Maintain immutable calculation traces

### Phase 3 — Privacy and security design

- Complete threat model and access model
- Conduct security review before accepting real data

### Phase 4 — Optional private ledger

- Proceed only after Phase 3 acceptance criteria are met

## 15. Definition of specification readiness

Implementation is ready to begin only when:

- Every calculation rule points to a source, derivation, judgment, or hypothesis label
- Assessment and settlement schemas are separate
- Whole-unit and carry-forward behavior have expected tests
- Multi-currency rate purposes are explicit
- Ownership transitions are effective-dated
- Historical reconstructions retain uncertainty
- Alternative lenses reconcile or explain divergence
- The public prototype cannot accept real household data
- Reviewers can reproduce every fictional output from immutable inputs
- General-audience reviewers can identify the threshold, the reason gold appears, and the difference between guidance and experiment without relying on prior project context

Until then, this repository remains an RFC and study aid rather than a calculator specification.
