# Architecture

```text
Test intent (story / Gherkin)
          |
          v
 AI test design + script generators -----> generated artifacts
          |
          +--> Cypress commands / API helpers
          +--> Playwright HealingPage / telemetry
          +--> synthetic data factory / Zod schemas
          |
          v
 CI quality gates -> reports -> defect feedback
```

## Guardrails

- AI output is a suggestion, not an approval gate.
- Offline mode is deterministic and is the CI default.
- Healing only tries explicitly configured fallback locators.
- Healing events are emitted to `reports/healing-events.jsonl` for review.
- Synthetic data is generated locally; do not place production PII in prompts or fixtures.
- Every generated test should be reviewed for assertions, authorization boundaries, and cleanup.
