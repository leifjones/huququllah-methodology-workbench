# Draft UX and Feature Proposals

**Status:** Pre-specification product proposal; not an authoritative source rule, approved calculation rule, or implemented feature

**Purpose:** Explore how an interactive workbench could preserve financial facts, user intent, uncertainty, and later reconciliation without forcing premature classifications

The authoritative sources and the project’s source-grounded synthesis constrain product behavior, but they do not prescribe screens, data fields, prompts, or interaction flows. Each proposal in this document must therefore distinguish:

- **Source-grounded fact or constraint**
- **Derived design requirement**
- **Proposed interaction**
- **Unresolved product or methodology question**

A proposal may be demonstrated with fictional data in the public methodology explorer before any private ledger accepts real financial information.

## 1. Remittance before assessment

### 1.1 User need

A believer may remit money to Huqúqu’lláh before calculating assessable property or identifying an exact obligatory amount, intending to reconcile the payment later.

The known fact is the remittance. The person’s intent may also be known. An assessment, obligation, and allocation do not yet exist merely because money was remitted.

This case must not be collapsed into either:

- a voluntary contribution below the threshold, or
- settlement credit toward an obligation that has not yet been identified.

### 1.2 Proposed state separation

| State | What it records | What it does not establish |
| --- | --- | --- |
| **Remittance fact** | Amount, native currency, payment date, and optional receipt or channel | That an obligation existed or was settled |
| **Intent at remittance** | What the person understood or intended when making the payment | Eligibility for obligation credit |
| **Assessment** | A dated calculation of assessable property, completed units, and resulting obligation | That any earlier payment is automatically allocated |
| **Allocation** | A deliberate link applying payment value to an identified obligation | A rewrite of the original payment or intent |
| **Later treatment decision** | A subsequent decision about an unmatched or excess amount | That the person held that later understanding on the payment date |

Threshold state, obligation state, payment state, and allocation state remain separate.

### 1.3 Proposed intent choices

When recording a remittance, the interface should support at least these states:

| Plain-language choice | Recorded intent | Immediate obligation credit |
| --- | --- | ---: |
| “I had already calculated an amount due.” | Settlement of an identified obligation; prompt to link or record it | Only the amount deliberately allocated |
| “I intended this toward whatever amount I would calculate later.” | Settlement intent pending assessment | $0 until deliberate allocation |
| “This was voluntary regardless of what was due.” | Voluntary contribution | $0 unless a later treatment is separately established |
| “I’m not sure.” | Unresolved | $0 |

The product may require one recorded state for deterministic behavior, but it must permit **unresolved** rather than requiring false certainty. Lack of an assessment must never default the remittance to voluntary.

### 1.4 Proposed entry flow

The interface may begin with:

> When you made this payment, had you already calculated an amount due?

Possible responses:

1. **Yes—link or record that obligation.**
2. **No—I intended this toward whatever amount I would calculate later.**
3. **No—this was voluntary regardless of what was due.**
4. **I’m not sure.**

The screen should explain that recording intent does not itself decide whether an obligation existed or whether the payment receives obligation credit.

A person who chooses settlement intent pending assessment may:

- Save the remittance and assess later
- Begin a draft assessment
- Link an assessment that has not yet been entered
- Leave notes or evidence without completing a calculation

### 1.5 Later assessment and allocation

When a later assessment is committed, the workbench may identify compatible unallocated settlement-intent payments and offer an allocation preview. It must not allocate them automatically.

The person should be able to:

- Allocate all or part of a payment to the new obligation
- Allocate one payment across multiple identified obligations
- Leave all or part unallocated
- Record necessary currency-conversion evidence
- Decline a suggested match
- Preserve an unresolved state

If the later obligation is smaller than the remittance, only the deliberately allocated portion receives obligation credit. The remainder keeps its existing state until a later treatment is recorded.

If the later assessment produces no obligation, the original settlement intent remains part of the historical record. The workbench may offer later treatment choices, but it must not rewrite the payment as having been voluntary when made.

### 1.6 Reporting and explanation

Before allocation, a settlement-intent-pending-assessment payment contributes to:

- **Total remitted**
- **Unallocated settlement-intent amount**

It contributes zero to:

- **Credit allocated toward obligations**
- **Settlement of an identified obligation**

After allocation, reports move only the allocated portion into obligation credit. Reports and diagnostics must explain any remaining difference without calling it an error or silently reclassifying it.

For example:

| Record | Total remitted | Obligation credit | Unallocated settlement intent |
| --- | ---: | ---: | ---: |
| $500 remitted before assessment | $500 | $0 | $500 |
| Later $1,900 obligation; $500 deliberately allocated | $500 | $500 | $0 |

The obligation then has $1,400 remaining. If no obligation had arisen, the report would continue to show $500 remitted and $0 obligation credit until a later treatment decision was recorded.

### 1.7 Derived design requirements

- Absence of a recorded assessment must not classify a remittance as voluntary.
- Stated settlement intent must not manufacture an obligation.
- A later assessment must not automatically allocate an earlier payment.
- A later treatment decision must supplement rather than silently rewrite the intent recorded at payment.
- Original amount and currency must remain visible beside any allocation conversion.
- Voluntary, unresolved, unallocated settlement-intent, and allocated amounts must remain explainable as distinct categories.
- The interface must use calm language and must not portray an unallocated payment as delinquent, erroneous, or suspicious.

### 1.8 Open product questions

1. Should **unresolved** be the default, or should the interface require an explicit choice?
2. May one remittance carry split intent at entry, or only acquire split treatment through later allocations?
3. What evidence is sufficient to suggest—but never automatically perform—a match between a payment and later assessment?
4. How should a person correct inaccurately recorded intent while preserving the prior record?
5. What terminology will a general Bahá’í audience understand without learning accounting language?
6. Which parts of this flow belong in the fictional public explorer, and which should wait for the private ledger?
