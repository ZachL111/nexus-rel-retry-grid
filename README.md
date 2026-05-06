# nexus-rel-retry-grid

`nexus-rel-retry-grid` explores reliability with a small Solidity codebase and local fixtures. The technical goal is to develop a Solidity command-oriented project for retry scenarios with round-trip fixtures, lossless normalization checks, and no network dependency.

## Reason For The Project

I want this repository to be useful as a quick reading exercise: fixtures first, implementation second, verifier last.

## Nexus Rel Retry Grid Review Notes

For a quick review, compare `budget pressure` with `recovery gap` before reading the middle cases.

## What It Does

- `fixtures/domain_review.csv` adds cases for budget pressure and failure width.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/nexus-rel-retry-walkthrough.md` walks through the case spread.
- The Solidity code includes a review path for `budget pressure` and `recovery gap`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## How It Is Put Together

The implementation keeps the scoring rule plain: reward signal and confidence, preserve slack, penalize drag, then classify the result into a review lane.

The Solidity checks add a pure review lens and Foundry coverage.

## Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Check It

The same command runs the local verification path. The highest-scoring domain case is `stale` at 202, which lands in `ship`. The most cautious case is `edge` at 135, which lands in `watch`.

## Boundaries

No external service is required. A deeper version would add more negative cases and a clearer boundary around invalid input.
