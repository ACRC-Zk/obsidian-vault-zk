# SDK overview

The **human** SDK wraps proof generation and Stellar contract interaction for integrators.

> **Status:** The SDK in `packages/sdk/` is used internally today. A **curated public release** (built to `dist/`, publishable on npm) is planned. This page describes the target public API.

## Goals

Let third-party Stellar dApps add **anonymous proof-of-personhood** with minimal code:

* Gate actions with `isVerified(address)`.
* Optionally use Layer 2 anonymous mode (`platformId`).

## Public scope (planned v0.1)

| Include | Exclude |
|---|---|
| Layer 1: `generateProof`, `verifyAndRegister`, `isVerified` | Layer 3 funding helpers |
| Layer 2: anonymous membership + `platformId` gating | Low-level encoders (`blsEncode`, `poseidonBls`, `merkle`) — internal |
| Network + contract config (testnet defaults, overridable) | Private monorepo-only utilities |

## Packaging (planned)

* ESM build + TypeScript declarations in `dist/`.
* Peer dependencies: `@stellar/stellar-sdk`, `snarkjs`.
* Browser and Node compatible.
* Circuit artifacts (`kyc.wasm`, `kyc_final.zkey`, `verification_key.json`) bundled or loadable by URL.

## Package name

Product name is **human**. The npm scope may ship as `@human/kyc-zk` or similar once the public package is cut (legacy internal name: `@behuman/sdk`).

## Related

* [Quickstart](quickstart.md)
* [API reference](api-reference.md)
* [Security & limitations](../security/limitations.md)
