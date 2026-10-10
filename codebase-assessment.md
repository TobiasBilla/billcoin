# Upstream Codebase Assessment

**Status:** Preliminary assessment. No base has been selected and no upstream source has been copied into this repository.

## Candidates

### Bitcoin Core
- Repository: https://github.com/bitcoin/bitcoin
- README identifies it as the Bitcoin Core integration/staging tree and documents the MIT license.
- Provides a mature UTXO full-node implementation, wallet options, peer-to-peer networking, and extensive tests.
- Current Unix build notes use CMake: https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md
- Upstream notes warn that the `master` branch is not guaranteed to be stable. Billcoin should pin a reviewed release tag or commit SHA, not follow a moving branch.

### Litecoin Core
- Repository: https://github.com/litecoin-project/litecoin
- README documents the MIT license and a Bitcoin-derived full-node codebase.
- Must be compared at a specific release/commit, including how its chain parameters, proof-of-work, difficulty rules, and inherited changes differ from Bitcoin Core.

## Preliminary recommendation

Start by evaluating Bitcoin Core at a stable tagged release. This is a recommendation for investigation, not final approval. Select the base only after building the unmodified candidate, running its supported test suites, reviewing license obligations, and documenting every planned consensus change.

## Required comparison

| Question | Evidence required |
|---|---|
| Build reproducibly on supported desktop OSes? | Exact release/commit, compiler/dependency versions, build logs |
| Existing tests pass unmodified? | Unit, functional, integration, lint, and relevant fuzz test results |
| Chain parameters isolated? | Reviewed inventory of genesis, network magic, ports, address prefixes, seeds, checkpoints, and chain IDs |
| PoW algorithm compatible with intended design? | Source-level analysis, performance measurements, threat model |
| Difficulty rules safe under target conditions? | Simulation and adversarial tests |
| Issuance and reserve logic correct? | Formal specification, integer arithmetic review, property tests |
| Licensing understood? | Retained notices, dependency licenses, legal review if needed |
| Release can be reproduced and verified? | Documented reproducible-build process and signed artifacts |

## Gate before modifying consensus

1. Choose and record an exact upstream release tag and commit SHA.
2. Preserve the upstream source and its license/notice files.
3. Build the unmodified code on the development computer.
4. Run the upstream test suites and save the results.
5. Write an architecture decision record listing every intended divergence.
6. Have another experienced engineer review the proposed consensus changes.

## Sources
- Bitcoin Core repository and README: https://github.com/bitcoin/bitcoin
- Bitcoin Core Unix build notes: https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md
- Bitcoin Core test documentation: https://github.com/bitcoin/bitcoin/tree/master/test
- Litecoin Core repository: https://github.com/litecoin-project/litecoin
