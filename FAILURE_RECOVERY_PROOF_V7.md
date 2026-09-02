# Privattice — Failure & Recovery Proof v7

## Mandatory injected failures
- projection corruption
- AGE unavailable
- cyclic graph
- high-degree node
- path explosion
- source conflict
- rebuild interruption
- duplicate import

## Pass criteria
For every failure: no invariant violation; no unauthorized bypass; no unbounded retry storm; orphan resources are reconciled; user-visible state becomes correct; telemetry identifies cause; retry/cancel/manual recovery is documented; recovery test is automated where feasible.
