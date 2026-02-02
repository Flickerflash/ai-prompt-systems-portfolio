# AI Prompt Systems Portfolio (IP‑Safe Samples)

This repository contains a small set of **public, IP‑safe examples** of my AI prompt systems work.

My private work includes more detailed frameworks (governance, frequency‑aware constraints, multi‑agent orchestration). Those are kept **private** to protect intellectual property and any future patentability. This repo is meant to show how I think and work, without exposing sensitive internals.

## Structure

Each entry lives in its own markdown file in this repo:

1. `01_state_anchor.md`
2. `02_constraint_gate.md`
3. `03_multi_agent_flow.md`
4. `04_parametric_constraint.md`
5. `05_error_recovery.md`

Each file follows the same format:

- Goal
- Example prompt or system message (simplified)
- Evaluation rubric (how I judge outputs)
- Notes on iteration and failure modes

---

## 1. State Anchor Prompt

**File:** `01_state_anchor.md`  
**Goal:** Keep an assistant consistently “on persona” and in scope across a long conversation.

- Shows how I define role, boundaries, and what to ignore.
- Includes a short checklist I use to check if the assistant stayed anchored.

## 2. Constraint Gate (Guardrail)

**File:** `02_constraint_gate.md`  
**Goal:** Enforce a small set of **non‑negotiable rules** (e.g., no legal advice, no internal tool names).

- Shows how I structure constraints in plain language.
- Includes a simple pass/fail rubric for whether the model respected constraints.

## 3. Multi‑Agent Orchestration Pattern

**File:** `03_multi_agent_flow.md`  
**Goal:** Show how multiple AI “roles” can cooperate (e.g., Researcher → Critic → Editor).

- High‑level description of the roles and their responsibilities.
- Example of a review loop where one agent checks another against a rubric.

## 4. Parametric (“Dial”) Constraint Example

**File:** `04_parametric_constraint.md`  
**Goal:** Demonstrate that I can tune behavior along a “dial” (e.g., strictness), **without** exposing proprietary math or full methodology.

- Describes a parameter like “strictness” and how it changes outputs.
- Shows how I would document and test different parameter settings.

## 5. Error Recovery & Robustness

**File:** `05_error_recovery.md`  
**Goal:** Show how I handle errors, bad outputs, or broken conversations.

- Example prompts for asking the model to correct itself or summarize what went wrong.
- Simple checklist for when to restart vs. when to repair a conversation.

---

## What’s intentionally **not** here

To protect my IP and any future patentability, I **do not** include:

- Full implementations of my frequency‑based / modal systems.
- Any prompts tied to real client data or confidential sources.
- Detailed internal governance documentation or unpublished research.

Those live in private repositories or offline archives and can be discussed at a high level in interviews if appropriate.

---

## How this relates to my resume

This portfolio connects directly to my resume bullets about:

- Prompt evaluation rubrics
- Guardrails and constraint prompts
- Multi‑agent orchestration
- Governance‑style documentation
- Robustness and error‑handling

If you’re reviewing my application and want to see more depth, I’m happy to walk through these entries live and discuss how I would adapt the same patterns to your stack.
