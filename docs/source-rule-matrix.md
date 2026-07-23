# Source-Rule Matrix

**Status:** Working source synthesis for review

**Purpose:** Separate what a source explicitly establishes from what a bookkeeping method, historical inference, or software design derives from it

This matrix is not a substitute for the texts. It is a traceability layer for a future calculation specification and should be reviewed by people familiar with the law of Huqúqu'lláh.

## Status vocabulary

| Label | Meaning |
| --- | --- |
| **Explicit constraint** | The cited text directly addresses the calculation question |
| **Authoritative synthesis** | A codification or later guidance assembles multiple source principles |
| **Worked example** | An example demonstrates a method or relationship but may not restate every applicable constraint |
| **Individual judgment** | The guidance expressly or practically leaves a decision to the believer's conscience |
| **Derived design rule** | A software consequence reasoned from sources; it remains distinguishable from source text |
| **Historical inference** | Context supplied by non-Bahá'í historical evidence; not authoritative guidance |
| **Experimental hypothesis** | A proposition being tested, not a rule attributed to the guidance |

## Matrix

Links in the table point to the full official section containing the cited item.

| Topic | Authoritative source | What the source explicitly establishes | Status | Specification consequence | Scope or remaining question |
| --- | --- | --- | --- | --- | --- |
| **Spiritual and social context** | [Codification preamble](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1) | Huqúqu'lláh connects economic activity with spiritual life, is a means for purification of wealth, remains a matter of individual conscience, and has implications for eliminating extremes of wealth and poverty and distributing resources more equitably. | Authoritative synthesis | Introduce the law's spiritual and social setting before presenting thresholds or calculations. Do not frame the workbench as a tax, collection mechanism, or compliance system. | Do not imply that one software methodology exhausts the law's spiritual meaning or that an individual's finances are open to inspection. |
| **Initial threshold** | [Kitáb-i-Aqdas, Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Codification III.2.1](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | The basic assessable sum is the value of 19 mithqáls of gold. | Explicit constraint | An obligatory assessment cannot arise below the first completed threshold unit. | Rate source, market convention, date, and local-currency translation still require specification. |
| **Bahá’í mithqál weight** | [Kitáb-i-Aqdas, Q&A 23](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Application compilation, paragraph 52](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3); [Codification III.2.1](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | One mithqál is 19 nakhuds, and 24 nakhuds equal 4.6 grams. Therefore 19 Bahá’í mithqáls equal `19 × 19 ÷ 24 × 4.6 = 69.1916… grams`, conventionally reported as approximately 69.2 g. | Explicit definition and authoritative guidance | Metric conversions must use the source-specified nakhud relationship rather than a generic or regional mithqál value. Preserve the exact relationship as the calculation basis and treat 69.2 g as its rounded display. | Decimal precision and display-rounding conventions still require specification. |
| **Rate** | [Q&A 89](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10) | Computation is based on nineteen out of one hundred. | Explicit constraint | Apply 19% to the assessable principal selected under the whole-unit rule. | Do not confuse 19% with one nineteenth. |
| **Whole-unit treatment** | [Q&A 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10); [Codification III.2.1.2](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | An amount beyond a completed nineteen remains exempt until it reaches a further nineteen; calculation is on whole units. | Explicit constraint and authoritative synthesis | Carry a sub-unit remainder without labeling an obligation due. A below-threshold contribution, if any, is voluntary and separate. | The data representation for carried remainders needs a normalized formula. |
| **Once-only principal** | [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Application compilation, paragraph 50](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | A given principal is not repeatedly assessed after Huqúq has been paid on it; a transfer to another person changes the situation. | Explicit constraint | Preserve assessment, obligation, and settlement history together with the carried principal baseline needed to avoid double assessment. Links from a current holding to that history may be kept for material transfers or replacements, but are not a required “purified” flag on every asset row. | What aggregate or event-linked representation best survives currency and ownership changes remains open. |
| **Subsequent acquisition and realized profit** | [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Kitáb-i-Aqdas note 125](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/15) | Subsequent realized profit or income creates further liability when it augments possessions by at least another prescribed amount. | Explicit constraint | Distinguish new acquisition and realized profit from transfers, reporting-currency changes, and recovery of prior loss. | Treatment of particular FX events requires further study. |
| **Gold-price movement without economic augmentation** | [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Kitáb-i-Aqdas note 125](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/15); [Application compilation, paragraphs 50 and 72](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3); [Codification III.2.2, III.2.4–5](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | The sources connect further liability with what accrues to principal, income after expenses, profit that adds to capital, subsequently acquired possessions, realized appreciation, and augmentation beyond a restored loss. They do not directly address unchanged cash gaining value relative to gold. | Authoritative synthesis supporting a derived design rule | In the provisional single-primary-currency lens, a gold-price movement alone does not create an augmentation event when nominal assessable property is unchanged and there is no acquisition, income, realized profit, realized appreciation, recovery beyond prior loss, or ownership event. A current-gold indexed view may display a different experimental result but may not silently create an economic event. | This synthesis is not an explicit ruling about currency or gold-price movements. Multi-currency holdings, FX realization, physical gold, inflation, and changes of primary currency remain open. |
| **Annual expenses and accumulation of savings** | [Application compilation, paragraphs 45, 48–49, 72](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | Necessary annual expenses are deductible; practical computation should account for accumulated savings rather than isolating each year so that losses and later investment results can be recognized. | Guidance and worked example | Support annual reconciliation as a bookkeeping lens over a continuing history. Record the individual's expense judgments. | The 1919 piastre example illustrates this lens but does not visibly apply the separate whole-unit gate; see below. |
| **Loss and recovery** | [Q&A 44–45](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Codification III.2.5](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | Recovery to a previously assessed amount after loss does not by itself trigger a second payment; liability resumes after loss is made good and possessions are augmented. | Explicit constraint and synthesis | Model loss and recovery as events, not merely current snapshots. | Asset-specific versus aggregate loss tracking needs specification and review. |
| **Gifts and inheritances** | [Application compilation, paragraphs 60 and 74](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3); [Codification III.2.3](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | A gift or bequest augments the recipient's possessions; transfer of ownership can make property assessable to its new owner. | Guidance and synthesis | Record donor, recipient, ownership-transfer date, value evidence, and recipient's assessment history. | Exempt property and difficult valuation cases require their own rationale. |
| **Unrealized appreciation** | [Codification III.2.4](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4); [Application compilation, paragraph 67](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | Increase in property value is not payable until realized; certain possessions need not be brought into account immediately and become assessable when sold. | Authoritative synthesis and guidance | Separate unrealized valuation views from realization events. | Whether a particular currency conversion constitutes realization is not resolved by software convenience. |
| **Debts and ability to pay** | [Codification III.2.6–7](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4); [Application compilation, paragraph 71](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | Debts take precedence, and payment depends on financial ability; timing has leeway. | Authoritative synthesis and guidance | Assessment, obligation, and settlement timing must be separate. Record relevant debt facts and payment status. | The individual applies the guidance to specific circumstances. |
| **Needful residence, furnishings, and equipment** | [Q&A 42](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9); [Q&A 95](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10); [Codification III.1](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | The residence and needful household, business, and agricultural equipment are exempt. | Explicit constraint | Permit item-level or aggregate-category classification with effective date and optional rationale. Record current-value evidence separately from original cost. | What is “needful” is left to individual judgment; the sources do not provide a de-minimis tracking amount or a component-splitting formula for mixed or upgraded items. |
| **Ownership versus control** | [Application compilation, paragraph 59](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | Huqúq applies to possessions recognized as one's own, not property merely controlled or used. | Guidance | Store ownership separately from account access, control, use, and payment source. | Legal and beneficial ownership may differ across jurisdictions. |
| **Spouses: joint or individual** | [Application compilation, paragraphs 59, 71, and 74](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3); [Codification III.3.7](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) | Spouses may choose to honor their obligations jointly or individually, while ownership remains relevant. | Guidance and individual judgment | Use effective-dated ownership and methodology decisions; do not implement joint/individual as a retrospective display toggle. | Divorce, remarriage, and transitions between methods require preserved history and may call for guidance. |
| **Freedom to devise a method** | [Application compilation, paragraph 66](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | The Universal House of Justice did not envisage issuing one specific method; believers may devise methods based on the texts and examples. | Enabling guidance | Permit multiple bookkeeping lenses while retaining authoritative constraints and traceability. | Freedom of method does not make a voluntary practice or experimental hypothesis an authoritative constraint. |
| **Voluntary contribution below threshold** | [Application compilation, paragraph 63](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) | A person who does not accumulate assessable property equal to 19 mithqáls has no obligation, but may contribute voluntarily. | Explicit guidance | Required amount below threshold is zero. Store any voluntary amount under a distinct category. Record future-credit intent as explicitly excluded, preserved for possible future allocation, or unresolved without treating intent as established eligibility. | The interface must not imply that voluntary generosity changes the threshold rule. Whether and under what conditions such a contribution may be credited toward a later obligation requires focused review; neither an unset exclusion nor an affirmative intent establishes eligibility. |
| **Conscience and non-solicitation** | [Universal House of Justice, 26 November 2000](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1) | Payment is a matter of conscience and individuals are not to be pressured or solicited. | Authoritative guidance | No compliance scoring, public disclosure, individualized pressure, or delinquency language. | Privacy and discourse safeguards must be reviewed before any real-data ledger. |

## The 1919 piastre example

### Documentary form and immediate question

Paragraph 49 of the [application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3) reports the substance of an interview with ‘Abdu'l-Bahá on 26 November 1919, in a note in Shoghi Effendi's handwriting from about 1920. The question asked whether Huqúq was calculated on net or gross income.

The reported explanation uses three relevant figures:

- A rate illustration in which 19 is taken from 100 piastres remaining after expenses
- A continuing-history example beginning with 1,000 piastres and later 2,000 piastres
- A third-year reconciliation in which 19% is paid on a 500-piastre increment

The word “may” in that passage describes a hypothetical balance—for example, what the person's total *may be*. The calculation itself is expressed procedurally: the person deducts the prior assessed amount and pays on the difference. It is not phrased as a voluntary option.

### What the example clearly illustrates

- The 19% rate
- Deduction of necessary expenses
- Reconciliation against principal on which Huqúq was already paid
- The once-only character of that previously assessed amount
- A continuing wealth history rather than a tax on the entire balance every year

### Historical-currency context

The Bahá'í source does not identify the currency convention. The most likely contextual reading is the Egyptian piastre then used in Palestine. A [Harvard history of Palestinian money](https://dash.harvard.edu/entities/publication/73120378-c8c2-6bd4-e053-0100007fdf3b) and a [United Nations historical note](https://www.un.org/unispal/document/auto-insert-211494/) document the period's currency setting.

A contemporary Egyptian 100-piastre gold coin is catalogued at 8.5 g and .875 fineness, or 7.4375 g of fine gold. See the [NGC/NumisMaster coin record](https://www.ngccoin.com/price-guide/world/egypt-100-piastres-km-324-1335-1916-cuid-35324-duid-101919). Using that coin as a reference and the source-defined threshold of `19 × 19 ÷ 24 × 4.6 = 69.1916… g` gives:

| Amount | Reference fine-gold equivalent | Approximate threshold units |
| ---: | ---: | ---: |
| 100 piastres | 7.4375 g | 0.107 |
| 500 piastres | 37.1875 g | 0.537 |
| ≈930.3 piastres | 69.1916… g | 1.000 |
| 1,000 piastres | 74.375 g | 1.075 |

This is a **historical inference**, not a conversion stated in the authoritative passage. Wartime convertibility, multiple circulating currencies, and local exchange practice limit the precision of the comparison. It nevertheless shows why the simplified 100- and 500-piastre numbers deserve a scope note.

### Synthesis for this workbench

The example's arithmetic does not visibly apply the whole-unit gate, especially when it applies 19% to the later 500-piastre increment. That is a genuine textual and numerical tension to document. It is not a sufficient basis for treating the threshold as optional because the sources directly answering the threshold question are explicit:

- [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9) identifies the initial basic sum.
- [Q&A 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10) states that an increase is exempt until it reaches a further nineteen.
- [Note 125](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/15) restates initial and subsequent threshold treatment.
- The [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4) expressly combines whole-unit treatment with deduction of annual expenses.

Accordingly, the current specification posture is:

1. Apply the explicit initial and further-unit threshold constraints.
2. Use the 1919 example to inform annual reconciliation, expense deduction, the 19% rate, and once-only principal.
3. Do not treat any one worked example as a complete executable algorithm when other directly applicable rules are stated elsewhere.
4. Preserve the apparent mismatch as a source-scope question for study and consultation. Any tentative resolution should retain its reasoning, provenance, and uncertainty; it must not become a fabricated authoritative ruling or a blocker to acknowledging the threshold.

## Review questions

1. Does each row accurately distinguish direct statement from derived consequence?
2. Are any source passages needed that materially change the current synthesis?
3. Is the proposed treatment of historical assessment units consistent with the once-only principle without assuming indexed credit?
4. What rate convention should determine a local-currency threshold at an assessment date?
5. Which ownership and cross-currency questions should be explored further through study, worked examples, and consultation, and which may also warrant focused consultation with an appointed representative before calculation behavior is specified?
