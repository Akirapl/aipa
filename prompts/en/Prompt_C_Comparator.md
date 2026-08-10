# AI Interaction Pattern Assessment (AIPA)
## v0.4 — Prompt C: COMPARATOR (split mode)

*Author: Dawid Kulik, B. Eng — [github.com/akirapl](https://github.com/akirapl) — akira3179082@gmail.com*

---

## Role and context of this prompt

This prompt is the third stage of the four-part split procedure. The COMPARATOR gathers **no evidence of its own** from chat histories and assigns **no classifications of its own**. Its sole task is to compare two or more judge reports attached to this chat as files. Admissible inputs:

- **AIPA-K** (question complexity, K1–K5) from Prompt A
- **AIPA-E** (correction events, E1–E5) from Prompt B

Two comparison directions: **longitudinal** (multiple reports of the same instrument over time) and **cross-instrument** (K vs. E, convergent validity).

**Forbidden:** chat history search, re-rating individual dimensions, "correcting" judge classifications.

**REFLECT rule (new in v0.4):** Reports from v0.4 onward contain an "AIPA-REFLECT" block at the end. This block is maintenance material for Prompt D and **not a finding**. The Comparator IGNORES its content entirely: no quoting from it, no use as comparison evidence, no evaluation. The only permitted mention: noting the block's presence/absence in the intake check (Phase 0).

---

## Process overview (strictly sequential)

| Phase | Content | Completion checkpoint |
|---|---|---|
| 0 | Intake check of reports | "Phase 0 complete" |
| 1 | Comparison per dimension | "Phase 1 complete" |
| 2 | Meta-analysis of the series | "Phase 2 complete" |
| 3 | Validation + overall assessment | "Phase 3 complete" |

---

## PHASE 0 — Intake check

For each attached report, check the metadata block and document in a table:

0. **Instrument type** — AIPA-K or AIPA-E? Sort reports into two tracks. Longitudinal comparisons (Phase 1) ONLY within the same track. Cross-track statements only in Phase 2. K-levels and E-levels are NEVER computed directly against each other — they measure different constructs.
1. **Instrument and procedure version** — identical within a track? If not: name the differences, mark the comparison as "limited comparability." Comparisons between methodologically different predecessors (e.g., a numeric score) and the K taxonomy are permitted only at the level of profile shape.
2. **Blindness** — which reports were blind (split mode), which contaminated? Flag contaminated reports as anchoring-suspect: their agreement with predecessors carries less evidentiary weight.
3. **Data periods** — overlapping or disjoint? Document the degree of overlap (mostly overlapping / partial / disjoint). This drives the decision rule in Phase 1.
4. **Judge** — same or different model generation? Same generation, new instance = intra-generation retest. Different generation or platform = inter-generation/cross-platform test. Name the test type.
5. **Evidence base** — raw fragments vs. summaries per report. Summary-based reports carry less weight in cases of divergence.
6. **REFLECT block** — present yes/no (note existence only, do not read/use content).
7. **Protocol fidelity** — does a report itself declare deviations from the procedure (e.g., a run without active search, a substitute evidence base)? Flag such reports as "procedural deviation" and give them reduced weight.

If a metadata block is missing: mark the report "incomplete metadata," downgrade its evidentiary weight, do not abort.

**Checkpoint:** Output: "Phase 0 complete. Reports: [count]. Test type: [...]. Overlap degree: [...]."

---

## PHASE 1 — Comparison per dimension

For each dimension (track K) or each evaluation row (track E), build a comparison row across all reports in the track (dominant level/count, highest level, confidence), and classify each difference using the following decision rule:

### Decision rule: behavioral change vs. judge noise

A difference may only be scored as a **behavioral change** (↑ or ↓) if AT LEAST ONE condition is met:

1. Data windows are **disjoint or mostly disjoint** AND the difference is at least one full level of the dominant classification.
2. The difference **replicates across at least two consecutive report transitions** in the same direction.
3. The later report documents **new patterns not present in the earlier window** as the rationale (not merely a different weighting of the same patterns).

Otherwise — especially with mostly overlapping windows — the difference defaults to **judge noise** (different resolution of borderline cases, e.g., K3/K4), is marked with →, and is named as such.

Differences in confidence or stability are NOT a behavioral change, but properties of the judge or the evidence situation.

Mark trends with ↑ → ↓ and justify each assignment against the rule (which condition is/is not met).

**Checkpoint:** Output: "Phase 1 complete."

---

## PHASE 2 — Meta-analysis of the series

1. **Replicated findings:** What is stable across ALL reports in a track (profile signature, relative weaknesses, dominant overall level)? These count as hard findings. Replication across different platforms/corpora carries the most weight.
2. **Unstable findings:** What jumps between reports? Primarily a measure of the **instrument's inter-judge reliability**, not of user behavior — name it explicitly as an instrument property. Dimensions with repeatedly low agreement are to be reported as a definitional weakness in the taxonomy.
3. **Convergent validity (K ↔ E):** Defined touchpoints:
   - **Reflective Thinking (K)** ↔ **source/latency profile (E)** (share of self-corrections, share "in-flow"): the same construct viewed from two directions. Agreement → a strong convergent finding. Contradiction → name as an open discrepancy; do NOT decide which instrument is right.
   - **Depth of Inquiry (K)** ↔ **share of E3/E4**: weakly coupled — operating at K4 is a precondition for making E4-level errors at all. A high K-level combined with a complete absence of higher E-levels is notable and should be named.
   - Before making any substantive judgment about a discrepancy: check the E-instrument's visibility bias (structural undercounting of self-corrections).
4. **Blindness effect:** Do blind reports differ systematically from contaminated ones? If both yield identical profiles, this retroactively strengthens the credibility of the contaminated runs.

**Checkpoint:** Output: "Phase 2 complete."

---

## PHASE 3 — Validation and overall assessment

### Validation

1. Was every trend assignment (↑ → ↓) explicitly justified against the decision rule?
2. Was a judge's classification never altered or "corrected" anywhere?
3. Were differences in overlapping data windows treated as noise by default?
4. Does the comparison contain speculative statements about the causes of behavioral change? (Only observed patterns are permitted; motives and life circumstances are not.)
5. Was any personal or confidential information reproduced beyond abstracted patterns?
6. Was the REFLECT block of every report fully ignored (aside from the existence note in Phase 0)?

### Overall assessment

Two separate judgments, each **Low / Medium / High** with rationale:

1. **Reliability of the longitudinal/convergent finding** — how robust are the trends, replications, and convergences?
2. **Reliability of the instruments themselves** — how consistently do independent judges classify? Basis: extent of judge noise from Phase 1/2, per track.

**Checkpoint:** Output: "Phase 3 complete."

---

## Note on procedural hygiene (to the user, repeat in the report)

The Comparator report contains conclusions about earlier results from both instruments. It must **never** be attached to or quoted in a future judge chat (neither Prompt A nor Prompt B). Likewise, A and B reports must never be attached to each other. The Comparator report must also NOT be handed to Prompt D — D receives only REFLECT blocks. Judge chats receive only their own prompt, with no attachments.
