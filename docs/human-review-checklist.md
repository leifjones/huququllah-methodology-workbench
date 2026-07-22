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
- [ ] `docs/draft-ux-and-feature-proposals.md`
- [ ] `docs/source-rule-matrix.md`
- [ ] `docs/open-questions-and-counterexamples.md`
- [ ] `docs/considered-approaches.md`
- [x] `docs/calculation-invariants.md`
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
- [ ] Assessment, obligation, payment, allocation, voluntary-treatment, and record-lifecycle model
- [ ] Event, provenance, asset classification, materiality, and partial-unit model
- [ ] Multi-currency strategy
- [ ] Ownership and household transitions
- [ ] Public explorer, private ledger, privacy, and agent-access boundary
- [ ] General-audience accessibility and experience principles
- [ ] Phases and specification-readiness criteria

### `docs/draft-ux-and-feature-proposals.md`

- [ ] Status, source/design boundary, user need, and state separation
- [ ] Intent choices, entry flow, later assessment, allocation, and reporting
- [ ] Derived design requirements and open product questions

### `docs/source-rule-matrix.md`

- [ ] Status vocabulary and spiritual/social context
- [ ] Threshold, rate, whole-unit, and once-only rows
- [ ] Acquisition, expenses, loss, gift, appreciation, and gold-price synthesis rows
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
- [ ] Focused consultation questions

### `docs/considered-approaches.md`

- [ ] Purpose, status vocabulary, and current-posture summary
- [ ] Single-primary-currency synthesis, source rationale, and limits
- [ ] Current-gold indexed-credit and payment-derived-unit approaches
- [ ] Separate “purified wealth” spending-account approach
- [ ] Posture-change protocol

### `docs/calculation-invariants.md`

- [x] Scope vocabulary and fictional-unit convention
- [x] Threshold, whole-unit, and voluntary-payment invariants
- [x] Financial identity, classification, and record-lifecycle invariants
- [x] Once-only principal and loss invariants
- [x] Assessment, settlement, allocation, and payment-reconciliation invariants
- [x] Multi-currency and rate-provenance invariants
- [x] Ownership and household-transition invariants
- [x] Hypothesis, source-status, and privacy invariants
- [x] Fictional acceptance suite

## Review log

The log may record both completed human reviews and review-state maintenance. Only an event explicitly identified as a completed human review can support a checked box.

| Date | Event | Person or agent | Scope | Outcome or follow-up | Link or notes |
| --- | --- | --- | --- | --- | --- |
| 2026-07-18 | Ledger structure changed | Codex (agent) | `AGENTS.md`; checklist policy and coverage | Added cross-agent maintenance rules and user-alert requirements; all new review scopes remain unchecked | [PR #2](https://github.com/leifjones/huququllah-methodology-workbench/pull/2) |
| 2026-07-18 | Ledger coverage updated | Codex (agent) | Design-plan event/provenance and calculation-invariant scopes | Expanded the existing unchecked design-plan scope to name asset classification and materiality; added missing coverage for once-only principal and loss invariants. No human review is asserted. | [PR #3](https://github.com/leifjones/huququllah-methodology-workbench/pull/3) |
| 2026-07-19 | Invariant convention clarified | Codex (agent) | Calculation-invariant scope vocabulary and fictional-unit convention | Clarified that simple rows are independent fixed-`U` cases, while later invariants address changing threshold values, currencies, dates, and valuation conventions. No human review is asserted. | [PR #4](https://github.com/leifjones/huququllah-methodology-workbench/pull/4) |
| 2026-07-19 | Ledger coverage expanded | Codex (agent) | Payment treatment, record lifecycle, reconciliation, agent-access, and focused-consultation scopes | Expanded existing unchecked scopes for voluntary-credit treatment, drafts and amendments, explainable payment reconciliation, permission-scoped agent diagnostics, and the fictional acceptance suite; added missing coverage for focused consultation questions. Corrected stale pending-PR references. No human review is asserted. | [PR #4](https://github.com/leifjones/huququllah-methodology-workbench/pull/4) |
| 2026-07-19 | Currency-display convention clarified | Codex (agent) | Design-plan multi-currency strategy, experience principles, and calculation-invariant currency/rate scopes | Clarified that recorded currency is the default display and that converted reporting values require visible rate provenance; added a concrete reconciliation example for total remitted versus obligation credit. No human review is asserted. | [PR #4](https://github.com/leifjones/huququllah-methodology-workbench/pull/4) |
| 2026-07-20 | Single-currency synthesis and approach history added | Codex (agent) | Source-matrix augmentation and voluntary-payment synthesis; design-plan primary-currency, voluntary-intent, and progressive-disclosure sections; new considered-approaches document; voluntary-payment reconciliation; indexed-credit candidate invariant; fictional acceptance suite | Added unchecked review coverage for the new approach-history document and gold-price synthesis row. Reopened the calculation-invariants whole-file review, threshold/whole-unit/voluntary-payment scope, assessment/settlement/allocation/payment-reconciliation scope, hypothesis/source-status scope, and fictional acceptance suite because the voluntary-intent examples, reconciliation, candidate invariant, and scenario changed reviewed content. No human review is asserted. | Branch `agent/document-single-currency-synthesis` |
| 2026-07-20 | Focused invariant decision | LJ Jones (human) | Calculation invariant 21 — gold-price movement without economic augmentation | Confirmed promotion from candidate to derived design rule, requested an explicit rationale, and approved clean renumbering. Broader calculation-invariant review remains open. | User direction in project conversation |
| 2026-07-20 | Ledger coverage and stale-state correction | Codex (agent) | New draft UX document; calculation-invariant whole-file, threshold/whole-unit/voluntary-payment, and fictional acceptance-suite scopes | Added unchecked whole-file and section coverage for `docs/draft-ux-and-feature-proposals.md`. Corrected stale checked states left after PR #7 added invariant 1a and changed the fictional acceptance suite. Design-plan and README scopes changed in PR #8 were already unchecked. No human review is asserted. | [PR #8](https://github.com/leifjones/huququllah-methodology-workbench/pull/8) |
| 2026-07-21 | Indexed-credit boundary and document structure clarified | Codex (agent) | Open Questions historical-state/indexed-credit section; Considered Approaches indexed-credit posture; design-plan indexed-credit boundary; README research questions; calculation invariants 19–20 | Reclassified the indexed-credit material as worked counterexamples while retaining the historical-state and source questions; aligned counterfactual research output with the prohibition on recording it as an obligation. Reopened the calculation-invariants whole-file review and hypothesis/source-status/privacy scope. No human review is asserted. | Branch `agent/succinct-gold-indexed-question` |
