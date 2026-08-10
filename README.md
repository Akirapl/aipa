**English** | [Deutsch](README.de.md) | [Polski](README.pl.md)

# AIPA — AI Interaction Pattern Assessment

A framework for scoring the *shape* of a human–AI conversation — not what the model outputs, but how the person is asking and how well mistakes get caught — using isolated LLM judges instead of self-report.

## The problem

Answers got cheap. A prompt in, a finished-looking answer out, seconds later — and the friction that used to force real understanding is gone. Every AI eval that exists measures the model's output quality. None of them ask the other question: is *this exchange* actually building understanding and catching its own errors, or just producing something plausible, fast?

AIPA started as an attempt to answer that for my own conversations — treating the transcript as data instead of trusting a gut feeling about whether an exchange "went well."

## How it's built

Two independent instruments share one methodology:

- **AIPA-K** classifies the structural *complexity* of the questions being asked (K1–K5) across eight behavioral dimensions: curiosity, depth of inquiry, iterative learning, cross-domain integration, problem-solving behaviour, information seeking, reflective thinking, experimentation.
- **AIPA-E** classifies *correction events* (E1–E5). Not "errors" — an error needs a ground truth the judge doesn't reliably have. A correction event is directly observable in the transcript: a premise, assumption, or claim gets revised, retracted, or shown wrong — by the user, the model, or reality (a failed test, for instance). Scored on three independent axes: severity, source, latency.

Both run through four isolated judge prompts, each executed in its own fresh session so no judge ever sees another's report:

| Prompt | Role | Sees |
|---|---|---|
| A — Complexity Judge | Classifies K1–K5 | Only the transcript, blind |
| B — Correction Judge | Classifies E1–E5 | Only the transcript, blind, independent of A |
| C — Comparator | Compares reports across runs and instruments | Locked judge reports only — never Reflect data |
| D — Maintainer | Proposes the next version | Only accumulated Reflect blocks — never the actual findings |

Inside each judge, phases run strictly in order and lock before the next begins: a contamination declaration, evidence gathering (minimum domain coverage is enforced, not optional), classification (then frozen), validation and self-critique, and a machine-readable Reflect block that feeds the Maintainer.

Two rules keep the instrument honest: a **rejection rule** that discards any evidence which is *about AIPA itself* — so it can't grade its own homework — and an **attribution rule** that scores only the human's question structure, never the model's answer complexity.

The four judges run as separate prompts by design, not by accident. An API-orchestrated version was scoped early and set aside — manual isolation made contamination easier to guarantee and, more importantly, easier to audit.

## What came out of running it

- Cross-platform testing surfaced a real methodological bug, not just a Claude quirk: a run on GPT showed that letting a judge work from an already-summarized context instead of a fresh search introduces uncontrolled selection bias. Prompt B now hard-aborts rather than proceed on fragments.
- *Reflective thinking* has come out as the lowest-agreement dimension across repeated, independent runs — a stable pattern across versions, not noise, and now a named target for v0.5.
- The latest full run pulled evidence from 12 independent conversation domains — double the protocol's enforced minimum — spanning technical, administrative, and everyday material, and the instrument held up outside a narrow test bed.
- The instrument is designed to revise itself: Prompt D never sees a single finding, only Reflect logs from past runs — that loop is what's driving the open items already queued for v0.5.

## Known limitations

- When only conversation summaries (not raw transcripts) are available as evidence, AIPA-E explicitly downgrades confidence on the affected axes rather than forcing a classification.
- Inter-judge reliability data is still thin. More independent runs — ideally from other users, on other conversations — would strengthen it faster than more runs by one person.

## Status

Active, currently **v0.4**. AIPA-K and AIPA-E version independently. Several v0.5 changes are already queued from Maintainer output.

## Repository layout

```
/prompts/en/   Prompts A–D, English (canonical)
/prompts/de/   Prompts A–D, German (original)
/prompts/pl/   Prompts A–D, Polish
/examples/     Anonymized sample judge reports and a full run
README.md      This file (English)
README.de.md   German
README.pl.md   Polish
LICENSE
```

## Using it

The judges are prompts, not code. Run them one at a time, in a clean session with no prior context attached:

1. Run Prompt A on a transcript → save the locked report.
2. Run Prompt B on the *same* transcript, separately → save the locked report.
3. Feed both locked reports — never the raw transcript — into Prompt C for the cross-instrument comparison.
4. Once Reflect blocks have accumulated across several runs, feed only those into Prompt D for the next version's change list.

Run all four prompts of one assessment series in the **same language track** (all from `/prompts/en/`, all from `/prompts/de/`, or all from `/prompts/pl/`). The three tracks are faithful translations of the same methodology, but the machine-readable Reflect block uses different field names per language, and Prompt D expects the field names of its own track.

## License

MIT.
