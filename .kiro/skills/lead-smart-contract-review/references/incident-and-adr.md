# Incident Readiness and ADRs

## Incident tabletop

For high-value components, periodically simulate:
- accounting mismatch
- compromised privileged key
- incorrect oracle/attestation
- broken upgrade
- stuck/paused settlement
- unauthorized asset movement
- external dependency failure

For each scenario answer:
1. How is it detected?
2. Who is paged/notified?
3. Can the blast radius be contained?
4. Which keys/roles/actions are required?
5. What evidence/state must be captured before intervention?
6. Can the system be paused safely?
7. Can it be upgraded safely in the current state?
8. Is rollback actually storage-compatible?
9. How are users/integrators reconciled afterward?
10. What invariant/process should change to prevent recurrence?

## Lightweight ADR template

Use ADRs only for decisions future engineers may reasonably question.

```text
ADR-NNN: <decision>

Context
- What problem/constraint caused this decision?

Options
- A
- B
- C (if relevant)

Decision
- Chosen approach

Why
- Security/correctness
- simplicity/maintainability
- compatibility/operations

Consequences
- What becomes easier?
- What becomes harder?
- What risks remain?

Revisit when
- Conditions that should trigger reevaluation
```

Keep an ADR short enough that engineers will actually maintain it.
