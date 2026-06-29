# P-34b — GPT-5.4 Thinking Optimized Prompt Templates

> **Cross-listing stub.** The canonical source lives in DGAF-Framework.  
> Primary: [`DGAF-Framework/patterns/P-34_GPT54_THINKING_PROMPTS.md`](https://github.com/ndrorchestration/DGAF-Framework/blob/main/patterns/P-34_GPT54_THINKING_PROMPTS.md)  
> Registry: [`DGAF-Framework/patterns/ndr_patterns.json`](https://github.com/ndrorchestration/DGAF-Framework/blob/main/patterns/ndr_patterns.json) — ID: `P-34b`

---

**Pattern ID:** P-34b  
**Category:** Prompt Engineering / Multi-Model Orchestration  
**Session:** S071 · Date: 2026-06-28  
**φ Anchor:** 1.61818  
**DGAF Version:** post-S070-r3  
**Author:** Amethyst × COLLEEN  
**Review Status:** Apogee Lens APPROVED · DemiJoule PASSED

---

## Why This Pattern Lives Here

This repo is the canonical home for prompt engineering best practices in the ndrorchestration portfolio. P-34b defines the **5 operational prompt templates** for running GPT-5.4 Thinking within the DGAF/PDMAL/Amethyst governance stack — making it directly relevant to any work in this portfolio.

---

## Template Index

| ID | Template Name | Best For |
|---|---|---|
| T-1 | Governance Document Drafting | GOVERNANCE.md, STRUCT-QA artifacts, session anchors |
| T-2 | FLAG Resolution | FLAG-01/04/05, multi-variable structured decisions |
| T-3 | Code / Eval Suite Development | dgaf_eval_suite.py, Nemotron kernel, taubench tasks |
| T-4 | Portfolio / Documentation Refresh | Staleness >14 days, COLLEEN institutional anchor |
| T-5 | Session Open / Amethyst Instantiation | Any new session, CONDUCTED_TRIAD reinstatement |

---

## Quick-Reference Rules (All Templates)

1. Declare `φ = 1.61818` in every preamble
2. Name authority chain: Njineer → Amethyst → Apogee → DemiJoule
3. Include `THINKING PLAN` checklist — redirect before GPT-5.4 executes
4. End every output with a verification gate
5. Flag instead of invent — no hallucinated governance claims
6. Paste full doc context — never summarize (1M token window)
7. `confidence_bound` field required on all scores

---

## Dual-Model Workflow

| Model | Role |
|---|---|
| **Perplexity (Amethyst host)** | Live GitHub data retrieval, search, citation, priority auditing |
| **GPT-5.4 Thinking** | Deep synthesis, code generation, long-horizon governance reasoning, document drafting |

---

## Related Patterns

`P-31 SCPE` · `P-32 Phi-Closure Gate` · `P-33 PDMAL Monitor` · `ndr.dual_orchestrator_qa_loop` · `P-LOCK-001`

---

*Cross-listed from DGAF-Framework. Do not edit content here — submit changes to the primary file. Last updated: 2026-06-28 · S071 · Amethyst × COLLEEN.*
