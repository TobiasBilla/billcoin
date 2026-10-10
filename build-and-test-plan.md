# Billcoin Baseline Build and Test Plan

**Goal:** Verify an unmodified, pinned upstream candidate before any Billcoin consensus changes.

## Environment

Use the desktop/laptop for C++ compilation and tests. The phone is suitable for reading documentation, reviewing pull requests, and tracking issues, but should not be the primary build environment.

Record:
- Operating system and version
- CPU architecture and available RAM/disk
- Compiler and version
- CMake and Python versions
- Exact upstream tag and commit SHA
- Commands executed and complete logs

## Baseline steps

1. Review upstream build documentation for the selected pinned release.
2. Clone or download that exact release using the upstream's documented process.
3. Verify the source revision and preserve its license and third-party notices.
4. Install only the documented dependencies from trusted package sources.
5. Configure a build with tests enabled.
6. Compile without modifying consensus or network code.
7. Run the upstream unit and functional test suites as documented for that release.
8. Save build/test output and note every failure; do not silently skip failures.
9. Repeat the build on a clean environment or have a second developer reproduce it.

For current upstream Unix build guidance, see https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md. Follow instructions matching the pinned release, since build commands may change between releases.

## Billcoin-specific tests (future work)

- Unique genesis block and network identifiers.
- Nodes reject blocks with invalid proof of work, invalid target, invalid timestamp, or invalid difficulty transitions.
- No transaction can create value outside the subsidy-plus-fees rules.
- Subsidy and halving calculations match a reference model at boundary heights.
- Maximum supply cannot be exceeded in any tested valid chain.
- Reserve allocation and vesting are deterministic across independent nodes.
- Double spends and invalid UTXO references are rejected.
- Nodes recover from peer disconnections and do not rely on one seed or operator.
- Fuzz tests cover transaction parsing, block parsing, consensus boundaries, and reserve logic.
- Wallet backup, restore, signing, and address/network separation are tested.
- Independent review closes all critical and high-severity findings before any public launch.

## Completion record

- [ ] Candidate and exact commit selected
- [ ] Clean baseline build succeeds
- [ ] Unit tests pass
- [ ] Functional/integration tests pass
- [ ] Known failures documented
- [ ] Reproduction by a second environment completed
- [ ] Architecture decision reviewed before consensus changes

**Important:** A successful baseline build only proves that the selected upstream source builds in that environment. It does not prove Billcoin exists, is secure, or is ready for real funds.
