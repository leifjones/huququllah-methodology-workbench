# Huqúqu'lláh Methodology Workbench

**Pre-specification RFC — independent, non-institutional research project**

**Date:** July 18, 2026

**Status:** Conceptual investigation; source synthesis and calculation specification required before implementation

## Huqúqu'lláh in brief

Huqúqu'lláh (the “Right of God”) is a spiritual law revealed by Bahá'u'lláh that connects material life, individual conscience, and service to humanity. The authoritative codification describes it as a means of purifying wealth and says that its implications include the elimination of extremes of wealth and poverty and a more equitable distribution of resources. Its calculation and payment remain a matter of conscience between the individual and God; this workbench is concerned with learning and recordkeeping, not enforcement.

The law applies to individual Bahá'ís worldwide, but an **obligatory amount arises only when a person's assessable possessions—after applicable exemptions, expenses, and losses—reach the prescribed threshold**; debts and ability to pay are also relevant to settlement. It is therefore not a charge on every paycheck or on every person regardless of circumstances. See the [preamble and determining provisions of the authoritative codification](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1).

## Purpose

This project is a learning-oriented workspace for exploring how people may understand, describe, and keep records related to the law of Huqúqu'lláh. It aims to help individuals and couples:

1. Study the authoritative guidance before selecting a bookkeeping method.
2. Describe their methodology so another person can understand its sources, judgments, and assumptions.
3. Distinguish authoritative constraints, bookkeeping lenses, personal judgments, market-rate assumptions, and experimental hypotheses.
4. Preserve reproducible historical records without reconstructing years of values and payments from memory.
5. Compare approaches and identify why their results differ.
6. Develop shared language for exchanging learning without creating pressure or financial surveillance.

The project is **not** intended to:

- Adjudicate what methodology another person must use
- Replace study of the authoritative texts or consultation with those familiar with the law
- Demand, solicit, transmit, or monitor payment
- Turn conscience into compliance
- Require disclosure of personal wealth
- Provide tax or legal advice
- Present the creator's current experiment as official or institutionally endorsed guidance

## Explicit threshold constraint

The threshold is not an open question in this project. The authoritative guidance states that obligatory payment begins when assessable possessions reach the value of **19 mithqáls of gold**, approximately **69.2 grams**, and that subsequent liability arises on further complete units after applicable expenses and losses. Amounts below the first or a further complete unit do not create an obligation, although a person may contribute voluntarily.

See [Q&A 8](https://www.bahai.org/r/491430606), [Q&A 89–90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10), the [codification](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4), and the [1987 clarification on voluntary contribution below the threshold](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).

## Why gold appears: historical assessment units and indexed credit

The law defines its threshold using the value of **19 mithqáls of gold**. Gold therefore enters this project first as the measuring standard named in the law—not because a person must own gold, pay in gold, or continually revalue all wealth in gold. A calculation expressed in a local currency must document the gold price and valuation date it used.

The creator's gold-denominated experiment uses that law-defined threshold as a meter stick: it records how many **completed nineteen-mithqál assessment units** became assessable at a historical assessment. The purpose of that record is to stay close to the law's base unit, not primarily to preserve purchasing power.

Three facts must remain separate:

1. **Assessment:** the completed units and assessable principal identified on a particular date.
2. **Obligation:** the monetary amount arising from that assessment.
3. **Settlement:** one or more payments allocated to that obligation.

The completed historical unit count does not change merely because gold, foreign-exchange rates, residence, display currency, or the payment date later changes. Nor should the count be reconstructed from the price of gold on a delayed payment date.

A different operation is to translate historical units at today's gold price and treat the resulting amount as a deductible or “purified” base against current wealth. This repository labels that operation the **current-gold indexed-credit hypothesis**. It may be displayed and tested, but it is not assumed to follow automatically from recording historical units and must not be presented as an authoritative rule.

## Status and scope

This is conceptual work, not yet an implementation specification. Before a calculation engine is built, the project needs:

- A reviewed source-rule matrix
- A normalized event and calculation specification
- A defined relationship among assessment, obligation, payment, and allocation
- Worked examples that combine all applicable constraints rather than treating one source example as a complete algorithm
- Explicit treatment of multiple currencies, ownership changes, losses, and incomplete historical records
- Reproducible fictional test cases

Two possible products are intentionally separated:

- A **public methodology explorer** using fictional examples and exposing source, judgment, and assumption layers
- A **private financial ledger**, deferred until a threat model, encryption approach, recovery model, export/deletion controls, and couple permissions have been reviewed

## Documentation

- [Design and discourse plan](docs/design-and-discourse-plan.md) — posture, methodology taxonomy, conceptual model, event model, multi-currency strategy, ownership transitions, and phases
- [Source-rule matrix](docs/source-rule-matrix.md) — what the sources explicitly establish, what each example illustrates, and what remains unresolved
- [Open questions and counterexamples](docs/open-questions-and-counterexamples.md) — indexed-credit counterexamples, delayed-payment failure, the 1919 piastre example, and continuity across currencies and ownership changes
- [Calculation invariants](docs/calculation-invariants.md) — correctness constraints and fictional acceptance tests for a future specification
- [Human review checklist](docs/human-review-checklist.md) — an explicit record of which files and sections people have deliberately reviewed

## Central research questions

1. What historical state should be preserved after assessment: native-currency principal, completed threshold units, identified property, or a linked combination?
2. Is a current-gold translation of historical units merely a reporting view, or can it defensibly function as a substantive indexed credit?
3. What date and evidence govern the local-currency value of a threshold unit at assessment?
4. How should incomplete historical payment records be reconstructed without presenting estimates as facts?
5. How should native-currency histories be consolidated without allowing current FX movements to create silent gains or losses?
6. How should ownership histories survive marriage, divorce, remarriage, gifts, inheritance, migration, and changes between joint and individual accounting?
7. Under what conditions should different bookkeeping lenses reconcile, and how should any divergence be explained?

The 1919 piastre example is treated as a **source-scope case**, not as evidence that the explicit threshold can be bypassed. It illustrates the 19% rate, deduction of expenses, annual reconciliation, and once-only treatment, while its simplified numbers do not visibly apply the whole-unit gate established elsewhere. See the [source-rule matrix](docs/source-rule-matrix.md#the-1919-piastre-example) for the evidence and synthesis.

## Posture and invitation

The project begins with humility about what is established, inferred, judged, or still unknown:

> This is how I am currently understanding the law and organizing my records. Here are the sources, judgments, assumptions, and calculations involved. Here are the results under alternative approaches. I offer it as an experiment and an invitation to learn together.

Readers are encouraged to study the linked texts, test the examples, share alternative approaches, and consult appointed representatives when a question calls for guidance. No page should demand payment, shame uncertainty, rank people, or imply institutional endorsement.

## Primary references

1. [A Codification of the Law of Huqúqu'lláh — determining the amount](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4)
2. [The Kitáb-i-Aqdas, Questions and Answers no. 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
3. [The Kitáb-i-Aqdas, Questions and Answers nos. 89–90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10)
4. [The Kitáb-i-Aqdas, note 125](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/15)
5. [Huqúqu'lláh—The Right of God, application of the law](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3)
6. [Universal House of Justice, 26 November 2000](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1)

## Next deliverable

The recommended next artifact is a calculation-specification workbook containing normalized schemas, formulas, rate provenance, source justifications, and expected results for the fictional cases in this repository. Implementation remains downstream of that specification and its review.

---

*This repository is a research project and invitation to study, not an official calculator or endorsed guidance.*
