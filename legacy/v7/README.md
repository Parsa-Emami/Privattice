# Privattice

> v7.0 status: **ARCHITECTURE-GO / BOOTSTRAP-GO / SOURCE-NOT-IMPLEMENTED**

This directory is a standalone GitHub repository starting point for Privattice. It contains the frozen architecture/specification, valid HTTP/event/configuration contracts, GitHub governance/security controls, and project-specific source bootstrap commands.

## Runtime boundary
- Laravel 13 control plane
- Go 1.27 graph builder/analyzer
- PostgreSQL 18.6
- Apache AGE 1.7.0 for PostgreSQL 18
- Valkey
- OpenTelemetry

## First executable proof
Inventory import → authoritative relational state → AGE projection → bounded path query → drop/rebuild projection → identical projection hash.

## Start
```bash
make validate
# verify the GitHub owner/module namespace first
make bootstrap
```

Read `ROADMAP_V7.md`, `PROJECT_START_CHECKLIST_V7.md`, `ACCEPTANCE_GATES_V7.md`, and `GITHUB_REPOSITORY_SETUP_V7.md` before the first code commit.

## Evidence rule
Architecture readiness is not production readiness. “S-tier”, “secure”, “resilient”, or performance claims require executable test/observability/failure/recovery/benchmark/release evidence.

## v7 portfolio position
Recommended implementation order: **4 / 10**. Graph projection/rebuild semantics are valuable but AGE adds operational complexity; better after one simpler project is shipped.
