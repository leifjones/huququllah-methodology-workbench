# Draft Explorer Architecture

**Status:** Candidate architecture for the first public methodology-explorer implementation; not an implementation specification, technology selection, or authorization to accept real financial data

**Purpose:** Define the smallest useful seam for turning reviewed fictional cases into deterministic, explainable explorer results without designing the deferred private ledger in advance.

**Review posture:** Planning material for human review. It is downstream of the [Design and Discourse Plan](design-and-discourse-plan.md), [Source-Rule Matrix](source-rule-matrix.md), [Calculation Invariants](calculation-invariants.md), and [Draft UX and Feature Proposals](draft-ux-and-feature-proposals.md). If this document conflicts with their source-status or product boundaries, those documents control until the conflict is deliberately resolved.

This proposal does not settle open calculation questions, select a language or framework, make an experimental approach authoritative, or authorize durable user-entered financial data.

## 1. The first implementation seam

The first end-to-end slice should be:

```text
curated fictional scenario
  -> explicit validated inputs
  -> deterministic evaluation
  -> structured result and trace
  -> progressively disclosed presentation
```

The first slice should implement the threshold ladder already named in the minimum fictional acceptance suite: fictional assessable amounts of `$9,999`, `$10,000`, `$19,999`, and `$20,000` with a fictional threshold-unit value `U = $10,000`. For this bounded case, each amount is already after the applicable fictional exemptions, expenses, and losses; the slice does not yet model how those judgments were reached.

That pedagogical use of `U` does not replace the source-defined threshold. A separate fixture should demonstrate the metric relationship `19 × 19 ÷ 24 × 4.6 = 69.1916… grams`. A later slice that translates the threshold into a real currency requires a reviewed valuation date, gold instrument, market convention, rate source, precision, and expected result. Until those inputs are specified, the explorer must label `U` as a fictional unit rather than imply that it has performed a real market valuation.

The expected threshold-ladder outputs are:

| Fictional assessable amount | Completed units | Obligatory principal | Obligatory amount | Remainder |
| ---: | ---: | ---: | ---: | ---: |
| `$9,999` | 0 | `$0` | `$0` | `$9,999` |
| `$10,000` | 1 | `$10,000` | `$1,900` | `$0` |
| `$19,999` | 1 | `$10,000` | `$1,900` | `$9,999` |
| `$20,000` | 2 | `$20,000` | `$3,800` | `$0` |

For each threshold-ladder case, the result should expose:

- Whether an obligatory amount arises
- The number of completed threshold units
- The principal entering the 19% calculation
- The obligatory amount
- The remainder below the next completed unit
- The source, derived-rule, and arithmetic steps needed to explain the result

The ordinary presentation may remain simple. Full provenance and arithmetic should be retained in the result and available on demand, not forced into every screen.

## 2. Deliberate sequence of fictional slices

After the threshold ladder proves the seam, the next slices should be selected from reviewed acceptance cases rather than from a speculative domain model.

| Order | Fictional slice | What it adds |
| ---: | --- | --- |
| 1 | Threshold ladder with fictional `U` | Whole-unit gate, 19% calculation, carried remainder, structured trace |
| 2 | `$6,000` with an illustrative `$100` voluntary contribution | Complete below-threshold stopping point; voluntary amount remains separate from obligation; future-credit intention can remain excluded, preserved for possible allocation, or unresolved |
| 3 | Unchanged previously assessed property followed by genuine additional accumulation | Once-only principal and a guided state transition across time |
| 4 | One selected comparison case | A labeled divergence explanation without allowing an experimental result to become the ordinary obligation |

Each slice should add only the concepts and controls that its reviewed inputs require. Missing data must not receive a semantic default when it is required for the selected case; irrelevant controls need not be shown, and curated context may be fixed explicitly by the scenario.

No percentage is prescribed for a below-threshold voluntary contribution. The `$100` amount is one fictional illustration, not a suggested norm.

## 3. Minimal conceptual vocabulary

The first slice needs a deliberately small model. Names remain provisional and do not imply database tables or public APIs.

| Concept | Responsibility in the explorer |
| --- | --- |
| `ScenarioDefinition` | Stable scenario identifier, version, title, fictional-data notice, guided steps, and source references |
| `EvaluationInput` | Exact immutable values required by the selected scenario |
| `ThresholdContext` | Source-defined weight relationship plus either a fictional `U` or reviewed rate evidence used to derive a currency value |
| `JudgmentOrAssumption` | An explicitly labeled scenario choice that is neither a recorded fact nor an authoritative constraint |
| `EvaluationResult` | Completion status, typed outputs, trace, diagnostics, and scenario/specification identifiers |
| `TraceNode` | Stable semantic step identifier, exact inputs and outputs, child steps, and applicable references |
| `Diagnostic` | Blocking invalidity, unresolved required input, warning, or informational notice |
| `SourceReference` | Citation and role without copying authority into application code or prose |
| `DivergenceReason` | Structured explanation of why two selected approaches differ |

The first slice does not require `History`, `Assessment`, `Obligation`, `PaymentAllocation`, `Amendment`, `Replay`, `Workspace`, or runtime source-authoring records. Those concepts should enter the active model only when a selected use case exercises them.

## 4. Logical boundaries

A modular monolith with a functional core and an imperative shell is a reasonable starting posture.

