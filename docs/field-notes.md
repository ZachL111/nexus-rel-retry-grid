# Field Notes

`nexus-rel-retry-grid` is easiest to review by starting with the fixture, not the prose.

The domain cases cover `budget pressure`, `failure width`, `recovery gap`, and `runbook drift`. They sit beside the smaller starter fixture so the project has both a compact scoring check and a domain-flavored review check.

The widest spread is between `budget pressure` and `recovery gap`, so those are the first two cases I would preserve during a refactor.

The extra check gives the repository a behavior path that can fail for a domain reason, not only a syntax reason.
