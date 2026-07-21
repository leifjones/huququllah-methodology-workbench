# Draft Implementation Architecture

**Status:** Pre-specification architecture proposal; not an implementation specification, technology selection, or authorization to accept real financial data

**Purpose:** Describe a restrained software structure that could implement a reviewed calculation specification without collapsing the project's source, methodology, judgment, hypothesis, and recordkeeping distinctions.

**Review posture:** Candidate planning material. Relevant human-review scopes remain open, and the calculation-specification workbook remains the recommended next deliverable.

This proposal is downstream of the [Design and Discourse Plan](design-and-discourse-plan.md), [Source-Rule Matrix](source-rule-matrix.md), [Calculation Invariants](calculation-invariants.md), and [Draft UX and Feature Proposals](draft-ux-and-feature-proposals.md).

It does not resolve open calculation questions, make an experimental methodology authoritative, select an implementation stack, or move the private ledger ahead of its privacy and security prerequisites.

## 1. Architectural posture

The recommended starting point is a **modular monolith with a functional core and imperative shell**.

The functional core contains deterministic domain values, calculations, state transitions, comparisons, and explanation traces. The imperative shell coordinates user interaction, clocks, identifiers, rate retrieval, persistence, imports, exports, authorization, and presentation.

The calculation core should not:

- Read the current time
- Fetch a live market rate
- Query storage
- Inspect environment configuration
- Look up behavior through a service locator
- Render user-facing prose
- Infer semantic defaults from missing information

Every value needed for evaluation should be supplied explicitly in an immutable input. An unresolved value should remain unresolved rather than becoming zero, exempt, voluntary, or settled.

Implementation remains conditional on the specification-readiness criteria in the design plan. Initial code should prove fictional cases and dependency boundaries rather than anticipate every possible private-ledger feature.

## 2. Product and module boundaries

The public methodology explorer and any future private ledger should share appropriate domain modules but have **separate composition roots and deployable hosts**.

The explorer must not be a private ledger with storage disabled by a feature flag. Its dependency graph should make durable personal-financial storage unavailable by construction.

A future private-ledger host may compose storage, encryption, recovery, permissions, deletion, and permission-scoped diagnostic adapters only after the privacy and security phase is complete.

Candidate logical modules are:

| Module | Responsibility |
| --- | --- |
| Shared model | Money, currency, dates, identifiers, ownership shares, provenance, and uncertainty |
| History | Financial facts, ownership intervals, classifications, decisions, remittances, and captured rates |
| Assessment | Frozen inputs, source-constrained evaluation, previews, committed assessments, and amendments |
| Settlement | Obligations, payments, allocations, reversals, balances, and reconciliation |
| Methodology | Bookkeeping lenses and versioned operating assumptions |
| Research | Experimental hypotheses and comparative views |
| Explanation | Structured traces, diagnostics, divergence reasons, and evidence references |
| Application | Preview, compare, commit, amend, allocate, reconcile, replay, import, export, and deletion use cases |
| Explorer host | Fictional scenarios, presentation, accessibility, and Phase 1 composition |
| Private-ledger host | Deferred composition for real private data |

These should begin as logical feature folders. They need not become separate packages or assemblies until a dependency boundary benefits from enforcement.

A possible initial shape is:

```text
src/
  Workbench.Core/
    Model/
    History/
    Assessment/
    Settlement/
    Methodology/
    Research/
    Explanation/
  Workbench.Application/
    Preview/
    Compare/
    Commit/
    Amend/
    Reconcile/
    Replay/
    Ports/
  Workbench.Explorer/
    Scenarios/
    Presentation/
    Composition/

tests/
  Invariants/
  Acceptance/
  Replay/
  Contracts/
  Architecture/

fixtures/
  fictional/
```

## 3. Canonical assessment and extension seams

The ordinary assessment path should use a **closed, explicit, versioned kernel**. Runtime configuration, registration order, reflection, a plugin, or a methodology profile must not silently remove, replace, or reorder source-constrained behavior.

The source-defined mithqál basis, whole-unit gate, 19% rate, once-only treatment, and obligatory-versus-voluntary separation are not user-selectable strategies. A substantive change requires a new specification/kernel version, updated expected cases, traceable rationale, and appropriate review.

Calculation order is domain meaning. A small concrete coordinator should make that order visible instead of hiding it in a generic rule engine or chain of responsibility.

Extensibility belongs around genuine variation:

