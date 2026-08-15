![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-Apache%202.0-01696f?style=flat-square)
![Language](https://img.shields.io/badge/Language-Python-blue?style=flat-square)
![IP Safe](https://img.shields.io/badge/IP--Safe%20Samples-public-4f98a3?style=flat-square)
![Maintained](https://img.shields.io/badge/Maintained-yes-437a22?style=flat-square)

> **Scope:** Public, IP-safe prompt-engineering portfolio. DGAF and other project references describe related workflows or mappings; they do not imply external certification or that every artifact in this repository has passed a common validation gate.

> **Status: Active work-in-progress.** Some artifacts are documented experiments, some are more mature evaluation specifications, and some are examples intended primarily for public demonstration. Check the individual artifact and evaluation evidence before treating a claim as validated.

> **Lineage:** This is the **public-facing IP-safe portfolio** — a curated selection of prompt patterns safe for public display. It is distinct from the private `ai-prompt-engineering-portfolio` and `AI-Prompt-Engineer` archives. Repository relationships do not by themselves establish that one repository validates another.

---

## Needle Templates — Prompt Specifications

The [`specs/needle/`](specs/needle/) directory contains prompt-engineering specifications for four Needle.app workflow templates. Each spec may include prompt structure, evaluation rubric, multi-agent flow, and output schema.

| Template Spec | NDR Patterns | NIST Controls | Run |
|---|---|---|---|
| [NT-01: Evaluate LLM Output Quality](specs/needle/NT-01-spec.md) | P-03, P-11 | GOVERN 1.7, MEASURE 2.5 | [needle.app →](https://needle.app/t/evaluate-llm-output-quality) |
| [NT-02: Generate Grounded KB Answers](specs/needle/NT-02-spec.md) | P-05 | MANAGE 2.2 | [needle.app →](https://needle.app/t/grounded-kb-answers) |
| [NT-03: KB Answer With Quality Check](specs/needle/NT-03-spec.md) | P-05, P-11, P-30 | MEASURE 2.9 | [needle.app →](https://needle.app/t/kb-answer-quality-check) |
| [NT-04: Define AI Governance Specification](specs/needle/NT-04-spec.md) | P-03, P-30 | GOVERN 1.7 | [needle.app →](https://needle.app/t/ai-governance-spec) |

**NIST/ISO mapping:** [ai-governance-frameworks/docs/needle-templates/](https://github.com/ndrorchestration/ai-governance-frameworks/tree/main/docs/needle-templates)  
**Canonical registry:** [DGAF-Framework/docs/needle/TEMPLATE_REGISTRY.md](https://github.com/ndrorchestration/DGAF-Framework/blob/main/docs/needle/TEMPLATE_REGISTRY.md)

References to NIST/ISO controls are mappings, not evidence of certification or endorsement.

---

## Quick Overview

This repo is an **AI Prompt Engineering Portfolio**.

It collects public examples of prompts and workflow patterns designed for agents, applications, and evaluation workflows. It shows how system prompts, instructions, constraints, and evaluation rubrics are structured.

The repository is an active work-in-progress:

- Some prompts are fully documented with inputs, outputs, and evaluation notes.
- Others are drafts or experiments.
- Evaluation notes describe the evidence available for the particular artifact; they should not be generalized to the entire repository.

If you're reviewing the portfolio:

- Start with one or two prompts in `systems/` or `examples/`.
- Review the associated evaluation notes and failure modes.
- Use `junior-apogee-app` as a separate related project where appropriate; the relationship does not imply that every prompt here has been evaluated there.

---

## Prompt-Engineering Repo Map

| Repo | Visibility | Purpose | Status |
|------|-----------|---------|--------|
| **`ai-prompt-systems-portfolio`** (this repo) | Public | IP-safe curated samples — recruiter/engineer entry point | Active |
| `ai-prompt-engineering-portfolio` | Private | Full benchmark/archive material | Active |
| `AI-Prompt-Engineer` | Private | Historical benchmark lineage / origin archive | Archive/Reference |

Historical certification records, if present in private repositories, remain historical records unless independently re-established.

---

# AI Prompt Systems Portfolio (IP-Safe Samples)

This repository contains public, IP-safe examples of AI prompt systems work. Private work may contain more detailed frameworks and internal methodology that is intentionally not reproduced here.

## Structure

Each entry lives in its own markdown file:

1. `01_state_anchor.md`
2. `02_constraint_gate.md`
3. `03_multi_agent_flow.md`
4. `04_parametric_constraint.md`
5. `05_error_recovery.md`

Each file follows the same general format:
- Goal
- Example prompt or system message (simplified)
- Evaluation rubric
- Notes on iteration and failure modes

## Prompt examples

### 1. State Anchor Prompt

**File:** `01_state_anchor.md`

**Goal:** Keep an assistant consistently on persona and in scope across a long conversation.

### 2. Constraint Gate

**File:** `02_constraint_gate.md`

**Goal:** Enforce a small set of non-negotiable rules and document pass/fail behavior.

### 3. Multi-Agent Orchestration Pattern

**File:** `03_multi_agent_flow.md`

**Goal:** Show how multiple AI roles can cooperate, for example Researcher → Critic → Editor.

### 4. Parametric Constraint Example

**File:** `04_parametric_constraint.md`

**Goal:** Demonstrate tunable behavior while keeping proprietary methodology out of the public example.

### 5. Error Recovery & Robustness Prompt

**File:** `05_error_recovery.md`

**Goal:** Handle failures such as missing data, tool failures, and unclear instructions without fabricating certainty.

---

## How to Review This Repo in 3 Minutes

- 1 minute: Skim this README.
- 1 minute: Open `01_state_anchor.md` and review the goal, example, and evaluation notes.
- 1 minute: Open another artifact such as `03_multi_agent_flow.md` and inspect its documented failure modes.

## Taxonomy: Patterns & Workflows

### Patterns
- **State Anchor Prompt** — maintain role consistency
- **Constraint Gate** — enforce non-negotiable rules
- **Parametric Constraints** — tune behavior along a documented parameter

### Workflows
- **Multi-Agent Orchestration** — sequential agent cooperation
- **Error Recovery** — graceful failure handling
- **Needle Templates** — project-specific prompt specifications with documented evaluation criteria

### Rubrics
Prompt artifacts may include pass/fail or scored evaluation rubrics. A rubric defines a local evaluation procedure; it does not establish external certification.

### Playbooks
See `specs/` for machine-readable evaluation specifications where present.

---

## Evaluation Specs & CLI

To evaluate a prompt output against a rubric, where the referenced CLI and spec exist in the current checkout:

```bash
python -m portfolio.eval specs/example.yaml --input "<prompt>" --output "<model response>"
```

Specs live in `specs/` and may use structures such as:

```yaml
name: "State Anchor Evaluation"
metrics:
  - name: "role_consistency"
    type: "boolean"
    description: "Did the assistant stay in role?"
  - name: "scope_adherence"
    type: "boolean"
    description: "Did the assistant respect boundaries?"
  - name: "helpfulness"
    type: "score"
    min: 0
    max: 5
rules:
  - if: "role_consistency == false"
    then: "pass = false"
```

## Epistemic standard

Use the repository-wide distinction:

`DEFINED → IMPLEMENTED → COMPUTED → VERIFIED → ATTESTED → HISTORICAL → HYPOTHESIS → METAPHOR → UNSUPPORTED → DEPRECATED`

A prompt specification is not proof of model performance. A local evaluation run is not proof of generalization. A historical benchmark is not current validation without a reproducible run.

## Related Projects

- `DGAF-Framework` — related governance/evaluation research track
- `ai-governance-frameworks` — external-framework mapping and governance artifacts
- `junior-apogee-app` — related agent evaluation application
- `resumeapex-eval` — related evaluation/benchmark project
- `Gold-star-standards` — related rubric/standards repository
- `sentinel-governance` — related CI/governance enforcement track

These are separate repositories. Cross-references do not constitute mutual validation.
