# Repository structure

The **human** application is a **layered monorepo**. Documentation lives in this vault; code lives on GitHub.

**Source:** https://github.com/ACRC-Zk/beHuman

## Top-level layout

```text
human/
├── README.md · Cargo.toml · package.json · Makefile · .env.example
│
├── identity/                 # LAYER 1 · KYC with ZK
│   ├── circuits/             # Circom — kyc.circom + compile/setup/prove scripts
│   ├── contracts/            # Soroban — kyc_verifier
│   └── issuer/               # KYC issuer (mock) + matcher/ (document + face gate)
│
├── platform/                 # LAYER 2 · Verified opinion platform
│   ├── circuits/             # Circom — post.circom (membership + platformId)
│   ├── contracts/            # Soroban — opinion_board
│   ├── api/                  # Backend: feed, profile, off-chain content
│   └── curation/             # AI validator + human moderation queue
│
├── packages/
│   ├── sdk/                  # Prover + Stellar tx helpers
│   └── shared/               # Shared TypeScript types
│
├── web/                      # React + Vite + TypeScript (single frontend)
│   └── src/                  # kyc/ (Layer 1) + platform/ (Layer 2)
│
├── scripts/                  # deploy_testnet.sh · e2e_demo.sh
└── .deploy/                  # Deployed contract IDs (testnet)
```

## Layer bridge

The **only on-chain bridge** between enrollment and platform gating for address-based apps:

```
is_verified(address)  →  kyc_verifier contract
```

Layer 2 uses a **ZK bridge** (`issuerRoot` membership) instead.

## Docs ↔ code mapping

| Documentation topic | Code path |
|---|---|
| Layer 1 circuit | `identity/circuits/src/kyc.circom` |
| KycVerifier | `identity/contracts/kyc_verifier/src/lib.rs` |
| Identity matcher | `identity/issuer/matcher/` |
| KYC flow / SDK | `packages/sdk/` + `web/` + `scripts/e2e_demo.sh` |
| Layer 2 platform | `platform/contracts/opinion_board` + `platform/api` |
| Curation | `platform/curation` |

## Conventions

* **Docs repo** (this vault): commits `docs: <change>`.
* **Code repo**: conventional commits (`feat:`, `fix:`, `chore:`).
* READMEs explicitly label **mock** components (issuer on testnet).

## Related

* [Environment setup](environment-setup.md)
* [Architecture overview](../architecture/overview.md)
