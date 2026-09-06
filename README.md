# Kiro Smart Contract Lead

Reusable Kiro steering and skill set for Lead Smart Contract / Blockchain Engineering reviews.

## What it does

The repository gives Kiro a repeatable lead-engineering review process covering:

- contract boundaries and responsibilities
- system invariants
- threat modelling
- storage layout and upgrade safety
- access-control architecture
- economic and state-machine correctness
- architectural PR review
- abstraction trade-offs
- Foundry fuzzing and invariant testing
- fork and smoke testing
- release/versioning strategy
- deployment verification
- incident response
- lightweight ADRs

## Structure

```text
.kiro/
├── steering/
│   └── smart-contract-lead-principles.md
└── skills/
    └── lead-smart-contract-review/
        ├── SKILL.md
        └── references/
            ├── architecture-and-domain.md
            ├── incident-and-adr.md
            ├── security-and-invariants.md
            ├── testing-and-pr-review.md
            └── upgrades-and-release.md
```

## Usage

Copy `.kiro/` into a Solidity project, then ask Kiro to run the lead smart-contract review on a feature, PR, upgrade, or release.

Example:

```text
Review this feature as a Lead Smart Contract Engineer.
Start with architecture, invariants, trust assumptions, state transitions,
access control, economic correctness, upgrade implications, and test strategy
before reviewing line-level implementation details.
```

The goal is to use AI as a rigorous second reviewer while keeping final engineering judgment with the human lead.
