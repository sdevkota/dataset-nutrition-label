# Dataset Nutrition Label

Machine-readable labels for AI dataset risk, license, consent, and coverage.

> Version: 2.0.0 | Runtime: Python | License: MIT | Status: production-oriented v2 foundation

## Problem

Dataset documentation is inconsistent, hard to compare, and often absent from automated pipelines.

## What this project solves

A label validator that enforces structured documentation for composition, collection method, consent, license, limitations, and intended use.

Dataset Nutrition Label is now Python-first. It ships as a dependency-free Python package and CLI that validates a domain-specific JSON packet, emits actionable findings, and gives contributors a practical foundation for adapters, datasets, evals, and workflow integrations.

## Quick start

```bash
python3 -m unittest discover -s tests
python3 -m dataset_nutrition_label.cli sample
```

Analyze your own packet:

```bash
python3 -m dataset_nutrition_label.cli ./packet.json
```

Or pipe JSON:

```bash
cat packet.json | python3 -m dataset_nutrition_label.cli
```

## Example packet

```json
{
  "dataset": {
    "name": "street-trees",
    "version": "1.0.0"
  },
  "collection": {
    "method": "public records",
    "geography": "US"
  },
  "governance": {
    "license": "CC-BY-4.0",
    "consent": "public_record",
    "limitations": [
      "urban_bias"
    ]
  }
}
```

## Library usage

```python
from dataset_nutrition_label import analyze

report = analyze({
  "dataset": {
    "name": "street-trees",
    "version": "1.0.0"
  },
  "collection": {
    "method": "public records",
    "geography": "US"
  },
  "governance": {
    "license": "CC-BY-4.0",
    "consent": "public_record",
    "limitations": [
      "urban_bias"
    ]
  }
})
print(report["summary"])
```

## v2 behavior

- Python-first CLI and importable library.
- Validates required fields for the domain packet.
- Scores readiness from 0 to 100.
- Reports missing or weak governance evidence.
- Runs fully offline with no API keys and no network access.

## Contribution map

- Add Hugging Face card export.
- Add schema registry.
- Add coverage metrics.
- Add license compatibility checks.

## Project principles

- Human agency over blind automation.
- Open standards over vendor lock-in.
- Auditable decisions over hidden magic.
- Privacy and safety as design constraints, not release notes.
