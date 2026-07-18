# Huqúqu'lláh Methodology Workbench

**Pre-specification RFC — Independent, non-institutional research project**  
**Date:** July 18, 2026  
**Status:** Conceptual investigation; requires validation before implementation

---

## Project Purpose

This project seeks to develop a learning-oriented workspace and discourse framework that helps individuals and couples:

1. **Learn how the law of Huqúqu'lláh may be carried out in practice** — starting with study of authoritative guidance.
2. **Describe their own methodology clearly** — so another person can understand their choices.
3. **Distinguish authoritative guidance, personal judgment, bookkeeping method, and market assumptions** — making each layer visible.
4. **Maintain understandable historical records** — without reconstructing years of values, rates, and payments from memory.
5. **Compare different approaches** — and identify precisely where methods diverge, without implying that all approaches are equally grounded in source texts.
6. **Develop shared language** — for discussing how the law applies in practice.
7. **Share learning while preserving privacy** — avoiding pressure, solicitation, or financial surveillance.

The project is **not** intended to:

- Adjudicate which methodology another person must use
- Replace study of authoritative texts or conversation with others who have studied the law
- Demand, solicit, transmit, or monitor payment
- Turn conscience into compliance
- Require disclosure of personal wealth
- Provide tax or legal advice
- Present the creator's current approach as the only legitimate calculation

---

## Critical Distinction: Historical Assessment Units vs. Indexed Credit

This project records how many **completed nineteen-mithqál assessment units** have historically become assessable and been discharged. This is a **historical accounting fact**.

Separately and distinctly, the project explores (but does not assume) that those historical units should be **translated at current gold prices** when determining a deductible or "purified" base against current wealth. This is an **experimental methodological hypothesis**.

**Key principle:**

> Gold is used to identify and record completed nineteen-mithqál assessment units at the time an assessment arises. The workbench separately explores—but does not assume—that those historical units should be translated at current gold prices when determining previously assessed principal.

The **number of completed historical units is dimensionless and immutable** once the assessment is fixed. A later change in gold price, currency, country, display currency, or payment date does not alter that historical count. Converting that count into a current monetary amount is a separate transformation labeled the **current-gold indexed-credit hypothesis**, not an authoritative rule.

---

## Status and Scope Notes

### This is conceptual work, not an implementation specification.

**Before any application is built**, the following must be resolved through study, consultation, and written specification:

1. **What historical fact is preserved after assessment?** Native-currency principal, completed nineteen-mithqál units, identified property, or some combination? And does translating that history at current gold prices provide only a presentational view or a substantive indexed credit?

2. **How do assessment and payment relate?** Assessment and payment are logically separate events with different dates and may use different gold prices. These must be untangled in the data model.

3. **How should bookkeeping methods be compared?** Different ledgering approaches (annual surplus vs. lifetime wealth reconciliation) should ideally reconcile when applied to complete and consistent facts. The system must identify why they diverge if they do.

4. **How should ownership, spouses, and property changes be modeled?** This is more complex than a display toggle and requires effective-dated, event-based accounting.

5. **How do the piastre example and the whole-unit rule coexist?** The 1919 worked example in the Compilation requires reconciliation with explicit whole-unit treatment in other authoritative texts.

### This is a research project, not institutional guidance.

No page, statement, or export from any future tool should imply institutional endorsement or official status. This is an experiment and invitation to study, not a settlement of contested questions.

### Two prospective products have been conflated.

This document envisions both:

- A **private financial ledger** for sensitive household data (deferred pending threat model and privacy review)
- A **public methodology explorer** with fictional examples and terminology development (suitable as a starting point)

The public-first approach is recommended; see `docs/design-and-discourse-plan.md`.

---

## Documentation

- **[docs/design-and-discourse-plan.md](docs/design-and-discourse-plan.md)** — Full design and discourse vision, methodology taxonomy, data model, user experience outline, and implementation phases.
- **[docs/source-rule-matrix.md](docs/source-rule-matrix.md)** — Authoritative sources, explicit principles, epistemic status, implementation consequences, and unresolved questions. Includes reconciliation of the 1919 piastre example with whole-unit rules.
- **[docs/open-questions-and-counterexamples.md](docs/open-questions-and-counterexamples.md)** — Blocking conceptual questions, worked counterexamples (gold rise/fall/delayed payment), and the piastre case study.
- **[docs/calculation-invariants.md](docs/calculation-invariants.md)** — Correctness and success criteria that any future calculation engine must satisfy.

---

## Central Blocking Questions

1. **Historical units vs. indexed credit:** What historical fact is preserved—native-currency principal, completed threshold units, or identified property—and does translating that at current gold prices provide only a presentational view or a substantive indexed credit?
2. **Assessment valuation date:** What date governs the gold value used for assessment?
3. **Payment-date gold:** If payment occurs later, does payment-date gold affect an already calculated assessment?
4. **Unrealized FX movements:** How should currency appreciation/depreciation be treated?
5. **Joint-to-individual transitions:** How should historical ownership and payment attribution be preserved?
6. **Trustworthy baseline initialization:** How should users with incomplete historical records establish a starting point?

---

## Posture and Invitation

This project begins with humility about what is and is not yet understood. The creator invites:

> This is how I am currently understanding the law and organizing my records. Here are the sources, judgments, assumptions, and calculations involved. Here is what results emerge under alternative approaches. I offer it as an experiment and an invitation to learn together.

Readers are encouraged to:

- Study the authoritative texts linked in this documentation
- Share feedback and alternative approaches in this repository's discussions
- Consult with others who have studied the law
- If questions arise that require guidance from appointed representatives, reach out to them with specific questions

No page should demand payment, shame uncertainty, rank approaches, or present one person's experiment as settled truth.

---

## Authoritative References

Primary sources supporting this project's foundation:

1. [A Codification of the Law of Huqúqu'lláh — determining the amount](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4)
2. [The Kitáb-i-Aqdas, Questions and Answers nos. 8, 90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
3. [Huqúqu'lláh—The Right of God (paragraphs 41, 49, 59–60, 63, 66)](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3)
4. [The Kitáb-i-Aqdas, note on Huqúqu'lláh](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/15)
5. [Universal House of Justice, 26 November 2000](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1)

---

## Next Steps

**No implementation work should proceed** until:

- The blocking questions above are addressed or explicitly deferred
- A written, normalized calculation specification exists
- Worked examples reconcile alternative approaches and source examples
- The assessment-payment separation is formally specified
- Fictional test cases demonstrate correctness invariants
- The source-rule matrix has been reviewed with attention to historical sources and scope boundaries

The recommended next deliverable is a **calculation specification workbook** containing schemas, formulas, test cases, and source justifications. See `docs/design-and-discourse-plan.md` for details.

---

*This documentation is a research project and invitation to study, not an official calculator or endorsed guidance.*
