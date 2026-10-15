# Privattice — product implementation roadmap

Web application delivery is tracked separately in [WEB_ROADMAP.md](WEB_ROADMAP.md). Engine milestones remain pending unless backed by their own evidence.

## C01 — `docs(product): confirm personal use acceptance and demand hypotheses`

Stage: foundation. Dependencies: None. Requirements: N01.

Deliverables: `docs/product/VALIDATION_LOG.md`.

- Choose one owned real task, identify current workaround and record measured baseline; public demand remains unvalidated.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C01.json.

Evidence: `docs/evidence/C01.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C02 — `chore(toolchain): verify supported versions and lock dependencies`

Stage: foundation. Dependencies: C01. Requirements: N02.

Deliverables: `docs/engineering/toolchain-lock.json`.

- Official support/release URLs and verification date exist for each selected dependency; no future or assumed version pin.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C02.json.

Evidence: `docs/evidence/C02.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C03 — `chore(app): initialize selected minimal runtime`

Stage: foundation. Dependencies: C02. Requirements: N03.

Deliverables: `docs/engineering/BOOTSTRAP_EVIDENCE.md`, `go.mod`, `go.sum`, `cmd/privattice/main.go`, `package.json`, `package-lock.json`, `apps/web/src/main.tsx`, `docs/engineering/WEB_RUNBOOK.md`.

- Fresh checkout boots minimal CLI or local UI; do not run legacy Laravel/PostgreSQL bootstrap.
- Web entry point is mandatory. W01-W05 supply the tested shell; complete engine obligations before verifying C03.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C03.json.

Evidence: `docs/evidence/C03.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C04 — `feat(contracts): freeze typed local and transport contracts`

Stage: foundation. Dependencies: C03. Requirements: N04.

Deliverables: `contracts/README.md`, `contracts/input.schema.json`, `contracts/result.schema.json`.

- Inputs, errors, output, schema versions, timeout and compatibility behavior are typed with positive/negative fixtures.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C04.json.

Evidence: `docs/evidence/C04.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C05 — `feat(storage): implement minimal authoritative storage adapter`

Stage: foundation. Dependencies: C04. Requirements: N05.

Deliverables: `docs/architecture/STORAGE_PROOF.md`, `internal/storage/adapter.go`, `tests/storage_test.go`.

- Authority, atomic write boundary and recovery mechanism match selected profile; storage loss test has actionable result.

Verification: tests/storage_test.go.

Evidence: `docs/evidence/C05.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C06 — `ci(checks): run actual runtime build and foundational tests`

Stage: foundation. Dependencies: C05. Requirements: N06.

Deliverables: `.github/workflows/runtime.yml`.

- Clean-checkout build, formatting and contract/invariant tests pass; plan validation is never reported as application testing.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C06.json.

Evidence: `docs/evidence/C06.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C07 — `feat(import): parse versioned inventory snapshots`

Stage: domain. Dependencies: C06. Requirements: F01.

Deliverables: `internal/importer/parser.go`, `tests/import_test.go`.

- Unsupported columns and source schema fail before inventory commit.

Verification: tests/import_test.go.

Evidence: `docs/evidence/C07.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C08 — `feat(normalize): assign stable entity and edge identities`

Stage: domain. Dependencies: C07. Requirements: F02.

Deliverables: `internal/inventory/normalize.go`, `tests/identity_test.go`.

- Input reordering does not change IDs or normalized edge hash.

Verification: tests/identity_test.go.

Evidence: `docs/evidence/C08.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C09 — `feat(provenance): retain source confidence and observation time`

Stage: domain. Dependencies: C08. Requirements: F03.

Deliverables: `internal/inventory/provenance.go`, `tests/provenance_test.go`.

- Conflicting assertions remain individually inspectable.

Verification: tests/provenance_test.go.

