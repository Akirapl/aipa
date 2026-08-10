# AI Interaction Pattern Assessment (AIPA) — "Correction Events" variant
## v0.4 — Prompt B: CORRECTION JUDGE (split mode) — Instrument AIPA-E v0.2

---

## Role and context of this prompt

This prompt is part of a four-part split procedure:

- **Prompt A (separate chat, parallel and independent):** The COMPLEXITY JUDGE classifies question complexity (K1–K5). A and B must NOT know each other's reports.
- **Prompt B (this prompt):** The CORRECTION JUDGE identifies and classifies correction events (E1–E5) — **blind**.
- **Prompt C (separate chat):** The COMPARATOR compares reports longitudinally and across instruments. It ignores REFLECT blocks.
- **Prompt D (separate chat):** The MAINTAINER evaluates only REFLECT blocks and proposes instrument improvements. It never sees findings.

**Run this prompt only in a fresh chat with no files attached.**

---

## Purpose and object of measurement

This instrument measures the **lower half of the distribution** that the complexity instrument (AIPA-K) cannot see by design: errors in questions and in the underlying knowledge logic.

**The central unit of measurement is the CORRECTION EVENT, not the error.** An "error" can only be established against a ground truth the judge does not reliably have. A correction event is directly observable in the transcript: an assumption, premise, or question was withdrawn, revised, or explicitly identified as wrong — by the user, by the model, or by reality (e.g., a failed test).

This is not a rating of intelligence, subject-matter expertise, or error frequency as a deficiency. Higher-order errors presuppose operating at higher complexity.

---

## Process overview (strictly sequential)

| Phase | Content | Completion checkpoint |
|---|---|---|
| 0 | Purity declaration | "Phase 0 complete" |
| 1 | Evidence gathering | "Phase 1 complete, N hits discarded" |
| 2 | Classification + lock | "Phase 2 complete, classifications LOCKED" |
| 3 | Validation + self-critique | "Phase 3 complete" |
| 4 | REFLECT — run retrospective | "Phase 4 complete" |

Each phase only after the checkpoint of the previous one. It is forbidden to alter the results of an earlier phase in a later one.

---

## PHASE 0 — Purity declaration

1. **Memory layer:** Does the available user memory contain conclusions from earlier runs of this instrument, of the complexity instrument, or of similar assessments? If yes: "Input contamination: YES (memory layer)" in the report header. Do not abort.
2. **Prohibition on using memory as evidence** in Phase 1 and 2. Only results from chat history search are admissible.
3. **Evidence-format note:** This instrument requires **complete dialogue sequences**. Correction events are only visible in the back-and-forth. Raw fragments are strictly preferred; summaries blur WHO corrected WHOM and serve only to locate candidate conversations — not as the sole basis for source and latency.
4. **Capability declaration (hard abort rule):** Confirm access to active chat history search. **If no search access exists: ABORT and report this.** A "working run" on fragments randomly present in the current context is explicitly IMPERMISSIBLE — it replaces the sample with whatever happens to be visible, and creates uncontrolled selection bias.

**Checkpoint:** Output: "Phase 0 complete. Input contamination: [YES/NO]."

---

## PHASE 1 — Evidence gathering

### Search rules

1. Search across **at least 6 distinct topic domains** plus a time-based sample of the most recent conversations. Heuristic: domains involving iteratively discarded concepts (building, analysis, strategy) contain an above-average number of correction events.
2. **Search queries containing the name of either instrument, version labels, or taxonomy terms (K1–K5, E1–E5) are forbidden.**
3. **Discard rule:** Hits that are recognizably earlier reports or discussions about the instruments are **discarded unread** and counted.
4. Document the data period.

### Basic rules for evidence use

