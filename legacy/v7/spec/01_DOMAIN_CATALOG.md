# Privattice — Final Implementation Specification

This specification freezes the v1 implementation contract. Changes that violate an invariant, authority boundary or public contract require an ADR/RFC and migration/compatibility plan.

## Domain objects
- `Source`
- `ImportSnapshot`
- `Identity`
- `Group`
- `Role`
- `Asset`
- `Relationship`
- `Provenance`
- `ProjectionCheckpoint`
- `GraphPath`
- `RiskModel`
- `RemediationSimulation`

## Aggregate rules
- Aggregate mutations occur through application commands, never controller/model convenience writes.
- Aggregate version is checked on conflicting writes.
- Invariants are tested with illegal-transition/negative cases.
- Domain objects do not import Laravel/Eloquent/vendor SDKs.

## Frozen v1 invariants
1. No relationship exists without provenance/confidence/source version.
2. Graph projection can be deleted and rebuilt from PostgreSQL without semantic loss.
3. Queries are bounded and cancellable.
4. Risk score records formula version and evidence; graph visualization never fabricates missing edges.