Evidence: `docs/evidence/C09.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C10 — `feat(inventory): atomically commit snapshot revisions`

Stage: domain. Dependencies: C09. Requirements: F04.

Deliverables: `internal/inventory/repository.go`, `tests/transaction_test.go`.

- Interrupted import exposes neither partial entities nor partial edges.

Verification: tests/transaction_test.go.

Evidence: `docs/evidence/C10.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C11 — `feat(graph): build bounded adjacency projection`

Stage: domain. Dependencies: C10. Requirements: F05.

Deliverables: `internal/graph/build.go`, `tests/graph_test.go`.

- Projection carries snapshot version and stays within memory budget.

Verification: tests/graph_test.go.

Evidence: `docs/evidence/C11.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C12 — `feat(rebuild): rebuild graph from authoritative inventory`

Stage: domain. Dependencies: C11. Requirements: F06.

Deliverables: `internal/graph/rebuild.go`, `tests/rebuild_test.go`.

- Deleted projection is reconstructed with identical semantic hash.

Verification: tests/rebuild_test.go.

Evidence: `docs/evidence/C12.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C13 — `feat(paths): enumerate bounded privilege paths`

Stage: domain. Dependencies: C12. Requirements: F07.

Deliverables: `internal/graph/paths.go`, `tests/paths_test.go`.

- Cycle handling terminates and result order is deterministic.

Verification: tests/paths_test.go.

Evidence: `docs/evidence/C13.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C14 — `feat(budgets): enforce expansion depth and deadline limits`

Stage: domain. Dependencies: C13. Requirements: F08.

Deliverables: `internal/graph/budget.go`, `tests/budget_test.go`.

- High-degree graph returns truncation reason and can be cancelled.

Verification: tests/budget_test.go.

Evidence: `docs/evidence/C14.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C15 — `feat(scoring): version explainable path ranking`

Stage: domain. Dependencies: C14. Requirements: F09.

Deliverables: `internal/risk/score.go`, `tests/score_test.go`.

- Score includes weight version and missing facts lower confidence explicitly.

Verification: tests/score_test.go.

Evidence: `docs/evidence/C15.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C16 — `feat(conflicts): apply explicit source precedence`

Stage: domain. Dependencies: C15. Requirements: F10.

Deliverables: `internal/inventory/resolve.go`, `tests/conflict_test.go`.

- Resolution records reason and original evidence is retained.

Verification: tests/conflict_test.go.

Evidence: `docs/evidence/C16.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C17 — `feat(simulation): compute hypothetical edge removal`

Stage: domain. Dependencies: C16. Requirements: F11.

Deliverables: `internal/remediation/simulate.go`, `tests/simulate_test.go`.

- Simulation cannot modify authoritative snapshot and reports changed reachable targets.

Verification: tests/simulate_test.go.

Evidence: `docs/evidence/C17.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C18 — `feat(diff): compare snapshots by semantic edges`

Stage: domain. Dependencies: C17. Requirements: F12.

Deliverables: `internal/inventory/diff.go`, `tests/diff_test.go`.

- Added and removed permissions are distinct from reordered records.

Verification: tests/diff_test.go.

Evidence: `docs/evidence/C18.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C19 — `feat(api): expose private path and inventory endpoints`

Stage: domain. Dependencies: C18. Requirements: F13.

Deliverables: `internal/http/api.go`, `tests/api_test.go`.

- Unauthenticated request fails and queries accept only bounded parameters.

Verification: tests/api_test.go.

Evidence: `docs/evidence/C19.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C20 — `feat(ui): show import history and inventory`

Stage: domain. Dependencies: C19. Requirements: F14.

Deliverables: `apps/web/src/pages/Inventory.tsx`, `apps/web/tests/inventory.spec.ts`.

- Source, age, missing data and failed imports are visible.

Verification: apps/web/tests/inventory.spec.ts.

Evidence: `docs/evidence/C20.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C21 — `feat(ui): render paths with keyboard table alternative`

Stage: domain. Dependencies: C20. Requirements: F15.

