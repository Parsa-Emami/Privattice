# Privattice — Data Ownership v7

- **PostgreSQL:** authoritative identities/assets/relationships/provenance
- **Apache AGE:** derived graph projection
- **Valkey:** jobs/cache only
- **ObjectStore:** raw import snapshots

## Universal rules
- cache is never authority
- derived projections have checkpoint + rebuild + staleness metric
- secrets/evidence follow project-specific retention and redaction
- deletion does not rewrite immutable audit/custody history
