# Dataset Nutrition Label

Machine-readable labels for AI dataset risk, license, consent, and coverage.

> Version: 1.0.0 | License: MIT | Status: production-oriented v1 foundation

## Problem

Dataset documentation is inconsistent, hard to compare, and often absent from automated pipelines.

## What this project solves

A label validator that enforces structured documentation for composition, collection method, consent, license, limitations, and intended use.

Dataset Nutrition Label ships as a small, dependency-free CLI and library. It validates a domain-specific JSON packet, emits actionable findings, and gives contributors a concrete surface for adding adapters, richer checks, schemas, and integrations.

## Who it is for

Dataset publishers, open ML communities, model governance teams.

## Quick start

```bash
npm test
npm start -- sample
```

Analyze your own packet:

```bash
dataset-nutrition-label ./packet.json
```

Or pipe JSON:

```bash
cat packet.json | node src/cli.js
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

```js
const { analyze } = require("./src/index.js");

const report = analyze({
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
});
console.log(report.summary);
```

## v1 behavior

- Validates required fields for the domain packet.
- Scores readiness from 0 to 100.
- Reports missing or weak governance evidence.
- Suggests next actions and contributor extension points.
- Runs fully offline with no API keys and no network access.

## Contribution map

Good first contributions:

- Add Hugging Face card export.
- Add schema registry.
- Add coverage metrics.
- Add license compatibility checks.

Larger contributions:

- Add a JSON Schema and compatibility tests.
- Build import/export adapters for popular AI frameworks.
- Add real-world fixtures from public, non-sensitive examples.
- Improve scoring with transparent, documented heuristics.

## Project principles

- Human agency over blind automation.
- Open standards over vendor lock-in.
- Auditable decisions over hidden magic.
- Privacy and safety as design constraints, not release notes.

## GitHub Pages

The marketing site lives in `site/index.html`. Enable GitHub Pages from the `site` folder or use the included Pages workflow after publishing.

## Security

This project does not process secrets by default. If you build adapters that touch production systems, keep least privilege, explicit consent, and auditable logs in the design.
