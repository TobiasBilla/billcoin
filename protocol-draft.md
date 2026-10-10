# Billcoin Protocol Draft (v0.1)

**Status:** Draft for review only. No consensus rules are implemented by this document.

## Purpose

Billcoin is intended to be an independent, peer-to-peer proof-of-work cryptocurrency. It must have its own chain identity and consensus parameters; it must never connect to or be confused with Bitcoin's production network.

## Proposed monetary parameters

| Parameter | Proposal | Status |
|---|---:|---|
| Name | Billcoin | Working name |
| Ticker | BIL | Provisional; availability and naming conflicts not checked |
| Maximum supply | 21,000,000 BIL | Proposed |
| Smallest unit | 0.00000001 BIL | Proposed (100,000,000 base units per BIL) |
| Consensus family | Proof of work | Proposed |
| Target block interval | 10 minutes | Proposed |
| Initial block subsidy | 50 BIL | Proposed |
| Halving interval | 210,000 blocks | Proposed |
| Transaction model | UTXO | Proposed |
| Development reserve | 5% of each block subsidy | Unapproved; requires deterministic consensus design |
| Premine | None proposed | Must be confirmed |

## Decisions that must remain open

1. **Proof-of-work algorithm:** Do not select RandomX or another algorithm until a technical assessment covers implementation maturity, validation cost, hardware concentration, mining incentives, and attack economics.
2. **Difficulty adjustment:** Specify and test behavior during large hash-rate changes, timestamp manipulation, and low-hash-rate periods.
3. **Development reserve:** Define the destination, accounting, spend restrictions, vesting start, edge cases, governance, and key recovery. Every reserve unit must count toward the same maximum supply. Prefer deterministic, independently verifiable rules over discretionary intervention.
4. **Network identity:** Define unique message-start bytes, ports, address prefixes, genesis block, chain parameters, and testnet/regtest identifiers. Verify no accidental network compatibility.
5. **Transaction and script rules:** Decide what is inherited unchanged and what is intentionally different. Avoid unnecessary changes to cryptographic primitives.
6. **Ticker/name:** Check trademark, naming, exchange, and domain conflicts before public branding.

## Supply accounting requirements

- All monetary values must use integer base units; never use floating-point arithmetic for consensus accounting.
- The sum of all issued spendable outputs, provably unspendable outputs, and reserve allocations must follow one documented issuance model.
- Subsidy calculation must be deterministic at every height, including after the final halving.
- Tests must prove that no valid block sequence can exceed the intended cap.
- Fees are transfers from existing outputs, not new issuance.

## Design principle

No change to consensus code should be made until the architecture decision record, threat model, and test plan are reviewed. A passing build does not establish security or production readiness.