| Boundary | Responsibility |
| --- | --- |
| Scenario catalog | Load curated, versioned fictional fixtures and explanatory content |
| Evaluation core | Validate explicit inputs and calculate deterministic results |
| Explanation | Produce semantic traces, diagnostics, and divergence reasons |
| Explorer application | Select a scenario, run an evaluation, and map the result to presentation state |
| Presentation | Provide guided interaction, progressive disclosure, accessibility, and the fictional-data boundary |

These may begin as folders rather than packages or services. The purpose of the boundaries is to make dependencies and meaning visible, not to maximize abstraction.

The evaluation core should not:

- Read the clock
- Fetch market data
- Query storage or the network
- Inspect environment configuration
- Render user-facing prose
- Select behavior through reflection, plug-ins, or mutable registration
- Infer zero, exemption, voluntariness, settlement, ownership, or another semantic value from a missing required input

Every evaluation input should be supplied explicitly and remain immutable for the duration of the run. The same input and version must produce the same result.

## 5. Closed calculation behavior and narrow extension seams

The source-defined mithqál relationship, whole-unit gate, 19% rate, once-only treatment, and distinction between obligatory and voluntary amounts are not user-selectable strategies. When implemented, source-constrained behavior should live in a small, explicit, versioned evaluator whose order is visible.

Variation should be added only where the existing methodology taxonomy allows genuine variation:

| Existing taxonomy | Explorer treatment |
| --- | --- |
| Authoritative constraint | Required evaluator behavior with source references |
| Derived design rule | Explicit versioned behavior with rationale and limits |
| Individual judgment | Scenario input, visibly labeled |
| Bookkeeping lens | Selected projection or comparison over the same explicit inputs |
| Experimental hypothesis | Opt-in comparison that cannot replace the ordinary result |
| Voluntary practice | Separate illustrative input and output, never obligatory principal |

A general rule engine, plug-in system, service locator, generic repository, event bus, or private-ledger persistence layer is not justified by the first slices.

## 6. Structured explanation and presentation

The evaluator should return structure rather than a number plus logs or assembled English prose. Trace and diagnostic code should emit stable semantic identifiers and typed parameters. Presentation code may then render a concise explanation and progressively disclose details.

For example, a below-threshold result may initially say that no payment is due and allow the person to stop. An optional explanation can disclose the fictional unit, comparison, remainder, source reference, and distinction between no obligation and a possible voluntary contribution.

Source quotations, project explanations, individual judgments, and experimental propositions must remain distinguishable. Human review of repository content does not create institutional authority, and the first implementation does not require a runtime editorial workflow to preserve that distinction.

Language-neutral semantic identifiers are preferable to calculations that emit assembled English sentences. This keeps future localization possible without selecting languages, translation storage, or localization tooling now. Locale must not alter calculation behavior, currency, rate convention, or source status.

## 7. Explorer privacy boundary

The public explorer must not be a private ledger with persistence disabled by a feature flag. Its composition should have no general workspace repository, receipt upload, free-form personal note store, import path, or private-history adapter.

Phase 1 may retain curated fictional fixtures and ordinary application assets. Interactive state may remain session-scoped and in memory. A fictional export may be generated at the user's request without creating a retained workspace.

The interface should clearly describe scenarios as fictional and should not invite a person to enter their household balances, payment history, ownership history, or other sensitive financial data. A later proposal for durable saving—even of nominally fictional scenarios—requires its own privacy review.

## 8. Tests that should shape the design

The first implementation should include tests that establish:

- Exact expected outputs for every selected fictional input
- Determinism for identical inputs and versions
- Correct completed-unit and remainder boundaries immediately below, at, and above a threshold unit
- Separation of voluntary illustration from obligatory amount
- Structured traces whose arithmetic reconciles to the result
- Progressive disclosure: applicable provenance remains available without being mandatory in the initial display
- No network, database, filesystem, clock, UI, or provider dependency in the evaluation core
- No path by which an experimental comparison replaces an ordinary result
- No explorer composition dependency on private-workspace storage or personal-data imports

Architecture tests should enforce only meaningful boundaries that exist in the chosen stack. They should not require premature package proliferation.

## 9. Decisions intentionally deferred

This proposal does not select:

- Programming language, UI framework, hosting platform, or package layout
- Serialized fixture format
- Live or historical rate provider
- Gold instrument, market convention, assessment-rate composition, precision, or rounding policy
- Supported languages or localization framework
- Durable scenario saving, accounts, authorization, or analytics
- Private-ledger schema, lifecycle, reconciliation, replay, security, recovery, or deletion behavior

The [Deferred Private-Ledger Concepts](deferred-private-ledger-concepts.md) note preserves questions that may matter later without making them dependencies of the explorer.

## 10. Ready-to-code gate

The first threshold-ladder slice is ready to implement when:

1. Its exact fictional inputs and expected outputs are reviewed.
2. Every displayed proposition has a reviewed source-status classification and reference.
3. The meaning of principal, completed units, obligatory amount, and remainder is unambiguous for the selected cases.
4. The fictional-`U` abstraction and source-defined metric conversion are presented without implying an unsupplied market valuation.
5. The ordinary below-threshold outcome remains a low-complexity stopping point.
6. The selected stack can enforce a deterministic evaluation core and an explorer composition without private-workspace storage.
7. Accessibility and explanatory-copy expectations for the slice are explicit enough to test.

Later slices should pass the same gate for the additional concepts they introduce. The architecture should grow from reviewed vertical cases, not from an attempt to model the eventual private ledger in advance.
