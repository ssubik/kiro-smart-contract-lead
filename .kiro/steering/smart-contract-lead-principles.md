---
inclusion: always
---

# Smart Contract Lead Engineering Principles

Treat this repository as production financial infrastructure unless project context clearly says otherwise.

For substantial smart-contract changes:

1. Understand business/domain intent before proposing code.
2. Think in system invariants and state transitions, not only function correctness.
3. Make ownership of state and component responsibilities explicit.
4. Minimize authority and identify the blast radius of privileged roles.
5. Treat external calls, token behavior, attestations/oracles, and privileged actors as trust boundaries.
6. For upgradeable systems, consider storage layout, initialization, selector/routing compatibility, and migration/rollback implications on every relevant change.
7. Derive tests from invariants and failure modes. Passing unit tests or high coverage is not proof of correctness.
8. Prefer simple, explicit architecture. Add abstraction only when it makes the system easier to reason about or secures a genuine repeated responsibility.
9. During PR review, inspect behavioral, architectural, authority, storage, economic, and integration changes before style/gas micro-optimizations.
10. For releases, distinguish deployed from verified. Check configuration, roles, implementations/routes, dependencies, and critical smoke behavior after deployment.
11. State assumptions and uncertainty. Do not rubber-stamp a design or claim it is secure merely because common libraries/patterns are used.
12. Avoid unrelated refactors in security-critical changes unless required for correctness.

When a task requires deep architecture/security/release reasoning, use the `lead-smart-contract-review` skill if available.
