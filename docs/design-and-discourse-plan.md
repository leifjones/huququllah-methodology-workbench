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
- No one must disclose financial information to participate in the discourse.
- A voluntary contribution and an obligatory amount are different concepts and must never be merged in reporting.
- The project should direct questions requiring guidance to appointed representatives rather than inventing definitive rulings.

This posture follows the emphasis on conscience and freedom from individual solicitation in the [26 November 2000 message of the Universal House of Justice](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1).

## 3. Methodology taxonomy

The workbench must not place unlike concepts in a single menu of competing “methods.” Use the following taxonomy.

| Layer | Meaning | Examples | Software treatment |
| --- | --- | --- | --- |
| **Authoritative constraint** | A principle stated directly in the authoritative guidance | Initial 19-mithqál threshold; 19% rate; whole-unit treatment; once-only treatment of principal | Always visible; not silently configurable |
| **Bookkeeping lens** | A way to organize the same financial history | Accumulation-of-savings reconciliation; wealth-balance reconciliation; transaction/provenance ledger | May be compared; should reconcile or explain divergence |
| **Individual judgment** | A decision expressly or practically left to conscience | Which expenses are necessary; timing within permitted leeway; joint or individual handling by spouses | Recorded with rationale and effective date |
| **Experimental hypothesis** | A proposed transformation not established as a rule | Translating historical units at today's gold price as a deductible indexed credit | Opt-in research view with warnings and counterexamples |
| **Voluntary practice** | Giving beyond what is presently obligatory | Contributing below the threshold; paying 19% of selected income regardless of threshold | Reported separately from obligation |
| **Software operating assumption** | A technical choice needed to calculate or display | Rate provider; time zone; decimal precision; display currency | Versioned and reproducible; never described as source law |

An “income orientation” and a “wealth orientation” may be bookkeeping lenses over the same history rather than competing substantive laws. Complete, consistently classified data should either reconcile or reveal precisely why they do not.

## 4. Source-grounded starting constraints

The calculation specification begins with these constraints:

1. Obligatory payment begins when assessable possessions reach the value of 19 mithqáls of gold, approximately 69.2 grams. [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
2. The rate is 19%. [Q&A 89](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10)
3. Amounts above a completed unit remain exempt until a further complete unit is reached. [Q&A 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10)
4. A given principal is subject once; realized profit or subsequent acquisitions become assessable when the prescribed amount is reached. [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
5. Applicable annual expenses, losses, debts, exemptions, ownership, and financial ability must be incorporated rather than appended after calculation. The [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) provides a concise synthesis.
6. Someone below the assessable threshold has no obligation, although a voluntary contribution is possible. See paragraph 63 in the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).

These constraints do not answer every bookkeeping or continuity question, but they prevent a methodology explorer from treating “19% of any selected income” as equivalent to the obligatory calculation.

## 5. Historical assessment units

### 5.1 Intended meaning

Gold can serve as the law-defined calibration for identifying a completed threshold unit at a historical assessment. It is not necessary to claim that gold preserves purchasing power or that every previously assessed currency amount should float with today's gold price.

For a particular assessment context `a`:

- `threshold_weight` is 19 mithqáls, approximately 69.2 grams of gold.
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

### 5.3 Current-gold indexed-credit hypothesis

The experimental transformation is:

`current indexed view = historical completed units × current threshold value`

It may be useful as a comparative display. Treating it as a substantive credit against current wealth is stronger: it can shelter genuinely new acquisitions when gold rises or manufacture apparent new wealth when gold falls. The worked examples are in [Open Questions and Counterexamples](open-questions-and-counterexamples.md#2-current-gold-indexed-credit).

The interface must therefore show two separately labeled outputs:

- **Historical units recorded**
- **Current-gold translation under experimental hypothesis**

No current-gold translation may overwrite the original assessment or silently enter an obligation calculation.

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
- Payment channel or receipt reference, if the user elects to keep it
- Conversion evidence when paid in a currency different from the obligation
- Notes and provenance

### Assessment-payment allocation

An allocation links settlement value to an obligation. It permits:

- One assessment settled by installments
- One payment allocated across more than one assessment
- Partial settlement
- Later corrections or reversals without rewriting history
- An outstanding balance independent of current gold prices

A payment made after gold has moved does not change the assessment. Deriving units from `payment ÷ 19% ÷ payment-date threshold value` is invalid when the payment date differs from the assessment date.

### Incomplete historical records

If only a payment is known, the tool may store an **estimated assessment reconstruction**, but it must retain:

- The original known fact
- The estimation method
- Candidate assessment dates or rate ranges
- Confidence level
- Who entered the estimate and when
- A visible warning that the unit count was inferred, not observed

## 7. Event and provenance model

Holdings snapshots are useful reconciliations but cannot explain how state changed. The conceptual model should include:

| Record | Purpose |
| --- | --- |
| `Workspace` | Private household or fictional public scenario |
| `Participant` | Person whose individual obligation or joint arrangement is being described |
| `FinancialEvent` | Acquisition, income, expense, transfer, gift, inheritance, disposal, gain, loss, recovery, or correction |
| `Holding` | Current derived position linked to the events that produced it |
| `ClassificationDecision` | Subject/exempt/unresolved status, rationale, source, confidence, and effective date |
| `OwnershipInterval` | Owner and share over an effective date range |
| `AssessmentEvent` | Reproducible historical assessment and completed units |
| `Obligation` | Amount arising from an assessment and its settlement status |
| `PaymentEvent` | Actual remittance fact |
| `PaymentAllocation` | Amount of a payment applied to an obligation |
| `RateSnapshot` | Gold or FX observation with provider, instrument, timestamp, unit, and retrieval evidence |
| `MethodologyProfile` | Versioned set of bookkeeping and operating choices |
| `DecisionRecord` | Personal judgment, reason, alternatives considered, and effective date |

Snapshots should reconcile to event history. They should not replace provenance.

## 8. Partial units and ordinary rounding

The whole-unit gate is a source constraint, not a cosmetic rounding preference. The specification must distinguish:

- A sub-unit assessable remainder carried toward a future complete unit
- Decimal rounding of a currency result
- Rate-source precision
- Timing discretion in settling an already identified obligation
- A voluntary contribution below the obligatory threshold

These must not be collapsed into a user setting called “rounding.”

## 9. Multi-currency strategy

### Preserve native facts

Every event retains its original amount and currency. A reporting currency is a view, not a rewrite. Rate snapshots retain their provenance and purpose, such as:

- Assessment valuation
- Payment conversion
- Period-end reconciliation
- Presentational display
- Experimental current-gold translation

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

The recommended first product uses fictional data and supports:

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

## 12. General-audience accessibility

The repository may preserve technical depth, but the videos, tools, examples, and explainers ultimately shared with others must be understandable to a general Bahá'í audience. They must not assume prior familiarity with accounting, software design, historical currencies, gold pricing, or the conversations that produced this RFC.

Public-facing materials should use progressive disclosure:

1. Begin with what Huqúqu'lláh is, its spiritual and social context, who may have an obligation, and the threshold.
2. Introduce gold as the law-defined threshold measure before discussing historical units or indexed-credit experiments.
3. Demonstrate one simple fictional example in a familiar local currency.
4. Add expenses, prior payments, or carried remainders only after the basic example is clear.
5. Place multi-currency histories, ownership transitions, provenance, and experimental hypotheses in optional deeper layers.

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
- Preserve original values beside converted views
- Explain divergences between methods
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

- Fictional scenarios only
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
