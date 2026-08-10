# AI Interaction Pattern Assessment (AIPA) — "Question Complexity" variant
## v0.4 — Prompt A: COMPLEXITY JUDGE (split mode)

*Author: Dawid Kulik, B. Eng — [github.com/akirapl](https://github.com/akirapl) — akira3179082@gmail.com*

---

## Role and context of this prompt

This prompt is part of a four-part split procedure:

- **Prompt A (this prompt):** The COMPLEXITY JUDGE classifies question complexity (K1–K5) — **blind**, with no knowledge of prior reports.
- **Prompt B (separate chat, parallel and independent):** The CORRECTION JUDGE classifies correction events (E1–E5). A and B must NOT know each other's reports.
- **Prompt C (separate chat):** The COMPARATOR compares judge reports longitudinally and across instruments. It ignores REFLECT blocks.
- **Prompt D (separate chat):** The MAINTAINER evaluates only the REFLECT blocks from multiple runs and proposes improvements to the instrument. It never sees findings.

**Run this prompt only in a fresh chat with no files attached.**

---

## Purpose

Analyze only the chat history available on this account. The goal is not to assess personality, intelligence, or subject-matter expertise. The object of analysis is the structural complexity of the questions and requests that serve as evidence for each dimension. What is being scored is not the quality of an answer, and not the intensity of a behavior, but the complexity of the questions asked. The analysis serves solely to describe usage behavior.

---

## Process overview (strictly sequential)

| Phase | Content | Completion checkpoint |
|---|---|---|
| 0 | Purity declaration | "Phase 0 complete" |
| 1 | Evidence gathering | "Phase 1 complete, N hits discarded" |
| 2 | Classification + lock | "Phase 2 complete, classifications LOCKED" |
| 3 | Validation + self-critique | "Phase 3 complete" |
| 4 | REFLECT — run retrospective | "Phase 4 complete" |

A phase may only begin once the checkpoint of the previous phase has been explicitly issued. It is forbidden to alter the results of an earlier phase in a later one.

---

## PHASE 0 — Purity declaration

1. **Memory layer:** Does the available user memory contain conclusions, results, or ratings from earlier runs of this instrument (or a substantially similar assessment)?
   - If yes: note in the report header "Input contamination: YES (memory layer)". Do NOT abort.
   - If no: note "Input contamination: NO".
2. **Prohibition on using memory as evidence:** The memory layer must NOT be used as an evidence source in Phase 1 and 2. The only admissible evidence is results from searching the chat history (raw fragments preferred, summaries secondary and flagged as such).
3. **Capability declaration:** Confirm that access to chat history search exists. **If no access exists: abort and report this.** A substitute run on fragments randomly present in the current context is not permitted — the instrument cannot be executed without search access.

**Checkpoint:** Output: "Phase 0 complete. Input contamination: [YES/NO]."

---

## PHASE 1 — Evidence gathering

### Search rules

1. Run searches across **at least 6 distinct topic domains** (e.g., technical diagnostics, project work, conceptual topics, formal/administrative matters, everyday requests, editorial tasks). In addition: a time-based sample of the most recent conversations, to reduce selection bias.
2. **Search queries containing the name of this instrument, its version labels, or its taxonomy terms are forbidden.**
3. **Discard rule:** Hits that are recognizably earlier reports from this instrument, or discussions about the instrument itself, are **discarded unread** and counted.
4. Prefer raw fragments of actual exchanges over summaries. If a classification rests predominantly on summaries, this must be stated in the confidence rating.
5. Document the observed data period (earliest and latest date).

### Basic rules for evidence use

- Use only information from the available chat histories.
- Do not speculate.
- Assess complexity solely on the observable structure of the questions, not on assumed intent.
- If no questions are available to support a dimension, explicitly write "Insufficient evidence."
- Do not quote conversations. Do not reproduce personal data, private topics, or the names of people or companies. Describe only abstracted question patterns.
- **Attribution rule:** Only the structure of the USER's questions is classified. Complexity found in model answers is not evidence. For summaries where question and answer have merged: rate lower when in doubt, or flag as uncertain.
- **Borderline-case protocol:** Every case where the assignment between two adjacent levels (especially K3/K4) appears undecidable is counted, and the decision heuristic used is noted. This count feeds into Phase 4.

**Checkpoint:** Output: "Phase 1 complete. Domains: [count]. Hits discarded: [count]. Data period: [from–to]."

---

## PHASE 2 — Classification and lock

### Complexity taxonomy

**K1 — Factual / point** A single factual question with exactly one correct answer. Retrieval of definitions or isolated facts, no constraints involved.

**K2 — Procedural / multi-step** A question about a multi-step procedure, or one with context. Sequential, without competing constraints.

**K3 — Analytical / conditional** A question with multiple constraints, comparisons, trade-offs, or if-then branches. Requires weighing options.

**K4 — Synthetic / systemic** The question integrates multiple concepts or fields, targets design or architecture, or anticipates second-order effects.

**K5 — Generative / meta** The question interrogates the problem framing itself, examines its own assumptions, generates new conceptual structures, or is recursive/self-reflective.

### Analysis dimensions

Characterize each dimension by: dominant complexity level (K1–K5), highest level observed, stability (consistent / sporadic / rising / falling — relative only to the current data window), confidence (Low / Medium / High), rationale, characteristics of the observed questions (abstracted, no quotes), possible alternative interpretation. Without supporting questions: "Insufficient evidence."

**1. Curiosity** — Tendency to actively explore new topics, ask about underlying mechanisms, and build knowledge beyond the immediate problem at hand. Marker: questions address the mechanism of action rather than just the application.

**2. Depth of Inquiry** — Systematic deepening through follow-up questions, constraints, counterexamples, detailed analysis. Marker: layered follow-up questions that introduce constraints or counterexamples into a previous answer.

**3. Iterative Learning** — Revisiting and building on earlier topics across multiple conversations. Marker: revisited questions build on prior results instead of repeating them.

**4. Cross-domain Integration** — Transfer of concepts between fields. Marker: questions connect multiple — ideally distant — domains within a single question.

**5. Problem-solving Behaviour** — Development of durable solution processes rather than one-off answers. Marker: questions aim at reusable procedures or root-cause analyses.

**6. Information Seeking** — Active search for sources, alternatives, literature, comparisons, evidence. Marker: questions weigh multiple sources or options against each other.

**7. Reflective Thinking** — Critical evaluation of one's own assumptions, strategies, and decisions. Marker: questions make the user's own assumptions the object of inquiry. **v0.4 refinement:** Distinguish and report two subforms separately: (a) DESIGNED reflection — the user builds structures/tools whose purpose is to test their own assumptions; (b) SPONTANEOUS reflection — the user questions their own assumptions in the middle of a substantive process, without being structurally forced to. The dimension's dominant level must be formed from BOTH subforms; a high rating based solely on subform (a) must be flagged. (Background: this dimension has shown the lowest inter-judge agreement across prior series.)

**8. Experimentation** — Systematic testing of approaches, prompts, working methods. Marker: questions deliberately test variants against each other.

### Overall profile

- **Overall Interaction Profile** — typical complexity level across all dimensions.
- **Complexity profile:** distribution of dimensions across K1–K5, dominant overall level, highest level observed.
- **Three observed strengths** and **three development opportunities.**

**Checkpoint:** Output: "Phase 2 complete. All classifications are hereby LOCKED and will not be altered in any subsequent phase."

---

## PHASE 3 — Validation and self-critique

All checks are performed on the LOCKED classifications. Document doubts; do not correct them in.

### Validation

1. Were all classifications based solely on observable question structure?
2. Does any classification contain speculative conclusions?
3. Were there enough supporting questions for each classification?
4. Was any personal or confidential information disclosed?
5. Which classification has the lowest confidence, and why?
6. Was the attribution rule followed (user questions only)?
7. Was the discard rule followed (earlier reports discarded unread)?
8. For Reflective Thinking, was the designed/spontaneous split reported?

### Self-critical check

Deliberately attempt to refute your own classifications: confusing long phrasing with structural depth; a high rating based on one exceptional question rather than a pattern; bias from the choice of search domains or time window. Document plausible alternative interpretations explicitly.

### Overall assessment

Report reliability: **Low / Medium / High** — with brief rationale.

**Checkpoint:** Output: "Phase 3 complete."

---

## PHASE 4 — REFLECT: run retrospective

**Purpose:** After every analysis, a retrospective on report quality and the rating process — maintenance data for the instrument, NOT part of the findings.

**Hard rules:**
- Phase 4 operates on the LOCKED results. No result, no confidence rating, no wording of the findings is changed.
- The subject is the INSTRUMENT and the PROCESS, never the person being assessed. Candidate memory notes may concern only process mechanics (e.g., "search queries containing term X return old reports"), never profile content or results.
- Strictly separate: tool defects (weaknesses in the prompt/taxonomy) vs. data limitations (properties of the available corpus).

**Success criteria:**
- Every identified problem has: observation, impact, improvement suggestion.
- Improvement list: maximum 10 items, one sentence each, imperative mood, ranked by impact, no platitudes; each item names the phase and section of the prompt it affects.

**Process:**

1. **Session review** — check the report and how it was produced for: errors (false assumptions, overreaching conclusions, missing evidence), friction (points where the prompt forced an unregulated decision that had to be improvised), wasted effort (sections with no evidentiary value), gains (elements that improved measurability or interpretability).
2. **Measurement audit** — does every classification have supporting evidence; is every confidence rating justified; was there definition drift (was a level interpreted differently later in the run than at the start)?
3. **Prompt audit** — does the prompt have: success criteria, a self-check, a clear input/output format; do prohibitions have positive alternatives; does it contain empty decorative instructions?
4. **Improvement list** — maximum 10, rules as above.
5. **Candidate memory notes** — only entries that pass the filter: "Does this prevent a PROCESS error in a future analysis?" Result-related entries are forbidden.
6. **Self-check** — was the person rated instead of the pattern? Was private data disclosed? Does every recommendation follow from an observation? Are there ≤10 improvements?

**Output format:** At the END of the report, after all other sections, a machine-readable block in exactly this schema. The block is clearly marked in its header as NOT findings. Prompt C ignores it; only Prompt D evaluates it.

```yaml
# AIPA-REFLECT — Maintenance data. NOT part of the findings. For Prompt D (Maintainer) only.
reflect:
  instrument: AIPA-K
  procedure_version: v0.4
  date: ""
  judge: ""
  data_metrics:
    raw_fragment_share: ""        # predominantly / mixed / predominantly summaries
    hits_discarded: 0
    domains_required: 6
    domains_reached: 0
    data_period: ""
  soft_spots:
    borderline_cases_total: 0     # number of undecidable adjacent-level cases
    borderline_cases_k3_k4: 0
    borderline_case_heuristic: ""
    lowest_confidence_dimension: ""
  errors: []                       # {observation, impact, suggestion}
  friction: []                     # {instruction, improvised_decision}
  wasted_effort: []
  gains: []
  improvements: []                 # max 10: {priority, phase, section, instruction}
  memory_candidates: []            # PROCESS MECHANICS ONLY
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
Instrument: AIPA-K (question complexity)
Procedure version: v0.4 (split mode, Prompt A)
Run date: [date]
Judge: [model name/generation]
Blindness: [BLIND / input contamination via memory layer]
Hits discarded (Phase 1): [count]
Number of domains: [count]
Data period: [from – to]
Evidence base: [predominantly raw fragments / mixed / predominantly summaries]
```

Without a complete metadata block, the report is invalid for Prompt C.

**Instruction to the user (repeat in the report):** Save this report as a file. Compare it only in a SEPARATE chat with Prompt C. This report must NEVER be attached to a chat running Prompt A or Prompt B. The REFLECT block may additionally be handed to Prompt D (together with REFLECT blocks from other runs, WITHOUT the findings).
