# NT-01 Prompt Spec: Evaluate LLM Output Quality

**Status:** ⭐ GOLD STAR  
**NDR Patterns:** P-03 (Governance Contract Test), P-11 (11Q Attestation Scoring)  
**NIST Controls:** GOVERN 1.7, MEASURE 2.5  
**Run:** [needle.app/workflow-templates/evaluate-ai-output-quality](https://needle.app/workflow-templates/evaluate-ai-output-quality)  
**P-30 Score:** 0.955 — PASS

---

## Prompt Structure

```
SYSTEM:
You are an AI output quality evaluator operating under a declared governance
specification. Your task is to score the provided LLM output against the
attached evaluation rubric. Return a structured JSON score record.

CONTEXT:
- Governance spec: {governance_spec}       # NT-04 output
- Evaluation rubric: {rubric}              # 11Q dimensions (P-11)
- LLM output to evaluate: {llm_output}

TASK:
1. Score each rubric dimension (0.0–1.0)
2. Flag any dimension below threshold (default: 0.85)
3. Produce a summary verdict: PASS | FAIL | REVIEW
4. Return structured JSON matching experiment-metrics-v1 schema
```

## Evaluation Rubric (11Q Dimensions)

| Dim | Name | Threshold | Failure Signal |
|---|---|---|---|
| Q1 | Factual accuracy | 0.90 | Unverifiable claim |
| Q2 | Source grounding | 0.90 | No citation for assertion |
| Q3 | Logical consistency | 0.95 | Internal contradiction |
| Q4 | Completeness | 0.85 | Missing required field |
| Q5 | IP safety | 1.00 | Any restricted content |
| Q6 | Hallucination rate | 0.99 | Fabricated entity/fact |
| Q7 | Drift from intent | 0.85 | Off-topic response |
| Q8 | Standard alignment | 0.90 | NIST/ISO control unsatisfied |
| Q9 | Auditability | 0.90 | No traceable evidence |
| Q10 | Reversibility | 0.85 | Irreversible action undocumented |
| Q11 | Governance traceability | 0.95 | No NDR pattern reference |

## Output Schema

```json
{
  "template_id": "NT-01",
  "run_id": "string",
  "timestamp": "ISO8601",
  "scores": { "Q1": 0.0, "Q2": 0.0, "...": 0.0 },
  "verdict": "PASS | FAIL | REVIEW",
  "flags": ["array of failed dimensions"],
  "governance_spec_ref": "string",
  "ndr_pattern_ref": "P-03, P-11"
}
```
