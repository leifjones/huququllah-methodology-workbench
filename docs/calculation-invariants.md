# Calculation Invariants

**Status:** Acceptance criteria for a future specification; not executable code

**Purpose:** Define failures that must be detected before any calculation engine is trusted

## 1. How to read these invariants

The invariants have three scopes:

- **Source constraint:** behavior directly grounded in authoritative guidance
- **Accounting integrity:** behavior needed to preserve facts and prevent duplicated or manufactured economic events
- **Research and safety:** behavior needed to distinguish hypotheses, uncertainty, privacy, and institutional status

An experimental methodology may intentionally produce a different *view*, but it may not alter historical facts, hide its status, or label its result authoritative.

Unless otherwise stated, examples use fictional data, exact decimal arithmetic, and a fictional assessment-date threshold unit `U = $10,000`. Each row or scenario is an independent data state, not a sequence through time, unless multiple dates are explicitly introduced. In practice, the local-currency value of `U` may vary by currency, assessment date, gold-valuation source, and valuation convention; later invariants test those changes explicitly.

## 2. Threshold and whole-unit invariants

### Invariant 1 — An obligatory amount does not arise below the threshold

**Scope:** Source constraint
**Basis:** [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9), [Q&A 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10), and the [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4)

**Given** assessable property of $9,999 and `U = $10,000`
**When** the obligatory assessment is calculated
**Then** completed units are zero, obligatory principal is zero, and required payment is zero.

**Failure:** Applying 19% to $9,999 and presenting $1,899.81 as due.

### Invariant 2 — Only completed units enter obligatory principal

**Scope:** Source constraint

The following rows are independent cases evaluated under the same fixed value of `U`; they are not successive periods.

| Assessable amount | Completed units | Obligatory principal | Carried remainder | Obligation at 19% |
| ---: | ---: | ---: | ---: | ---: |
| $9,999 | 0 | $0 | $9,999 | $0 |
| $10,000 | 1 | $10,000 | $0 | $1,900 |
| $19,999 | 1 | $10,000 | $9,999 | $1,900 |
| $20,000 | 2 | $20,000 | $0 | $3,800 |

Ordinary currency rounding occurs after the whole-unit rule. It must not be used to round a partial unit upward into an obligation.

### Invariant 3 — Voluntary contribution remains distinct from obligation

**Scope:** Source constraint and accounting integrity
**Basis:** Paragraph 63 of the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3)

**Given** $6,000 below-threshold assessable property and a voluntary $100 contribution marked as explicitly excluded from future obligation credit
**Then** required payment remains zero, total voluntary remitted is $100, and credit allocated toward an obligation is zero.

The voluntary amount must not silently reduce a future obligatory base or be described as payment of an amount due unless a reviewed source-grounded treatment explicitly establishes that consequence. If the explicit-exclusion option is unset, the system records the future-credit treatment as unresolved rather than silently treating the amount as eligible.

## 3. Financial identity invariants

### Invariant 4 — Transfers within the same assessment scope do not create wealth

**Scope:** Accounting integrity

**Given** $1,000 in account A
**When** it is transferred to account B owned by the same person within the same assessment scope
**Then** total property and new acquisition remain unchanged.

**Failure:** Recording the deposit to B as $1,000 of new income while retaining A's withdrawal only as an expense or ignoring it.

### Invariant 5 — Splitting or merging holdings does not alter the result

**Scope:** Accounting integrity

**Given** one $20,000 holding
**When** it is represented as two $10,000 holdings without a change in ownership or classification
**Then** completed units, obligatory principal, and obligation are identical.

### Invariant 5a — Exchanging cash for an owned asset does not make property disappear

**Scope:** Accounting integrity

**Given** $10,000 cash within one assessment scope
**When** it is exchanged for a vehicle with a reported current value of $10,000
**Then** the decrease in cash and increase in the owned vehicle offset in the current property reconciliation. The vehicle's `subject`, `exempt`, or `unresolved` classification is recorded separately; the system must not assume that the purchase is an annual expense merely because cash left an account.

