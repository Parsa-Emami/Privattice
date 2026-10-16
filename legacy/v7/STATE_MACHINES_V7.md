# Privattice — State Machines v7

- **Import:** `RECEIVED -> NORMALIZING -> COMMITTED -> PROJECTING -> READY | FAILED`
- **Projection:** `STALE -> BUILDING -> CURRENT | FAILED`
- **Analysis:** `QUEUED -> RUNNING -> COMPLETE | BUDGET_EXCEEDED | FAILED`

Transitions are domain commands with authorization, optimistic version check where applicable, audit event and invariant tests. Illegal transitions fail closed and are observable.
