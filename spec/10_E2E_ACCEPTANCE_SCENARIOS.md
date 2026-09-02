# Privattice — Final Implementation Specification

This specification freezes the v1 implementation contract. Changes that violate an invariant, authority boundary or public contract require an ADR/RFC and migration/compatibility plan.

## Golden E2E scenarios
1. Import authoritative inventory and project graph
2. Query bounded explainable path
3. Drop projection and rebuild same semantic edge-set digest
4. Cycle/high-degree graph hits budget cleanly
5. Conflicting source facts preserve provenance

For every golden scenario record expected authoritative state, emitted event IDs/types, audit action, projection state, critical metrics and cleanup state. Run from a clean environment with deterministic synthetic fixtures. At least one scenario must fail mid-flight and then converge after restart/retry/reconciliation.