**Failure:** Recording the $10,000 cash outflow as an expense while omitting the acquired vehicle from both holdings and any identified aggregate, without an explicit classification or selected-method treatment.

### Invariant 5b — Aggregating small possessions is transparent

**Scope:** Accounting integrity and individual judgment

**Given** $120 of ordinary small possessions
**When** they are represented as individual rows or as one `ordinary personal goods` aggregate with the same classification
**Then** the selected calculation reaches the same result. The aggregate records its estimate, date, classification, and any optional rationale.

**Failure:** Using aggregation to hide a relevant value, double-count a group and its component rows, or treat an aggregation decision as an authoritative exemption.

### Invariant 6 — Drafts, committed assessments, amendments, and deletion remain distinguishable

**Scope:** Accounting integrity and individual judgment

Draft classifications and scenarios may be edited, undone, or fully deleted without preserving revision history. A preview may calculate consequences without changing a committed record.

Once an assessment is committed, an ordinary edit does not mutate it in place. A correction or reconsideration proceeds through an amendment that shows affected dependent results before confirmation and retains the earlier committed version. The amendment records when it was entered and the date from which it applies; its rationale may be supplied, omitted, or marked unknown.

Full deletion remains a separate user-controlled operation. If a deleted record contributed to an assessment, obligation, payment allocation, or later calculation, the system must delete, invalidate, or recalculate those dependent results consistently and must not leave them appearing valid without their former basis.

## 4. Assessment and settlement invariants

### Invariant 7 — Later market changes do not rewrite a committed unit count

**Scope:** Accounting integrity

**Given** a committed assessment of one completed unit on date A
**When** gold, FX, residence, or display currency later changes
**Then** the date-A assessment still records one completed unit.

A correction may create a superseding amendment linked to the earlier assessment; ordinary changes in rates do not mutate either version. A separate explicit full-deletion operation is governed by Invariant 6.

### Invariant 8 — Delayed payment does not rewrite an assessment

**Scope:** Accounting integrity

**Given:**

- Date-A unit value: $10,000
- Date-A completed units: 1
- Date-A obligation: $1,900
- Date-B unit value at payment: $20,000
- Date-B payment: $1,900

**Then:**

- Historical units remain 1
- Obligation settled is $1,900
- Outstanding balance becomes zero
- Payment-date gold may be retained as payment metadata but produces no replacement unit count

**Failure:** Reconstructing `0.5 unit` from the date-B price.

### Invariant 9 — Installments do not alter assessed principal

**Scope:** Accounting integrity

Paying one $1,900 obligation as one payment or as two $950 installments produces the same assessment, obligation total, and final settlement state.

### Invariant 10 — Allocations conserve value

**Scope:** Accounting integrity

For each payment:

`sum(payment allocations) + unallocated payment balance = payment amount`

For each obligation:

`sum(valid allocations) + outstanding balance = obligation amount`, adjusted only by explicit correction or reversal events.

An allocation cannot exceed either the available payment balance or the obligation balance.

Within one currency, or after applying documented conversions for a shared reporting view, the system must also reconcile:

`total remitted = obligation settlement credit + voluntary explicitly excluded + voluntary unresolved + unallocated settlement-intent amount ± corrections or reversals`

If total remitted differs from credit toward obligations, the interface and any diagnostic API must expose the records and categories producing the difference. “The totals are different” is not a sufficient explanation.

### Invariant 11 — Payment source and obligation owner are separate

**Scope:** Accounting integrity and ownership

A spouse or shared account may supply funds for a payment without silently changing who owns the obligation or the property assessed. Any different treatment requires an explicit ownership or gift event.

## 5. Once-only principal and loss invariants

### Invariant 12 — Previously assessed principal is not assessed twice

**Scope:** Source constraint

**Given** $10,000 principal assessed and settled
**When** the unchanged property remains in the ledger next period
**Then** it is not new assessable principal merely because another snapshot was taken.

