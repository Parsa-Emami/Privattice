# Privattice — First 30 Commit Plan v7

These are atomic intent boundaries, not mandatory commit-message text. Do not combine unrelated items merely to hit a number.

1. chore: initialize toolchain manifests and lockfiles
2. ci: make repository validation executable
3. chore: add local development environment/health checks
4. test: add clean-bootstrap smoke test
5. docs: freeze Phase 0 invariants and ADR index
6. phase0: bootstrap authoritative PostgreSQL inventory model
7. phase0: define source adapters and provenance envelope
8. phase0: normalize assets/identities/relationships
9. phase0: assign stable IDs independent of ingestion order
10. test(phase0): add normalization fixtures
11. docs(phase0): record exit evidence and ADR updates
12. phase1: define relational→graph projection contract
13. phase1: implement idempotent projector to Apache AGE
14. phase1: store projection generation/checkpoint
15. phase1: support full drop/rebuild
16. test(phase1): add projection golden tests
17. docs(phase1): record exit evidence and ADR updates
18. phase2: implement bounded path query API
19. phase2: enforce depth/node/time budgets
20. phase2: add query cancellation and cost telemetry
21. phase2: return explicit truncation metadata
22. test(phase2): add budget enforcement tests
23. docs(phase2): record exit evidence and ADR updates
24. phase3: version risk rules and weights
25. phase3: separate observed facts from inferred risk
26. phase3: produce explanation path for each risk score
27. phase3: calibrate unknown/missing data behavior
28. test(phase3): add explanation consistency tests
29. docs(phase3): record exit evidence and ADR updates
30. test: close Phase 0/1 regression or failure-proof gap before scope expansion