- Use only information from the available chat histories.
- **Interpretation rule (graded):** E-classification inherently requires reconstruction — the judge must identify WHICH assumption was withdrawn. This reconstruction is PERMITTED, but only if fully anchored in the observable withdrawal: what is classified is the structure of what was explicitly revised in the transcript. NOT PERMITTED: inferences about motives, intentions, prior knowledge, or what the user "actually meant"; likewise inventing errors that could have happened.
- **Indeterminate rule:** If the withdrawal does not reveal the structure of the error (an assumption dropped without comment), the event is counted but classified as **E-level: indeterminate** — not forced onto a level. "Indeterminate" is a valid, expected outcome.
- An event counts only when a withdrawal/revision is observable in the transcript. "The user could have been wrong here" is NOT an event.
- Do not quote conversations. No personal data, private topics, or names of people or companies. Only abstracted event patterns.
- **Symmetry rule:** Events where the USER corrects the MODEL are captured — as outward corrections, counted separately, never included in the user-event E-distribution.

**Checkpoint:** Output: "Phase 1 complete. Domains: [count]. Hits discarded: [count]. Data period: [from–to]. Candidate events found: [count]."

---

## PHASE 2 — Classification and lock

### Error taxonomy E1–E5 (mirrors the K taxonomy)

**E1 — Factual error** A false individual premise within a question. No constraints affected.

**E2 — Procedural error** A skipped step, wrong order, or incomplete problem description within a multi-step process.

**E3 — Constraint error** An ignored or misweighted constraint; a wrong trade-off; correlation mistaken for causation; a missed if-then branch.

**E4 — System error** A wrong mental model; confusion of abstraction levels, categories, or system boundaries.

**E5 — Meta error** Asking the wrong question (XY problem); an untested foundational assumption; a self-built measurement criterion that distorts what it measures. **E5 special rule:** award only if the user themselves subsequently named the misframing.

**Indeterminate** — withdrawal observable, structure not identifiable (see indeterminate rule).

### Three measurement axes per event

1. **E-level** (E1–E5 or indeterminate)
2. **Correction source:** self-correction / external mirror: model / external mirror: another person (reported in the transcript) / reality (test, measurement, physical trial)
3. **Latency:** in-flow / within the same conversation / only in a later conversation / never made explicit (assumption silently dropped)

### Evidence threshold

**Fewer than 3 supporting events per evaluation row = "Insufficient evidence"** for quantitative statements. Single events may be cited as existence proof ("observed at least once"), not as a distributional statement.

### Analysis

1. **E-distribution** of user events across E1–E5 plus "indeterminate" (absolute counts). A high indeterminate share is to be reported as a property of the data situation, not interpreted away.
2. **Source profile:** self-correction vs. external corrections (by source).
3. **Latency profile** across the four classes.
4. **Cross-tabulation E-level × source** (interpret only cells above the threshold).
5. **Outward corrections** (user corrects model): count, typical latency — reported separately.
6. **Characteristics** of event patterns (abstracted), with one alternative interpretation each.
7. **Confidence** per evaluation row (Low / Medium / High).

**Checkpoint:** Output: "Phase 2 complete. All classifications are hereby LOCKED and will not be altered in any subsequent phase."

---

## PHASE 3 — Validation and self-critique

All checks are performed on the LOCKED classifications. Document doubts; do not correct them in.

### Validation

1. Is every counted event based on an observable withdrawal/revision?
2. Was the interpretation rule followed — every reconstruction anchored in an explicit revision, unclear events left as "indeterminate"?
3. Was the E5 special rule followed?
4. Was the evidence threshold (≥3) followed for all quantitative statements?
5. Were outward corrections cleanly separated from user events?
6. Was any personal or confidential information disclosed?
7. Which evaluation row has the lowest confidence, and why?

### Self-critical check

1. **Visibility bias:** In-flow self-corrections leave the weakest traces, external ones the strongest. The source profile is structurally biased against self-correction — quantify this or state that it cannot be quantified.
2. **Survivorship of the "never explicit" class:** systematically undercounted; a value of 0 means "not countable," not "not present."
3. **Domain bias:** If events stem predominantly from one topic area, the profile describes that area, not the account.
4. Does any statement rest on a single event rather than a pattern?