| Existing taxonomy | Candidate software form |
| --- | --- |
| Authoritative constraint | Required behavior in the closed versioned kernel |
| Bookkeeping lens | Selectable projection over the same frozen history |
| Individual judgment | Effective-dated input record, not registered code |
| Experimental hypothesis | Opt-in, non-committable comparison |
| Voluntary practice | Payment intent and reporting state separate from obligation |
| Software operating assumption | Explicit versioned profile data |

A candidate evaluation flow is:

```text
Frozen history
  -> bookkeeping lens
  -> normalized assessment case
  -> versioned source-constrained kernel
  -> assessment preview
  -> explicit commit

Same facts + ordinary preview
  -> experimental research view
  -> non-committable comparison

Payments + deliberate allocations
  -> reconciliation + structured explanation
```

Only an explicitly reviewed application path may create an allocatable obligation. The canonical assessment path is one such path; an experimental comparison never is. A historical-reconstruction or previously calculated external-obligation claim is likewise non-allocatable. If the product supports confirmation of such a claim, a separate provenance-bearing path must create an obligation record. Whether that path should exist and what it requires remain open, and it must not represent an imported or reconstructed result as having been produced by the canonical kernel.

The exact normalized assessment case remains an open specification question.

## 4. Interfaces, ports, and adapters

Interfaces should mark genuine variation or an external boundary, not decorate every domain class.

Candidate strategy interfaces include:

- `IBookkeepingLens`, projecting frozen history into a normalized assessment case
- `IResearchView`, producing a labeled comparison without producing a committable assessment

Candidate application ports include:

- `IFictionalScenarioSource` for curated explorer cases
- `IRateObservationSource` for obtaining an external gold or FX observation
- `IExplanationRenderer` for presentation-specific output
- An explicit export boundary
- Clock and identifier sources used only by application commands
- A future use-case-specific private history store
- A future permission-scoped, read-only diagnostic query surface

The evaluator consumes captured rate evidence—`RateSnapshot` references and their purpose-specific `RateApplication` records—not a rate provider. A rate adapter retrieves and normalizes one or more observations before calculation while preserving provider, instrument, units, effective time, retrieval time, purpose, and evidence. The exact rate composition required by an assessment remains an open specification question.

A legacy-import adapter should be an anti-corruption boundary. It preserves known payments as facts while labeling payment-derived assessment dates, units, or principal as estimates or historical inferences.

Persistence boundaries should reflect use cases. A generic `IRepository<T>` would obscure commitment, amendment, dependency, allocation, and full-deletion semantics.

The future diagnostic interface should expose structured reconciliation through the application layer rather than provide direct access to domain storage. The same explanation must remain available in the product without requiring an agent.

## 5. State and lifecycle boundaries

The architecture should distinguish:

- **Recorded facts:** original amount, currency, date, owner, and provenance
- **Decision records:** a person's judgment or intent, its effective date, and optional rationale
- **Committed calculation records:** historical assertions produced from frozen inputs under identified versions
- **Derived views:** holdings, converted values, balances, comparisons, and current-gold translations

Derived views do not replace their inputs. A converted value retains the original native amount and the applied rate evidence.

A committed assessment is not edited in ordinary use. A correction or reconsideration creates a linked amendment. Semantic immutability does not prohibit explicit privacy deletion: deletion may physically remove records and must remove, invalidate, or recalculate dependents consistently.

The state distinctions in the remittance UX must survive implementation:

- A remittance fact does not establish an obligation.
- Intent at remittance does not establish eligibility for credit.
- Lack of a recorded assessment does not make a payment voluntary.
- Settlement intent pending assessment does not manufacture an obligation.
- A committed assessment does not allocate an earlier payment automatically.
- A later treatment supplements rather than silently rewrites original intent.
- Only a deliberately allocated portion contributes to obligation credit.

Suggested payment matches are query results. Allocation requires a separate confirmation command.

## 6. Safe syntactic builders

A small fluent syntax may make fictional scenarios and executable acceptance cases readable. Builders construct validated immutable inputs; they do not become a second calculation engine.

A safe builder must not:

- Read today's date
- Retrieve a live rate
- Choose a default epistemic category silently
- Treat missing intent as voluntary
- Infer ownership or classification
- Commit an assessment or allocate a payment
- Hide recorded currency or rate purpose
- Execute expressions supplied by scenario data

Required uncertainty should be explicit, such as `.Intent(Unresolved)`. `Build()` should return validation diagnostics rather than a partially valid object.

Illustrative syntax, not a selected API:

