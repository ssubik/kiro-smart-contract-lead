# Testing and PR Review

## Risk-to-test mapping

Do not start from "which functions need tests?" Start from "which properties/failure modes need evidence?"

### Unit tests
Use for deterministic local behavior and specific transition rules.

### Fuzz tests
Use when the dangerous space is input combinations, amounts, boundaries, ordering parameters, timestamps, or identities.

### Stateful invariant tests
Use when correctness must survive arbitrary sequences of operations across multiple actors and states.

Build handlers that represent realistic allowed actions and include adversarial sequencing. Track ghost variables/reference accounting when useful.

### Differential tests
Use when there is a simpler trusted model/reference implementation whose outputs/properties can be compared.

### Fork/integration tests
Use when correctness depends on real deployed contracts, token behavior, proxy state, permissions, oracle state, or upgrade migration.

### Smoke tests
Use after deployment for a small set of critical end-to-end behaviors that demonstrate wiring/configuration is correct. Smoke tests are not a substitute for the full suite.

## PR review order

1. Requirement/domain delta
2. Architecture/boundaries
3. Invariants/economic effects
4. Authority/access control
5. Storage/upgrade compatibility
6. External interactions
7. Test evidence
8. Integration/release impact
9. Implementation readability/gas/style

## Questions to force depth

- What is the highest-value thing this PR can break?
- What behavior changed even if the ABI did not?
- Which old invariant relies on an assumption this PR changes?
- Is any new privileged path introduced indirectly?
- Can a callback observe an intermediate state?
- Can the action be replayed or performed twice?
- What happens at zero, max, boundary timestamps, and rounding edges?
- What happens when the external dependency behaves unexpectedly?
- What test would have caught the most damaging plausible bug?

## Coverage

Coverage is a signal for unexecuted code, not correctness. Prefer changed-line coverage as a fast gate only when backed by risk-based tests and periodic/full-suite coverage. Never lower system-level testing merely to optimize CI latency.