Deliverables: `apps/web/src/pages/Paths.tsx`, `apps/web/tests/paths.spec.ts`.

- Every displayed path links provenance and truncation metadata.

Verification: apps/web/tests/paths.spec.ts.

Evidence: `docs/evidence/C21.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C22 — `feat(ui): compare remediation simulation results`

Stage: domain. Dependencies: C21. Requirements: F16.

Deliverables: `apps/web/src/pages/Remediation.tsx`, `apps/web/tests/remediation.spec.ts`.

- Observed facts and hypothetical effects have separate text labels.

Verification: apps/web/tests/remediation.spec.ts.

Evidence: `docs/evidence/C22.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C23 — `feat(export): create portable snapshot analysis report`

Stage: domain. Dependencies: C22. Requirements: F17.

Deliverables: `internal/export/bundle.go`, `tests/export_test.go`.

- Report binds snapshot hash, rules and query budgets.

Verification: tests/export_test.go.

Evidence: `docs/evidence/C23.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C24 — `feat(retention): expire source imports safely`

Stage: domain. Dependencies: C23. Requirements: F18.

Deliverables: `internal/retention/cleanup.go`, `tests/retention_test.go`.

- Deletion cannot leave a current graph claiming missing inventory as present.

Verification: tests/retention_test.go.

Evidence: `docs/evidence/C24.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C25 — `feat(privacy): redact identifiers in shared reports`

Stage: domain. Dependencies: C24. Requirements: F19.

Deliverables: `internal/export/redact.go`, `tests/redact_test.go`.

- Redacted IDs preserve relation consistency without mapping file in public bundle.

Verification: tests/redact_test.go.

Evidence: `docs/evidence/C25.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C26 — `test(capacity): benchmark bounded snapshot analysis`

Stage: domain. Dependencies: C25. Requirements: F20.

Deliverables: `tests/benchmark_test.go`, `docs/evidence/graph-benchmark-template.md`.

- Target graph workload stays within budget or documented lower supported limit is adopted.

Verification: tests/benchmark_test.go.

Evidence: `docs/evidence/C26.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C27 — `test(security): close abuse and authorization release gaps`

Stage: private-release. Dependencies: C26. Requirements: N27.

Deliverables: `tests/release/security-matrix.md`.

- Run project-specific negative UAT plus XSS/import/auth checks for enabled surfaces; document unsupported attack surface and unresolved findings.

Verification: tests/release/security-matrix.md.

Evidence: `docs/evidence/C27.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C28 — `perf(budgets): measure target workload and overload behavior`

Stage: private-release. Dependencies: C27. Requirements: N28.

Deliverables: `docs/evidence/performance.json`.

- Record hardware, OS, source digest, workload, p50/p95/p99 where meaningful, CPU, RSS, storage growth, cancellation and saturation; lower supported limits if targets fail.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C28.json.

Evidence: `docs/evidence/C28.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C29 — `feat(operations): expose health diagnostics and bounded logs`

Stage: private-release. Dependencies: C28. Requirements: N29.

Deliverables: `ops/diagnostics.md`.

- Local health/status path identifies storage/job/provider failure; sensitive content is absent from synthetic log sentinel test.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C29.json.

Evidence: `docs/evidence/C29.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C30 — `test(recovery): prove personal backup restore and private install`

Stage: private-release. Dependencies: C29. Requirements: N30.

Deliverables: `docs/evidence/private-install.json`.

- Fresh machine/browser install and restore completes project UAT; personal deployment remains private until its relevant safety gates pass.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C30.json.

Evidence: `docs/evidence/C30.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C31 — `build(packaging): create versioned installable artifacts`

Stage: public-release. Dependencies: C30. Requirements: N31.

Deliverables: `scripts/package.sh`, `docs/release/ARTIFACTS.md`, `ops/web/nginx.conf.template`, `ops/web/service.systemd`, `docs/engineering/WEB_RUNBOOK.md`.

