# Nexus Rel Retry Grid Walkthrough

I use this file as a small checklist before changing the Solidity implementation.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | budget pressure | 173 | ship |
| stress | failure width | 185 | ship |
| edge | recovery gap | 135 | watch |
| recovery | runbook drift | 185 | ship |
| stale | budget pressure | 202 | ship |

Start with `stale` and `edge`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

The next useful expansion would be a malformed fixture around failure width and runbook drift.
