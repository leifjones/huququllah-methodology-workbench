# Calculation Invariants

**[PLACEHOLDER: This document specifies correctness requirements that any future calculation engine must satisfy, organized as invariants and counterexamples]**

## Core invariants

Any calculation system, regardless of which methodology is selected, must satisfy these invariants. If it does not, there is a bug.

### 1. Transfers between accounts do not create assessable wealth

**Invariant:** Moving $1,000 from account A to account B, when both are in the same owner's assessment base and assessed as part of a completed calculation, does not create a new $1,000 assessable increase.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

### 2. Splitting or merging holdings does not alter economic result

**Invariant:** Combining two holdings into one, or splitting one holding into two, does not change the total assessed amount or payment obligation.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

### 3. Splitting one payment into installments does not alter historical assessed base

**Invariant:** A single assessment payment of $1,900 made on date X, or split into $950 on date X and $950 on date Y, should result in the same historical assessed base being recorded.

**Why this matters:** The assessed base is a record of historical principal, not a function of how payment was made or sequenced.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

### 4. Delayed payment does not rewrite an assessment

**Invariant:** If an assessment is calculated on date X with gold at price A, and payment occurs on date Y with gold at price B, the assessment is not retroactively altered by the later gold price.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED WITH GOLD MOVEMENT SCENARIO]

### 5. Previously assessed property is not assessed twice without explicit source-grounded reason

**Invariant:** Once property has been assessed and Huqúqu'lláh paid, that same property should not become assessable again in a subsequent period without a source-grounded reason (such as recovery from loss, or a deliberate change in classification).

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

### 6. Recovery of prior loss is distinguished from new augmentation

**Invariant:** If property drops from $100,000 to $80,000 (a $20,000 loss) and later recovers to $100,000, the recovery should be recorded and distinguished from a new $20,000 acquisition.

**Why this matters:** Different judgments and possibly different payment obligations may apply.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED WITH LOSS AND RECOVERY SEQUENCE]

### 7. Display-currency changes affect presentation, not economic result

**Invariant:** Converting a calculation from USD reporting to EUR reporting should change displayed amounts but not the underlying obligation amount in the original currency, within defined precision tolerance.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED WITH MULTI-CURRENCY SCENARIO]

### 8. Unrealized price or FX movements do not silently become realized gains

**Invariant:** A property whose USD value increases due to FX appreciation should not automatically be treated as a realized gain if the property itself has not been sold or exchanged.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

### 9. Every historical assessment is reproducible from immutable inputs

**Invariant:** Given:
- The original property or principal
- The date of assessment
- The gold price used
- The methodology/formula version
- The personal judgments recorded

...a future user should be able to reproduce the same assessment result, even if gold prices, FX rates, or current property values have changed.

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED WITH RECONSTRUCTED ASSESSMENT SCENARIO]

### 10. Different bookkeeping lenses reconcile or explicitly identify divergence

**Invariant:** When the same complete set of financial facts is processed through two different bookkeeping methods (e.g., annual surplus vs. lifetime wealth reconciliation), they should either:

1. Produce identical results, or
2. Explicitly identify which judgment, missing event, classification, or valuation assumption accounts for the difference.

**Counterexample (buggy behavior):** [TO BE POPULATED WITH DIVERGING METHODS]

**Test case:** [TO BE POPULATED]

### 11. Every displayed rule, method, or assumption shows its epistemic status

**Invariant:** Every statement in the UI or export should be labelable as:
- Authoritative source requirement
- Derived from authoritative source via explicit reasoning
- Personal judgment point
- Software operating assumption
- Experimental hypothesis

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

### 12. Public prototype uses only fictional data until privacy model is reviewed

**Invariant:** No version released publicly should accept, store, display, or export real household financial data until:
- A threat model has been documented
- Encryption architecture has been specified
- Key recovery procedures have been addressed
- Data export and deletion capabilities have been tested
- Couple permission and access control have been designed
- A security review has been conducted

**Counterexample (buggy behavior):** Releasing a "demo" version that accepts real data for "testing."

**Test case:** [TO BE POPULATED]

### 13. No page implies institutional endorsement

**Invariant:** Every page, statement, export, video, or discourse material should clearly communicate:
- This is a research project and learning tool, not official guidance
- This represents one person's experiment, not a settled consensus
- Consultation with appointed representatives remains essential
- This is not a substitute for study of authoritative sources

**Counterexample (buggy behavior):** [TO BE POPULATED]

**Test case:** [TO BE POPULATED]

---

## Test scenarios required before implementation is trusted

[PLACEHOLDER: COMPREHENSIVE TEST SUITE TO BE POPULATED]

The test scenarios from the original v0.1 (holding at unit value, multi-currency consolidation, historical payment with gold movement, joint/individual transitions, loss and recovery, etc.) should be formalized here with expected outputs under each methodology profile.

---

**STATUS:** This document is not complete until specific test cases with expected results are written for each invariant. This is suitable work for a collaborative specification phase before coding begins.
