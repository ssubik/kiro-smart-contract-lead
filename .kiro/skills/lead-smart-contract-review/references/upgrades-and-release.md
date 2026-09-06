# Upgrade, Release, and Deployment Review

## Upgrade compatibility

Check the actual mechanism in this repository. Depending on proxy/router architecture inspect:
- storage layout diff
- inheritance reordering
- inserted/removed state variables
- storage gaps/namespaces
- constructors vs initializers
- initializer replay/protection
- implementation initialization lock
- immutable values
- library linking
- selector additions/removals/replacements/collisions
- interface/event compatibility
- migration steps
- version metadata

Do not assume rollback is safe. A new implementation may mutate storage into a shape the old implementation cannot interpret.

## Upgrade manifest

For meaningful upgrades prefer a machine-readable or reviewable manifest containing:
- component/package
- previous version and target version
- old implementation
- new implementation
- selectors/functions changed
- storage-layout result
- expected bytecode/code hash when available
- linked libraries/dependencies
- initializer/migration calldata
- deployment transaction/address
- required role/config changes

## Pre-deployment gates

Require appropriate evidence for:
- compile/test success
- unit/fuzz/invariant tests
- storage compatibility
- selector/routing checks
- fork/integration test where environment dependency matters
- review/audit findings disposition when applicable
- deployment script dry-run/simulation
- correct chain and addresses

## Post-deployment verification

Verify state, not only transaction success:
- implementation/proxy/admin/beacon
- expected runtime bytecode
- roles/ownership/guardian
- initialized values
- version registration
- selectors/routes
- dependency addresses
- pause state
- key balances/accounting
- emitted events
- representative smoke operations

## Release strategy

Prefer small, reproducible releases with explicit compatibility expectations. Separate:
- code complete
- reviewed
- release/tagged
- deployed
- verified
- production-ready

A tag or successful deployment does not by itself imply production readiness.
