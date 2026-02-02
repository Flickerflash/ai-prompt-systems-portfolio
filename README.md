# ai-prompt-systems-portfolio
Public examples of my AI prompt systems and evaluation work (IP-safe, no client data).
AI Prompt Systems Portfolio (IP‑Safe Samples)
This repository contains a small set of public, IP‑safe examples of my AI prompt systems work.

My private work includes more detailed frameworks (governance, frequency‑aware constraints, multi‑agent orchestration). Those are kept private to protect intellectual property and potential patentability. This repo is meant to show how I think and work, without exposing sensitive internals.

What’s included here
Each entry follows the same format:

Goal

Prompt(s) or system message structure (simplified)

Evaluation rubric (how I judge outputs)

Notes on iteration and failure modes

1. State Anchor Prompt
Goal: Keep an assistant consistently “on persona” and in scope across a long conversation.

System message shows how I define role, boundaries, and what to ignore.

Includes a short checklist I use to check if the assistant stayed anchored.

2. Constraint Gate (Guardrail)
Goal: Enforce a small set of non‑negotiable rules (e.g., do not give legal advice, do not mention internal tools).

Shows how I structure constraints in plain language.

Includes a simple pass/fail rubric for whether the model respected constraints.

3. Multi‑Agent Orchestration Pattern
Goal: Show how multiple AI “roles” can cooperate (e.g., Researcher → Critic → Editor).

High‑level description of the roles and their responsibilities.

Example of a review loop where one agent checks another against a rubric.

4. Frequency‑Aware / Parametric Constraint Example (Simplified)
Goal: Demonstrate that I can tune behavior along a “dial” (e.g., more strict vs. more flexible), without exposing proprietary math or full methodology.

Describes a parameter like “strictness” or “creativity” and how it changes outputs.

Shows how I would document and test different parameter settings.

5. Error Recovery & Robustness
Goal: Show how I handle errors, bad outputs, or broken conversations.

Example prompts for asking the model to correct itself or summarise what went wrong.

Simple checklist for when to restart vs. when to repair a conversation.

What’s intentionally not here
To protect my IP and any future patentability, I do not include:

Full implementations of my frequency‑based / modal systems.

Any code or prompts tied to real client data or confidential sources.

Detailed internal governance documentation or unpublished research.

Those live in private repositories or offline archives and can be discussed at a high level in interviews if appropriate.

How this relates to my resume
This portfolio connects directly to my resume bullets about:

Prompt evaluation rubrics

Guardrails and constraint prompts

Multi‑agent orchestration

Governance‑style documentation

Robustness and error‑handling

If you’re reviewing my application and want to see more depth, I’m happy to walk through these entries live, explain my thinking, and discuss how I would adapt the same patterns to your stack.

