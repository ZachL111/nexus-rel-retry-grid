# nexus-rel-retry-grid

`nexus-rel-retry-grid` packages a practical reliability exercise in Solidity. The emphasis is on deterministic behavior, a small public API, and examples that explain the tradeoffs.

## How I Read Nexus Rel Retry Grid

The useful thing to inspect here is how the same score rule is represented in code, metadata, and examples. If those three pieces disagree, the audit script should make the drift visible.

## Problem Shape

This project keeps the domain idea close to the tests. That makes it useful as a reference implementation, a small experiment, or a starting point for a more specialized tool.

## Scenario Walkthrough

The examples are meant to be readable before they are exhaustive. They cover enough variation to show how latency and risk can pull a decision below the threshold.

## Internal Model

The design is intentionally direct: parse or construct a signal, score it, classify it, and verify the expected branch. This makes the repository useful for studying reliability behavior without needing a service or database unless the language project itself is SQL. The Solidity project uses Foundry tests and pure contract functions so invariants are cheap to exercise.

## Main Behaviors

- Models failure windows with deterministic scoring and explicit review decisions.
- Uses fixture data to keep retry budgets changes visible in code review.
- Includes extended examples for runbook checks, including `recovery` and `degraded`.
- Documents recovery paths tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.

## How To Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.

## Validation

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Repository Map

- `src`: primary implementation
- `test`: language test directory
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `foundry.toml`: Foundry project configuration

## Follow-Up Work

- Add malformed input fixtures so the failure path is as visible as the happy path.
- Split the scoring constants into a typed configuration object and validate it before use.
- Add a comparison mode that shows how decisions change when one signal is adjusted.
- Add one more reliability fixture that focuses on a malformed or borderline input.

## Known Edges

The examples cover useful edges, not every edge. A larger version would add malformed-input tests, richer reports, and deeper domain parsers.

## Run It Locally

Use a normal shell with Solidity available on `PATH`. The verifier is written as a PowerShell script because the portfolio was assembled on Windows.
