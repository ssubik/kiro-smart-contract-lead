# Security, Invariants, and Threat Modeling

## Invariant taxonomy

### Conservation
Examples:
- accounted assets never exceed assets controlled by the system unless the model intentionally represents receivables/debt
- total debits and credits reconcile under the protocol's accounting model

### Authorization
- only the intended actor can mutate a protected agreement/context
- authority in one context cannot leak to another

### State machine
- only explicitly valid transitions are reachable
- terminal states cannot be reactivated unless the domain explicitly permits it

### Isolation
- assets/rights belonging to one agreement/account cannot satisfy or be withdrawn through another

### Solvency / collateralization
- operations cannot leave the system below required collateral/coverage constraints except in explicitly modelled default states

### Uniqueness / replay
- one-time actions cannot be executed twice
- signed operations cannot be replayed across contexts/chains/nonces when prohibited

### Supply / balance
- mint/burn/transfer operations preserve protocol-specific supply and balance relations

## Threat-model worksheet

### Assets
What can be stolen, frozen, corrupted, forged, double-counted, or made unavailable?

### Actors
For each actor identify capabilities, incentives, and whether they are trusted, semi-trusted, or untrusted.

### Trust assumptions
Write them as falsifiable statements, e.g.:
- "The attestor reports values for the correct context and freshness window."
- "The upgrade key cannot be used by one individual without the required governance process."

### Failure challenge
For each assumption ask:
- malicious?
- compromised?
- unavailable?
- stale?
- reordered?
- incorrect but validly signed?

Then determine prevention, detection, containment, and recovery.

## External-call review

For every external call inspect:
- call target control
- callbacks/reentrancy
- state before call
- return-value handling
- revert behavior
- gas/griefing
- token quirks
- approval/allowance lifetime
- arbitrary code execution via hooks/fallbacks

Checks-effects-interactions is a useful baseline, not a proof of safety.

## Signatures/attestations

Review:
- domain separator and chain binding
- nonce/replay strategy
- expiry/freshness
- signer authority and context
- delegated signing semantics
- zero/default values
- signature malleability/format assumptions where relevant
