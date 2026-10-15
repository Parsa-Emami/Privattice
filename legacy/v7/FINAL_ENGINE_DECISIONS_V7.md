# Privattice — Final Engine Decisions v7

These are accepted v1 decisions, not open blockers. Alternatives require a future ADR and must preserve public/domain contracts.

1. PostgreSQL relational inventory is authoritative. Apache AGE v1.7/PG18 is the reference graph projection backend for v1.
2. GraphBackend is a port; optional Neo4j Community adapter may exist later without changing domain semantics or licensing the core under GPL.
3. Projection rows carry source entity version/checkpoint. A full graph rebuild must reproduce the same semantic edge-set hash.
4. Traversal is always bounded by max depth, max paths, max expanded vertices, wall-clock deadline and cancellation token.
5. Path ranking is deterministic: edge exposure weight + privilege gain + evidence confidence + target criticality; scoring formula is versioned.
6. Every relationship edge has provenance/source/confidence/observed_at. Conflicts are preserved and resolved by explicit precedence policy, never overwritten silently.
7. No write is accepted only into the graph projection. All imports land in authoritative inventory first.
