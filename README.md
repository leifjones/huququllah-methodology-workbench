# Huqúqu'lláh Methodology Workbench

**Independent, non-institutional design and learning project**

**Status:** Designing a public, interactive methodology explorer using fictional scenarios; personal financial data is out of scope for the first product

## Huqúqu'lláh in brief

Huqúqu'lláh (the “Right of God”) is a spiritual law revealed by Bahá'u'lláh that connects material life, individual conscience, and service to humanity. The authoritative codification describes it as a means of purifying wealth and says that its implications include the elimination of extremes of wealth and poverty and a more equitable distribution of resources. Its calculation and payment remain a matter of conscience between the individual and God.

An obligatory amount arises only when a person's assessable possessions—after applicable exemptions, expenses, and losses—reach the prescribed threshold; debts and ability to pay are also relevant to settlement. Huqúqu'lláh is therefore not a charge on every paycheck or on every person regardless of circumstances. See the [preamble and determining provisions of the authoritative codification](https://www.bahai.org/r/769134373).

## What this project is building

This repository is designing a tool for visualizing, explaining, and discussing how the guidance may apply in concrete situations. The first public product is intended to be an **interactive methodology explorer** that uses fictional scenarios rather than personal financial data.

The explorer should help people:

1. Move through simple cases—an initial assessment, a voluntary contribution below the threshold, and later accumulation under the once-only principle—before adding more complex circumstances.
2. See which parts of a result come from authoritative guidance, recorded facts, individual judgments, bookkeeping choices, market-rate evidence, or experimental hypotheses.
3. Inspect a reproducible calculation trace rather than receive an unexplained amount.
4. Compare approaches and identify exactly why their results differ.
5. Use concrete scenarios to initiate individual study, shared exploration, and consultation, including the development of tentative source-grounded answers whose uncertainty remains visible.

The design may later support a **private financial ledger** for individuals or couples who choose to use their own data. That possibility is deferred until privacy, security, permissions, recovery, export, correction, and deletion have been designed and reviewed. It is a possible later use of the work, not the premise of the public explorer.

## Project boundaries

The project is **not** intended to:

- Determine what methodology another person must use or what amount another person owes
- Replace study of the authoritative texts, personal reflection, shared consultation, or consultation with those familiar with the law
- Demand, solicit, transmit, or monitor payment
- Turn conscience into compliance
- Require disclosure of personal wealth
- Provide tax or legal advice
- Present a project conclusion as official or institutionally endorsed guidance

## Threshold and current calculation posture

The threshold is not an open question in this project. [Q&A 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9) states that obligatory payment begins when assessable possessions reach the value of **19 mithqáls of gold**, and subsequent liability arises on further complete units after applicable expenses and losses. Amounts below the first or a further complete unit do not create an obligation.

A person whose assessable possessions remain below the threshold may stop there: no payment is due. [Paragraph 63 of the application compilation](https://www.bahai.org/r/553865725) confirms that the person may nevertheless contribute voluntarily if they wish. No percentage is prescribed for that voluntary contribution, and the project must not portray 19%—or any other amount—as expected or due below the threshold.

For metric calculation, the project uses the source-specified relationship that **one mithqál consists of 19 nakhuds, and 24 nakhuds equal four and three-fifths grams**. The threshold is therefore `19 × 19 ÷ 24 × 4.6 = 69.1916… grams`, conventionally reported as approximately **69.2 grams**. See [paragraph 52 of the application compilation](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3).

Gold enters the ordinary calculation as the law-defined measure used to value a threshold unit at an assessment. It does not follow that a person must own or pay in gold, or that previously assessed wealth should continually change with today's gold price. The current working synthesis for simple cases uses a primary currency and event-based augmentation: a gold-price movement alone does not create new income, acquisition, realized profit, recovery, or another economic event.

The earlier approach of translating historical units at today's gold price and using the result as deductible “purified” principal is **not the ordinary product path**. It remains documented only as design history and an optional counterfactual for understanding why it was set aside. See [Considered Approaches and Current Posture](docs/considered-approaches.md) and the [worked counterexamples](docs/open-questions-and-counterexamples.md#2-historical-state-question-and-indexed-credit-counterexamples).

## Documentation

- [Design and discourse plan](docs/design-and-discourse-plan.md) — the primary product plan: posture, audience, conceptual and event models, experience principles, public/private boundary, and development phases
- [Source-rule matrix](docs/source-rule-matrix.md) — what the sources explicitly establish, what each example illustrates, and where synthesis or judgment begins
- [Calculation invariants](docs/calculation-invariants.md) — correctness constraints and fictional acceptance cases for future implementation
- [Draft UX and feature proposals](docs/draft-ux-and-feature-proposals.md) — proposed interactions whose details are still being designed
- [Open questions and counterexamples](docs/open-questions-and-counterexamples.md) — remaining representation, reconstruction, currency, ownership, and consultation questions, together with cases that rule out unsafe transformations
- [Considered approaches and current posture](docs/considered-approaches.md) — the decision record for provisional, experimental, legacy, and set-aside approaches
- [Human review checklist](docs/human-review-checklist.md) — the record of which files and sections people have deliberately reviewed

## Development path

Current work is refining the source synthesis, design plan, invariants, and fictional scenarios that the explorer will communicate. The first tangible implementation target is the public methodology explorer:

- Interactive fictional scenarios
- Guided state-transition playback
- Visible source, judgment, assumption, and calculation layers
- Comparison views and explanations of divergence
- No collection or storage of personal financial data

A calculation engine suitable for personal records and an optional private ledger are later stages, not prerequisites for making the questions and current design visible.

## Posture and invitation

The project does not have authority to issue rulings, but it can still support meaningful inquiry. Readers are encouraged to study the linked texts, test the fictional cases, share alternative reasoning, consult with one another, and preserve tentative source-grounded conclusions together with remaining uncertainty and conditions for reconsideration.

When a question may call for guidance from an appointed representative, the workbench should help people frame it for consultation and preserve what was learned. Such consultation complements rather than shortcuts individual reflection, study, and shared exploration. Recording a conclusion in the project does not make it official guidance.

## Primary references

1. [A Codification of the Law of Huqúqu'lláh — determining the amount](https://www.bahai.org/library/authoritative-texts/compilations/codification-law-huququllah/4)
2. [The Kitáb-i-Aqdas, Questions and Answers no. 8](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/9)
3. [The Kitáb-i-Aqdas, Questions and Answers nos. 89–90](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/10)
4. [The Kitáb-i-Aqdas, note 125](https://www.bahai.org/library/authoritative-texts/bahaullah/kitab-i-aqdas/15)
5. [Huqúqu'lláh—The Right of God, application of the law](https://www.bahai.org/library/authoritative-texts/compilations/huququllah-right-god/3)
6. [Universal House of Justice, 26 November 2000](https://www.bahai.org/library/authoritative-texts/the-universal-house-of-justice/messages/20001126_001/1)

---

*This repository is an invitation to study, visualize, and discuss—not an official calculator or endorsed guidance.*
