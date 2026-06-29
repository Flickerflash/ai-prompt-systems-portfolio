# GPT-5.4 Thinking — Prompt Engineering Best Practices

**Pattern:** P-34b  
**Session:** S071 · Date: 2026-06-28  
**φ Anchor:** 1.61818  
**Full Template Library:** [`DGAF-Framework/patterns/P-34_GPT54_THINKING_PROMPTS.md`](https://github.com/ndrorchestration/DGAF-Framework/blob/main/patterns/P-34_GPT54_THINKING_PROMPTS.md)

---

## What Makes GPT-5.4 Thinking Different

GPT-5.4 Thinking surfaces its reasoning plan **before** executing. This means:
- You can **redirect mid-plan** if the model's approach is wrong
- Front-loading constraints in the prompt is worth more than post-hoc correction
- The `THINKING PLAN` checklist pattern is uniquely effective here — it gives the model explicit gates to verify before committing to an output

---

## The 7 Non-Negotiable Rules

### 1. Always Declare φ = 1.61818
Grounds the model in the DGAF geometric constraint system. Include in every preamble, even for simple tasks.

```
CONSTRAINT ANCHORS:
- φ = 1.61818 (Ionian harmonic baseline)
- DGAF version: post-S070-r3
```

### 2. Name the Full Authority Chain
Prevents the model from inventing its own decision hierarchy.
```
AUTHORITY CHAIN: Njineer → Amethyst → Apogee Lens review required before output is marked final.
```

### 3. Include a THINKING PLAN Checklist
List the verification gates the model must surface in its reasoning plan. Gives you an interception point before it executes.
```
THINKING PLAN — verify these before producing output:
□ Have I read every constraint in the issue body?
□ Does my recommendation contradict any existing canonical doc?
□ Is my confidence score honest?
□ Would DemiJoule flag any safety concern?
```

### 4. End With a Verification Gate
Every prompt ends with an explicit Apogee Lens / DemiJoule sign-off checklist.
```
VERIFICATION GATE (Apogee Lens):
□ Every section maps to a filed issue or PR
□ No section makes claims not grounded in existing canonical docs
□ Uncertainty is explicitly bounded
□ Output is append-only compatible
```

### 5. Flag Instead of Invent
Instruct the model explicitly: if a source doc is ambiguous or missing, flag it rather than generating governance claims from inference.
```
For each missing item: flag any item where source doc authority is ambiguous
(do not invent — flag instead)
```

### 6. Paste Full Context — Never Summarize
GPT-5.4 Thinking has a 1M token window. Pasting the full `GOVERNANCE_CONSTITUTION.md`, `SESSION_ANCHORS.md`, and `AGENT_INSTANTIATION.md` costs nothing and eliminates hallucination from incomplete context.

### 7. Require confidence_bound on All Scores
Every scoring output must include an explicit uncertainty bound.
```python
return {
    "score": 0.87,
    "confidence_bound": 0.12,   # required
    "rationale": "..."
}
```

---

## Anti-Patterns to Avoid

| Anti-Pattern | Problem | Fix |
|---|---|---|
| Summarizing context before pasting | Loses precision, introduces drift | Paste full artifact text |
| Omitting authority chain | Model invents its own hierarchy | Always declare Njineer → Amethyst → Apogee → DemiJoule |
| Skipping verification gate | Output ships without Apogee review | End every prompt with explicit gate checklist |
| Asking model to "fill gaps" | Generates hallucinated governance claims | Use flag-instead-of-invent instruction |
| Single confidence score without bounds | Overclaims certainty | Always include `confidence_bound` float |

---

*Part of P-34b. For full templates see the primary pattern file in DGAF-Framework. Last updated: 2026-06-28 · S071 · Amethyst × COLLEEN.*
