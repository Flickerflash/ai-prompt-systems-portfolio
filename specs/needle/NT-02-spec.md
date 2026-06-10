# NT-02 Prompt Spec: Generate Grounded KB Answers

**Status:** ACTIVE  
**NDR Pattern:** P-05 (Tri-Phase CI Gate — retrieve+generate phases)  
**NIST Controls:** MANAGE 2.2  
**Run:** [needle.app/workflow-templates/generate-grounded-knowledge-base-answers](https://needle.app/workflow-templates/generate-grounded-knowledge-base-answers)

---

## Prompt Structure

```
SYSTEM:
You are a knowledge base answer generator. You MUST only use the provided
retrieved context to answer. Do not generate from prior knowledge.
If the context does not contain the answer, return: INSUFFICIENT_CONTEXT.

CONTEXT:
- Retrieved passages: {retrieved_passages}   # from KB retrieval step
- Source metadata: {source_metadata}         # document IDs, dates
- User query: {query}

TASK:
1. Generate a grounded answer using only the retrieved passages
2. Cite the specific passage(s) used for each claim
3. Flag any claim that required inference beyond direct retrieval
4. Return structured output matching grounded-answer-v1 schema
```

## Multi-Agent Flow

```
Phase 1: RETRIEVE (P-05)
  │  Agent: KB Retrieval
  │  Input: user query
  │  Output: retrieved_passages + source_metadata
  │  Gate: min 2 passages required; no passage = ABORT
  ▼
Phase 2: GENERATE (P-05)
  │  Agent: Grounded Generator (this template)
  │  Input: retrieved_passages
  │  Output: grounded_answer + citations
  │  Gate: all claims must cite a passage
  ▼
[NT-03] EVALUATE (P-05 Phase 3 → P-11)
     Agent: Quality Evaluator
     Input: grounded_answer
     Output: 11Q score + audit record
```

## Output Schema

```json
{
  "template_id": "NT-02",
  "run_id": "string",
  "timestamp": "ISO8601",
  "answer": "string",
  "citations": [{ "claim": "string", "passage_id": "string" }],
  "inference_flags": ["claims requiring inference beyond retrieval"],
  "retrieval_metadata": { "passage_count": 0, "source_ids": [] },
  "ndr_pattern_ref": "P-05"
}
```