A new assessment requires a source-grounded event such as qualifying augmentation, realized profit, recovery beyond prior loss, or transfer to another owner.

The necessary assessment, obligation, settlement, and carried-principal history may be held at an aggregate or event level. A current asset row does not need its own prior-payment or “purified” flag unless an optional link is useful to explain a material transfer or replacement.

### Invariant 13 — Recovery of prior loss is distinguished from augmentation

**Scope:** Source constraint and accounting integrity
**Basis:** [Q&A 44–45](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)

**Given:**

1. Previously assessed property: $100,000
2. Recorded loss: property falls to $80,000
3. Later recovery: property returns to $100,000

**Then** the $20,000 recovery restores the prior position and is not silently labeled new augmentation. A later increase beyond the restored position is separately identifiable.

### Invariant 14 — A change of ownership is not a transfer between the same owner's accounts

**Scope:** Source constraint and ownership

The system must distinguish an internal transfer from a gift, inheritance, sale, or other passage to a new owner. It records the ownership event and applies the recipient's history rather than carrying the former owner's settlement status forward by default.

## 6. Currency and rate invariants

### Invariant 15 — Display currency changes presentation, not historical facts

**Scope:** Accounting integrity

**Given** an assessment stored in USD with documented date-A rates
**When** a user selects EUR as the display currency
**Then** the original USD amount, completed units, assessment date, and obligation remain unchanged. The EUR amount is a labeled conversion with its own rate provenance.

Switching back to USD must reproduce the original stored values, subject only to an explicitly stated display-rounding tolerance.

### Invariant 16 — Rate purpose is explicit

**Scope:** Accounting integrity

Every gold or FX observation identifies its purpose:

- Assessment valuation
- Payment conversion
- Period-end reconciliation
- Current display
- Experimental current-gold translation

A rate captured for one purpose cannot silently replace the rate used for another.

### Invariant 17 — Unrealized FX movement does not silently become acquisition

**Scope:** Source synthesis and accounting integrity

**Given** an unchanged EUR holding whose current USD display value rises solely because EUR appreciates
**Then** the system records a reporting-currency movement, not new income or acquisition, unless a separately documented realization rule and event apply.

The precise treatment of realized currency gain remains a specification question; the invariant prevents accidental resolution by current-rate display logic.

## 7. Indexed-credit research invariants

### Invariant 18 — Current-gold translation cannot overwrite historical state

**Scope:** Research integrity

If one historical unit is shown at today's gold price, the output is labeled a current translation. The stored historical assessment remains unchanged.

### Invariant 19 — Substantive indexed credit is opt-in and labeled experimental

**Scope:** Research integrity

The default source-grounded view may not silently deduct `historical units × current unit value` from present wealth. If a research profile enables that operation, the interface and export must:

- Label it the current-gold indexed-credit hypothesis
- Cite no authority that does not actually establish it
- Show the non-indexed comparison
- Display the gold-rise and gold-fall consequences
- Preserve the same historical unit count in both views

### Invariant 20 — Gold-rise and gold-fall consequences are reproducible

**Scope:** Research integrity

