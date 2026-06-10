# NT-03 Prompt Spec: KB Answer With Quality Check

**NDR Patterns:** P-05 (Tri-Phase CI Gate), P-11 (11Q Attestation Scoring), P-30 (Apogee Gate)  
**NIST Controls:** MEASURE 2.9  
**Run:** [needle.app/t/kb-answer-quality-check](https://needle.app/t/kb-answer-quality-check)

---

## Prompt Structure

```
SYSTEM:
You are a combined KB answer generator and quality evaluator.
Execute all three phases sequentially: retrieve, generate, evaluate.
Return a single unified audit record.

CONTEXT:
- KB retrieval system: {kb_system}
- Governance spec: {governance_spec}    # NT-04 output
- Evaluation rubric: {rubric}           # NT-01 11Q dimensions
- User query: {query}

TASK:
1. [RETRIEVE] Pull relevant passages from KB for the query
2. [GENERATE] Produce a grounded answer from retrieved passages only
3. [EVALUATE] Score the answer against the 11Q rubric
4. Return unified audit record (all three phase outputs combined)
```

## Sequential Flow (P-05 → P-11)

```
[RETRIEVE]  ← P-05 Phase 1
    │  output: retrieved_passages
    ▼
[GENERATE]  ← P-05 Phase 2
    │  output: grounded_answer + citations
    ▼
[EVALUATE]  ← P-05 Phase 3
    │  output: 11Q scores → triggers P-11
    ▼
[11Q SCORE] ← P-11
    │  output: verdict + flagged dimensions
    ▼
[AUDIT RECORD] — stored; feeds P-30 attestation gate
```

## Output Schema

```json
{
  "template_id": "NT-03",
  "run_id": "string",
  "timestamp": "ISO8601",
  "retrieve_phase": {
    "passages": [], "source_ids": []
  },
  "generate_phase": {
    "answer": "string", "citations": []
  },
  "evaluate_phase": {
    "scores": { "Q1": 0.0, "Q11": 0.0 },
    "verdict": "PASS | FAIL | REVIEW",
    "flags": []
  },
  "audit_ready": true,
  "ndr_pattern_ref": "P-05, P-11, P-30"
}
```
