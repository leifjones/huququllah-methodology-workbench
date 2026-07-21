# Open Questions and Counterexamples

**Status:** Research backlog with worked fictional cases

**Purpose:** Expose where a proposed representation or transformation changes the result before it becomes software behavior

## 1. Established constraints versus open questions

The existence of the threshold is **not** an open question in this project. The authoritative guidance establishes:

- An initial threshold equal in value to 19 mithqáls of gold; using the source-specified relationship of one mithqál to 19 nakhuds and 24 nakhuds to 4.6 grams, this is `19 × 19 ÷ 24 × 4.6 = 69.1916… grams` (approximately 69.2 g). See [application compilation, paragraph 52](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).
- A 19% rate
- Whole-unit treatment for initial and further increments
- Once-only treatment of a given principal
- A distinction between obligatory payment and voluntary contribution below the threshold

See [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9), [Q&A 89–90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10), and the [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4).

The open questions concern how a historical, multi-currency, changing-ownership ledger preserves and applies those constraints without adding unstated rules.

## 2. Historical-state question and indexed-credit counterexamples

### 2.1 What remains open

After a historical assessment, the durable state might preserve native-currency principal, property provenance and transformations, completed nineteen-mithqál units, or a linked combination. That representation question remains open.

The indexed-credit design question does not remain open: translating historical units at today's gold price and deducting the result from present assessable wealth is excluded from the ordinary calculation and retained only as an explicitly enabled counterfactual research view. See [Considered Approaches and Current Posture](considered-approaches.md#2-current-gold-indexed-credit).

Recording historical units and using their current translation as deductible principal are different operations. The following cases show why they must remain separate.

### 2.2 Worked counterexamples

In both cases, one historical threshold unit is worth **$10,000**; the person has **$10,000** of assessable property, which is assessed and settled; and that property is retained.

| Gold movement and later event | Historical-principal result | Current-gold indexed-credit result | Consequence |
| --- | --- | --- | --- |
| **Gold rises:** a current unit becomes **$20,000**; the person acquires **$20,000**; total property is **$30,000** | $10,000 previously assessed; $20,000 new—one complete current unit | $20,000 indexed credit; only $10,000 appears new | Shelters $10,000 of the new acquisition and delays the complete unit |
| **Gold falls:** a current unit becomes **$5,000**; no acquisition, profit, or transfer occurs; property remains **$10,000** | $10,000 previously assessed; $0 new | $5,000 indexed credit; $5,000 appears new—one complete current unit | Manufactures an apparent increment without an economic event |

These cases establish that using a current translation as deductible credit can change a substantive result. They do not challenge recording historical unit counts or displaying a clearly labeled current translation as a counterfactual research view.

## 3. Assessment and payment occur at different times

### 3.1 Delayed-payment counterexample

1. On assessment date A, one threshold unit is **$10,000**.
2. One unit is assessed, producing a **$1,900** obligation.
3. Payment is delayed until date B.
4. On date B, one threshold unit is **$20,000**.
5. The person pays the original $1,900 obligation in full.

If the system reconstructs historical units from the payment using the date-B price, it obtains:

`$1,900 ÷ 19% ÷ $20,000 = 0.5 unit`

The historical assessment was one unit, not half a unit. The later payment price cannot rewrite it.

### 3.2 Required separation

The ledger therefore needs distinct records for:

- Assessment inputs and completed units
- Obligation amount and currency
- Payment fact
- Amount allocated from the payment to the obligation
- Outstanding balance

One assessment may have several payments, and one payment may settle several assessments. Neither relationship changes the original unit count.

### 3.3 Historical records with only a payment

Many existing ledgers will know the payment date and amount but not the original assessment date or inputs. The tool must not manufacture precision. Open choices include:

- Record the payment without a reconstructed unit count
- Store a range based on plausible assessment dates
- Permit a user-supplied estimated assessment with optional rationale
- Mark a migrated gold-equivalent value as payment-date metadata only

Every reconstruction needs provenance and confidence.

## 4. The 1919 piastre source-scope case

### 4.1 Why it drew attention

Paragraph 49 of the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) reports the substance of an interview with ‘Abdu'l-Bahá on 26 November 1919. It uses 100 piastres to illustrate the 19% rate and later applies 19% to a 500-piastre difference in a multi-year example.

The “may” in the passage qualifies a hypothetical total that the person may possess. The next steps are stated procedurally: prior assessed principal is deducted and 19% is paid on the 500-piastre difference. The payment step is not worded as “may contribute” or “can pay.”

### 4.2 Likely historical magnitude

