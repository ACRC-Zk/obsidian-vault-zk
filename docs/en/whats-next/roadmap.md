# Roadmap

Current status and planned work for **human**.

**Last updated:** June 2026

## Shipped (testnet)

### Layer 1 — Identity

- [x] Circom circuit (BLS12-381 + Merkle)
- [x] `kyc_verifier` contract with tests
- [x] Document + face matcher with anti-duplicate
- [x] SDK: `generateProof`, `verifyAndRegister`, `isVerified`
- [x] Browser flow + Stellar Wallets Kit
- [x] E2E script (`scripts/e2e_demo.sh`)

### Layer 2 — Platform

- [x] Platform circuit (`platformId` + membership + `contentHash`)
- [x] `opinion_board` contract
- [x] Off-chain API (profile, feed, articles)
- [x] AI curation + human moderation queue
- [x] Ephemeral fee payer (testnet)

### Onboarding

- [x] Email-based embedded wallet (Pollar) for Web3 newcomers — custodial wallet does not sign human ZK actions

## In progress

- [ ] Credential persistence polish (`credentialStore` UX)
- [ ] Informal crypto audit (nullifier, address binding, issuer root)
- [ ] Public SDK package (`dist/`, npm-ready)
- [ ] This GitBook documentation (ongoing)

## Planned

- [ ] Production KYC provider (licensed issuer / national ID integration)
- [ ] Fee relayer (replace friendbot ephemeral accounts)
- [ ] Username uniqueness enforcement
- [ ] Timing correlation mitigations
- [ ] Moderation governance + appeals
- [ ] Mainnet deployment after audit

## Future — Layer 3

See [Funding ZK (future)](funding-zk.md). Not part of the current production scope.

## Related

* [For judges and developers](../introduction/for-judges-and-developers.md)
* [SDK overview](../sdk/overview.md)
* [Security & limitations](../security/limitations.md)