```csharp
var scenario = FictionalScenario.Named("payment-before-assessment")
    .On(paymentDate)
        .Remittance(Usd(500))
        .Intent(SettlementPendingAssessment)
    .On(assessmentDate)
        .AssessmentRateEvidence(assessmentRateEvidence)
        .AssessableProperty(Usd(10_000))
        .Classification(Subject, IndividualJudgment)
    .Build();

var preview = kernelV1.Evaluate(
    lensV1.Project(scenario.FrozenHistory, scenario.Profile));

var comparison = indexedCreditV1.Compare(
    scenario.FrozenHistory, preview.Value);
```

The kernel derives the local-currency threshold value from the fixed source-defined weight and the supplied assessment-rate evidence. A caller cannot provide a threshold amount directly.

Production commands may use named constructors when they express requirements more plainly than a fluent builder.

## 7. Explicit registration and composition

Registration should be explicit, immutable, role-specific, and fail fast. The explorer composition root names the exact kernel, lenses, research views, renderers, and fictional scenario sources it includes.

Separate catalogs may be useful for:

- Required kernel/specification versions
- Bookkeeping lenses
- Experimental research views
- Presentation renderers
- Serialized fictional-scenario schema versions

Registration should reject duplicate identifiers, missing versions, unknown dependencies, and category mismatch.

Reflection scanning, keyed runtime rule lookup, global mutable registries, and service-container access inside domain or application code should be avoided. A methodology profile references known identifiers and versions; it does not contain executable rules.

The explorer composition root must not reference private-ledger storage, recovery, or real-workspace adapters.

## 8. Structured explanations and multilingual readiness

Every evaluation should return a structured result rather than a number plus log text. A candidate result includes:

- Completion status
- Typed value, when complete
- Calculation trace
- Diagnostics
- Input fingerprint
- Specification and methodology versions

Trace nodes should carry stable semantic identifiers, exact numeric inputs and outputs, applicable source and decision references, epistemic information, child steps, and structured presentation parameters.

Diagnostics should distinguish blocking invalidity, unresolved questions, warnings, and informational notices. An incomplete result should identify the missing or unresolved inputs.

Alternative lenses either reconcile or return structured divergence reasons such as classification, timing, missing event, valuation, ownership, or hypothesis. Payment reconciliation returns named categories rather than an unexplained residual.

### Multilingual design note

This proposal does not select supported languages, translation tooling, localization libraries, or a delivery schedule.

The model should use stable language-neutral identifiers and keep localized presentation separate from calculation and provenance. Stored values, currency identities, dates, rule identifiers, and calculation parameters remain locale-independent.

Calculation and diagnostic code should emit structured semantic identifiers and parameters rather than assembled English sentences. Localized labels must never be parsed as domain identifiers or rule names.

Language or locale selection must not change primary currency, rate convention, assessment date, ownership scope, rounding, or methodology. Multi-language and multi-currency support are orthogonal concerns.

Source quotations and translations require language and provenance metadata. Official source translations must remain distinguishable from project-authored or user-supplied wording. Externalizing strings does not establish that a translation is authoritative, reviewed, complete, or safe for private financial text.

Right-to-left layout, bidirectional text, text expansion, pluralization, font coverage, accessibility, and knowledgeable terminology review remain future acceptance concerns rather than current framework commitments.

## 9. Versioning and replay

Historical replay must not depend on current rates, current posture, current locale, or the latest implementation.

A committed assessment should pin at least:

- Record-schema version
- Kernel/specification version
- Bookkeeping-lens version
- Methodology-profile revision
- Source-catalog version
- Precision convention
- Rate-snapshot identifiers
- Ordered input identifiers or content hashes
- Input fingerprint

Replay resolves the recorded versions. If an exact version is unavailable, it reports that limitation instead of silently substituting the latest behavior.

Re-evaluation under a newer specification or lens produces a comparison or amendment preview. It does not rewrite the historical record.

The project still needs to decide whether old executable bundles remain runnable indefinitely or whether a frozen input, result, and trace are sufficient for some records.

Deletion may deliberately make replay impossible. Dependent records must not remain apparently valid after their basis is removed.

## 10. Phase 1 persistence and privacy posture

Phase 1 should durably retain only curated fictional fixtures, explanatory content, and non-financial application assets.

It may support guided authoring and constrained transformations of fictional scenarios, provided the interface clearly frames them as fictional. It should not provide an unrestricted personal-finance workspace, invite real household-financial entry, or accept free-form personal notes, receipt uploads, or imports. Interactive authored state may remain session-scoped and in memory.

A user-requested fictional export may be generated without creating a retained workspace. Rate retrieval, if offered, should not transmit scenario financial values to a provider.

The safest explorer composition has no general workspace-storage port or adapter. A later proposal for durable scenario saving requires separate privacy review and an architecture update.