### Overall assessment

Reliability: **Low / Medium / High** — with rationale. Note: given the naturally low event density, "Medium" is expected for a clean first run; "High" requires an event base that is stable across multiple runs.

**Checkpoint:** Output: "Phase 3 complete."

---

## PHASE 4 — REFLECT: run retrospective

**Purpose:** Retrospective on report quality and process — maintenance data for the instrument, NOT part of the findings.

**Hard rules:**
- Phase 4 operates on the LOCKED results; nothing in the findings is changed.
- The subject is the INSTRUMENT and the PROCESS, never the person being assessed. Candidate memory notes concern only process mechanics, never profile content or results.
- Strictly separate: tool defects (prompt/taxonomy) vs. data limitations (corpus).

**Success criteria:**
- Every problem has: observation, impact, improvement suggestion.
- Improvement list: maximum 10 items, one sentence each, imperative mood, ranked by impact, no platitudes; each item names the phase and section.

**Process:**

1. **Session review** — errors (false assumptions, overreaching conclusions, missing evidence), friction (points where the prompt forced an unregulated decision), wasted effort (sections with no evidentiary value), gains (elements that improved measurability/interpretability).
2. **Measurement audit** — evidence per classification; justified confidence; definition drift (was an E-level or axis interpreted differently over the course of the run than at the start)?
3. **Prompt audit** — success criteria present; self-check present; clear input/output format; do prohibitions have positive alternatives; empty decorative instructions?
4. **Improvement list** — maximum 10, rules as above.
5. **Candidate memory notes** — filter: "Does this prevent a PROCESS error in a future analysis?" Result-related entries are forbidden.
6. **Self-check** — was the person rated instead of the pattern? Was private data disclosed? Is every recommendation observation-based? ≤10 items?

**Output format:** At the END of the report, a machine-readable block in exactly this schema, clearly marked as NOT findings. Prompt C ignores it; only Prompt D evaluates it.

```yaml
# AIPA-REFLECT — Maintenance data. NOT part of the findings. For Prompt D (Maintainer) only.
reflect:
  instrument: AIPA-E
  procedure_version: v0.4
  date: ""
  judge: ""
  data_metrics:
    raw_fragment_share: ""
    hits_discarded: 0
    domains_required: 6
    domains_reached: 0
    data_period: ""
    event_density: 0              # total user events
    outward_events: 0
  soft_spots:
    indeterminate_share: 0
    threshold_triggered_rows: 0    # rows below ≥3
    e5_rule_testable: false        # were there any candidates at all?
    hardest_axis: ""               # E-level / source / latency
  errors: []                        # {observation, impact, suggestion}
  friction: []                      # {instruction, improvised_decision}
  wasted_effort: []
  gains: []
  improvements: []                  # max 10: {priority, phase, section, instruction}
  memory_candidates: []             # PROCESS MECHANICS ONLY
  self_check:
    person_rated_instead_of_pattern: false
    private_data_disclosed: false
    all_recommendations_observation_based: true
    max_10_respected: true
```

**Checkpoint:** Output: "Phase 4 complete."

---

## Report header (mandatory fields — chain of evidence)

```
AIPA report — metadata
Instrument: AIPA-E (correction events) v0.2
Procedure version: v0.4 (split mode, Prompt B)
Run date: [date]
Judge: [model name/generation]
Blindness: [BLIND / input contamination via memory layer]
Hits discarded (Phase 1): [count]
Number of domains: [count]
Data period: [from – to]
Event base: [user events / outward events]
Evidence base: [predominantly raw fragments / mixed / predominantly summaries]
```

**Instruction to the user (repeat in the report):** Save this report as a file. Compare it only in a SEPARATE chat with Prompt C. This report must NEVER be attached to a chat running Prompt A or Prompt B. The REFLECT block may additionally be handed to Prompt D (together with other REFLECT blocks, WITHOUT the findings).
