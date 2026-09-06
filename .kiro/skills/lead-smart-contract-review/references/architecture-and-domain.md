# Architecture and Domain Review

## Contract-boundary test

For every component answer five questions:
1. What state is authoritative here?
2. What decisions may this component make?
3. Which actors/components can request those decisions?
4. Which external facts does it trust?
5. Which domain concepts should it remain ignorant of?

A boundary is suspicious when two contracts both believe they own the same business fact, a generic asset-transfer component knows agreement/default/business semantics, or changing one requirement requires touching many unrelated components.

## Prefer authority boundaries over file-size boundaries

Do not split a contract merely because it is large. Split when responsibilities, authority, lifecycle, trust, or upgrade cadence are meaningfully different.

## Abstraction test

Before adding an abstraction ask:
- What concrete duplication/problem exists now?
- Are there at least two real use cases?
- Does the abstraction make privilege, storage, value movement, and error behavior easier to reason about?
- Can a reviewer understand the execution path without jumping through many contracts?
- Will the abstraction remain stable if the domain changes?

Prefer duplication over a misleading abstraction when the shared shape is accidental rather than semantic.

## State-machine review

Represent states explicitly when the domain has lifecycle restrictions. For every transition document:
- source state(s)
- target state
- actor/authority
- business preconditions
- value/state effects
- external interactions
- emitted evidence
- timeout/time dependency
- recovery/reversal semantics

Look for:
- skipped states
- impossible/reachable-invalid states
- transitions that can execute twice
- partial transitions around external calls
- final states that are accidentally reversible
- asset movement before entitlement is established
- state changes that rely on off-chain assumptions not enforced on-chain

## Economic flow review

Trace value as a ledger, not as a call graph.
For each operation capture:
- value before
- value moved
- fees/haircuts/rounding
- value after
- owner/beneficiary before and after
- accounting representation before and after

Check conservation equations and whether any temporary state permits withdrawal, reuse, double-counting, or unintended exposure.
