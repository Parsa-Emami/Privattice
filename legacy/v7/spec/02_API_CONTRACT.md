# Privattice — Final Implementation Specification

This specification freezes the v1 implementation contract. Changes that violate an invariant, authority boundary or public contract require an ADR/RFC and migration/compatibility plan.

## HTTP conventions
- Prefix `/api/v1`; JSON UTF-8; explicit content type.
- Resource IDs are opaque UUID/ULID-style identifiers and authorization is re-evaluated after lookup.
- Cursor pagination for unbounded collections.
- Mutation request/response schemas are versioned in OpenAPI; unknown security-sensitive fields are rejected where ambiguity is dangerous.
- Stable error codes follow the common error standard.

| Method | Route | Purpose | Gate |
|---|---|---|---|
| `POST` | `/imports` | Ingest versioned synthetic/authorized inventory | auth + validation + idempotency where side-effecting |
| `GET` | `/assets/{asset}` | Read authoritative asset + graph freshness | auth + validation + idempotency where side-effecting |
| `POST` | `/paths/query` | Bounded path query | auth + validation + idempotency where side-effecting |
| `GET` | `/projections/status` | Projection checkpoint/staleness | auth + validation + idempotency where side-effecting |
| `POST` | `/projections/rebuild` | Admin rebuild derived graph | auth + validation + idempotency where side-effecting |
| `POST` | `/remediations/simulate` | Non-destructive what-if edge changes | auth + validation + idempotency where side-effecting |

## Compatibility
Additive compatible changes may ship in v1. Removing/renaming/changing semantics requires deprecation + migration and normally a new API major. Golden request/response fixtures run in CI.
