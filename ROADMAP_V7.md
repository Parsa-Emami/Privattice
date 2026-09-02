# Privattice — Definitive Sequential Roadmap v7

**Portfolio order:** 4 / 10
**Complexity:** High
**Planning estimate:** 12–16 focused weeks (not a promise; recalibrate after Phase 1)

**Why this order:** Graph projection/rebuild semantics are valuable but AGE adds operational complexity; better after one simpler project is shipped.

## First executable proof
Inventory import → authoritative relational state → AGE projection → bounded path query → drop/rebuild projection → identical projection hash.

## Rules for this repository
- One phase at a time; no implementation work for phase N+1 before phase N exit evidence is merged.
- Contract/schema changes precede dependent implementation.
- Every retryable operation is idempotent.
- Every derived store/projection has a rebuild path.
- Negative and failure tests are part of the feature, not post-release hardening.
- Status claims must be evidence-backed.

## Phase 0 — Inventory/provenance model

**Implementation deliverables**
- Bootstrap authoritative PostgreSQL inventory model
- Define source adapters and provenance envelope
- Normalize assets/identities/relationships
- Assign stable IDs independent of ingestion order

**Required verification**
- normalization fixtures
- duplicate/reordered ingestion tests
- provenance completeness tests

**Definition of Done**
- Equivalent inventory inputs create the same authoritative entities and provenance regardless of record order.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 1 — AGE projection compiler

**Implementation deliverables**
- Define relational→graph projection contract
- Implement idempotent projector to Apache AGE
- Store projection generation/checkpoint
- Support full drop/rebuild

**Required verification**
- projection golden tests
- idempotency tests
- drop/rebuild hash test

**Definition of Done**
- Dropping AGE state and rebuilding from PostgreSQL produces an identical projection hash.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 2 — Bounded path engine

**Implementation deliverables**
- Implement bounded path query API
- Enforce depth/node/time budgets
- Add query cancellation and cost telemetry
- Return explicit truncation metadata

**Required verification**
- budget enforcement tests
- path correctness fixtures
- adversarial graph tests

**Definition of Done**
- Queries cannot run unbounded and report when results are truncated by safety limits.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 3 — Risk/explanation model

**Implementation deliverables**
- Version risk rules and weights
- Separate observed facts from inferred risk
- Produce explanation path for each risk score
- Calibrate unknown/missing data behavior

**Required verification**
- explanation consistency tests
- missing-data tests
- score determinism tests

**Definition of Done**
- Every score is reproducible and traceable to facts, rule version, and graph paths.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 4 — Graph UI

**Implementation deliverables**
- Render bounded graph slices only
- Progressive expansion with server-side budgets
- Accessible tabular alternative to graph
- Preserve query/revision context in URL/state

**Required verification**
- UI performance tests
- keyboard navigation tests
- large-slice guard tests

**Definition of Done**
- UI never requests an unbounded graph and all core information is available without visual-only interaction.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 5 — Remediation simulation

**Implementation deliverables**
- Clone graph state logically for simulation
- Apply hypothetical control changes without mutating authoritative facts
- Recompute affected paths/risks
- Show delta with assumptions

**Required verification**
- non-mutation tests
- delta correctness fixtures
- simulation isolation tests

**Definition of Done**
- Simulations are isolated, reproducible, and cannot alter observed inventory state.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 6 — Snapshot/diff/import adapters

**Implementation deliverables**
- Immutable snapshots of authoritative state
- Entity/relationship diff engine
- Additional inventory adapters behind common boundary
- Import error quarantine/report

**Required verification**
- snapshot integrity tests
- diff fixtures
- adapter contract tests

**Definition of Done**
- Two snapshots produce deterministic diffs and adapter failures cannot partially corrupt authoritative state.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Phase 7 — Scale/failure/public v1

**Implementation deliverables**
- Projection lag SLOs
- AGE unavailable/recovery behavior
- Large graph benchmark
- Signed release and rebuild drill

**Required verification**
- failure injection
- restore/rebuild drill
- load benchmark

**Definition of Done**
- Public v1 demonstrates recovery from derived-store loss and meets documented bounded-query budgets.
- CI is green from a clean checkout.
- New behavior is observable without logging secrets/sensitive payloads.
- Failure behavior and rollback/recovery note are documented.
- Contracts and README status are updated if externally visible behavior changed.

## Public v1 invariant
The project is not called production-ready merely because all phases are coded. `PUBLIC-V1-GO` requires the repository release gate, clean-install proof, security/recovery evidence and signed/verifiable release artifacts.
