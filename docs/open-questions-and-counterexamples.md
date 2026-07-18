# Open Questions and Counterexamples

**[PLACEHOLDER: This document develops the six central blocking questions with worked counterexamples and analysis of their implications for data model and calculation engine design]**

## Central blocking questions

### 1. Previously assessed principal in fiat currency

**Question:** When fiat-currency principal was assessed (e.g., $10,000 USD), should that principal be carried forward as:

- Its historical currency amount ($10,000), or
- A quantity of gold (grams), or  
- Something else?

**Why it matters:**
- If carried as currency, then the "previously assessed base" is simply the historical amount. Future comparisons are straightforward.
- If converted to gold and carried as grams, then the base is revalued whenever gold price changes. This can produce counterintuitive results.
- The authoritative worked example in paragraph 49 of the Compilation appears to carry the amount as currency, but this is not explicitly stated.

**Counterexample — Gold rises:**

[TO BE POPULATED WITH DETAILED SCENARIO]

**Counterexample — Gold falls:**

[TO BE POPULATED WITH DETAILED SCENARIO]

**Implications for design:**
- [TO BE POPULATED]

### 2. Assessment valuation date

**Question:** What date governs the gold value used for an assessment?

**Why it matters:**
- [TO BE POPULATED]

**Scope implications:**
- [TO BE POPULATED]

### 3. Payment-date gold

**Question:** If payment occurs later than assessment, does payment-date gold have any bearing on an already calculated assessment?

**Why it matters:**
- [TO BE POPULATED]

**Counterexample — Delayed payment:**

[TO BE POPULATED WITH SCENARIO SHOWING GOLD MOVEMENT BETWEEN ASSESSMENT AND PAYMENT]

**Implications for design:**
- [TO BE POPULATED]

### 4. Unrealized FX movements

**Question:** How should currency appreciation or depreciation be treated when holdings are denominated in non-reference currencies?

**Why it matters:**
- [TO BE POPULATED]

**Scope implications:**
- [TO BE POPULATED]

### 5. Joint-to-individual accounting transitions

**Question:** How should historical ownership and payment attribution be preserved when a household moves from joint to individual assessment (or vice versa)?

**Why it matters:**
- [TO BE POPULATED]

**Scope implications:**
- [TO BE POPULATED]

### 6. Trustworthy baseline initialization

**Question:** How should users with incomplete historical records establish a starting point they can trust?

**Why it matters:**
- [TO BE POPULATED]

**Scope implications:**
- [TO BE POPULATED]

---

## Gold-indexing in detail

[SECTIONS TO BE POPULATED]

### The rise scenario
### The fall scenario
### Why this is a research question, not a settled principle
### What source validation would be needed

---

**STATUS:** This document is critical for understanding why the v0.1 design was incomplete. Populating it requires both technical analysis and consultation with someone familiar with the authoritative guidance on Huqúqu'lláh.
