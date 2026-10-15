# ADR 0003 — Privattice reference decision

**Status:** Accepted for v1

## Decision
Projection rows carry source entity version/checkpoint. A full graph rebuild must reproduce the same semantic edge-set hash.

## Consequences
Implementation and tests must preserve this boundary. An alternative is allowed only through the relevant port/adapter when it preserves authority, public contracts, security invariants and migration semantics.

## Revisit trigger
Measured benchmark, security evidence, maintenance/licensing change or operational incident demonstrates the reference choice no longer satisfies the declared workload/threat model. Revisit via a new superseding ADR; never silently rewrite history.
