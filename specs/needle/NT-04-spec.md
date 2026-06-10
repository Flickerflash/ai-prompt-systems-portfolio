# NT-04 Prompt Spec: Define AI Governance Specification

**Status:** ACTIVE  
**NDR Patterns:** P-03 (Governance Contract Test), P-30 (Apogee Attestation Gate)  
**NIST Controls:** GOVERN 1.7  
**Run:** [needle.app/workflow-templates/implement-governance-multi-agent-orchestration](https://needle.app/workflow-templates/implement-governance-multi-agent-orchestration)

---

## Prompt Structure

```
SYSTEM:
You are an AI governance specification author operating under ISO 42001
and NIST AI RMF. Your task is to produce a formal, versioned governance
specification document for the described AI system or use case.

CONTEXT:
- AI system description: {system_description}
- Applicable standards: {standards}       # NIST AI RMF, ISO 42001, IIA
- Risk register (if existing): {risks}    # optional prior state
- Owner: {owner}

TASK:
1. Define scope: which systems and use cases are governed
2. Build risk register: identify AI risks, severity, likelihood
3. Document treatment decisions: accept / mitigate / transfer per risk
4. Define human oversight procedures: who reviews what, at what frequency
5. Define metrics and monitoring: how governance effectiveness is measured
6. Version and ratify: date, owner, approval chain
7. Return structured governance spec matching governance-spec-v1 schema
```

## Output Schema

```json
{
  "template_id": "NT-04",
  "spec_id": "string",
  "version": "semver",
  "timestamp": "ISO8601",
  "owner": "string",
  "scope": "string",
  "risk_register": [
    {
      "risk_id": "string",
      "description": "string",
      "severity": "LOW | MEDIUM | HIGH | CRITICAL",
      "likelihood": "LOW | MEDIUM | HIGH",
      "treatment": "ACCEPT | MITIGATE | TRANSFER",
      "treatment_detail": "string"
    }
  ],
  "oversight_procedures": [
    { "reviewer": "string", "scope": "string", "frequency": "string" }
  ],
  "metrics": [
    { "metric_id": "string", "description": "string", "target": "string" }
  ],
  "ratification": {
    "ratified_by": "string",
    "date": "ISO8601",
    "approval_chain": []
  },
  "ndr_pattern_ref": "P-03, P-30",
  "standards_ref": ["NIST AI RMF GOVERN 1.7", "ISO 42001 §6.1", "ISO 42001 §9.1"]
}
```

## Multi-Agent Role

NT-04 is the **definition layer** — it produces the spec that all other templates
evaluate against:

```
NT-04 (define spec)
  │
  ├── NT-01 (evaluate outputs against spec)
  ├── NT-02 (generate answers constrained by spec)
  └── NT-03 (combined retrieval+eval against spec)
```
