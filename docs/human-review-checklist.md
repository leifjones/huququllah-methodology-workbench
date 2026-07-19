# Human Review Checklist

**Status:** Living review record

**Purpose:** Make visible what people have deliberately read and considered. An unchecked box means that no complete human review has yet been recorded; it does not mean the material is wrong. A checked box records review, not official approval or institutional endorsement.

## How to record and maintain review state

- A human should check a box only after reviewing the entire named scope.
- Add the reviewer, date, outcome, and a link or short note in the review log.
- Record focused comments without checking a whole-file box unless the whole file was reviewed.
- Reopen a checkbox when a later change materially affects the reviewed scope.
- Use the Git history and linked pull request for the exact version reviewed.
- Agents must follow the maintenance and user-alert protocol in [`AGENTS.md`](../AGENTS.md). Agents may reopen stale review state and maintain checklist coverage, but may never award human review to themselves.
- Routine changes to checkboxes and the log do not invalidate review of this checklist. Changes to its policy, scope groupings, or meaning do.

## Whole-file review

- [ ] `README.md`
- [x] `AGENTS.md`
- [ ] `docs/design-and-discourse-plan.md`
- [ ] `docs/source-rule-matrix.md`
- [ ] `docs/open-questions-and-counterexamples.md`
- [ ] `docs/calculation-invariants.md`
- [ ] `docs/human-review-checklist.md`

## Section review

### `AGENTS.md`

- [x] Human review ledger maintenance and user-alert rules

### `README.md`

- [x] Huqúqu'lláh in brief, purpose, and project boundaries
- [ ] Explicit threshold constraint
- [ ] Why gold appears, historical units, and indexed-credit distinction
- [ ] Status, products, and research questions
- [ ] Posture, references, and next deliverable

### `docs/design-and-discourse-plan.md`

- [ ] Desired contribution and non-negotiable posture
- [ ] Methodology taxonomy and source-grounded constraints
- [ ] Historical units and indexed-credit hypothesis
- [ ] Assessment, obligation, payment, and allocation model
- [ ] Event, provenance, asset classification, materiality, and partial-unit model
- [ ] Multi-currency strategy
- [ ] Ownership and household transitions
- [ ] Public explorer, private ledger, and privacy boundary
- [ ] General-audience accessibility and experience principles
- [ ] Phases and specification-readiness criteria

### `docs/source-rule-matrix.md`

- [ ] Status vocabulary and spiritual/social context
- [ ] Threshold, rate, whole-unit, and once-only rows
- [ ] Acquisition, expenses, loss, gift, and appreciation rows
- [ ] Debt, exemptions, ownership, and spouse rows
- [ ] Freedom of method, voluntary contribution, and conscience rows
- [ ] 1919 piastre example: documentary form and historical context
- [ ] 1919 piastre example: synthesis and review questions

### `docs/open-questions-and-counterexamples.md`

- [ ] Historical-state question
- [ ] Gold-rise and gold-fall counterexamples
- [ ] Delayed-payment counterexample
- [ ] Multi-currency, migration, and ownership questions
- [ ] Baseline reconstruction and alternative-lens reconciliation
- [ ] Piastre source-scope case

### `docs/calculation-invariants.md`

- [ ] Scope vocabulary and fictional-unit convention
- [ ] Threshold, whole-unit, and voluntary-payment invariants
- [ ] Financial identity and classification invariants
- [ ] Once-only principal and loss invariants
- [ ] Assessment, settlement, and allocation invariants
- [ ] Multi-currency and rate-provenance invariants
- [ ] Ownership and household-transition invariants
- [ ] Hypothesis, source-status, and privacy invariants
- [ ] Fictional acceptance suite

## Review log

The log may record both completed human reviews and review-state maintenance. Only an event explicitly identified as a completed human review can support a checked box.

| Date | Event | Person or agent | Scope | Outcome or follow-up | Link or notes |
| --- | --- | --- | --- | --- | --- |
| 2026-07-18 | Ledger structure changed | Codex (agent) | `AGENTS.md`; checklist policy and coverage | Added cross-agent maintenance rules and user-alert requirements; all new review scopes remain unchecked | [PR #2](https://github.com/leifjones/huququllah-methodology-workbench/pull/2) |
| 2026-07-18 | Ledger coverage updated | Codex (agent) | Design-plan event/provenance and calculation-invariant scopes | Expanded the existing unchecked design-plan scope to name asset classification and materiality; added missing coverage for once-only principal and loss invariants. No human review is asserted. | Follow-up PR pending |
| 2026-07-19 | Invariant convention clarified | Codex (agent) | Calculation-invariant scope vocabulary and fictional-unit convention | Clarified that simple rows are independent fixed-`U` cases, while later invariants address changing threshold values, currencies, dates, and valuation conventions. No human review is asserted. | Follow-up PR pending |