- Static/CLI/container artifact matches chosen distribution; SBOM, licenses, checksums and provenance truthfully reflect what is built.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C31.json.

Evidence: `docs/evidence/C31.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C32 — `feat(web): configure domain tls and isolated public demo`

Stage: public-release. Dependencies: C31. Requirements: N32.

Deliverables: `infra/deployment.md`, `docs/evidence/domain.json`.

- Domain/HTTPS/cookies/CSP and private-origin policy are checked; public demo contains synthetic data only and dangerous runtime features are disabled.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C32.json.

Evidence: `docs/evidence/C32.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C33 — `test(ux): verify accessibility mobile and update behavior`

Stage: public-release. Dependencies: C32. Requirements: N33.

Deliverables: `docs/evidence/ux.json`.

- Keyboard/table alternative, 360px through 1440px layouts, empty/error/offline states and N-1 data upgrade fixtures work on documented supported platforms.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C33.json.

Evidence: `docs/evidence/C33.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C34 — `docs(release): publish english usage limits and support contract`

Stage: public-release. Dependencies: C33. Requirements: N34.

Deliverables: `docs/release/USER_GUIDE.md`, `SECURITY.md`.

- New user completes one documented task; English install/use/privacy/limits/support pages include owner contact supplied by maintainer and actual evidence links.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C34.json.

Evidence: `docs/evidence/C34.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C35 — `test(release): exercise signed artifact and clean upgrade paths`

Stage: public-release. Dependencies: C34. Requirements: N35.

Deliverables: `docs/evidence/release-verification.json`.

- Install artifact from clean environment; verify signer with independently trusted key/identity; supported upgrade and rollback preserve latest valid data.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C35.json.

Evidence: `docs/evidence/C35.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C36 — `docs(beta): record independent pilot feedback and beta gate`

Stage: public-release. Dependencies: C35. Requirements: N36.

Deliverables: `docs/product/PILOT_RESULTS.md`.

- Target: 5 relevant trials, 3 complete core task and 2 return for real repeat use; if unavailable continue personal release and mark demand unvalidated rather than inventing pilots.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C36.json.

Evidence: `docs/evidence/C36.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C37 — `fix(beta): resolve evidence backed pilot blockers`

Stage: public-release. Dependencies: C36. Requirements: N37.

Deliverables: `docs/product/BETA_FIXES.md`.

- Fix observed failures, re-run affected checks, record remaining limitations; if no pilots, use observed personal UAT issues and retain unvalidated market label.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C37.json.

Evidence: `docs/evidence/C37.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C38 — `docs(service): freeze retention portability quotas and support policy`

Stage: public-release. Dependencies: C37. Requirements: N38.

Deliverables: `docs/release/SERVICE_POLICY.md`.

- For public service state data location, deletion/export rules, quotas, expected support and outage behavior; paid billing and SLA are not enabled without separate ADR.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C38.json.

Evidence: `docs/evidence/C38.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C39 — `ci(release): verify v1 gate from clean source tree`

Stage: public-release. Dependencies: C38. Requirements: N39.

Deliverables: `docs/evidence/v1-gate.json`.

- Every mandatory requirement has actual passed evidence; no critical open security/recovery issue; release profile and demand status are explicit.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C39.json.

Evidence: `docs/evidence/C39.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.

## C40 — `chore(release): publish v1 artifacts and monitor first use`

Stage: public-release. Dependencies: C39. Requirements: N40.

Deliverables: `docs/evidence/launch.json`, `plans/progress.json`.

- Release only verified profile artifacts, run installed smoke test, record actual version/source digest and follow up support/rollback; never publish fabricated claims.

Verification: Run the actual project checks relevant to this task and record results in docs/evidence/C40.json.

Evidence: `docs/evidence/C40.json`.

Rollback: Before release: revert isolated code change with tests. For persisted data: preserve exports/backup and last compatible reader; use forward repair after new writes. Do not restore a stale snapshot over newer data.
