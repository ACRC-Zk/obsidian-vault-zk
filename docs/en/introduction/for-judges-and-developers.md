# For judges and developers

This page orients two audiences: **judges** evaluating the project and **developers** integrating or extending it.

---

## For judges (5-minute read)

### Elevator pitch

**human** is the first ZK proof-of-personhood stack built for **Stellar**: verify real humans on-chain without exposing personal data, then let them participate in a verified opinion platform anonymously.

### Why ZK is essential

Without Zero-Knowledge proofs, a smart contract must receive personal data to trust identity claims. With ZK, the contract only receives a **mathematical proof** that:

* the user holds a valid issuer-signed credential,
* they satisfy a predicate (e.g. age, country),
* they have not registered before (nullifier),
* the proof is bound to their Stellar address.

Remove ZK and the privacy model collapses.

### What is demonstrable today (testnet)

| Component | Demo |
|---|---|
| Document + face matcher | User uploads ID photo and live selfie; matcher gates enrollment |
| ZK circuit (Circom / BLS12-381) | Groth16 proof of credential + Merkle membership |
| `kyc_verifier` contract | `verify_and_register` + `is_verified` on testnet |
| Web app | Full browser flow with Stellar Wallets Kit |
| Layer 2 platform | Anonymous `platformId`, on-chain post anchor, off-chain feed |
| Curation | AI agent + human moderation queue (off-chain) |

### Honest limitations

* Issuer is a **mock** on testnet (face matcher, not licensed KYC).
* Deployed on **testnet** only.
* SDK public release is **planned** (see [SDK overview](../sdk/overview.md)).

Read [Security & limitations](../security/limitations.md) for the full list.

### Suggested demo path

1. Connect wallet → enroll (DNI photo + face scan).
2. Generate proof → `verify_and_register` on testnet.
3. Query `is_verified(address)` → true.
4. Switch to platform → derive `platformId` → post opinion anchored on-chain.

Details: [Running the demo](../developer-guides/running-the-demo.md).

---

## For developers (start here)

### Repository

Source code: **https://github.com/ACRC-Zk/beHuman**

> Legacy GitHub org/repo naming; the product is **human**.

### Monorepo layout (by layer)

```text
human/
├── identity/          # Layer 1 — circuits, kyc_verifier, issuer/matcher
├── platform/          # Layer 2 — circuits, opinion_board, api, curation
├── packages/sdk/      # Prover + Stellar tx helpers
├── packages/shared/   # Shared TypeScript types
├── web/               # React + Vite frontend (KYC + platform)
└── scripts/           # deploy_testnet.sh, e2e_demo.sh
```

Full detail: [Repository structure](../developer-guides/repository-structure.md).

### Integration path

1. [Environment setup](../developer-guides/environment-setup.md)
2. [KYC flow](../architecture/kyc-flow.md) — understand the four phases
3. [SDK quickstart](../sdk/quickstart.md) — gate an action with `isVerified`
4. [API reference](../sdk/api-reference.md)

### Key contracts (testnet)

| Contract | Role |
|---|---|
| `kyc_verifier` | Verify ZK proof; register address; `is_verified` |
| `opinion_board` | Anchor posts by `platformId` + `contentHash` |

Contract IDs are in the repo's `.deploy/` directory after deployment.

### Architecture deep dives

* [Layer 1 — Identity](../architecture/layer-1-identity.md)
* [Layer 2 — Platform](../architecture/layer-2-platform.md)
* [Platform identity (platformId)](../architecture/platform-identity.md)

---

## Questions?

* [Glossary](../glossary.md) — ZK, Stellar, and identity terms
* [Roadmap](../whats-next/roadmap.md) — what ships next
