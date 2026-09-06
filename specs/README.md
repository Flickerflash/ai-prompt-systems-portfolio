# specs/ — Machine-Readable Evaluation Specifications

This directory contains YAML evaluation specifications associated with the public prompt artifacts in this portfolio.

> **Evidence boundary:** these files define local metrics, scoring rules, and pass/fail criteria. They are specifications/data, not an executable evaluation harness, external certification, or evidence that a prompt performs well across models or tasks.

## How to use these specs

Use them as structured inputs to an evaluator that you implement and test separately. This repository does not currently ship a Python evaluator package or supported evaluation CLI.

For executable benchmarking work, use a repository that actually contains and tests an evaluation harness, such as `resumeapex-eval`.

## Spec index

| File | Prompt | Pattern class |
|---|---|---|
| `example.yaml` | Template / reference spec | General |
| `01_state_anchor_eval.yaml` | State Anchor | State management |
| `02_constraint_gate_eval.yaml` | Constraint Gate | Constraint handling |
| `03_multi_agent_eval.yaml` | Multi-Agent Flow | Orchestration |
| `04_parametric_eval.yaml` | Parametric Constraint | Parameterization |
| `05_error_recovery_eval.yaml` | Error Recovery | Resilience |

## Spec format

A specification may contain fields such as:

```yaml
name: "<Eval Name>"
version: "1.0.0"
pattern_class: "<class>"
metrics:
  - name: "<metric_name>"
    type: "boolean | score"
    description: "<what this local rubric measures>"
    weight: <0.0-1.0>
rules:
  - if: "<metric> == <value>"
    then: "pass = false"
passing_threshold: 0.75
```

Any `governance`, ecosystem, DGAF, or persona fields retained inside individual specs should be interpreted as project metadata unless an executable integration explicitly enforces them. Cross-repository references do not transfer validation.