The source does not define its piastre. Under the most likely Egyptian-currency reading for Palestine in 1919, a contemporary 100-piastre gold coin provides a 7.4375 g fine-gold reference. Historical context is available from a [Harvard dissertation](https://dash.harvard.edu/entities/publication/73120378-c8c2-6bd4-e053-0100007fdf3b), a [United Nations note](https://www.un.org/unispal/document/auto-insert-211494/), and the [NGC/NumisMaster record for the 1916 coin](https://www.ngccoin.com/price-guide/world/egypt-100-piastres-km-324-1335-1916-cuid-35324-duid-101919).

| Amount | Reference fine gold | Approximate source-defined threshold units |
| ---: | ---: | ---: |
| 100 piastres | 7.4375 g | 0.107 |
| 500 piastres | 37.1875 g | 0.537 |
| 1,000 piastres | 74.375 g | 1.075 |

This comparison is contextual, not authoritative, and exact wartime exchange practice is uncertain. On that likely reading, however, both the 100-piastre rate illustration and the 500-piastre later increment are below one complete threshold unit.

### 4.3 Current synthesis

The passage is a real numerical counterpoint worth documenting, but not a persuasive route around the threshold:

- Its immediate question concerns net versus gross income.
- It reports the substance of an oral explanation rather than presenting a normalized specification.
- It clearly illustrates rate, expense deduction, annual reconciliation, and once-only principal.
- It does not mention the threshold or explain how sub-unit remainders interact with the example.
- [Q&A 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10) directly answers that interaction and says an increment remains exempt until a further nineteen.
- The later [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) retains both annual expense treatment and the whole-unit rule.

The workbench should therefore apply the explicit threshold and use the piastre passage within its demonstrated scope. The mismatch remains visible as a consultation note; it is not a blocking ambiguity about whether an obligatory threshold exists.

## 5. Multiple currencies and movement between countries

### 5.1 Preserving native histories

A person may own assets and receive income in several currencies. Converting the entire history into today's reporting currency can create phantom changes. The event record should retain:

- Original amount and currency
- Date and economic purpose
- Owner
- Classification and any optional rationale
- Any rate used, with its purpose and source

Native-currency subledgers can feed a consolidated personal view without becoming separate spiritual obligations. Whether a particular consolidation method is appropriate remains a methodology question.

### 5.2 Open currency questions

- Which date governs conversion when several currencies jointly complete a threshold unit?
- Which rate is appropriate where official, commercial, and parallel markets coexist?
- Does an unrealized reporting-currency gain remain merely presentational?
- What event counts as realization when one currency is exchanged for another?
- How should hyperinflation, redenomination, currency collapse, or capital controls be recorded?
- How should physical gold be distinguished from gold used only as a threshold calibration?

### 5.3 Moving countries

Migration should not overwrite the earlier ledger. It should create effective-dated changes in residence, functional currency, rate convention, and reporting view. Open questions include:

- Whether prior assessed principal continues in native currency, historical units, property provenance, or a combination
- How a new functional currency should translate carried sub-unit remainders
- How to avoid treating a coordinate change as an economic acquisition
- How to compare assets remaining in the former country with assets acquired in the new one

## 6. Ownership, marriage, divorce, and remarriage

The guidance distinguishes ownership from mere control and permits spouses to proceed jointly or individually. See paragraphs 59, 71, and 74 of the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).

### 6.1 Marriage

Questions to preserve rather than answer silently:

- What assessment histories does each spouse bring into the marriage?
- Which property remains individually owned, becomes jointly owned, or is gifted?
- Is a joint method prospective, or does the couple intend to reconstruct prior periods?
- How are payments sourced from one spouse but allocated to another's obligation recorded?
- How are mixed-faith households and civil community-property rules represented?

### 6.2 Divorce

- Does division of joint property represent allocation of already owned shares, a change of hands, or both?
- How are prior joint assessments and payments attributed after separation?
- How can each resulting ledger avoid double assessment while retaining evidence?
- Which civil-law ownership effects take precedence in the factual record?

The software must record the transition and expose the question. It must not invent a doctrinal answer.

### 6.3 Second marriages

- How do two independent histories enter a new joint arrangement?
- What if one person's property has been assessed and the other's has not?
- How should jointly acquired property link to pre-existing individual bases?
- Can the couple change methods prospectively without rewriting earlier events?

### 6.4 Death and inheritance

Death introduces estate obligations and later ownership transfer to heirs. A future specification needs separate states for:

- The deceased person's remaining obligation
- Estate settlement
- Exempt and assessable property
- Transfer date and recipient
- The recipient's new assessment history

## 7. Trustworthy baseline initialization

Many users will lack a complete event history. Possible initialization modes are:

| Mode | Description | Required warning |
| --- | --- | --- |
| **Documented history** | Reconstruct from dated records and rate evidence | Missing periods still identified |
| **Opening balance with provenance** | Record a starting assessment state supported by prior ledger totals | Does not claim asset-level reconstruction |
| **Estimated range** | Preserve minimum and maximum plausible prior assessed principal or units | Cannot be displayed as exact |
| **Prospective-only experiment** | Begin recording now without asserting that earlier obligation is settled | Not a historical clearance statement |

The user should be able to revise an uncommitted estimate freely or amend a committed estimate with a preview of dependent effects. An amendment may preserve the earlier committed version while making the revision operative; a rationale is optional. Full deletion remains a separate user-controlled action whose dependent effects must be resolved consistently.

## 8. Questions for focused consultation

The most useful consultation questions are narrow and testable:

1. What should remain invariant when previously assessed fiat principal crosses currencies or jurisdictions?
2. Does any authoritative guidance support current-gold translation as a substantive credit rather than a display?
3. What valuation date is appropriate when the economic event, assessment, and payment occur on different dates?
4. How should carried sub-unit remainder be represented across currency changes?
5. What principles should guide allocation of prior joint history after divorce or a move to individual handling?
6. Can a voluntary contribution ever be credited toward a later obligation, and if so, under what conditions and documentation?
7. Is the proposed scope treatment of the 1919 piastre example sound?

Answers should be added to the source-rule matrix with their provenance and date, not absorbed invisibly into a formula.
