# Repository Instructions for Agents

## Human review ledger is required

`docs/human-review-checklist.md` is the authoritative record of deliberate **human** review. Treat its checked state as evidence about a particular document version, not as a general approval that survives later edits.

### Before changing documentation

1. Read `docs/human-review-checklist.md`.
2. Identify every whole-file and section-level checklist scope the proposed change may affect.
3. Note whether any affected scope is currently checked.

### Maintain the ledger in the same change

- Never check a human-review box because an agent read, generated, validated, or reviewed the material. A box may become checked only when a human explicitly confirms that the named scope was reviewed.
- When a substantive edit affects a checked section, change that section's box from `[x]` to `[ ]`. Also reopen its whole-file box if that box is checked.
- Substantive edits include changes to meaning, claims, interpretations, formulas, examples, sources, scope, structure, or user-facing explanation.
- Purely mechanical edits—such as whitespace, formatting, or correction of a typo that cannot alter meaning—do not normally invalidate review. State that judgment in the completion report.
- When adding, deleting, renaming, moving, splitting, or combining a document or section, update the checklist's file and section coverage to match. Preserve a checked state only when the reviewed content and meaning are unchanged; when uncertain, reopen it.
- Record reopened reviews and structural ledger changes in the review log. Routine checkbox and log maintenance does not by itself invalidate review of the checklist; changes to the checklist's policy or scope structure do.

### Check for misses before finishing

Compare the changed files and headings with the ledger before completing any task that changes repository documentation.

- If a changed scope has no checklist entry, add one and alert the user.
- If an earlier substantive change appears to have left a stale `[x]`, reopen it, record the correction, and alert the user.
- If review validity is uncertain, do not silently preserve a checked state. Reopen it and explain the uncertainty.
- Do not silently infer a reviewer, review date, or review outcome from a PR comment, approval, agent review, or passing check.

Every completion message and pull-request description for repository changes must include one of these explicit statements:

- `Human review ledger: updated — <scopes changed or reopened>.`
- `Human review ledger: checked — no update needed because <reason>.`
- `Human review ledger warning: <missing, stale, or uncertain coverage and what was done>.`

If the agent cannot update the ledger or determine the affected scope, it must tell the user before presenting the work as complete.