For a future private ledger, ordinary relational storage with typed records, immutable committed revisions, explicit amendments, and rebuildable projections is a plausible starting posture. This is not a normalized schema selection.

Full event sourcing is not the default. Event-like domain records do not require an event store, and replay and append-only retention create unresolved semantic-versioning and privacy-deletion costs.

## 11. Rejected or conditional patterns

- **Dynamic rule engine — rejected initially:** source-constrained behavior should not be rewritten through configuration or user formulas.
- **Plugin or reflection-based rule discovery — rejected initially:** unreviewed behavior must not self-activate.
- **One universal methodology interface — rejected:** it would collapse constraints, lenses, judgments, hypotheses, voluntary practices, and assumptions.
- **Full event sourcing — conditional:** chronological records and replay may be useful, but semantic evolution and deletion remain unresolved.
- **Full CQRS, mediator bus, or event bus — conditional:** explicit commands and queries are useful; infrastructure frameworks are not yet justified.
- **Generic repositories or active record — rejected:** they obscure lifecycle and deletion behavior.
- **Microservices — rejected for the foreseeable scope:** separate product hosts do not require distributed domain services.
- **Explorer/private host selected by feature flag — rejected:** the privacy boundary should be structural.
- **Automatic payment allocation — rejected:** suggestions may be generated, but allocation requires confirmation.
- **Explanation reconstructed from logs — rejected:** domain steps emit their own semantic trace.
- **Double-entry postings — conditional:** they may help conservation if the normalized specification demonstrates a fit.
- **Durable Phase 1 workspace persistence — rejected by default:** it weakens the fictional-only boundary.

## 12. Architectural fitness tests

Automated tests should enforce that:

- Core modules have no database, network, filesystem, clock, UI, provider, or framework dependency.
- Authoritative calculation does not depend on experimental, registration, persistence, or presentation code.
- Evaluation is deterministic for identical frozen inputs and versions.
- Historical replay succeeds without network, clock, database, or current rate services.
- Methodology profiles cannot disable or replace required source-constrained behavior.
- Missing intent, classification, date, rate, or currency does not receive a semantic default.
- Only explicitly reviewed application paths can construct an allocatable obligation; experimental code cannot.
- Raw reconstruction and external-obligation claims or previews cannot enter allocation or canonical-assessment persistence. Any future confirmation path must produce a provenance-bearing obligation record without relabeling it as kernel-generated.
- Committing an assessment does not create a payment allocation.
- Suggested matches do not create allocations.
- Allocations conserve payment and obligation value through partial allocation, conversion, excess, and reversal.
- Current rates, posture, locale, and display currency do not mutate historical results.
- Draft mutation, amendment, and full deletion remain distinct operations.
- Recorded currency remains available beside every converted view.
- Every converted value exposes rate purpose and provenance.
- Every displayed proposition exposes applicable source, computational role, version/posture, and fact provenance without relying on one ambiguous status.
- Every invariant has an executable fictional acceptance case.
- Alternative lenses reconcile or provide structured divergence.
- Semantic trace values remain unchanged across presentation locales.
- The public build has no durable arbitrary-financial-data write path.
- Full deletion removes or invalidates dependent projections and diagnostic copies.

## 13. Open decisions

Before implementation, the project still needs to decide:

1. What normalized input every bookkeeping lens must produce
2. Which calculation sequence and formulas constitute the first closed kernel
3. Which terminology is canonical across source basis, computational role, posture, provenance, and human-review state
4. What exact event and decision revisions an assessment commit freezes
5. How carried principal and sub-unit remainder survive currency or methodology changes
6. Whether and under what reviewed treatment a voluntary contribution may receive later obligation credit
7. Whether unresolved intent is the entry default and whether one remittance may carry split intent
8. Which evidence may support a non-binding allocation suggestion
9. Whether a previously calculated external obligation or historical reconstruction may become allocatable and, if so, what confirmation and provenance requirements would prevent representing it as kernel-generated
10. Which guided inputs and constrained transformations of fictional cases the Phase 1 explorer needs
11. What evidence and executable versions must remain available for replay
12. How amendments distinguish corrected facts, reconsidered judgments, and newly available information
13. What dependency model governs deletion and recalculation
14. Whether balanced postings improve the normalized financial-event model
15. Which module boundaries eventually require compile-time enforcement
16. Which implementation language, storage technology, and UI framework fit the reviewed specification
17. What multilingual content-governance and review process would be required before supporting any language
18. What privacy, security, and permission decisions would permit a private ledger

Until these decisions and the specification-readiness criteria are satisfied, this document remains an architecture hypothesis and review aid rather than a commitment to build.
