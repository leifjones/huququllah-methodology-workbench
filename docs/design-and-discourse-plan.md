# Design and Discourse Plan

**[PLACEHOLDER: This document will contain the full vision, reorganized and corrected per v0.2 requirements]**

## Sections to be populated

1. **Overall posture and invitation** — Research project, learning orientation, invitation to contribute

2. **Methodology taxonomy** — CORRECTED FROM V0.1
   - Authoritative constraints (what the sources explicitly establish)
   - Bookkeeping lenses (annual surplus, wealth reconciliation, transaction-basis ledgers)
   - Individual judgment points (necessitousness, timing, spouse structure, exceptional cases)
   - Experimental hypotheses (gold-indexing of fiat principal, revaluation approaches)
   - Voluntary practices beyond threshold (e.g., 19% of income irrespective of amount)
   - Software operating modes (manual recordkeeping, calculator modes)

3. **Gold-indexing as blocking hypothesis**
   - Fictional counterexample: gold rises, sheltering new acquisition
   - Fictional counterexample: gold falls, creating phantom difference
   - What this establishes and does not establish
   - Why source validation is required

4. **Assessment and payment as separate events**
   - Why the v0.1 formula fails
   - Counterexample: delayed payment with gold movement
   - Revised data model distinguishing assessment events from payment events
   - Assessment-payment allocation (one-to-many, many-to-one settlement)

5. **Event-based accounting model**
   - Why snapshots alone are insufficient
   - Financial event categories (acquisition, income, transfer, reclassification, gain, loss, recovery, gift/inheritance, disposal, ownership change, assessment, payment, correction)
   - Current holdings as derived/reconciled view
   - Supported, unresolved, and out-of-scope cases

6. **Ownership and couple modeling**
   - Property owned vs. controlled vs. used
   - Corporate ownership vs. individual interest
   - Payment source vs. obligation owner
   - Effective-dated ownership records
   - Scope flagging: non-Bahá'í spouses, trusts, custodial property, etc.

7. **Partial units and rounding clarification**
   - Source-grounded whole-unit treatment
   - Carry-forward below a complete additional unit
   - Ordinary decimal rounding
   - Timing discretion
   - NOT a freely configurable "rounding" setting

8. **Multi-currency design and phantom gains**
   - Why converting all holdings at current FX can create phantom gains
   - Original vs. functional currency
   - Realization of currency gains
   - Assessment-date vs. current FX
   - Physical gold and non-currency assets
   - Blocking questions

9. **Vocabulary model — revised**
   - Financial fact vs. ownership fact vs. source rule vs. user judgment vs. classification confidence
   - Assessment status vs. payment status
   - Revised definitions avoiding circular conclusions

10. **Public vs. private product separation**
    - Begin with public methodology explorer (fictional data, methodology comparison, terminology development)
    - Defer private ledger (requires threat model, privacy architecture, key recovery, couple permissions)

11. **User experience outline**
    - Setup and mode selection
    - Holdings table and judgment interface
    - Assessment and comparison dashboards
    - Methodology statement generation and export
    - Tone and spiritual safety

12. **Data model — event/provenance centered**
    - Household/workspace
    - Participant
    - Financial events (with type, date, amount, currency, classification, rationale)
    - Assessment event (distinct from payment)
    - Payment event (distinct from assessment)
    - Assessment-payment allocation
    - Rate snapshots (gold and FX)
    - Ownership records (effective-dated)
    - Methodology profile and decision log

13. **Implementation phases — frozen pending specification**
    - Phase 0: Clarify and validate (calculation specification, consultation)
    - Phase 1: Blocked until Phase 0 completes
    - Phase 2: Blocked
    - Phase 3: Blocked
    - Phase 4: Blocked

---

**STATUS:** This section requires complete rewrite per the critique. Current v0.1 content is preserved in the repository history but does not reflect the revised conceptual model. See `docs/open-questions-and-counterexamples.md` and `docs/source-rule-matrix.md` for supporting analysis.