Using the fictional cases in [Open Questions and Counterexamples](open-questions-and-counterexamples.md#2-current-gold-indexed-credit):

- A rise from a $10,000 historical unit to a $20,000 current unit produces a $20,000 experimental credit, not a changed historical count.
- A fall to a $5,000 current unit produces a $5,000 experimental credit, not a new acquisition event.

If the hypothesis changes an obligation result, the divergence must be displayed rather than normalized away.

## 8. Reproducibility and methodology invariants

### Invariant 21 — Every historical assessment is reproducible

**Scope:** Accounting integrity

Reproduction requires immutable access to:

- Assessment scope and owner
- Financial events or opening state
- Exemptions and deductions
- Classification and judgment records
- Gold and FX rate snapshots
- Carried remainder and prior assessed principal
- Methodology and formula version
- Precision rules

Current rates must not affect replay of a historical assessment.

### Invariant 22 — Bookkeeping lenses reconcile or explain divergence

**Scope:** Research integrity

When two lenses process the same complete event history, they must either:

1. Produce the same completed units and obligation, or
2. Identify the exact differing classification, timing rule, missing event, valuation assumption, or hypothesis.

“Different method” is not a sufficient explanation by itself.

### Invariant 23 — Source examples are applied within declared scope

**Scope:** Source synthesis

The 1919 piastre example may test:

- 19% arithmetic
- Expense deduction
- Annual reconciliation
- Deduction of previously assessed principal

It must not make a below-threshold amount obligatory in the specification while Q&A 90 and the codification's whole-unit rule remain applicable. The apparent numerical mismatch is retained as a source-scope note for review.

### Invariant 24 — Every displayed proposition has an epistemic status

**Scope:** Research integrity

Every rule or output is traceable as one of:

- Explicit authoritative constraint
- Authoritative synthesis or guidance
- Derived design rule
- Individual judgment
- Historical inference
- Software operating assumption
- Experimental hypothesis
- Voluntary practice

An output assembled from several layers exposes all of them.

## 9. Ownership and continuity invariants

### Invariant 25 — Ownership changes are effective-dated

**Scope:** Accounting integrity

Marriage, gift, inheritance, separation, divorce, remarriage, and death do not retroactively rewrite ownership. They create effective-dated intervals and transition events.

### Invariant 26 — Switching joint and individual handling does not erase history

**Scope:** Accounting integrity and individual judgment

A prospective change from joint to individual handling, or the reverse, preserves:

- Prior assessments
- Obligation owners
- Payment allocations
- Ownership shares
- Methodology effective dates

The system may generate a transition view but may not redistribute historical units automatically.

### Invariant 27 — Migration is not an acquisition event

**Scope:** Accounting integrity

Changing residence or functional currency changes reporting context. It does not itself create wealth, dispose of assets, or reset prior assessments.

## 10. Uncertainty and safety invariants

### Invariant 28 — Estimated history remains visibly estimated

**Scope:** Research integrity

If an assessment is reconstructed from a payment or opening balance, the record retains method, date range, evidence, author, and confidence. Estimated and observed values cannot share an indistinguishable status.

### Invariant 29 — A public prototype uses fictional data

**Scope:** Privacy safety

No public prototype may accept or retain real household financial data until a threat model, encryption architecture, recovery process, permissions model, export/deletion behavior, and security review have been completed.

### Invariant 30 — No output implies institutional endorsement or compliance status

**Scope:** Spiritual and discourse safety

Every page and export states that this is an independent learning project. The system does not rank people, expose payment histories, issue delinquency warnings, solicit payment, or describe uncertainty as noncompliance.

## 11. Minimum fictional acceptance suite

| Scenario | Primary invariants |
| --- | --- |
| $9,999, $10,000, $19,999, and $20,000 with `U = $10,000` | 1–3 |
| $6,000 with a $100 voluntary contribution under explicitly excluded and unresolved future-credit treatments | 3, 10 |
| Transfer between two accounts of one owner | 4 |
| Split one holding into two rows; exchange cash for an asset; aggregate ordinary small possessions | 5, 5a–5b |
| One assessment paid immediately versus in installments | 7–10 |
| Payment delayed while gold doubles | 7–10, 16 |
| Unchanged assessed property across two periods | 12 |
| Loss to $80,000 and recovery to $100,000 | 13 |
| Gift from one owner to another | 14, 25 |
| USD/EUR display switch with no economic event | 15–17 |
| Gold-indexed credit when gold doubles and halves | 18–20 |
| Annual-surplus and wealth-reconciliation lenses over identical events | 21–22 |
| 1919 piastre arithmetic combined with whole-unit gate | 23 |
| Marriage, divorce, and prospective method change | 25–26 |
| Move between countries with retained foreign assets | 15–17, 27 |
| Payment-only historical migration with uncertain assessment date | 28 |
| Public fictional demo and methodology export | 29–30 |

The calculation specification must supply exact inputs and expected outputs for every row before implementation is considered trustworthy.
