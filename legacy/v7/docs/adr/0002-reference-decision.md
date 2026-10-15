# ADR 0002 — Privattice reference decision

**Status:** Accepted for v1

## Decision
GraphBackend is a port; optional Neo4j Community adapter may exist later without changing domain semantics or licensing the core under GPL.

## Consequences
Implementation and tests must preserve this boundary. An alternative is allowed only through the relevant port/adapter when it preserves authority, public contracts, security invariants and migration semantics.

## Revisit trigger
Measured benchmark, security evidence, maintenance/licensing change or operational incident demonstrates the reference choice no longer satisfies the declared workload/threat model. Revisit via a new superseding ADR; never silently rewrite history.
