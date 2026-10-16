# Privattice — Final Implementation Specification

This specification freezes the v1 implementation contract. Changes that violate an invariant, authority boundary or public contract require an ADR/RFC and migration/compatibility plan.

| Data class | v1 rule |
|---|---|
| raw imports | content-addressed snapshots by policy; can expire after provenance-safe period |
| authoritative entities | current + history necessary for provenance |
| graph projection | disposable/rebuildable |
| query results | short-lived cache; saved analyst findings explicit records |

## Classification labels
`PUBLIC`, `INTERNAL`, `CONFIDENTIAL`, `SECRET`, plus project-specific `EVIDENCE`/`SECURITY_TELEMETRY`. Classification drives logging, export, encryption, backup and retention behavior.

## Deletion
Deletion is an explicit domain operation with authorization, hold checks, audit and downstream projection/cache invalidation. Derived stores must not resurrect deleted authoritative data during rebuild.
